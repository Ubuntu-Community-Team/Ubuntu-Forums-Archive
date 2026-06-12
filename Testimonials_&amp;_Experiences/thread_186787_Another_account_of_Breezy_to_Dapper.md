---
title: "Another account of Breezy to Dapper"
date: 2006-06-02
forum: Testimonials &amp; Experiences
---

### Post by meng on 2006-06-02
Here's a brief account of my experience with the upgrade. Perhaps you will recognize some aspects in common with your own experience.

1. I had decided to wait 2 weeks after release before upgrading, so that I could learn and avoid the common pitfalls. That resolution didn't last long: I came home and couldn't wait to jump on the bandwagon. (I guess I can't be a true Linux user, surely Linux users don't believe in bandwagons?)
2. Of course, I made sure to back up my personal data before upgrading, even though my /home is on a separate partition. You can never be too safe. This is when I discovered that my DVD-writer had died (took me 30 minutes to be sure that it was truly dead, initially I thought it was a problem with automounting). No problem - ran out to the local electronics franchise to pick up a dual-layer writer at a bargain price.
3. Backed up data, burned the alternate-i386 iso. Used this as the repository for upgrading.
4. Reboot. X-server crashes. ("Oh bother!" I said, well it was a little more colorful than that." But no need to panic - with my backup computer I get online and figure out that I need to dist-upgrade then reconfigure xserver and gdm. Oh goody it works now, quickly install nvidia-glx. Nice.
5. Stupid PCMCIA, I don't need it for my desktop. Minor annoyance, easily fixed using sysv-rc-conf.
6. Hey, where did my applications go? (openoffice, mplayer, vlc, azureus) Ick, totem-gstreamer has replaced totem-xine. Easily fixed by updating repos and visiting synaptic package manager several times. Eww, openoffice looks ugly. Fixed by installing openoffice-gnome and openoffice-gtk.
7. Menus are different - fixed by opening smeg and re-enabled many of the shortcuts.
8. At least adobe reader, java and realplayer are still there.
9. Okay now everything's running as before. What's different?

[LIST]
[*]Now running firefox 1.5. rather than 1.0.x. Um, it looks ... the same.
[*]GNOME 2.14 and upgraded vorbis-tools. Finally I can audio-preview .ogg files. And the recent documents function is working consistently ... so far.
[*]Shutdown menu initially looked ugly with only one of six icons showing. Nicer when all 6 icons finally appeared (not sure what I did to enable this).
[*]Dialog asking for sudo password is bigger and uglier, and the screen fade is a bit annoying. I'll learn to live with it.
[/LIST]

The important thing is, everything works. Relatively little manual tweaking was required. By comparison, the Hoary to Breezy upgrade broke my system completely (probably because of broken packages prior), and I have never got a Windows version upgrade to work. Both these situations were only resolved by clean install.

Bottom line: I'm happy. It wasn't entirely painless, but nevertheless the best upgrade experience I've ever had.

---

### Post by mostwanted on 2006-06-02
FF 1.5 is quicker than 1.0, supports canvas and svg and better plugins, so it's not quite the same :)

I usually do dist-upgrading for testing out new stuff in the alpha/beta phase, but prefer to make a clean install for a new stable system. Doesn't come with the same share of problems you (sometimes) get from doing an upgrade.

---

### Post by meng on 2006-06-02
[QUOTE=mostwanted]FF 1.5 is quicker than 1.0, supports canvas and svg and better plugins, so it's not quite the same :)[/QUOTE]
Thanks for the info. I didn't know the specifics, but I knew it's not actually the same, I was just joking about the superficial appearance. Same with GNOME/Nautilus - for me the outward appearance is identical -  but I was more aware of the differences underneath.

---

### Post by donmiguel on 2006-06-05
[QUOTE=meng]
...
4. Reboot. X-server crashes. ("Oh bother!" I said, well it was a little more colorful than that." But no need to panic - with my backup computer I get online and figure out that I need to dist-upgrade then reconfigure xserver and gdm. Oh goody it works now, quickly install nvidia-glx. Nice.
5. Stupid PCMCIA, I don't need it for my desktop. Minor annoyance, easily fixed using sysv-rc-conf.
...[/QUOTE]


hi meng!
i have exactly these two problems after making dist-upgrade.... well, the PCMCIA-stuff i think i know how to handle. but first, i gotta fix xserver and gdm. 
How exactly did you make it?? i would be very thankful if you could quick post that, so i don't screw up more :)
i guess its sudo apt-get reconfigure xserver?? or sth like that??

greets from lausanne
donmiguel

---

### Post by meng on 2006-06-05
Hello over there in Switzerland (do I have my geography correct?)
This is more or less what I did
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)
but that didn't work. So I did
sudo apt-get dist-upgrade
first, then repeated the other steps, and it worked.

---

### Post by WiseElben on 2006-06-11
I downloaded the ISOs, and the check sums matched, but I could never burn it properly. I wasted 3 CDs, and all 3 were corrupt. So then I just decided to upgrade instead, using this topic: [http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

Well, I broke x a couple of times, screwed up Grub a few times, but I eventually got everythign working! Wohoo! Oh yeah, I'm a Linux noob, so I feel very proud now. =)

---

### Post by wishy77 on 2006-06-11
Impatience got the better of me and I tried the (new) automatix Breezy upgrade 
and trashed my Breezy....couldn't make head nor tail of the errors/screens so back to square 1.
Up and running with a new Breezy install  and finally downloaded the alternative iso and u beauty it burnt perfectly and I loaded Dapper.
Crossed fingers and used Automatix for Dapper as per the  instructions.....puuuurfect.
HP psc 1400 all-in-on printer/scanner/copier..perfect, again  everything "just works"
THANKS again to all the crew/developers etc and arnie boy and the automatix builders..much appreciated.
Dapper is great.

---

