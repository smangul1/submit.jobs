# Oda


1. Create run.template.sh with Z insteadof chr

2. 

```
while read line;do sed 's/chrZ/'$line'/g' run.template.sh >run.${line}.sh;done<../chr.txt```

3. Create job.template.sh

```
executable              = /nfs/home/smangul/nfs3/raritet.MDD/annotated.varinats.frequency.category.individuals.10/run.chrZ.sh
log                     = chrZ.log
output                  = chrZ.out.txt
error                   = chrZ.errors.txt
request_memory=12G
request_cpus=1
queue 1
````

4. 

```
while read line;do sed 's/chrZ/'$line'/g' job.template.sh >job.${line}.sh;done<../chr.txt
```

5. 
```
chmod 755 *sh
for f in job*;do condor_submit $f;done
```
