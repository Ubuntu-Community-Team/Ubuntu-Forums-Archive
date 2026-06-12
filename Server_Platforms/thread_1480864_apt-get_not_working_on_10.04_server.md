---
title: "apt-get not working on 10.04 server"
date: 2010-05-12
forum: Server Platforms
---

### Post by jamesjwilsonsr on 2010-05-12
Details:
-New install
-Installed with http proxy however that detail was actually not necessary (subnet this VM is on doesn't need it, and actually can't use it).  
-I edited /etc/apt/apt.conf and changed the value to "false".
-I issued the command "http_proxy=" to blank out the env variable that was set for the http_proxy previously.  I cannot find anywhere that references the proxy info now.

Now, I don't know if my issues are related to that, but that is the only thing that was not the norm with this install (my first on this network, going to setup Zenoss or Nagios).

Anyhow, when I run apt-get install/update, I get a string of errors like the following:
```
Could not connect to us.archive.ubuntu.com:80, (91.189.92.167). - connect (111: Connection Refused [IP:91.189.92.167 80
as well as many of these:
Err http://us.archive.ubuntu.com/ubuntu lucid/main
and so on and so forth with all the sources 
```

I can ping 91.189.92.167, DNS is working because I can ping us.archive.ubuntu.com.  I can telnet out to several web servers on port 80 as well (though I cannot do the same to us.archive.ubuntu.com but am not sure if that is normal behavior or not).  
So my issue isn't network/routing nor is ithostname resolution/DNS.  My issue doesn't seem to be the proxy setting I undid as it it gets to the destination without it. 
I've Googled and Googled and searched here and found some things that led me to the steps I already have taken, but I still cannot install packages.

Any suggestions or help would be appreciated.

---

### Post by cdenley on 2010-05-12
```

echo -e "HEAD / HTTP/1.0\nHost: us.archive.ubuntu.com\n"|nc -q 1 -v -w 5 us.archive.ubuntu.com 80
grep -i proxy /etc/apt/apt.conf.d/*
grep -i proxy /etc/apt/apt.conf

```

---

### Post by jamesjwilsonsr on 2010-05-12
> **cdenley said:**
> 
echo -e "HEAD / HTTP/1.0\nHost: us.archive.ubuntu.com\n"|nc -q 1 -v -w 5 us.archive.ubuntu.com 80
nc: connect to us.archive.ubuntu.com port 80 (tcp) failed: connection refused
...6 times

> grep -i proxy /etc/apt/apt.conf.d/*
nothing

> grep -i proxy /etc/apt/apt.conf
```
Acquire::http::Proxy "false" ;
```


Thanks for the help so far :)

---

### Post by cdenley on 2010-05-12
> **jamesjwilsonsr said:**
> nc: connect to us.archive.ubuntu.com port 80 (tcp) failed: connection refused
...6 times


Definitely a networking problem. I can connect to the server just fine.
```

host us.archive.ubuntu.com
echo -e "HEAD / HTTP/1.0\nHost: us.archive.ubuntu.com\n"|nc -q 1 -v -w 5 91.189.88.46 80

```

---

### Post by jamesjwilsonsr on 2010-05-12
The weird thing is I can ping it and hit other sites using the command you supplied (such as our website or my home website...I just changed us.archive.ubuntu.com to our stuff, it worked)

But you are right, the problem, whatever it is, is on my end.
I'm sure there is a weird config in my organization somewhere.
We have a metro-ether link between our office and our corporate office, and our internet goes out through them.
They have an ISA server there but as I understand it there is very little filtering going on.  

After I set up a lucid desktop on another VLAN and was able to use apt-get successfully, I figured there was some sort of filtering going on unknown to me.  

The server was on a /23 vlan.  There is a DHCP range and a static range that splits the 512 addresses in half, 10.1.0.0/24 is dhcp and static on 10.1.1.0/24.  I switched the server to an IP on the static range and apt-get works now.

---

### Post by Spunner on 2010-05-13
I have exactly the same problem on my 10.04 desktop.

Everything has been working fine until now... I have made no changes to my setup (I've been too busy).

```
$ sudo apt-get update
Err http://au.archive.ubuntu.com lucid Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (202.158.214.106). - connect (111: Connection refused)
Err http://au.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_AU                                                                                       
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_AU                                                                                 
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_AU                                                                                   
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_AU                                                                                 
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com lucid-updates Release.gpg                                                                                                  
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_AU                                                                               
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_AU                                                                         
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_AU                                                                           
  Unable to connect to au.archive.ubuntu.com:http:
Err http://au.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_AU                                                                         
  Unable to connect to au.archive.ubuntu.com:http:
Get:1 http://dl.google.com stable Release.gpg [189B]                                                                                                        
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_AU                                   
Hit http://archive.canonical.com lucid Release.gpg                                         
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_AU
Ign http://deb.playonlinux.com lucid Release.gpg                     
Get:2 http://dl.google.com stable Release [2,540B]                   
Hit http://security.ubuntu.com lucid-security Release.gpg              
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_AU
Hit http://archive.canonical.com lucid Release                       
Get:3 http://dl.google.com stable/main Packages [904B]               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com lucid-security Release
Hit http://archive.canonical.com lucid/partner Packages
Ign http://deb.playonlinux.com/ lucid/main Translation-en_AU
Hit http://security.ubuntu.com lucid-security/main Packages
Get:4 http://deb.playonlinux.com lucid Release [1,722B]
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Ign http://deb.playonlinux.com lucid/main Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://deb.playonlinux.com lucid/main Packages
Hit http://deb.playonlinux.com lucid/main Packages
Fetched 3,634B in 2s (1,215B/s)
Reading package lists... Done
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (202.158.214.106). - connect (111: Connection refused)

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

```
$ echo -e "HEAD / HTTP/1.0\nHost: au.archive.ubuntu.com\n"|nc -q 1 -v -w 5 au.archive.ubuntu.com 80
nc: connect to au.archive.ubuntu.com port 80 (tcp) failed: Connection refused
nc: connect to au.archive.ubuntu.com port 80 (tcp) failed: Network is unreachable

$ echo -e "HEAD / HTTP/1.0\nHost: us.archive.ubuntu.com\n"|nc -q 1 -v -w 5 us.archive.ubuntu.com 80
Connection to us.archive.ubuntu.com 80 port [tcp/www] succeeded!
HTTP/1.1 200 OK
Date: Thu, 13 May 2010 17:04:46 GMT
Server: Apache/2.2.8 (Ubuntu)
Connection: close
Content-Type: text/html;charset=UTF-8

$ grep -i proxy /etc/apt/apt.conf.d/*
$ grep -i proxy /etc/apt/apt.conf
grep: /etc/apt/apt.conf: No such file or directory
$ grep -i proxy /etc/apt/apt.conf/*
grep: /etc/apt/apt.conf/*: No such file or directory

```

So, I can't access my Australian repositories, but I can access the us ones... strange...

---

### Post by arrrghhh on 2010-05-13
Can you ping au.archive.ubuntu.com?  You could also try a different mirror, although it's almost certainly something blocking it within your network/provider.

---

### Post by cdenley on 2010-05-13
That mirror, hosted by AARNET, is down.

---

### Post by Spunner on 2010-05-13
Oh yeah, I can ping it fine... I got my updates by changing to the main repo.

EDIT: thanx... I'll change back in the morning.

---

### Post by TaylorHxx on 2011-03-03
I am having the same problem as jameswilson. Same situtuation except I have changed no conf files. The "echo" returns the same results as jameses but the "grep" returns "no such file or directory". My internet connection is up. The server is a dmz host on my router and has a static NAT in my router to translate my public ip address to the private address of my server and i have assigned my server a static lease on my router. I have also forwarded all incoming requests on port 80 and 8080 to my server, though i believe this is redundant since it is dmz. In addition to forwarding ports 80 and 8080 if have set a rule to redirect incoming request on port 81 to port 80 so i can view the webpage from the wan side of my router on my home network instead of my routers web-access page. I had the same router configuration set on a desktop to allow it to serve a web page and apt-get still worked fine so I believe this is a problem with apt-gets conf file or sources list. Sorry if I am unclear i a NooB at networking and have only been working with linux for ~six months now. Please help and thank you in advance.

Sorry i have not set up the port 81 redirect on this setup. also i can not ping anything from my server but i can ping from my desktop. any ideas what might be blocking my connections? p.s. although i am having trouble with outgoing connections my web page is being served properly and i will be checking if ssh works off my home network later tonight

Sorry for wasting your forum space I resolved my problem after viewing my firewall log on my router. Seems the problem was with the static NAT after disabling that my connections go through fine. 

The security log read read Outgoing traffic: Blocked - NAT error: no free NAT IP.  although my problem is resolved now it would be nice if someone could explain this error to me and why it occurred for my future reference.

---

