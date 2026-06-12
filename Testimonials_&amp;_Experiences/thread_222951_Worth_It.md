---
title: "Worth It"
date: 2006-07-25
forum: Testimonials &amp; Experiences
---

### Post by paulmerchant on 2006-07-25
I don't want to make this a horror story, but I have to be honest. Ubuntu Dapper Drake has been hard on me. But I still think it's been worth it.

To start things off, I should say that somehow I became a prime Ubuntu candidate over the last few years. I moved from MS Office at work and WordPerfect Office at home to OpenOffice both places, from PhotoShop to The Gimp, from Delphi (Pascal) to dev tools like Python, and I've been using applications like Inkscape and Blender and Audacity and open source content management systems. I even had a little Red Hat experience managing some servers a few years ago. Recently I woke up one day and wondered why I wasn't running GNU/Linux.

The first thing I did was play with some Live CDs. Then I tried an installation on a laptop with Mepis 6, a well rounded live CD. It went great, even with some not that great hardware. Everyone kept praising Ubuntu so I thought I would try that instead, especially since Mepis installed so easily and I new it was based on Ubuntu. I blasted Mepis and started to install Ubuntu 6.06 LTS. Unfortunately, the graphical installer (Live CD) kept haning and causing problems (a 256mb ram laptop). Finally I tried the alternate install disc. It was a better install experience anyway (more options). After many hours, I had my first Ubuntu install and I knew it was exactly what I wanted. I loved setting up my desktop. I loved the look of the latest Gnome. I loved being part of the Ubuntu community. I loved having the latest and greatest Dapper Drake. With some optimizations, applications ran really smooth. Everything was great except...

I couldn't keep a network connection even when wired into the NIC. I did some research and it looked like the NIC was busted and erroring all over the place with the default install kernel for 6.06. That's OK, I thought, I'll just get the wireless working and then update. The wireless (the infamous Broadcom 4306) was easy to install with Mepis with just one little blacklist tweak. Well, I followed every tutorial I could for Ubuntu. The hard part of trying to get the wireless working was that I didn't even have a wired connection. I could get some files off the install CD (like ndiswrapper), but I couldn't get all the tools needed very easily, but I thought I did everything. (Unfortunately, I was facing another network issue that I didn't even know about yet). After a day of trying everything I could, I gave up and started to install Ubuntu another laptop instead.

The other laptop installed easier. I even ran the updates using the NIC, but it took several tries because I was having network issues with this computer, too. Everything was slow and every connection would eventual die. I sometimes had DNS and sometimes didn't. I could sometimes hit the router and sometimes couldn't. The dumb thing was that this Dell laptop had a super common 3Com NIC. I knew it wasn't a rare kernel issue like what I was experiencing with the other computer. When I took the computer to my office, I had the same problems. Finally I found out that sometimes you had to turn off ipv6. I killed ipv6 and started to have some success with everything else (and I did a few tweaks to get a wireless card working). Yeah, I had my first installation. (I fixed a couple of other things, like the synaptic touch pad that isn't enabled in Dapper Drake clean installs for some bizarre reason, even though wacom tablets are?).

Back to the other laptop that was failing. I figured if I could get one laptop going, I could get the other one going, too. No luck, though. Even with my knowlege about how my routers were dying with the ipv6, I still couldn't get the wireless or the NIC to work. I decided to try a clean install. Still no luck because the network tools all seem to conflict with each other on Dapper Drake and if you're already having trouble, it's almost impossible to figure out why without the ability to be online and get things like network manager, etc. (I could probably do it without a connection now that I've had a few days with Ubuntu and I know exactly which fixes work in my situation, but that's a different story.) I decided to install Ubuntu 5.10 and then move to Dapper Drake. That worked. It got me past the kernel issue that killed my NIC. Then, after going through every How To on this forum for my wireless (again!), I finally got one of them to work (ndiswrapper with network manager for me, the firmware fix was very unstable). I had more difficulty turning off ipv6 again, though, as it started to mess up all my connections ... again. Eventually I had all network issues resolved. After all this, however, I went to plug in my printer and a USB drive and discovered that my USB, which was working a while ago, had died. I found on this forum that the latest updates have killed my USB on this laptop. (I found a quick fix for now until the next update.)

(This all makes me wonder if each new kernel or update will break something.)

For the happy ending. I worked through all of the issues, even resolving at least 3 concurrent networking show stoppers on just one laptop. I'm pleased as can be with the end result (although, if any of the devs read this, getting to this point is a lot easier today with Mepis).

My next post will be all warm and fuzzy because I really do love Ubuntu. I hope it isn't this hard for everyone to install. Dapper Drake has better sound support, updated Gnome, and cool things that I wouldn't want to live without, but it seems that for some of us the installation can be quite a  bit more difficult than distros like Mepis or Ubuntu 5.10.

---

### Post by paulmerchant on 2006-07-25
I thought I would add a few warm and fuzzy things. My scanners and printers work great (without huge installs). Actually setting up all of my work spaces and applications (except video editing and writing music, which I hope to be doing on Ubuntu sometime in the future) has been a piece of cake.

And to give Ubuntu devs their due, I've had nightmares with Windows installations, nightmares that would never go away like they often do with Ubuntu, because there's no ubuntuforums.org or because I would have to go out and buy an upgrade to my OS to solve the problem. I do have to give some kudos to the Mepis team, they've taken the latest Ubuntu core and have made it a whole lot easier to install and added better support for many, many networks and laptops.

Edit: If anyone reads this, sorry the above post was so long. Next post I'll try to be shorter (and maybe help someone through some of these current issues).

---

### Post by hellmet on 2006-07-26
the only bad hardware i had was the NIC card..
once I got rid of it..everything else started falling into place..
its really difficult without internet on the OS u are still learning!!

---

### Post by mkw87 on 2006-07-28
I'm yet to actually use Kino to edit some video, but I failed to get it to capture correctly.  However, I use a program called dvgrab, it works great, I plug my video camera in via firewire, power it up, open a terminal, and type dvgrab and it starts recording for me.  I was amazed when using it in windows that 1) the default cable was USB which provided me with horrible quality video 2) I had to manually watch stuff as I recorded it

Now I just have to do some editing and see if kino is really as great as everyone else says it is (In windows I use vdubmod and premier)

However, I am in the process of troubleshooting a Broadcom 4306 wireless card on my g/f's laptop, so wish me the best there :P
(I don't get discouraged easily).

---

### Post by paulmerchant on 2006-07-29
> **mkw87 said:**
> However, I am in the process of troubleshooting a Broadcom 4306 wireless card on my g/f's laptop, so wish me the best there :P
(I don't get discouraged easily).

With some persistance, you'll do fine with that wireless. I've configured dvgrab. Glad to hear it works good for you. I was hoping to use it along with the new Blender sequence editor to do some video editing (I already have a bit of Blender experience). Kino seems to lack a bit, but it should be fun to try, too. It's been a while since I've done that type of editing. I hear AviDemux can give us some of the functionality of VirtualDub and AviSynth. It'll probably be important to use since both Kino and Blender are a bit limited.

---

