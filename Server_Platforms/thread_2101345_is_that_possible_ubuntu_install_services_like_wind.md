---
title: "is that possible ubuntu install services like window?"
date: 2013-01-04
forum: Server Platforms
---

### Post by chinye2020 on 2013-01-04
i have develop a services can run properly in window server 2008,
it is develop by Delphi or VB.NET
is those services can install in Ubuntu Server GUI Mode?
and how to install?
or
i can use any language to develop a service? like the window service one.
but make sure can be install and run properly in ubuntu/Linux

---

### Post by oldos2er on 2013-01-04
Moved to Server Platforms.

---

### Post by chinye2020 on 2013-01-04
i want to develop a service like window service in Ubuntu,
this service is a server listener, will listening port 6903,
and waiting any packets receive and save to the MySQl database.
i would like to know which language can be develop and work properly in Ubuntu?
is that Vb.NET or Delphi possible?

---

### Post by akshay.bhardwaj on 2013-01-04
Well it is possible. Well for ubuntu you can go for wide range of options but I will propose you go for python (quite easy to implement) or C/C++. .NET framework is not inherently supported on linux except you can try mono. But if you want something solid on linux/ubuntu go for python or C/C++. Then create a library and run it as service using inbuilt features of linux.

---

### Post by cybergalvez on 2013-01-04
> **chinye2020 said:**
> i want to develop a service like window service in Ubuntu,
this service is a server listener, will listening port 6903,
and waiting any packets receive and save to the MySQl database.
i would like to know which language can be develop and work properly in Ubuntu?
is that Vb.NET or Delphi possible?

in my opinion "services" are actually easier to write on Linux then they are in windows, nothing really special needed. As far as which language, pick your favorite. You mention VB.Net, which is a Microsoft product who does not support Linux, however if you can code in c# then you can use mono, Delphi is a flavor of Pascal which you can use Lazarus with free Pascal if that is your preference. Mine is Python, but they all work.

Code what you want, and just start it as a daemon, in Linux daemons (services) do not need to be started or managed in any special way. Howeve if you really want to manage it the correct way (startup when your computer starts ect) you will have to write an upstart script ([http://upstart.ubuntu.com/](http://upstart.ubuntu.com/))

---

### Post by gnush on 2013-01-04
I think Python would be a good choice. Here's a rough draft I made - I don't know if it works as I haven't tested it, but see it as an overview.

```
import socket
import _mysql
import sys

try:
    username = sys.argv[1]
    password = sys.argv[2]
    port = sys.argv[3]
    db_name = sys.argv[4]
    table_name = sys.argv[5]
    host = ''

except IndexError:
    print "Error: "
    print "Be sure to specify username, password, port, database name and table name.\n"
    print "Syntax: ./script.py username password port db_name table_name."
    print "Example: ./script.py hank mypass 8762 testdb test_table"
    print "\nExit..."
    sys.exit(1)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((host, port))
s.listen(1)

c, addr = s.accept()

while 1:
    data = c.recv(1024)
    if not data: break
c.close()

mysql_c = None

try:
    mysql_c = _mysql.connect('localhost', username, password, db_name)
    mysql_c.query('insert into '+table_name+' values '+data)

except _mysql.Error, e:
    print "Error: %d: %s " % (e.args[0], e.args[1])
    sys.exit(1)

finally:
    if mysql_c:
        mysql_c.close()
```[I]Relevant links:

[http://docs.python.org/2/library/socket.html](http://docs.python.org/2/library/socket.html)
[http://mysql-python.sourceforge.net/MySQLdb.html](http://mysql-python.sourceforge.net/MySQLdb.html)[/I]

---

### Post by koenn on 2013-01-04
> **oldos2er said:**
> Moved to Server Platforms.

it's a programming question, really.

---

### Post by koenn on 2013-01-04
> **chinye2020 said:**
> i have develop a services can run properly in window server 2008,
it is develop by Delphi or VB.NET
is those services can install in Ubuntu Server GUI Mode?
and how to install?
or
i can use any language to develop a service? like the window service one.
but make sure can be install and run properly in ubuntu/Linux

It's not really a quastion of what language, but of compilers. You need to compile your "service" so that it will run on Linux. 
Also, if you've written it in a way that relies on windows system stuff (components, libraries, ...), it will obviously only work on Windows.

---

### Post by cariboo on 2013-01-04
> **chinye2020 said:**
> i have develop a services can run properly in window server 2008,
it is develop by Delphi or VB.NET
is those services can install in Ubuntu Server GUI Mode?
and how to install?
or
i can use any language to develop a service? like the window service one.
but make sure can be install and run properly in ubuntu/Linux

What type of service are you wanting to set up, as it may already be available in the repositories. BTW, the server does not come with a gui of any sort, so if you feel you need one, you will have to install it yourself.

**Note:** I've merged your two threads, as one of the other staff moved the thread from where it was to this sub-forum.

---

### Post by chinye2020 on 2013-01-05
> **gnush said:**
> I think Python would be a good choice. Here's a rough draft I made - I don't know if it works as I haven't tested it, but see it as an overview.

```
import socket
import _mysql
import sys

try:
    username = sys.argv[1]
    password = sys.argv[2]
    port = sys.argv[3]
    db_name = sys.argv[4]
    table_name = sys.argv[5]
    host = ''

except IndexError:
    print "Error: "
    print "Be sure to specify username, password, port, database name and table name.\n"
    print "Syntax: ./script.py username password port db_name table_name."
    print "Example: ./script.py hank mypass 8762 testdb test_table"
    print "\nExit..."
    sys.exit(1)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((host, port))
s.listen(1)

c, addr = s.accept()

while 1:
    data = c.recv(1024)
    if not data: break
c.close()

mysql_c = None

try:
    mysql_c = _mysql.connect('localhost', username, password, db_name)
    mysql_c.query('insert into '+table_name+' values '+data)

except _mysql.Error, e:
    print "Error: %d: %s " % (e.args[0], e.args[1])
    sys.exit(1)

finally:
    if mysql_c:
        mysql_c.close()
```[I]Relevant links:

[http://docs.python.org/2/library/socket.html](http://docs.python.org/2/library/socket.html)
[http://mysql-python.sourceforge.net/MySQLdb.html](http://mysql-python.sourceforge.net/MySQLdb.html)[/I]

Wow!? Python code seen like quite easy...

---

