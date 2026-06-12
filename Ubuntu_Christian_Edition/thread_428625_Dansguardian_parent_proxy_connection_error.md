---
title: "Dansguardian parent proxy connection error"
date: 2007-04-30
forum: Ubuntu Christian Edition
---

### Post by SonicSteve on 2007-04-30
Hi folks,
I've found a few threads that have this problem mentioned, but none seem to mention how to fix it. So without further adieu here it is;

steve@ubuntu-desktop:~$ sudo dpkg-reconfigure dansguardian
Password:
 * Stopping DansGuardian dansguardian                                    [ OK ] 
 * Starting DansGuardian dansguardian                                        
   Error connecting to parent proxy
                                                                                                      [fail]
invoke-rc.d: initscript dansguardian, action "start" failed.


Does anyone know why this is happening? I've restarted the computer, and tried the dpkg command again. I've tried re-installing dansguardian using this command;
 sudo apt-get install dansguardian tinyproxy firehol

The result is that it tells me that nothing was updated or installed. It seems that dansguardian was installed, it just won't start.

I have followed this thread; [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008) 

I got to 2 E, and the error came up after running then dpkg command.

Setting up Dansguardian using Tinyproxy and Firehol on Ubuntu/Edubuntu

1. Ensure "universe repository" is activated and install packages:
sudo apt-get update
sudo apt-get install dansguardian tinyproxy firehol

Note: will probably need to reinstall dansguardian to overcome clamav config errors.

2. Edit: sudo gedit /etc/dansguardian/dansguardian.conf

a) Add comment (#) to:
#UNCONFIGURED

b) Turn off virus checking (if not wanted):
virusscan=off

c) Check that the following are set:
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

d) Save & exit.

e) Run:
**sudo dpkg-reconfigure dansguardian**

I can still access the internet and email, 
If anyone knows why this is happening I would really love your help.

I am running a dlink router but unless danguardian uses a special port to do it's thing I doubt that it's causing a problem.

---

### Post by rurouni.nz on 2007-10-19
I encountered exactly the same problem.

For me the fix was easy:

I changed the http_port option to "http_port 127.0.0.1:3128 transparent"

This made sense as all requests will come from the localhost to the localhost.

Rurouni.nz

---

### Post by Wiebelhaus on 2007-10-19
May I ask if dansgaurdian really works?

---

### Post by SonicSteve on 2007-10-26
You can ask but I never got installed. I should try again now since I've re-installed things since then.

---

### Post by alingham on 2009-05-06
I'm having issues with this too.
Only occurs after upgrading to 9.04. Worked fine in 8.10

Does anyone have a solution? 
I couldn't find any reference to http_port mentioned in previous post...

---

### Post by KIAaze on 2009-05-06
> **sx66gns said:**
> May I ask if dansgaurdian really works?
Yes it works.

"Error connecting to parent proxy" is usually caused by two things:
1)The proxy isn't running.
2)The proxy port number in dansguardian doesn't correspond to the port the proxy is listening to.

1)To check if the proxy is running, you can use:
```
ps aux | grep tinyproxy
``` (if you use tinyproxy)
```
ps aux | grep squid
``` (if you use squid)

2)To check which port the proxy is listening to if it's running:
```
sudo lsof -i
```
Check a specific port:
```
sudo lsof -i :3128
```

And if you want an easy dansguardian installation, you can try the GUI I'm working on:
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)
[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

Where the port numbers are configured:
/etc/dansguardian/dansguardian.conf:
```
proxyport = 3128
```
/etc/tinyproxy/tinyproxy.conf:
```
Port 8888
``` (this is most likely your problem since before the default was 3128 )
/etc/squid/squid.conf:
```
http_port 3128
```
/etc/squid3/squid.conf:
```
http_port 3128
```

To restart the services after making changes:
```
/etc/init.d/dansguardian restart
/etc/init.d/tinyproxy restart
/etc/init.d/squid restart
/etc/init.d/squid3 restart
```

---

### Post by ahalin on 2010-04-11
As usual it just won't work out of the box.

Back to OpenDNS and trying to make automatic IP address updates work....

---

### Post by KIAaze on 2010-04-11
Webcontentcontrol did not work out of the box for you?

---

### Post by david_kt on 2010-04-11
> **ahalin said:**
> As usual it just won't work out of the box.

Back to OpenDNS and trying to make automatic IP address updates work....

Try dansguardian gui from ubuntu-ce, should work out of the box using autoconfiguration option. Better still, use ubuntu ce.

DK

---

