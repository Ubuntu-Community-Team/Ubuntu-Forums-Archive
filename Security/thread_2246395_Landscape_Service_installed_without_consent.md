---
title: "Landscape Service installed without consent"
date: 2014-09-29
forum: Security
---

### Post by intuition2 on 2014-09-29
A programmer helped me to install Ubuntu on my laptop, and without my consent he installed the Landscape Service.
When I asked him what it was I was told it was a simple tool to change the background, and I can find the icon on the System Settings.
I found it weird and later checked it out and soon realized it could be a risk, for I didn't ask for any remote assistance.

When I try to open it the following message appears:

"System Policy prevents you from reading and writing landscape client Settings.
An application is attempting to perform an action that requires privileges.

Authentication is required to perform this action"

Ask for password - I insert it - and try to authenticate it

But then a message pops out on the top right corner saying "Landscape management service - Authentication failed"

Is it possible to know if someone is monitoring my laptop and if my information is at risk through the Landscape Service?!

Thanks for your consideration.

---

### Post by Elfy on 2014-09-30
unmerged from [http://ubuntuforums.org/showthread.php?t=2245891](http://ubuntuforums.org/showthread.php?t=2245891)

Keep this thread ontopic for this only

---

### Post by tgalati4 on 2014-09-30
It is a remote monitor application.  You should have root privileges to remove it:

> tgalati4@Mint14-Extensa ~ $ apt-cache search landscape
landscape-client - The Landscape administration system client
landscape-client-ui - The Landscape administration system client - UI configuration
landscape-client-ui-install - The Landscape administration system client - UI installer
landscape-common - The Landscape administration system client - Common files


Perhaps he thought it would help if technical issues came up, he could log in to fix them.

It's your computer.  Do what you want.  Put stickers on it.

---

### Post by thnewguy on 2014-09-30
Landscape is a monitoring service so your programmer is not being honest with you. Assuming your user has admin access you can remove Landscape using the command
```

apt-get remove landscape-client landscape-common

```

If that does not work, then you should probably consider your machine compromised. Your next steps would be to backup any files you have on the computer and re-install Ubuntu.

---

### Post by Bucky Ball on 2014-09-30
Or possibly:

```
**sudo** apt-get remove landscape-client landscape-common
```

;)

But like thnewguy said ...

---

### Post by fugu2 on 2014-10-01
> **Bucky Ball said:**
> ```
sudo apt-get **purge** landscape-client landscape-common
```the purge command will not just uninstall the package(s), but also remove and configuration files that are associated with the packages

---

### Post by Bucky Ball on 2014-10-01
> **fugu2 said:**
> the purge command will not just uninstall the package(s), but also remove and configuration files that are associated with the packages

Completely aware of that, and fixable if that is the case and anything essential is removed, which may not be the case ...

---

### Post by intuition2 on 2014-10-01
I've installed ubuntu on another system now, so I would like to dig more this subject about Landscape before deleting it. 
I would like to discover some evidence that he really did it.

Is there anyway to check out more about it? 

I've tried to find the configuration files (I've also tried with sudo but it didn't work either... Don't know if I'm doing it right!):

Me@Mine:~$  /etc/landscape/client.conf
bash: /etc/landscape/client.conf: Permission denied

Me@Mine:~$ landscape-config
error: config file /etc/landscape/client.conf can't be read

Me@Mine:~$  /var/log/landscape/sysinfo.log
bash: /var/log/landscape/sysinfo.log: Permission denied

Me@Mine:~$ ~/.landscape/sysinfo.log
bash: /home/sofia/.landscape/sysinfo.log: Permission denied

Anyone know what does it mean?

Thanks everyone!

---

### Post by Doug S on 2014-10-01
> **intuition2 said:**
> Is there anyway to check out more about it?I have never used landscape, but will make some comments below anyhow.> **intuition2 said:**
> 
Me@Mine:~$  /etc/landscape/client.conf
bash: /etc/landscape/client.conf: Permission deniedIt is not an executable file. So even with "sudo" you will have troubles. You could open it with and editor (I prefer nano, but you can use your preferred editor), or list out the file using"cat". Depending on the file permissions, I would do this:```
sudo nano /etc/landscape/client.conf
``` or ```
sudo cat /etc/landscape/client.conf | more
```(Note: Depending on file permissions, the "sudo" may or may not be needed)> **intuition2 said:**
> Me@Mine:~$ landscape-config
error: config file /etc/landscape/client.conf can't be readI don't know for sure, but it seems to me this one should be:```
Me@Mine:~$ sudo landscape-config
```> **intuition2 said:**
> Me@Mine:~$  /var/log/landscape/sysinfo.log
bash: /var/log/landscape/sysinfo.log: Permission deniedSame as above: Not an executable. Use an editor or cat or whatever.> **intuition2 said:**
> Me@Mine:~$ ~/.landscape/sysinfo.log
bash: /home/sofia/.landscape/sysinfo.log: Permission deniedSame as above: Not an executable. Use an editor or cat or whatever.> **intuition2 said:**
> Anyone know what does it mean?Yes, respectfully, you need to study up some about the very basics. I do not know a good basic reference, but perhaps someone will chime in with a link to one.

---

### Post by bashiergui on 2014-10-02
> [FONT=UICTFontTextStyleBody]I would like to discover some evidence that he really did it[/FONT]
[FONT=UICTFontTextStyleBody]Is there anyway to check out more about it? [/FONT]What more are you looking for? You're certain you didn't install landscape and the programmer told you he installed it. Case closed.

If you want more read the [landscape user guide]("http://landscape.canonical.com/static/doc/user-guide/"). Maybe you can figure out how to initiate a connection of your computer to the server... his server. Then you can look in your firewall logs to see what his IP is. You could look through all your logs for connections to that IP to determine how often he connected.

---

### Post by tgalati4 on 2014-10-02
Look in /var/log/auth.log and /var/log/auth.log.1 to see external connections to your machine.  Post any that you don't understand.  Don't post the entire file.

IT folks tend to do things that can make others feel paranoid, but they are conditioned to make their life easier.  I would assume that your system has been compromised, but not for evil purposes--unless you find direct evidence for it.  If you take your car in to get your oil changed at a Quick-Change Oil Mart, and they forget to tighten the drain plug and you lose oil, who's fault is it?

---

### Post by intuition2 on 2014-10-02
When I try to remove or purge this is what happens:

```
Me@Mine:~$ apt-get remove landscape-client landscape-common
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Me@Mine:~$ sudo apt-get remove landscape-client landscape-common
[sudo] password for Me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  python-configobj python-twisted-names
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  landscape-client landscape-client-ui landscape-common
0 upgraded, 0 newly installed, 3 to remove and 26 not upgraded.
After this operation, 1193 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
Me@Mine:~$ sudo apt-get purge landscape-client landscape-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  python-configobj python-twisted-names
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  landscape-client* landscape-client-ui* landscape-common*
0 upgraded, 0 newly installed, 3 to remove and 26 not upgraded.
After this operation, 1193 kB disk space will be freed.
Do you want to continue? [Y/n] 
```

So I guess it must a good sign that at least I can do this!...

Now figuring out a way "to initiate a connection of *my* computer to the server... his server", that would be perfect! I think that's exactly what I need! But since I wasn't able to log in, because it didn't accept my password, and the only other option was to create a new account on Landscape...But can't see nothing there! I've also asked for help directly to Landscape Services, and I'm still waiting!..

[And, yes, you're right! It looks like I have a long way ahead of me, still... I  hope it's not too late to start learning one more new language. I'm very  thankful for all your help! (I'll take a look at [http://ss64.com/bash/](http://ss64.com/bash/)) ]

---

### Post by Bucky Ball on 2014-10-02
Please run these commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You have unrequired stuff you can get rid of and updates and upgrades you should probably do before going much futher. Also, please use [code][/ code] tags around code. Makes it neater and much easier to read as it keeps the original formatting (I have added them to your last post and code). Cheers. ;)

---

