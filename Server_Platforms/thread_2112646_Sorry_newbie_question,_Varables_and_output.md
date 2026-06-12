---
title: "Sorry newbie question, Varables and output"
date: 2013-02-05
forum: Server Platforms
---

### Post by StefanThorpe on 2013-02-05
I would like to run a script that checks to see is Mysql is live. I think something like

```
mysqladmin -umysql ping
```If the result does match mysqld is alive then I would like it to send an email using mailx.


My question is this 
Why does this only show the last line? and how do I get it to show the full results
```
mysqladmin -umysql ping | $result
echo $result 

```Thanks

Stefan

---

### Post by spynappels on 2013-02-05
Are you sure there is more than one line in the output? On my server the output is a single line:
```
stefan@fileserver:~$ mysqladmin -u root -p ping
Enter password: 
mysqld is alive
stefan@fileserver:~$
```

I'm also not sure what the pipe to $result is trying to achieve, do you want to append the output of the ping command to $result? Or is $result simply the output from the command? A different way of doing that would be:
```
result=$(mysqladmin -umysql ping)
echo $result
```

---

### Post by The Cog on 2013-02-05
How about:
```
mysqladmin -umysql ping
if [ $? == 1 ] ; then
    sendmail or whatever the command is
fi
```
Sorry, I don't know the command to send an email

Or...
```

if ! mysqladmin -umysql ping
then
    sendmail or whatever the command is
fi
```

---

### Post by spynappels on 2013-02-05
> **The Cog said:**
> How about:
```
mysqladmin -umysql ping
if [ $? == 1 ] ; then
    sendmail or whatever the command is
fi
```
Sorry, I don't know the command to send an email

Or...
```

if ! mysqladmin -umysql ping
then
    sendmail or whatever the command is
fi
```

The OP said he wanted an email sent if the mysqld is alive, counterintuitive but there you go...

Anyway, if the mail is to contain the results of the ping command, another option would be:
```
mysqladmin -umysql ping > /path/to/outfile
if [ $? == 0 ] ; then
    mailx -s "Some Subject" -a /path/to/outfile some.address@somedomain
fi
```

---

### Post by PowerBarry43 on 2013-02-05
Hi

I would recommend instead of using a variable actually using a file in /tmp to store all the info. Then just output that file with cat notice thee difference between backtick ` (left of 1 on most keyboards) and apostrophe ' ;) 

```
mysqladmin -umysql ping > /tmp/result
cat `/tmp/result` | mail -s “mysql” your@email.com
```

Hope this helps!

Barry

---

### Post by StefanThorpe on 2013-02-05
Ok I'm getting closer

 ```
 #!/bin/bash
 
mysqladmin -umysql ping > /tmp/sqlresults
if ! cmp -s /tmp/sqlresults /tmp/sqlalive; then
        mailx -A gmail -s "Test Number 5" stefan.thorpe@gmail.com < /tmp/sqlresults
fi

```
sqlalive is and exact copy of any alive output.( A single line that shows mysqld is alive)

The compare checks to see if there is a difference if there is then it send me an email. With the results attached. However when the mysql is not running it displays the message below in the terminal and doesn't place it in the file. How do I resolve this?

```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

---

### Post by steeldriver on 2013-02-05
That would be because the message is going to the error stream instead of the standard output stream - if you want to capture both streams try either

```
mysqladmin -umysql ping > /tmp/sqlresults **2>&1**
```or (bash 4+ only iirc)

```
mysqladmin -umysql ping **&>** /tmp/sqlresults
```

---

### Post by hawkmage on 2013-02-05
If you are tyring to get both stdout and error you have to do the redirect of stderr to std out before you redirect to the file like this:
```
mysqladmin -umysql ping 2>&1 > /tmp/sqlresults
```

Or if you want to capture it in a varable and not put it in a file:
```
result=$(mysqladmin -umysql ping 2>&1)
```

---

### Post by SeijiSensei on 2013-02-05
I much prefer to run ps to find out if some daemon is running:

```
[ "$(ps ax | grep mysqld)" = "" ] && mail -s 'mysql down' you@example.com
```

This approach generalizes to all daemon processes and doesn't depend on a specific feature of MySQL.

---

### Post by spynappels on 2013-02-06
> **StefanThorpe said:**
> Ok I'm getting closer

 ```
 #!/bin/bash
 
mysqladmin -umysql ping > /tmp/sqlresults
if ! cmp -s /tmp/sqlresults /tmp/sqlalive; then
        mailx -A gmail -s "Test Number 5" stefan.thorpe@gmail.com < /tmp/sqlresults
fi

```
sqlalive is and exact copy of any alive output.( A single line that shows mysqld is alive)

The compare checks to see if there is a difference if there is then it send me an email. With the results attached. However when the mysql is not running it displays the message below in the terminal and doesn't place it in the file. How do I resolve this?

```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

Can you please confirm that you want to send a mail when mysql is down or when it is alive? The OP suggested you wanted to send a mail if mysql was alive, but the post quoted above suggests the opposite, which admittedly does make more sense.

If you want to get an email if it is down, SeijiSensei's solution is tidier if the output of the ping is not really important.

---

