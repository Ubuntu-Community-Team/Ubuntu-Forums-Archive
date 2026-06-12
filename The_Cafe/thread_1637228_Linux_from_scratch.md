---
title: "Linux from scratch"
date: 2010-12-04
forum: The Cafe
---

### Post by ki4jgt on 2010-12-04
Anyone have any successful encounters with the book? I want to build my own Linux distro. Have an idea which I think is pretty cool, but want to setup and use it like crazy. I think other people will like also. :-)

---

### Post by Spr0k3t on 2010-12-04
I did a build with the book a while back.  I will say it's one of the best learning experiences I've had with Linux in general.  I built a psuedo slack like setup using rat poison.  The whole reason was to create an extremely fast lightweight no mouse release for a laptop where the touchpad died.  This was back in 2005 though... haven't really played much with LFS since I started using Ubuntu and other variants.

This is the book I had quite a while ago... was a good read, not for the faint obviously: [http://www.amazon.com/Linux-Scratch-Gerard-Beekmans/dp/0595137652](http://www.amazon.com/Linux-Scratch-Gerard-Beekmans/dp/0595137652)

---

### Post by ki4jgt on 2010-12-04
I want to build a completely txt based distro which as soon as you log in looks something like this:

1) File Browser
2) Web Browser
---------------
3) Programs
4) Terminal
---------------
5) Network
6) Users and Settings
---------------
7)
8)
9)
---------------
0) Shut Down

You get the idea. Basically the entire OS would be an easy to use Terminal with no GUI. Using programs like elinks and several others. I would also like the network section to list wifi conncections like:

1) Linksys
2) NETGEAR
3) 2WIRES

Anyway I think that would be really cool. Especially if I can think of a calendar program and an email program.

---

### Post by Spice Weasel on 2010-12-04
> **ki4jgt said:**
> You get the idea. Basically the entire OS would be an easy to use Terminal with no GUI. Using programs like elinks and several others. I would also like the network section to list wifi conncections like:

If you do this... Instead of elinks, use links2 (framebuffer mode with graphics). I'd love that OS forever. :D

Need me a Unix-like terminal w/ graphics when working on other people's PCs.

---

### Post by 3Miro on 2010-12-04
Have you tried Gentoo or Arch Linux. You can get exactly what you are describing with Gentoo very easily. You can probably also get that from an alternative install of Ubuntu.

Linux from scratch is great if you want to learn Linux, but making your on distro is not a one-person-job. Think about security updates and maintenance.

---

### Post by ki4jgt on 2010-12-04
> **3Miro said:**
> Linux from scratch is great if you want to learn Linux, but making your on distro is not a one-person-job. Think about security updates and maintenance.

I don't plan to do many upgrades. Just some here and there make it super guarded OS and then allow the user to do the rest.

EDIT: I also want to get it down to about 70 megs.

---

### Post by frostschutz on 2010-12-04
I did Linux from Scratch years and years ago. I can't comment on today's version of the guide but back then it worked well enough.

You should be aware that for most people, Linux from Scratch is useful as a learning experience only. I installed a complete desktop environment with LFS, however it became impossible to manage after a short while (incompatibilities between various software versions). At that point I switched back to a ready to use distro.

Nowadays doing LFS is much easier than it was back then, since today you can just use a virtual machine. No need to actually mess up your system with it ;)

---

### Post by ki4jgt on 2010-12-04
If one wanted to mod Ubuntu for this endevor, what would they have to do?

---

### Post by amauk on 2010-12-04
> **ki4jgt said:**
> If one wanted to mod Ubuntu for this endevor, what would they have to do?You can get the complete source for any ubuntu release from [http://cdimages.ubuntu.com](http://cdimages.ubuntu.com) in the "source" directory of each release

Here's the Maverick source images
[http://cdimage.ubuntu.com/releases/maverick/release/source/](http://cdimage.ubuntu.com/releases/maverick/release/source/)

---

### Post by 3Miro on 2010-12-04
> **ki4jgt said:**
> If one wanted to mod Ubuntu for this endevor, what would they have to do?

Your best bet is to try the Ubuntu alternate install. On the boot screen when you choose Install/Try, hit F4 and tell it to install a base CLI system only. Once it has installed, you get a command prompt only and you can "apt-get links" and other software like that.

Going Ubuntu -> Linux from Scratch may be too much of a jump. What I did was Ubuntu -> Arch -> Gentoo and decided to stay there. LFS may be a nice project for when I get time, but not any time soon.

---

### Post by ki4jgt on 2010-12-04
How would you access wifi in this cli?

---

### Post by ki4jgt on 2010-12-04
Ok, I'm pretty much planning the security thing, three layers :-)

1) <Inner> System Core - Non-persistant
2) <Outer> User Data - User's files
3) <Farest Out> User settings - Require core access to change (Hackers must go through here to get to the files and the core.) - Persistent with core access only!!

---

### Post by amauk on 2010-12-04
> **ki4jgt said:**
> How would you access wifi in this cli?Put all the details into /etc/network/interfaces (same as with wired network settings)

See the man page for iwconfig for all the settings

---

### Post by ki4jgt on 2010-12-05
OK, now I pretty much have ubuntu setup with connections. I can't get links2 to display the images in the terminal. It will display them in a Graphical terminal, but not in an actual CTRL + ALT + F1 terminal.

---

### Post by Shining Arcanine on 2010-12-05
> **ki4jgt said:**
> Anyone have any successful encounters with the book? I want to build my own Linux distro. Have an idea which I think is pretty cool, but want to setup and use it like crazy. I think other people will like also. :-)
Building your own operating system is feasible. Building one others can use is not. I suggest that after you discover the great pain it is to be your own distribution vendor, you try out Gentoo Linux.

Gentoo Linux's out-of-box customize-ability is close to Linux from Scratch and it is fairly easy to modify in the places where it is not. Those modifications could then be submitted via a Gentoo Linux bug report and if they are done well, they will likely be accepted into Gentoo Linux, so you would not have the bear the sole burden of making updates to Gentoo compatible with your system. Then other people could benefit from your improvements too and you could focus on them as opposed to all of the other things you need for a distribution, like package maintainers for roughly 16000 packages.

---

### Post by ki4jgt on 2010-12-05
Once I get it good, I don't plan on updating it.:frown:

I don't plan to add very much to it. The end user will have to update themselves.

---

### Post by ki4jgt on 2010-12-14
Anyone know any good terminal based email clients and in the (ctrl alt f1) terminal links2 will not display images anyone know a fix to this?

---

### Post by unknownPoster on 2010-12-14
> **ki4jgt said:**
> Once I get it good, I don't plan on updating it.:frown:

I don't plan to add very much to it. The end user will have to update themselves.

Good luck with that being successful. I don't know of any other OS that forces users to update it themselves.

---

### Post by ki4jgt on 2010-12-14
> **unknownPoster said:**
> Good luck with that being successful. I don't know of any other OS that forces users to update it themselves.

I'm planning on creating a release cycle but other than that, I'm going to make it a very locked down distro. One in which no one is trusted.

---

