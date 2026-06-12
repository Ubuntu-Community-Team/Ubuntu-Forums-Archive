---
title: "Parallel Mysql dump"
date: 2011-09-19
forum: Server Platforms
---

### Post by rtznprmpftl on 2011-09-19
Hello everyone.

at the moment im doing my mysqlbackups by dumping every database in an extra file.

the script looks like that 
```

DATABASES="$(mysql -h localhost -Bse 'show databases')"

for db in $DATABASES
do
    mysqldump   $db | gzip -3 > $db.sql.gz
done
wait

```
While this is quite convenient it has the problem that these are done sequential. which means that it takes quite a lot time and 3 cores of the cpu are getting bored.


what i found to execute this in parralel is the parralel command from the moreutils package but i havent found out how to apply this to my script.
can anyone help me with this task ?

---

### Post by koenn on 2011-09-19
you could try simply backgrounding (&) the mysqldump. This will make your loop continue to its next iteration without waiting for the command to finnish, resulting in n quasi simultaneous  dumps. Ideally, your OS will spread them over all available CPUs. 

as you have pipes and redirects there, you probably need to () the command; something like 
```

do
   ( mysqldump   $db | gzip -3 > $db.sql.gz  ) &
done

```

---

### Post by rtznprmpftl on 2011-09-19
This would get a little anoying, i have a lot of databases (iirc 60) using 10 gb of space.
This makes the Server unusable for about an hour.

---

### Post by koenn on 2011-09-19
because you'd be using all cpus ?

meh. first you complain they're idle, then you complain they're busy. What is it that you want then ?

---

### Post by koenn on 2011-09-19
I had a look at parallel

a quick and dirty way to do this would be to build a list of things to do, and feed that list into parallel (as opposed to iterating though a loop)

think something like
```

do
   echo  "mysqldump   $db | gzip -3 > $db.sql.gz " >> things_to_do
done

parallel <things_to_do


```
you might need some options to 'parallel' there


or have a look at [http://www.gnu.org/software/parallel/man.html#example__rewriting_a_for_loop_and_a_while_read_loop](http://www.gnu.org/software/parallel/man.html#example__rewriting_a_for_loop_and_a_while_read_loop)
and try something like
```
cat list_of_databases |parallel mysqldump ...
```
but in this approach you'll need to find a way to keep  your output redirect per job, it'll probably default to all jobs. think parenteses, -q, or qoutes and escapes

---

### Post by rtznprmpftl on 2011-09-19
If i fire all at once, the disk io is problematic.


what i tried so far is 
```


mysql -h localhost -Bse 'show databases' | parallel -i -- mysqldump {} | gzip -3 > {}.sql.gz
 

```
where i get "sh: {}: not found" as an error
```


mysql -h localhost -Bse 'show databases' | parallel -i -- "mysqldump {} | gzip -3 > {}.sql.gz"
 

```
returns "mysqldump: Got error: 1049: Unknown database '{}' when selecting the database"


and
```

dump_db () {
mysqldump  $1 | gzip -3 > $1.sql.gz
} 
mysql -h localhost -Bse 'show databases' | parallel -- dump_db

```
returns "sh: dump_db: not found"



now i have really no idea what to do

---

