---
title: "MySQL extremely slow"
date: 2011-01-27
forum: Server Platforms
---

### Post by amish_geek on 2011-01-27
I've got Ubuntu Server 10.04 on a fairly beefy box (quad-core xeon 2.67ghz, 2gb ram)  Standard mysql-server installed, with many databases.


Lately, mysql has been extremely slow and almost non-responsive.  Server loads are low.

Running mtop reveals many, many processes from the user: debian-sys-maint querying the information_schema table with the exact same query, over and over.


"Select count(*) from tables where engine = 'innodb'"

This is adversely affecting my database server, and thus my websites which rely on mysql.  Every search I've done looking for more information about the debian-sys-maint user shows problems where that users was deleted.  The user isn't deleted.

Any suggestions on what I can do to make my server fast again?

---

### Post by Vegan on 2011-01-27
If the server load is high, adding RAM will perk up performance. The larger the databases, the more RAM MySQL would love to have.

---

### Post by amish_geek on 2011-01-28
Server loads are low... between 1 & 2 so not even maxing out the CPU's.


I do believe I'm experiencing a bottleneck with IO though... this is the results of iostat:
```

Linux 2.6.32-28-server (cw2) 	01/28/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.48    0.00    0.93   12.83    0.00   85.77

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda             228.78      5575.45      1729.49  232459094   72108368


```

---

### Post by amish_geek on 2011-01-28
And this is the current listing in mtop....


```

load average: 1.22, 1.42, 1.52 mysqld 5.1.41-3ubuntu12.9 up 0 day(s),  4:58 hrs                                                                                                                              
74 threads: 73 running, 1 cached. Queries/slow: 13/0 Cache Hit: 72.25%                                                                                                                                       
Opened tables: 0  RRN: 272  TLW: 64  SFJ: 0  SMP: 0  QPS: 0                                                                                                                                                  
                                                                                                                                                                                                             
ID       USER     HOST             DB           TIME   COMMAND STATE        INFO                                                                                                                             
102      debian-s localhost        information_ 16421  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
151      debian-s localhost        information_ 15520  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
168      debian-s localhost        information_ 15220  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
178      debian-s localhost        information_ 14918  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
200      debian-s localhost        information_ 14620  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
220      debian-s localhost        information_ 14321  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
243      debian-s localhost        information_ 14021  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
270      debian-s localhost        information_ 13718  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
287      debian-s localhost        information_ 13420  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
311      debian-s localhost        information_ 13119  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
325      debian-s localhost        information_ 12819  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
344      debian-s localhost        information_ 12520  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
364      debian-s localhost        information_ 12220  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
387      debian-s localhost        information_ 11918  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
413      debian-s localhost        information_ 11618  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
429      debian-s localhost        information_ 11320  Killed  checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
449      debian-s localhost        information_ 11019  Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
467      debian-s localhost        information_ 10718  Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
488      debian-s localhost        information_ 10419  Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
503      debian-s localhost        information_ 10119  Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
516      debian-s localhost        information_ 9818   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
533      debian-s localhost        information_ 9519   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
545      debian-s localhost        information_ 9220   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
569      debian-s localhost        information_ 8919   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
592      debian-s localhost        information_ 8620   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
610      debian-s localhost        information_ 8319   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
856      debian-s localhost        information_ 8019   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
910      debian-s localhost        information_ 7420   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
923      debian-s localhost        information_ 7121   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
933      debian-s localhost        information_ 6822   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
946      debian-s localhost        information_ 6518   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
971      debian-s localhost        information_ 6223   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
983      debian-s localhost        information_ 5919   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
999      debian-s localhost        information_ 5620   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
1019     debian-s localhost        information_ 5321   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
1032     debian-s localhost        information_ 5022   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
1050     debian-s localhost        information_ 4719   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                   
1063     debian-s localhost        information_ 4421   Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'   

```

---

### Post by DaithiF on 2011-01-28
First a bit of background info ... at mysql startup, debian based distros run the script /etc/mysql/debian-start, which in turns calls several functions in /usr/share/mysql/debian-start.inc.sh

one of these 'check_for_crashed_tables', iterates over tables in your database doing a record count for each.

Two things:
1. there is a long standing mysql bug ([http://bugs.mysql.com/bug.php?id=19588](http://bugs.mysql.com/bug.php?id=19588)) which complains about very poor performance querying information_schema when the number of databases and/or tables is large.  The debian script use information_schema to loop through the databases / tables it needs to do table counts for.

2. the mtop output you posted shows queries checking row counts for tables of type Innodb .. that has me a bit confused because on my 10.04 box those startup queries only check MyISAM tables.  The distinction is important because a count(*) on a MyISAM table is more or less instantaneous (as the row count is stored as a table attribute), whereas on an Innodb table it requires actually reading table or index data to perform a count.  I also thought the whole point of checking the table count was to identify which MyISAM tables had errors (reported as part of checking their table counts), so I don't see any merit in doing innodb table counts as part of this startup process.

Perhaps something in those scripts has been customised on your server -- below is the content of the check_for_crashed_tables from /usr/share/mysql/debian-start-inc.sh on my server.

In any case, you could dispense with this particular start-up check and comment out the function invocation from /etc/mysql/debian-start to confirm if this is indeed the problem.


```
function check_for_crashed_tables() {
  set -e
  set -u

  # But do it in the background to not stall the boot process.
  logger -p daemon.info -i -t$0 "Triggering myisam-recover for all MyISAM tables"

  # Checking for $? is unreliable so the size of the output is checked.
  # Some table handlers like HEAP do not support CHECK TABLE.
  tempfile=`tempfile`
  # We have to use xargs in this case, because a for loop barfs on the
  # spaces in the thing to be looped over.
  LC_ALL=C $MYSQL --skip-column-names --batch -e  '
      select concat('\''select count(*) into @discard from `'\'',
                    TABLE_SCHEMA, '\''`.`'\'', TABLE_NAME, '\''`'\'')
      from information_schema.TABLES where ENGINE='\''MyISAM'\' | \
    xargs -i $MYSQL --skip-column-names --silent --batch \
                    --force -e "{}" >$tempfile
  if [ -s $tempfile ]; then
    (
      /bin/echo -e "\n" \
        "Improperly closed tables are also reported if clients are accessing\n" \
    "the tables *now*. A list of current connections is below.\n";
       $MYADMIN processlist status
    ) >> $tempfile
    # Check for presence as a dependency on mailx would require an MTA.
    if [ -x /usr/bin/mailx ]; then
      mailx -e -s"$MYCHECK_SUBJECT" $MYCHECK_RCPT < $tempfile
    fi
    (echo "$MYCHECK_SUBJECT"; cat $tempfile) | logger -p daemon.warn -i -t$0
  fi
  rm $tempfile
}

```

---

### Post by datamove on 2011-01-28
12% iowait - mysql is waiting on disk I/O. Try to experiment with ext3 istead of ext4. IIRC there were reports that ext4 is slow for databases. Otherwise get faster disk or read elsewhere how to optimize mysql for performance.

---

### Post by amish_geek on 2011-01-28
I've disabled the check_for_crashed_tables function (commented it out).  The function itself is identical to yours.

I restarted Mysql and still:

```

load average: 2.46, 1.53, 1.27 mysqld 5.1.41-3ubuntu12.9 up 0 day(s),  0:10 hrs                                                                                                                                                                                   
5 threads: 5 running, 4 cached. Queries/slow: 153/0 Cache Hit: 5.52%                                                                                                                                                                                              
Opened tables: 0  RRN: 272  TLW: 0  SFJ: 0  SMP: 0  QPS: 0                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                  
ID       USER     HOST             DB           TIME   COMMAND STATE        INFO                                                                                                                                                                                  
15       debian-s localhost        information_ 384    Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                                                                        
27       debian-s localhost        information_ 83     Query   checking per SELECT ... FROM tables WHERE ENGINE = 'InnoDB'                                                                                                                                        
17       mysqltop localhost                            Query                show full processlist                                                                                                                                                                 
---                                                                

```

---

### Post by amish_geek on 2011-01-28
I solved the issue.

I had recently installed Munin on the server to track and graph my server stats.  I had installed the mysql_innodb plugin.  The mysql_innodb plugin, when called every 5 minutes by munin, somehow caused the debian-sys-maint user to run that query.


Disabling that plugin solved the problem.

---

