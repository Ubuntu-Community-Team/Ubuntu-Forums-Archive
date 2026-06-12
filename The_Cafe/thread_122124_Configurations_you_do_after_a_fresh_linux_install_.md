---
title: "Configurations you do after a fresh linux install on your system?"
date: 2006-01-26
forum: The Cafe
---

### Post by towsonu2003 on 2006-01-26
My list is as follows: 
*make winmodem work (slmodem)
*configure wvdial and pray for dial up
*make wlan0 work with ndiswrapper (and pray some more)
*take a chance at getting the proprietary ati driver to work (nope, maybe next release)
*configure conky (although not a system configuration, helps me maintain the system so much, I had to list it here)
and that's all after a fresh ubuntu 5.10 install.

What do you configure in your system -especially the more experienced users? No need for technical info (that's why I'm posting it to Community Chat). 

The reason I'm posting this is to learn whether I could do other configurations for an optimal usage. Not having ANY linux users around me, I don't know whether I am using this optimally. Also, I'd like to know what is possible ;)

thanks.

---

### Post by dickohead on 2006-01-26
Mostly I just install software, customise the GUI, and connect to network resources.

ie:
Change theme to milk, milk mint or bluewave.
Thunderbird (install and setup)
AmaroK
Install Gnome Art Manager
Download backgrounds, icons etc
Samba shares

Sometimes if I can be bothered I setup NVidia 3D acceleration, but I have no use for it so I don't bother.

---

### Post by Ultimo Aliento on 2006-01-26
First , i made accounts for my brothers, then i get java and flash, later the mp3 codecs and the ati drivers, after that i configure firefox to get all the speed posible with my conection.

I copy all my gnome stuff, safely guarded on another partition, and i take like 3 hours changing my desktop until i feel comfortable, after that , the rest is just stetic and games :P

---

### Post by Perfect Storm on 2006-01-26
1. Adds extra stuff to my sourcelist
2. checking for updates.
3. installs kernel i686 or compiling my own (if in the mood)
4. Setting up nvidia card and screen resolution.
5. apt-gets all the applications I use/downloading and the other appplication which aren't in the repo. (java, codecs, flash, pixel32, crossoveroffice etc. etc. etc.)
6. tweaking.
7. Installs native games.
8. Installs Cedega, wine, dosbox + non-native games.
9. more tweaking.
10. Setting themes (metacity, GTK2, icons, sounds, GDM, Splash, gdesklets and cursor) Always using thte same, got it backup'ed on CD with a script so it take some secs.
11. ...and properly some more which I can't remember :P

---

### Post by towsonu2003 on 2006-01-27
[QUOTE=Artificial Intelligence]
6. tweaking.
9. more tweaking.
[/QUOTE]
and you tweak...... ?? :)

---

### Post by poofyhairguy on 2006-01-27
1. Use Automatix
2. CP a backup of my Xorg.conf to the right place
2. Download smp kernel and bittornado-gui

done.

It used to be much harder.

---

### Post by Alpha_toxic on 2006-01-27
1. swap the kernel with 686-smp
2. Automatix (Opera, codecs, j2rm, j2sdk, nVidia, Adobe Reader...)
3. XMMS, Synaptic (instead of Adept), some eyecandy (Moodin, 3ddesk, xdesktopwaves, some applets)
3. remove some of the stuff I don't use, so it doesn't get in the way (Amarok, PDFVewer, scanner and printer stuff, wireless, bluetooth...)
4. Eclipse, Kdevelop, build-essentials...

---

### Post by fuscia on 2006-01-27
i've only re-installed a couple of times, but what i have done was do the default install (never managed to do a server install without a major fuckup. after it's in, i go through synaptic and prune away all the junk i don't use (office, games, gaim, etc.), add new sources, xmms, alternative window managers (if i were to do this now, i'd switch to wdm and dump gnome, as i have eventually done), dillo, opera, rox-filer. don't remember what else.

---

### Post by mohapi on 2006-01-27
I usually just grab the Automatix package, since it seems to have everything I need. I'm lucky in that sense; my machine more or less installs itself. I do have to activate the subwoofer.

I install Scribus. I think that's it. And Nvu.

---

### Post by ardchoille on 2006-01-27
add various repos (universe, multiverse, plf, etc)
sudo apt-get update && sudo apt-get upgrade

sudo apt-get firestarter
set up firestarter

sudo apt-get install rkhunter
run rkhunter

sudo apt-get install chkrootkit
run chkrootkit

add group wheel
sudo chown root:wheel /bin/su
sudo chmod 4750 /bin/su

echo This is a private network > /etc/issue
echo This is a private network > /etc/issue.net

echo ALL: 127.0.0.1 >> /etc/hosts.allow
echo ALL: PARANOID >> /etc/hosts.deny

sudo mv /usr/bin/ssh-agent /usr/bin/ssh-agent-origin && sudo killall ssh-agent

open /etc/ssh/ssh_config and replace "#   Protocol 2,1" with "#   Protocol 2"

sudo apt-get install apache2
tweak apache conf to disallow all outside connections
open /etc/apache2/ports.conf and replace "Listen 80" with "Listen 127.0.0.1:80"

sudo apt-get install php5
install PmWiki

There are more commands that I do to tweak and lockdown my box and I have them in a master script that I run just after a fresh install.. it runs while I go eat lunch :)

---

### Post by TechSonic on 2006-01-27
1. Update ATI Radeon 9200 Drivers from [www.ati.com](www.ati.com)
2. Run Synaptic and install applications, Nvu, Helix player.. etc
3. Set Gnome eyecandy to bare minimum.
4. Make a mounted connection to my web site [www.techsonic.net](www.techsonic.net) and configure Nvu to publish to it.
5. Change to alsa-oss
6. Enable all repositories and update if needed.
7. Mount my NTFS partition from WinXP to access Mp3s and movies stored on it.
8. Configure Apache, MySQL, PHP, Postfix and fetchmail.
9. Transfer all testing material for my site to my local apache.
10. Configure Mail and Gaim for my accounts.
11. Install America's Army and Teamspeak.
12. Edit some menus and then check if all works.
13. Open digital camera with Gtkam to make sure it's connecting.
12. Play Gnometris :)
13. Change splash screens, login screens with some of my own Tails Images. :D
14. Play some of my ocremix.org downloads and watch some movies on atomfilms.com

---

### Post by jc87 on 2006-01-27
686 kernel 

Sources.list  

Removable drives and media only to mount when inserted/hot plugged  

Gnome eye candy (gdesklets , themes , small changes in the panels , etc..)

Make GDM login as jc87 automatically 

Try to make my radeon 9250 work (failed so far)

Install apps like Nvu , Xine , etc...

Codecs , flash , java , etc...

Download pr0n

---

### Post by Lovechild on 2006-01-27
[QUOTE=TechSonic]1. Update ATI Radeon 9200 Drivers from [www.ati.com](www.ati.com)
[/QUOTE]

Use the xorg driver instead, it's more stable and provides the same performance on your card. r200 series Radeon card are some of the best supported videocards on Linux.

Anyways I:
0) Security updates
1) replace OpenOffice with GNOME Office
2) replace Firefox with Epiphany + Epiphany extensions
3) change metacity button order to close:minimize,maximize
4) restore user backup
5) remove gnome-games
6) rearrange menus
7) install MonoDevelop

---

### Post by TechSonic on 2006-01-27
Why?  it works fine.  It actually runs America's army with faster frame rate then on Windows with the offical cd drivers.


[QUOTE=Lovechild]Use the xorg driver instead, it's more stable and provides the same performance on your card. r200 series Radeon card are some of the best supported videocards on Linux.

Anyways I:
0) Security updates
1) replace OpenOffice with GNOME Office
2) replace Firefox with Epiphany + Epiphany extensions
3) change metacity button order to close:minimize,maximize
4) restore user backup
5) remove gnome-games
6) rearrange menus
7) install MonoDevelop[/QUOTE]

---

