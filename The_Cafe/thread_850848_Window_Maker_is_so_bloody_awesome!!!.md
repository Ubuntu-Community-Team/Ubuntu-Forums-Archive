---
title: "Window Maker is so bloody awesome!!!"
date: 2008-07-06
forum: The Cafe
---

### Post by SirThom on 2008-07-06
I can't get over it.
I had a really good experience with GNOME, an eh experience with KDE, and an even better experience with xfce (which I thought that I would stick with).
But then I installed Window Maker.
OMG BRILLIANT!!!

It has about 0 bloat, but still does cool stuff.
And it's quick!  From the login screen it's not even 2 seconds to get my desktop up.  And I have 7 docapps running.

I still have to find workarounds for a few things.  Like I couldn't get a WiFi manager to come up, but if I run 'nm-applet' from shell, and control-C after a minute, it seems to connect me even though I don't see it working.  Until something better comes around, I still have xfce for emergency repairs.

There is a screenshot below.  Notice that there is no toolbar (there are toolbars available but nads to them).  I opened some menus by right clicking and left them lying around the desktop.  I got rid of the paper clip thing because it was annoying (theoretically a good idea but not for me . . . I use three desktops but what they are for changes regularly).  The last item on my WMdoc (on the right) is a drawer which I have set up with icons (most of which I chose myself) to run things not coming up in the contextual menus for some reason.  I have gretl, 4L-gui, k9copy, nm-applet (I'm soon be modding the login script to execute that and the screensaver engine when I log in), eject CD (the CD/DVD button is not cooperating for some reason), and on the bottom row, kfontview and Xfe file viewer (which is now showing up in my contextual menus so I may remove).

The 4L-gui I have to fix yet.  It needs be run as super-user.  I tried giving the command for that button (all the buttons I set up by modifying a text file) to be 'sudo 4L-gui,' 'xterm && 4L-gui' and 'xterm||sudo 4L-gui' but the first one does nothing and the second two bring up a terminal window and nothing else.  I might write a script that consists of 'sudo 4L-gui' or 'xterm && sudo 4L-gui' and have it run one of those, but besides that I'm not sure what else to do.  Does anyone have an idea?

[http://i25.tinypic.com/15mcrj5.png](http://i25.tinypic.com/15mcrj5.png)

Anyway, if anyone enjoys the problem-solving side of playing with computers and wants something wicked-fast based on an amazing interface paradigm, then they should check out Window Maker.

---

### Post by RiceMonster on 2008-07-06
Glad you found something you really like. I use Openbox.

But anyway, you're probably going to want to autostart nm-applet when you log in, and you might want a tray so you can see it (I use stalonetray which works as a docapp, but there's also trayer). I don't know how to autostart apps in window maker, but I'm sure it's not hard. Do a little research. You may also want to use a gtk theme to make things look a little nicer (I recommend lxappearence for that).

Lastly, +1 for no panels. Who needs em?

---

### Post by LaRoza on 2008-07-06
> **SirThom said:**
> 
Anyway, if anyone enjoys the problem-solving side of playing with computers and wants something wicked-fast based on an amazing interface paradigm, then they should check out Window Maker.

Tried it, it is just the same as KDE and GNOME, at least, to those who use tiling window managers!

---

### Post by akiratheoni on 2008-07-06
WHERE'S THE EYE CANDY ZOMGGGGGGGGG IT LOOKS UGLYYYY



I'm kidding. Glad to see you've found something else, I like Openbox but I might give Window Maker a try soon.

---

### Post by SirThom on 2008-07-06
> **RiceMonster said:**
> Glad you found something you really like. I use Openbox.

But anyway, you're probably going to want to autostart nm-applet when you log in, and you might want a tray so you can see it (I use stalonetray which works as a docapp, but there's also trayer). I don't know how to autostart apps in window maker, but I'm sure it's not hard. Do a little research. You may also want to use a gtk theme to make things look a little nicer (I recommend lxappearence for that).

Lastly, +1 for no panels. Who needs em?

Someone on lj sent me a link that I haven't looked at but I think I only have to write a script, but it in a certain place, and make it executable.

I'm hesitant about the tray but I might install one and take a look.  I think I have most of what I want to see in docapps, although I haven't quite gotten something to tell me the core temperatures working yet (this computer gets very hot so it's important to monitor that).

I think that I'm going to keep this theme.  The black that fades subtly to a dark grey goes well with my background and represents my personal philosophy of stripping bloat to use CPU cycles for the programmes and not the operating system.  I run a lot of mathematical simulations and statistical applications on my machine (no video games), and I prefer it to run like a Ferrari (minimalist in design and built to the highest standards for racetrack performance), not a blinged out SUV with cup holders, window defrosters, air conditioner, GPS nav, DVD player, ground effects lighting, etc.

---

### Post by FFighter on 2008-07-06
> **SirThom said:**
> I can't get over it.
I had a really good experience with GNOME, an eh experience with KDE, and an even better experience with xfce (which I thought that I would stick with).
But then I installed Window Maker.
OMG BRILLIANT!!!

It has about 0 bloat, but still does cool stuff.
And it's quick!  From the login screen it's not even 2 seconds to get my desktop up.  And I have 7 docapps running.

I still have to find workarounds for a few things.  Like I couldn't get a WiFi manager to come up, but if I run 'nm-applet' from shell, and control-C after a minute, it seems to connect me even though I don't see it working.  Until something better comes around, I still have xfce for emergency repairs.

There is a screenshot below.  Notice that there is no toolbar (there are toolbars available but nads to them).  I opened some menus by right clicking and left them lying around the desktop.  I got rid of the paper clip thing because it was annoying (theoretically a good idea but not for me . . . I use three desktops but what they are for changes regularly).  The last item on my WMdoc (on the right) is a drawer which I have set up with icons (most of which I chose myself) to run things not coming up in the contextual menus for some reason.  I have gretl, 4L-gui, k9copy, nm-applet (I'm soon be modding the login script to execute that and the screensaver engine when I log in), eject CD (the CD/DVD button is not cooperating for some reason), and on the bottom row, kfontview and Xfe file viewer (which is now showing up in my contextual menus so I may remove).

The 4L-gui I have to fix yet.  It needs be run as super-user.  I tried giving the command for that button (all the buttons I set up by modifying a text file) to be 'sudo 4L-gui,' 'xterm && 4L-gui' and 'xterm||sudo 4L-gui' but the first one does nothing and the second two bring up a terminal window and nothing else.  I might write a script that consists of 'sudo 4L-gui' or 'xterm && sudo 4L-gui' and have it run one of those, but besides that I'm not sure what else to do.  Does anyone have an idea?

[http://i25.tinypic.com/15mcrj5.png](http://i25.tinypic.com/15mcrj5.png)

Anyway, if anyone enjoys the problem-solving side of playing with computers and wants something wicked-fast based on an amazing interface paradigm, then they should check out Window Maker.

It looks ugly

---

### Post by LaRoza on 2008-07-06
> **FFighter said:**
> It looks ugly

Using what criteria? It is uncluttered.

A window manager should, IMO, manage windows and not be a show in itself.

wmii is a better wm than Window Maker, and it is plainer but more functional and more beautiful. No, it isn't a video game like GNOME/KDE with its constant shuffling and resizing of windows by the user, but a killer manager of windows.

---

### Post by wrtpeeps on 2008-07-06
xfce4 is both good looking and uncluttered.

---

### Post by mips on 2008-07-06
Still reminds me of NeXTSTEP :)

---

### Post by regomodo on 2008-07-06
Looks a bit '97ish. I'll stick with JWM thanks.

---

### Post by LaRoza on 2008-07-06
> **wrtpeeps said:**
> xfce4 is both good looking and uncluttered.

It is the same as GNOME and KDE is that respect, it is up to the user.

---

### Post by graabein on 2008-07-06
I like Window Maker a lot. Old school style.

---

### Post by -grubby on 2008-07-06
Window maker is nice, I never really experienced much of it, but those little dock things are kinda cool. I didn't get it to look all that great, and just stick with Fluxbox. Man I wish Fluxbox tiled windows, I find wmii usable, but I find it hideously ugly (the green toolbar .. :X) and I don't want to remember 10 keyboard shortcuts. Otherwise it's fine. And I want a user configurable menu for it too.

---

### Post by LaRoza on 2008-07-06
> **nathangrubb said:**
> Window maker is nice, I never really experienced much of it, but those little dock things are kinda cool. I didn't get it to look all that great, and just stick with Fluxbox. Man I wish Fluxbox tiled windows, I find wmii usable, but I find it hideously ugly (the green toolbar .. :X) and I don't want to remember 10 keyboard shortcuts. Otherwise it's fine. And I want a user configurable menu for it too.

Green? It is a darkblue...

Of course it depends on the version and setup. wmii is very easy to customize.

You don't "remember" the keys any more than you "remember" how to type. At first you have to, then it becomes natural very quickly.

---

### Post by chucky chuckaluck on 2008-07-06
> **LaRoza said:**
> No, it isn't a video game like GNOME/KDE

haha! i guess that would make compiz the open source equivalent to grand theft auto.

the last couple of times i've tried windowmaker, i thought something was wrong with it, on both arch and baboontu. it's like there's a delay, or something. also, i find configuring it to be a giant pain in the butt. it can looks nice, though.

---

### Post by Anzan on 2008-07-06
I use GNOME and Fluxbox. Xfce occasionally. Trying to get into ratpoison and awesome. 

But when I want a particular kind of experience, Window Maker is great.

By the way, I've read somewhere on here that their website says its back under development.

---

### Post by -grubby on 2008-07-06
> **LaRoza said:**
> Green? It is a darkblue...

Of course it depends on the version and setup. wmii is very easy to customize.

You don't "remember" the keys any more than you "remember" how to type. At first you have to, then it becomes natural very quickly.

Maybe I'm just blind then, but I swear it looks green on this screen. Also, would you mind pointing me to some guide I can use to customize Wmii? Perhaps I'll give it another go, thanks :)

---

### Post by init1 on 2008-07-06
Heh, glad you've found your favorite :D
I felt like that when I found flwm. I'm in using Gnome right now though.

---

### Post by SirThom on 2008-07-06
> **mips said:**
> Still reminds me of NeXTSTEP :)

NeXTSTEP was quite awesome . . .

---

### Post by toupeiro on 2008-07-07
Wow... I didn't know window maker was still around.  That was the first Linux GUI I ever tried to use.  Looks about the same :)

---

### Post by graabein on 2008-07-07
> **nathangrubb said:**
> Maybe I'm just blind then, but I swear it looks green on this screen. Also, would you mind pointing me to some guide I can use to customize Wmii? Perhaps I'll give it another go, thanks :)

[http://w3.linux-magazine.com/issue/64/Desktopia_Wmii.pdf]("http://w3.linux-magazine.com/issue/64/Desktopia_Wmii.pdf")

[http://box-look.org/]("http://box-look.org/")

[http://nex-3.com/posts/52-trying-out-wmii]("http://nex-3.com/posts/52-trying-out-wmii")

---

### Post by c01e on 2009-07-29
totally agree. wmaker is the king - the quickest environment to work in, for ALL tasks, if you take advantage of custom key bindings and menus.

Tip: you can alway run the ubuntu panel via typing gnome-panel and that will show you the nm-applet monitor in the top right corner.

Tip: Use vmware on a powerful server, ssh -X into it from your laptop and run vmware loaded with any/all windows environments at once. I use them to use Protel, Pro Engineer, Solid Works and to play around with remote and local windows vulnerabilities.

My desktop: [http://i32.tinypic.com/2cep8jo.png](http://i32.tinypic.com/2cep8jo.png)

Recommended software:
    * Internet Browser: firefox
    * E-Mail Client: thunderbird
    * Graphical Tools: gimp inkscape imagemagick dia eog
    * Audio Players: rhythmbox xmms
    * Video Players: mplayer vlc totem
    * CD/DVD Ripping/Burning: mkisofs cdrecord dvdrecord dvdbackup
    * Video Editing: kdenlive kino cinelerracv
    * Scanning Util: xsane
    * Printing Util: gtklp a2ps
    * Math Tools: apcalc octave scilab gnuplot
    * P2P: bittorrent limewire IRC
    * Chat: ircii xchat skype amsn pidgin
    * Text editor: emacs
    * Document Viewer: evince xpdf gnochm
    * Professional document writing: latex
    * WYSIWYG editor: openoffice
    * Circuit Diagrams: eagle
    * 3D modeling and animation: blender
    * Proxy Tools: tor privoxy macchanger
    * Network monitoring: tcpdump iptraf ethstatus wavemon kwifimanager wifi-radar tcpick pktstat nast dsniff ethereal etherape htop netflow psad snort fail2ban
    * System monitoring: sysstat hddtemp hdparm lm-sensors conky
    * Packet Manipulation: scapy packit nemesis
    * DNS tools: geoip-bin traceroute
    * Vulnerabilities Packages: nmap nikto nessus metasploit BackTrack
    * Anti-virus: clamav
    * Rootkits: rkhunter chkrootkit
    * Crackers: crack-md5 fcrackzip pdfcrack medussa john
    * Wifi Crackers/Utils: aircrack kismet weplab
    * Passwd Generators: wordplay an apg gpw otp
    * File Protection: secure-delete
    * Remote Login Software: ssh vnc rdesktop
    * Windows X: wine vmware
    * Fake Servies: fakepop honeyd
    * WM Docks: wmclock wmusic wmacpi wmnet wmnd wmmixer wmwifi wmifinfo wmwave wmmisc bubblefishymon wmfire wmnotify wmweather+ 

ENJOY!

---

### Post by Giant Speck on 2009-07-29
Zombie thread!  Run! Ruuuuuuuuuuuuuuuuuun!

Oh, God!  It's got my leg!

---

### Post by bossyandrew on 2009-07-29
> **LaRoza said:**
> Tried it, it is just the same as KDE and GNOME, at least, to those who use tiling window managers!
Yup , i have try this the same to you...:D

---

### Post by koleoptero on 2009-07-29
> **Giant Speck said:**
> Zombie thread!  Run! Ruuuuuuuuuuuuuuuuuun!

Oh, God!  It's got my leg!

rofl. There was an image to go with your post, give me a moment to find it...

EDIT: Here it is:

[IMG]http://www.w3bdevil.com/forums/Old-MummyHead.jpg[/IMG]

---

### Post by amitabhishek on 2009-07-29
I am trying hard to like it...:(

---

### Post by frodon on 2009-07-29
necromancing

Thread closed.

---

