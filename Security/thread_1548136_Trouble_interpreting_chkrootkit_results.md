---
title: "Trouble interpreting chkrootkit results"
date: 2010-08-07
forum: Security
---

### Post by i_dont_know_what_im_doing on 2010-08-07
Since I'm kind of paranoid, I decided to run chkrootkit today, and I'm having trouble interpreting the results. Pretty much everything said not infected or not found, etc, except for a few results:  
```
Checking `syslogd'... not tested
```(any particular reason this wasn't tested?)

Next, I got this:
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/xulrunner-1.9.2.8/.autoreg /usr/lib/jvm/java-1.5.0-gcj-4.4/.java-gcj-4.4.jinfo /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/jvm/java-6-sun-1.6.0.16/.systemPrefs /usr/lib/thunderbird-3.0.6/.autoreg /usr/lib/firefox-3.6.8/.autoreg /usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit

After a bit of Googling, it sounds like chkrootkit has something against hidden files in root folders and incorrectly flags them as dangerous. However, most of the forum threads I saw had shorter lists of "suspicious files." I'm assuming these are harmless anyway?

This is the main part that I'm confused about:
```
Checking `chkutmp'... The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root          943 tty7   /usr/bin/X -nr -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-TkMiPb
! (myusername)       3406 pts/1  /bin/bash
! root         3572 pts/1  /bin/sh /usr/sbin/chkrootkit
! root         6142 pts/1  ./chkutmp
! root         6144 pts/1  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         6143 pts/1  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
```I've been searching for information about this, but haven't found anything conclusive. A few forum threads listed something similar to that, but only one or two processes listed. I have 6 listed there. It also seems kinda weird that I'm seeing things like "/bin/sh /usr/sbin/chkrootkit" and "./chkutmp" there. Chkrootkit found out that it's hiding its own processes? Some of the other processes look complicated and didn't turn up any Google results. What should I make of this?

Random information: I originally installed Kubuntu 7.04, then later did a clean install (but kept my /home partition intact) of Kubuntu 8.10, and since then, I've upgraded every 6 months and am currently using Kubuntu 10.04. I've installed a few .debs (eg., Skype, Google Picasa, ...a few others I can't recall at the moment), and compiled a few programs, but I'm fairly sure I haven't installed anything dangerous. I've tried to mostly use stuff from the repositories.

Are there any applications that scan my entire computer, tell me I'm fine, and then tell me to stop worrying about malware? :p

Edit: This is kinda unrelated, but I'll ask it anyway in case anyone knows. A few weeks ago, our power went out a few times. Ever since then, my computer displays a "checking drives for errors..." screen while booting up, about 1 in every 10 boot-ups. Usually this screen takes about a minute, but occasionally takes up to ~30 minutes. So far, it has only once displayed a "A problem has been found" message, and asked me to press a keyboard key to fix it, and I assume it fixed it. Is there something I should do about this?

Thanks :)

---

### Post by cariboo on 2010-08-08
The first thing to do is rid your mind of the misconception that Ubuntu is like windows. The only place malware can be installed with out root privileges is your home directory, as a normal user, you don't have any permissions to change/install anything out side of the home directory.

The second thing to do is only install packages from trusted sources, usually the repositories/ppa's. Anything you install from anywhere else is suspect. One of our members downloaded a .deb packaged theme from gnome-look.org, fortunately he suspected something was strange, and posted in the forums before installing it.

Third, don't run as root all the time, you can do more damage to the system yourself than most malware can.

Fourth read the security stickies at the top of this page, they can help you secure your system.

You don't need to run utilities like rkhunter and chkrootkit, unless you suspect your system is doing something it shouldn't. The files chkrootkit found are all normal parts of the os. The best thing for your peace of mind is to learn as much about Ubuntu as you know about windows.

Relax and have fun.

[b]Edit:{/b} For your partition problem, boot from the Live CD, and once at the desktop open a terminal and type:

```
fsck -y /dev/sdX
```

where X is the partition you are having the problem with. The above command will check/repair your file system.

---

### Post by i_dont_know_what_im_doing on 2010-08-08
Thanks for the reply. I guess I was just overreacting because I didn't know what it meant. My main concern is that at some point I might have haphazardly installed a shady .deb or program before I realized they could potentially be dangerous, or did something stupid as root. This is why I was hoping to run a program that would check for problems.

You say that the only place something harmful can be installed is my home directory (without root perms). Will scanning /home with ClamAV protect me from that? A lot of my documents were copied from my old XP system, so I wouldn't want to "inherit" anything from there. I'm aware that Windows viruses can't really run under Ubuntu, but what if I ran something with Wine? Somehow a Windows program I installed put desktop icons on my Ubuntu desktop, so I assume they could theoretically infect /home files? 

Another thing is, I have Apache and MySQL installed so I can test a few php files. I try to write clean, secure code, but I can't guarantee that I haven't written something that could be exploited. I've set Apache to only listen to 127.0.0.1:80, and set UFW to deny everything incoming, and my router presumably has a firewall, so I assume this doesn't cause any security problems? I just realized that I've been letting php use the root MySQL account, and assumed it was okay because it was just a development server, but now that I think about it, I should probably go change that now. :/

Also, how would I "suspect my system is doing something it shouldn't"? I thought the idea is that these things try to run seamlessly in the background, so I'm not sure how I would notice them. I suppose I could try reading logs, but I don't really understand them. Plus that seems like a lot of maintenance, especially when all I really want to do is browse the web/do word processing/write a few scripts. Am I just being too lazy?

I have read the security stickies, but I guess it would be a good idea to go review them. Sorry for the wall of text... I'm just curious about these things. Thanks for teaching me more about Ubuntu. :)

---

### Post by cariboo on 2010-08-09
> Thanks for the reply. I guess I was just overreacting because I didn't know what it meant. My main concern is that at some point I might have haphazardly installed a shady .deb or program before I realized they could potentially be dangerous, or did something stupid as root. This is why I was hoping to run a program that would check for problems.

There is nothing that can scan for mistakes you've made, I would suggest until you get more familiar with Ubuntu, keep a log of the changes you make to the system.

> You say that the only place something harmful can be installed is my home directory (without root perms). Will scanning /home with ClamAV protect me from that? A lot of my documents were copied from my old XP system, so I wouldn't want to "inherit" anything from there. I'm aware that Windows viruses can't really run under Ubuntu, but what if I ran something with Wine? Somehow a Windows program I installed put desktop icons on my Ubuntu desktop, so I assume they could theoretically infect /home files? 


Viruses in wine will only affect your wine directory, and can't propigate through the rest of the system. The big thing to do is ensure that the wine directory isn't linked to your Windows partition in any way. ClamAV supposedly will scan for Linux viruses, but there aren't any in the wild at the moment.

> Another thing is, I have Apache and MySQL installed so I can test a few php files. I try to write clean, secure code, but I can't guarantee that I haven't written something that could be exploited. I've set Apache to only listen to 127.0.0.1:80, and set UFW to deny everything incoming, and my router presumably has a firewall, so I assume this doesn't cause any security problems? I just realized that I've been letting php use the root MySQL account, and assumed it was okay because it was just a development server, but now that I think about it, I should probably go change that now. :/

If you don't have port 80 port-forwarded through your router, so that there is no external (internet) access to the the web server you are pretty will safe, and can basically do whatever you want. I've been running a server for years, that has no access from the wild, and have never experienced any problems other than those of my own making. :)

> Also, how would I "suspect my system is doing something it shouldn't"? I thought the idea is that these things try to run seamlessly in the background, so I'm not sure how I would notice them. I suppose I could try reading logs, but I don't really understand them. Plus that seems like a lot of maintenance, especially when all I really want to do is browse the web/do word processing/write a few scripts. Am I just being too lazy?

Truthfully I'm kind of lazy, so I only run the occasional port scan from a different system on my internal network. The services I run http, ssh internally never get access to the internet. 

I don't run a firewall on any of the systems on my internal network, including 2 windows only and 1 XP/Kubuntu/Maverick/Lucid minimal quad boot system. I have found over the years the firewall in my router is perfectly adequate for my needs. The only time any of my Windows computers have been infected with malware is when I've installed the malware myself for testing purposes. Common sense goes a long way to keeping my systems safe.

---

### Post by i_dont_know_what_im_doing on 2010-08-09
Thanks again, you're clearing a lot of things up for me. Hopefully these will be my last questions... :D

> Viruses in wine will only affect your wine directory, and can't  propigate through the rest of the system. The big thing to do is ensure  that the wine directory isn't linked to your Windows partition in any  way. ClamAV supposedly will scan for Linux viruses, but there aren't any  in the wild at the moment.So how does this work? Does wine only give them permission to create new files on the Desktop or something? What if I run a .exe from somewhere other than my wine directory? Also, how is having my wine directory linked to my Windows partition dangerous? Not that I'd want to do that, I'm just don't see how it's any more dangerous that running the same .exe's from the Windows side of the computer.

> If you don't have port 80 port-forwarded through your router, so that  there is no external (internet) access to the the web server you are  pretty will safe, and can basically do whatever you want.True, I just like to have another layer of protection. For some reason, my router automatically forwards ports for programs like Skype, so I just want to make sure that if it somehow automatically forwards port 80, I'll still be okay.

> Truthfully I'm kind of lazy, so I only run the occasional port scan from  a different system on my internal network. The services I run http, ssh  internally never get access to the internet. What information would I find with a port scan? If I've enabled a firewall, it seems like it wouldn't find anything. Should I disable my firewall to test it? How would I tell the difference between something dangerous, and just some server application I accidentally installed? Also, can't programs just initiate a connection themselves to avoid opening a port?

Keeping a log of changes I make is a good idea, I'm going to start doing that from now on. (Like any .debs I install, or programs I compile, or any root-owned files/settings that I change, I'm assuming? Anything else I should log?) Anyway, I think I'm just going to plan on reinstalling at some point, maybe when 10.10 comes out. That way it'll clean up all the clutter and mistakes and I'll have a fresh start. I should probably also clean out my /home of old program settings. :)

---

### Post by cariboo on 2010-08-10
> So how does this work? Does wine only give them permission to create new files on the Desktop or something? What if I run a .exe from somewhere other than my wine directory? Also, how is having my wine directory linked to my Windows partition dangerous? Not that I'd want to do that, I'm just don't see how it's any more dangerous that running the same .exe's from the Windows side of the computer

I haven't used wine in about 8 years, but from threads here in this subforum, malware only affects the wine directory as that is where the pseudo windows programs/libraries are located. Linking your windows partition allows malware to migrate to that partition. 

If you get infected, it's just a matter of removing the wine directory in your home directory and the problem is solved.

> True, I just like to have another layer of protection. For some reason, my router automatically forwards ports for programs like Skype, so I just want to make sure that if it somehow automatically forwards port 80, I'll still be okay.

Don't quote me on this, but most routers only block service ports up to 1024, services like skype and p2p user random ports every time you use them, so it would take quite a while to scan all 655355 available ports looking for them. 

> What information would I find with a port scan? If I've enabled a firewall, it seems like it wouldn't find anything. Should I disable my firewall to test it? How would I tell the difference between something dangerous, and just some server application I accidentally installed? Also, can't programs just initiate a connection themselves to avoid opening a port? 

A quick and dirty port scan will give you information on what ports are open and listening, this is what a port scan on my server looks like:

```
nmap willy

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-09 22:48 PDT
Interesting ports on willy (192.168.1.250):
Not shown: 994 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs

Nmap done: 1 IP address (1 host up) scanned in 0.17 seconds
```

The scan shows you what ports are opened by what service in the above example:

[list=1]
[*] ssh = openssh-server
[*] http = appache2
[*] rpcbind = portmap used with nfs file sharing
[*] netgios-ssn - Samba for file sharing with Windows computers
[*] microsoft-ds - Samba again
[*] nfs - nfs-kernel server, for sharing files via nfs
[/list]

The way I found out about what each open port was for, was looking up the service on google.

Ports are only open when a service is running, for instance to shut down apache, use the following command with any version older than lucid:

```
sudo /etc/init.d/apache2 stop
```

Lucid and newer:

```
sudo service apache2 stop
```

to restart the service just use start instead of stop. If the service is stop there is nothing listening on the port it uses.

I use ufw to enable iptables rules when I'm out and about with my netbook, running nmap against the netbook with ufw enabled, basically doesn't show anything, not even that the netbook is up and running.

The one thing to note is, that running a scan from localhost will give different results than by running it from another computer on the network:

```
nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-09 23:02 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 993 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.13 seconds
```

as you can see in the above example it shows that mysql is also running, whereas in the first scan which I did from the computer I'm using now it wasn't shown at all.

There is no quick and dirty security guide, bodhi.zazen's stickies go a long way towards getting a start on security, but depending on how far you want to go, it's basically up to you. The one point you should keep in mind, is that security is like an onion, the more layers, the more secure you are.

---

