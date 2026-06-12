---
title: "Using apache2"
date: 2011-05-03
forum: Server Platforms
---

### Post by Avamander on 2011-05-03
I have installed
apache2,
apache2-mpm-prefork,
apache2.2-bin,
apache2-utils,
apache2.2-common.

Is there a php,mysql built in?
What folder do i put my website?
What command do i need to use to start and stop apache?
If there isnt php,mysql built in how do i install it ?

---

### Post by usatonycuba on 2011-05-03
```
sudo apt-get install lamp-server^
```The above code install the whole LAMP: Linux - Apache - MySQL - PHP

[COLOR=Black]Restart[/COLOR]  Apache with the following terminal command:
```

sudo /etc/init.d/apache2 restart


```Stop Apache with the following terminal command:
```
sudo /etc/init.d/apache2 stop
```Your web site should be (With LAMP installed) at...  [COLOR=DarkRed]**/var/www/**[/COLOR]

---

### Post by satanselbow on 2011-05-03
Hey usatonycuba,

Does that apt-get leave you with the same LAMP stack you would get through **tasksel?**

Just asking cos that was gonna be my answer ;)

---

### Post by usatonycuba on 2011-05-03
> **Avamander said:**
> I have installed
apache2,
apache2-mpm-prefork,
apache2.2-bin,
apache2-utils,
apache2.2-common.

Is there a php,mysql built in?
What folder do i put my website?
What command do i need to use to start and stop apache?
If there isnt php,mysql built in how do i install it ?

> **satanselbow said:**
> Hey usatonycuba,

Does that apt-get leave you with the same LAMP stack you would get through **tasksel?**

Just asking cos that was gonna be my answer ;)

I think the answer to your **tasksel** question would be the question of @Avamander... There is wtho separate things.

Edited:
concerning to ```
sudo apt-get install lamp-server^
```... That will be install  the whloe LAMP (including commons, and on.....).. Also i guess that I will NOT recomend using TASKSEL to a beginner:

> **WARNING:** Use tasksel **only** to **install** tasks, **never** to **remove** any! According to [https://launchpad.net/bugs/574287](https://launchpad.net/bugs/574287) it will remove each package in the list of that task (and possibly render your **system unusable**).  ...So, based on the question of the topic, my answer would be: use [COLOR=DarkRed]sudo apt-get install lamp-server^[COLOR=Black] ... where [/COLOR][/COLOR]caret (^) was generally required at the end of the command in older  versions of tasksel. It is not required in newer versions of tasksel. [COLOR=DarkRed]...BUT... [COLOR=Black]using just the apt-get code as I did recommend ..it will be install "[/COLOR][/COLOR]everything he needs" [COLOR=DarkRed][COLOR=Black]by a [/COLOR][/COLOR]simple-minded[COLOR=DarkRed][COLOR=Black] way[/COLOR]
[/COLOR]

---

### Post by Avamander on 2011-05-05
When i started it it gives me :```

sudo /etc/init.d/apache2 restart
[sudo] password for Avamander: 
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

---

### Post by jramshu on 2011-05-05
Are you installing this on a machine with a desktop?
I got mine up and running twice with no errors by using the Ubuntu Server cd, no desktop. I say twice because as I was learning I tinkered with too much stuff on there and did a clean install again just to make sure I hadn't opened any vulnerabilities.

EDIT: Have you gone through the server manual. It's a little long, but very useful. I also referenced unixmen too.


[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
[http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat)

---

### Post by satanselbow on 2011-05-05
> **Avamander said:**
> 
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName


In a terminal:

```
sudo gedit /etc/apache2/httpd.conf
```

Which will open the already existing but empty file

Type the following line and save:

```
ServerName  localhost
```

Then restart apache as before:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by Avamander on 2011-05-05
if i have a domain name (moodul.dyndns.org) then what

---

### Post by usatonycuba on 2011-05-05
> **Avamander said:**
> if i have a domain name (moodul.dyndns.org) then what
Can you Type the result of
```
hostname
```
Please.

EDITED:

Before do any change to your files... make sure to [COLOR="DarkRed"]back[/COLOR] - [COLOR="DarkRed"]it[/COLOR] - [COLOR="DarkRed"]up[/COLOR] first..!!

If you are behind a Router you should give a static address to your Server Machine first.. tha will be at network/interfaces ..(you have to make sure to enter the correct information (values) from - your settings).. it will be:

 ```
nano /etc/network/interfaces 
```


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static         
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 192.168.1.1

```
then:

 ```
/etc/init.d/networking restart
``` 

Now go ahead and:

 ```
nano /etc/hosts
``` 



```
127.0.0.1       localhost.localdomain   localhost
192.168.1.100   moodul.dyndns.org     moodul.dyndns

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```


 ```
echo moodul.dyndns.org > /etc/hostname 
```

```
 /etc/init.d/hostname restart 
```
 
```
 hostname 
```

```
 hostname -f 
```

```
/etc/init.d/apache2 restart
```

---

### Post by Avamander on 2011-05-06
```
Avamander@Koduarvuti:~$ sudo echo moodul.dyndns.org > /etc/hostname
bash: /etc/hostname: Permission denied
```

---

### Post by usatonycuba on 2011-05-06
> **Avamander said:**
> Avamander@Koduarvuti:~$ sudo echo moodul.dyndns.org > /etc/hostname
bash: /etc/hostname: Permission denied
```

Avamander@Koduarvuti:~$ sudo su
enter your pass

```

Still don't go ?

---

### Post by Avamander on 2011-05-13
@jramshu    Yes i use machine with desktop

@usatonycuba    Hostname result :```
Koduarvuti
```

---

