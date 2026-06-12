---
title: "I feel like I'm in an unwinnable war / paranoid questions"
date: 2014-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by james_smith2 on 2014-02-09
Hi,
Admittedly I'm new to Linux - Ive read the dumbies guide and the linux handbook but I'm still learning constantly, its infinite!


Anyway, I lost my business due to Windows, Kaspersky and hardware firewalls that in truth offer no protection to the end user.  So I switched to Linux - its better for sure - but theres so much to do even to get basic security.  At the mo I'm running Alpine Linux and because its not user friendly I also boot a live CD and use various distros, currently mint right this second.

Anyway I have some questions - hopefuly just paranoia

Firstly my root is not / or /. or dev/sda  - it is  ~   and in here I've found some files
.config   
.gvfs
.bashrc
.gksu.lock
.dmrc
.bindkey
.ICEauthority
.gtkbookmarks
and my home folder as symlink

to name just a few but more interestingly Ive found

.com32 and .menu.c32

Originally my live cd, would show the boot sequence when i press tab but I noticed soon it had placed the .com32 and menu.c32 infront of the boot line and it appeared to of changed as well to a dir called /isolinux/

I wouldn't think anything was wrong; except now I cannot tab anymore.  Its been blocked and the features to do itegrity tests and nokms and safe mode etc are now inaccessable.

I also found my other disc fails the integrity test - which concerns me.


Other strange things I've found hidden about are;

An 8.2kb partition called OSMIN   -  I cannot access it either no matter what text editor I use and if I type head in terminal my fonts go haywire.


Also

I tried doing system settings in my GUI and noticed;
pulse-audio --log-target=syslog
WNCKApplett
MD
S2U
SASLAUTHD
RT-KIT Daemon
KHUGEPAGED

and other strange named processes.

I hope its just me worrying but Ive had 1 business stolen.  I can't handle it happening again.  I'm devising a security policy now and I will learn everything I need to secure my browser, linux and network - its gonna take a LONG time though!

Other strange things, a file called do-not-hibernate  that is empty?   lol  what?

also my log for ive disc mint cinnamon says;
installed-ubiquity-frontend-gtk
trigproc-libc-bin-ubuntu4   :/
installed status ureadahead

I have an alternatives.log and its got stuff about openbsd
loads about usr/share/fonts

isn't that my shared directory?   	 	 	 	


 some more...   pdate-alternatives 2013-11-26 21:50:58: link group rsh updated to point to /usr/bin/ssh
 update-alternatives 2013-11-26 21:50:58: run with --quiet --install /usr/bin/rlogin rlogin /usr/bin/slogin 20 --slave

update-alternatives 2013-11-26 21:51:01: run with --install /usr/bin/telnet telnet /usr/bin/telnet.netkit 100 --slave /usr/share/man/man1/telnet.1.gz

very odd - i wouldn't even want telnet services running!
Why always in the share dir too

theres a file called   fail.log
and inside is thousands of hash symbols?   ######################## like that?  What would that be?

update-alternatives 2013-11-26 21:51:30: run with --install /usr/bin/fakeroot fakeroot /usr/bin/fakeroot-tcp 30 --slave /usr/share/man/man1/fakeroot.1.gz fakeroot.1.gz /usr/share/man/man1/fakeroot-tcp.1.gz --slave /usr/share/man/man1/faked.1.gz faked.1.gz /usr/share/man/man1/faked-tcp.1.gz --slave /usr/share/man/es/man1/fakeroot.1.gz fakeroot.es.1.gz /usr/share/man/es/man1/fakeroot-tcp.1.gz --slave /usr/share/man/es/man1/faked.1.gz faked.es.1.gz /usr/share/man/es/man1/faked-tcp.1.gz --slave /usr/share/man/fr/man1/fakeroot.1.gz fakeroot.fr.1.gz /usr/share/man/fr/man1/fakeroot-tcp.1.gz --slave /usr/share/man/fr/man1/faked.1.gz faked.fr.1.gz /usr/share/man/fr/man1/faked-tcp.1.gz --slave /usr/share/man/sv/man1/fakeroot.1.gz fakeroot.sv.1.gz /usr/share/man/sv/man1/fakeroot-tcp.1.gz --slave /usr/share/man/sv/man1/faked.1.gz faked.sv.1.gz /usr/share/man/sv/man1/faked-tcp.1.gz
update-alternatives 2013-11-26 21:51:35: run with --install /usr/bin/lzma lzma /usr/bin/xz 20 --slave /usr/share/man/man1/lzma.1.gz lzma.1.gz /usr/share/man/man1/xz.1.gz --slave /usr/bin/unlzma unlzma /usr/bin/unxz --slave /usr/share/man/man1/unlzma.1.gz unlzma.1.gz /usr/share/man/man1/unxz.1.gz --slave /usr/bin/lzcat lzcat /usr/bin/xzcat --slave

sounds sinister!!!!   I hope this is just normal stuff   :/

---

### Post by howefield on 2014-02-09
Best stop posting for a minute and read your pms.

---

### Post by The Cog on 2014-02-09
Perhaps you should ask in the Alpine Linux forums. 

A few notes:
~ is the shortcut notation for your home folder which is normally /home/username. Try the command [FONT=Courier New]echo ~[/FONT] and see that it has been expanded. This is normal.

/usr/share is a folder of resources that are "shared" in the sense that they are readable by all users of the computer. This is normal. It is not a shared directory in the sense of being available across a network unless you install some kind of server and configure it to share that folder and I can't think why you would do that.

telnet is a telnet client, not a telnet server. It is normal for it to be linked via a symlinks through /etc/slternatives, which allows you to use one of several possible telnet clients. The telnet server is called telnetd and is not (on Ubuntu) installed by default.

Moved to OS chat as not an *buntu question.

---

### Post by bashiergui on 2014-02-09
Hire a professional security consultant. Not your friend's nephew. A legit pro.


I'm all for learning on your own. It's daft to start where you're at and try to learn it all to secure an existing operating business.

---

### Post by lykwydchykyn on 2014-02-09
Honestly, I don't know the answer to all of these questions; but in most cases you're jumping at shadows here.  If you're new to linux, why are you using something like Alpine linux?
[quote="Alpine linux website"]
Alpine Linux is a community-developed operating system designed for x86 Routers, Firewalls, VPNs, VoIP and servers.
[/quote]
Not exactly a desktop distro for newbies.  IMHO you're better off using a distro or OS you can understand and feel some level of trust towards rather than arbitrarily picking one that claims to be more secure. 

As for all these files and processes with "strange names" -- names of things in Linux is a mix of unix tradition and techie acronyms with a healthy dose of hacker humour.   If you're ever in doubt about what something is, consult your favorite search engine.

---

### Post by james_smith2 on 2014-02-09
No this is ubuntu - mint - cinnamon - it claims to be ubuntu

I just found a directory called libcrack and libcrack.dict

my HD is not plugged in.  this is on a finalised CD.   Please help.  Am I going nuts?  Its a live CD off of a magazine.

Ive been reading every security bookj / linux book I can get trust me!!   I own about 6 now and I've read them all more than once.


You don't understand - I lost my entire life to hackers.  took my business, lost my family.  Please help me   :(   I'm ready to give up on life - for good.


So far I've read - Linux for dumbies, hacking for dumbies, securing linux, Nmap network scanning.  Network security for dumbies.    -   Please give me some slack here - i lost a 6 figure business, my carrear, my entire life - ive been reading for over 1 year and these books don't mention anything about this stuff im seeing.  I WOULD not ask here if I had not checked my books first!  theres nothing about this stuff and lets face it - Linux is VAST to say the least.

I'm sorry - just put the boot in me if you want - i've had 2 yearsd off it I'm ready to off my self anyway.

---

### Post by QIII on 2014-02-09
I suggest, in all sincerity, that you let your choice of distros sit on the back burner, turn off your computer and deal with far more important things in your life at this juncture.

This is not the place for you to find what you really need.

My very sincerest and best wishes for you.

Thread closed.

---

