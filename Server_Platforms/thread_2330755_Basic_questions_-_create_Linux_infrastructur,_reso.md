---
title: "Basic questions - create Linux infrastructur, resources, management, security"
date: 2016-07-14
forum: Server Platforms
---

### Post by maerzhase on 2016-07-14
I am new to Linux, but want to learn how it works. I will go step by step, but i have some basic questions.
 Even tho they may be general Questions for Linux Servers, i decided to  use Ubuntu as OS and think that i get the best answers/help here. (Sorry  if this is not the right Board to ask, please move than.)

My Plans:
I want to create some servers (Web/Reverse Proxy, FTP) in my DMZ and  later in LAN a Fileserver and a Linux DC (right now LAN Zone is Win  only).

Now i have troubles in understanding the basics:

1) I know the Swap partition size is related to the used RAM, i could do  it all auto, but than i dont learn anything or understand why. Since i  dont know how much resource i need now or later on my system and it  should be able to scale, i thought on putting the Swap on a separate  virtual disc. So if i need more RAM and therefore more Swap, i can just  increase the size of my VMDK. (Sidenote: In an real Server environment, i  could put the Swap drive on a second Raid for performance - is that  needet?). I guess i can do the configuration in advanced install mode.
My questions to this are:
[LIST]
[*]Does this make sense at all, or are there better ways to achive a scaling Swap partition? 
[*]If i will (in future) adjust my the Swap size, does the system need some adjustments, or is it automatic regulated? 
[/LIST]
 
2) Is there any guidline on how to roughly estimate/calculate the  resources the server needs to do his work. I know this is a very  case-specific question and depends on a lot more information on what the  server is expected to do, how many users etc.. But my resources are  limited. Maybe this helps to give me a little hint:

I plan to run a minmal Server Setup with nginx als reverse-proxy for my Tomcat in my homelab (so no real workload, 1 user :wink: - remember its just for training). Same would go for the FTP and Fileserver.
Since nothing happens there, can i assume i just need to meet the  minimal Ubuntu Server requiremts. Of course i can experiment(and i  will), but its good to have a starting point.
For the Webserver something like: 1core 500mhz - 512mb Ram (Swap=2x RAM) - ~2gbg HDD

3) The management comes to my mind. I can administrate every server on  its own, but this is work and time intense. I think something like  Webmin should do the job. I can add servers and modules and do the  administration from one central point. I think i create an extra  server(in LAN, it may become the DC) to run this. If i understand it  right, Webmin is the tool to use for management of several servers,  right?

4) AppArmor (SELinux?) runs on Ubuntu. Is it standart for server too?  Can i deactivate this w/o problems? Is there any standart policy or rule  set for different purposes, like for Webservers, Fileservers. Or do i  have to set up everything my own? I dont like to hustle with this  problem now - i can learn that later, when i have basic understand of  Linux and how everything works.



thats it for now
I really appreciate any help you can provide and maybe someone has a  good beginner guide to share or a book recommendation related to that  topic. I read alot step by step guides, but (for now) i have trouble  understanding some of the parts - its a bit overwhelming when comming  from Windows. But in the end its learning by doing :smile:

---

### Post by TheFu on 2016-07-14
Welcome to the forums.  You are biting off a bunch of stuff.

a) do not use FTP. Use sftp that is built-into the openssh-server already. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  Don't. Just don't.  Wish they'd stop teaching anything about plain FTP. It should have died out in the mid-1990s when telnet use did. There are better, more convenient, and definitely more secure alternatives.

b) Java is a resource hog.  1.5G of RAM and 1 CPU minimum, but it might need 10G of RAM and 10 CPUs eventually.  With perl, python, php webapps, you can run on 384MB of RAM.  With Ruby, the gem management tool doesn't work in less than 768MB of RAM, though ruby webapps can work in less - do you want to increase the RAM and reboot just to patch the gems?

c) Don't use webmin ... er ... ever. Learn to manage the systems following the normal Unix methods.  Webmin just adds multiple, new, security issues. Sadly, the people who want webmin the most are the least likely to be able to secure it.  In the hands of a master Admin, it can be secured, provided network access to it is blocked from all IPs except the 1 for that admin guy. Nobody else should be able to see the login page at all. Until you have the skills to make that happen, don't attempt to install webmin.  By that time, I expect you'll be happily managing the different config files with **sudoedit** anyway.  Management of Unix/Linux systems these days is performed using a devops tool like Ansible or puppet or chef or Salt or rexify or cfengine or ... 20 others.

d) AppArmour isn't like SELinux - we don't turn it off. I've never had any issues with it, but I could certainly learn more. There is a method to have apparmour monitor a program running and capture the required files to be accessed. Then you can use that as the settings for that program/daemon and prevent misuse.

e) Swap - these days servers don't use swap because RAM is cheap and we just add more RAM as needed.  On a low-end system or a brand-new system having 2G of SWAP would be where I started.  For Java, I'd add more and expect it to be big and slow, since that is the nature of Java, IMHO.

Then I'd watch the monitoring (don't forget to install tools for that) over a week or 2 and see what needs to be tuned.  More CPU? More or less RAM?  How's the disk use going. Static or rapidly increasing?  This is all normal performance management stuff, but also useful to notice when a system isn't behaving as normal (got hacked?). You'll be able to pinpoint when that happened and find the files the cracker dropped on the system, probably.

If you are running inside a VM, there are many tuning parms for that.  Most important is the way the storage is laid out. There can be a 50-80% difference in performance for badly created VM storage.

My basic server gets 1G of RAM and 1CPU to use.  If I don't know how much storage it needs, it gets 8G, but most will use much less - 2G-4G of they are just providing services, not doing data/file stuff.  Have a few systems with 20+G of storage, those are the exceptions around here.  The system I have running a reverse proxy (nginx), blog (RoR) and few static websites (nginx) has ... 1.2G of RAM
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       7.1G  3.2G  3.6G  47% /
/dev/vda2       2.3G  1.1G  1.1G  49% /var/www
```
of disk.
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1191        994        196          0        278        300
-/+ buffers/cache:        415        775
Swap:            0          0          0
``` of RAM used. Zero swap (like my tuning?).

```
$ more /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
```
and 1 CPU - I forced the C2D level in the VM to help with live migrations between different systems here.

Many of your swap questions have been asked and answered in these forums many times. Search and review those if you want more details.  Just know that "Desktops" tend to need 4G of swap thanks to hog browsers and monster GUIs ... that's sorta the minimal these days and if you have 16G of RAM, 1G of swap for a desktop is probably just fine.  For servers, the goal is to need ZERO swap.  If the server is doing lots of file transfers, then leaving some RAM for disk buffers is smart. That way the files will transfer at wire speed, not disk speed.

Sounds like you are coming from the same way that I did. My best advice for [Learning Linux]("http://blog.jdpfu.com/2014/12/28/learning-linux").

---

### Post by maerzhase on 2016-07-17
So i read alot of your suggested guide, tried some stuff at home. Slowly but surely i am getting warm with the Linux bash. So for now,  webserver(just webserver, reverse proxy is next) is running - but space  for improvements and security things. 
I have to say i realy love that link. That stuff gave me so much in understanding(but i am still reading), why in Linux things are in that way. Way better than the usual guides: Linux is different, everything is free, you can chosse 10mio Desktops, do this and that step by step.
Additional to that i found Linux from Scratch, which looks promising to me, will read/do that to for the general understanding.

For my questions:
Guess i was a bit lazy with forum/google search, but you still helped :D .
I will not use FTP, never thought of that. I misused the term here. I my should have written SFTP or FTPS, i know the issues. Will try both, so i know how its done.
"Ansible or puppet or chef or Salt or rexify or cfengine"  - have to do some research, looked a bit into ansible. Thanks for the tip here, i only knew Webmin before.

In general **THANK YOU** for your answer, especially for that link, that was extremely helpful.

---

### Post by TheFu on 2016-07-17
Glad it helped.  FTPS has an issue which makes it less-desireable. The client can ask for zero encryption. That's a non-starter for me.  Also, using one of the major FTP servers which happens to have added SFTP and FTPS support after the fact is a non-starter for me.  All of them - ALL - have had their source code compromised before and people where deploying those servers for months and longer with back doors added that nobody noticed.  openssh-server has had some issues too - all code does - but it is used my pretty much everyone on every unix platform so that when anything funny is seen, it gets investigated then fixed.  You need ssh anyway, so why not use sftp too?

Bash isn't just Linux. It is on all the major platforms and all Unix platforms. Plus, many people dno't use bash for the shell, which is perfectly acceptable. I ran sh, then ksh, then csh, then tcsh ... and finally around 2010, switched to bash. I miss some things about tcsh, but overall, bash is nice. For scripting, I tend to use sh and only switch to bash when the more advanced features are needed. If a script is over 1 pg in length, I'll switch to perl. That is my scripting language of choice, but there are others, like Python which are very useful too.

Guide?  Why to stop using FTP?  Not much of a guide.   The **Learning Linux** link is infinitely useful, however. Hope you like it. Take it you are in the PDF book?  Lots to know and you'll never know it all.  All this knowledge is like drinking from a firehose. ;)

Linux from Scratch has a place, but most people shouldn't ever need to touch it.  Going outside the popular distros is asking for maintenance nightmares.  I know some people who think that deploying Gentoo or Arch on 500 systems isn't anything. If their management knew how much time they were wasting, well, I would fire them. Sure, there are highly specialized situations where custom everything is completely required, but hopefully someone with 5+ yrs of experience would be making those decisions, to avoid as many pitfalls as possible. There are pitfalls with everything - my goal is to avoid as many of those as possible and have 100% uptime (outside planned, announced, maintenance windows).  Every application needs a maintenance window, period.  There are ways to minimize and almost completely remove downtime, but .... 

Anyway - good luck! And don't forget to have the appropriate amount of fun with this stuff.

---

