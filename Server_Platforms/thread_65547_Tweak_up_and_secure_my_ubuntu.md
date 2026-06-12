---
title: "Tweak up and secure my ubuntu"
date: 2005-09-14
forum: Server Platforms
---

### Post by cyclister on 2005-09-14
First I want to tell you that I do not have english version of ubuntu.

I have discovered an interactive "thing" in my startup and when I use that I can shutdown processes.My intentions is to redduce processes or backgroundprogramms I do not acctully use for my daily surfing on internet.
How many can I acctully shutdown in the startup?
I use Gaim little IRC and Firefox for the moment so many server applications is not in use, so they are like unnecesary for me at the moment.
I would be glad if someone could do write me som sort of list I can print out until I can that list.

Offtopic
Many thx I think ubuntu is great its easy to use its like debian light and the best of all its competly free of charge, I have run windows for many years and always blamed my self for "stealing" it.Now I do not have to steal just run my ubuntu distro many thx

---

### Post by KingBahamut on 2005-09-14
[QUOTE=cyclister]First I want to tell you that I do not have english version of ubuntu.

I have discovered an interactive "thing" in my startup and when I use that I can shutdown processes.My intentions is to redduce processes or backgroundprogramms I do not acctully use for my daily surfing on internet.
How many can I acctully shutdown in the startup?
I use Gaim little IRC and Firefox for the moment so many server applications is not in use, so they are like unnecesary for me at the moment.
I would be glad if someone could do write me som sort of list I can print out until I can that list.

Offtopic
Many thx I think ubuntu is great its easy to use its like debian light and the best of all its competly free of charge, I have run windows for many years and always blamed my self for "stealing" it.Now I do not have to steal just run my ubuntu distro many thx[/QUOTE]
 Well you likely kill fetchmail, cron, anacron without problem. Granted you arent going to use those services.

---

### Post by cyclister on 2005-09-14
:smile: That wasent even hard to know that I can remember, thanks man.
How do I acctully know if my iptables is working and also my nmap?

---

### Post by TheDanMan on 2005-09-14
How do you know your iptables is working?  Nmap it.  How do you know Nmap is working?  You Nmap another computer.

---

### Post by KingBahamut on 2005-09-14
Nmap is not an active Daemon if thats what your asking.

---

### Post by drogoh on 2005-09-14
[QUOTE=KingBahamut]Well you likely kill fetchmail, cron, anacron without problem. Granted you arent going to use those services.[/QUOTE]

Fetchmail I can see, not many desktop users would be using it but... why cron and anacron?

---

### Post by LordHunter317 on 2005-09-14
I'm pretty sure disabling those would be a v. bad thing.

---

### Post by cyclister on 2005-09-15
So you are saying that I do not have to have nmap to getting a higher level of security?
But if I have a router and a router it self counts as a little cimpouter in some ways can I nmap that to my little network?

If I do have nmap would that be more insecure in some ways?
But the other hand is that I do think nmap helps beacuse my internet flow is much more stable with that.Nmap might locate my router and getting by that more safer and more stable connection, but hey I can be wrong here.

---

### Post by jdong on 2005-09-15
[QUOTE=KingBahamut]Well you likely kill fetchmail, cron, anacron without problem. Granted you arent going to use those services.[/QUOTE]
** Hold on!**
Fetchmail is fairly safe to kill (postfix is NOT. system mail needs to get through), if you dont' use it as a daemon.

Cron is **VITAL** to the continual health of your system! Ubuntu has numerous maintenance  tasks scheduled to execute nightly via Cron, from system updates to refreshing man pages. These tasks need to be able to execute.


If you don't keep your system on 24/7, **anacron** is also important to have. It'll run cron jobs at other times if they don't run at their scheduled times.


All three are extremely minimal security risks, if any at all. Leave Cron and Anacron enabled for sure!

---

### Post by TheDanMan on 2005-09-15
Nmap is a program that allows you to scan for open ports on your system or other systems.  Nmap does not run all the time nor does running it in any way improve security other than getting you to take other actions.

Setting up a good firewall is a good idea if you are not already behind a firewall.  If you have a firewall router that is good, however you need to set that up, just as you would have to set up iptables if you don't have another firewall between you and the internet.

Personally at home I do not run a firewall on my systems because I have a firewall router.  The router is set up to deny all incoming UDP traffic.  That takes care of 99% of all malstuff.  The fact is you're not likely to get hacked running any flavor of linux.  It doesn't mean its not possible, just means not likely unless you're visable to the entire internet as a webserver or other internet server would be.

---

### Post by LordHunter317 on 2005-09-15
[QUOTE=TheDanMan]Setting up a good firewall is a good idea if you are not already behind a firewall.[/quote]Only if you're going to start running services.

>  The fact is you're not likely to get hacked running any flavor of linux.Not that's simply not true.  Linux vulernabilites are becoming more and more commonplace.  Including ones that countermeasures like a firewall won't protect you against.

---

### Post by jdong on 2005-09-15
[QUOTE=TheDanMan]  The fact is you're not likely to get hacked running any flavor of linux..[/QUOTE]
Untrue.

There exists distributions out there that don't perform regular security updates stringently (mostly the under-maintained, handful-of-volunteers type).

Vulnerabilities are vulnerabilities, regardless of platform. If they're open, they will eventually get exploited. Don't let that happen. Patch up regularly, run a distribution that maintains security patches for the packages you need to use.


Server or PC, Linux OpenBSD or Windows.... security needs to be kept in mind.

---

### Post by TheDanMan on 2005-09-16
Well allow me to defend myself, that was an opinion.  :-D

I didn't say it wasn't going to happen, but that it was unlikely.  Now, unlikely is a variable.  It is unlikely compared to plugging in a windows machine to the internet.  However if you have it out there unpatched for long enough you will get hacked.

---

### Post by seiflotfy on 2005-09-16
so what programs would you suggest to install or remove to have a secure ubuntu
(on a laptop)!!!

---

### Post by TheDanMan on 2005-09-16
For a laptop or a Desktop:

Install firestarter.
Install whatever other apps you want.
Don't uninstall anything.
Create a cron job to email logs to you then delete firestarter logs for you.

---

### Post by LordHunter317 on 2005-09-16
[QUOTE=TheDanMan]I didn't say it wasn't going to happen, but that it was unlikely.  Now, unlikely is a variable.  It is unlikely compared to plugging in a windows machine to the internet.[/quote]Even that is not even true anymore, especially if your system is not totally up to date.

---

### Post by jdong on 2005-09-16
[QUOTE=TheDanMan]For a laptop or a Desktop:

Install firestarter.
Install whatever other apps you want.
Don't uninstall anything.
Create a cron job to email logs to you then delete firestarter logs for you.[/QUOTE]

You don't even need Firestarter. Just **be careful what you install** -- by default, Ubuntu installs no exploitable services, and servers installed only listen to localhost (not remotely exploitable).

So, you need to manaully and **consciously** make the decision to install a public service, which probably means you should investigate the consequences of performing such actions.


Also, please **KEEP UP TO DATE** with patches! That's very important to continued security.

---

### Post by JEDIDIAH on 2005-09-16
I still run a firewall on my servers so I can create exclusion lists for any host/subnet that malware traffic originates from. Basically, anything that pops up in the apache, snort or daemon log that looks fishy gets turned into a firewall rule. 

    Just running snort is a good idea. It will give you a good feel for what is getting past the separate firewall. I also gives you a good idea on how people are trying to abuse any exposed services.

    If I could run snort & my processing script on the external firewall I'd really prefer that (any suggestions?).

---

### Post by Kyral on 2005-09-16
Question along the same lines. I run sshd on my box so when I'm in the computer labs on campus I can use FreeNX to connect to it. How would I secure my box against attacks directed at the sshd? (Keep in mind I usually stop the daemon when I get back home).

Also what is a good program for interfacing with iptables?

---

### Post by jdong on 2005-09-16
> **Kyral]Question along the same lines. I run sshd on my box so when I'm in the computer labs on campus I can use FreeNX to connect to it. How would I secure my box against attacks directed at the sshd? (Keep in mind I usually stop the daemon when I get back home).
[/quote]
Specifically with FreeNX, I recommend NOT using Nomachine NX keys. If (in the **PURELY HYPOTHETICAL** situation) an exploit was found in the NX authentication protocol, systems using the Nomachine key are just sitting ducks to zombie attacks.

SSH-wise, like I've said before, keep up with security updates to both FreeNX and SSH , **monitor your SSH auth.logs** -- it's much more important to stop an attack before it gets anywhere important than to lose your hair being ultra-paranoid.

Change your passwords often, and make sure your client systems are **FREE FROM KEYLOGGERS** and other junk -- I've seen cases at school of Win2k3 servers being brought down thanks to unwise use of domain admin accounts and Terminal Server  said:**
> 
Also what is a good program for interfacing with iptables?

GUI, Firestarter.

Non-GUI/webGUI, Webmin, and Shorewall. I like the Shorewall system the best -- it simplifies IPTables to self-explanatory, well-documented columnar configuration tables not to mention WebMIN's frontend to it.

However, running WebMIN is one more *potential* security risk. Try to use SSH tunneling and minimize publicly open ports whenever possible!

---

### Post by Kyral on 2005-09-16
Someone in #ubuntu gave me the iptables rule to drop all SSH attempts that come from off my campus.

Also what key should I use in place of the NoMachine key?

And me being updated is no problem. I sync to the Repos prolly 5 times a day

---

### Post by seiflotfy on 2005-09-19
[QUOTE=TheDanMan]For a laptop or a Desktop:

Install firestarter.
Install whatever other apps you want.
Don't uninstall anything.
Create a cron job to email logs to you then delete firestarter logs for you.[/QUOTE]

how does one create cron job!!!

---

### Post by JEDIDIAH on 2005-09-19
[QUOTE=jdong]Specifically with FreeNX, I recommend NOT using Nomachine NX keys. If (in the **PURELY HYPOTHETICAL** situation) an exploit was found in the NX authentication protocol, systems using the Nomachine key are just sitting ducks to zombie attacks.

SSH-wise, like I've said before, keep up with security updates to both FreeNX and SSH , **monitor your SSH auth.logs** -- it's much more important to stop an attack before it gets anywhere important than to lose your hair being ultra-paranoid.

Change your passwords often, and make sure your client systems are **FREE FROM KEYLOGGERS** and other junk -- I've seen cases at school of Win2k3 servers being brought down thanks to unwise use of domain admin accounts and Terminal Server ;). Use a LiveCD like PXES or Kanotix whenever appropriate.


GUI, Firestarter.

Non-GUI/webGUI, Webmin, and Shorewall. I like the Shorewall system the best -- it simplifies IPTables to self-explanatory, well-documented columnar configuration tables not to mention WebMIN's frontend to it.

However, running WebMIN is one more *potential* security risk. Try to use SSH tunneling and minimize publicly open ports whenever possible![/QUOTE]
 When you're running an ssh server, also don't forget about the "AllowUsers" setting in the sshd_config file. This will lower the profile of your ssh server somewhat.

---

### Post by TheDanMan on 2005-09-19
I only know how to do it from a command line using crontab.  I don't know of a gui tool that will allow you to add one.

---

### Post by seiflotfy on 2005-09-20
[QUOTE=TheDanMan]I only know how to do it from a command line using crontab.  I don't know of a gui tool that will allow you to add one.[/QUOTE]
 Create a cron job to email logs to you then delete firestarter logs for you.

how do i do that!!

---

### Post by cyclister on 2005-09-25
Hey this was really fun to read I think some of you are really good at this, first of all I want to get the end of my compilation, do not get how its gonna work.But I guess when I have more computers up and going I can get help via X-chat or some other client.
But then I want to have my own email "server" that cron mail sounds nice.But what that thing with firestater log, these two sounds pretty neat and nice man, that I want too  :grin:

---

