---
title: "HOWTO: Graphical IP Blocker"
date: 2007-08-20
forum: Tutorials
---

### Post by uljanow on 2007-08-20
This article describes how to block lists with a graphical front-end called **IPblock**. No knowledge of networking, firewalls or command-line configuration are needed. Due to the way **IPblock** works it doesn't change the behavior of existing firewalls which makes it compatible ** [1]** with other firewall applications like **ufw**, **shorewall** or **fireHOL**. This howto is intended for Beginners and was tested on Ubuntu Feisty, Gutsy, Hardy, Intrepid, Jaunty and Karmic (32-bit and 64-bit).

**[SIZE="3"]Installation[/SIZE]**
Add the iplist repository to your sources.list. Make sure to use the correct sources.list that corresponds to your current distribution:
[LIST]
[*]Ubuntu 10.10 "**Maverick** Meerkat":
```
sudo wget http://iplist.sf.net/sources.list.d/maverick.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 10.04 LTS "**Lucid** Lynx":
```
sudo wget http://iplist.sf.net/sources.list.d/lucid.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 9.10 "**Karmic** Koala":
```
sudo wget http://iplist.sf.net/sources.list.d/karmic.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 9.04 "**Jaunty** Jackalope":
```
sudo wget http://iplist.sf.net/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 8.10 "**Intrepid** Ibex":
```
sudo wget http://iplist.sf.net/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 8.04 "**Hardy** Heron":
```
sudo wget http://iplist.sf.net/sources.list.d/hardy.list -O /etc/apt/sources.list.d/iplist.list
```
[/LIST]
The key of the signed packages can be imported like this: 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C6E3D905C8BCD56BB02E6E0B39456311108B243F
```
There is also another way to import the key. You could save the [pub key]("http://iplist.sourceforge.net/uljanow.gpg") to a file and import it through *System->Administration->Software Sources->Authentication->Import Key-file*.

After an update of the Software sources iplist can be installed with any package manager. E.g.:
```
sudo apt-get update
sudo apt-get install iplist
```

Note: If **sun-java*** is installed by **gdebi** it requires to open the terminal part of **gdebi** and accept sun's license agreement.
[COLOR="Red"]Packages for Feisty and Gutsy can be found in the [0.19 release]("https://sourceforge.net/project/showfiles.php?group_id=198679&package_id=238704&release_id=571106").[/COLOR]

After the installation **IPblock** can be found in *Applications -> Internet -> IPblock*.

[IMG]http://iplist.sourceforge.net/img/tab_log.png[/IMG]

**[SIZE="3"]Lists[/SIZE]**

The default choice for lists is similar to **PeerGuardian**.
[LIST]
[*]**level1.gz** - Anti-P2P organizations and known government addresses
[*]**ads-trackers-and-bad-pr0n.gz** - Advertising and data tracker servers
[*]**spyware.gz** - Malicious spyware and adware servers
[*]**edu.gz** - Educational institutions and universities
[*]**bogon.gz** - Spoofed IP-addresses
[/LIST]
These lists are maintained by [www.bluetack.co.uk](www.bluetack.co.uk) [(list descriptions)]("http://iplist.sourceforge.net/faq.html#0x02a"). Custom p2p or dat lists can easily be added. Note that lists can optionally be compressed with gzip.
The URL file **/etc/ipblock.lists** contains list descriptions.

[IMG]http://iplist.sourceforge.net/img/tab_lists.png[/IMG]

**[SIZE="3"]Settings[/SIZE]**

All options can be configured in this and the network tab. Auto-updating lists is important and the default choice of 2 days is reasonable. Using out-of-date lists is not  recommended.
To ignore outgoing network traffic like HTTP or EMAIL (pop3) use the ignored ports section. Note that http and dns (domain) is ignored by default. The connection-settings specify which type of connections should be filtered.

[IMG]http://iplist.sourceforge.net/img/tab_settings.png[/IMG][IMG]http://iplist.sourceforge.net/img/tab_network.png[/IMG]

[COLOR="Red"]**[1] NOTE: IPblock** needs to be started after other firewall applications. [/COLOR]   

**[SIZE="5"][FAQ on iplist.sf.net]("http://iplist.sourceforge.net/faq.html")[/SIZE]**

---

### Post by maynoth on 2007-08-21
awesome stuff thank you so much!!!!!

one less reason to use windows...

---

### Post by maynoth on 2007-08-21
just tried it out, can you have it set up to add url's from bluetack... instead of having to download the file manually?

---

### Post by uljanow on 2007-08-21
> **maynoth said:**
> just tried it out, can you have it set up to add url's from bluetack... instead of having to download the file manually?

**/usr/share/doc/iplist/README.lists** already contains many additional lists from bluetack. To use those just add the basename in the list section.
e.g. 
README.lists contains "http://www.bluetack.co.uk/config/spider.gz". So adding spider.gz in *List tab -> Add* and doing an update should work.

---

### Post by maynoth on 2007-08-21
oh wow... Just wow...

man you Absoflippinglutely rock!!!1


THANK YOU SO MUCH....

---

### Post by pelle.k on 2007-08-21
This is good news! I do run ipblock, but what i didn't know is that they nowadays include a GUI. I must say ipblock seems very promising.
I suggest you (uljanow) check out my [moblock FAQ]("http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock"), and implement something like it... people are gonna want to know more.

Good luck!

---

### Post by berttt on 2007-08-21
Thanks for the info, has anyone had problems with this yet? Having problems getting it to work.

---

### Post by maynoth on 2007-08-21
worked great for me,  the program launcher is in applications-->internet--->ipblock

---

### Post by berttt on 2007-08-23
I installed it using gdebi and everything went ok, i can update the lists but when i "enable" it locks up. It doesn't change from disabled and it blocks all connections to and from the internet. Not sure why :( :(

---

### Post by antharr on 2007-08-23
I installed Ipblock and the installation went fine, however it will not start when I click on it. Anyone have any idea why it would do this?

---

### Post by kraymore on 2007-08-23
is it possible to implement and fetch peerguardian lists (updated lists) so that i might not have to run moblock on gutsy ?

thank you

---

### Post by uljanow on 2007-08-24
> **berttt said:**
> I installed it using gdebi and everything went ok, i can update the lists but when i "enable" it locks up. It doesn't change from disabled and it blocks all connections to and from the internet. Not sure why :( :(

I assume you wait long enough because loading lists takes some time. Could you post/attach the output of
```
cat /var/log/syslog | grep iplist
```

---

### Post by uljanow on 2007-08-24
> **antharr said:**
> I installed Ipblock and the installation went fine, however it will not start when I click on it. Anyone have any idea why it would do this?

Can you start the GUI from command-line ?
```
sudo ipblock -g
```

---

### Post by ffejrey on 2007-08-24
Can I run this in the background somehow?

---

### Post by john_navarro on 2007-08-24
sudo ipblock -g &

---

### Post by ffejrey on 2007-08-25
When I do that the GUI still shows up, is there a way so I don't see the GUI?

---

### Post by uljanow on 2007-08-25
> **ffejrey said:**
> When I do that the GUI still shows up, is there a way so I don't see the GUI?

Running ipblock in background can be done by using it from command-line: 
```
Usage: ipblock [options]
Options:
 -s    start blocking
 -d    stop blocking
 -r    restart script
 -u    update lists
 -c    convert lists to ipl format
 -g    start ipblock GUI
 -l    show status
 -h    show this help

```

---

### Post by uljanow on 2007-08-25
> **kraymore said:**
> is it possible to implement and fetch peerguardian lists (updated lists) so that i might not have to run moblock on gutsy ?

thank you

peerguardian, moblock and ipblock all use lists from bluetack.co.uk. But the peerguardian list names differ ([http://peerguardian.sourceforge.net/lists/](http://peerguardian.sourceforge.net/lists/)).

---

### Post by spockrock on 2007-08-25
Hi guys I use moblock is there any difference between this and moblock????  Any differences between the two apps?

---

### Post by uljanow on 2007-08-29
> **spockrock said:**
> Hi guys I use moblock is there any difference between this and moblock????  Any differences between the two apps?

The main difference is that iplist is customizable with iptables which e.g. allows to REJECT packets or to keep existing firewall configurations.

---

### Post by maynoth on 2007-08-29
one request for a feature,  could you add the option to exclude msn, yahoo, and aim, and icq ports

---

### Post by maynoth on 2007-08-29
btw thanks for making it easier to add all the lists... your program rules!!!!


I love the new 0.15!

thank you so much!!!!

---

### Post by nowshining on 2007-08-30
Great but it would be nice if there were a way to close it and it straight to the tray. :) anyway it seems like igmp is not blocked by my firewall like I'd liked.. :( I hate juno and their IGMP....

---

### Post by nowshining on 2007-08-30
however this is a great way to see if your firewall is working, as I got some some TCP ins that are not blocked by my firewall and udp..lolz

edit: and no I do not have any ports open at this mement..


edit2 by the above I mean I use arno-iptables-firewall and it works great and is EASY to setup and easy to input custom rules without all the hassle and I highly suggest it to anyone out there and well without having any p2p right now and all ports suppose to be closed and stuff it logged juno's IGMP packets coming in and blocked it, went to my firewall custom rules .conf file and noticed I didn't put the rules I asked for in there- done that, saved and restarted the firewall thru the terminal and Viola no IGMP blocks from it...and it's been clear for awhile now, without this i'd never known.. :) ty for finding it, etc..  now i'll have to session it to startup upon reboot and block in the background... hehehe ;) and it also helped me learn that i didn't have to put the $ in from of every custom rule..


edit3: nope so i'm using this program to block it..

---

### Post by nowshining on 2007-08-30
> **maynoth said:**
> one request for a feature,  could you add the option to exclude msn, yahoo, and aim, and icq ports

to do that go to the settings tab

find TCP see the box next to it, check it then input the tcp ports it uses, if udp check the UDP checkbox, in either box you want to unblock I believe you do the folloing, example unblock port 8080 and 800

8080, 800


:)

---

### Post by uljanow on 2007-08-30
> **maynoth said:**
> one request for a feature,  could you add the option to exclude msn, yahoo, and aim, and icq ports

According to my /etc/services those ports are "msnp mmcc aol". As nowshining said just enter that string in the tcp inputbox without ".

---

### Post by nowshining on 2007-08-30
by the way i tried sudo ipblock -s to start hidden but it never did start up the commands are actually

Usage: ipblock {start|stop|restart|update|convert|status}

ipblock start
ipblock stop
ipblock restart
ipblock update
ipblock convert
ipblock status


with of course sudo at the beginning.. :)

---

### Post by nowshining on 2007-08-30
okay i got it working to startup on reboot :) 

first these are the AIM, Jabber (also googlechat), msn, yahoo, icq ports

open er up DO NOT ENABLE YET

check mark next to TCP
in the box copy & paste

```

msnp mmcc aol xmpp-client

```

Open up a terminal and STOP iptables etc. or disable your firewall by pressing stop on the GUI or whatever..

Go back to ipblock
go to tab Protection
then click the Enable button

Restart the Firewall - if stopped iptables use the same command but at the end instead of stop put start or restart hit enter..

To get it to start up on every boot and protect invisible

1. Set EVERYTHING UP TO ALLOW THRU THE SETTINGS OF THIS PROGRAM, esp.. HTTP and ESP. if you're using ALL THE LISTS like i did it's called pipfilter in the bluetack url at the end.. :) and check mark everything you want such as FTP, etc...again and make sure that if you want updates every day or so to make sure it's checked at least.. ;)

2. open up your sudoers file by opening up a terminal and doing the following command:
```

export EDITOR=gedit && sudo visudo

```

At the end input & change USERNAME to your username you log in as

USERNAME ALL= NOPASSWD: /usr/sbin/ipblock

save

exit

back at terminal you should be

next open up start - preferences - sessions

click new

for name input 

ipblock

for command input

sudo /usr/sbin/ipblock -start -s

click ok, go to tab Session Options

click save the current session. :)

exit the Sessions program

now reboot...


edit:

to read the logs and to check and make sure it's working do the following

open up a terminal and enter:

sudo ipblock status

hit enter :)

---

### Post by nowshining on 2007-08-30
I forgot to add with my firewall setup + Huge Hosts file + this going :) My dialup Flies...I'm serious.. :P pages load up WAY quicker.. hehehe

---

### Post by rajvirnijjar on 2007-08-30
Hello,

I am trying to install ipblock but I am having trouble. I downloaded the ipblock-0.15.tar.gz file from the link. Then I extracted it using tar. Then I used gdebi but the ipblock does not show up in applications>internet>ipblock after i use gdebi. I am new to linux so I am not sure what I am doing wrong. Can someone please help me out. Thanks in advance.

---

### Post by nowshining on 2007-08-30
hi if your using ubuntu download the .deb file. :) it's already ready to go and then double click on it - and in the upper right hit install - in other words it is pre-packaged... :)

but it will connect you to the internet to download the needed  dependency files tho..


edit - yes deb is debian and ubuntu is debian based so just about anything .deb is installable to ubuntu.. ;)

pick the .deb file that corresponds to your computer

1386 for x86 computers - 32 bits
amd64 for 64 bit computers

and choose whether you have Gutsy or Feisty - gutsy is in development you prob have feisty..


edit2/3: i had to download  	iplist_0.15-0feisty1_i386.deb   for my computer...

---

### Post by onestep on 2007-09-06
> **nowshining said:**
> okay i got it working to startup on reboot :) 


Great tutorial! It now starts on boot up and works good!!

One question, if I need to how do I start up the GUI?

I used "$ sudo ipblock stop" to stop the app and then started it up with $ sudo ipblock start -g". It runs, but not in GUI mode. Any ideas?

Thanks from a nOOb who's learning!

---

### Post by uljanow on 2007-09-07
> **onestep said:**
> One question, if I need to how do I start up the GUI?

I used "$ sudo ipblock stop" to stop the app and then started it up with $ sudo ipblock start -g". It runs, but not in GUI mode. Any ideas?

```
$ sudo ipblock -dg
```This stops the already running session and starts the GUI.

Those "start" or "stop" parameters are just shortcuts and only useful if ipblock is used as an init-script. 

At the moment only the GUI has an auto-update functionality. But it's possible to force an update "$ sudo ipblock -u" if ipblock is used only via command-line.

---

### Post by onestep on 2007-09-07
> **uljanow said:**
> ```
$ sudo ipblock -dg
```This stops the already running session and starts the GUI.

When I do that, it stops the running session but does not display the GUI. This is what the terminal shows;

```
~$ sudo ipblock -dg
Stopping ipblock...done.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:91)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.Toolkit$2.run(Toolkit.java:836)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:828)
        at java.awt.Toolkit.getEventQueue(Toolkit.java:1678)
        at java.awt.EventQueue.invokeLater(EventQueue.java:954)
        at org.ipblock.gui.ipblockUI.main(Unknown Source)
```

---

### Post by uljanow on 2007-09-07
Sometimes security settings prohibit to connect to  another user's X-screen.  
I suggest to stop it (sudo ipblock -d) and start it through *Applications -> Internet -> ipblock* as usual.

---

### Post by onestep on 2007-09-07
> **uljanow said:**
> 
I suggest to stop it (sudo ipblock -d) and start it through *Applications -> Internet -> ipblock* as usual.

I can stop ipblock as instructed, but starting it through *Applications -> Internet -> ipblock* does not work. It has not worked since I followed the instructions on post #28 to make ipblock run in the background, and automatically start up at boot. 

The only reason I want to have GUI access is to do a manual update of the filters. 

I've added the command "sudo ipblock -u" to Gnome Schedule 1.0.0 If I set it up correctly it will update every 2 days. Any idea how can I check if the update actually takes place?

---

### Post by uljanow on 2007-09-07
> **onestep said:**
> I can stop ipblock as instructed, but starting it through *Applications -> Internet -> ipblock* does not work. It has not worked since I followed the instructions on post #28 to make ipblock run in the background, and automatically start up at boot. 

The only reason I want to have GUI access is to do a manual update of the filters. 

I've added the command "sudo ipblock -u" to Gnome Schedule 1.0.0 If I set it up correctly it will update every 2 days. Any idea how can I check if the update actually takes place?

I've tried the instructions from post #28 and I get the same behavior / error you've posted. To fix this I would undo the changes (the sudoers entry and the gnome session manager entry).  
To start ipblock at boot just add this line to **/etc/rc.local** (as root)
```
/usr/sbin/ipblock -s
``` The line should be before "exit 0".

Now you should be able to stop ipblock and start the GUI in both ways.

I think updating with Gnome Scheduler might not work. But adding this line to **/etc/crontab** (as root) will do it
> 30 18    * * *   root    /usr/sbin/ipblock -u
Lists are updated daily (18:30).

The GUI shows the last update time regardless of how the update took place. Alternatively check the last modified time:
```
ls -l /var/cache/iplist/.update-stamp
```

---

### Post by onestep on 2007-09-08
Thank you!

ipblock now loads at boot to run in the background _and_ I'm able to run it's GUI when I want to!

This is why the Ubuntu Linux community is so GREAT!

---

### Post by nowshining on 2007-09-12
by the way to do an update of the filters open up a terminal and do the following

sudo ipblock -u

or

sudo ipblock update


:)

edit:

to also see the logs

do the following

sudo ipblock status

---

### Post by maynoth on 2007-09-12
Bluetack.co.uk has been down for several days now,  I have been wondering whats going on.     Then I realized my ISP is blocking my connection to them.  I can access the site fine and manually download the files using tor.    Would it be too much trouble to be able to have IPBlock use tor to update the lists?    

I can manually update using a web browser and TOR

---

### Post by nowshining on 2007-09-12
lolz Odd is your ISP copper.net, because I am using Juno with copper.nets DNS servers and well If I use junos than I can download the pipfilter, if I use copper.nets then I get a cannot connect attempt.. :/


as for your question - you should be able to to modify the proxy settings in connection or the place where it asks for that kind of info. I fogot.. :) plus that I cannot open ipblock gui the way I have it setup and plus that gives a bit of security if another person doesn't know how to use the command line,

---

### Post by uljanow on 2007-09-12
> **maynoth said:**
> Bluetack.co.uk has been down for several days now,  I have been wondering whats going on.     Then I realized my ISP is blocking my connection to them.  I can access the site fine and manually download the files using tor.    Would it be too much trouble to be able to have IPBlock use tor to update the lists?    

I can manually update using a web browser and TOR

Just open **/usr/sbin/ipblock** (as root) and add the following at line 31 
```
export http_proxy="127.0.0.1:8118"
``` If you're not using TOR+Privoxy then you could take the proxy's IP-address and port from your web-browser settings.

---

### Post by nowshining on 2007-09-12
ahh working for me now, probably because the Second DNS just craps out on the first one. In other words using .22 will go nowhere except to query .21

---

### Post by sefs on 2007-09-28
So just to confirm.  This works perfectly with iptables & firestarter, and there are no conflicts?  One does not disable the other? They can be run together in peace & love?

PS: we really need that tray icon for the gui :D

Good work guys.

---

### Post by Nooreazy on 2007-09-28
HEY!! this thing actaully works 
thx

---

### Post by Nooreazy on 2007-09-28
How can i know if its working? o_0

---

### Post by sefs on 2007-09-28
When you enable it ... try browsing to microsoft.com or mpaa.org, and report back what happens :D

Also if you start up frostwire with this thing enable, do a search on a popular song like Rihanna's "shut up and drive"  and watch the logs (which updates in realtime it looks like) you will see many evil-doers being blocked :D

---

### Post by Nooreazy on 2007-09-28
> **sefs said:**
> When you enable it ... try browsing to microsoft.com or mpaa.org, and report back what happens :D

Also if you start up frostwire with this thing enable, do a search on a popular song like Rihanna's "shut up and drive"  and watch the logs (which updates in realtime it looks like) you will see many evil-doers being blocked :D
Oh yeah it worked :guitar:. 
it wont let me enter mpaa site lol.

---

### Post by nowshining on 2007-09-29
u can have it allow port 80 if u'd like and other custom things if it gets in ur way. :)

---

### Post by aparigraha on 2007-09-30
> **sefs said:**
> So just to confirm.  This works perfectly with iptables & firestarter, and there are no conflicts?  One does not disable the other? They can be run together in peace & love?

PS: we really need that tray icon for the gui :D

Good work guys.

I have iptables and ipblock running as well and no problems so far at all. It's been running for days without any hassle.:)

For the tray icon u can try AllTray:
```
sudo apt-get install alltray
```

start it with:
```
sudo alltray "ipblock -g"
```
try "man alltray" or "man ipblock" for more commands and help

THX for the great HOWTO!

---

### Post by twinszg on 2007-10-04
I need help. 
When I press enable button I get error message " iplist(9518);error cant find level1.gz

---

### Post by Drillbit on 2007-10-04
SOrry, noob question but how do I let uTorrent in? How do I free up it's port using ipblock?

---

### Post by uljanow on 2007-10-04
> **twinszg said:**
> I need help. 
When I press enable button I get error message " iplist(9518);error cant find level1.gz
Try an update before starting it.
If bluetack.co.uk is not responding. I'd temporary remove the list.

---

### Post by uljanow on 2007-10-04
> **Drillbit said:**
> SOrry, noob question but how do I let uTorrent in? How do I free up it's port using ipblock?
Nice combination ;)

Check the TCP box (in the ignored ports section) and enter the port uTorrent listens on. In case ipblock is already running, restart it.

---

### Post by Palmyra on 2007-10-04
Who created ipblock, and why didn't this person just work with peerguardian and moblock?  Moblock is set to become the official peerguardian version on Linux, and ipblock may be useful to those who created Moblock and peerguardian.

---

### Post by outphase on 2007-10-05
How do I set up a whitelist? level1 seems to block Fatwallet.

---

### Post by nowshining on 2007-10-05
open it up and check port 80 or http to allow for it to go thru, you can also and should check ftp, https in advance. :) then do a restart of the program or reload the program, etc.. and the ur done.

---

### Post by nowshining on 2007-10-05
or reload lists if that's what it asks - i forgot - i also uninstalled due to some probs I thought it was casuing which of course found out it wasn't really the cause.

---

### Post by outphase on 2007-10-05
Thanks, it's good now.

---

### Post by uljanow on 2007-10-05
> **Palmyra said:**
> Who created ipblock, and why didn't this person just work with peerguardian and moblock?  Moblock is set to become the official peerguardian version on Linux, and ipblock may be useful to those who created Moblock and peerguardian.

I'm the author and before I started writing iplist/ipblock I looked at the moblock source and decided that it was necessary to write something from scratch with different design choices to put in the features I wanted. But at that time I wasn't thinking about releasing it.

---

### Post by maynoth on 2007-10-06
im glad you did release it it rules!!! thank you so much!

---

### Post by Razzack on 2007-10-07
Seems great but get the following when entering ipblock -g after it has been started:

Exception in thread "main" java.lang.UnsupportedClassVersionError: org/ipblock/gui/ipblockUI (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

-Any ideas...? :confused:

---

### Post by uljanow on 2007-10-07
> **Razzack said:**
> Seems great but get the following when entering ipblock -g after it has been started:
It looks like you're using a java vm version 1.4. However, the GUI requires the version 1.5 or later.

---

### Post by Razzack on 2007-10-08
Had 1.6 installed but not enabled as provider. Got it up and running after: *sudo update-alternatives --config java* and choosing the 1.6. Thanks for the clue :).

---

### Post by Palmyra on 2007-10-14
IPBLOCK is of no use to some people.      

> * level1.gz - Anti-P2P organizations and known government addresses

If you're not using P2P, you don't need this "protection."

>     * ads-trackers-and-bad-pr0n.gz - Advertising and data tracker servers

I am not sure what this is, but ads can be blocked using Firefox extensions.

>     * spyware.gz - Malicious spyware and adware servers

Is there really a fear of spyware on Ubuntu?  I've been using Ubuntu for over a year, and I have never come across spyware even though I download just about anything I see on the Internet.

>     * edu.gz - Educational institutions and universities

I don't understand the reasoning behind this one, but since I don't take my laptop to schools, I am not sure this serves a purpose at all.

>     * bogon.gz - Spoofed IP-addresses

Don't know which about Bogon, but unallocated IPs don't appear to pose a threat.  As long as you're keeping yourself free of problems on the Internet, there's not much you have to worry about.

It seems to me this application is more for people who like messing with the "dangerous" side of the Internet, and do so purposely.

---

### Post by uljanow on 2007-10-15
> **Palmyra said:**
> IPBLOCK is of no use to some people.
ACK. Some people don't even use firewalls or computers at all.

> I am not sure what this is, but ads can be blocked using Firefox extensions.
Blocking hosts on an application based level is one way to do it. Another approach is to use programs such as peerguardian, moblock or ipblock because it is more convenient to do this kind of task in combination with the firewall.

> It seems to me this application is more for people who like messing with the "dangerous" side of the Internet, and do so purposely.
iplist/ipblock is GPL-Software and can be used for any purpose.

---

### Post by dkrus on 2007-10-24
Just tried this out and it is working great...Thanks

---

### Post by maynoth on 2007-10-28
> **Palmyra said:**
>   It seems to me this application is more for people who like messing with the "dangerous" side of the Internet, and do so purposely.

bwhahahah. omfg I think I just hacked up a lung.   is this dude 12 years old or what...

wow...

---

### Post by maynoth on 2007-10-28
btw you can stop IPblock from messing up pidgin by ignoring this string of ports

1024 1863 5050 5190

---

### Post by KubuntuKilledMe on 2007-10-29
I've tried using this program, but i find it impossible.

On the first run i try to click the enable button. It asks if i want to update the lists. I say yes, and it hangs there for 10 minutes until i kill it. 

Now everytime i run it, even after a reboot (!), when i click enable it shows an empty dialog. Actually all dialogs shown are empty.

Also does it run at startup? Do i have to keep the window open for it to block? All of these questions would be fascinating if it would, you know, do ANYTHING.

---

### Post by uljanow on 2007-10-29
> **KubuntuKilledMe said:**
> On the first run i try to click the enable button. It asks if i want to update the lists. I say yes, and it hangs there for 10 minutes until i kill it.
If there were no error messages, it was probably still downloading.

> Now everytime i run it, even after a reboot (!), when i click enable it shows an empty dialog. Actually all dialogs shown are empty.
Does this still occur after a successful update? 

> Also does it run at startup?It doesn't start at boot. It can be done by adding "/usr/sbin/ipblock -s" to /etc/rc.local. But to use the GUI it would require to stop ipblock manually (sudo ipblock -d).

> Do i have to keep the window open for it to block?Yes. Running it in background can be done by using ipblock from the command-line (man 8 ipblock).

---

### Post by MicroChris on 2007-10-30
How do I uninstall this? I don't want it anymore..

---

### Post by uljanow on 2007-10-30
```
aptitude purge iplist
```

---

### Post by NoSmokingBandit on 2007-10-30
When i run it nothing happens. This is the terminal ouput:

steven@steven-desktop:~$ ipblock
error: You must be root to use ipblock
steven@steven-desktop:~$ sudo ipblock
steven@steven-desktop:~$ 

I do that and no windows or anything come up. The process doesnt show up in the system monitor either.

Edit:
Nevermind my problem. I'll just use the built-in ip blocker in deluge with the pg2 lists.

---

### Post by uljanow on 2007-10-30
```
sudo ipblock -h
```This would show the available options.

---

### Post by NoSmokingBandit on 2007-10-30
steven@steven-desktop:~$ sudo ipblock -g
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.EventQueue.invokeLater(libgcj.so.81)
   at org.ipblock.gui.ipblockUI.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...2 more
steven@steven-desktop:~$ 

...is what happens. I have no idea how to even start reading that... :confused:

---

### Post by uljanow on 2007-10-30
It looks like libgj is conflicting with sun's virtual machine (had a similar problem on Debian Etch). If you use sun's vm it is safe to remove gcj to fix this.

```
dpkg --list | grep gcj
```
This will show the version of gcj-<version>-base that can be removed.
```
aptitude remove gcj-<version>-base
```

---

### Post by NoSmokingBandit on 2007-10-30
aha! Runs perfect now. Thanks for the help! :guitar:

---

### Post by NoSmokingBandit on 2007-11-06
Is anyone else unable to load the Level1 block list? I havent been able to get it the past few days :/

---

### Post by kurotsuno on 2007-11-07
installed it got it up and running but few questions.

I've managed to update the level1 list but when I run bit torrent I get no log reports of ips blocked. 

Does this give you information in the graphic interface of ips that have been blocked simaler to peer guardian 2 ?

Also I have a custom list of ips I wish to add how do I go about that pg2 just took the text file but do I have to convert the file into a different file format other than txt for it to use it ?

Seems to work ok just want to get the best out of it.

---

### Post by uljanow on 2007-11-07
> **kurotsuno said:**
> I've managed to update the level1 list but when I run bit torrent I get no log reports of ips blocked. 

Does this give you information in the graphic interface of ips that have been blocked simaler to peer guardian 2 ? Yes. On the first page is a screenshot of blocked BBC ranges while HTTP was not excluded. Try [http://www.bbc.co.uk](http://www.bbc.co.uk) if you use level1.
> Also I have a custom list of ips I wish to add how do I go about that pg2 just took the text file but do I have to convert the file into a different file format other than txt for it to use it ?If the textfile is a p2p or dat file, it should work directly.
> A p2p format looks like this:
name : 127.0.0.1 - 127.0.0.2

A dat file has this format:
127.0.0.1 - 127.0.0.2, <0-255>, name 

---

### Post by NoSmokingBandit on 2007-11-07
i still cant get level1.gz to load. The url im using is the one ipblock has in it, [http://iplist.sf.net/lists/level1.gz.php](http://iplist.sf.net/lists/level1.gz.php)
Is that right? When i click Enable i get the error

iplist[8169]: error: cant find level1.gz

---

### Post by uljanow on 2007-11-07
> i still cant get level1.gz to load. The url im using is the one ipblock has in it, [http://iplist.sf.net/lists/level1.gz.php](http://iplist.sf.net/lists/level1.gz.php)
Is that right? When i click Enable i get the error

iplist[8169]: error: cant find level1.gz[http://iplist.sf.net/lists/](http://iplist.sf.net/lists/) are redirections to bluetack lists. In your case  level1.gz needs to be downloaded via update.

---

### Post by kurotsuno on 2007-11-07
I'm not sure why but I get level1 failed update error alot is a way I can purge the downloaded lists so I can re download them maybe that might clear it up.

---

### Post by NoSmokingBandit on 2007-11-07
lol, that was an easy fix. Thanks a bunch.

---

### Post by Goodson1974 on 2007-11-10
Hi everyone

I've just installed ipblock on my desktop and laptop, and i've configured it to start on boot and run in the background thanks to this wonderful thread!

I'm rather new to this ip blocking business, and the problem i've come across is that i can't access any page on the BBC site.

Is there a way that i can allow the BBC site?

Cheers

I re-read the thread and realised the answer was in there!

---

### Post by C4nc3l on 2007-11-10
I think IPblock is a nice tool...but... don't start in my pc :(
When i try ```
sudo ipblock start
``` and also in GUI it start to work but it never turns to enabled...
In command line it leaves me with ```
 Starting ipblock...
```

At first time it asks me to upload and it was all ok until i try to enable...

Any idea?

---

### Post by uljanow on 2007-11-10
Could you post the output of```
grep iplist /var/log/syslog*
```

---

### Post by cox377 on 2007-11-15
> Dear members and guests,

Regretfully we need to let you all know that in one weeks time the site may be closing indefinitely. Our web hosting bill is currently 3 months behind and without this server in operation there will also be no more blocklist updates possible.

We ask you to make a choice and decide on our future. If you want to help keep us alive then we need your support and donations.

There are literally millions of people downloading our files, however only a very small proportion of people find the time to invest anything in return to ensure that our free services can continue.

Everything we do here is offered free of charge, we make absolutely no money whatsoever. We do however spend quite a lot of time to keep everything running as best as we can for your benefit.

In the event that we cannot afford to continue offering our services for free, then we may need to consider introducing a small subscription/fee based service for downloading the blocklist updates and possibly looking towards using ads throughout the site.

We also need more server mirrors to cope with the excessive bandwidth/traffic associated with hosting the lists.

So now you can either choose to do nothing and let BISS die or help support us so that we can continue to support you. If you find any value in our free programs and services here then please consider donating.

The choice is now yours.

Our donation page is here :
[http://www.bluetack.co.uk/donate/index.html](http://www.bluetack.co.uk/donate/index.html)

Looks like they shall be no more

[HTML]http://www.bluetack.co.uk/forums/index.php?[/HTML]

---

### Post by uljanow on 2007-11-15
I'll set up a mirror.

---

### Post by cox377 on 2007-11-15
Sound's good

I was actually wondering after that how the load could be so easily spread

CoXen

---

### Post by Aldanga on 2007-11-21
Forgive my ignorance, but I can't seem to find an answer to my question in this thread.

Once IP Block is enabled, everything is just peachy, with the status and log and all. After a while, though, I can't access any web pages at all. I've enabled HTTP/HTTPS/FTP, etc. I don't know what has happened.

Any help would be appreciated.

FYI, I'm running 64 Bit Gutsy.

---

### Post by uljanow on 2007-11-21
> After a while, though, I can't access any web pages at all. I've enabled HTTP/HTTPS/FTP, etc. I don't know what has happened.Are you using the latest version 0.15.1 ? Have you restarted IPblock after enabling those ports ?

---

### Post by Aldanga on 2007-11-22
Yes, I am using the latest. I downloaded the package off of sourceforge. I did restart.

If I recall correctly (I have uninstalled the package for the time being) it would disallow web access once I started up my PC. that is, I had ip* load on startup and that is when it would start blocking http, etc.

So, yes. I believe that would qualify as restarting. I also stopped and restarted via terminal.

---

### Post by uljanow on 2007-11-22
It seems like the iplist daemon died for some reason, but iptables was still redirecting traffic to it. The default behaviour of the kernel is to drop those packets.
What does  "grep iplist /var/log/syslog*" show ? How often did this occur and is it reproducible ?

---

### Post by Aldanga on 2007-11-22
> Nov 21 18:28:19 blackathlon iplist[23426]: error: no running iplist instance found 
Nov 21 18:28:42 blackathlon iplist[23562]: error: can't send job to msq 
Nov 21 18:28:49 blackathlon iplist[23593]: error: can't send job to msq 
Nov 21 18:55:08 blackathlon iplist[31578]: error: no running iplist instance found 
Nov 21 18:55:14 blackathlon iplist[31607]: error: iplist needs to be run as root 
Nov 21 19:13:53 blackathlon iplist[9918]: error: no running iplist instance found 
Nov 21 19:13:57 blackathlon iplist[9933]: error: iplist needs to be run as root 
Nov 21 19:17:22 blackathlon iplist[11007]: error: no running iplist instance found 
Nov 21 19:17:48 blackathlon iplist[11134]: error: iplist needs to be run as root 
Nov 21 19:21:26 blackathlon iplist[12251]: error: no running iplist instance found 
Nov 21 20:49:24 blackathlon iplist[9455]: error: no running iplist instance found 
Nov 21 20:49:50 blackathlon iplist[9579]: error: iplist needs to be run as root 
Nov 21 21:30:32 blackathlon iplist[22070]: error: no running iplist instance found 
Nov 21 21:31:39 blackathlon iplist[22430]: error: can't find stop 

That's the log.

It would occur every time I enabled the blocker. It would only allow traffic if I disabled the blocker.

It happens with moblock also, so that leaves me scratching my head. I can't get any IP filter to work so far without blocking web or IM traffic. It seems to work fine with torrent software, but not otherwise, even with the torrents on halt. The only time it lets me continue IM use is when I have an established connection. If I sign out of Pidgin it won't let me sign back in without disabling the blocker.

---

### Post by uljanow on 2007-11-23
Like I thought. If this also happens with moblock then the reason why iplist dies is probably libnetfilter-queue related. But further digging is required.

The following test would redirect all traffic to iplist which accepts it.
```
iptables -I INPUT -j NFQUEUE
echo ":127.0.0.1-127.0.0.1" | iplist -v -p accept -t accept -f /tmp/ipblock.log -l all -
```What does the last command show ?

After the test you can revert the changes by killing iplist with CTRL-C (or "iplist -k") and removing the iptables rule :
```
iptables -D INPUT -j NFQUEUE
```

---

### Post by Aldanga on 2007-11-25
I was having a lot of trouble with my installation, so i did a wipe and install on Thursday.

I reinstalled iptables about two minutes ago, but everything got blocked. It wouldn't even allow me to run the commands you gave me. It said something about iplist needing to be run as root. I did use sudo when I ran the commands, but it just wouldn't work. My PC wouldn't reach any web traffic so I uninstalled the package.


Any more ideas?

---

### Post by kraymore on 2007-11-26
i'm using ipblock.  when i start it from terminal, it starts with no gui.  however when i update from terminal it does not download level1.gz.  how do i get it to download this file ?  it never has.  

thank you

---

### Post by uljanow on 2007-11-26
> **kraymore said:**
> i'm using ipblock.  when i start it from terminal, it starts with no gui.  however when i update from terminal it does not download level1.gz.  how do i get it to download this file ?  it never has.  

The GUI starts with "ipblock -g" (as root). It looks like bluetack.co.uk has a bandwidth issue. But there is a mirror available. To use it edit (as root) **/usr/share/doc/iplist/README.lists** and replace *[http://iplist.sf.net/lists/level1.gz.php](http://iplist.sf.net/lists/level1.gz.php)* with *[http://iplist.sf.net/mirror/level1.gz.php](http://iplist.sf.net/mirror/level1.gz.php)*.
Before updating IPblock should be disabled because it might block those hosts.

// EDIT: ATM IPblock uses the mirror as the default source to help bluetack.co.uk reducing their bandwidth. The lists are hosted on an university network, which is fast and hopefully more reliable. The mirror is updated every 2 days. So there's no need to edit the README.lists.

---

### Post by ace007 on 2007-11-27
Thanks for the tutorial!

---

### Post by onion221 on 2007-11-27
I tried to install this and it froze and wouldn't close so I restarted the computer. Now when i try to install it or install anything else for that matter it won't let me it says only one software management tool is allowed to run at the same time. Nothing else is open but this.

How do I correct this problem?

---

### Post by uljanow on 2007-11-28
> **onion221 said:**
> I tried to install this and it froze and wouldn't close so I restarted the computer. Now when i try to install it or install anything else for that matter it won't let me it says only one software management tool is allowed to run at the same time. Nothing else is open but this.

I would try aptitude or apt-get which are more verbose.
To install the prerequisites manually which are listed on the first page:
```
aptitude install <prerequisites packages>
```Then a simple 
```
dpkg -i ./iplist-<version>_<arch>.deb
```would install the package.

On Fedora you can use yum, which install the prerequisites automatically:
```
yum --nogpgcheck install ./iplist*
```

If an eror occurs, please post the error message.

---

### Post by BassKozz on 2007-12-01
I keep getting the following error message when starting IPblock > iptables: Chain already exists
What gives?

**EDIT**: I rebooted and enabled and I didn't get the error message but now the whole WAN is down, I can't even "ping google.com" :(

---

### Post by uljanow on 2007-12-02
> **B/-\ssKozz said:**
> I keep getting the following error message when starting IPblock 
What gives?This might be caused by double-clicking the enable-button. The message shows that IPblock was already running.   You can stop it with "sudo ipblock -d", so that the error message disappears.

> **EDIT**: I rebooted and enabled and I didn't get the error message but now the whole WAN is down, I can't even "ping google.com" :(

Did you see blocked IPs in the log window ? Maybe your ISP or DNS-server is in the lists.

---

### Post by PhilJ on 2007-12-02
Sorry tried this but it locks up, tells me ipchains exist, I cant connect to anything and I cant shut down the gui. done everything suggested here.
back to  Moblock

Philj

---

### Post by BassKozz on 2007-12-02
> **uljanow said:**
> This might be caused by double-clicking the enable-button. The message shows that IPblock was already running.   You can stop it with "sudo ipblock -d", so that the error message disappears.
Nope, I am not double clicking... When I use "sudo ipblock -d" it tells me that there aren't any instances running (er, something along those lines, I forget the exact message) :(...
I also noticed something else odd, when I click the "Enable" button it turns to "Disable" but the text header still reads "ipblock is Disabled" ???
See screenshots:
**_BEFORE_**

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/IPblock-1.png[/IMG]

**_AFTER_**

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/IPblock-2.png[/IMG]

Weird :confused:

> **uljanow said:**
> 
Did you see blocked IPs in the log window ? Maybe your ISP or DNS-server is in the lists.

Nope nothing is showing in the GUI, I even disabled HTTP blocking and that didn't fix it :(

---

### Post by uljanow on 2007-12-02
> **B/-\ssKozz said:**
> Nope, I am not double clicking... When I use "sudo ipblock -d" it tells me that there aren't any instances running (er, something along those lines, I forget the exact message) :(...
I also noticed something else odd, when I click the "Enable" button it turns to "Disable" but the text header still reads "ipblock is Disabled" ???

Weird :confused:

Nope nothing is showing in the GUI, I even disabled HTTP blocking and that didn't fix it :(

This looks like a bug in the GUI. Can you start it on the command-line ?
```
sudo ipblock -sl
```

---

### Post by BassKozz on 2007-12-02
> **uljanow said:**
> This looks like a bug in the GUI. Can you start it on the command-line ?
```
sudo ipblock -sl
```
Started:```
Starting ipblock...done.
Queue   Policy (mark)   Ranges  Target (mark)   File
0       REPEAT (65534)  237561  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/edu.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz
                                REPEAT (65535)  /var/cache/iplist/spider.gz
1       REPEAT (65534)  237561  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/edu.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz
                                REPEAT (65535)  /var/cache/iplist/spider.gz

Chain input_match (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain output_match (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Last log messages...

```
But now how do I know if it's working? and How can I see what gets blocked, etc... ?

---

### Post by uljanow on 2007-12-03
> **B/-\ssKozz said:**
> But now how do I know if it's working? and How can I see what gets blocked, etc... ?

The output you've posted shows that it's working (iplist daemon is running, iptables rules are set). The logfile is **/tmp/ipblock.log**. Entries with "match=" are blocked IPs. You can still use the GUI to configure IPblock. I'll release a bugfixed Version 0.15.2 soon.

---

### Post by andhar on 2007-12-03
I am very interested in this I will have to try it when I get home from work in the am , will this work with torrentflux? when started from cmd line?

---

### Post by BassKozz on 2007-12-04
> **andhar said:**
> I am very interested in this I will have to try it when I get home from work in the am , will this work with torrentflux? when started from cmd line?
I am by no means an expert on this, but I am pretty sure this will work with any/all torrent applications because it filters the IP's at the system level, so it shouldn't matter which client you use.

This should also filter IP's in any/all applications, because it's filtering the WHOLE box (system).
HTH

---

### Post by BassKozz on 2007-12-06
I don't know what I did, but now I can no longer access my Xubuntu Box remotely via SSH like I used to be able to, and when I connect locally, I can't even ping google.com...
and when I run "ipblock -sl" I get:
```
Starting ipblock...iptables: Chain already exists
```
PLEASE HELP

---

### Post by warchief_ryan on 2007-12-06
cool I was looking for something like to PG.

I don't know if your taking suggesting or not but, a Updating progress bar or percentage somewhere would be great, and the ability to send to tray.

---

### Post by uljanow on 2007-12-07
> **warchief_ryan said:**
> I don't know if your taking suggesting or not but, a Updating progress bar or percentage somewhere would be great, and the ability to send to tray.

Actually I'm still looking for some new ideas. ATM I'm in the planning stage of a rewrite of iplist to enable a clean server/client model in order to write a more powerful GUI, probably in gtk+. But this will take some time.
A new feature e.g. will be to have 3 kinds of lists (allow, block, exclude).

---

### Post by flehnerz on 2007-12-07
> **B/-\ssKozz said:**
> Started:```
Starting ipblock...done.
Queue   Policy (mark)   Ranges  Target (mark)   File
0       REPEAT (65534)  237561  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/edu.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz
                                REPEAT (65535)  /var/cache/iplist/spider.gz
1       REPEAT (65534)  237561  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/edu.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz
                                REPEAT (65535)  /var/cache/iplist/spider.gz

Chain input_match (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain output_match (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            reject-with tcp-reset 
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Last log messages...

```
But now how do I know if it's working? and How can I see what gets blocked, etc... ?

I tried starting IpBlock up in this manner and it still gives me the same error. MOblock is disabled as well. What gives?

---

### Post by uljanow on 2007-12-08
> **flehnerz said:**
> I tried starting IpBlock up in this manner and it still gives me the same error. MOblock is disabled as well. What gives?

Is this resolved with the version 0.16 ?

---

### Post by uljanow on 2007-12-08
> 2007-12-8 

	* release (0.16)
	* minor GUI bugfixes 
	* improved robustness of IPblock
	* starting IPblock takes less time
	* changed max files per queue to 32
	* iplist doesn't terminate on unsupported file types
	* minor changes to logging
	* added IPTABLES_CHAIN option
	* added IPTABLES_LOG option
	* added http_proxy option
	* added DEBUG switch
1

---

### Post by naminem on 2007-12-08
when i start ipblock, i can't access the internet.

i have allowed for http and https.

but when i allow certain ports in UDP, it works.

can anyone tell me what's up? i'm using swiftfox btw.


Edit: i live in a dorm at a university

---

### Post by uljanow on 2007-12-09
> **naminem said:**
> when i start ipblock, i can't access the internet.

i have allowed for http and https.

but when i allow certain ports in UDP, it works.
Maybe your DNS-server is in the lists. Try to ignore UDP port 53.

> Edit: i live in a dorm at a university
I would remove the edu.gz lists, if you're using it.

---

### Post by junkalam on 2007-12-09
Anyone know how to exclude a specific ip from being blocked without manually editing the blocklists? I'm having trouble listening to some shoutcast streams...

thanks..

---

### Post by onion221 on 2007-12-09
i scanned with rkhunter&chkrootkit and i found this

[16:11:26]   Checking /dev for suspicious file types         [ None found ]
[16:11:26]   Checking for hidden files and directories       [ Warning ]
[16:11:26] Warning: Hidden directory found: /etc/.java
[16:11:26] Warning: Hidden directory found: /dev/.static
[16:11:26] Warning: Hidden directory found: /dev/.udev
[16:11:26] Warning: Hidden directory found: /dev/.initramfs
[16:11:26] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)

Did ipblock create these hidden directory's?

---

### Post by airtonix on 2007-12-09
maaaaaan, java sucks

---

### Post by uljanow on 2007-12-10
> **onion221 said:**
> i scanned with rkhunter&chkrootkit and i found this

[16:11:26]   Checking /dev for suspicious file types         [ None found ]
[16:11:26]   Checking for hidden files and directories       [ Warning ]
[16:11:26] Warning: Hidden directory found: /etc/.java
[16:11:26] Warning: Hidden directory found: /dev/.static
[16:11:26] Warning: Hidden directory found: /dev/.udev
[16:11:26] Warning: Hidden directory found: /dev/.initramfs
[16:11:26] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)

Did ipblock create these hidden directory's?

No.

---

### Post by Difranco1911 on 2007-12-21
Just recently IPBlock no longer works.   I click on the program it screen opens, then closes without any error.  I tried uninstalling it and downloading a new package and re-installing but that did not help.

Advice?

---

### Post by uljanow on 2007-12-21
> **Difranco1911 said:**
> Just recently IPBlock no longer works.   I click on the program it screen opens, then closes without any error.  I tried uninstalling it and downloading a new package and re-installing but that did not help.
Does "sudo ipblock -g" show any error messages ?

---

### Post by Difranco1911 on 2007-12-21
Here is what I got

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b58758dbe11, pid=8425, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/difranco/hs_err_pid8425.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by Difranco1911 on 2007-12-21
Okay I've included the referenced log file.

```


---------------  T H R E A D  ---------------

Current thread (0x0000000000609000):  JavaThread "main" [_thread_in_vm, id=8427, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609000, RBX=0x0000000000609000, RCX=0x0000000000609000, RDX=0x00002b5874b9a280
RSP=0x00000000400fe840, RBP=0x00000000400fe870, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd78783, R11=0x00002b587584b2f0
R12=0x0091af1000000009, R13=0x0000000000609000, R14=0x00000000400fe910, R15=0x00002b5875ce16c0
RIP=0x00002b58758dbe11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe840)
0x00000000400fe840:   00000000400fe960 00002aaaaef34fd0
0x00000000400fe850:   0000000000000101 00002aaaaef34fd0
0x00000000400fe860:   00000000400fe910 0000000000609000
0x00000000400fe870:   00000000400fe8e0 00002aaaabd787b0
0x00000000400fe880:   00000000008a19f8 00000000008a1a18
0x00000000400fe890:   00000000008a1a20 00000000008a1a20
0x00000000400fe8a0:   00000000400fe8a0 0000000000000000
0x00000000400fe8b0:   00000000400fe910 00002aaaaef38a48
0x00000000400fe8c0:   0000000000000000 00002aaaaef34fd0
0x00000000400fe8d0:   0000000000000000 00000000400fe900
0x00000000400fe8e0:   00000000400fe960 00002aaaabd6c342
0x00000000400fe8f0:   0000000000000000 00002aaaabd74cee
0x00000000400fe900:   0091af1000000009 00000000008a1a00
0x00000000400fe910:   00002aaaceb990c0 00000000000000ff
0x00000000400fe920:   00000000400fe920 00002aaaaf580947
0x00000000400fe930:   00000000400fe978 00002aaaaf583e10
0x00000000400fe940:   0000000000000000 00002aaaaf580960
0x00000000400fe950:   00000000400fe900 00000000400fe970
0x00000000400fe960:   00000000400fe9c0 00002aaaabd6c2b8
0x00000000400fe970:   0091af1000000009 00002aaaabd6c1e9
0x00000000400fe980:   00000000400fe980 00002aaaaf580a1c
0x00000000400fe990:   00000000400fe9e0 00002aaaaf583e10
0x00000000400fe9a0:   0000000000000000 00002aaaaf580a40
0x00000000400fe9b0:   00000000400fe970 00000000400fe9d0
0x00000000400fe9c0:   00000000400fea28 00002aaaabd6c2b8
0x00000000400fe9d0:   0000000000000009 0091af1000000000
0x00000000400fe9e0:   0000000000000000 00000000400fe9e8
0x00000000400fe9f0:   00002aaaaf30e989 00000000400feab8
0x00000000400fea00:   00002aaaaf32b5c8 0000000000000000
0x00000000400fea10:   00002aaaaf30ec18 00000000400fe9d0
0x00000000400fea20:   00000000400feac0 00000000400feb00
0x00000000400fea30:   00002aaaabd6c11a 0000000000000000 

Instructions: (pc=0x00002b58758dbe11)
0x00002b58758dbe01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002b58758dbe11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

Stack: [0x0000000040000000,0x0000000040101000],  sp=0x00000000400fe840,  free space=1018k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x5c9e11]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x30ec06]
V  [libjvm.so+0x30fe0d]
V  [libjvm.so+0x3102f1]
V  [libjvm.so+0x389aaa]
V  [libjvm.so+0x3943fa]
C  [libjava.so+0x1242d]  Java_java_lang_Class_forName0+0x15d
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x39b888]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x33b231]
V  [libjvm.so+0x3583d5]
C  [libjli.so+0x3abd]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00000000008afc00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=8438, stack(0x0000000040b0b000,0x0000000040c0c000)]
  0x0000000000762000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=8436, stack(0x0000000040909000,0x0000000040a0a000)]
  0x000000000075f400 JavaThread "CompilerThread1" daemon [_thread_in_native, id=8435, stack(0x0000000040808000,0x0000000040909000)]
  0x000000000075b400 JavaThread "CompilerThread0" daemon [_thread_in_native, id=8434, stack(0x0000000040707000,0x0000000040808000)]
  0x0000000000759c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=8433, stack(0x0000000040606000,0x0000000040707000)]
  0x0000000000732400 JavaThread "Finalizer" daemon [_thread_blocked, id=8432, stack(0x0000000040505000,0x0000000040606000)]
  0x0000000000730c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=8431, stack(0x0000000040404000,0x0000000040505000)]
=>0x0000000000609000 JavaThread "main" [_thread_in_vm, id=8427, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x000000000072b000 VMThread [stack: 0x0000000040303000,0x0000000040404000] [id=8430]
  0x0000000000764000 WatcherThread [stack: 0x0000000040a0a000,0x0000000040b0b000] [id=8437]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 3584K, used 2776K [0x00002aaaceb90000, 0x00002aaacef90000, 0x00002aaad9630000)
  eden space 3072K, 90% used [0x00002aaaceb90000,0x00002aaacee462f0,0x00002aaacee90000)
  from space 512K, 0% used [0x00002aaacef10000,0x00002aaacef10000,0x00002aaacef90000)
  to   space 512K, 0% used [0x00002aaacee90000,0x00002aaacee90000,0x00002aaacef10000)
 PSOldGen        total 5312K, used 0K [0x00002aaab9630000, 0x00002aaab9b60000, 0x00002aaaceb90000)
  object space 5312K, 0% used [0x00002aaab9630000,0x00002aaab9630000,0x00002aaab9b60000)
 PSPermGen       total 21248K, used 7506K [0x00002aaaaee30000, 0x00002aaab02f0000, 0x00002aaab9630000)
  object space 21248K, 35% used [0x00002aaaaee30000,0x00002aaaaf584b20,0x00002aaab02f0000)

Dynamic libraries:
00400000-00401000 r-xp 00000000 08:02 3719672                            /usr/lib/jvm/java-7-icedtea/jre/bin/java
00600000-00601000 rw-p 00000000 08:02 3719672                            /usr/lib/jvm/java-7-icedtea/jre/bin/java
00601000-0092c000 rw-p 00601000 00:00 0                                  [heap]
40000000-40003000 ---p 40000000 00:00 0 
40003000-40101000 rwxp 40003000 00:00 0 
40101000-40102000 ---p 40101000 00:00 0 
40102000-40202000 rwxp 40102000 00:00 0 
40202000-40203000 ---p 40202000 00:00 0 
40203000-40303000 rwxp 40203000 00:00 0 
40303000-40304000 ---p 40303000 00:00 0 
40304000-40404000 rwxp 40304000 00:00 0 
40404000-40407000 ---p 40404000 00:00 0 
40407000-40505000 rwxp 40407000 00:00 0 
40505000-40508000 ---p 40505000 00:00 0 
40508000-40606000 rwxp 40508000 00:00 0 
40606000-40609000 ---p 40606000 00:00 0 
40609000-40707000 rwxp 40609000 00:00 0 
40707000-4070a000 ---p 40707000 00:00 0 
4070a000-40808000 rwxp 4070a000 00:00 0 
40808000-4080b000 ---p 40808000 00:00 0 
4080b000-40909000 rwxp 4080b000 00:00 0 
40909000-4090c000 ---p 40909000 00:00 0 
4090c000-40a0a000 rwxp 4090c000 00:00 0 
40a0a000-40a0b000 ---p 40a0a000 00:00 0 
40a0b000-40b0b000 rwxp 40a0b000 00:00 0 
40b0b000-40b0e000 ---p 40b0b000 00:00 0 
40b0e000-40c0c000 rwxp 40b0e000 00:00 0 
2aaaaaaab000-2aaaaaaad000 r--s 00015000 08:02 3280881                    /usr/share/java/ipblockUI.jar
2aaaaaaad000-2aaaaaab6000 r--s 00065000 08:02 3702957                    /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaaaaab6000-2aaaaaaba000 r--s 00079000 08:02 3702972                    /usr/lib/jvm/java-7-icedtea/jre/lib/jsse.jar
2aaaaaabc000-2aaaaaac4000 r-xp 00000000 08:02 14959195                   /lib/librt-2.6.1.so
2aaaaaac4000-2aaaaacc3000 ---p 00008000 08:02 14959195                   /lib/librt-2.6.1.so
2aaaaacc3000-2aaaaacc5000 rw-p 00007000 08:02 14959195                   /lib/librt-2.6.1.so
2aaaaacc5000-2aaaaacc6000 r--p 2aaaaacc5000 00:00 0 
2aaaaacc6000-2aaaaacc7000 rw-p 2aaaaacc6000 00:00 0 
2aaaaacc7000-2aaaaaccf000 r-xp 00000000 08:02 3719665                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaccf000-2aaaaaece000 ---p 00008000 08:02 3719665                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaece000-2aaaaaed0000 rw-p 00007000 08:02 3719665                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed0000-2aaaaaed8000 rw-s 00000000 08:02 8388677                    /tmp/hsperfdata_root/8425
2aaaaaedf000-2aaaaaef5000 r-xp 00000000 08:02 14959185                   /lib/libnsl-2.6.1.so
2aaaaaef5000-2aaaab0f4000 ---p 00016000 08:02 14959185                   /lib/libnsl-2.6.1.so
2aaaab0f4000-2aaaab0f6000 rw-p 00015000 08:02 14959185                   /lib/libnsl-2.6.1.so
2aaaab0f6000-2aaaab0f8000 rw-p 2aaaab0f6000 00:00 0 
2aaaab0f8000-2aaaab100000 r-xp 00000000 08:02 14959186                   /lib/libnss_compat-2.6.1.so
2aaaab100000-2aaaab2ff000 ---p 00008000 08:02 14959186                   /lib/libnss_compat-2.6.1.so
2aaaab2ff000-2aaaab301000 rw-p 00007000 08:02 14959186                   /lib/libnss_compat-2.6.1.so
2aaaab301000-2aaaab30b000 r-xp 00000000 08:02 14959190                   /lib/libnss_nis-2.6.1.so
2aaaab30b000-2aaaab50a000 ---p 0000a000 08:02 14959190                   /lib/libnss_nis-2.6.1.so
2aaaab50a000-2aaaab50c000 rw-p 00009000 08:02 14959190                   /lib/libnss_nis-2.6.1.so
2aaaab50c000-2aaaab516000 r-xp 00000000 08:02 14959188                   /lib/libnss_files-2.6.1.so
2aaaab516000-2aaaab715000 ---p 0000a000 08:02 14959188                   /lib/libnss_files-2.6.1.so
2aaaab715000-2aaaab717000 rw-p 00009000 08:02 14959188                   /lib/libnss_files-2.6.1.so
2aaaab717000-2aaaab725000 r-xp 00000000 08:02 3719662                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab725000-2aaaab924000 ---p 0000e000 08:02 3719662                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab924000-2aaaab926000 rw-p 0000d000 08:02 3719662                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab926000-2aaaab954000 r-xp 00000000 08:02 3719643                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab954000-2aaaabb53000 ---p 0002e000 08:02 3719643                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb53000-2aaaabb57000 rw-p 0002d000 08:02 3719643                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb57000-2aaaabb67000 r-xp 00000000 08:02 3719663                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb67000-2aaaabd67000 ---p 00010000 08:02 3719663                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd67000-2aaaabd69000 rw-p 00010000 08:02 3719663                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd69000-2aaaabfd9000 rwxp 2aaaabd69000 00:00 0 
2aaaabfd9000-2aaaaed69000 rwxp 2aaaabfd9000 00:00 0 
2aaaaed69000-2aaaaed73000 rwxp 2aaaaed69000 00:00 0 
2aaaaed73000-2aaaaee29000 rwxp 2aaaaed73000 00:00 0 
2aaaaee30000-2aaab02f0000 rwxp 2aaaaee30000 00:00 0 
2aaab02f0000-2aaab9630000 rwxp 2aaab02f0000 00:00 0 
2aaab9630000-2aaab9b60000 rwxp 2aaab9630000 00:00 0 
2aaab9b60000-2aaaceb90000 rwxp 2aaab9b60000 00:00 0 
2aaaceb90000-2aaacef90000 rwxp 2aaaceb90000 00:00 0 
2aaacef90000-2aaad9630000 rwxp 2aaacef90000 00:00 0 
2aaad9630000-2aaad963b000 rwxp 2aaad9630000 00:00 0 
2aaad963b000-2aaad9684000 rwxp 2aaad963b000 00:00 0 
2aaad9684000-2aaad9687000 rwxp 2aaad9684000 00:00 0 
2aaad9687000-2aaad972e000 rwxp 2aaad9687000 00:00 0 
2aaad972e000-2aaad9731000 rwxp 2aaad972e000 00:00 0 
2aaad9731000-2aaad9784000 rwxp 2aaad9731000 00:00 0 
2aaad9784000-2aaad9788000 rwxp 2aaad9784000 00:00 0 
2aaad9788000-2aaad9830000 rwxp 2aaad9788000 00:00 0 
2aaad9830000-2aaad983b000 rwxp 2aaad9830000 00:00 0 
2aaad983b000-2aaad9884000 rwxp 2aaad983b000 00:00 0 
2aaad9884000-2aaad99fe000 r--s 035c6000 08:02 3702978                    /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaad99fe000-2aaad9a3d000 r--p 00000000 08:02 3163129                    /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaad9a3d000-2aaad9a44000 r--s 00000000 08:02 3113511                    /usr/lib/gconv/gconv-modules.cache
2aaad9a44000-2aaad9ae2000 r-xp 00000000 08:02 3719632                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaad9ae2000-2aaad9ce1000 ---p 0009e000 08:02 3719632                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaad9ce1000-2aaad9ced000 rw-p 0009d000 08:02 3719632                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaad9ced000-2aaad9d11000 rw-p 2aaad9ced000 00:00 0 
2aaad9d11000-2aaad9d59000 r-xp 00000000 08:02 3719670                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaad9d59000-2aaad9f59000 ---p 00048000 08:02 3719670                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaad9f59000-2aaad9f5c000 rw-p 00048000 08:02 3719670                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaad9f5c000-2aaad9f5e000 rw-p 2aaad9f5c000 00:00 0 
2aaad9f5e000-2aaad9f65000 r--s 00000000 08:02 5571132                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaad9f65000-2aaad9f6a000 r--s 00000000 08:02 5571237                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaad9f6d000-2aaad9f6f000 r-xp 00000000 08:02 3097917                    /usr/lib/libXinerama.so.1.0.0
2aaad9f6f000-2aaada16e000 ---p 00002000 08:02 3097917                    /usr/lib/libXinerama.so.1.0.0
2aaada16e000-2aaada16f000 rw-p 00001000 08:02 3097917                    /usr/lib/libXinerama.so.1.0.0
2aaada16f000-2aaada180000 r-xp 00000000 08:02 3097907                    /usr/lib/libXext.so.6.4.0
2aaada180000-2aaada37f000 ---p 00011000 08:02 3097907                    /usr/lib/libXext.so.6.4.0
2aaada37f000-2aaada380000 rw-p 00010000 08:02 3097907                    /usr/lib/libXext.so.6.4.0
2aaada380000-2aaada48a000 r-xp 00000000 08:02 3097886                    /usr/lib/libX11.so.6.2.0
2aaada48a000-2aaada68a000 ---p 0010a000 08:02 3097886                    /usr/lib/libX11.so.6.2.0
2aaada68a000-2aaada691000 rw-p 0010a000 08:02 3097886                    /usr/lib/libX11.so.6.2.0
2aaada691000-2aaada696000 r-xp 00000000 08:02 3097935                    /usr/lib/libXtst.so.6.1.0
2aaada696000-2aaada896000 ---p 00005000 08:02 3097935                    /usr/lib/libXtst.so.6.1.0
2aaada896000-2aaada897000 rw-p 00005000 08:02 3097935                    /usr/lib/libXtst.so.6.1.0
2aaada897000-2aaada89f000 r-xp 00000000 08:02 3097915                    /usr/lib/libXi.so.6.0.0
2aaada89f000-2aaadaa9f000 ---p 00008000 08:02 3097915                    /usr/lib/libXi.so.6.0.0
2aaadaa9f000-2aaadaaa0000 rw-p 00008000 08:02 3097915                    /usr/lib/libXi.so.6.0.0
2aaadaaa0000-2aaadaaa2000 r-xp 00000000 08:02 3097892                    /usr/lib/libXau.so.6.0.0
2aaadaaa2000-2aaadaca1000 ---p 00002000 08:02 3097892                    /usr/lib/libXau.so.6.0.0
2aaadaca1000-2aaadaca2000 rw-p 00001000 08:02 3097892                    /usr/lib/libXau.so.6.0.0
2aaadaca2000-2aaadaca7000 r-xp 00000000 08:02 3097903                    /usr/lib/libXdmcp.so.6.0.0
2aaadaca7000-2aaadaea6000 ---p 00005000 08:02 3097903                    /usr/lib/libXdmcp.so.6.0.0
2aaadaea6000-2aaadaea7000 rw-p 00004000 08:02 3097903                    /usr/lib/libXdmcp.so.6.0.0
2aaadaea7000-2aaadaeed000 r-xp 00000000 08:02 3719635                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaadaeed000-2aaadb0ec000 ---p 00046000 08:02 3719635                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaadb0ec000-2aaadb0f0000 rw-p 00045000 08:02 3719635                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaadb0f0000-2aaadb100000 rw-p 2aaadb0f0000 00:00 0 
2aaadb100000-2aaadb106000 r--s 00000000 08:02 5571264                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaadb106000-2aaadb10b000 r--s 00000000 08:02 5571266                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaadb10b000-2aaadb10c000 r--s 00000000 08:02 5571297                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaadb10f000-2aaadb189000 r-xp 00000000 08:02 3098108                    /usr/lib/libfreetype.so.6.3.16
2aaadb189000-2aaadb389000 ---p 0007a000 08:02 3098108                    /usr/lib/libfreetype.so.6.3.16
2aaadb389000-2aaadb38e000 rw-p 0007a000 08:02 3098108                    /usr/lib/libfreetype.so.6.3.16
2aaadb38e000-2aaadb39b000 r-xp 00000000 08:02 14958658                   /lib/libgcc_s.so.1
2aaadb39b000-2aaadb59b000 ---p 0000d000 08:02 14958658                   /lib/libgcc_s.so.1
2aaadb59b000-2aaadb59c000 rw-p 0000d000 08:02 14958658                   /lib/libgcc_s.so.1
2aaadb59c000-2aaadb5b2000 r-xp 00000000 08:02 3098668                    /usr/lib/libz.so.1.2.3.3
2aaadb5b2000-2aaadb7b2000 ---p 00016000 08:02 3098668                    /usr/lib/libz.so.1.2.3.3
2aaadb7b2000-2aaadb7b3000 rw-p 00016000 08:02 3098668                    /usr/lib/libz.so.1.2.3.3
2aaadb7b3000-2aaadb7ba000 r--s 00000000 08:02 5571132                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaadb7ba000-2aaadb7bf000 r--s 00000000 08:02 5571237                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaadb7bf000-2aaadb7c5000 r--s 000f6000 08:02 3702977                    /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaadb7c5000-2aaadb7f4000 r-xp 00000000 08:02 3719652                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaadb7f4000-2aaadb9f3000 ---p 0002f000 08:02 3719652                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaadb9f3000-2aaadb9f5000 rw-p 0002e000 08:02 3719652                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaadb9f5000-2aaadb9f7000 rw-p 2aaadb9f5000 00:00 0 
2aaadb9f7000-2aaadb9fd000 r--s 00000000 08:02 5571264                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaadb9fd000-2aaadba02000 r--s 00000000 08:02 5571266                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaadba02000-2aaadba03000 r--s 00000000 08:02 5571297                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaadba03000-2aaadba0b000 r--s 00000000 08:02 5571298                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaadba0b000-2aaadba11000 r--s 00000000 08:02 5571302                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaadba11000-2aaadba12000 r--s 00000000 08:02 5571306                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaadba12000-2aaadba13000 r--s 00000000 08:02 5571309                    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaadba13000-2aaadba14000 r--s 00000000 08:02 5571310                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaadba14000-2aaadba17000 r--s 00000000 08:02 5571311                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaadba17000-2aaadba1a000 r--s 00000000 08:02 5571312                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaadba1a000-2aaadba20000 r--s 00000000 08:02 5571313                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaadba20000-2aaadba27000 r--s 00000000 08:02 5571314                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaadba27000-2aaadba28000 r--s 00000000 08:02 5571315                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaadba28000-2aaadba2a000 r--s 00000000 08:02 5571316                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaadba2a000-2aaadba2b000 r--s 00000000 08:02 5571317                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaadba2b000-2aaadba2d000 r--s 00000000 08:02 5571318                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaadba2d000-2aaadba36000 r--s 00000000 08:02 5571319                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaadba36000-2aaadba3a000 r--s 00000000 08:02 5571320                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaadba3a000-2aaadba3d000 r--s 00000000 08:02 5571321                    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaadba3d000-2aaadba3e000 r--s 00000000 08:02 5571322                    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaadba3e000-2aaadba3f000 r--s 00000000 08:02 5571323                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaadba3f000-2aaadba40000 r--s 00000000 08:02 5571324                    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaadba40000-2aaadba42000 r--s 00000000 08:02 5570973                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaadba42000-2aaadba46000 r--s 00000000 08:02 5571076                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaadba46000-2aaadba4d000 r--s 00000000 08:02 5571130                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaadba4d000-2aaadba50000 r--s 00000000 08:02 5571139                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaadba50000-2aaadba6f000 r--s 00000000 08:02 5571141                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaadba6f000-2aaadba70000 r--s 00000000 08:02 5571149                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaadba70000-2aaadba78000 r--s 00000000 08:02 5571150                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaadba78000-2aaadba83000 r--s 00000000 08:02 5571151                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaadba83000-2aaadba86000 r--s 00000000 08:02 5571156                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaadba86000-2aaadba89000 r--s 00000000 08:02 5571163                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaadba89000-2aaadba8b000 r--s 00000000 08:02 5571164                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaadba8b000-2aaadba8f000 r--s 00000000 08:02 5571169                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaadba8f000-2aaadba90000 r--s 00000000 08:02 5571184                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaadba90000-2aaadba91000 r--s 00000000 08:02 5571193                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaadba91000-2aaadba96000 r--s 00000000 08:02 5571217                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaadba96000-2aaadba99000 r--s 00000000 08:02 5571224                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaadba99000-2aaadbaa1000 r--s 00000000 08:02 5570645                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaadbc0b000-2aaadbc13000 r--s 00000000 08:02 5571298                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaadbc13000-2aaadbc19000 r--s 00000000 08:02 5571302                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaadbc19000-2aaadbc1a000 r--s 00000000 08:02 5571306                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaadbc1a000-2aaadbc1b000 r--s 00000000 08:02 5571309                    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaadbc1b000-2aaadbc1c000 r--s 00000000 08:02 5571310                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaadbc1c000-2aaadbc1f000 r--s 00000000 08:02 5571311                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaadbc1f000-2aaadbc22000 r--s 00000000 08:02 5571312                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaadbc22000-2aaadbc28000 r--s 00000000 08:02 5571313                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaadbc28000-2aaadbc2f000 r--s 00000000 08:02 5571314                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaadbc2f000-2aaadbc30000 r--s 00000000 08:02 5571315                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaadbc30000-2aaadbc32000 r--s 00000000 08:02 5571316                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaadbc32000-2aaadbc33000 r--s 00000000 08:02 5571317                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaadbc33000-2aaadbc35000 r--s 00000000 08:02 5571318                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaadbc35000-2aaadbc3e000 r--s 00000000 08:02 5571319                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaadbc3e000-2aaadbc42000 r--s 00000000 08:02 5571320                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaadbc42000-2aaadbc45000 r--s 00000000 08:02 5571321                    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaadbc45000-2aaadbc46000 r--s 00000000 08:02 5571322                    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaadbc46000-2aaadbc47000 r--s 00000000 08:02 5571323                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaadbc47000-2aaadbc48000 r--s 00000000 08:02 5571324                    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaadbc48000-2aaadbc4a000 r--s 00000000 08:02 5570973                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaadbc4a000-2aaadbc4e000 r--s 00000000 08:02 5571076                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaadbc4e000-2aaadbc55000 r--s 00000000 08:02 5571130                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaadbc55000-2aaadbc58000 r--s 00000000 08:02 5571139                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaadbc58000-2aaadbc77000 r--s 00000000 08:02 5571141                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaadbc77000-2aaadbc78000 r--s 00000000 08:02 5571149                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaadbc78000-2aaadbc80000 r--s 00000000 08:02 5571150                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaadbc80000-2aaadbc8b000 r--s 00000000 08:02 5571151                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaadbc8b000-2aaadbc8e000 r--s 00000000 08:02 5571156                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaadbc8e000-2aaadbc91000 r--s 00000000 08:02 5571163                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaadbc91000-2aaadbc93000 r--s 00000000 08:02 5571164                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaadbc93000-2aaadbc97000 r--s 00000000 08:02 5571169                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaadbc97000-2aaadbc98000 r--s 00000000 08:02 5571184                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaadbc98000-2aaadbc99000 r--s 00000000 08:02 5571193                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaadbc99000-2aaadbc9e000 r--s 00000000 08:02 5571217                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaadbc9e000-2aaadbca1000 r--s 00000000 08:02 5571224                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaadbca1000-2aaadbca9000 r--s 00000000 08:02 5570645                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaadc000000-2aaadc56b000 rw-p 2aaadc000000 00:00 0 
2aaadc56b000-2aaae0000000 ---p 2aaadc56b000 00:00 0 
2b5874766000-2b5874783000 r-xp 00000000 08:02 14958659                   /lib/ld-2.6.1.so
2b5874783000-2b5874786000 rw-p 2b5874783000 00:00 0 
2b5874982000-2b5874984000 rw-p 0001c000 08:02 14958659                   /lib/ld-2.6.1.so
2b5874984000-2b587499a000 r-xp 00000000 08:02 14959193                   /lib/libpthread-2.6.1.so
2b587499a000-2b5874b99000 ---p 00016000 08:02 14959193                   /lib/libpthread-2.6.1.so
2b5874b99000-2b5874b9b000 rw-p 00015000 08:02 14959193                   /lib/libpthread-2.6.1.so
2b5874b9b000-2b5874b9f000 rw-p 2b5874b9b000 00:00 0 
2b5874b9f000-2b5874baf000 r-xp 00000000 08:02 3719630                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b5874baf000-2b5874daf000 ---p 00010000 08:02 3719630                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b5874daf000-2b5874db1000 rw-p 00010000 08:02 3719630                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b5874db1000-2b5874db3000 r-xp 00000000 08:02 14959182                   /lib/libdl-2.6.1.so
2b5874db3000-2b5874fb3000 ---p 00002000 08:02 14959182                   /lib/libdl-2.6.1.so
2b5874fb3000-2b5874fb5000 rw-p 00002000 08:02 14959182                   /lib/libdl-2.6.1.so
2b5874fb5000-2b5874fb6000 rw-p 2b5874fb5000 00:00 0 
2b5874fb6000-2b5875108000 r-xp 00000000 08:02 14959106                   /lib/libc-2.6.1.so
2b5875108000-2b5875307000 ---p 00152000 08:02 14959106                   /lib/libc-2.6.1.so
2b5875307000-2b587530a000 r--p 00151000 08:02 14959106                   /lib/libc-2.6.1.so
2b587530a000-2b587530c000 rw-p 00154000 08:02 14959106                   /lib/libc-2.6.1.so
2b587530c000-2b5875312000 rw-p 2b587530c000 00:00 0 
2b5875312000-2b5875a5a000 r-xp 00000000 08:02 3719667                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b5875a5a000-2b5875c5a000 ---p 00748000 08:02 3719667                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b5875c5a000-2b5875cd4000 rw-p 00748000 08:02 3719667                    /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b5875cd4000-2b5875d0e000 rw-p 2b5875cd4000 00:00 0 
2b5875d1d000-2b5875d9d000 r-xp 00000000 08:02 14959183                   /lib/libm-2.6.1.so
2b5875d9d000-2b5875f9c000 ---p 00080000 08:02 14959183                   /lib/libm-2.6.1.so
2b5875f9c000-2b5875f9e000 rw-p 0007f000 08:02 14959183                   /lib/libm-2.6.1.so
7fff3632e000-7fff36341000 rwxp 7fff3632e000 00:00 0                      [stack]
7fff36341000-7fff36344000 rw-p 7fff36341000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Xmx512M 
java_command: /usr/share/java/ipblockUI.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/sbin:/usr/sbin:/bin:/usr/bin
USERNAME=difranco
LD_LIBRARY_PATH=/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server:/usr/lib/jvm/java-7-icedtea/jre/lib/amd64:/usr/lib/jvm/java-7-icedtea/jre/../lib/amd64
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4ccc50], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 38912, NOFILE 1024, AS infinity
load average:0.24 0.51 1.25

CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 11, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 4054804k(2426744k free), swap 7815580k(7815580k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Fri Dec 21 19:36:05 2007
elapsed time: 0 seconds



```

---

### Post by uljanow on 2007-12-21
This is a bug in the IcedTea VM. I've tested IPblock with **sun-java5-jre** and **sun-java6-jre** which are recommended and work. Other VMs might not be 100% java compatible.
With "sudo update-alternatives --config java" you can change the current VM.

---

### Post by Difranco1911 on 2007-12-22
Thank you very much.  changing to java 6 fixed it for me.

---

### Post by uljanow on 2007-12-22
```
* release (0.17)
* fixed bug 1852759 (thanks to ekimregnirps)
* improved cleanup of iptables rules
* resolved conflict between using GUI and CLI
* added cron job to auto-update lists
* added AUTOSTART option and init script
* minor GUI layout changes
```
.

---

### Post by linuxlurker on 2007-12-24
Hi, cool program.

However, for some reason, the auto-start with reboot doesn't work at all for me.  I think this is a new feature from .16 to .17?

I'm running Gutsy and Shorewall.

Shorewall runs @reboot via cron

When I reboot, ipblock -l shows that it's active, but not running via the command line (i.e. it doesn't say "ipblock isn't running" but it doesn't block anything).

To get it up and running, I have to:

ipblock -d
ipblock -s

Anyone else running into this problem, or have a solution?

---

### Post by Rabidmonkey1 on 2007-12-24
Hi all,

I'm running into a problem with Java; not very sure what to do...  Take a look:

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b18c2c27e11, pid=7808, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/bob/hs_err_pid7808.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

``` 

Any ideas?  I would love to get this program working...  Thanks!!

---

### Post by uljanow on 2007-12-24
> **linuxlurker said:**
> However, for some reason, the auto-start with reboot doesn't work at all for me.  I think this is a new feature from .16 to .17?

I'm running Gutsy and Shorewall.

Shorewall runs @reboot via cron

The cron service starts after IPblock, so shorewall is probably removing previously inserted iptables rules.
I haven't considered cron, only other firewall applications to make sure that IPblock runs as the last application that changes iptables rules.

Does it work if you change the start order ?
```
sudo update-rc.d -f ipblock remove
sudo update-rc.d ipblock start 99 2 3 4 5 . stop 00 0 1 6 .
```

---

### Post by uljanow on 2007-12-24
> **Rabidmonkey1 said:**
> Hi all,

I'm running into a problem with Java; not very sure what to do...  Take a look:

...
Any ideas?  I would love to get this program working...  Thanks!!

[http://ubuntuforums.org/showpost.php?p=3995174&postcount=129](http://ubuntuforums.org/showpost.php?p=3995174&postcount=129)

---

### Post by Jeff_From_VA on 2007-12-26
Thanks for this!

I used to use moblock, but have had nothing but problems with it for the last several releases.  Don't get me wrong I am not bashing moblock, I am sure the issues were mistakes on my end, as moblock is not quite as easy to configure as this is.  

This was very simple to install, and set up. I also love how everything is in one simple to use GUI, including the logs.  

I had one question about how it updates.  You had mentioned in this thread it will update via a cron job.  I just installed this on my wife's laptop which is not always on.  I am not too familiar with how cron works  in cases where the PC is off.  Will the cron update happen when she turns on her laptop after missing a previous update because the PC was off when cron was originally scheduled to run?  I want to make sure she stays up to date, and am fearful that if her pc is not on during the time cron runs she will not end up getting updated.

---

### Post by uljanow on 2007-12-26
> **Jeff_From_VA said:**
> I had one question about how it updates.  You had mentioned in this thread it will update via a cron job.  I just installed this on my wife's laptop which is not always on.  I am not too familiar with how cron works  in cases where the PC is off.  Will the cron update happen when she turns on her laptop after missing a previous update because the PC was off when cron was originally scheduled to run?

If you use [anacron]("http://packages.ubuntu.com/gutsy/admin/anacron") the lists will get updated in the specified interval or as closely as possible. Anacron is for systems that don't run 24h a day and is installed by default on Ubuntu desktops.

---

### Post by Comhra on 2007-12-27
I installed IPBlock yesterday.  It's blocking my pop 3 email accounts (gmail via Thunderbird), it's blocking the @Weather Report Applet so that it can't update and it's blocking my dictionary applet.  It's also blocking some radio stations.  Without a whitelist; IPblock is a pain. There doesn't seem to be a way to filter these apps so that they're not caught by IPblock.
Is there someway I can allow these and still use IPblock?

Failing that, how do I remove it.  I can't see it in Synaptic and Terminal can't find it.

---

### Post by Comhra on 2007-12-27
Got it.

 sudo aptitude purge iplist

This did the trick!

---

### Post by uljanow on 2007-12-28
```
* release (0.18)
* made init scripts more distribution specific 
* added ALLOW_LIST option
* changed URL list format
* integrated country lists
```
Finally there is an IP-whitelisting feature. The updated first page describes how to use it.

---

### Post by ssc351 on 2007-12-28
Yo I can't seem to get this thing to run, it starts up, but I can't enable it... it looks like its missing IP tables, but I don't know...here are the ouputs:

 egrep "iplist|ipblock" /var/log/syslog
Dec 28 17:43:23 dell640m ipblock[9084]: error: IPblock needs to be run as root
Dec 28 18:09:39 dell640m ipblock[9727]: error: failed to start, cleaning up
Dec 28 18:10:50 dell640m ipblock[9753]: error: failed to start, cleaning up
Dec 28 18:11:37 dell640m ipblock[9817]: error: IPblock needs to be run as root
Dec 28 18:12:05 dell640m ipblock[9823]: error: failed to start, cleaning up
Dec 28 18:15:00 dell640m ipblock[9849]: error: failed to start, cleaning up
Dec 28 18:17:10 dell640m ipblock[9909]: error: failed to start, cleaning up
Dec 28 18:17:25 dell640m ipblock[9958]: error: failed to start, cleaning up
Dec 28 18:17:47 dell640m ipblock[9978]: error: update of ads-trackers-and-bad-pr0n.gz failed
Dec 28 18:19:02 dell640m ipblock[10033]: error: update of ads-trackers-and-bad-pr0n.gz failed
Dec 28 18:19:55 dell640m ipblock[10076]: error: failed to start, cleaning up
Dec 28 18:20:26 dell640m ipblock[10097]: error: failed to start, cleaning up
Dec 28 18:20:37 dell640m ipblock[10118]: error: failed to start, cleaning up
Dec 28 18:21:32 dell640m ipblock[10174]: error: update of ads-trackers-and-bad-pr0n.gz failed
Dec 28 18:23:40 dell640m ipblock[10287]: error: failed to start, cleaning up
Dec 28 18:25:35 dell640m ipblock[10333]: error: IPblock is not running
Dec 28 18:27:33 dell640m ipblock[10373]: error: failed to start, cleaning up
Dec 28 18:30:34 dell640m ipblock[10397]: error: failed to start, cleaning up
Dec 28 18:32:09 dell640m ipblock[8394]: error: failed to start, cleaning up
Dec 28 18:33:53 dell640m ipblock[8839]: error: update of ads-trackers-and-bad-pr0n.gz failed


DEBUG=1 ipblock -sl
+ set -e
+ set -u
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin
+ [ -f /etc/ipblock.conf ]
+ . /etc/ipblock.conf
+ AUTOSTART=Yes
+ BLOCK_LIST=ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz level1.gz 
+ ALLOW_LIST=allow.p2p
+ IPTABLES_CHAIN=INPUT OUTPUT 
+ IGN_TCP_OUTPUT=http ftp https 900137 
+ IGN_UDP_OUTPUT=
+ IGN_TCP_INPUT=
+ IGN_UDP_INPUT=
+ IGN_TCP_FORWARD=
+ IGN_UDP_FORWARD=
+ IPLIST_LISTDIR=/var/cache/iplist
+ UPDATE_STAMP=/var/cache/iplist/.update-stamp
+ URL_FILE=/usr/share/doc/iplist/README.lists
+ LOG_FILE=/tmp/ipblock.log
+ LOG_LEVEL=match
+ IPTABLES_LOG=No
+ VERBOSE=No
+ UPDATE_INTERVAL=2
+ http_proxy=127.0.0.1:8118
+ VERSION=0.18
+ QUEUE=0xff
+ POLICY=REPEAT
+ POLICY_MARK=0xfffe
+ BLOCK_TARGET=REPEAT
+ BLOCK_TARGET_MARK=0xffff
+ NICE=-5
+ NEW=-m state --state NEW
+ export IPLIST_LISTDIR
+ export http_proxy
+ id -u
+ [ 1000 != 0 ]
+ logger -s -t ipblock[9490] error: IPblock needs to be run as root
ipblock[9490]: error: IPblock needs to be run as root
+ exit 1


sudo ipblock -sl
/usr/sbin/ipblock: 348: iptables: not found
/usr/sbin/ipblock: 348: iptables: not found
ipblock[9493]: error: failed to start, cleaning up
/usr/sbin/ipblock: 1: iptables: not found

---

### Post by uljanow on 2007-12-28
The iptables command wasn't found. Which distro are you using and what does the following show ?
```
whereis iptables
ls -l /bin/sh
```

BTW, port number 900137 is misspelled.

---

### Post by jre on 2007-12-28
did you run it as root?

---

### Post by ssc351 on 2007-12-29
whereis iptables
iptables: /usr/local/sbin/iptables /usr/local/lib/iptables


ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-04-24 15:34 /bin/sh -> dash

Also, I ran it as root from terminal.  I also ran it from the gui and had to put in my password when it opened up and immediately opened up with errors.

---

### Post by ssc351 on 2007-12-29
Sorry, also I am using ubuntu gusty

---

### Post by uljanow on 2007-12-29
Normally iptables is in **/sbin/**. So it's required to change **/usr/sbin/ipblock** (as root) and replace the line (26) starting with PATH with:
```
PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/local/sbin:/usr/local/bin
```
There were also "error: update of ads-trackers-and-bad-pr0n.gz failed" messages, if that file doesn't exist but is listed in BLOCK_LIST, it will refuse to start. Looks like you're using 127.0.0.1:8118 as proxy. On my machine Privoxy which listens on 8118 blocked the download of ads-trackers-and-bad-pr0n.gz because it tends to block ads and banners etc.. This might be the case here, too.

---

### Post by ssc351 on 2007-12-29
> **uljanow said:**
> Normally iptables is in **/sbin/**. So it's required to change **/usr/sbin/ipblock** (as root) and replace the line (26) starting with PATH with:
```
PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/local/sbin:/usr/local/bin
```
There were also "error: update of ads-trackers-and-bad-pr0n.gz failed" messages, if that file doesn't exist but is listed in BLOCK_LIST, it will refuse to start. Looks like you're using 127.0.0.1:8118 as proxy. On my machine Privoxy which listens on 8118 blocked the download of ads-trackers-and-bad-pr0n.gz because it tends to block ads and banners etc.. This might be the case here, too.


That fixed it...Thanks!

How come the path was different on my machine?

---

### Post by gmaniac on 2008-01-01
Very very very useful program. 
One note for the howto about the whitelist. ipblock service must be stoped because 
if it's running it will overide the changes in conf.

---

### Post by gmaniac on 2008-01-01
Another note. I think that by default it should ignore traffic at least in http port
because (with the current default lists) i couldn't even see some youtube videos!

---

### Post by uljanow on 2008-01-01
> **gmaniac said:**
> Another note. I think that by default it should ignore traffic at least in http port
because (with the current default lists) i couldn't even see some youtube videos!

The problem is that port 80 can be used by any application (e.g. bittorrent client).

---

### Post by gmaniac on 2008-01-03
> **uljanow said:**
> The problem is that port 80 can be used by any application (e.g. bittorrent client).

I didn't think of that. I thought this was only for browsing the web. But the problem is (since this is an InstallnPlay kind of an application) that users who don't know about much of this stuff (i.e they just installed ubuntu and installed 2-3 apps) will not even know/notice why they couldn't browse a perfectly legit looking site. If my weather applet didn't connect for me at first and if I hadn't browsed that day some videos i could have forgotten i installed this app (It's that great :)) so as to look what's going on.

Because crippling the web is not a solution it shouldn't be a default option. If someone wants extra protection he should know what trouble lies ahead and enable it on his own. 
If someone wants that extra protection then **in** traffic could be droped. Maybe the program could drop the packets based on the ports that listen for p2p in the client. So a range to protect could be implemented in some way. But I think this is too much.

---

### Post by isaacj87 on 2008-01-04
Hi,

I've been reading up on MoBlock and IPBlock...I finally decided to install it and give it a try. :)

Quick question...On page 5 of this thread towards the bottom, a user suggests using alltray and running this command:

```
sudo alltray "ipblock -g"
``` 

Is this still valid after all the version updates since then? Or is there a simpler way to have the program start in the tray?

Thanks!

---

### Post by isaacj87 on 2008-01-04
Oh. BTW...

It's a bit off-topic, but I would be nice if this program shipped with a default icon. Maybe some talented user could come up with something? I'll try to make something...but don't expect it to be any good!

---

### Post by uljanow on 2008-01-04
> **isaacj87 said:**
> Hi,

I've been reading up on MoBlock and IPBlock...I finally decided to install it and give it a try. :)

Quick question...On page 5 of this thread towards the bottom, a user suggests using alltray and running this command:

```
sudo alltray "ipblock -g"
``` 

Is this still valid after all the version updates since then? Or is there a simpler way to have the program start in the tray?

Thanks!

Using alltray works. Currently there is no other way to do this.

---

### Post by uljanow on 2008-01-04
> **isaacj87 said:**
> Oh. BTW...

It's a bit off-topic, but I would be nice if this program shipped with a default icon. Maybe some talented user could come up with something? I'll try to make something...but don't expect it to be any good!

There are no plans for a logo/icon. But I look forward to a contributions.

---

### Post by isaacj87 on 2008-01-05
One last noobie question...

I noticed on the front page that ipblock doesn't conflict with FireHOL and shorewall...is it the same for Firestarter as well?

thanks!

---

### Post by uljanow on 2008-01-05
> **isaacj87 said:**
> I noticed on the front page that ipblock doesn't conflict with FireHOL and shorewall...is it the same for Firestarter as well?
Yes. The only requirement is that IPblock needs to be run after the application/script that changes iptables rules.
Everything that starts at boot time does not conflict with IPblock.

---

### Post by isaacj87 on 2008-01-05
> **uljanow said:**
> Yes. The only requirement is that IPblock needs to be run after the application/script that changes iptables rules.
Everything that starts at boot time does not conflict with IPblock.

Hmm...I just followed these instructions to get Firestarter to properly load upon boot up....

[http://ubuntuforums.org/showthread.php?t=542756&highlight=howto+firestarter]("http://ubuntuforums.org/showthread.php?t=542756&highlight=howto+firestarter")

Do I need to make a special startup script now? Or everything is normal...

---

### Post by uljanow on 2008-01-05
> **isaacj87 said:**
> Do I need to make a special startup script now? Or everything is normal...

No, there's no need to change anything. It should work fine.

---

### Post by Munkster on 2008-01-12
> **uljanow said:**
> To start ipblock at boot just add this line to **/etc/rc.local** (as root)
```
/usr/sbin/ipblock -s
``` The line should be before "exit 0".

Now you should be able to stop ipblock and start the GUI in both ways.

I've followed these instructions but Ipblock is not starting up at boot. 

My /etc/rc.local file looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/sbin/ipblock -s
exit 0
```

Any ideas?

---

### Post by uljanow on 2008-01-12
The latest version has an AUTOSTART option, which can be set in the GUI. There is no need to edit **/etc/rc.local**.

---

### Post by Munkster on 2008-01-12
OK, I am now running 0.18 and I have set it to autostart. 

However, when I check the status it returns:
```
Queue   Policy (mark)   Ranges  Target (mark)   File
255     REPEAT (65534)  204194  REPEAT (65535)  /var/cache/iplist/level1.gz
                                REPEAT (65535)  /var/cache/iplist/ads-trackers-and-bad-pr0n.gz
                                REPEAT (65535)  /var/cache/iplist/spyware.gz
                                REPEAT (65535)  /var/cache/iplist/bogon.gz

iptables: No chain/target/match by that name

```
I am using Gutsy and I have Firestarter running as well

---

### Post by uljanow on 2008-01-12
Firestarter has removed the iptables rules of IPblock. This is why IPblock needs to be started after other firewalls. 
Starting Firestarter with an init script at boot time should resolve this.

---

### Post by MEGAMANULTIMATE on 2008-01-21
It was working great at first. Now, it just won't start up. This is what happened when I started with 'sudo ipblock -g':

matthew@matthew-laptop:~$ sudo ipblock -g
Exception in thread "main" java.lang.NoClassDefFoundError: org.ipblock.gui.ipblockUI
   at java.lang.Class.initializeClass(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: java.lang.ProcessBuilder not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/ipblockUI.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
 
Any suggestions?

---

### Post by uljanow on 2008-01-21
Changing the the java settings to sun's virtual machine should fix it (gcj is not fully java compatible).
```
sudo update-alternatives --config java
```

---

### Post by Ripfox on 2008-01-21
libnfnetlink0 is installed and it still asks for libnfnetlink1 as a dep.

Sorry if this is a repeat

---

### Post by uljanow on 2008-01-21
> **ripfox said:**
> libnfnetlink0 is installed and it still asks for libnfnetlink1 as a dep.

Only iplist packages for feisty depend on libnfnetlink1, which was renamed to  libnfnetlink0 in gutsy. You could try a gutsy package of iplist, but I haven't tested it with hardy.

---

### Post by MEGAMANULTIMATE on 2008-01-21
Thanks, uljanow. It's working just fine now. I was wondering though, do you have a theory as to why it suddenly switched javas (or something)? If not, don't worry about it.

---

### Post by Ripfox on 2008-01-21
Well, it installs ok here with the Gutsy package but no graphical front end. When I start it from the terminal with sudo ipblock I get this:

> Usage: ipblock [options]

Options:
 -s	start blocking
 -d	stop blocking
 -r	restart IPblock
 -u	update lists
 -c	convert lists to ipl format
 -g	start IPblock GUI
 -l	show status
 -v	show version and exit
 -h	show this help


and from the menu it does nothing.

---

### Post by Ripfox on 2008-01-21
> pilot@DualCoreHeron:~$ sudo ipblock -g
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5303767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb53038b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb535029d]
#3 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb54508ce]
#4 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb542d067]
#5 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb542d318]
#6 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb542d61f]
#7 [0xb5d4decd]
#8 [0xb5d46edd]
#9 [0xb5d46edd]
#10 [0xb5d44249]
#11 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c40d]
#12 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x6310378]
#13 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c2a0]
#14 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x363) [0x6272153]
#15 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d5f96d]
#16 [0xb5d4decd]
#17 [0xb5d46d77]
#18 [0xb5d44249]
#19 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c40d]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)

?

---

### Post by uljanow on 2008-01-21
This is a java bug in hardy.
**workaround** - [http://ubuntuforums.org/showthread.php?t=621864](http://ubuntuforums.org/showthread.php?t=621864)
**bugreport** - [https://bugs.launchpad.net/ubuntu/+bug/181582](https://bugs.launchpad.net/ubuntu/+bug/181582)

---

### Post by pandorazboxx on 2008-01-21
I installed this, but now i cant access anything from the internet at all. (i had to switch over to windows to type this). I clicked ignore HTTP and such, and even when ipblock is disabled i can no longer get on the internet. please help if anyone has had this problem. thanks. and i'm on gutsy and i'm using the latest ipblock GUI.

---

### Post by uljanow on 2008-01-22
> **pandorazboxx said:**
> I installed this, but now i cant access anything from the internet at all. (i had to switch over to windows to type this). I clicked ignore HTTP and such, and even when ipblock is disabled i can no longer get on the internet. please help if anyone has had this problem. thanks. and i'm on gutsy and i'm using the latest ipblock GUI.

Maybe your ISP or DNS-servers are being blocked (**/tmp/ipblock.log**) and need to be whitelisted. Removing some lists might help, too.

---

### Post by uljanow on 2008-01-24
[Security flaw in default configuration (<= 0.18 )]("https://sourceforge.net/forum/forum.php?forum_id=777729")

// EDIT: fixed in iplist-0.19

---

### Post by nitri on 2008-01-27
First of all thank you uljanow for this excellent prog.
I'm running hardy and had the problem  with java 6.
I  installed icedtea then "sudo update-alternatives --config java" and selected icedtea to provide java.
After this the gui is working like a charm.
Thank you again for the prog.

---

### Post by kellogs908 on 2008-02-04
i have installed this program i think three times now without problems but i think i must have done soemthign wrong this time
wehn i try to open it, i get a dependancy error lbnetfilter-queue1

---

### Post by uljanow on 2008-02-04
Which distro are you using and is the universe repository enabled ?

---

### Post by jollytim on 2008-02-06
I am trying to install on Hardy, using 'Gutsy" deb file for iplist.

I was having a problem getting the gui to work (seemed to work at command line but not in gui).

used this code to do the current workaround for java to make gui work.

sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so

Seems to work now.

---

### Post by bone2006 on 2008-02-14
I love ipblock, but when I reboot it sometimes seems that it's not enabled.  How do you enable it when you restart so that I don't have to open up the gui or use the command line.
I just want it blocked all the time even if I don't enable it manually?

---

### Post by uljanow on 2008-02-15
> **bone2006 said:**
> I love ipblock, but when I reboot it sometimes seems that it's not enabled.
Autostart is set but it only starts sometimes ? If that's the case you could try to change line 133 of **/usr/sbin/ipblock** (version 0.19) by replacing "sleep 1" with "sleep 2".

---

### Post by kpkeerthi on 2008-02-20
I don't have iptables installed. Will ipblock work?

---

### Post by uljanow on 2008-02-20
> **kpkeerthi said:**
> I don't have iptables installed. Will ipblock work?

No. It also requires kernel support for nfqueue, mark, state, tcp, iprange, reject (, log) matches/targets.

---

### Post by isaacj87 on 2008-03-04
Hi, 

I've been adding list and I'm currently blocking **315298** IP Ranges. I have these lists installed:

The default:
-level1.gz 
-ads-trackers-and-bad-pr0n.gz 
-spyware.gz 
-edu.gz
-bogon.gz

and the extra lists I added:
-Dshield 
-templist
-level2
-level3

The problem is, whenever I try to add a country (or more lists too), for example the usa.p2p list, the number of ranges being blocked goes down to **186000**(!!). Why does this happen? Is this a bug?

Update: I just tried to install the rangetest list from the B.I.S.S forums and the number of ranges went down to **280000** :(


Thanks!

---

### Post by uljanow on 2008-03-04
The number of ranges doesn't specify the actual amount of IP-addresses because ranges have variable length. Useless ranges are also merged (e.g. small ranges that are covered by a larger range are removed).

---

### Post by RizingDamp on 2008-03-10
Hi,

Well I have been using the 019 version of the IP blocker without problem so far.  However I updated my lists today and noticed that the text file within the level1.gz list has risen from some 10.3mb to over 600mb in size and upon restarting the blocked ip ranges has considerably reduced.  Also I always could open the level1 text file but now when I try I get an error(see below)

gzip: /tmp/fr-ZaUglf/level1.gz: unexpected end of file

Hope you can make something of this.  I tried removing the IP List package but get an error with regard /var/cache/iplist not empty.....


Help.

---

### Post by uljanow on 2008-03-10
Today the update went wrong, but it's fixed now. Just try another update.

---

### Post by RizingDamp on 2008-03-10
Ok all sorted.....thanks

---

### Post by RizingDamp on 2008-03-11
I understand that using the command **sudo aptitude purge iplist** will remove the program and all of its configuration files but will it also remove the directory** iplist** that is created in /var/cache.  When I was having problems last night trying to update the level1.gz list I tried to remove  IP Block using Synaptic and by sudo dpkg -P iplist but I noticed that the iplist directory remained having removed the program and configuration files.  


I appreciate your help on the above.


Thanks.

---

### Post by uljanow on 2008-03-11
**/var/cache/iplist** has to be empty in order to be removed by the package manager.

---

### Post by RizingDamp on 2008-03-11
Thanks Uljanow for your swift responses to my questions.

I forgot to pre-warn you in my first post that I have only just migrated to Ubuntu so am finding most things a struggle at the moment.  Am I correct in thinking that it was upon installing IPBlock that created the directory iplist?  So to remove this directory at such a time that I might not need to use IPBlock, then I have to remove the contents firstly before I use the command sudo aptitude purge iplist?

Once again thank you for your patience.

---

### Post by mandrill on 2008-03-17
> **uljanow said:**
> ```
* release (0.18)
* made init scripts more distribution specific 
* added ALLOW_LIST option
* changed URL list format
* integrated country lists
```
Finally there is an IP-whitelisting feature. The updated first page describes how to use it.

And this is what I get. Immediate and total crash due to java conflict.

jim@monkey:~$ sudo ipblock -g
exec: 348: java: not found

I have jre6 installed and every other program works - this one did too
until I re-installed gutsy a couple day ago.....

---

### Post by uljanow on 2008-03-17
What does "whereis java" show and is a default java VM set ("sudo update-alternatives --config java") ?

---

### Post by mandrill on 2008-03-17
jim@monkey:~$ whereis java
java: /usr/bin/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz

jim@monkey:~$ sudo update-alternatives --config java
[sudo] password for jim:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:


I started following the file path as per "whereis java" & got this far - usr/bin/java, where I got this - THIS LINK IS BROKEN, "This link can't be used, because its target "/usr/lib/jvm/java-1.5.0-sun/jre/bin/java" doesn't exist."

Why, I wonder, is it looking for java-1.5.0?

This is also broken- looking for version 5 of java......... /java.1.gz

---

### Post by mandrill on 2008-03-17
I think I solved this. I installed "galternatives" in terminal, then searched for and deleted every directory with a reference to jre, then I deleted .java in my home folder, then re-installed jre6 from synaptic, and now iPBlock seems to work. Lets see if it continues to work.....

---

### Post by Nameless_one on 2008-04-08
How can I add my own iptables entries, while using ipblock? Will they be restored after a restart? 

I want to allow traffic on port 22, so that I can login remotely to my PC via ssh.

EDIT: I also have my http traffic blocked :( I have told IPBlock to ignore http and https, and I have also whitelisted my router's IP (and my own in the local network), but a couple of minutes after IPBlock starts, it begins blocking my browsing, and in the log are shown blocks containing traffic from my router to my local IP.

---

### Post by mandrill on 2008-04-08
> **Nameless_one said:**
> How can I add my own iptables entries, while using ipblock? Will they be restored after a restart? 

I want to allow traffic on port 22, so that I can login remotely to my PC via ssh.

EDIT: I also have my http traffic blocked :( I have told IPBlock to ignore http and https, and I have also whitelisted my router's IP (and my own in the local network), but a couple of minutes after IPBlock starts, it begins blocking my browsing, and in the log are shown blocks containing traffic from my router to my local IP.

You're off topic, but I would suggest looking into moblocker (peer guardian's "replacement". And if you've turned off HTTP - well, you've turned off http. Good Luck!

---

### Post by Nameless_one on 2008-04-08
I am using moblock already, and trying to replace it with IPBlock.

The problem was that even though I had made a .p2p file and added it to iplist.conf, something I did reverted iplist.conf to its previous state (I think I restarted IPBlock). That problem's gone. 

Adding an exception to iptables is a bit off topic, but I am more concerned about how will IPBlock behave after I do that, and wether this will interfere with its proper function. If this is still off topic, then OK.

---

### Post by uljanow on 2008-04-08
The GUI needs to be closed before making changes to ipblock.conf. 
The only limitation with other iptables rules is that the rules have to be inserted before IPblock starts.

---

### Post by Nameless_one on 2008-04-09
Thank you, that was the answer I was looking for.

EDIT: actually, there is one more question: when is IPBlock started and its iptables rules initialised? How can I automatically add iptables rules before ipblock starts, on system startup? I guess I could add them to /etc/init.d/ipblock, but that sounds kinda hackish :-\

---

### Post by uljanow on 2008-04-09
If autostart is set IPblock inserts iptables rules at the last runlevel  (S99). Otherwise when you enable it. I would recommend using a custom init script or front-end like firestarter or fireHOL. Both ways shouldn't conflict with IPblock.

---

### Post by grossaffe on 2008-04-30
> **uljanow said:**
> I'll set up a mirror.

did anything ever come of this, because i haven't been able to update ipblock, and since i just downloaded it, that means i can't use it.

---

### Post by uljanow on 2008-04-30
Sourceforge.net seems to be down. So the update links don't work. You could manually download the lists [1] and copy them to /var/cache/iplist.

[1] [http://iplist.sourceforge.net/mirror/](http://iplist.sourceforge.net/mirror/)

---

### Post by grossaffe on 2008-04-30
> **uljanow said:**
> Sourceforge.net seems to be down. So the update links don't work. You could manually download the lists [1] and copy them to /var/cache/iplist.

[1] [http://iplist.sourceforge.net/mirror/](http://iplist.sourceforge.net/mirror/)

ok, now when downloading from there, do i want to right-click and save link as?  when i do that i'm saving a .gz.php.  is that what i want or do i just want the .gz?  if so, do i need to do anything to convert it or do i just remove the .php ending?

---

### Post by uljanow on 2008-04-30
Right-clicking and "save link as" should work. The ending .php should be removed. Alternatively:
```
cd /var/cache/iplist
sudo wget http://iplist.sf.net/mirror/level1.gz.php
```

---

### Post by grossaffe on 2008-04-30
thanks a bunch.

---

### Post by lwpack on 2008-05-05
Hello.  Everytime I start the IPblock gui it freezes.  It's working from the command line.  I've tried completely removing it and then reinstalling it and it doesn't help.  Not sure what to do.  This just started yesterday and before that it was fine.  I'm running Hardy.  In case it helps:


lwpack@lwpack-desktop:~$ egrep "iplist|ipblock" /var/log/syslog
May  5 08:42:12 lwpack-desktop iplist[14201]: error: no running iplist instance found 
May  5 08:42:24 lwpack-desktop iplist[14230]: error: no running iplist instance found 
May  5 08:43:10 lwpack-desktop ipblock[14256]: error: IPblock needs to be run as root
May  5 08:50:14 lwpack-desktop iplist[14719]: error: no running iplist instance found 
May  5 08:50:22 lwpack-desktop iplist[14721]: error: can't send job to msq 
May  5 08:50:46 lwpack-desktop iplist[14736]: error: no running iplist instance found 
May  5 09:31:35 lwpack-desktop iplist[6660]: error: can't send job to msq 
May  5 09:34:18 lwpack-desktop ipblock[6684]: error: IPblock needs to be run as root
May  5 10:19:20 lwpack-desktop iplist[7519]: error: can't find kill 
May  5 10:19:35 lwpack-desktop iplist[7529]: error: no running iplist instance found 
May  5 10:23:54 lwpack-desktop iplist[7986]: error: iplist needs to be run as root 
May  5 10:24:11 lwpack-desktop ipblock[7989]: error: IPblock is not running
May  5 10:24:16 lwpack-desktop iplist[7995]: error: no running iplist instance found 
May  5 10:24:33 lwpack-desktop iplist[8012]: error: iplist needs to be run as root 
May  5 10:40:26 lwpack-desktop ipblock[8026]: error: IPblock needs to be run as root
May  5 10:50:42 lwpack-desktop ipblock[8323]: error: failed to start, cleaning up
May  5 10:53:13 lwpack-desktop ipblock[8416]: error: failed to start, cleaning up
May  5 10:54:00 lwpack-desktop ipblock[8494]: error: IPblock is not running
May  5 10:56:13 lwpack-desktop ipblock[8621]: error: failed to start, cleaning up
May  5 10:57:17 lwpack-desktop ipblock[8868]: error: failed to start, cleaning up
May  5 10:57:35 lwpack-desktop ipblock[8939]: error: failed to start, cleaning up
May  5 10:57:53 lwpack-desktop ipblock[8993]: error: failed to start, cleaning up
May  5 10:58:10 lwpack-desktop ipblock[9046]: error: failed to start, cleaning up
May  5 10:58:22 lwpack-desktop ipblock[9099]: error: failed to start, cleaning up
May  5 10:59:33 lwpack-desktop ipblock[9321]: error: failed to start, cleaning up
May  5 11:00:00 lwpack-desktop ipblock[9448]: error: failed to start, cleaning up
May  5 11:00:30 lwpack-desktop ipblock[9578]: error: failed to start, cleaning up
May  5 11:01:39 lwpack-desktop ipblock[9899]: error: failed to start, cleaning up
May  5 11:03:55 lwpack-desktop ipblock[10171]: error: failed to start, cleaning up
lwpack@lwpack-desktop:~$ DEBUG=1 sudo ipblock -sl
Queue	Policy (mark)	Ranges	Target (mark)	File
255	REPEAT (65534)	316093	REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/level1.gz
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/level2.gz
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/dshield.txt
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/bogon.gz
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/edu.gz
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/spyware.gz
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/Microsoft.gz
				REPEAT (65535)	/media/NTFS/Documents/Blocklists/PeerGuardian/ads-trackers-and-bad-pr0n.gz

Chain BLOCK_MATCH (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Last Updated Mon May  5 08:47:38 PDT 2008
Last log messages (/tmp/ipblock.log):
20:09:58 INPUT: Match=SafeNetinc Hits=16 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=17 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=18 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=19 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=20 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=21 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=22 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=23 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:09:58 INPUT: Match=SafeNetinc Hits=24 Target=REPEAT SRC=38.100.26.120:6882 DST=192.168.1.64:35022 Proto=UDP
20:10:01 INPUT: Match=UniversityofPittsburgh Hits=2 Target=REPEAT SRC=130.49.6.130:2244 DST=192.168.1.64:35022 Proto=TCP
lwpack@lwpack-desktop:~$

---

### Post by uljanow on 2008-05-06
Which java version are you using ("java -version") ? Are there any error messages if you start the GUI ("sudo ipblock -g") ?

---

### Post by lwpack on 2008-05-06
lwpack@lwpack-desktop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

There are no errors when running sudo ipblock -g

The other thing I should mention is that the tabs Protection, Lists, Settings don't appear.  The gui starts up completely frozen.  I tried the java workaround in case that's what was causing it, but it didn't help.  Thanks for the help.

---

### Post by DJiNN on 2008-05-07
I've just installed this app on Hardy (Xubuntu) & it's working fine. Easier to get going than MoBlock for me, and i really like the interface.  Is it still being developed? :)

---

### Post by uljanow on 2008-05-07
> **lwpack said:**
> lwpack@lwpack-desktop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

gcj is not fully java compatible. You could try sun-java5-jre instead (Updating the default settings can be done with "sudo update-alternatives --config java").

---

### Post by uljanow on 2008-05-07
> **DJiNN said:**
> Is it still being developed?
Yes.

---

### Post by lwpack on 2008-05-07
That worked.  Thank you!
Also, it doesn't seem to start automatically when I boot even though the autostart box is checked.  I changed line 133 in /usr/sbin/ipblock to sleep 2, but it hasn't helped.

---

### Post by uljanow on 2008-05-09
> **lwpack said:**
> Also, it doesn't seem to start automatically when I boot even though the autostart box is checked.

Are you using another firewall application ? IPblock needs to be started after other firewalls. Particulary firewalls that start with a gnome-session conflict with the autostart option of IPblock.

---

### Post by Berolina on 2008-05-21
Hi, 
I'm trying to use ipblock, but encounter a java problem when starting it. As I am rather new to Ubuntu I would like to know how to solve this issue:

[HTML]:~/Desktop$ sudo ipblock -g
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/**xawt/libmawt.so**
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.Component.<clinit>(Component.java:568)
[/HTML]
The highlighted part of the path is missing in my installation

This is the jdk version I use:
[HTML]java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
[/HTML]

What must I do to get the correct version? 
I installed ipblock via gdebi, no error messages or missing packages reported during installation.

Thanks a lot,

Berolina

---

### Post by uljanow on 2008-05-21
The OpenJDK doesn't include most GUI libs yet due to licensing issues. You could try sun-java6-jre instead (Updating the default settings can be done with "sudo update-alternatives --config java").

---

### Post by Berolina on 2008-05-21
> **uljanow said:**
> The OpenJDK doesn't include most GUI libs yet due to licensing issues. You could try sun-java6-jre instead (Updating the default settings can be done with "sudo update-alternatives --config java").

Hi Uljanow,

thanks a lot, works like charm now.... keep up the good work!!!

Berolina

---

### Post by joeboentoe on 2008-05-29
I get an error when trying to install:

 sudo apt-get install libnetfilter-queue1


the error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libnetfilter-queue1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7986B of archives.
After this operation, 69.6kB of additional disk space will be used.
(Reading database ... 145641 files and directories currently installed.)
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.13-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libnetfilter-queue1_0.0.13-1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libnetfilter_queue_libipq.so.1.0.0', which is also in package libnetfilter-queue
Errors were encountered while processing:
 /var/cache/apt/archives/libnetfilter-queue1_0.0.13-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I deleted /usr/lib/libnetfilter_queue_libipq.so.1.0.0, but that don't works. I hope that wasn't an important lib :p

I am on an amd64 and running ubuntu hardy heron

Someone has a solution?

---

### Post by uljanow on 2008-05-29
Try to remove libnetfilter-queue* first.
```

sudo apt-get --purge remove libnetfilter-queue libnetfilter-queue1
sudo gdebi /path/to/iplist*.deb

```

---

### Post by joeboentoe on 2008-05-29
thank you very much!, it worked!

---

### Post by belgofac on 2008-06-08
WOW!  This is it guys, this is the new Peerguardian for Linux.  For the last 2 days I had problems trying to get Moblock working with Mint Elyssa
(I stil have Moblock running with mint Daryna) but with no luck.
This worked straight out of the box.  Great work.

For future reference:

Ipblock started to block my own machines after a few minutes (192.0.0.0)
Put this number in a new "allow" list and Bob's your uncle.

If you get an error message combo window like "error: could not find Trojan.gz list and Java error", there's absolutely nothing wrong with Java, it just cannot load that particular list.  Remove this list from preferred lists and reload.  

Again, great work. 

Maybe you could put the following into your "HowTo"
for Linux noobs like myself:

When making your own "allow" list make sure you do a "sudo chmod 777 /var/cache/iplist/" beforehand.  Copy the allow.p2p list, rename it to e.g. allowme.p2p, place it in the same /var/cache/iplist/ directory.  Open your new allowme.p2p and delete the Ip #'s in there and replace them with the ones you want to whitelist. 

Next you "sudo gedit /etc/ipblock.conf" and look for the line with ALLOW_LIST="allow.p2p"
Add the newly created allowme.p2p after allow.p2p and save.  It looks like this: ALLOW_LIST="allow.p2p allowme.p2p"

Thanks,

Ed

---

### Post by Nameless_one on 2008-06-10
Why would you "sudo chmod" that directory? I think you probably shouldn't.

---

### Post by belgofac on 2008-06-12
> Why would you "sudo chmod" that directory? I think you probably shouldn't.

Could not get access to it to put the allowme.p2p in it.

---

### Post by Nameless_one on 2008-06-12
You should just use sudo. If you use a graphical interface, you could run "gksudo nautilus" to get a nautilus window with root privileges, and if you use the command line, you should just "sudo mv" the file into the directory.

---

### Post by belgofac on 2008-06-14
I ran into a bit of a problem:

Opera is getting blocked (Opera software + widgets). I put it in the whitelist as follows:

> This is an example allow list which must be uncompressed
# and in p2p format. It's recommended to keep the number of
# entries small (e.g. 100).
#
# <Name> : <Start IP> - <End IP>

# IPs needed for updating lists
My machine: 192.168.0.0 - 192.168.0.255
MCE australia: 210.50.7.243
Opera: 213.236.208.60 - 213.236.208.255
# Warning: don't use this list for custom entries
# because the package manager might remove/override the
# changes made to this file
# Instead create a separate list and add it to ALLOW_LIST
# in /etc/ipblock.conf


My machine IP is ok but the 2 other Ip's remain blocked.  See the ipblock.log below:

> 15:21:24 OUTPUT: Match=OperaSoftwareASA Hits=16 Target=REPEAT SRC=192.168.0.2:59714 DST=213.236.208.60:80 Proto=TCP
15:22:06 OUTPUT: Match=OperaSoftwareASA Hits=17 Target=REPEAT SRC=192.168.0.2:59720 DST=213.236.208.60:80 Proto=TCP
15:23:02 OUTPUT: Match=OperaSoftwareASA Hits=18 Target=REPEAT SRC=192.168.0.2:59725 DST=213.236.208.60:80 Proto=TCP
15:23:34 OUTPUT: Match=OperaSoftwareASA Hits=19 Target=REPEAT SRC=192.168.0.2:59727 DST=213.236.208.60:80 Proto=TCP
15:24:26 OUTPUT: Match=OperaSoftwareASA Hits=20 Target=REPEAT SRC=192.168.0.2:59729 DST=213.236.208.60:80 Proto=TCP
15:27:54 OUTPUT: Match=OperaSoftwareASA Hits=21 Target=REPEAT SRC=192.168.0.2:39683 DST=213.236.208.60:80 Proto=TCP
15:28:02 OUTPUT: Match=OperaSoftwareASA Hits=22 Target=REPEAT SRC=192.168.0.2:39685 DST=213.236.208.60:80 Proto=TCP
15:28:12 OUTPUT: Match=OperaSoftwareASA Hits=23 Target=REPEAT SRC=192.168.0.2:39688 DST=213.236.208.60:80 Proto=TCP

---

### Post by belgofac on 2008-06-14
> Opera blocked, see previous post

I can answer my own question: after a re-boot it worked. Logging out and in again did not help.

---

### Post by uljanow on 2008-06-14
IPblock needs to be restarted in most cases if configuration files are changed.

The MCE australia line is malformed. It has to look like
```
MCE australia: 210.50.7.243 - 210.50.7.243
```

---

### Post by belgofac on 2008-06-15
UJ:Thanks mate, all ok now.:)

---

### Post by Nameless_one on 2008-06-20
I've got a problem with IPBlock. What happens is, after a few hours, IPBlock continues to run, but stops working. I leave the house, and when I return, the log only has blocked connections for a few hours after I started IPBlock. 

If I press Restart, or Disable and Enable it again, it starts blocking connections immediately.

---

### Post by uljanow on 2008-06-21
When IPblock restarts it appends the old messages in the logfile to the log box so it could appear that it blocks connections. If that is not the case here what does the following show after a few hours
```
sudo ipblock -l
sudo egrep "iplist|ipblock" /var/log/syslog*
```

You could also try to ping a host (if you use level1.gz):
```
ping $(zcat /var/cache/iplist/level1.gz | grep -o -E "([0-9.]+){4}" | head -n1)
```

---

### Post by Nameless_one on 2008-06-22
It seems to be working after all. When I ping 3.0.0.0, ping outputs
```
PING 3.0.0.0 (3.0.0.0) 56(84) bytes of data.
From 172.19.3.2 icmp_seq=1 Destination Port Unreachable

```

and the log also shows this. So it must be working.

---

### Post by JemW on 2008-06-27
I'm uncertain about a couple of things:

I have IPblock set to autostart. How can I tell if it's running? Is it a service running in the background? If I open the GUI and then close it, does that kill it completely or...is it still running?

When should I use the Ignored Ports section? Do I need ticks in boxes here as a default?

Thanks.

---

### Post by uljanow on 2008-06-29
> **JemW said:**
> I have IPblock set to autostart. How can I tell if it's running? Is it a service running in the background? If I open the GUI and then close it, does that kill it completely or...is it still running?If autostart is set it starts as a service during boot process. You can check the status with "sudo ipblock -l". If you close the GUI it will continue to work.


> When should I use the Ignored Ports section? Do I need ticks in boxes here as a default?That depends on how you use IPblock and what kind of services interfere with it.

---

### Post by JemW on 2008-07-12
Can I rephrase my question and hopefully someone can educate me:

I'm using IPblock 0.19 on Ubuntu Hardy, with Azureus 2.5.0.4 for obvious purposes. If that's all I use it for, what would you recommend as the optimum settings? If I have Incoming and Outgoing checked (don't know if that's necessary) then I can't contact some websites using the the browser, such as [www.bbc.co.uk](www.bbc.co.uk). Other sites seem to be OK so far. So, currently I have the settings as per the attached screenshot, to overcome the 'bbc problem'. Do I / Should I check any of the other 'Ignore' fields? If so, why...? And will my choice of settings affect network performance in any way?

Thanks.

---

### Post by uljanow on 2008-07-14
The settings are reasonable. I wouldn't change connection settings (incoming and outgoing are required in this case). If the ignore http option is set ipblock should not affect visiting websites. The   overhead of ipblock is very low.

---

### Post by JemW on 2008-07-14
> **uljanow said:**
> The settings are reasonable. I wouldn't change connection settings (incoming and outgoing are required in this case). If the ignore http option is set ipblock should not affect visiting websites. The   overhead of ipblock is very low.

Many Thanks!

---

### Post by berzerke on 2008-07-16
I've got IPBlock working. No problems there. I am concerned about the block lists though. According to the config file, it gets it's lists from Bluetack. Poking around in their forums, it looks like the lists haven't been updated in around 2 years. Using old, outdated lists probably defeats most of the usefulness of ipblock.

I did find the page [http://www.bluetack.co.uk/bims/filters/](http://www.bluetack.co.uk/bims/filters/) which does have recently updated lists, but only 4 of them, and looking at the ipblock config file for URL's (/usr/share/doc/iplist/README.lists), it doesn't seem to be downloading any from this page.

Am I missing something here or is the default configuration out of date?

---

### Post by jre on 2008-07-16
> **berzerke said:**
> I've got IPBlock working. No problems there. I am concerned about the block lists though. According to the config file, it gets it's lists from Bluetack. Poking around in their forums, it looks like the lists haven't been updated in around 2 years. Using old, outdated lists probably defeats most of the usefulness of ipblock.
Most bluetack lists (e.g. the [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)) are updated daily. I don't understand what information you got.
For example I made a diff between the level1 list of 2008-06-18 and 2008-07-13. This counts 5757 lines, so there were about 2000 changes. Of course some (or perhaps even many) might only be minor or fixing a typo.
But still, I don't know any better lists. Remember that Windows PeerGuardian uses the same lists.

The lists in [http://www.bluetack.co.uk/bims/filters/](http://www.bluetack.co.uk/bims/filters/) are just a compilation of the lists in [http://www.bluetack.co.uk/config](http://www.bluetack.co.uk/config). So if you want to go for the most up-to-date lists choose the latter source.

Greets
jre

---

### Post by berzerke on 2008-07-16
The reason I believe(d) the lists are old is the following: If you look at the blocklist FAQ on the bluetack site ([http://www.bluetack.co.uk/forums/index.php?autocom=faq&CODE=02&qid=17](http://www.bluetack.co.uk/forums/index.php?autocom=faq&CODE=02&qid=17)), there is a download link. This takes you to lots of the individual blocklists ([http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4](http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4)). All of them are dated June 8, 2006. Thus the two years old.

I've downloaded nipfilter from both [http://www.bluetack.co.uk/config/](http://www.bluetack.co.uk/config/) and [http://www.bluetack.co.uk/bims/filters/](http://www.bluetack.co.uk/bims/filters/) and the md5sums are identical. It appears the FAQ link is outdated, not the lists themselves.

Whew...Good to be wrong. Thanks for setting me straight.

---

### Post by jre on 2008-07-16
Ah, I think this date is just the date of the description :-)
AFAIK ipfilter.dat lists are just compiled once a week or even a month. The other (single) lists (like level1) get updates on a daily or even higher frequency.

Have fun
jre

---

### Post by uljanow on 2008-07-29
> * release (0.20)
* fixed gcc-4.3 compiling issues
* added menu starter for fedora
* moved README.lists to /etc/ipblock.lists
* added import URL feature in GUI
* added OpenSuSE 11 support

I dropped support for Feisty, Gutsy and Fedora Core 7 and 8.

---

### Post by TheValk on 2008-08-03
Thanks for a very useful utility.
I have one question however.
I am running version 0.2 on Hardy.
My LAN is using IP range 172.16.0.1 - 99 so it gets hits from BOGON in the Log.
I created a list called allowmy.p2p in /var/cache/iplist/
containing 
My Lan :	172.16.0.1	- 172.16.0.99
and altered the entry in /etc/ipblock.conf to read
ALLOW_LIST="allow.p2p allowmy.p2p"

After rebooting I still get entries in the GUI log window such as
12:25:40.177879 Blocked=Bogon Hits=17 SRC=172.16.0.16 DST=224.0.0.1 Proto=IGMP HW_PROTO=0x2048 LEN=36 ID=132 INDEV=2
appearing.
What am I misunderstanding?

---

### Post by uljanow on 2008-08-03
Allowing IP-ranges results in checking whether the destination is in that range (in IN, OUT and FWD chains). It doesn't check the source IP. Therefore the above log entry appears due to DST=224.0.0.1 . This means that you can connect to machines in 172.16.0.1-99 and vice versa.

---

### Post by TheValk on 2008-08-03
I see. Thanks for the swift reply and thanks again for IPblock.

---

### Post by Toleedo on 2008-08-07
I installed ipblock on hardy and everything was fine, but recently when ipblock is running i cannot access webpages.  I have http allowed.  To fix this I basically do the disable enable thing with my nic, this allows me to access webpages but then ipblock stops blocking.  Restarting ipblock gets it blocking again, but then I can't access webpages...does anyone know why this is?  Thanks in advance

---

### Post by uljanow on 2008-08-10
You could try to ignore UDP-port 53. What does "egrep "iplist|ipblock" /var/log/syslog*" show ?

---

### Post by bark50 on 2008-08-10
I installed IP Block two days ago, and it has worked fine up until now.  Today I started it and updated the lists.  Now it tells me "Blocking 0 IP Ranges."  I've tried restarting it and rebooting my machine.  How can I get it working again?  Thanks.

---

### Post by uljanow on 2008-08-10
Looks like the last update went wrong and the lists have probably zero size. It seems like Bluetack has some issues. But it should be fixed now (I set the iplist mirror as primary source). Just try another update.

---

### Post by bark50 on 2008-08-10
Many, many thanks!  That did it!

---

### Post by lwpack on 2008-08-16
Hi.  I am trying to connect to my home machine from work (both running hardy) via remote desktop on port 5900.  I have ipblocker running on my home machine and it blocks the remote desktop connection.  I know this because when I disable ipblock it works fine.  On the settings tab I have tcp and udp checked and I wrote in 5900.  What am I doing wrong?  Thanks.

---

### Post by uljanow on 2008-08-16
The ignored port section in the GUI is for outgoing connections only. You could add the port to **IGN_TCP_INPUT** and **IGN_UDP_INPUT** in **/etc/ipblock.conf**.

---

### Post by lwpack on 2008-08-16
Thanks, that worked.

---

### Post by uljanow on 2008-09-14
A new version is out ! 
Changes:
	> * release (0.21)
	* added BLOCK_LIST_*, ALLOW_LIST_* and IPTABLES_CHAIN_ALLOW options
	* modified GUI to show the last 12 log entries
	* allow lists can optionally be compressed with gzip
	* extendet LOG_IPTABLES feature to show allowed packets
	* Update messages are appended to logfile
	* added Update dialog for adding lists from URL
	* default allow list is only valid in the output chain
	* added more countries (e.g. russia, india)
	* improved GUI cleanup

---

### Post by gingin on 2008-09-21
application have worked with out a hitch until came a long same updates... Just not sure what.. IP block began to freeze and not to respond.
A question is how to clean uninstall IP block ?

---

### Post by uljanow on 2008-09-22
> **gingin said:**
> application have worked with out a hitch until came a long same updates... Just not sure what.. IP block began to freeze and not to respond.
A question is how to clean uninstall IP block ?

Could you post the output of "sudo java -verbose -jar /usr/share/java/ipblockUI.jar" and perhaps "grep -r upgrade /var/log/dpkg.log" to see if an upgraded package caused some issues. 
You can remove IPblock with
```
sudo aptitude purge iplist
sudo rm -rf /var/cache/iplist
```

//EDIT:
To fix it I would remove every package that contains *gcj* (especially gcj-4.1, gcj-4.2, java-gcj-compat). Most packages that need gcj depend on a metapackage java2-runtime which is provided by sun-java[5-6]-jre, so it shouldn't remove any wanted packages.

---

### Post by uljanow on 2008-10-02
> Changes
* release (0.22)
* added BLOCK_TARGET_* options and set the default 
  action for incoming blocked packets to DROP
* modified GUI log entries
* fixed new GUI logging bug.

---

### Post by nfw on 2008-10-02
Hey guys.

Just installed Ipblock, working ok. One problem though. When checking my Transmission settings page, it says that my port is closed, but I have the port listed in the TCP ignored ports section. Any solutions?

EDIT: Nevermind, I got it fixed. The ignore setting in the GUI only applies to outgoing connections. I went into /etc/ipblock.conf and found the setting I needed to change (incoming TCP).

---

### Post by jre on 2008-10-03
> **nfw said:**
> Just installed Ipblock, working ok. One problem though. When checking my Transmission settings page, it says that my port is closed, but I have the port listed in the TCP ignored ports section. Any solutions?

EDIT: Nevermind, I got it fixed. The ignore setting in the GUI only applies to outgoing connections. I went into /etc/ipblock.conf and found the setting I needed to change (incoming TCP).

Are you sure that you want IPBlock to ignore traffic on your transmission port? Why did you install it?

:-)
jre

---

### Post by nfw on 2008-10-03
> **jre said:**
> Are you sure that you want IPBlock to ignore traffic on your transmission port? Why did you install it?

:-)
jre

It came with my Ubuntu installation. The interface is simple, so I went with it. Does nobody like it?

---

### Post by jre on 2008-10-04
> **nfw said:**
> It came with my Ubuntu installation. The interface is simple, so I went with it. Does nobody like it?

IPList/IPBlock is a fine application.
You misunderstood me, I wrote: Are you sure that you want IPBlock to **ignore** traffic on your transmission port?

So I think you are configuring it the wrong way. Most people install IPBlock so that it can check traffic of apps like transmission. But you told IPBlock not to check transmissions traffic.
I know that you did this because transmission said that the port is closed. This probably happened because IPBlock blocked the test IP used by transmission. So the right way to fix your problem is to allow traffic to this test IP.

---

### Post by uljanow on 2008-10-04
As mentioned on the mailing list the next version will have a new GUI with native look & feel and some other features like systray (systray only works with metacity).

---

### Post by kpkeerthi on 2008-10-06
The native GUI is a welcome change. Just curious what GUI toolkit will be used for building the GUI?

systray only works with metacity? - What about openbox/xfce users (like me)?

I wish the toolbar, where Disable, Restart, etc. buttons are displayed, 
uses GTK icons with labels instead of labels only.

Will it still require JRE as a dependency?

---

### Post by uljanow on 2008-10-06
The GUI toolkit is still Swing but java 1.6 has a new Swing Application Framework which can display GUIs in a native way on Windows XP, Vista, Mac OSX and Linux GNOME. Therefore I can reuse the existing Code. :) However the native look & feel will only apply to GNOME.

Systray works only with metacity at the moment. But an updated version of java (1.6.0.10) extends that support to compiz.

A jre is still needed, but openjdk6 is sufficient which is GPL. So there's no need to install the proprietary sun-java6-jre.

---

### Post by kpkeerthi on 2008-10-07
Thanks. Appreciate your reply.

If I run iplist in command-line mode, will jre still be used and running?

---

### Post by uljanow on 2008-10-07
No. iplist/ipblock can be used from the command-line without java.

---

### Post by kpkeerthi on 2008-10-07
> **uljanow said:**
> No. iplist/ipblock can be used from the command-line without java.

Great. I going to try it now (in Archlinux).

---

### Post by uljanow on 2008-10-14
Finally:)> Changes:
* release (0.23)
* new GUI with native look & feel in GNOME
* added systray support (only Metacity currently)
* added new ipblock icon
* added GUI logfile 
* added GUI_START_MINIMIZED option
* added GUI_LAST_LOG_LINES option
* added GUI_AUTOSCROLL option

---

### Post by uljanow on 2008-11-07
There is a new Ubuntu repository available (i386, amd64) at 
```
deb http://ppa.launchpad.net/ssakar/ubuntu intrepid main
deb-src http://ppa.launchpad.net/ssakar/ubuntu intrepid main
```
The main page is updated accordingly.

[Furthermore I'm trying to get it upstream.]("https://bugs.launchpad.net/ubuntu/+bug/294838")

---

### Post by airbornemist6 on 2008-11-09
I can't get the GUI to come up. From CLI, I can get it to update and start blocking, however, when I try and start the GUI it just sits there and does nothing. Any ideas?

---

### Post by uljanow on 2008-11-09
What does **/tmp/ipblockUI.log** show after a failed attempt with "sudo ipblock -g" ?

---

### Post by airbornemist6 on 2008-11-09
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.EventQueue.invokeLater(EventQueue.java:957)
	at javax.swing.SwingUtilities.invokeLater(SwingUtilities.java:1289)
	at org.jdesktop.application.Application.launch(Application.java:181)
	at ipblockui.IpblockUIApp.main(Unknown Source)

---

### Post by uljanow on 2008-11-09
You could try the jre from the package **sun-java6-jre**. After the installation it is required to select it as the default one.
```
sudo update-alternatives --config java
```

---

### Post by airbornemist6 on 2008-11-09
Awesome! Thanks! That fixed it! Now I can use linux as my primary operating system! xD

---

### Post by roger7 on 2008-11-27
Noob here.
I'm using Intrepid with a fresh install.
Trying to get iplist 0.23 working but getting errors
I suspect they are java errors but I am running JRE 6.
It is showing as disabled and when I try to enable it gives the following error messages
```
[COLOR="Blue"]iplist[7011] error: can't find level1.gz
ipblock[6997] error: failed to start, cleaning up.[/COLOR]
```

When I try to update nothing seems to happen.

Any help would be much appreciated
Thanks

---

### Post by uljanow on 2008-11-27
Updates should work now. Just try another update and restart. You could also temporarily remove the list.

---

### Post by uljanow on 2008-11-30
A new version is out. Since yesterday the download section at sourceforge.net only contains packages that are not available from the new software repositories (Ubuntu, Fedora and OpenSuSE). How to get the latest version using repositories is described at  [http://iplist.sourceforge.net/download.html](http://iplist.sourceforge.net/download.html) . 
 
The new version in the repositories is labed 0.24-0ubuntu3 and 0.24-21.1 (Fedora and OpenSuSE), respectively. 
 
The short description of this release would be that it has an easy-to-use whitelist manager.  
 
The long version: 
* enabled busyIcon of the GUI 
* fixed compiler warnings  
* fixed lintian error due to force-reload 
* added IGN_PROTO_* options to ignore protocols 
* changed Debian java dependency to java6-runtime 
* fixed opensuse autostart issues 
* added new whitelist manager 
* added context menu to allow logged IPs 
* fixed compiler warnings 
* added LESS_MEMORY option and compiler flag 
* renamed option to GUI_START_HIDDEN 
* added GUI_THEME option 
* added GUI_WHITELIST_* options 
* added log column Type 
* added -i parameter to ipblock 
* added automatical restart to list manager 
* added online help menuitem

---

### Post by EdThaSlayer on 2008-11-30
Do you really have to keep running this program as root? I'm kind of getting scared, or can I just do the list thing and quit IPblocker?

---

### Post by uljanow on 2008-11-30
IPlist and IPblock require root privileges. The GUI doesn't stop blocking if you close it. So you could use it just for tweaking settings and then close it.

---

### Post by EdThaSlayer on 2008-11-30
> **uljanow said:**
> IPlist and IPblock require root privileges. The GUI doesn't stop blocking if you close it. So you could use it just for tweaking settings and then close it.

Good to hear this news. :) 
Thanks for the info. I will update it once every week by running the application.

---

### Post by gingin on 2008-12-07
Thank you for really nice how to. But it is same tiny things to make it really finish to perfection.As specially for people with a beginers experiences.

> Create a new file in /etc/apt/sources.list.d named iplist.list with the following content:[QUOTE]
[/QUOTE]

After creating a new file with text editor (ipilist.list) I can not save it in normal fashion, because promition is denied.
Mine first question would be: how to do that? 
Must be don in terminal? If it is so how to create text file in terminal.

> The iplist package can be installed with gdebi which resolves all dependencies or manually after having installed the following prerequisites:[QUOTE]
[/QUOTE]

There we meeting another problem,specially for beginer.
iplist-0.24.tar.gz -this is what you are getting after download as an iplist.After extracting  iplist-0.24.tar.gz on desktop (usual situation),
you are geting iplist-0.24 folder containing a lot of files and none of t
hem can be installed with Archive manager.
So how to handle all those files in  iplist-0.24 folder? What to do with them?

I think answers to those questions will help really aloat.

Thanks in adwance

---

### Post by uljanow on 2008-12-07
Try to open the texteditor with "sudo gedit &" in a terminal. Afterwards:

sudo aptitude update
sudo aptitude install iplist

---

### Post by silverwolf636 on 2008-12-08
I've been running IPBlock for a week now with outstanding results. It was blocking 271k ports but now it's only 7434 ports. Any idea what may have happen?

Thanx

---

### Post by uljanow on 2008-12-08
Maybe an update didn't finish. Does it still occur after another update ?

---

### Post by silverwolf636 on 2008-12-09
I'm back up to 228846.  Still missing a few but it's a little better.

---

### Post by lwpack on 2008-12-13
Hi.  I'm running pyTivo which transfers video files from my computer to my tivo (which is on the same network) on a port of my choosing (9032 say).  I've noticed that if I start pyTivo before ipblock, everything is fine.  But if ipblock is started first, it blocks pyTivo even though it's set to ignore port 9032 and my home network is in my whitelist.  Is there a workaround?

---

### Post by Hashmere on 2008-12-13
How does this program compare to MoBloquer?

---

### Post by uljanow on 2008-12-13
> **lwpack said:**
> Hi.  I'm running pyTivo which transfers video files from my computer to my tivo (which is on the same network) on a port of my choosing (9032 say).  I've noticed that if I start pyTivo before ipblock, everything is fine.  But if ipblock is started first, it blocks pyTivo even though it's set to ignore port 9032 and my home network is in my whitelist.  Is there a workaround?

In the default configuration whitelisting is only valid for outgoing traffic. To whitelist incoming connections change the option in /etc/ipblock.conf (as root) to:
```
ALLOW_LIST_INPUT="allow-perm.p2p allow-temp.p2p"
```

---

### Post by crog62 on 2008-12-16
Hi - Running ipblock/iplist on Intrepid and cannot get it to start. I get the message: 

[INDENT]ipblock -sl
iptables: No chain/target/match by that name
ipblock[27682]: error: failed to start, cleaning up
[/INDENT]
output of DEBUG=1 ipblock -sl
[INDENT]DEBUG=1 ipblock -sl

+ set -e
+ set -u
+ PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin
+ VERSION=0.24
+ QUEUE=0xff
+ QUEUE_INPUT=0xfd
+ QUEUE_OUTPUT=0xfe
+ QUEUE_FORWARD=0xff
+ POLICY=REPEAT
+ POLICY_MARK=0xfffe
+ BLOCK_TARGET=REPEAT
+ BLOCK_TARGET_INPUT=DROP
+ BLOCK_TARGET_OUTPUT=REPEAT
+ BLOCK_TARGET_FORWARD=REPEAT
+ BLOCK_TARGET_MARK=0xffff
+ NICE=-5
+ NEW=-m state --state NEW
+ GUI_LOG_FILE=/tmp/ipblockUI.log
+ [ -f /etc/ipblock.conf ]
+ . /etc/ipblock.conf
+ AUTOSTART=Yes
+ IPTABLES_CHAIN_BLOCK=INPUT OUTPUT 
+ IPTABLES_CHAIN_ALLOW=OUTPUT
+ LESS_MEMORY=No
+ BLOCK_LIST=level1.gz ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz 
+ BLOCK_LIST_INPUT=
+ BLOCK_LIST_OUTPUT=
+ BLOCK_LIST_FORWARD=
+ ALLOW_LIST=
+ ALLOW_LIST_INPUT=
+ ALLOW_LIST_OUTPUT=allow.p2p allow-perm.p2p allow-temp.p2p
+ ALLOW_LIST_FORWARD=
+ IGN_TCP_INPUT=
+ IGN_UDP_INPUT=
+ IGN_TCP_OUTPUT=http 
+ IGN_UDP_OUTPUT=domain ntp
+ IGN_TCP_FORWARD=
+ IGN_UDP_FORWARD=
+ IGN_PROTO_INPUT=
+ IGN_PROTO_OUTPUT=
+ IGN_PROTO_FORWARD=
+ IPLIST_LISTDIR=/var/cache/iplist
+ LOG_FILE=/tmp/ipblock.log
+ LOG_LEVEL=match
+ LOG_IPTABLES=No
+ VERBOSE=Yes
+ URL_FILE=/etc/ipblock.lists
+ UPDATE_STAMP=/var/cache/iplist/.update-stamp
+ UPDATE_INTERVAL=1
+ http_proxy=
+ GUI_START_HIDDEN=No
+ GUI_LAST_LOG_LINES=10
+ GUI_AUTOSCROLL=Yes
+ GUI_THEME=Gtk
+ GUI_WHITELIST_PERM=/var/cache/iplist/allow-perm.p2p
+ GUI_WHITELIST_TEMP=/var/cache/iplist/allow-temp.p2p
+ export IPLIST_LISTDIR
+ export http_proxy
+ id -u
+ [ 0 != 0 ]
+ [ 1 -ne 0 ]
+ LOG_IPTABLES=0
+ VERBOSE=-v
+ getopts sdriucglvh opt
+ do_start
+ is_running
+ local ret=0
+ iptables -L -n
+ grep -E _MATCH|_QUEUE
+ pkill -SIGUSR1 iplist
+ return 0
+ trap on_start_failure INT TERM EXIT
+ start_iplist
+ nice -n -5 iplist --daemon -v -f /tmp/ipblock.log -l match
+ sleep 1
+ eval echo $BLOCK_TARGET_INPUT
+ echo DROP
+ eval echo $QUEUE_INPUT
+ echo 0xfd
+ eval echo $BLOCK_LIST_INPUT
+ echo
+ iplist -i -p REPEAT -P 0xfffe -t DROP -T 0xffff -n 0xfd level1.gz ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz
+ eval echo $BLOCK_TARGET_OUTPUT
+ echo REPEAT
+ eval echo $QUEUE_OUTPUT
+ echo 0xfe
+ eval echo $BLOCK_LIST_OUTPUT
+ echo
+ iplist -i -p REPEAT -P 0xfffe -t REPEAT -T 0xffff -n 0xfe level1.gz ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz
+ insert_rules
+ iptables -N BLOCK_MATCH
+ iptables -N ALLOW_MATCH
+ [ 0 -eq 0 ]
+ iptables -A BLOCK_MATCH -p tcp -j REJECT --reject-with tcp-reset
+ iptables -A BLOCK_MATCH -j REJECT --reject-with icmp-port-unreachable
+ iptables -A ALLOW_MATCH -j ACCEPT
+ cd /var/cache/iplist
+ [ -f /etc/fedora-release ]
+ [ -f /etc/SuSE-release ]
+ iptables -N INPUT_QUEUE
+ eval echo $IGN_TCP_INPUT
+ echo
+ eval echo $IGN_UDP_INPUT
+ echo
+ eval echo $IGN_PROTO_INPUT
+ echo
+ echo OUTPUT
+ grep -q INPUT
+ eval echo $QUEUE_INPUT
+ echo 0xfd
+ iptables -A INPUT_QUEUE -j NFQUEUE --queue-num 0xfd
+ iptables -I INPUT 1 -m mark --mark 0xffff -j BLOCK_MATCH
+ iptables -I INPUT 2 -m state --state NEW -m mark ! --mark 0xfffe -j INPUT_QUEUE
+ iptables -N OUTPUT_QUEUE
+ eval echo $IGN_TCP_OUTPUT
+ echo http
+ iptables -A OUTPUT_QUEUE -p tcp --dport http -j RETURN
+ eval echo $IGN_UDP_OUTPUT
+ echo domain ntp
+ iptables -A OUTPUT_QUEUE -p udp --dport domain -j RETURN
+ iptables -A OUTPUT_QUEUE -p udp --dport ntp -j RETURN
+ eval echo $IGN_PROTO_OUTPUT
+ echo
+ echo OUTPUT
+ grep -q OUTPUT
+ zcat -fq allow.p2p allow-perm.p2p allow-temp.p2p /dev/null
+ sed s/[ \t]*//g
+ grep -o -E ([0-9.]+){4}[-]([0-9.]+){4}
[B]+ iptables -A OUTPUT_QUEUE -m iprange --dst-range 130.149.17.156-130.149.17.156 -j ALLOW_MATCH
iptables: No chain/target/match by that name[/B]
+ on_start_failure
+ logger -s -t ipblock[12263] error: failed to start, cleaning up
ipblock[12263]: error: failed to start, cleaning up
+ do_stop
+ is_running
+ local ret=0
+ iptables -L -n
+ grep -E _MATCH|_QUEUE
+ ret=2
+ pkill -SIGUSR1 iplist
+ ret=5
+ return 5
+ delete_rules
+ stop_iplist
+ iplist -k
[/INDENT]

It appears to fail on iptables -A OUTPUT_QUEUE -m iprange --dst-range 130.149.17.156-130.149.17.156 -j ALLOW_MATCH
 
Any ideas?

Craig

---

### Post by uljanow on 2008-12-16
Looks like there is no module iprange available. Is it enabled in your kernel ?
```
$ grep -ri iprange /boot/config-$(uname -r)
CONFIG_NETFILTER_XT_MATCH_IPRANGE=m
```

---

### Post by crog62 on 2008-12-16
You are correct, it is not enabled.

Newbie question - is there an easy way to enable this without rebuilding the kernel?

---

### Post by uljanow on 2008-12-16
No. But using the default Ubuntu kernel would be sufficient.

---

### Post by crog62 on 2008-12-16
It doesn't appear to be set in 2.6.25-2 which was installed with the upgrade to 8.10, Intrepid.

config-2.6.25-2-386:# CONFIG_NETFILTER_XT_MATCH_IPRANGE is not set

I'll research this some more - maybe pull off another version of the kernel if I can figure that out.

Thanks,
Craig

---

### Post by uljanow on 2008-12-16
I'd use linux-image-2.6.27-9-generic .

---

### Post by Scary Rob on 2009-01-01
I've just installed the latest version of IPBlock on Intrepid and hit something that I can't work out whether it's a problem or not.

I've used this program for previous versions of Ubuntu before, and the sign I usually take that it's working properly is that it won't let me look at government websites, the BBC website or Microsoft's official website. I've played with the settings, but I can get onto these websites while the current version of IPlist is running. Does this mean it's not working? And if not, how can I fix it?

Thanks in advance.

---

### Post by uljanow on 2009-01-01
Recent versions ignore http and dns by default. If you use level1.gz you could try
```
ping $(zcat /var/cache/iplist/level1.gz | grep -o -E "([0-9.]+){4}" | head -n1)
```

---

### Post by Toleedo02 on 2009-01-04
Code:

deb [http://ppa.launchpad.net/ssakar/ubuntu](http://ppa.launchpad.net/ssakar/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/ssakar/ubuntu](http://ppa.launchpad.net/ssakar/ubuntu) intrepid main

I'm new to ubuntu and was wondering how I go about putting this code into the folder /etc/apt/sources.list.d/iplist.list

I was able to create the iplist.list folder under root, but cannot figure out how to put the above code into this folder.  If anyone could help a noob out I would appreciate it.  Thank you.

---

### Post by uljanow on 2009-01-05
**iplist.list** should be the file containing the 2 lines. Try the following commands to add the repo:

```
sudo rmdir /etc/apt/sources.list.d/iplist.list
sudo wget http://iplist.sf.net/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/iplist.list
```

---

### Post by Toleedo02 on 2009-01-05
so basically I need to d/l the repo before creating the iplist.list directory?  Thanks

---

### Post by DeMartini on 2009-01-05
Create a new file (as root) in /etc/apt/sources.list.d named iplist.list with the following content depending on the Ubuntu version:

I'm using Hardy 8.04 and i'm not sure how to execute the above directions, can i create a new file in nautilus, then add the files???

---

### Post by Scary Rob on 2009-01-07
> **uljanow said:**
> Recent versions ignore http and dns by default. If you use level1.gz you could try
```
ping $(zcat /var/cache/iplist/level1.gz | grep -o -E "([0-9.]+){4}" | head -n1)
```

Thanks! I've only used it with the GUI, though. Where should I be putting this code? Is there a file I should be altering, or is this a terminal job?

---

### Post by uljanow on 2009-01-07
> **Scary Rob said:**
> Thanks! I've only used it with the GUI, though. Where should I be putting this code? Is there a file I should be altering, or is this a terminal job?

This is terminal command. Open a terminal and copy & paste it. Abort the test with control + C. The ipblock log window should show the blocked pings.

---

### Post by uljanow on 2009-01-07
> **DeMartini said:**
> I'm using Hardy 8.04 and i'm not sure how to execute the above directions, can i create a new file in nautilus, then add the files???

There is no need to create a folder. I updated the first post with easier installation instructions for hardy and intrepid. 

There is also a good wiki article on [how to add repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by newto on 2009-01-09
If I exit the GUI does it stop the program entirely, or does it continue to run in the background?

---

### Post by uljanow on 2009-01-10
If it's enabled and the GUI is closed it will continue to block in the background. The GUI is just a frontend. When the GUI starts it can also detect if the service is already running.

---

### Post by boob11 on 2009-01-14
thnx

---

### Post by teaguepatrick on 2009-01-18
Does this mean my computer is trying to send data to the Department of Defense?  All of this stuff says Type OUT - and to weird places like State of California, DoD, General Electric...

Someone help me understand this? Just online spam trolls trying to port scan me? or is my PC trying to contact these IP addresses??

If my computer is trying to contact all these sites without me telling it to - does that mean I have some kind of crazy linux spyware virus that is sending my data to the Department of Defense??

---

### Post by uljanow on 2009-01-18
At least the logs show an attemp to establish a connection to an IP-range owned by DoD. Is there any filesharing application running ?

With the command "netstat -n -p" you can list the programs using a network connection. It might be useful to disable ipblock during that time.

---

### Post by -jay- on 2009-01-19
thanks was looking for something like this

---

### Post by 1cyclops9 on 2009-01-22
hello, I am running LinuxMint 6 and for some reason I can't run the GUI of ipblock. Even from the terminal I type:

tyrone@tyrone-laptop ~ $ sudo ipblock -g
tyrone@tyrone-laptop ~ $ 

and that is all it happens it never open the GUI, I think the problem relies on java what can i do please?

---

### Post by uljanow on 2009-01-22
There is a GUI logfile located at **/tmp/ipblockUI.log**. Are there any messages in the logfile after "sudo ipblock -g" fails ?

---

### Post by 1cyclops9 on 2009-01-22
I get

java.lang.NoClassDefFoundError: com.sun.java.swing.plaf.gtk.GTKLookAndFeel
   at ipblockui.IpblockUIApp.startup(Unknown Source)
   at org.jdesktop.application.Application$1.run(Application.java:171)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.90)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.90)
   at java.awt.EventDispatchThread.run(libgcj.so.90)

---

### Post by 1cyclops9 on 2009-01-22
My /tmp/ipblockUI.log says:
java.lang.NoClassDefFoundError: com.sun.java.swing.plaf.gtk.GTKLookAndFeel
at ipblockui.IpblockUIApp.startup(Unknown Source)
at org.jdesktop.application.Application$1.run(Applica tion.java:171)
at java.awt.event.InvocationEvent.dispatch(libgcj.so. 90)
at java.awt.EventQueue.dispatchEvent(libgcj.so.90)
at java.awt.EventDispatchThread.run(libgcj.so.90)

---

### Post by uljanow on 2009-01-22
Try to install openjdk-6-jre or sun-java6-jre and set it as the default java vm.
```
sudo update-alternatives --config java
```
If there are still problems starting the GUI [this faq entry]("http://iplist.sourceforge.net/faq.html#0x06") might help.

---

### Post by 1cyclops9 on 2009-01-23
Its working now but only when I launch it from the terminal why is that?

---

### Post by uljanow on 2009-01-24
> **1cyclops9 said:**
> Its working now but only when I launch it from the terminal why is that?

This seems to be a bug in the mintMenu. But there is a workaround:
Run
sudo gedit /usr/share/applications/ipblock.desktop

and change the line 
Exec=gksu "/usr/sbin/ipblock -g"

to
Exec=gksu "/usr/sbin/ipblock gui"

,save and exit.

---

### Post by 1cyclops9 on 2009-01-24
Its working now thank you very much now I am gonna see if its actually working

---

### Post by ondrugs on 2009-02-01
does anyone know if there are any plans to make IpList available for PPC?

my Mac Mini is sitting here doing nothing. might as well put it to some good use!

---

### Post by uljanow on 2009-02-02
There are no plans for PowerPC support due to lack of hardware and working ppc emulation (openhackware bug). But you could [build deb packages]("http://iplist.sourceforge.net/faq.html#0x02") on ppc.

---

### Post by halovivek on 2009-02-02
Hi
i am using utorrent using wine as well torrent client in Ubuntu. will it block it default. if so how to overcome that one?

---

### Post by ondrugs on 2009-02-02
> **uljanow said:**
> There are no plans for PowerPC support due to lack of hardware and working ppc emulation (openhackware bug). But you could [build deb packages]("http://iplist.sourceforge.net/faq.html#0x02") on ppc.

Excellent! Thanks for that!

Now can anyone tell me how to submit a package installation bug report? :)

[INDENT]The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
[/INDENT]

---

### Post by silverwolf636 on 2009-02-02
I've had Ipblocker setup up for about a month now and have yet been able to update.  I am running 64bit hardy.  I was set up with 32bit but redid my system and installed the 64.  Just can't figure out what I am doing wrong.
Thanx

---

### Post by smcleod on 2009-02-04
ip blocker blocks my outgoing mail in evolution smtp server connection. in the ip blocker settings i have the ignored ports checked. when i try to send email this is what it says under the Protection tab

OUTPUT:Blocked=Savvis Hits=22 SRC=192.168.1.4.50587 DST=209.8.224:25 Proto=TCP

thanks for any help

---

### Post by uljanow on 2009-02-05
> **halovivek said:**
> Hi
i am using utorrent using wine as well torrent client in Ubuntu. will it block it default. if so how to overcome that one?

You could ignore the ports that utorrent uses if you don't want IPblock to filter those connections.

---

### Post by uljanow on 2009-02-05
> **smcleod said:**
> ip blocker blocks my outgoing mail in evolution smtp server connection. in the ip blocker settings i have the ignored ports checked. when i try to send email this is what it says under the Protection tab

OUTPUT:Blocked=Savvis Hits=22 SRC=192.168.1.4.50587 DST=209.8.224:25 Proto=TCP

If you add "smtp" to ignored outgoing TCP ports and restart IPblock it should allow mail traffic.

---

### Post by iceman_ch on 2009-02-06
Has anyone had any problems with it crashing as soon as you start running it?  I can start it in the terminal and it dosn't give any errors except that it won't update but, that could be because I'm at school. Whenever I start it the screen flickers and then goes nuts.  If I wait a while compuiz shuts off and returns me back to the desktop with Ipblock running.  I've checked the dependancies and I made sure java was installed.

---

### Post by uljanow on 2009-02-06
What does the logfile **/tmp/ipblockUI.log** say after you start it through the main menu ?

---

### Post by smcleod on 2009-02-08
> **uljanow said:**
> If you add "smtp" to ignored outgoing TCP ports and restart IPblock it should allow mail traffic.

thanks that did the trick:D

---

### Post by silverwolf636 on 2009-02-09
I am currently running Ipblock with the following list:
level1.gz
ads-trackers-and-bad-prOn.gz
edu.gz
spyware.gz
bogon.gz

I had a longer list but completely redid my system and they are gone.
Can someone forward me the link to get them (i.e. China, Microsoft, Trojan.gz, etc...)? I had around twenty (20) I think.

Thanx

---

### Post by uljanow on 2009-02-10
All lists can be added through List tab -> Add URL .

---

### Post by xingewen on 2009-02-10
Thanks, it's working like a charm .

---

### Post by kiprit on 2009-02-13
Thanks all for the explanations... I have a quick question though:

If I close the GUI, I understand that the IPlist is continuing to run; and I presume that it is running with all the lists that I added using IPblock...

On the other hand, I still think that it would be great to be able to minimize IPblock to system notification area. Is there a way to do it?

---

### Post by uljanow on 2009-02-14
> **kiprit said:**
> On the other hand, I still think that it would be great to be able to minimize IPblock to system notification area. Is there a way to do it?

Clicking on hide in the context menu of the IPblock icon in the system tray minimizes the GUI.

---

### Post by kiprit on 2009-02-18
> **uljanow said:**
> Clicking on hide in the context menu of the IPblock icon in the system tray minimizes the GUI.
I think this is my problem, IPblock never appears in my system tray...

---

### Post by uljanow on 2009-02-18
This feature requires the latest openjdk-6-jre or sun-java6-jre which are in Intrepid. Alternatively disabling compiz should make it appear in the system tray.

---

### Post by mistypotato on 2009-02-18
This looks like something I've been wanting :p

Not wanting to be a party pooper but I'm very new to Linux and I've heard a few precautionary words of wisdom from the admins here.....

so.....

How can we know this program doesn't have a malicious backend attached ?

Just curious and again, a totally linux noobie question

---

### Post by uljanow on 2009-02-19
> **mistypotato said:**
> How can we know this program doesn't have a malicious backend attached ?

Just curious and again, a totally linux noobie question

By reading the source code which is freely available on iplist.sf.net .

---

### Post by mistypotato on 2009-02-19
ah....

simple and elegant.
why isn't everyone using Linux instead of Windows.

thx

---

### Post by uljanow on 2009-02-19
A new version is out!> Changes: 
* release (0.25) 
* fixed gzip error message 
* moved icon to /usr/share/pixmaps/ 
* removed "-u root" parameter in desktop file 
* added gentoo init script 
* fixed linux mint menu starter issue 
* fixed OpenSuse 11.1 rpm-lint errors 
* fixed format of range names in logfile 
* added if-up script (Debian) 
* fixed GUI problem in Arch Linux 
* whitelisted ranges allow incoming traffic (default setting) 
* added -p option to restart iplist only (used by ipblock.cron) 
* removed update IP ranges in allow.p2p due to default http whitelist 

---

### Post by kiprit on 2009-02-21
> **uljanow said:**
> This feature requires the latest openjdk-6-jre or sun-java6-jre which are in Intrepid. Alternatively disabling compiz should make it appear in the system tray.

Since I do have the jre stuff the reason should be compiz related. But I would  prefer having compiz than having IPblock at sys tray. 
Thanks for the suggestions anyway!

Besides the tray icon issue i do really like IPblock and think it is a life saver!

---

### Post by Griz054 on 2009-02-23
I can't get the keys to authenticate the package.

```
griz@griz-laptop:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv 39456311108B243F
gpg: requesting key 108B243F from hkp server wwwkeys.eu.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

Any suggestions?

---

### Post by uljanow on 2009-02-23
You could save the [pub key]("http://iplist.sourceforge.net/uljanow.gpg") to a file and import it through *System->Administration->Software Sources->Authentication->Import Key-file*.

---

### Post by anabasi on 2009-02-27
Hi!

I can't get the keys to authenticate the package: I got the same error posted by Griz054.  
```

gpg: requesting key 108B243F from hkp server wwwkeys.eu.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

Moreover, the link posted by uljanow in the previous post doesn't seem be working: Firefox can't get a connection with the server keyserver.ubuntu.com:11371.

What can I do?

Thanks.

---

### Post by mistypotato on 2009-02-27
Hello uljanow,

Just wanted to thank you for all your efforts you put into this.

It's really a great program and VERY handy.  I have it running on 3 ubuntu 8.10 machines including a server.

It worls perfect on the server and one of my machines and I think you've read my posts so you're aware of the maxed out cpu issue I'm having on one of the pcs.

Anyway, I see you get tons of gripes and complaints....

[SIZE="4"]**This is a THANK YOU for all you do to make this happen**[/SIZE]  :KS:KS:KS:KS:KS

---

### Post by dimitriv on 2009-03-09
I installed as per the instructions on the How To front page  (Intrepid 8.10 both 32bit & 64bit [2 seperate installs both with 100% CPU usage]). 

When IP Blocker ran it consumed 100% CPU. It seemed to run OK (no errors etc.). While System Monitor shows 100% CPU usage (or 100% of single core on dual core) the Sys Mon Processes tab does not show IP Blocker (or anything) as utilising high CPU. CPU usage increases to 100% when IP Blocker is started (even in the short moments before the UI is even displayed), remains at 100% even when set to Disabled, and then as soon as the IP Blocker UI is closed the CPU returns to normal (low CPU usage). 

Following suggestion made in another post I tried

sudo aptitude install sun-java6-jre
sudo update-alternatives --config java

For the second command it said there are 2 alternatives which provide 'java'.
1 java-6-cacao 
2 java-6-sun

cacao was the default.
I selected 2 to make java-6-sun the default.

hey presto, both machines fixed, CPU usage now normal

Thanks uljanow

---

### Post by Stoptheglaciers on 2009-03-13
I haven't had a chance to read through all the posts so sorry if this question has already been answered.

Will this ipblocker function properly without previously setting up a firewall program? From reading the first post in the HOWTO it makes it seem like IPblock is more or less an extention of the functions of a firewall application, such as firestarter.

Thanks

---

### Post by uljanow on 2009-03-14
IPblock/iplist don't require other firewall programs, except iptables. There's no need to set up other applications in order to use IPblock.

Firestarter is just a front-end for iptables. IPblock however is a front-end for iplist which is a plugin for an iptables extension.

---

### Post by starslights on 2009-03-17
hello,

i have unbutu hardy 8.04 and iplist 0.25 are installed and can update list and load it well ..

The problem no ip appare on the log and see nothing write in , like activity ect... so i don't know why are like this...

No message error appare too.. enybody have a idea plaese ?

I am new in unbutu but have help to install it ...

thanks in advance for help  :D

my best

---

### Post by ssc351 on 2009-03-20
Hey Guys,

Having some problems getting it updated and enabled...

Here is the ouputs:
+ set -e
+ set -u
+ PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin
+ VERSION=0.25
+ QUEUE=0xff
+ QUEUE_INPUT=0xfd
+ QUEUE_OUTPUT=0xfe
+ QUEUE_FORWARD=0xff
+ POLICY=REPEAT
+ POLICY_MARK=0xfffe
+ BLOCK_TARGET=REPEAT
+ BLOCK_TARGET_INPUT=DROP
+ BLOCK_TARGET_OUTPUT=REPEAT
+ BLOCK_TARGET_FORWARD=REPEAT
+ BLOCK_TARGET_MARK=0xffff
+ NICE=-5
+ NEW=-m state --state NEW
+ GUI_LOG_FILE=/tmp/ipblockUI.log
+ [ -f /etc/ipblock.conf ]
+ . /etc/ipblock.conf
+ AUTOSTART=Yes
+ IPTABLES_CHAIN_BLOCK=INPUT OUTPUT 
+ IPTABLES_CHAIN_ALLOW=INPUT OUTPUT
+ LESS_MEMORY=No
+ BLOCK_LIST=ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz china.p2p.gz usa.p2p.gz dshield.gz level1.gz 
+ BLOCK_LIST_INPUT=
+ BLOCK_LIST_OUTPUT=
+ BLOCK_LIST_FORWARD=
+ ALLOW_LIST=
+ ALLOW_LIST_INPUT=allow-perm.p2p allow-temp.p2p
+ ALLOW_LIST_OUTPUT=allow-perm.p2p allow-temp.p2p
+ ALLOW_LIST_FORWARD=
+ IGN_TCP_INPUT=
+ IGN_UDP_INPUT=
+ IGN_TCP_OUTPUT=ftp https pop3 ssh 9001 
+ IGN_UDP_OUTPUT=domain ntp
+ IGN_TCP_FORWARD=
+ IGN_UDP_FORWARD=
+ IGN_PROTO_INPUT=
+ IGN_PROTO_OUTPUT=
+ IGN_PROTO_FORWARD=
+ IPLIST_LISTDIR=/var/cache/iplist
+ LOG_FILE=/tmp/ipblock.log
+ LOG_LEVEL=match
+ LOG_IPTABLES=No
+ VERBOSE=Yes
+ URL_FILE=/etc/ipblock.lists
+ UPDATE_STAMP=/var/cache/iplist/.update-stamp
+ UPDATE_INTERVAL=1
+ http_proxy=127.0.0.1:8118
+ GUI_START_HIDDEN=No
+ GUI_LAST_LOG_LINES=10
+ GUI_AUTOSCROLL=Yes
+ GUI_THEME=Gtk
+ GUI_WHITELIST_PERM=/var/cache/iplist/allow-perm.p2p
+ GUI_WHITELIST_TEMP=/var/cache/iplist/allow-temp.p2p
+ export IPLIST_LISTDIR
+ export http_proxy
+ id -u
+ [ 0 != 0 ]
+ [ 1 -ne 0 ]
+ LOG_IPTABLES=0
+ VERBOSE=-v
+ getopts sdripucglvh opt
+ do_start
+ is_running
+ local ret=0
+ iptables -L+ grep -E _MATCH|_QUEUE
 -n
+ pkill -SIGUSR1 iplist
+ return 0
+ trap on_start_failure INT TERM EXIT
+ start_iplist
+ nice -n -5 iplist --daemon -v -f /tmp/ipblock.log -l match
+ sleep 1
+ eval echo $BLOCK_TARGET_INPUT
+ echo DROP
+ eval echo $QUEUE_INPUT
+ echo 0xfd
+ eval echo $BLOCK_LIST_INPUT
+ echo
+ iplist -i -p REPEAT -P 0xfffe -t DROP -T 0xffff -n 0xfd ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz china.p2p.gz usa.p2p.gz dshield.gz level1.gz
iplist[26709]: error: can't find ads-trackers-and-bad-pr0n.gz
+ on_start_failure
+ logger -s -t ipblock[26692] error: failed to start, cleaning up
ipblock[26692]: error: failed to start, cleaning up
+ do_stop
+ is_running
+ local ret=0
+ iptables -L -n
+ grep -E _MATCH|_QUEUE
+ pkill -SIGUSR1 iplist
+ ret=3
+ return 3
+ stop_iplist
+ iplist -k

$sudo ipblock -sl
iplist[26772]: error: can't find ads-trackers-and-bad-pr0n.gz
ipblock[26755]: error: failed to start, cleaning up

I am running Jaunty 64bit.

---

### Post by uljanow on 2009-03-20
> **ssc351 said:**
> Hey Guys,

Having some problems getting it updated and enabled...

$sudo ipblock -sl
iplist[26772]: error: can't find ads-trackers-and-bad-pr0n.gz
ipblock[26755]: error: failed to start, cleaning up

I am running Jaunty 64bit.

There is a file missing. Try an update with "sudo ipblock -u" before starting.

---

### Post by starslights on 2009-03-21
hello,

And for my problem , nobody have a idea`?

I have just nothing in log and i see no ip bloqued or no bloqued

The update and program run , only that are strange..

Unbutu hardy 8.04 and iplist 0.25 

thanks in advance for help 

When need info need ask me while i don't know linux

---

### Post by uljanow on 2009-03-21
> **starslights said:**
> hello,

And for my problem , nobody have a idea`?

I have just nothing in log and i see no ip bloqued or no bloqued

The update and program run , only that are strange..

Unbutu hardy 8.04 and iplist 0.25 

thanks in advance for help 

When need info need ask me while i don't know linux

If it starts without an error message it should work. You could test it with an ip range that is in one of the lists. E.g. if you use level1.gz try "ping 3.0.0.0".

---

### Post by starslights on 2009-03-21
i don't know how test your ping but are this config right?

i use port 22 for FTP and nx client 

[IMG]http://www.lookpic.com/files/iplist.jpg[/IMG]

thanks in advance

ps: that's block site web and utorrent when i don't open port and cut my connection nx too when not config so you have sure right work but cannot sure while i see nothing to say it scan ip..

AFTER 20 or 30 min that's make the serveur crash and it restart ....

---

### Post by jsnelli2 on 2009-03-21
Great program, I've having one problem though.  I am unable to retrieve my university email.  I have added smtp to both ingoing and outgoing ignored tcp ports which stopped me from getting the error.  I am able to send email it appears, but I cannot retrieve it.  When I go to the university's website I am unable to see the button for the webbased login and if I attempt to go directly to the url of it it will not let me.

Along with the email login it is preventing me from seeing any of the search functions on the webpage.  This does not effect other web based mail such as yahoo.  Any ideas?

---

### Post by ssc351 on 2009-03-21
> **uljanow said:**
> There is a file missing. Try an update with "sudo ipblock -u" before starting.


Ya that is the other problem...I can't update the ipblocker or enable it.

---

### Post by starslights on 2009-03-22
i have find the error .that's with iptables...

I have nothing special config only the 3 basic rules ..

can somebody told me step by step how coonfig it? i have not enough knowleadge for that .

thanks in advance

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            MARK match 0xffff 
INPUT_QUEUE  all  --  anywhere             anywhere            state NEW MARK match !0xfffe 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            MARK match 0xffff 
OUTPUT_QUEUE  all  --  anywhere             anywhere            state NEW MARK match !0xfffe 

Chain ALLOW_MATCH (4 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain BLOCK_MATCH (2 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain INPUT_QUEUE (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ssh 
RETURN     udp  --  anywhere             anywhere            udp dpt:ssh 
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range -----------
ALLOW_MATCH  all  --  anywhere             anywhere            source IP range ------------
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 253

Chain OUTPUT_QUEUE (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ftp 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ssh 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:ssh 
RETURN     udp  --  anywhere             anywhere            udp dpt:domain 
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range ----------------------
ALLOW_MATCH  all  --  anywhere             anywhere            destination IP range ---------------------
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 254


error in log:

Mar 22 12:30:47 ns364846 iplist[26843]: info: Terminated signal caught 
Mar 22 12:31:39 ns364846 iplist[27068]: thread[3082017680]: error: can't bind nf_queue handler 
Mar 22 12:31:44 ns364846 iplist[27068]: thread[3062889360]: error: can't bind nf_queue handler 
Mar 22 14:28:06 ns364846 iplist[439]: thread[3083066256]: error: can't bind nf_queue handler 
Mar 22 14:28:11 ns364846 iplist[439]: thread[3082013584]: error: can't bind nf_queue handler


it ask for that too: iptables v1.3.8: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

---

### Post by uljanow on 2009-03-22
> **starslights said:**
> i have find the error .that's with iptables...

I have nothing special config only the 3 basic rules ..

can somebody told me step by step how coonfig it? i have not enough knowleadge for that .


it ask for that too: iptables v1.3.8: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps **iptables or your kernel needs to be upgraded**.

Have you tried using a ubuntu kernel ? It looks like your current kernel is missing some modules.

---

### Post by cashtr on 2009-03-25
Hi,
I installed the iplist, and it seems to be working from the command line (only indication is that cpu is active when I start it), although I still can connect to mpaa.org etc. but I thought this might be because http is allowed or stg. Anyway my problem is that I cannot start the gui version. I already tried iplist -g from the command line with no luck. any suggestions?

---

### Post by uljanow on 2009-03-26
To start the GUI use "sudo ipblock -g". What does the logfile **/tmp/ipblockUI.log** say after starting the GUI ?

---

### Post by starslights on 2009-03-26
hello uljanow, i don't know how look for kernel, i am newbie in linux and a friend who know have take a look but don't find...

---

### Post by cashtr on 2009-03-26
> **uljanow said:**
> To start the GUI use "sudo ipblock -g". What does the logfile **/tmp/ipblockUI.log** say after starting the GUI ?
I guess it is the sun license thingy in your howto, but I do not know how to fix this, opening console part of it and so on. Here is the log file:

Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.EventQueue.invokeLater(EventQueue.java:957)
	at javax.swing.SwingUtilities.invokeLater(SwingUtilities.java:1289)
	at org.jdesktop.application.Application.launch(Application.java:181)
	at ipblockui.IpblockUIApp.main(Unknown Source)

---

### Post by uljanow on 2009-03-27
> **cashtr said:**
> I guess it is the sun license thingy in your howto, but I do not know how to fix this, opening console part of it and so on. Here is the log file:

I'd suggest to install sun's vm and set it as default.
```

sudo aptitude install sun-java6-jre
sudo update-alternatives --config java

```

---

### Post by [slash]root on 2009-03-27
Thanks, work perfectly.

Anyone need help with [Java Runtime](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)?

EDIT: There's a [tutorial](http://ubuntuforums.org/showthread.php?t=76702) on this forum too

---

### Post by xxacidmv on 2009-04-04
This program is exactly what I was looking for.  It works great and is easy to use.  Thank you

---

### Post by spacegypsy on 2009-04-05
Thanks a lot.
Indeed the easiest peerguardian alternative for Linux.

Great.:popcorn:

---

### Post by BB88 on 2009-04-26
Fantastic, just what I needed for my Migration on to Jaunty from Vista! :D

---

### Post by uljanow on 2009-05-01
A new version is out which consists of small bug-fixes and enhancements.
Most important changes are better KDE support and the removal of
dependencies of desktop-environments. As a result iplist can be
installed on a headless server without X or if iplist is installed on a
KDE-based system it doesn't require any gnome-related packages or extra
modifications.

> 
Changelog:
* release (0.26)
* fixed broken LESS_MEMORY option
* fixed regex bug (2683790) due to latest grep 2.5.4
* fixed if-up script warning due to exit code
* fixed autostart bug in ubuntu jaunty
* added theme option to GUI
* improved kde support
* added generic su-to-root wrapper to ipblock
* removed dependencies on desktop-environments

---

### Post by kb3hkg on 2009-05-01
I had used an old version of this program about a year ago and it worked great. Now that I have Jaunty installed I am working on upgrading.

---

### Post by k3ntegra on 2009-05-01
How do i minimize ipblock (latest version) to the task bar, like deluge rhythm box and many other programs?

---

### Post by uljanow on 2009-05-01
The status icon has a context menuitem "Hide".

---

### Post by k3ntegra on 2009-05-01
> **uljanow said:**
> The status icon has a context menuitem "Hide".

Yeah, unfortunately the status icon refuses to come up at the panel when  iplist opens. Other programs status panel comes up though. It was able to come up though when i ran it in opensuse

---

### Post by uljanow on 2009-05-02
You could try sun-java6-jre. Other VMs seem to have problems with compiz and the status icon.
```

sudo aptitude install sun-java6-jre
sudo update-alternatives --config java
```

---

### Post by k3ntegra on 2009-05-02
> **uljanow said:**
> You could try sun-java6-jre. Other VMs seem to have problems with compiz and the status icon.
```

sudo aptitude install sun-java6-jre
sudo update-alternatives --config java
```

i typed "sudo aptitude install sun-java6-jre"

and eventually got the following

> 
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                    

i dont know how to ok this

[http://img.photobucket.com/albums/v488/K3N_Shady/javaproblem.png](http://img.photobucket.com/albums/v488/K3N_Shady/javaproblem.png)

---

### Post by k3ntegra on 2009-05-02
I tried installing java manually

and got 
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I typed sudo dpkg --configure -a in the terminal, and typed my password and got the message

dpkg: status database area is locked by another process

When i type, ps ax | grep dpkg , i get 

> k3ntegra@venom-dtop:~$ ps ax | grep dpkg
 4297 pts/1    Ss+    0:00 /usr/bin/dpkg --status-fd 36 --unpack --auto-deconfigure /var/cache/apt/archives/odbcinst1debian1_2.2.11-16build3_amd64.deb /var/cache/apt/archives/unixodbc_2.2.11-16build3_amd64.deb /var/cache/apt/archives/sun-java6-bin_6-13-1_amd64.deb /var/cache/apt/archives/sun-java6-jre_6-13-1_all.deb /var/cache/apt/archives/gsfonts-x11_0.21_all.deb
 4324 pts/1    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst install
 4330 pts/1    S+     0:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst install
 6201 pts/2    R+     0:00 grep dpkg
k3ntegra@venom-dtop:~$ 


---

### Post by uljanow on 2009-05-02
You can navigate with the tab-key until the "OK" is selected and press enter. If you have closed the terminal and can't find that dialog window, try to kill dpkg and restart.

> sudo killall dpkg
sudo killall aptitude
sudo aptitude install sun-java6-jre
sudo update-alternatives --config java

---

### Post by k3ntegra on 2009-05-02
> **uljanow said:**
> You can navigate with the tab-key until the "OK" is selected and press enter. If you have closed the terminal and can't find that dialog window, try to kill dpkg and restart.

i checked add/remove and looks like java is installed now

i ran the rest of the lines and got these

> k3ntegra@venom-dtop:~$ sudo killall dpkg
[sudo] password for k3ntegra: 
dpkg: no process killed
k3ntegra@venom-dtop:~$ sudo update-alternatives --config java 

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.
k3ntegra@venom-dtop:~$ 

I then ran ipblock and it still refuses to come up at the status panel

---

### Post by uljanow on 2009-05-03
> There is only 1 program which provides javaThat means sun-java6-jre wasn't installed.

---

### Post by rock4christ on 2009-05-08
Is it just me, or is bluetack.co.uk/config/level1.gz down?( along with bluetack.co.uk/config/level1.zip and bluetack.co.uk/config/proxy.zip)

---

### Post by warchief_ryan on 2009-05-11
How much less memory does the LESS_MEMORY option use?


Also I don't know why you guys are messing around with java unless you just must have a gui, I prefer to just remove it from the dependinces before compiling.

---

### Post by uljanow on 2009-05-12
> **warchief_ryan said:**
> How much less memory does the LESS_MEMORY option use?

That depends on the configuration. If LESS_MEMORY is not set iplist creates one queue for each chain (in, out, fwd) that is used. That has some advantages: dropping incoming packets (instead of rejecting), specifying lists for specific chains only,  increased performance (multi-threaded design), ... . Disadvantages are, it takes longer to load lists and an increased memory usage (~10-20 MB). Unless you have limited RAM I wouldn't recommend using the option.

---

### Post by miljo123 on 2009-05-12
iplist allows users with no or basic knowledge of iptables to filter (e.g. to block) network traffic based on (automatically updated) lists. These lists have various formats and are sorted by different categories (e.g. countries, adware, corporations).

---

### Post by uljanow on 2009-05-15
I've just uploaded **Tor** (stable 0.2.0.34) to the ppa repository because it's missing in Ubuntu 9.04 Jaunty. It's the same version as the one from debian/tor project.

---

### Post by khaos28 on 2009-05-18
whats the sudo code for un-installation?

---

### Post by Josephxfs on 2009-07-09
for some reason in the programs tray icon it shows a lower number of ip ranges than the lists I loaded have(and I know there should be more ip ranges) is this simply a GUI glitch or am I not receiving protection from certain ip ranges because the program has a default limit???

---

### Post by uljanow on 2009-07-09
iplist automatically merges ranges. If you set the verbose option your logs /var/log/syslog should contain lines like "iplist[XX]: info: 12396 ip ranges inserted". However it will not give a notice if a range is merged. The number of IP ranges doesn't say how many IPs are actually blocked.

---

### Post by alphaniner on 2009-07-31
Where can I get a description of the various lists, ie. what their intention is, broadly speaking?  Such as:

bogon
dshield
iana*
level*
nipfilter
pipfilter

---

### Post by uljanow on 2009-08-01
> Where can I get a description of the various lists, ie. what their intention is, broadly speaking? Such as:

Bluetack has a nice [faq]("http://blocklistpro.com/faqs/biss-ip-blocklists-faq.html").

---

### Post by richierich1986 on 2009-08-12
when ubuntu starts, iplist is running, but when i start ipblock gui, it shows it's disabled... :s

running "ps aux | grep ipblock" both in user and root shows iplist IS running, but the gui shows it is NOT enabled..

please help me out here?

---

### Post by uljanow on 2009-08-12
Have you installed other firewall applications ? Probably another app is removing the iptables rules inserted by ipblock.

ipblock needs to be started after other firewall application. Normally it's compatible with ufw, shorewall, etc. which start at runlevel < 99.

---

### Post by richierich1986 on 2009-08-13
I actually solved this already... although I have no clue as to what it is I've done to solve it. I was fooling around a bit and apparently somewhere along the way I've done something to make things work proper! 

Thanks anyway for the reply  ;)

---

### Post by jre on 2009-08-14
If it is a firewall (most times it is ufw) this problem will arise again, whenever you change settings in ufw, because ufw will then purge iplists iptables rules.

---

### Post by alphaniner on 2009-08-19
> **uljanow said:**
> Bluetack has a nice [faq]("http://blocklistpro.com/faqs/biss-ip-blocklists-faq.html").

Thank you.

---

### Post by kozimodo on 2009-08-26
I'm not sure what the problem is but I can no longer get ipblock to work.  It's been a while since I've used it so I'm not sure what change in my system caused it.  Basically if I start ipblock ("sudo ipblock -g") nothing happens.  It doesn't give me anything.  No error messages, nothing in the syslog, nothing.  I'm at a loss. :confused:

---

### Post by uljanow on 2009-08-26
What does the logfile **/tmp/ipblockUI.log** say if you try to open the GUI with "sudo ipblock -g" ?

---

### Post by kozimodo on 2009-08-26
Here is the ipblockUI.log file:
```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

---

### Post by uljanow on 2009-08-26
The gui requires java-1.6. Can you change your default java vm (to openjdk6 or sun-java6-jre)?

```
sudo update-alternatives --config java
```

---

### Post by kozimodo on 2009-08-26
Thanks! ipblock works again!

---

### Post by mistypotato on 2009-09-02
With IPBlock, can I use CDIR notation in a custom created list?

I tried it and it does not seem to work.

Instead, it seems to only accept ranges in this format.....

[SIZE="4"]xxx.xxx.xxx.xxx[COLOR="Red"]-[/COLOR]xxx.xxx.xxx.xxx[/SIZE]

---

### Post by uljanow on 2009-09-02
CDIR notation is not supported (only dat, p2p and a binary format). If you try to load an unknown list format, a log message should appear.
```
grep -r iplist /var/log/syslog*
```

---

### Post by SanjoEel on 2009-09-11
Thanks for the walk through! IPBlock is great.

---

### Post by Bloemetjesgordijn on 2009-09-19
hi guys,

I wanted to use IPblock but the fonts are way to small (unreadable).

Can someone help me to changes this.

[IMG][[IMG]http://img41.imageshack.us/img41/8317/ipblock.th.png[/IMG]](http://img41.imageshack.us/i/ipblock.png/)[/IMG]

Thx

Bloemetjesgordijn

---

### Post by alibabajr on 2009-09-19
Thanks, works great. Block all the fake emule server and many more.

---

### Post by Shujah on 2009-09-21
Excellent app, worked flawlessly on jaunty. One small irritation is that closing the windows [via x in titlebar] closes the application when it should hide it.

---

### Post by cbugsubunt on 2009-09-22
great app and easy

---

### Post by Cypher1101 on 2009-09-27
I tried to add one of TBG's blocklists and it didn't seem to add anything to the list of ranges blocked. Is Ipblock incompatible with tbg's lists? (tbg.iblocklist.com)

Is there a way i can check what what ranges are added by each list loaded?

update: I noticed that the gz was being downloaded and stored in the cache folder, but not being loaded properly. So I opened up my lists file and deleted the URL I had added with the gui. Just out of curiousity, I imported the URL one more time and it went through perfectly. The extra ranges show up as expected now. How strange.

I really like the prog BTW

---

### Post by bark50 on 2009-09-29
I lost my Ipblock!  It had been working faultlessly.  Now when I try to start it, after entering my password, nothing happens.  I've uninstalled and reinstalled, and this didn't help.  I first noticed the problem right after installing some recent Ubuntu updates that required a restart of my computer, but that wouldn't have anything to do with the problem, would it?  Any help getting Ipblock back would be greatly appreciated.

Edit:  Problem solved.  I ran sudo update-alternatives --config java and changed from jvm/java-gcj to jvm/java-6-sun and now IPblock works fine.  If I'm possibly screwing something else up in my system by having done this, someone please let me know.  Otherwise, I'm happy!

This is a great program.  Thanks to uljanow.

---

### Post by uljanow on 2009-10-09
A new version 0.27 is available.

> * release (0.27)
* improved performace of list routines
* fixed theme of context menu in whitelist manager
* improved status check routines
* changed UI to include a log-level combobox
* added info dialog if log entry is double-clicked
* replaced tail dependency
* removed GUI_LAST_LOG_LINES option

---

### Post by gyebro on 2009-10-17
I'd like to ignore a port range(both tcp and udp) in ipblock that Steam uses (tcp: 27020-27039, udp:27000-27015). Is there a way setting a whole range of ports in ipblock gui, or do I have to enter every single port from 27020 to 27039?
Thanks for your reply.

---

### Post by uljanow on 2009-10-17
> **gyebro said:**
> I'd like to ignore a port range(both tcp and udp) in ipblock that Steam uses (tcp: 27020-27039, udp:27000-27015). Is there a way setting a whole range of ports in ipblock gui, or do I have to enter every single port from 27020 to 27039?
Thanks for your reply.

[http://iplist.sourceforge.net/faq.html#0x0c](http://iplist.sourceforge.net/faq.html#0x0c)

---

### Post by matyasfalvi on 2009-11-01
Thanx for the awesome app. It works great!

Btw does anyone know a place where this whole thing is explained, how it works, how to interpret the output and things like that. 

Thanx

---

### Post by uljanow on 2009-11-01
> **matyasfalvi said:**
> Thanx for the awesome app. It works great!

Btw does anyone know a place where this whole thing is explained, how it works, how to interpret the output and things like that. 

Thanx

Thanks. 

There isn't any comprehensive technical documentation. [Here]("http://iplist.sourceforge.net/documentation.html") (bottom of page) is a short explanation how iplist works. To interpret the log window basic network knowledge is needed like IPs, Protocols, network layers, etc. But that's beyond the scope of the documentation for iplist/ipblock. If you need a bittorrent guide, check out [this]("http://ubuntuforums.org/showthread.php?t=1259923").

---

### Post by Paul86fxr on 2009-11-06
Excellent job, well done. I appreciate the tutoral:KS

---

### Post by matyasfalvi on 2009-11-06
Thanx a lot!

---

### Post by chewearn on 2009-12-28
I have been getting a weird problem.

Every other day after iplist auto-updated the block lists, my bittorrent connections got "clogged up" (sorry, but I couldn't think of a better term to describe it).  Basically, the download speeds are slow, DHT is disconnected, and not able to connect to some trackers.

If I restart iplist (sudo ipblock -r), everything is back to normal.

This is on Ubuntu Intrepid x64.

Any idea?  In the short term, I am thinking of working around this problem by adding a mandatory restart command into the ipblock cron.

---

### Post by uljanow on 2009-12-28
The cron script updates lists and only restarts iplist. During the restart all new connections are blocked. I don't know if bittorrent uses a persistent or new connection for every chunk. If it's the latter case it can cause a performance decrease.


If you make a restart (-r), ipblock does not filter for a few seconds. Therefore I would suggest to just forbid restarting by changing the line

ipblock is_running || PARAM="-up"
to
ipblock is_running || PARAM="-u"
in **/etc/cron.daily/ipblock**

I'm assuming you don't have weeks of uptime. ;)

---

### Post by chewearn on 2009-12-28
> **uljanow said:**
> The cron script updates lists and only restarts iplist. During the restart all new connections are blocked. I don't know if bittorrent uses a persistent or new connection for every chunk. If it's the latter case it can cause a performance decrease.

Thanks for the clarification.

The problem was, the clogged up state persisted indefinitely.  To be more precise, I usually checked a few hours later in the day and found it has not been working properly since it updated in the morning.

It would appear that connections that have been opened before the update continued to function (account for non-zero download/upload speed), but no new connections could be made since.

> If you make a restart (-r), ipblock does not filter for a few seconds. Therefore I would suggest to just forbid restarting by changing the line

ipblock is_running || PARAM="-up"
to
ipblock is_running || PARAM="-u"
in **/etc/cron.daily/ipblock**
I am not sure if this will work, because prior to last week, I kept the ipblock GUI opened all the time.  That was when I first noticed this problem.  The cron script said that if the GUI is opened, it update without restart?

Then, I thought if I don't keep the GUI opened, the problem might be resolved with the restart, but it didn't.

> I'm assuming you don't have weeks of uptime. ;)In the past, I have an extremely stable Gutsy box, which ran a personal record of 200+ days uptime :P.  But six months after Gutsy EOL, I took it upon myself to fresh install Jaunty.  Unfortunately, the PC go completely dead a day later.  Totally dead, not even showing the BIOS POST screen.  An Evil Jackalope has killed my PC!  But I can't full proof it! :x

Now, I ran ipblock + bittorrent on another an Intrepid PC.  I am no longer able to achieve more than a few days of uptime because of various reasons.

--

Anyway, thanks again.  I will have to think about whether I could risk a few seconds of gap every two days; or I might make a custom script to shutdown bittorrent during the gap.

---

### Post by bark50 on 2010-02-03
For the past 5 days (at least 5 days), I've been getting error messages when trying to update the standard lists.  The messages are:  "error: update of (level1.gz, ads-trackers-and-bad-pr0n.gz, etc.) failed".  Should I just be patient and keep trying every day?  Or do I need to do something else?  Thanks!


Update:  Doing a Google search, I found this for bluetack.co.uk:  We estimate around the 1st of Feburary that the Bluetack site will be taken offline, and could be offline for at least 1 -2 weeks. ...

Does anyone have any recommendations for comparable lists from other websites?

---

### Post by FooAtari on 2010-02-06
> **bark50 said:**
> For the past 5 days (at least 5 days), I've been getting error messages when trying to update the standard lists.  The messages are:  "error: update of (level1.gz, ads-trackers-and-bad-pr0n.gz, etc.) failed".  Should I just be patient and keep trying every day?  Or do I need to do something else?  Thanks!


Update:  Doing a Google search, I found this for bluetack.co.uk:  We estimate around the 1st of Feburary that the Bluetack site will be taken offline, and could be offline for at least 1 -2 weeks. ...

Does anyone have any recommendations for comparable lists from other websites?

So thats the problem! Just have to wait it out I guess...

---

### Post by Redsandro on 2010-03-06
One cannot start the app when user is not a sudo'er.
Can I make it autostart for a non-sudoer?

I have a safe user for guest usage and I want to block any and all advertiser and tracker crap. But I don't want to make that user sudo'er.

---

### Post by uljanow on 2010-03-06
If you enable autostart it will filter all connections systemwide. The GUI however doesn't need to run at all. But it requires root rights.

---

### Post by Redsandro on 2010-03-06
Ah thanks. Yeah I see it running in top. I needed to reboot. Now a lot of advertisements are blocked! I kind of miss some of them. ;)

---

### Post by uljanow on 2010-03-10
A new version is out:
>         * release (0.28 )
        * fixed debian ifup script
        * added GUI watchdog
        * Improved GUI log routines
        * Reduced GUI memory usage
        * added IP counter
        * improved reload behaviour of list manager

---

### Post by FooAtari on 2010-03-11
Improved GUI and Memory useage, sounds good. Shall check it out tonight.

---

### Post by chewearn on 2010-03-11
I updated to the new version today, and encountered a problem: iplist failed to start on every boot.  I have to enable it manually every time.

Error message in syslog:
```
Mar 11 xx:xx:xx user-desktop ipblock[5897]: error: failed to start, cleaning up
```

---

### Post by uljanow on 2010-03-11
> **chewearn said:**
> I updated to the new version today, and encountered a problem: iplist failed to start on every boot.  I have to enable it manually every time.

Error message in syslog:
```
Mar 11 xx:xx:xx user-desktop ipblock[5897]: error: failed to start, cleaning up
```

Which distro are you using ?

---

### Post by chewearn on 2010-03-11
> **uljanow said:**
> Which distro are you using ?

I am using Ubuntu Intrepid 8.10 (desktop 64-bit).

---

### Post by A-DavRoyShi-X on 2010-04-30
Using Ubuntu Netbook Edition 10.04

Problem is that it's always disabled (with a blank white window), no matter how I install it. Even tried lenny-support, but that didn't make any visible difference. Also followed your instructions multiple times, but it's still the same.

Tried on both Wired and Wireless. Using Acer [IMG]http://ubuntuforums.org/data:image/x-icon;base64,AAABAAEAEBAQAAAAAAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAACAAACAAAAAgIAAgAAAAIAAgACAgAAAwMDAAICAgAAAAP8AAP8AAAD//wD/AAAA/wD/AP//AAD///8AAAAAAAAAAAAAAAAAEQAAAAAAAACZAAAAAAAAABkAAAAAAAAAGREQAAAAAAAZmZkAAAAAAAkQAAABAAABCZERAAmQABkBmZkQAZEZkQAAAAAAGZGRAAAAAAAJEJEAAAAAAAGRkQAAAAAAAJmQAAAAAAAAGZAAAAAAAAABEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA[/IMG][IMG]http://ubuntuforums.org/data:image/x-icon;base64,R0lGODlhEAAQANUAAB53rjOPx7u7uziUzcbe7cfg7mmt1mGkzYi/4eTx+MTc61aXv8HZ6ERERF6gyGao0snh8FqbxN3d3cPb6RhxqC6JwSN9tCiDuyIiIkak3kOh2wphlw5mnAZdkkCd1xNrojyZ0gNZjgAAAP///wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAAAAAAALAAAAAAQABAAAAZtwJFwKMwYj0YiUcNsMpVDj3QqhQpB2CxWiBF5G6MBgpgYcAXEgNoAUQfOxIr8UZBXuF6RZHTpHwh9F3BDFoUOCoUWg0IAjRETjQCLIxSVCwyVFFYjH52enZscoqOimxunqKebHaytrJshsbKxQQA7[/IMG][IMG]http://ubuntuforums.org/data:image/x-icon;base64,AAABAAEAEBAQAAAAAAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD///8A9///AMbv/wCt7/8AhOf/AFLW/wAxzv8A5/f3AJTe7wB71u8Azt7nAFK93gA5tdYAQq3GAEKctQAAAAAA3duImLuivc3GZXcHAAlma9ZmZmZoBWZsxmZmQiB2ZmzVQ3AHgwZmbNAHOWaSAmZr1VZmQgIgRmzWZkICWAICXdZSB1YgSQAAsgdWUglgJlunlmUAViBmbNZmaSZmJGZr1mZmZmZmZmzWZmZmZmZmbMZmZmZmZmZs7dzdzdzdzd0AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA[/IMG][IMG]http://ubuntuforums.org/data:image/x-icon;base64,AAABAAEAEBAQAAEABAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAEAgQAhIOEAMjHyABIR0gA6ejpAGlqaQCpqKkAKCgoAPz9%2FAAZGBkAmJiYANjZ2ABXWFcAent6ALm6uQA8OjwAiIiIiIiIiIiIiI4oiL6IiIiIgzuIV4iIiIhndo53KIiIiB%2FWvXoYiIiIfEZfWBSIiIEGi%2FfoqoiIgzuL84i9iIjpGIoMiEHoiMkos3FojmiLlUipYliEWIF%2BiDe0GoRa7D6GPbjcu1yIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA[/IMG]Aspire One (model ZG5).

---

### Post by A-DavRoyShi-X on 2010-04-30
> **A-DavRoyShi-X said:**
> Using Ubuntu Netbook Edition 10.04

Problem is that it's always disabled (with a blank white window), no matter how I install it. Even tried lenny-support, but that didn't make any visible difference. Also followed your instructions multiple times, but it's still the same.

Tried on both Wired and Wireless. Using Acer [IMG]http://ubuntuforums.org/data:image/x-icon;base64,AAABAAEAEBAQAAAAAAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAACAAACAAAAAgIAAgAAAAIAAgACAgAAAwMDAAICAgAAAAP8AAP8AAAD//wD/AAAA/wD/AP//AAD///8AAAAAAAAAAAAAAAAAEQAAAAAAAACZAAAAAAAAABkAAAAAAAAAGREQAAAAAAAZmZkAAAAAAAkQAAABAAABCZERAAmQABkBmZkQAZEZkQAAAAAAGZGRAAAAAAAJEJEAAAAAAAGRkQAAAAAAAJmQAAAAAAAAGZAAAAAAAAABEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA[/IMG][IMG]http://ubuntuforums.org/data:image/x-icon;base64,R0lGODlhEAAQANUAAB53rjOPx7u7uziUzcbe7cfg7mmt1mGkzYi/4eTx+MTc61aXv8HZ6ERERF6gyGao0snh8FqbxN3d3cPb6RhxqC6JwSN9tCiDuyIiIkak3kOh2wphlw5mnAZdkkCd1xNrojyZ0gNZjgAAAP///wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAAAAAAALAAAAAAQABAAAAZtwJFwKMwYj0YiUcNsMpVDj3QqhQpB2CxWiBF5G6MBgpgYcAXEgNoAUQfOxIr8UZBXuF6RZHTpHwh9F3BDFoUOCoUWg0IAjRETjQCLIxSVCwyVFFYjH52enZscoqOimxunqKebHaytrJshsbKxQQA7[/IMG][IMG]http://ubuntuforums.org/data:image/x-icon;base64,AAABAAEAEBAQAAAAAAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD///8A9///AMbv/wCt7/8AhOf/AFLW/wAxzv8A5/f3AJTe7wB71u8Azt7nAFK93gA5tdYAQq3GAEKctQAAAAAA3duImLuivc3GZXcHAAlma9ZmZmZoBWZsxmZmQiB2ZmzVQ3AHgwZmbNAHOWaSAmZr1VZmQgIgRmzWZkICWAICXdZSB1YgSQAAsgdWUglgJlunlmUAViBmbNZmaSZmJGZr1mZmZmZmZmzWZmZmZmZmbMZmZmZmZmZs7dzdzdzdzd0AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA[/IMG][IMG]http://ubuntuforums.org/data:image/x-icon;base64,AAABAAEAEBAQAAEABAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAEAgQAhIOEAMjHyABIR0gA6ejpAGlqaQCpqKkAKCgoAPz9%2FAAZGBkAmJiYANjZ2ABXWFcAent6ALm6uQA8OjwAiIiIiIiIiIiIiI4oiL6IiIiIgzuIV4iIiIhndo53KIiIiB%2FWvXoYiIiIfEZfWBSIiIEGi%2FfoqoiIgzuL84i9iIjpGIoMiEHoiMkos3FojmiLlUipYliEWIF%2BiDe0GoRa7D6GPbjcu1yIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA[/IMG]Aspire One (model ZG5).
Actually, there's still a problem. It's still blank even after enabling it!

How do I know it's working? It does say "IPBlock - x-number IPs loaded" on the taskbar though.

---

### Post by A-DavRoyShi-X on 2010-05-01
> **A-DavRoyShi-X said:**
> Actually, there's still a problem. It's still blank even after enabling it!

How do I know it's working? It does say &quot;IPBlock - x-number IPs loaded&quot; on the taskbar though.

Everything working fine after reboot. Can see the GUI and log now. Maybe that should be included in the tutorial..

---

### Post by A-DavRoyShi-X on 2010-05-01
> **A-DavRoyShi-X said:**
> Everything working fine after reboot. Can see the GUI and log now. Maybe that should be included in the tutorial..

Okay, to ensure it will work without any problems, I have to disable it before exiting or shutting down. If I don't, it will likely become blank.

---

### Post by Tanner2007 on 2010-05-11
Can someone please help me, im a noob but this app keeps blocking google.com yahoo.com and etc how can i bypass this not to block these sites 

(soon as i disable it, sites work, once reabled, they blocked)

---

### Post by bark50 on 2010-05-11
> **Tanner2007 said:**
> Can someone please help me, im a noob but this app keeps blocking google.com yahoo.com and etc how can i bypass this not to block these sites 

(soon as i disable it, sites work, once reabled, they blocked)

Click on the "Network" tab and put a check mark in the box "HTTP".  Does that work?

---

### Post by pk_m on 2010-06-01
Nice one to gain knowledge for new users like me...

---

### Post by dino99 on 2010-06-24
hi,

using ipblock 0.28 on lucid and maverick 32 with sun-java6-jre, all gcj packages removed

i'm searching why the whitelist never remove the "temporary" ip, even after a reboot. I need to open the list and remove them one by one, there is no way to select all the temporary ip at once, strange.

so, how to modify the conf file to have the temporary ip removed automaticaly by default on shutdown or better when closing Firefox or any browser ? ( i hope a new gui could give the choice to set a expiration for temporary ips)

---

### Post by uljanow on 2010-06-25
> **dino99 said:**
> hi,

using ipblock 0.28 on lucid and maverick 32 with sun-java6-jre, all gcj packages removed

i'm searching why the whitelist never remove the "temporary" ip, even after a reboot. I need to open the list and remove them one by one, there is no way to select all the temporary ip at once, strange.

so, how to modify the conf file to have the temporary ip removed automaticaly by default on shutdown or better when closing Firefox or any browser ? ( i hope a new gui could give the choice to set a expiration for temporary ips)

How does your conf file look like ?

---

### Post by dino99 on 2010-06-25
thanks for your response, below ipblock.conf (/etc) (its the default maverick installation, where i've added lists)

AUTOSTART="Yes"
IPTABLES_CHAIN_BLOCK="INPUT OUTPUT "
IPTABLES_CHAIN_ALLOW="INPUT OUTPUT"
LESS_MEMORY="No"
BLOCK_LIST="level1.gz ads-trackers-and-bad-pr0n.gz edu.gz spyware.gz bogon.gz china.p2p.gz dshield.gz level3.gz level2.gz india.p2p.gz "
BLOCK_LIST_INPUT=""
BLOCK_LIST_OUTPUT=""
BLOCK_LIST_FORWARD=""
ALLOW_LIST=""
ALLOW_LIST_INPUT="allow-perm.p2p allow-temp.p2p"
ALLOW_LIST_OUTPUT="allow-perm.p2p allow-temp.p2p"
ALLOW_LIST_FORWARD=""
IGN_TCP_INPUT=""
IGN_UDP_INPUT=""
IGN_TCP_OUTPUT="https "
IGN_UDP_OUTPUT="domain ntp"
IGN_TCP_FORWARD=""
IGN_UDP_FORWARD=""
IGN_PROTO_INPUT=""
IGN_PROTO_OUTPUT=""
IGN_PROTO_FORWARD=""
IPLIST_LISTDIR="/var/cache/iplist"
LOG_FILE="/tmp/ipblock.log"
LOG_LEVEL="match"
LOG_IPTABLES="No"
VERBOSE="No"
URL_FILE="/etc/ipblock.lists"
UPDATE_STAMP="/var/cache/iplist/.update-stamp"
UPDATE_INTERVAL="1"
http_proxy=""
GUI_START_HIDDEN="Yes"
GUI_AUTOSCROLL="Yes"
GUI_THEME="Gtk"
GUI_WHITELIST_PERM="/var/cache/iplist/allow-perm.p2p"
GUI_WHITELIST_TEMP="/var/cache/iplist/allow-temp.p2p"

---

### Post by uljanow on 2010-06-26
The configuration looks ok. Normally temporary IPs are removed when the GUI exits. If that's not the case, there should be some entries in the GUI logfile **/tmp/ipblockUI.log**.

---

### Post by d3v1150m471c on 2010-06-26
you can do this with iptables as well. firestarter works just as well, perhaps better.

---

### Post by Lute on 2010-06-28
Hi, thanks for the tutorial. 

I removed the default lists and tried to put the ones from [http://tbg.iblocklist.com/]("http://tbg.iblocklist.com/") , cause bluetack didn't used to update much, but it didn't load any IP's. So I went with their ipfilter.dat.gz and I believe it works, says loaded bunch of ip's. 

So my question, is it ok what I did?, is the defaults better? if not, any other out there?

I would like support for upload whitelists, like for world of warcraft and other programs, but it works for now by adding 1 at a time to permanent.

Thanks in advance
Lute

---

### Post by jre on 2010-06-28
Please try the TBG blocklists with the links that you find here: [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)
You will get slightly other URLs then. Otherwise blocklist selection is a personal decision depending on your personal needs. I suggest you read the explanations on iblocklist.com. Be careful not to take too many lists.

---

### Post by TheDebianGuy on 2010-06-29
Hi, i did the commands but it doesn't appear under application->internet. Any tips?
Thanks.

---

### Post by Hakuna Matata on 2010-07-05
I have the same problem as TheDebianGuy, i did all the commands, but the iplist doesn't appear in application--->internet. Please help :KS

---

### Post by uljanow on 2010-07-06
> **Hakuna Matata said:**
> I have the same problem as TheDebianGuy, i did all the commands, but the iplist doesn't appear in application--->internet. Please help :KS
> Hi, i did the commands but it doesn't appear under application->internet. Any tips?
Thanks. 

The file **ipblock.desktop** should be located in **/usr/share/applications/**. Which distro version and desktop environment are you using ?

---

### Post by Cavsfan on 2010-07-12
This is nice, but it is keeping me from connecting to websites like adobe and netflix.
I entered "sudo aptitude purge iplists" and even rebooted, but it is still blocking websites.

I cannot find anything else to change.
Thanks

EDIT: I got it un-installed by reinstalling it via synaptic, un-installing it and then rebooting.
Thanks I am good now!

---

### Post by Veld on 2010-08-13
IPs in the lists are still being blocked even when not running the GUI or logged in the root account, right?

---

### Post by uljanow on 2010-08-14
> **Veld said:**
> IPs in the lists are still being blocked even when not running the GUI or logged in the root account, right?

Yes, given the fact that it has been enabled (by autostart or manually).

---

### Post by dino99 on 2010-08-21
new issue on maverick:

was working fine till yesterday August 20th, now i cant enable it

[https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/621636](https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/621636)

---

### Post by bark50 on 2010-08-21
> **dino99 said:**
> new issue on maverick:

was working fine till yesterday August 20th, now i cant enable it

[https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/621636](https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/621636)

I'm on lucid, kernel linux 2.6.32-24-generic-pae, and ipblock was working fine till now.  Now when I try to enable it, I get "iplist[2013]: error: no running iplist instance found" and "ipblock[1995]: error: failed to start up, cleaning up".  Putting egrep "iplist|ipblock" /var/log/syslog in the terminal gives:

tom@tom-desktop:~$ grep iplist /var/log/syslog*
/var/log/syslog:Aug 21 08:23:49 tom-desktop iplist[16488]: error: can't convert 192
/var/log/syslog:Aug 21 08:23:49 tom-desktop iplist[16499]: error: no running iplist instance found
/var/log/syslog:Aug 21 09:37:44 tom-desktop iplist[17020]: error: can't convert 192
/var/log/syslog:Aug 21 09:37:44 tom-desktop iplist[17031]: error: no running iplist instance found
/var/log/syslog:Aug 21 09:40:08 tom-desktop iplist[1865]: error: can't convert 192
/var/log/syslog:Aug 21 09:40:08 tom-desktop iplist[1876]: error: no running iplist instance found
/var/log/syslog:Aug 21 09:40:35 tom-desktop iplist[1904]: error: can't convert 192
/var/log/syslog:Aug 21 09:40:35 tom-desktop iplist[1915]: error: no running iplist instance found
/var/log/syslog:Aug 21 09:41:34 tom-desktop iplist[2002]: error: can't convert 192
/var/log/syslog:Aug 21 09:41:34 tom-desktop iplist[2013]: error: no running iplist instance found
/var/log/syslog.1:Aug 21 07:58:27 tom-desktop iplist[16195]: error: can't convert 192
/var/log/syslog.1:Aug 21 07:58:27 tom-desktop iplist[16206]: error: no running iplist instance found
tom@tom-desktop:~$ egrep "iplist|ipblock" /var/log/syslog
Aug 21 08:23:49 tom-desktop iplist[16488]: error: can't convert 192
Aug 21 08:23:49 tom-desktop iplist[16499]: error: no running iplist instance found
Aug 21 08:23:49 tom-desktop ipblock[16481]: error: failed to start, cleaning up
Aug 21 09:37:44 tom-desktop iplist[17020]: error: can't convert 192
Aug 21 09:37:44 tom-desktop iplist[17031]: error: no running iplist instance found
Aug 21 09:37:44 tom-desktop ipblock[17013]: error: failed to start, cleaning up
Aug 21 09:40:08 tom-desktop iplist[1865]: error: can't convert 192
Aug 21 09:40:08 tom-desktop iplist[1876]: error: no running iplist instance found
Aug 21 09:40:08 tom-desktop ipblock[1858]: error: failed to start, cleaning up
Aug 21 09:40:35 tom-desktop iplist[1904]: error: can't convert 192
Aug 21 09:40:35 tom-desktop iplist[1915]: error: no running iplist instance found
Aug 21 09:40:35 tom-desktop ipblock[1897]: error: failed to start, cleaning up
Aug 21 09:41:34 tom-desktop iplist[2002]: error: can't convert 192
Aug 21 09:41:34 tom-desktop iplist[2013]: error: no running iplist instance found
Aug 21 09:41:34 tom-desktop ipblock[1995]: error: failed to start, cleaning up
tom@tom-desktop:~$ DEBUG=1 sudo ipblock -sl
[sudo] password for tom: 
iplist[2335]: error: no running iplist instance found
ipblock[2313]: error: failed to start, cleaning up
tom@tom-desktop:~$ 


Any help would be appreciated.

---

### Post by dasbooter on 2010-08-21
Ditto to the previous post....Hope the dev checks in on this thread periodically

---

### Post by sparky64 on 2010-08-21
Same problem here. log results match as well.

Aug 21 21:55:29 home iplist[2562]: error: can't convert 192
Aug 21 21:55:29 home iplist[2573]: error: no running iplist instance found
Aug 21 21:56:51 home iplist[2656]: error: can't convert 192
Aug 21 21:56:51 home iplist[2667]: error: no running iplist instance found

---

### Post by Zone17 on 2010-08-21
same problem here, any info?

iplist[4362]: error: no running iplist instance found
ipblock[4345]: error: failed to start, cleaning up

---

### Post by jfroebe on 2010-08-21
If you're getting a parsing error that is preventing ipblock / iplist from starting such as "error: can't convert 192", the first thing to do is to check with ip blocking list is causing the issue.  In your /etc/ipblock.conf, comment out your lists one at a time until you find the problem list.  

#BLOCK_LIST="badpeers.gz bogon.gz level1.gz"
BLOCK_LIST="badpeers.gz level1.gz

Since yesterday, I've noticed that bogon.gz was causing the problem.  Now, let's look at the only place that produces the "can't convert " error message:

uint32_t list::str2ip(const std::string& str)
{
        uint16_t a, b, c, d;

        if (sscanf(str.c_str(), "%hu.%hu.%hu.%hu", &a, &b, &c, &d) != 4 ||
                        a > 255 || b > 255 || c > 255 || d > 255)
                throw std::runtime_error("can't convert " + str);

        return a << 24 | b << 16 | c << 8 | d;
}

Notice that the sscanf() will read in a *full* ip address and convert it to hex.  If any part of the ip address is invalid (like a letter) or missing (see the bogon snippet below), iplist will spit out the error message and die.

The last two lines of bogon.gz (/var/cache/iplist/bogon.gz) shows us an incomplete ip address:

Bogon:192.231.155.0-192.231.155.255
[COLOR="Red"]Bogon:192.231.188.0-192[/COLOR]

Whether or not to forgo the bogon.gz is up to you but personally I would like an option in iplist to print a warning and skip over that bad ip entry.

---

### Post by blooze on 2010-08-21
I just removed the last line from bogon.gz and it worked fine.

---

### Post by jfroebe on 2010-08-21
Bewarned though.  The next time ipblock updates the filters, bogo.gz will be overwritten.

---

### Post by dbzkid on 2010-08-22
Saw that after August 20th my iplist/ipblock gave me that "No instance of iplist found" error. It is corrected if you remove bogon from the lists like jfroebe said.
Alternatively you can extract the txt file from the bogon.gz, remove the last line, and repackage it as "bogon.gz"

---

### Post by james59802 on 2010-08-22
deleting the last line worked for me too

---

### Post by bark50 on 2010-08-22
I was able to get it going following the previous replies.  To summarize, either one of these worked for me:
1. Delete the bogon.gz list from the "Lists" tab of IPBlock, or
2. Navigate to /var/cache/iplist using the terminal command "sudo nautilus" without the quotes.  Extract the bogon.gz file.  Double-click on the text file that was extracted to open it up in Gedit.  Delete the last line in the list and save the file.  Rezip the text file as bogon.gz (I renamed my previous bogon.gz as "bogon_old.gz").  Close everything and restart IPBlock.  Like someone said before, though, when IPBlock updates to a new bogon.gz file, we'll get the same error messages.  However, I assume we won't get the error messages if the new bogon.gz no longer has the offending line.  Does that sound right to somebody who knows more about this stuff than I do (which is just about anybody!  :lolflag: )?

---

### Post by sllih on 2010-08-24
Thank you! Yes, I resolved the problem with bagon.gz by clicking *Update* button and then *Enable*. Seems like bagon.gz was broken and after update everything works fine again. :)

---

### Post by zorblek on 2010-09-06
I'm using Ipblock on Lucid. It installed and updated just fine, but when I try to enable it, I get the following error messages:
```
iplist[14322]: error: can't find level1.gz
ipblock[14308]: error: failed to start, cleaning up
```
I get the same message when I run it from the command line. Any suggestions would be appreciated.

---

### Post by kingbob on 2010-09-06
I have the same problem.  I found out that, when downloading the lists, they are not being named|renamed properly.  i.e. 

x.gz     [http://www.y.com/x.gz.php](http://www.y.com/x.gz.php)

downloads as x.gz.php, while iplist/ipblock looks for "x.gz" only in the /var/cache/iplist/ folder.  Some other lists which are like

qqqq.gz   [http://www.y.com/mmmmm.gz](http://www.y.com/mmmmm.gz)

of course, do not work either. I believe that some renaming is expected from either some lib with 10.4 Lucid (server) or the ipblock updater function which isn't happening at this time.

I noticed that for each offending file I removed from the list, it complained about the next one.  I renamed a bunch of them, but it also seems to fail to ungz a .gz.php file and the lists aren't loaded properly.

Please help!

---

### Post by Trinisan on 2010-09-06
I'm having the same problem as the last 2 posts. 
none of my lists can be found even though they are /var/cache/iplist
they are in *.gz. tried to load one at a time with the same error.

---

### Post by zorblek on 2010-09-06
I checked /var/cache/iplist, and sure enough, all of the *.gz files were *.gz.php. So I renamed them and that seemed to do the trick. It would be nice if this were fixed, though. I don't want to have to rename the files every time it updates.

---

### Post by KEE on 2010-09-07
hmm, this works buts its weird and i some how block pidgin(hotmail.com, Gmail.com, yahoo.ca, Icq) also theres an error every time i launch[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-2-3.png[/IMG]

---

### Post by KEE on 2010-09-08
man how do you unstall this ? it dont even update i dont even its working anymore. just wanna unstall thanks =)

---

### Post by phaed on 2010-09-08
You would uninstall with:

sudo apt-get purge iplist

---

### Post by dino99 on 2010-09-14
> **dino99 said:**
> new issue on maverick:

was working fine till yesterday August 20th, now i cant enable it

[https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/621636](https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/621636)

vote to this bug report if you want/need this bug fixed (yes it affect me)

---

### Post by dino99 on 2010-09-14
trojan.gz is corrupted too

---

### Post by Justin C. on 2010-09-17
Under 10.04, I got it to load the lists by manually deleting the *.gz files and adding the *.gz.php files in /var/cache/iplist

---

### Post by TheDebianGuy on 2010-09-22
Not working!!!

I installed it, but i keep getting this message when i enable:
iplist[3373]: error: can't find level1.gz
ipblock[3358]: error: failed to start, cleaning up

What do i do?:(:confused:

PS: I really don't know how to use it, so can someone explain the basic functions?
Thanks :)

---

### Post by anitract on 2010-09-22
My temporary fix for the php file name issue was to create soft links in the same /var/cache/iplists directory pointing to the .php files.

So, for example, my level1.gz downloads as level1.gz.php, so i created a soft link named level1.gz that is pointing to level1.gz.php, like so:

sudo ln -s level1.gz.php level1.gz

I did this for all lists effected....seems to work.
EDIT: doing this ensures you don't have to ever physically rename the php files

---

### Post by phaed on 2010-09-22
> **TheDebianGuy said:**
> Not working!!!

I installed it, but i keep getting this message when i enable:
iplist[3373]: error: can't find level1.gz
ipblock[3358]: error: failed to start, cleaning up

What do i do?:(:confused:

PS: I really don't know how to use it, so can someone explain the basic functions?
Thanks :)


You should probably read the whole thread, as that question has been answered.  The problem is that IPBlock is downloading the filter files and attaching .php to the end of them.  They are located in /var/cache/iplist/

So download/update the filter lists with IPBlock, then in a terminal type:

cd /var/cache/iplist

sudo rename 's/\.php//' *.php


That's it.  Note, you'll have to do that every time you update your filters.

---

### Post by TheDebianGuy on 2010-09-22
Hey thanks! it worked!!
:)

---

### Post by anitract on 2010-09-22
If you create the soft links instead, you never have to rename.  :)

---

### Post by uljanow on 2010-09-24
For some reason the server returns lists differently. I use the following php redirects in [http://iplist.sf.net/lists/level1.gz.php:](http://iplist.sf.net/lists/level1.gz.php:)

```
<?php
    header('Location: http://user.cs.tu-berlin.de/~uljanow/lists/level1.gz');
?>
```

But lately it returns level1.gz.php instead of level1.gz. Any suggestions on how to fix this ? It's probably related to the sourceforge webserver.

---

### Post by Graziello on 2010-10-14
And what is iplist repository for Maverick?

---

### Post by phaed on 2010-10-14
Uljanow: click back one page.

Graziello:  you can use past repos.  Try the lucid one.

---

### Post by Graziello on 2010-10-14
Ok, i will try, thank you

---

### Post by mistypotato on 2010-10-18
I can't seem to do a test by blocking my workstation's IP address which is 192.168.0.102.

In other words, I have IPLIST on a server in my local network and I can access the server from a workstation in the local network.

I have a blocklist in which I added the following line.......

TEST:192.168.0.102-192.168.0.103


I saved the file and re-loaded it.  All seemed ok.

It seems to be blocking most other IP's and even others in the same list as I see new blocks popping up...

**However, I am still able to access the server from 192.168.0.102 :confused:**

I made sure that 192.168.0.102 was NOT on the  whitelist.

Anyone ?

---

### Post by uljanow on 2010-10-21
Added maverick support. There's also a new version 0.29 with minor changes (maverick & lucid only).

> * release (0.29)
* fixed compiler issues 
* faulty lines don't cause an exit
* fixed broken file names during update
* fixed lintian errors (deb packages)

---

### Post by endotherm on 2010-10-21
> **uljanow said:**
> For some reason the server returns lists differently. I use the following php redirects in [http://iplist.sf.net/lists/level1.gz.php:](http://iplist.sf.net/lists/level1.gz.php:)

```
<?php
    header('Location: http://user.cs.tu-berlin.de/~uljanow/lists/level1.gz');
?>
```But lately it returns level1.gz.php instead of level1.gz. Any suggestions on how to fix this ? It's probably related to the sourceforge webserver.
I've seen that happen if there is no server side mimetype set for the response stream, or if the handlers for php are messed up and it isn't parseing the page as a script. no apache expert though.

---

### Post by Soccer on 2010-11-15
Help....unable to launch GUI.  I can no longer launch the GUI (have successfully used the GUI for 6 months).  Tried via the Ubuntu Application Menu and the -g option from terminal.  Tried uninstalling and reinstalling the app and no luck.  Can successful run through terminal with all other options but can't get the GUI to start up.  Any suggestions or what additional information can I provide to help others help me to diagnose and fix problem.
Running under lucid

TIA

---

### Post by whitemagicwoman on 2010-11-26
Thanks for posting this.  It seems to work better with Pidgin than Mobloquer does (which was my only problem with that worthy program).

---

### Post by jre on 2010-11-27
> **whitemagicwoman said:**
> Thanks for posting this.  It seems to work better with Pidgin than Mobloquer does (which was my only problem with that worthy program).

Both apps work the same way. The only difference is the default blocklist setup and port whitelistings. So by configuring these things you get the same results with both applications.

---

### Post by fredted40x on 2010-12-06
Have just installed ipblock.

It comes with 5 lists, when i click update do these update as well from bluetack?

Also how can i add more lists. I have read bluetacks are the best but they are out of date. Can anyone tell me please where i can get compatible lists from and how to install and the readme file no longer exists that is talked about on page 1.

Any help would be great,


Thanks

---

### Post by bark50 on 2010-12-07
I reinstalled Ubuntu 10.04 (didn't like 10.10) and followed the directions in the first post to reinstall iplist.  With my previous installation, I could enable IPblock when incoming, outgoing, and forwarded were unchecked under the network tab.  Now the program won't enable unless incoming is checked.  If I try to enable the program with incoming unchecked, I get the message, "error: can't get status of iplist".  Any ideas on what needs to be done so I can enable IPblock when the incoming box is unchecked?  Thanks.

---

### Post by BlueboxPhone on 2010-12-09
This is a great and powerful tool. I am a noob and it took me 15 hours to load this. I dont even know how, but a key was involved. This is way too hard for most. I have no clue what I did. but if anyone needs some help bashing their way through this, just let me know and I will try to help you.

---

### Post by IuilAine on 2010-12-24
I'm new to IPBlock, and I would be incredibly appreciative if someone could explain or take screen shots of the configuration I should have to make sure I have it correct. I don't often do anything other than surf the internet, chat, and download torrents through qbitorrent.

I want to understand how IPBlock works, but I am not 100% sure I do, even with reading through this thread.

Thanks!

-Iui

---

### Post by jayshomebrew on 2010-12-27
Thanks again, worked perfectly out of the box.

they're watching us..:popcorn:

[url=http://www.zimagez.com/zimage/screenshot-1176.php]
  [img]http://www.zimagez.com/miniature/screenshot-1176.php[/img]
[/url]


here's my network tab: (shown updating)
[url=http://www.zimagez.com/zimage/screenshot-2129.php]
  [img]http://www.zimagez.com/miniature/screenshot-2129.php[/img]
[/url]

settings tab:
[url=http://www.zimagez.com/zimage/screenshot-3102.php]
  [img]http://www.zimagez.com/miniature/screenshot-3102.php[/img]
[/url]

lists tab:
[url=http://www.zimagez.com/zimage/screenshot-485.php]
  [img]http://www.zimagez.com/miniature/screenshot-485.php[/img]
[/url]

These are the default settings, except perhaps the 'autostart' checkbox.
note that it says "xxxxxxx IPs blocked" at the top of each screenshot.

---

### Post by trinitydan on 2010-12-27
I just wanted to commend the OP as well on a really nice howto. I noticed it's been kept really up to date which is great too!  Thanks [uljanow]("http://ubuntuforums.org/member.php?u=335776")!

---

### Post by Magic_Spehar on 2010-12-28
I have been using IPblock for the last couple of years to my full satisfaction.  

However I do have an issue regarding the option "autostart".  As I understand when I boot Ubuntu it should also automatically start up. 

When I check the running processes at my Sessions Manager Ipblock is nowhere to be seen. How can I be a 100% sure IPblock is already running ?

---

### Post by trinitydan on 2010-12-28
When I set it to autostart in crunchbang linux which has a verbose boot I see it start the IPBlock daemon.  Also if you look in the log for blocked traffic before you physically opened it, that would be a sure sign it's working as it should.

---

### Post by Magic_Spehar on 2010-12-28
Hi trinitydan,

I checked my log and indeed, it was already blocking. Thx for the simple solution. 

But it remains weird that the process "ipblock" is nowhere to be found in my sessions manager.

---

### Post by uljanow on 2010-12-28
> **Magic_Spehar said:**
> Hi trinitydan,

I checked my log and indeed, it was already blocking. Thx for the simple solution. 

But it remains weird that the process "ipblock" is nowhere to be found in my sessions manager.

IPblock is a front-end for iplist which runs as a daemon process if autostart is enabled.

---

### Post by silverwolf636 on 2011-01-15
I am running Ubuntu Lucid 10.04 and have just installed IP Block. Everything is running fine except I am getting:
 
Range    Source          Destination     Protocol     Action     Hits   Type
Consig   192.168.2.1     192.168.2.3        UDP       Blocked     ##     In 

the source is actually my router. My settings are Autostart Verbose Auto-Update: 2 days Log Level: Match HTTP Proxy 127.0.0.1:8118

Connection I have 

Incoming and Outgoing checked
Ignored Ports (out) I have HTTPS FTP POP3
TCP ssh 9001
UDP domain ntp

all checked

Any suggestions?
Thanx gang.
[COLOR="Red"]**These are the setting I currently have. The post above is incorrect.**[/COLOR]

---

### Post by Blue Dolphins on 2011-01-20
I just installed iplist 0.29 but I can't find the binary to run.  the installation was successful but when I type iplist in the terminal all I get is "no command 'iplist' found".  I searched my filesystem and couldn't find it that way either.  am I supposed to use some other command to start up iplist?

---

### Post by silverwolf636 on 2011-01-23
> **Blue Dolphins said:**
> I just installed iplist 0.29 but I can't find the binary to run.  the installation was successful but when I type iplist in the terminal all I get is "no command 'iplist' found".  I searched my filesystem and couldn't find it that way either.  am I supposed to use some other command to start up iplist?

all I type is iplist -h for the commands.

---

### Post by TangRedSocks on 2011-01-25
Auto start, auto update, auto imported lists? This is an awesome addition to my ubuntu.

---

### Post by squarepants on 2011-01-26
Thank you for this post. It was extremely easy to implement.

However, is there anyway to have IPBlock enabled and have my torrents run at full speed? When enabled my torrent download rate is significantly lower as compared to when it is disabled.

---

### Post by Objekt on 2011-02-27
I, too, was very happy to find this post, and I now have IPBlock keeping the parasites at bay.  I use PeerBlock when I run Windows 7, for the same reasons.

However, I think I'm missing something with regard to whitelists.  As in, there don't seem to be any, or maybe I just don't understand how to add them to IPBlock.

I looked through the Bluetack bunch's website, but all the lists were oriented toward blocking stuff, not allowing the stuff you do want.

In particular, I would like to whitelist traffic for websites I use, such as Netflix, manufacturer product forums, etc.

I suppose I could completely disable blocking of HTTP traffic, but that would sort of defeat the purpose of using IPBlock.

---

### Post by bark50 on 2011-02-27
> **Objekt said:**
> I, too, was very happy to find this post, and I now have IPBlock keeping the parasites at bay.  I use PeerBlock when I run Windows 7, for the same reasons.

However, I think I'm missing something with regard to whitelists.  As in, there don't seem to be any, or maybe I just don't understand how to add them to IPBlock.

I looked through the Bluetack bunch's website, but all the lists were oriented toward blocking stuff, not allowing the stuff you do want.

In particular, I would like to whitelist traffic for websites I use, such as Netflix, manufacturer product forums, etc.

I suppose I could completely disable blocking of HTTP traffic, but that would sort of defeat the purpose of using IPBlock.

Objekt -

When something shows as being blocked on the log tab of IPBlock, you can left-click to highlight it, then right-click to allow the site temporarily or permanently.

---

### Post by Objekt on 2011-02-27
Sure, but I don't want to have to do that every time I try to access a website with HTTP blocking enabled.  It gets old, fast.

I've had to do it with Peerblock under Windows, and it can get really tedious.

I'd much prefer to have a text file or something containing a list of IP addresses known to be associated with a certain service/company website.  If I have to right click and allow every time, I might as well turn IPBlock off.

---

### Post by -=hazard=- on 2011-06-17
> **Objekt said:**
> Sure, but I don't want to have to do that every time I try to access a website with HTTP blocking enabled.  It gets old, fast.

I've had to do it with Peerblock under Windows, and it can get really tedious.

I'd much prefer to have a text file or something containing a list of IP addresses known to be associated with a certain service/company website.  If I have to right click and allow every time, I might as well turn IPBlock off.
For whitelist

Create a p2p list in /var/cache/iplist/ and add the file to ALLOW_LIST in /etc/ipblock.conf Before editing the configuration file the GUI needs to be closed.
A sample p2p list: localhost : 127.0.0.1 - 127.0.0.1

Explanation from this [FAQ]("http://iplist.sourceforge.net/faq.html#0x01")

---

### Post by VcDeveloper on 2011-06-27
Need help! Just installed IPBlock and I can't get it to update.

---

### Post by Sylos on 2011-06-29
> **VcDeveloper said:**
> Need help! Just installed IPBlock and I can't get it to update.

Im having the same problem here. I just installed 10.04 and got ipblock from the repos but it wont update or start. I wonder of bluetack is down and that may be the problem for updating. Not sure why it wont start though.

Any help appreciated.

Heres the error when i try to start with ipblock -s

```
iplist[1886]: error: can't find level1.gz
ipblock[1872]: error: failed to start, cleaning up

```

---

### Post by Sylos on 2011-06-29
It appears the failure to start is because there are no .gz files containing ip ranges for it use - probabbly due to the failure to update.

Im going to try to obtain/create them from other sources and see if I cant get it running.

In the meantime any help is welcome.

---

### Post by djcj on 2011-07-16
First off, thank you uljanow, 

I'm a Ubuntu newbie but after reading this thread can appreciate the work and benefit you've provided with iplist.  Another reason I'm happy to be using Ubuntu and confident in Linux becoming more influential with helpful programmers like yourself.  Super easy to install.

Few questions when you have time:

1) I'd like to start using bit torrents ala Deluge, Vuze, Transmission, Ktorrent, etc.. but was worried when I saw this on Youtube:

**How Anti-P2P lawsuit evidence is collected.**

[http://www.youtube.com/watch?v=KRMsoeofGcI&feature=related](http://www.youtube.com/watch?v=KRMsoeofGcI&feature=related)

Does IPBlock protect against this?

2) Also, earlier in the thread, either you or someone had mentioned to try visiting MPAA.org and microsoft.com to see what happened.  I got the impression that you would be blocked since they collect info.  But I tried visiting those two sites and nothing special happened.  Has something changed in the last few years or are my settings too lax?

Thanks in advance

---

### Post by Objekt on 2011-07-16
Best thing is to use a VPN service so you're connecting through another country, e.g. Sweden.

A bit of a pain, but probably worth it if you download a lot.

---

### Post by VcDeveloper on 2011-07-29
Is there an install for 11.04 natty?

---

### Post by k3yb0ardn1nja on 2011-08-08
Thanks!

---

### Post by Plasma_NZ on 2011-08-11
> **VcDeveloper said:**
> Is there an install for 11.04 natty?

I'd also like to know.... natty i386 and amd64 would be nice..

---

### Post by mujahied on 2011-08-12
thanks man just a question can i use this method and discard the ip tables

---

### Post by nmxdaven on 2011-09-16
This is my favorite Linux ipblocker out of all of the others that I've tried, but I keep running into this problem. Its happened to me twice now on two different machines. 

Things work perfectly for 2-3 months, then out of the blue I get,

>  ipblock[4064]:error updating *list name 

I've tried uninstalling and reinstalling and I get the same thing. Just so strange that it works so well until a certain amount of time has passed. Anyone have a fix for this? I really want to keep using ipblock, its the only one that I really like.

11.04 x64

---

### Post by ein.grosses.pils on 2011-10-04
Same again. I have 11.04 xubuntu and tried the 10.04 version of iplist, but I get the exact same error with or without trying the gui. However, I had previously tried another pc with 11.04 ubuntu (full version with gnome) and iplist and its gui seemed to work okay, at least without errors, though I don't remember if I tested the blocking. maybe there is just some component from gnome that I need? 

Even if this project isn't maintained, the lists themselves get updated. Or should I just try a different solution?


> **Sylos said:**
> Im having the same problem here. I just installed 10.04 and got ipblock from the repos but it wont update or start. I wonder of bluetack is down and that may be the problem for updating. Not sure why it wont start though.

Any help appreciated.

Heres the error when i try to start with ipblock -s

```
iplist[1886]: error: can't find level1.gz
ipblock[1872]: error: failed to start, cleaning up

```

---

### Post by vociferous666 on 2011-10-07
honestly this is some crap software.

great idea, but the update function is the Achilles heel. 
Bluetack updates their lists regularly, this enables you to use them, except it wont download the lists, which always have the same filename and path on the server, only the contents of the list files change.

so yea, look at moblock or some other solution for linux. this is dead in the water from what i can tell.

i am on karmic btw. and followed directions.

---

### Post by ein.grosses.pils on 2011-10-07
thanks mobock up and running easy (sorry broken keyboard)

> **vociferous666 said:**
> honestly this is some crap software.

great idea, but the update function is the Achilles heel. 
Bluetack updates their lists regularly, this enables you to use them, except it wont download the lists, which always have the same filename and path on the server, only the contents of the list files change.

so yea, look at moblock or some other solution for linux. this is dead in the water from what i can tell.

i am on karmic btw. and followed directions.

---

### Post by Phlash on 2012-02-17
> **uljanow said:**
> This article describes how to block lists with a graphical front-end called **IPblock**. No knowledge of networking, firewalls or command-line configuration are needed. Due to the way **IPblock** works it doesn't change the behavior of existing firewalls which makes it compatible ** [1]** with other firewall applications like **ufw**, **shorewall** or **fireHOL**. This howto is intended for Beginners and was tested on Ubuntu Feisty, Gutsy, Hardy, Intrepid, Jaunty and Karmic (32-bit and 64-bit).

**[SIZE=3]Installation[/SIZE]**
Add the iplist repository to your sources.list. Make sure to use the correct sources.list that corresponds to your current distribution:
[LIST]
[*]Ubuntu 10.10 "**Maverick** Meerkat":
```
sudo wget http://iplist.sf.net/sources.list.d/maverick.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 10.04 LTS "**Lucid** Lynx":
```
sudo wget http://iplist.sf.net/sources.list.d/lucid.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 9.10 "**Karmic** Koala":
```
sudo wget http://iplist.sf.net/sources.list.d/karmic.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 9.04 "**Jaunty** Jackalope":
```
sudo wget http://iplist.sf.net/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 8.10 "**Intrepid** Ibex":
```
sudo wget http://iplist.sf.net/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/iplist.list
```
[*]Ubuntu 8.04 "**Hardy** Heron":
```
sudo wget http://iplist.sf.net/sources.list.d/hardy.list -O /etc/apt/sources.list.d/iplist.list
```
[/LIST]
The key of the signed packages can be imported like this: 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C6E3D905C8BCD56BB02E6E0B39456311108B243F
```There is also another way to import the key. You could save the [pub key]("http://iplist.sourceforge.net/uljanow.gpg") to a file and import it through *System->Administration->Software Sources->Authentication->Import Key-file*.

After an update of the Software sources iplist can be installed with any package manager. E.g.:
```
sudo apt-get update
sudo apt-get install iplist
```Note: If **sun-java*** is installed by **gdebi** it requires to open the terminal part of **gdebi** and accept sun's license agreement.
[COLOR=Red]Packages for Feisty and Gutsy can be found in the [0.19 release]("https://sourceforge.net/project/showfiles.php?group_id=198679&package_id=238704&release_id=571106").[/COLOR]

After the installation **IPblock** can be found in *Applications -> Internet -> IPblock*.

[IMG]http://iplist.sourceforge.net/img/tab_log.png[/IMG]

**[SIZE=3]Lists[/SIZE]**

The default choice for lists is similar to **PeerGuardian**.
[LIST]
[*]**level1.gz** - Anti-P2P organizations and known government addresses
[*]**ads-trackers-and-bad-pr0n.gz** - Advertising and data tracker servers
[*]**spyware.gz** - Malicious spyware and adware servers
[*]**edu.gz** - Educational institutions and universities
[*]**bogon.gz** - Spoofed IP-addresses
[/LIST]
These lists are maintained by [www.bluetack.co.uk]("http://www.bluetack.co.uk") [(list descriptions)]("http://iplist.sourceforge.net/faq.html#0x02a"). Custom p2p or dat lists can easily be added. Note that lists can optionally be compressed with gzip.
The URL file **/etc/ipblock.lists** contains list descriptions.

[IMG]http://iplist.sourceforge.net/img/tab_lists.png[/IMG]

**[SIZE=3]Settings[/SIZE]**

All options can be configured in this and the network tab. Auto-updating lists is important and the default choice of 2 days is reasonable. Using out-of-date lists is not  recommended.
To ignore outgoing network traffic like HTTP or EMAIL (pop3) use the ignored ports section. Note that http and dns (domain) is ignored by default. The connection-settings specify which type of connections should be filtered.

[IMG]http://iplist.sourceforge.net/img/tab_settings.png[/IMG][IMG]http://iplist.sourceforge.net/img/tab_network.png[/IMG]

[COLOR=Red]**[1] NOTE: IPblock** needs to be started after other firewall applications. [/COLOR]   

**[SIZE=5][FAQ on iplist.sf.net]("http://iplist.sourceforge.net/faq.html")[/SIZE]**
Thank you, thank you, thank you.  I am a complete linux noob and this was one of the things I was fighting with the other night.  This worked perfectly for me in Mint 12 using the maverick link.

---

### Post by starz677 on 2012-04-30
The logs are written to file /tmp/ipblock.log

---

### Post by Inoki on 2012-11-16
I'm having issues adding new lists. As source I picked [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php), but whenever I try to import one from there it gives me errors. Using latest version of Iplist on Ubuntu Studio 12.10.

---

### Post by bignellrp on 2013-05-01
> **Phlash said:**
> Thank you, thank you, thank you.  I am a complete linux noob and this was one of the things I was fighting with the other night.  This worked perfectly for me in Mint 12 using the maverick link.


Hi, i installed this to 10.10 and have since upgraded to 12.04.  Iplist still seems to be working but the apt sources have been commented out by the upgrade:

$ cat /etc/apt/sources.list.d/iplist.list
# deb [http://ppa.launchpad.net/ssakar/ppa/ubuntu](http://ppa.launchpad.net/ssakar/ppa/ubuntu) maverick main # disabled on upgrade to precise

# deb-src [http://ppa.launchpad.net/ssakar/ppa/ubuntu](http://ppa.launchpad.net/ssakar/ppa/ubuntu) maverick main # disabled on upgrade to precise

Is there a newer version for 12.04?

---

### Post by bark50 on 2013-05-01
When I was running Xubuntu 12.04 I used the instructions here to install Peer Guardian for linux: [http://forums.linuxmint.com/viewtopic.php?f=90&t=94172&p=539688#p539688]("http://forums.linuxmint.com/viewtopic.php?f=90&t=94172&p=539688#p539688").

The one exception to the instructions is I never clicked on <Yes> for automatically starting Peer Guardian linux.  I wanted it to only start when I wanted it to.

---

