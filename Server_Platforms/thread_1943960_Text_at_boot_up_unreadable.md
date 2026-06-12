---
title: "Text at boot up unreadable"
date: 2012-03-20
forum: Server Platforms
---

### Post by wantan0 on 2012-03-20
I have installed Ubuntu server 11.10 and am experimenting with setting up a home server on an old PC I pulled out of the trash. My hope is to expand it's space in the future but for now I'm just tinkering.

Installation was fine, however sometimes on boot up the text becomes complete nonsense. The characters are ether a jumbled mess or horribly smudged (see photos). This doesn't happen all the time, nor does it ever happen to Grub. Does anyone know why this might be?

Specs:
800 MHz Celeron
128 MB RAM
30 GB Hard Drive

---

### Post by arrrghhh on 2012-03-20
Did you install a DE, or is this still GUI-less?  I'd say there might be something wrong with your video card, the buffer doesn't seem happy.  

Can you administer the machine remotely?  I rarely, if ever, am on the server itself - I am always SSH'd either over the WAN or LAN into the server.  The only time I had to get back on the box was a while back when I disabled password auth and messed up my SSH keys, lol.

---

### Post by hawkmage on 2012-03-20
Whenever I have seen something like this is is usualy the video card, cable or monitor that is starting to flake out.

---

### Post by bubylou on 2012-03-20
I have the same problem on my old server but the text usually comes up at the end. Does your server have a floppy drive? If so then try disabling it, that was one solution i cam across when i had this problem, don't ask why. But it was never really a problem since im never physically on the server.

---

### Post by wantan0 on 2012-03-20
Thanks everyone for you suggestions. It turns out it was way easier to establish a connection through my university's network than I thought, so I'll just remote in from now on.

My guess is whatever on board video chip this paperweight is running is going a little senile. Maybe I'll have to upgrade sooner than I thought...

Also it is GUI-less, because my Mechanical Engineering friends are waaaay more impressed with a command line. Haha.

---

### Post by bubylou on 2012-03-20
An excellent and simplistic choice. Don't forget to mark the thread as solved.

---

### Post by Razorpac on 2012-10-07
I got the same problem on a old computer.
i dont have ssh installed yet so i cant connect to it.
i dont think its the grapics because i tried switch to an another graphics card and the problem persists.,
when i put in a live cd, the graphics are normal.
 
i wish a solution for this problem that enable me to install ssh blindly without seeing what im doing or something to alter the graphics so i can see what im doing..

the goal is to use the computer remotely.

---

### Post by Bashing-om on 2012-10-07
@ Razorpac; Hi ! Welcome to the forum.

  alter the graphics: try booting with the "nomodeset" option.
Soon as bios screen clears depress a key =>boot options menu.
select f6 (nomodeset), f10 to continue booting.

In the event this does not resolve your problem, start another post for additional assistance.
[INDENT]warm regards <==BDQ

[/INDENT]

---

