---
title: "Is Bastille necessary for hardening?"
date: 2010-07-16
forum: Security
---

### Post by wacky_sung on 2010-07-16
I just ponder can anybody shed some light to me how to manually disable service such as FTP,SSH,etc in which Bastille is doing.If all the services can be manually disable,which mean Bastille is just a tool to help newbies like me to use it.

---

### Post by cdenley on 2010-07-16
I don't know much about Bastille, but I'm sure everything it does can be done manually. It does much more than disabling services, though. There should be no network services such as FTP or SSH running unless you installed them.

---

### Post by wacky_sung on 2010-07-16
Yeah,probably you can tell the steps to disable FTP,SSH,Clear text,etc manually.Currently i am using Bastille to do all those tasks for me :( In this way,it help me has a better understanding of Ubuntu which is very new to me.

[http://www.bastille-unix.org/](http://www.bastille-unix.org/)

---

### Post by cdenley on 2010-07-16
> **wacky_sung said:**
> Yeah,probably you can tell the steps to disable FTP,SSH,Clear text,etc manually.Currently i am using Bastille to do all those tasks for me :( In this way,it help me has a better understanding of Ubuntu which is very new to me.


You would probably be much better off reading the sticky.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

You shouldn't try "hardening" your system unless you fully understand what you are doing. You might break something.

---

### Post by wacky_sung on 2010-07-16
Thank for your advise.In fact i have read that countless times.I still prefer using hardening process before even proceed with IDS.IF you hardened Ubuntu and move to IDS give you a better security as what i personally feel.

Just like people using like to use SSH or FTP to hack but you have disable the services which make it even tougher for them to root you.

---

### Post by cdenley on 2010-07-16
> **wacky_sung said:**
> Just like people using like to use SSH or FTP to hack but you have disable the services which make it even tougher for them to root you.

That is why there are no network services installed by default, so there shouldn't be any disabling needed.

Ubuntu should be secure out-of-the box. As long as you don't misconfigure your system, hardening shouldn't be necessary. Bastille may do a little extra, but you're probably better off not trying it unless you understand what it is doing in my opinion. I don't think any "newbies" should even touch Bastille. The changes Bastille makes aren't there by default for a reason.

---

### Post by wacky_sung on 2010-07-16
Actually i am aware of what i am doing inspite i am new using Bastille.I have disable bastille firewall by default it will load during startup manually.Thank you so much for your concern.I wanna learn something in depth of Ubuntu Operating System which may run like OpenBsd concept.

[http://www.openbsd.org/](http://www.openbsd.org/)
[http://www.openbsd.org/security.html](http://www.openbsd.org/security.html)
```
To ensure that novice users of OpenBSD do not need to become security experts overnight (a viewpoint which other vendors seem to have), we ship the operating system in a Secure by Default mode. All non-essential services are disabled. As the user/administrator becomes more familiar with the system, he will discover that he has to enable daemons and other parts of the system. During the process of learning how to enable a new service, the novice is more likely to learn of security considerations.
```

Hopefully i do not violate the rules here by posting another distro.If so, you can remove it.Thank.

---

### Post by cdenley on 2010-07-16
Ubuntu uses the same concept, as I've said repeatedly. There are no services or daemons that you need to disable unless you enabled/installed them.

---

### Post by wacky_sung on 2010-07-16
Probably you can tell me how to manually check if the FTP, SSH ,etc service has been enabled or not.Even by default, the demon is disable but how do you manually verify it apart from port scanning.

---

### Post by cdenley on 2010-07-16
> **wacky_sung said:**
> Probably you can tell me how to manually check if the FTP, SSH ,etc service has been enabled or not.Even by default, the demon is disable but how do you manually verify it apart from port scanning.

You can list all listening processes
```

sudo netstat -tulnp

```
If you have a desktop install, that will include a CUPS server only listening on 127.0.0.1, and [avahi]("http://en.wikipedia.org/wiki/Avahi_%28software%29") listening on a UDP port. If you use DHCP, then your DHCP client will also be listening UDP port 68.

---

### Post by wacky_sung on 2010-07-16
Thank but somehow you only show me how to see listening port but not to disable a daemon / service.

Example, the SSH port is open and can you show me how to disable the daemon without uninstalling it.

Hopefully you get what i mean.

---

### Post by bodhi.zazen on 2010-07-16
> **wacky_sung said:**
> I just ponder can anybody shed some light to me how to manually disable service such as FTP,SSH,etc in which Bastille is doing.If all the services can be manually disable,which mean Bastille is just a tool to help newbies like me to use it.

The biggest "problem" with Bastille, it is fairly generic, and it is easy to break Ubuntu the first few times you run it.

If you understand what you are doing and what the options mean, it works "OK".

If you do not understand the option(s), you really need to read the documentation.

IMO you are better off learning :

Apparmor
Snort
iptables

and reading the appropriate security information on the services you run.

IMO security is a process and the biggest "problem" with Bastille is it seems to promote an install in and forget it mentality.

I think

Learn to secure it -> Install it -> secure it -> bring it on line -> monitor it 

Despite those philosophical differences, if you want to try Bastille go for it, but, as I said, it is fairly generic, there are a few options that do not work, and it is easy to break Ubuntu if you choose the wrong option.

---

### Post by cdenley on 2010-07-16
> **wacky_sung said:**
> Thank but somehow you only show me how to see listening port but not to disable a daemon / service.

Example, the SSH port is open and can you show me how to disable the daemon without uninstalling it.

Hopefully you get what i mean.

I can't imagine why you would want a disabled service installed, but in ubuntu 10.04, you can disable a service by renaming the upstart configuration file to a different file extension.
```

sudo mv /etc/init/ssh.conf /etc/init/ssh.disabled

```
Hardening tools may assume you use sysv, not upstart, and may attempt to disable services by removing symlinks in /etc/rc?.d. This will not work in ubuntu 10.04 for most services.

---

### Post by bodhi.zazen on 2010-07-16
> **wacky_sung said:**
> Thank but somehow you only show me how to see listening port but not to disable a daemon / service.

Example, the SSH port is open and can you show me how to disable the daemon without uninstalling it.

Hopefully you get what i mean.

sudo service ssh stop

To stop it from running at boot, edit nano /etc/init/ssh.conf

change the start on ...
stop on ...

to the behavior you want.

---

### Post by wacky_sung on 2010-07-16
> **bodhi.zazen said:**
> The biggest "problem" with Bastille, it is fairly generic, and it is easy to break Ubuntu the first few times you run it.


IMO security is a process and the biggest "problem" with Bastille is it seems to promote an install in and forget it mentality.

I think

Learn to secure it -> Install it -> secure it -> bring it on line -> monitor it 


Indeed i agree with you in some ways but i have already installed and reinstalled several times before it finally work for me.I do like Bastille as the tools work perfectly for me.I am using it only for desktop but not server.So far it working good for me.

Apparmor - I have read your posting regarding Apparmor but i face  some problem to disable enforce.It only can change from complain to enforce or via vera but if you wanna disable both is only by disable a profile.I try to enforce firefox but it lock out the java which i totally cannot run with site running with java.

Snort - I am yet to go much indepth or installed it.

Iptables - I have learned the basic but not sure how much more is  require to go about writing a good firewall script.As you have seem those other posting of iptables are those accumulated from difference sources / rewritten by me.

---

### Post by wacky_sung on 2010-07-16
> **cdenley said:**
> I can't imagine why you would want a disabled service installed, but in ubuntu 10.04, you can disable a service by renaming the upstart configuration file to a different file extension.
```

sudo mv /etc/init/ssh.conf /etc/init/ssh.disabled

```
Hardening tools may assume you use sysv, not upstart, and may attempt to disable services by removing symlinks in /etc/rc?.d. This will not work in ubuntu 10.04 for most services.

Probably you can tell me what is the upstart configuration file location?

Is that below by manually using gedit to change it?

[https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes)

```
/etc/event.d no longer used
The version of upstart included in Ubuntu 9.10 no longer uses the configuration files in the /etc/event.d directory, looking to /etc/init instead. No automatic migration of changes to /etc/event.d is possible. If you have modified any settings in this directory, you will need to reapply them to /etc/init in the new configuration format by hand. (402759)
```

---

### Post by cdenley on 2010-07-16
> **wacky_sung said:**
> Probably you can tell me what is the upstart configuration file location?

For SSH? We already told you.
/etc/init/ssh.conf
Each service has its own upstart configuration file in that directory, with a .conf file extension. Renaming it to a different extension as I suggested prevents upstart from reading it, therefore prevents upstart from loading the service.

> **wacky_sung said:**
> 
Is that below by manually using gedit to change it?

Yes, that or any text editor you prefer. Did you make changes to upstart configuration files in previous versions of ubuntu then upgrade?

---

### Post by cariboo on 2010-07-16
I thought Bastille had been abandoned, according to the web site, it was supposed to be updated in 2008, but there is no sign of an update for Debian based distros.

---

### Post by wacky_sung on 2010-07-17
I do a full format for the upgrade from previous to current 10.04.Many thank to those who help.

---

