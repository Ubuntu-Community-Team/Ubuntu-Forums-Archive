---
title: "remote mysql host login test weird help"
date: 2011-01-11
forum: Server Platforms
---

### Post by sdowney717 on 2011-01-11
according to this
[http://www.debianhelp.co.uk/remotemysql.htm](http://www.debianhelp.co.uk/remotemysql.htm)

I should be able to login to another server but all it does is return the help pages?

```
scott@scott-desktop:~$ **mysql -u root –h 192.168.1.101 –p**
mysql  Ver 14.14 Distrib 5.1.49, for debian-linux-gnu (i686) using readline 6.1
Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license
Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  -I, --help          Synonym for -?
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field completion, but startup
                      and reconnecting may take a longer time. Disable with
                      --disable-auto-rehash.
  -A, --no-auto-rehash 
                      No automatic rehashing. One has to use 'rehash' to get
                      table and field completion. This gives a quicker start of
                      mysql and disables rehashing on reconnect.
  -B, --batch         Don't use history file. Disable interactive behavior.
                      (Enables --silent.)
  --character-sets-dir=name 
                      Directory for character set files.
  --column-type-info  Display column type information.
  -c, --comments      Preserve comments. Send comments to the server. The
                      default is --skip-comments (discard comments), enable
                      with --comments.
  -C, --compress      Use compression in server/client protocol.
  -#, --debug[=#]     This is a non-debug version. Catch this and exit.
  --debug-check       Check memory and open file usage at exit.
  -T, --debug-info    Print some debug info at exit.
  -D, --database=name Database to use.
  --default-character-set=name 
                      Set the default character set.
  --delimiter=name    Delimiter to be used.
  -e, --execute=name  Execute command and quit. (Disables --force and history
                      file.)
  -E, --vertical      Print the output of a query (rows) vertically.
  -f, --force         Continue even if we get an SQL error.
  -G, --named-commands 
                      Enable named commands. Named commands mean this program's
                      internal commands; see mysql> help . When enabled, the
                      named commands can be used from any line of the query,
                      otherwise only from the first line, before an enter.
                      Disable with --disable-named-commands. This option is
                      disabled by default.
  -g, --no-named-commands 
                      Named commands are disabled. Use \* form only, or use
                      named commands only in the beginning of a line ending
                      with a semicolon (;). Since version 10.9, the client now
                      starts with this option ENABLED by default. Disable with
                      '-G'. Long format commands still work from the first
                      line. WARNING: option deprecated; use
                      --disable-named-commands instead.
  -i, --ignore-spaces Ignore space after function names.
  --local-infile      Enable/disable LOAD DATA LOCAL INFILE.
  -b, --no-beep       Turn off beep on error.
  -h, --host=name     Connect to host.
  -H, --html          Produce HTML output.
  -X, --xml           Produce XML output.
  --line-numbers      Write line numbers for errors.
  -L, --skip-line-numbers 
                      Don't write line number for errors.
  -n, --unbuffered    Flush buffer after each query.
  --column-names      Write column names in results.
  -N, --skip-column-names 

```

---

### Post by Thirtysixway on 2011-01-11
are you typing just -p or -p mysql? From the guide it looks like you're missing **-p mysql**

help pages show if you're missing an argument (or if you type --help of course )

---

### Post by sdowney717 on 2011-01-11
just seems to be -p
should be like 
hi mysql, i am user webadmin at host 172.20.6.2 and my password I will type in by hand

> Step # 6: Test it

From remote system type command

$ mysql -u webadmin –h 172.20.5.2 –p

---

### Post by Thirtysixway on 2011-01-11
You're right! hmm. I don't know exactly why it's not working, but I got it to work on my machine by rearranging the arguments
```
mysql -h 192.168.1.101 -u root -p
```
(of course I got a could not connect error since I don't have a server running at that IP, but it should work for you)

---

### Post by sdowney717 on 2011-01-11
yeah that worked why is that!
> scott@scott-desktop:~$ mysql -h 192.168.1.101 -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 205
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 

---

### Post by sj1410 on 2011-01-12
-p should be after -u root

thats the reason

---

### Post by sdowney717 on 2011-01-12
thanks, that web site needs to fix itself
documentation that is wrong causes people to wonder why.

> From remote system type command

$ mysql -u webadmin –h 172.20.5.2 –p

You can also use telnet to connect to port 3306 for testing purpose

$ telnet 172.20.5.2 3306


---

