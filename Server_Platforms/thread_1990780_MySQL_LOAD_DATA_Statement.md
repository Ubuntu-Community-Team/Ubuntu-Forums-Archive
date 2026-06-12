---
title: "MySQL LOAD DATA Statement"
date: 2012-05-29
forum: Server Platforms
---

### Post by larka06 on 2012-05-29
I have ubuntu 12.04 I am trying to learn MySQL on. The MySQL version is 5.5.22-0buntu1 (Ubuntu). When I follow the book at MySQL I run into a problem they can not help me with because it is Ubuntu specific.
LOAD DATA LOCAL INFILE '/file/file/file.txt INTO TABLE. I get this response;
**The used command is not allowed with this MySQL version.**
I hope somebody knows something I have tried serveral combinations of the LOAD DATA statement, alas, nothing works

---

### Post by memilanuk on 2012-05-31
Well... since no one else is taking a stab at this, I will.

```
LOAD DATA LOCAL INFILE '/file/file/file.txt INTO TABLE.
```

Looks like a couple potential typos - lack of a following/closing single quote (') after file.txt, and no table name supplied.  Could be that just got missed whilst writing the post... but figured I'd go for the easy ones first ;)

Other than those two changes, it should work.  AFAIK, MySQL isn't significantly different in any meaningful way from MySQL on any other platform - especially not for something as basic as loading a data file.

FWIW... is the version mysql in the book the same as the one on your Ubuntu box (5.5)?  Once in a while you might find some issues there if the book is based on a very different release... but as long as they both 5.x releases it should be close.

HTH,

Monte

---

### Post by LHammonds on 2012-05-31
Let's not forget that even books can have typos.  Be sure to check multiple references if you cannot get one example to work right.

Here is a good place for accurate info: [MySQL 5.5 Load Data]("http://dev.mysql.com/doc/refman/5.5/en/load-data.html")

---

### Post by daniel4ing on 2012-06-01
I've been having issues with this mysql. From what I've gathered they decided to switch this off in the current version of MYSQL and if you want to enable it, you'll have to recompile mysql with --enable-local-infile. since the binary doesn't even allow you to change the option.

---

### Post by memilanuk on 2012-06-01
daniel,

Not entirely correct.

You're right; it turns out that for whatever well-intentioned reason this flavor of mysql doesn't by default allow loading from a local infile.

```

mysql> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;
ERROR 1148 (42000): The used command is not allowed with this MySQL version
mysql>

```

If you search the MySQL Reference Documentation for Error 1148, further down the page linked above, in the comments:

> 
Posted by Aaron Peterson on November 9 2005 4:35pm

With a defalut installation from FreeBSD ports, I had to use the command line

mysql -u user -p --local-infile menagerie

to start the mysql monitor, else the LOAD DATA LOCAL command failed with an error like the following:

ERROR 1148 (42000): The used command is not allowed with this MySQL version

...


which *does* work.

```

monte@oobun2:~$ mysql -h localhost -u monte -p monte --local-infile
Enter password: 

...

mysql> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;
Query OK, 8 rows affected (0.04 sec)
Records: 8  Deleted: 0  Skipped: 0  Warnings: 0

mysql> SELECT * FROM pet;
+----------+--------+---------+------+------------+------------+
| name     | owner  | species | sex  | birth      | death      |
+----------+--------+---------+------+------------+------------+
| Fluffy   | Harold | cat     | f    | 1993-02-04 | NULL       |
| Claws    | Gwen   | cat     | m    | 1994-03-17 | NULL       |
| Buffy    | Harold | dog     | f    | 1989-05-13 | NULL       |
| Fang     | Benny  | dog     | m    | 1990-08-27 | NULL       |
| Bowser   | Diane  | dog     | m    | 1979-08-31 | 1995-07-29 |
| Chirpy   | Gwen   | bird    | f    | 1998-09-11 | NULL       |
| Whistler | Gwen   | bird    | NULL | 1997-12-09 | NULL       |
| Slim     | Benny  | snake   | m    | 1996-04-29 | NULL       |
| Puffball | Diane  | hamster | f    | 1999-03-30 | NULL       |
+----------+--------+---------+------+------------+------------+
9 rows in set (0.00 sec)

mysql>

```

---

### Post by ChristopheH on 2012-07-23
Memilanuk,

I have the same issue while loading my data, but I would like to apply your solution to a software called orthomcl which use perl DBI to connect to the database and then process my data.

Do you have any idea about the way to do that? I'm not used to perl and bioperl, so I could not manage to find a solution..

The problem is located in orthmclLoadBlast

sub loadBlastMySQL {
  my ($base, $blastFile) = @_;
  require DBD::mysql;
  my $dbh = $base->getDbh();
  my $sst = $base->getConfig("similarSequencesTable");
  my $sql = "
 LOAD DATA
 LOCAL INFILE \"$blastFile\"
 REPLACE INTO TABLE $sst
 FIELDS TERMINATED BY '\\t'
";
  my $stmt = $dbh->prepare($sql) or die DBI::errstr;
  $stmt->execute() or die DBI::errstr;
}

**using these methods:**

sub getConfig {
  my ($self, $prop) = @_;
  die "can't find property $prop in config file" unless $self->{config}->{$prop};
  return $self->{config}->{$prop};
}


sub getDbh {
  my ($self) = @_;

  if (!$self->{dbh}) {
    my $dbVendor = $self->getConfig("dbVendor");
    if ($dbVendor eq 'oracle') {
      require DBD::Oracle;
    } elsif ($dbVendor eq 'mysql') {
      require DBD::mysql;
    } else {
      die "config file '$self->{configFile}' has invalid value '$dbVendor' for dbVendor property\n";
    }

    $self->{dbh} = DBI->connect($self->getConfig("dbConnectString"),
                $self->getConfig("dbLogin"),
                $self->getConfig("dbPassword")) or die DBI::errstr;
  }
  return $self->{dbh};
}


I hope that somebody could help me with that..

Thank you!

---

### Post by memilanuk on 2012-07-23
For perl?... no idea, sorry.

---

### Post by pdleirer on 2012-12-09
'LOAD INFILE' and it's variants ( DATA, XML ) can be re-enabled within mysqld and mysql client by altering the /etc/mysql/my.cnf file.

Under the sections [mysqld] and [mysql] add 'local-infile=1':

[mysqld]

.... some configs ...

local-infile=1

[mysql]

.... some configs ....

local-infile=1


The MYSQL development team thought it necessary to further enhance the security of the software with this feature. Be sure to evaluate your overall security posture before implementing this change.

Very Respectfully

---

### Post by AboYamaan on 2013-02-03
> **memilanuk said:**
> daniel,

Not entirely correct.

You're right; it turns out that for whatever well-intentioned reason this flavor of mysql doesn't by default allow loading from a local infile.

```

mysql> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;
ERROR 1148 (42000): The used command is not allowed with this MySQL version
mysql>

```If you search the MySQL Reference Documentation for Error 1148, further down the page linked above, in the comments:



which *does* work.

```

monte@oobun2:~$ mysql -h localhost -u monte -p monte --local-infile
Enter password: 

...

mysql> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;
Query OK, 8 rows affected (0.04 sec)
Records: 8  Deleted: 0  Skipped: 0  Warnings: 0

mysql> SELECT * FROM pet;
+----------+--------+---------+------+------------+------------+
| name     | owner  | species | sex  | birth      | death      |
+----------+--------+---------+------+------------+------------+
| Fluffy   | Harold | cat     | f    | 1993-02-04 | NULL       |
| Claws    | Gwen   | cat     | m    | 1994-03-17 | NULL       |
| Buffy    | Harold | dog     | f    | 1989-05-13 | NULL       |
| Fang     | Benny  | dog     | m    | 1990-08-27 | NULL       |
| Bowser   | Diane  | dog     | m    | 1979-08-31 | 1995-07-29 |
| Chirpy   | Gwen   | bird    | f    | 1998-09-11 | NULL       |
| Whistler | Gwen   | bird    | NULL | 1997-12-09 | NULL       |
| Slim     | Benny  | snake   | m    | 1996-04-29 | NULL       |
| Puffball | Diane  | hamster | f    | 1999-03-30 | NULL       |
+----------+--------+---------+------+------------+------------+
9 rows in set (0.00 sec)

mysql>

```

Thank u very much! It's really a complete and useful answer for such a problem.

---

