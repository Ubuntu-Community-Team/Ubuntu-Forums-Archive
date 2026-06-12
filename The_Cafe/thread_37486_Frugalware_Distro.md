---
title: "Frugalware Distro"
date: 2005-05-27
forum: The Cafe
---

### Post by LongTooth on 2005-05-27
I'm as much a dedicated Ubuntu man as any other on this forum. Its my main distro. But that doesn't stop me exploring other distros. And I hope it doesn't stop you either.  Do yourself a favor and check out Frugalware. It's a Slackware based distro that comes pretty much ready to use right out of the box. 

I've been playing with it for some two weeks. And I'm finding it a well put together distro. Unlike Slackware - which I didn't care for- it uses Pacman for a package manager and that is a something new for me. I've got the apt-get commands (or most of them) in my head and ready to use. The experience has been very pleasant. 

Distrowatch.com was impressed with the distro and on their recommendation I decided to try it.  Distrowatch did advise its not for newbie. And it's definitely not for the faint of heart. But if you've got a test box or spare HD visit them. [http://frugalware.org/news.php](http://frugalware.org/news.php)

---

### Post by bored2k on 2005-05-27
What is their release cycle ? I see they have some very updated packages like MPlayer 1.7. What's the default DM, how many discs ? Their screenshots show the most popular DM's, so wich one is it ? How good is this PACMAN Pkg manager ? Stable/Fast/Slow ? What's the new thing it incorporates to the linux community ?

---

### Post by totalshredder on 2005-05-27
[QUOTE=bored2k]What is their release cycle ? I see they have some very updated packages like MPlayer 1.7. What's the default DM, how many discs ? Their screenshots show the most popular DM's, so wich one is it ? How good is this PACMAN Pkg manager ? Stable/Fast/Slow ? What's the new thing it incorporates to the linux community ?[/QUOTE]
I'm no expert, but I used arch linux for a while (where pacman orignated from) and I'd have to say pacman is my fav. package manager of all. Very smooth.

---

### Post by bored2k on 2005-05-27
[QUOTE=totalshredder]I'm no expert, but I used arch linux for a while (where pacman orignated from) and I'd have to say pacman is my fav. package manager of all. Very smooth.[/QUOTE]
 So how does it work ?

---

### Post by TravisNewman on 2005-05-27
pacman install <package>
or something similar. If I remember correctly. ;)

There's also a recursive uninstall. Like, in Ubuntu for example, if it had pacman you could recursively uninstall ubuntu-desktop and it would get rid of everything it depends on, unless needed by others.

---

### Post by LongTooth on 2005-05-27
Just starting out with it I can't answer all you questions but I'll try. 

Looks like the release cycle is around 6 mo. The next one, 0.3,  will be released 10/13/05. 

The default DM is KDM. But it was easy enouth to change to GDM. Being a Gnome man, I just had to do that. 

"How good is this PACMAN Pkg manager?"  It's akin to CLI Apt-get. Su > pacman -Syu...will update your system. pacman -R (packagename) will remove, etc. I just have to get the commands down. A frontend, ala Synaptic, for Pacman is also provided but I haven't tried it yet.  I'm in the process of deleting programs I either don't want or use. And using pacman -R (packagename) I've been able to do so.

I believe speed is subjective but as Frugalware is based on Slackware I'm extremely pleased with the speed and I installed everything on the CDs.

Stream video/audio come completely ready for the user. All the codex (streaming video-WMV, .mov, mpg, etc) needed. Also Flash, Java, etc.   

Stable: As for bugs, the only quirk I come across is the browser crashing occasionally when viewing streaming video or using BMP with streaming audio. Hopefully this will be corrected when the next release come out. Other than that I feel Frugalware is very stable. Don't forget, like Ubuntu, this is only the second version. 

Only the first two CDs are needed. But there is also a netinstall CD. I gave that a try but that didn't work for me. Pilot error? Probably. So I downloaded the CDs needed and installed that way. One does have the option to be slective when istalling programs but again I wasn't succesful in that and ending up installing everything. Once I had my system up, I didn't want to reistall. Thus the deleting of apps, DEs, WM, etc. Maybe I'll do a fresh install and...Nah. I don't think so. 


A full install takes 3.9Gb of space. that's a lot. But I've been able to get some of that back removing packages. KDE, IceWM, XFCE4.2, Enlightment, and several 'BoxWM come with it. As in other distros, more programs then one can use are installed by default. All the editors anyone would want and more. Clean up time for me. 

The community is small and lacking. As is the documentation but I attribute that to this being a young distro. I hope so. 

I'm still in the discovery stage with this distro but I see great potential.

---

