---
title: "[SOLVED] Home Server(broken laptop) help?"
date: 2008-09-02
forum: Server Platforms
---

### Post by pBeseda on 2008-09-02
Ok, I have thought this through, checked out the topics around this forum, done a little research. I think what I want to do is possible, and it's probably been asked before(plus or minus some details). I'm relatively new to Ubuntu and Linux systems. I have a working knowledge of the CLI but nothing beyond that.

Here's what I'm after: I want to set up a home server that can be controlled through a laptop(over a wireless network).

Here are the details and obstacles: I have a great laptop that I want to use as the controller. I run Ubuntu 8.04, and love it. I'll call this "laptop"

I have a second laptop, a few years older with a broken screen. The drive, motherboard etc. works fine, but the screen is broken. Can't see anything at all. It can be attached to an external monitor(that I dont have, but would really like to get my hands on) and I've found it to be pretty functional. I found out that Ubuntu is indeed installed on this old laptop; Ubuntu 8.04. I"ll call this "server"

I have an external hard drive(250gb) that holds my music, photos, and movies. I have a stereo system that will be plugged into the server to play music. If possible, the server will also be hooked up to a video output to my TV(it's an old TV, might not work)

I want to be able to do a number of things:
1. My laptop must remain portable. Not plugged into anything(except power). I want to be able to do this all over my wireless network.

2. Control the server from my laptop(play music, movies, display photos etc)(VNC, ssh, whatever, I'm not sure what works best)

3. Add or remove music, movies and photos from the hard drive connected to the server using my laptop. (I'll be using it to back up my photos)

4. Not have to touch the server(except to turn it on and off). This may include installation of software.

5. Figure out how to use the IR remote that came with my laptop(HP Pavilion dv6000)



If you can help me with a solution to any of these requests, or engineer an entire system, I'd love to hear(and try) your ideas. If you could so much as point me in the right direction, I would be stoked. Thanks so much for helping me with this. This community is great and I know I can expect some great help and to learn a lot from everyone.

Note: The screen is not "broken". I found it works for 10-30 seconds upon booting. It cuts out and the back lights are off after that. Not sure why that is. It's probably the inverter, I don't really want to get it fixed.

I'm ready to put a lot of work into this to learn a lot and make my system functional and seemless if possible. Also, not to spend money.

Things I'm thinking/researching involve an unattended install of a custom server distro(ssh or VNC ready to go), automatic backups of my photos(I'm a photographer),

---

### Post by lazyart on 2008-09-02
So, the broken laptop has ubuntu on it?

Pop out the hard drive from the broken laptop and put it in your working laptop.  Log into Ubuntu, install openssh-server and enable desktop sharing.  Turn off desktop effects (VNC doesn't like it). Give it a static IP address so that you will have a way to find it on the network.

You might want to look into NoMachine.  I just put this on my desktop and it's nice.  Outperforms VNC a million times over and unlike VNC you don't have to be already logged in to use it.

If you're going to use VNC, set the broken laptop to autologin.  Once it's set, put the hard drive back into the broken unit and fire it up.  Put your original hd back into the working laptop.  Fire up Terminal Server Client, set it to VNC and enter the ip address you set for the other machine.  Your deskto should appear and you can get down to business.  If something is not going right, you can always SSH to it and investigate.

Good luck!

---

### Post by pBeseda on 2008-09-02
That would be great. The hard drive switch doesn't seem that easy. I popped em both out no problem, the old one doesn't seem to be able to connect to the new laptop, maybe I'm just not educated in hard drive connectivity to make it work. I can take pictures if you need me to.

I'll definitely look into NoMachine. Having used VNC before, I'd definitely like something better. Thanks for the advice.

Anyone else have ideas? Is there a way to get onto the broken laptop without touching it? as far as I can tell it doesn't have ssh, and desktop sharing is disabled.

---

### Post by Smandola on 2008-09-03
Unfortunately you need to see what you are doing in order to get your server setup/configured.  If you have no access to an external monitor, do one of your friends have a laptop that is similar to your server ?  and would they mind you pulling the hard drive out.  

Another suggestion is to go to your local internet cafe, and ask them to use on of their external monitors.  They may even be nice enough to let you use it for free.

---

### Post by eldragon on 2008-09-03
blind folded hit ctrl-alt-f1 on the server (asuming youve got linux already installed)...and enter your username/password
then do 
sudo apt-get install openssh-server , type password and type a couple of Ys to be sure :D

you should be able to login to the laptop's ip with ssh now and continue the tweaking through there.


good luck

---

### Post by lazyart on 2008-09-03
to do the hard drive thing you might have take the mounting plastic and such and put it on the other one for it to fit.  The hard drive is a standard part in the laptop, but the mounting hardware may not be.  Some drives will have a black plastic "blade" over the pin connectors that you can simply pull off.

When pulling things off and putting them on, notice the pins on the hard drive.  There will be a long group of them, then a little gap and a group of 4 pins off to one side.  Use that to orient things correctly.

---

### Post by pBeseda on 2008-09-03
You guys are awesome. I'm trying the hard drive things again right now, if that doesn't work I'll try the blind openssh install. If that doesn't work, I bet the computer commons at my school will let me use one of their monitors.

---

### Post by pBeseda on 2008-09-03
Ok, update. The hard drives still seem incompatible. I took off the plastic blade plug thingy from the new one but there was no way to connect it to the old one. Maybe I'm still missing something.

I tried to install openssh-server on the server but I don't think it worked. I'm still getting "connection refused".

In search of an external monitor...

---

### Post by pBeseda on 2008-09-03
Ok, so I had an idea. It worked. So far. Someone might be able to shed light on this.

I pulled apart the laptop, unplugged the inverter from the LCD screen. Booted it up.

Waited until it was booted, ctl + alt+ F1

plugged back in the inverter, screen works...

---

### Post by pBeseda on 2008-09-04
It was like a miracle or something. I got the screen to work for long enough to set up the openssh and even desktop sharing. Now I'm set. Got it plugged into my stereo and its cranking tunes. Controlled by nxclient from my laptop. all the while slaving away F@H and some number crunching from school. Thanks everyone.

---

### Post by lazyart on 2008-09-04
Fantastic!

---

