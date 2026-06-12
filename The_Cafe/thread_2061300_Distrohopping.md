---
title: "Distrohopping"
date: 2012-09-22
forum: The Cafe
---

### Post by Bazon on 2012-09-22
**Why I started:**
I like Gnome Shell. Mostly because of its ability to be modded by extensions. But [this bug]("https://bugs.launchpad.net/ubuntu/precise/+source/gnome-control-center/+bug/965921") (and some other things...) made me think I can't get a real good vanilla Gnome-Shell by Ubuntu...


**The differences I discovered**:
_debian_
feels like good old ubuntu, I really like it. Most things added to ubuntu (unity, software center) are not interesting for me.
BUT:
[LIST]
[*]Adding a printer was a bit harder, I needed an online connection to do that.
[*]bind mounts in /etc/fstab are shown in the system monitor as mounted devices. that's not sooo bad, but as I bind many folders from the same drive in my home-directory, it is really redundant information.
[/LIST]
But overall a good experience. Gnome-Fallback-Mode is also more beautiful than in ubuntu. *(In debian, it looks more like Gnome-Shell with two panels...)*

_fedora:_
I started with Fedora, because the live-USB was amazing fast. I never had such a fluid live-system!
But the disappointment began soon:
[LIST]
[*]At the first boot, the system ended in a black screen. I found out that was because of my TV attached to the HDMI port in my Nvidia Card. Disconnecting the TV, rebooting, getting the proprietary nvidia driver solved the problem, but that really wasn't a good first impression...
[*]the bind mounts-problem is even worse than in debian: In Fedora, the bind-mounts in fstab are even shown in nautilus! (left column, under "devices") unfortunately, they are completely useless there, clicking them leads to nothing....
[*]And finally: The font rendering in fedora is really bad, especially in Firefox. I tried several tricks, from editing .fonts.conf (which helped a bit) to installing addition fonts-packages, looking at that pixelated font-rendering is just depressing.
[/LIST]


**Why I stay with Ubuntu:**
The worst thing in Fedora were really the fonts. I really have to say to the debian/ubuntu guys: Good job! Fonts are important, it's the thing you look to with the highest optical concentration. 
OK, that wasn't a problem in debian, but anyway, the thing that bothered me in ubuntu is easily solveable by going a bit in dconf, for the bind-mounts thing, I haven't found a solution yet...

I really didn't thought fonts can be so important to me! *(Although in 2006, when I last tried fedora, fedora had the same problem which kept me from trying on with fedora...)*


**What are your experiences?**
I mean apart from obvious things like .deb vs .rpm and different desktop environments.
And, additionaly: Do you know the reason for the bind-mounts problem I described or the fonts-rendering problem in fedora?

---

### Post by GreatDanton on 2012-09-22
I didn't try Debian, but I have the same experience like you. Ubuntu 12.04 was not working very well (because of the graphic drivers), so I decided to try Fedora 17. Live usb, was impressive. Everything was so fluent. After I installed it (very fast boot) the first thing I noticed was ugly fonts. After a while I installed Ubuntu fonts (but font was different than in Ubuntu 12.04) and Gnome tweak. I was playing with Gnome tweak (I don't remember where and what I changed, but it was under Fonts tab.) and at the end I was able to use nice Ubuntu font.

I was using Fedora for few months, but then I decided to test Ubuntu 12.10 (Alpha 2). I was lucky because almost everything was working out of the box, so I decided to stay on Ubuntu 12.10.

Regards.

---

### Post by Bazon on 2012-09-22
I also tried to get the fonts better with the gnome-tweak-tool in fedora, but it didn't affected Firefox! I was only able to control Firefox rendering by .fonts.conf...

A, but there is one thing which was really better in Fedora: 
The [Gnome-Bridge-Theme]("http://gnome-look.org/content/show.php?content=151057"), which gives GTK2-Applecations a nice Adwaita-Look, works very good in Fedora but very bad in Ubuntu. Whyever. :-(

---

### Post by Cheesemill on 2012-09-22
I switched to Arch on my home workstation because I was getting tired of the whole 6 month upgrade cycle. I was using 12.10 before this but when they switched to gnome-shell 3.5 it obviously broke all of my extensions.

Arch uses unpatched source direct from upstream to create its packages so it's as close to a 'proper' gnome-shell distro as you are going to get.

I still like the Ubuntu look though so I have the Ubuntu fonts and Ambience theme installed.

---

### Post by warm cardigan on 2012-09-22
Until 11.10, I used Ubuntu exclusively. After the untimely demise of Gnome 2, I tried many other distributions, eventually settling on Xubuntu 12.04. I'm happy now :)

---

### Post by MarjaE on 2012-09-22
I tried Xubuntu 11.10 a while ago. The installer crashed partway through. I managed to get it kinda-sorta running only to find it had no way to disable the malfunctioning touchpad.

Does Xubunti support laptops yet?

---

### Post by BigSilly on 2012-09-22
I'm using Gnome Shell on openSUSE 12.2. I recognised a while ago that Shell wasn't that good on Ubuntu. Personally I much prefer openSUSE's Gnome to Fedora's, it just feels more solid and polished to me. And I prefer the tools (YAST is more sensible in Gnome than KDE, which already hosts a lot of the tools YAST has). I have used Shell on Ubuntu in the past but it doesn't feel loved in the same way, often missing a lot of features as you say. Maybe that will change with the new Gnome Shell remix, but I think it may take some time. In the meantime, I'm happy to stick with openSUSE, and I'd recommend it to anyone looking for high quality Gnome Shell experience.

---

### Post by exploder on 2012-09-22
I run Ubuntu 12.04, Mint 13 and PCLinuxOS KDE. Ubuntu 12.04 has become quite the favorite with all of the improvements that have come to Unity. Cinnamon in Mint 13 is every bit as interesting to me as Unity. PCLinuxOS always works on my hardware, it's a rolling release and the mylivecd tool is simply the best default tool on the planet. I recommend all 3 of these distros depending on what the user is interested in.

---

### Post by Peripheral Visionary on 2012-09-22
I hopped along with my "Linux mentor" whenever *he* hopped,  because he made it sound so fun and exciting! It was totally foreign to me that computers could be exciting, especially changing the operating system. But Robin made it sound like I was missing out on the best fun ever.  Except for dancing, *maybe*.

By the time I joined the fun, I had a chance to play (on his computer) with Mint, Crunchbang, Phoenix (One of PCLinuxOS' lightweight versions), Mepis, Debian, SalixOS ("for lazy Slackers"), and now Xubuntu.

Robin is with the angels now, and probably has them hopping along with him from distro to distro and from one percussive dance routine to another.  And I must admit, without him I'm not so inclined to hop. I inherited his old computer which had Xubuntu 10.04 on it (still Beta at the time), and I was so afraid to change anything! But when the new LTS came out and was a couple of months old, I followed my former teacher's advice for "casual users" like me:


[LIST]
[*]Stick to LTS versions
[*]Don't upgrade 'til they're a few months old
[*]Upgrading is never mandatory
[*]Write down every change you make so you can change it back or get help here on the forums
[*]Always keep it simple and fun.
[/LIST]
I may never hop again, except of course, in dances. Robin's choreography is full of jumps and hops and spins.  But I do cherish the memories of distro-hopping and the  joy that my teacher and friend took in doing so, even when things went badly wrong.

---

### Post by vexorian on 2012-09-22
I was planning to move to Debian. But now that I tried 12.04 for real and I like unity I will have to wait for them to support unity well. To be honest, it is pretty irrational of them to give more care to that lacking gnome-shell rather than in making unity available for the freer world.

I used to collect live CD/USB distros. Puppy Linux is still the most useful thing ever for emergencies. Also liked Slax back in the day.

---

### Post by malspa on 2012-09-22
> **BigSilly said:**
> I'm using Gnome Shell on openSUSE 12.2. I recognised a while ago that Shell wasn't that good on Ubuntu. Personally I much prefer openSUSE's Gnome to Fedora's, it just feels more solid and polished to me. And I prefer the tools (YAST is more sensible in Gnome than KDE, which already hosts a lot of the tools YAST has). I have used Shell on Ubuntu in the past but it doesn't feel loved in the same way, often missing a lot of features as you say. Maybe that will change with the new Gnome Shell remix, but I think it may take some time. In the meantime, I'm happy to stick with openSUSE, and I'd recommend it to anyone looking for high quality Gnome Shell experience.

I'm using GNOME Shell in Ubuntu 12.04 and in Fedora 16. No complaints, but I appreciate this tip about GNOME Shell in openSUSE 12.2 (although I'm happy running KDE in that one).


> **Bazon said:**
> The worst thing in Fedora were really the fonts.

Fonts in Fedora haven't been an issue here. Maybe I just don't pay much attention to that sort of thing.

---

### Post by robtygart on 2012-09-22
I started off with Mint 10 KDE, then I went to Kubuntu, I also use Puppy.

---

### Post by vexorian on 2012-09-22
GS in 12.04 is lacking mainly because it is an old version. Getting the PPA updated version improves most of it.

---

### Post by Cheesemill on 2012-09-23
Which PPA would that be?

Precise comes with gnome-shell 3.4.1, the only version I can find for Ubuntu that is higher than that is the Quantal version which is the 3.5.92 dev version (3.6 which is the next stable version isn't out for another few days).

Even my Arch setup which uses the latest available stable version is only using 3.4.2

---

### Post by mamamia88 on 2012-09-23
I started out with ubuntu, used mint, and debian, but think i have finally found my home with arch.     The documentation is so good and anything i can't get from the official repos i can get from yaourt.   The first time i installed it took very long because i was using my phone as reference and the screen kept timing out.   If you use gparted live to format your partitions and have a us keyboard you could get up and running very quickly.   just did it again today and it went super smooth with the beginners guide open on my ps3

---

### Post by ratcheer on 2012-09-23
I am a pretty bad distro hopper. I currently have five installed on my PC.

I have been using **Ubuntu** the longest, something over three years. I am currently on 12.04.1 64-bit and Unity. Ubuntu is so solid, it gets kind of boring. So ...

Next longest on my PC is **Arch Linux**, 64-bit rolling release. I keep it up to date on a daily basis.I use it with an Openbox desktop and  tint2 panel.

Then comes **Sabayon 10**, a Gentoo-based distro. It is very solid and stable, but it's on kernel 3.5.4. I am using LXDE, but I also have Gnome 3 and gnome-shell installed and available. Although, they keep increasing the release numbers, it is also a rolling release.

Next is **Siduction Linux**, a derivative of Aptosid which is a derivative of Debian. Another rolling release, also on Linux 3.5.4. I'm also using LXDE on this one. This may be my favorite distro. It and Sabayon are my top two. This is the only one of all my distros that automatically detects and mounts my btrfs data filesystem. Ubuntu and Sabayon handle it pretty well, and Arch requires manual intervention every time I boot it.

Finally, over the past few days, I have installed **Gentoo Linux** and LXDE. I originally installed E17 on it, but I couldn't get E17 to run, even though the install seemed to be successful. Arch and Siduction are some pretty hands-on distros, but Gentoo takes the cake. Everything you do is pretty difficult. As soon as I get through learning what I can learn from it, I will probably wipe the partition. But I must say, it was very interesting installing it from a tarball, chroot'ing into the extracted files, and configuring it from the kernel on up. In fact, it's a lot like Linux From Scratch.

Tim

---

### Post by Porcini M. on 2012-09-28
> **ratcheer said:**
> Ubuntu is so solid, it gets kind of boring. So ...


:) The reason for the distrohopping + the inevitable return.

---

