---
title: "how to close ports with GUFW?"
date: 2009-06-30
forum: Security
---

### Post by jadu on 2009-06-30
hello, 
So here I'm trying to become a Ubuntu expert, for the small non profit where I work, starting from zero...I just installed GUFW for a firewall, because I read on the forums that firestarter is no longer recomended, and that GUFW is easier to use.
 Then I went to the Shieldsup site, that I read about on this forum, and it told me have some ports open. telnet, ftp, and http. The others were listed as "stealth". 
I read here that "stealth" is really "drop", and what that means. But I would like to learn how to close those ports with GUFW. I read on one site that says to change the "GUFW setting to: 12345 ALLOW Anywhere". But I can't find that on the GUFW interface I have. How do I do that?
From what I understand, it IS a problem if the ports are open, right? Though I read that the Shieldsup site gives "wrong" diagnosis because they check the router, not the computer. Still, I'd like to know how to close the ports (assuming that's necessary).

Also, I read that "hardware" firewalls are better than "software" firewalls. What I have with GUFW is a software firewall, right? I don't know the difference.

thanks

---

### Post by t4thfavor on 2009-06-30
Shieldsup is looking at your router, not your PC. The router probably has some ports open for management, which you can't stop from happening if you want to manage it remotely.

A hardware firewall is just software running on an appliance. The only reason they are better is that they are usually tuned to a purpose, and fairly hardned against attacks while a software firewall runs on a pc (or other computer device) on top of a general purpose OS that has a bunch of other software on it. This other software is where the problem lies. A vulnerability in that other software makes your firewall useless. A software firewall is usually slower since process priority is given to user functions instead of services.

GUFW is a software firewall in the sense that you run it on a server or destop. 
In the end GUFW uses iptables as its actual backend firewall process as do 90% of hardware firewalls.

In the end its OK to have a few services open to the internet, because you need them. It also helps for security if you change the default port for each srvice to something similar but different (SSH 22 -> SSH 2222) This helps to prevent bot attacks.

If you have any more questions, I will be happy to try and answer them.


EDIT:
I almost forgot, I dont run any firewalls on my workstations, as its just something I have found gets in the way of doing actual work. I rely on good filters at the perimeter and intelligent spam filters in my email. 

Its not if you are compromised, its when. Some people go a long time without an issue, and others don't.

---

### Post by bodhi.zazen on 2009-06-30
Keep reading :)

To be honest, it really really helps to learn the basics of iptables. I know it is intimidating at first, but if you understand iptables (at least the basics) the rest falls into place.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The "problem" with understanding of iptables is you need to understand at least the basics of networking ...

If you do not understand those things, simply install gufw and click the enable button :lolflag:

Also security on Linux is different from security on Windows, so you may want to look at this as well :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by jadu on 2009-07-01
hello,

thanks a lot for your answers. I read the IP tables tutorial, and it was very helpful and easy to understand (at least the basics part, the second part went over my head, I'm afraid). And the security tutorial I had looked at yesterday.
I ran nmap, like it suggested in bhodi's tutorial. (I'm copying the output below). I understood the part that "All 1715 scanned ports are closed". That seems to be enough, right? Just with having the GUFW  activated?
It was helpful to learn about IPtables, but I think I'll stick with GUFW, since after I leave my work I don't know who will be handling the computers, someone with as little knowledge as me or less, so easier is better.
Are there any other problems you see in the output of the nmap scan? 
Is responding to pings a problem?

Do you think it's worth it to "change the default port for each srvice to something similar but different (SSH 22 -> SSH 2222)", like t4hfavor suggested? How would I do that, if so?

t4thfavor offered to answer other questions I have, hmm actually... I have two posts up still that haven't been answered, if you have any ideas.

[http://ubuntuforums.org/showthread.php?p=7541486#post7541486](http://ubuntuforums.org/showthread.php?p=7541486#post7541486)
 
and less important, you could scroll down to my last post on this one:
[http://ubuntuforums.org/showthread.php?t=1200210](http://ubuntuforums.org/showthread.php?t=1200210)

thanks again then



Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-07-01 10:01 COT
Initiating Ping Scan at 10:01
Scanning 192.168.0.2 [1 port]
Completed Ping Scan at 10:01, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 10:01
Completed Parallel DNS resolution of 1 host. at 10:01, 0.01s elapsed
Initiating Connect Scan at 10:01
Scanning XXXXXXXXXXX [1715 ports]
Completed Connect Scan at 10:01, 0.06s elapsed (1715 total ports)
Initiating Service scan at 10:01
SCRIPT ENGINE: Initiating script scanning.
LUA INTERPRETER in nse_init.cc:763: /usr/share/nmap/scripts/robots.nse:4: module 'http' not found:
	no field package.preload['http']
	no file '/usr/share/nmap/nselib/http.lua'
	no file './http.lua'
	no file '/usr/local/share/lua/5.1/http.lua'
	no file '/usr/local/share/lua/5.1/http/init.lua'
	no file '/usr/local/lib/lua/5.1/http.lua'
	no file '/usr/local/lib/lua/5.1/http/init.lua'
	no file '/usr/lib/nmap/nselib-bin/http.so'
	no file './http.so'
	no file '/usr/local/lib/lua/5.1/http.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
SCRIPT ENGINE: Aborting script scan.
Host XXXXX appears to be up ... good.
All 1715 scanned ports on  XXXXXXXX are closed

Read data files from: /usr/share/nmap
Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.150 seconds

---

### Post by bodhi.zazen on 2009-07-01
Awesome :)

Normally I think of changing ssh port 22 -> to a higher port such as 2222 "security through obscurity", and security through obscurity is no security at all.

ssh (port 22) is one exception to the rule as if you install openssh-server you will see port 22 gets hammered by script kiddies.

To lock down ssh see (you do not need this if you are not running a server):

[AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by jadu on 2009-07-02
thanks a lot for your help, I appreciate it.

---

