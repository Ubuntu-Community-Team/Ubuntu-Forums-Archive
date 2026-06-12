---
title: "Firestarter ?"
date: 2005-02-02
forum: Server Platforms
---

### Post by ThePainter on 2005-02-02
Hi,
Ive installed Firestarter as explained in ubuntuguide.org but there is no option in it to start the firewall on boot up.
I have put it into the session startup so it starts on boot but it asks for my password every time I boot up cause it will only run in root.
If I dont start it this way it doesnt show up in the process list.
Is this really necessary or am I missing something ?

---

### Post by ubuntu UsER on 2005-02-02
[QUOTE=ThePainter]Hi,
Ive installed Firestarter as explained in ubuntuguide.org but there is no option in it to start the firewall on boot up.
I have put it into the session startup so it starts on boot but it asks for my password every time I boot up cause it will only run in root.
If I dont start it this way it doesnt show up in the process list.
Is this really necessary or am I missing something ?[/QUOTE]

There is nice howto somewhere in this forum, but in my opinion you don't have to have your firewall gui working all the time. I think you should create some rules in your firewall and close gui, but firewall will be still working :)

---

### Post by machiner on 2005-02-02
In Linux there is a firewall built right into the kernel. Starting at boot time. (Cntrollable)

All firestarter does is write a script that introduces rules into the script running iptables.

Yo are protected regardless of whether you see the GUI for Firestarter starting at boot -- 

As well, in the options for Firestarter there are tick-marks that you might apply to ensure Firestarter re-starts when your ip changes, when you boot, etc.

It's in there.

---

### Post by piedamaro on 2005-02-02
[QUOTE=machiner]In Linux there is a firewall built right into the kernel. Starting at boot time. (Cntrollable)

All firestarter does is write a script that introduces rules into the script running iptables.

Yo are protected regardless of whether you see the GUI for Firestarter starting at boot -- 

As well, in the options for Firestarter there are tick-marks that you might apply to ensure Firestarter re-starts when your ip changes, when you boot, etc.

It's in there.[/QUOTE]
 Issue a:
sudo iptables --list

if you see a ton of output your firewall is running. As machiner said, it doesn't depend on the gui (of course :D)

---

### Post by jdodson on 2005-02-03
[QUOTE=ThePainter]Hi,
Ive installed Firestarter as explained in ubuntuguide.org but there is no option in it to start the firewall on boot up.
I have put it into the session startup so it starts on boot but it asks for my password every time I boot up cause it will only run in root.
If I dont start it this way it doesnt show up in the process list.
Is this really necessary or am I missing something ?[/QUOTE]

if you install firestarter, by default in ubuntu it loads when your computer does.  ubuntu loads all deamons/servers by default(or at least it seems to).

---

### Post by ubervan on 2005-03-17
Hi

You may want to check out the following FAQ on the FS website:
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by mseney on 2005-03-17
These are my results without a firewall running on pretty much a default Hoary 5.04 Preview install.

[http://scan.sygatetech.com/probe.html](http://scan.sygatetech.com/probe.html)

We have determined that your IP address is xxx.xxx.xxx.xxx
Operating System = Linux i686
Browser = Firefox 1.0
Unable to determine your computer name!
Unable to detect any running services!
* Note I changed my actual IP that it found to xxx.xxx.xxx.xxx

---

### Post by Dana on 2005-03-20
Firestarter works pretty well for me. However occasionally it seems to prohibit me from obtaining or sending email from Evolution. Then I stop Firestarter, check/send email and restart Firestarter. And then I have no problem... until the next time it happens which fortunately is rarely. See the same sort of thing happen on a racing web site that has a live timing and scoring java applet. When the java applet initializes it does not work properly but if I stop Firestarter, restart the java applet and then restart Firestarter the applet works properly for the remainder of the session. Any thoughts on what is going on?

---

### Post by Nano on 2005-03-20
However, if you still want to load it at startup what you have to do is the following:
1) Add firestarter to  /etc/sudoers:
add: "username ALL=NOPASSWD:/usr/sbin/firestarter"
right after "username ALL=(ALL) ALL"
where "username" is YOUR user name

2) Add it to the start up programs in your session conf:
Go to System->Prefs->Sessions and click the tab "Start up programs" (the last)
and add: "gksudo /usr/sbin/firestarter" as command.

Next time you boot it should boot automatically.

CHeers

---

### Post by bored2k on 2005-03-21
[QUOTE=jdodson]if you install firestarter, by default in ubuntu it loads when your computer does.  ubuntu loads all deamons/servers by default(or at least it seems to).[/QUOTE]
 Nice to know. I had that doubt myself .

---

### Post by G_u_s on 2005-10-16
is it also true that the ICS function of Firestarter remains loaded even when Firestarter itself is not ? i seem to remember that it is NOT the case, but i know precious little about unix systems...

---

### Post by Pietr The Engineer on 2007-04-03
Late in the day but I've only been using Linux a week, but I've been around the block generally.
If Firestarter is blocking mail (in my case outgoing), I found that you have to change the default preferences so that rules are applied **immediately**.
This saves stopping and starting, or worse, rebooting.
:popcorn:

---

