---
title: "Script to keep ip address and update on Database"
date: 2013-10-17
forum: Server Platforms
---

### Post by kwN7kft on 2013-10-17
Hi there,


I'm using a dynamic Ip and I would like to make some script to ping the address and keep on a file.
   Then I would make an update on database changing ip address.
Is there anyone that could help ?

I'm using ubuntu server 12.04 LTS and the database it's mysql 5.5

Thanks in advanced.

---

### Post by houstonbofh on 2013-10-17
wget -O - -q icanhazip.com

You can pipe this to a file, or a database, or script it however you want.

---

### Post by drmrgd on 2013-10-17
You could get your IP address alone by piping ifconfig to a perl oneliner and then redirect that to a file:

```

$ ifconfig eth0 | perl -e '($ip) = map { /inet addr:(\d+\.\d+\.\d+\.\d+).*/ } <>; print "$ip\n"' >> ipaddress.txt

```

I'm assuming that you're using eth0 as your main network device.  That should capture the IP address string and writing to a file called ipaddress.txt.  You could get fancier with adding the date string and such too if you wanted.

Edit:
forgot the example:

```

$ ifconfig eth0 | perl -e '($ip) = map { /inet addr:(\d+\.\d+\.\d+\.\d+).*/ } <>; print join( "\t", scalar localtime(), $ip ), "\n"' 
Thu Oct 17 18:31:27 2013        192.168.1.6

```

---

### Post by kwN7kft on 2013-10-18
Hi there,


Thanks for the answers, the commands are awesome and then I could made the update with some script like :

But to update then I must read text file to update on database, and for update could it be something like this:

> con=mysqli_connect("db1");

if mysqli_connect_errno()
   {
    echo "Failed to connect" . mysqli_connect_error();
   }
mysqli query ($con,"Update table1 Set IP=(value from text file where ip is kept) where ip=123.123.123.123

mysqli_close($con);



Is there any other method more simpler than that ?
Could it be more liable insert the  ip on table at the same time that he reads the ip?

---

### Post by Habitual on 2013-10-18
```
mysqli query ($con,"Update table1 Set IP=$(curl icanhazip.com) where ip=123.123.123.123
```perhaps?

---

### Post by steeldriver on 2013-10-18
For a simple update, it should be practical to do it all from the shell I think e.g.

```
mysql -u*user* [-p*password*] -D*database* -e "UPDATE *yourtable* SET ip = \"$IP\" WHERE *somefield* = *somevalue*"
```

---

### Post by kwN7kft on 2013-10-19
Hi there,

Thanks 

I think in the end I could have a script something like this.

#bash

[COLOR=#000000]wget -O - -q icanhazip.com
mysql -u user [-ppassword] -Ddatabase -e "Update [/COLOR][COLOR=#000000]your table SET ip=\"$IP\" Where some field = some value"

Is this possible ?
Or using mysql with curl option could be more simple ?

Thanks in advanced.

[/COLOR]

---

### Post by drmrgd on 2013-10-19
I don't know SQL at all.  But, I think that approach can work if you store the IP address you get from 'icanhazip.com' in the variable $IP prior to calling the mysql command:

```

#!/bin/bash

IP=$(curl icanhazip.com)
mysql -u user [-ppassword] -Ddatabase -e "Update your table SET ip=\"$IP\" Where some field = some value"


```

---

### Post by kwN7kft on 2013-10-19
HI there,

using curl as mentioned I got the following 

% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:15 --:--:--     0 0curl: (7) couldn't connect to host

And no ip returned to keep it in variable ?

Tried to -4 parameter result is the same .

---

### Post by hawkmage on 2013-10-19
Unfortunately curl will change it's output if it is not going to a terminal device, try the "-s" option on curl.

---

### Post by kwN7kft on 2013-10-19
So I used dig

The final if someone wants to use it:

#!/bin/bash


IP=$(dig +short )
mysql -u user -ppass -D your database -e "Update your table from db SET (field of table of DB indicating ip to change) ='$IP' where  table of DB='Value to identify the modification on DB'"

Thanks
to all
Topic to close

---

### Post by hawkmage on 2013-10-19
It is odd that the dig command gives you your IP.  With no host to resolve I get the root DNS server names:
```
hawkmage@ubuntults:~$ dig +short
d.root-servers.net.
e.root-servers.net.
c.root-servers.net.
g.root-servers.net.
l.root-servers.net.
i.root-servers.net.
k.root-servers.net.
h.root-servers.net.
a.root-servers.net.
m.root-servers.net.
b.root-servers.net.
j.root-servers.net.
f.root-servers.net.
```

---

### Post by kwN7kft on 2013-10-20
You are right,

Missing host 

[COLOR=#000000]#!/bin/bash[/COLOR]


[COLOR=#000000]IP=$(dig +short  <Host of dynamic ip> )[/COLOR]
[COLOR=#000000]mysql -u user -ppass -D your database -e "Update your table from db SET (field of table of DB indicating ip to change) ='$IP' where table of DB='Value to identify the modification on DB'"

That's it

thanks once again.



[/COLOR]

---

### Post by kwN7kft on 2013-10-22
Hi there,

Keep thinking If I keep ip compare it and then if different make update if not different get out of cicle

---

