---
title: "so i have a pc with no graphics card...."
date: 2009-12-31
forum: The Cafe
---

### Post by nerdy_kid on 2009-12-31
and i would like to use it as a server.  So i was wondering if there would be a way to install ubuntu so that a openssh server was running directly after the install; as i have no screen :)  This is assuming of course that the LiveCD has an openssh server running...  which i havnt confirmed.
thanks!

---

### Post by kevinatkins on 2009-12-31
Ubuntu desktop definitely does not include any ssh server as part of the default install; I'm not sure about the server version - either way though, it's only an apt-get away.. I'd be inclined to pop a gfx card in the machine temporarily, do the installation and get everything setup then remove card and run headless from then on..

---

### Post by nerdy_kid on 2009-12-31
i would pop the graphics card in but i dont have one and the pc is old so i dont want to spend ANY money on it LOL
never knew apt-get could be so far away :(

if i manage to get ubuntu even installed, i could just take the HD out and add a new boot script that installs openssh?

how would i get it installed though....

---

### Post by markp1989 on 2009-12-31
> **nerdy_kid said:**
> i would pop the graphics card in but i dont have one and the pc is old so i dont want to spend ANY money on it LOL
never knew apt-get could be so far away :(

if i manage to get ubuntu even installed, i could just take the HD out and add a new boot script that installs openssh?

how would i get it installed though....

after ssh is installed it will start at boot. 

you could put the hard drive in a differnet pc install it , then put it back.

if the pc will post with out a gfx card mite be a problem

---

### Post by nerdy_kid on 2009-12-31
> **markp1989 said:**
> after ssh is installed it will start at boot. 

you could put the hard drive in a differnet pc install it , then put it back.

if the pc will post with out a gfx card mite be a problem

wouldnt installing it on the HD using a seperate pc mess up the install a lot?  or do i just have to ```

sudo dpkg-reconfigure --all

```

once i boot it up in the screenless pc

> 
after ssh is installed it will start at boot.

right but i meant create a one-time script to use apt-get to install openssh, but never mind, that idea is stupid.

---

### Post by forrestcupp on 2009-12-31
How are you going to do a sudo dpkg-reconfigure --all if you can't see anything you're doing?

---

### Post by nerdy_kid on 2009-12-31
well right, that would be the issue.  I was going use a different pc to install ubuntu (server probaly) on the HD set up an openssh server, then move the HD back to the initial pc.  Then once it had booted, and i could login via ssh, i could do an sudo dpkg-reconfigure --all.  I am going to try this as soon as i get a chance.

---

### Post by FuturePilot on 2009-12-31
> **nerdy_kid said:**
> wouldnt installing it on the HD using a seperate pc mess up the install a lot?  or do i just have to ```

sudo dpkg-reconfigure --all

```


No. I've moved server installs from one computer into another without any problem. The only thing you'll need to do is delete /etc/udev/rules.d/70-persistent-net.rules or your network won't work. It will get recreated on the next boot with the correct information for the network card.

---

### Post by CharlesA on 2009-12-31
> **FuturePilot said:**
> No. I've moved server installs from one computer into another without any problem. The only thing you'll need to do is delete /etc/udev/rules.d/70-persistent-net.rules or your network won't work. It will get recreated on the next boot with the correct information for the network card.

That's good to know.

Thanks!

I'd do this if the OP doesn't want to spend any more money on the machine.

---

### Post by MaxIBoy on 2009-12-31
Try a custom installer CD with simple-CDD, available for Debian and Ubuntu. Make sure sshd is installed on your custom CD. Add a script to set up the network connection. You can even set up Mutt on the CD and have it send you an email with the output of "ifconfig," so you know what address to SSH into. Obviously test this all with Qemu or something before you waste a CD...
[http://manpages.ubuntu.com/manpages/jaunty/man1/simple-cdd.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/simple-cdd.1.html)
[http://wiki.debian.org/Simple-CDD/Howto](http://wiki.debian.org/Simple-CDD/Howto)

---

### Post by ssam on 2009-12-31
one of these may work for you
[https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations](https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations)

i have installed ubuntu onto a beagleboard with no monitor. by using sd card image, and a serial link.

---

### Post by TheOrangePeanut on 2009-12-31
Try this.  Pop the CD in the machine, and boot it, and at the same time, boot the install in a virtual machine.  Then you will know exactly what is happening and what you should be doing.  Do just enough to get ssh installed, and there you go.

---

### Post by handy on 2009-12-31
You should be able to get a PCI graphics card from the rubbish dump/recyclers for $1-.

---

### Post by nerdy_kid on 2009-12-31
thanks guys! VERY useful replies...will post my luck as soon as i get a chance!

---

### Post by dragos240 on 2009-12-31
You could get an ssh server running during an arch install. You can use ssh while using another computer. You could also configure the server to connect to your network and then start ssh. The arch install is all text. No need for a graphics card.

---

### Post by Exodist on 2009-12-31
> **nerdy_kid said:**
> and i would like to use it as a server.  So i was wondering if there would be a way to install ubuntu so that a openssh server was running directly after the install; as i have no screen :)  This is assuming of course that the LiveCD has an openssh server running...  which i havnt confirmed.
thanks!
Call your local PC shop and see if they got a old used pci or agp card laying arudn with dust on it for $5. If you buy something else from them that you need they may even give you the card.

---

### Post by redrac on 2009-12-31
Don't know of any motherboards that will boot without any video card.  Will get an error beep about no video. Even rack servers usually have onboard rage pro cards.

---

### Post by Exodist on 2009-12-31
> **redrac said:**
> Don't know of any motherboards that will boot without any video card.  Will get an error beep about no video. Even rack servers usually have onboard rage pro cards.
ditto

---

### Post by nerdy_kid on 2010-01-04
ok, so i removed the HD, installed 9.10: everything went perfectly.  Downloaded openssh using apt-get -d, copied it on the HD and rebooted into it.  Installed the server, and verified that it worked.  Shut down....

Popped the HD back into the gfx-less PC and turned it on.  I get
"beeeep beep beep" out of the system beeper, then nothing for bout a minute, then "beep beep".  Then it repeats.  So I took the HD to another machine, and tested it; no error exept a note about the swap not mounting, and there is a /dev/sdb when there is no other HD on the system.


soooo that'd be be the gfx card??? I guess ill have to spend a buck or two.........

---

### Post by Dr. C on 2010-01-04
Sounds like the motherboard will not boot without a video card. I would go the junk AGP, PCI or even ISA (if the PC is that old) video card route.

---

### Post by CharlesA on 2010-01-04
Stupid question, but did it boot before you removed the hard drive?

If it didn't, then it probably won't boot without a video card.

---

### Post by nerdy_kid on 2010-01-04
> **CharlesA said:**
> Stupid question, but did it boot before you removed the hard drive?

If it didn't, then it probably won't boot without a video card.

um idk, first thing i did was format the HD... probably not, it looks like the motherboard needs a gfx card, so ill have to go and get an ancient one that couldnt handle a 3d cube for a couple of bucks

---

### Post by nerdy_kid on 2010-01-04
thanks for all your help, everyone!
:D

---

### Post by The Real Dave on 2010-01-04
Ya, I'm going to second what's being said, sounds like the mobo is halting because it can't find a gfx card. Then again, it could be halting because its got no keyboard or similar stupid error ;) Find yourself a cheap GFX card, PCI or AGP, whatever the mobo will take and you can find cheapest (try eBay), all it needs to do is get to the BIOS. 

Once you get there, take a while to trawl through it and try to find the section about halting on errors, should be with the boot stuff. Set it to never halt or whatever it says, and you should be good to go :) 

Just out of curiosity, what kind PC is this? Specs / Pic please? :) I love seeing old hardware being reused, I've  a bucket of old PCs, most old and underpowered. My second server is a 451Mhz PIII :) 128Mb of PC-100 RAM and using only 30Mbs of it :) Specs and Pics [here]("http://linuxexpresso.wordpress.com/hardware/").

---

### Post by nerdy_kid on 2010-01-04
> **The Real Dave said:**
> Ya, I'm going to second what's being said, sounds like the mobo is halting because it can't find a gfx card. Then again, it could be halting because its got no keyboard or similar stupid error ;) Find yourself a cheap GFX card, PCI or AGP, whatever the mobo will take and you can find cheapest (try eBay), all it needs to do is get to the BIOS. 

Once you get there, take a while to trawl through it and try to find the section about halting on errors, should be with the boot stuff. Set it to never halt or whatever it says, and you should be good to go :) 

Just out of curiosity, what kind PC is this? Specs / Pic please? :) I love seeing old hardware being reused, I've  a bucket of old PCs, most old and underpowered. My second server is a 451Mhz PIII :) 128Mb of PC-100 RAM and using only 30Mbs of it :) Specs and Pics [here]("http://linuxexpresso.wordpress.com/hardware/").

I accualy dont know all the specs, as it was given to me by a friend, and as yet i have been able to boot it :S

Its a
IBM type 6349
Pentium 4
both RAM slots are filled, so im guessing ~512 mb of RAM (it was a winXP, 512 was average back then i think...)
has a floppy, CDrom, 20Gb HD.
um....IBM motherboard also.....
all for now; here are the pics: (sorry for the low-rez, my Sony Cybershot is lacking a memory card right now -- i get 11mb of internal mem thats it)



I also have a few pentium 2 (hehehe) pcs that im gonna attack next.

My dad still uses a HP packlard *360mhz pc with 4mb video RAM* (going off memory there) still runs....:lolflag:

---

### Post by nerdy_kid on 2010-01-04
nice site, btw.  gonna be visiting that every now and then ;)

---

### Post by The Real Dave on 2010-01-04
> **nerdy_kid said:**
> I accualy dont know all the specs, as it was given to me by a friend, and as yet i have been able to boot it :S

Its a
IBM type 6349
Pentium 4
both RAM slots are filled, so im guessing ~512 mb of RAM (it was a winXP, 512 was average back then i think...)
has a floppy, CDrom, 20Gb HD.
um....IBM motherboard also.....
all for now; here are the pics: (sorry for the low-rez, my Sony Cybershot is lacking a memory card right now -- i get 11mb of internal mem thats it)



I also have a few pentium 2 (hehehe) pcs that im gonna attack next.

My dad still uses a HP packlard *360mhz pc with 4mb video RAM* (going off memory there) still runs....:lolflag:

Nice! Thats alot more powerful than most of the PCs I work with, I've so many damn old Celeron chips, from 200-2400Mhz :lolflag: Looks like it'll make a great server.

Once piece of advice, give it a good cleaning. Take everything you can out, buy yourself an airduster, and clean as much as possible, inside the PSU, in heatsinks, take some kitchen towel to the case, the works. You'd be amazed how much more life you can eek out of hardware by cleaning it, and keeping it someway clean. A &#8364;5 airduster can save you a lot of hassle. Use it with a hoover (beware of static) to get rid of that dust, and it'll be like a new PC. That and the high possibility of you Pentium IV chip featuring thermal-throttling, once it gets over a certain temp it throttles its speed to  protect itself. If you keep it clean, it'll stay cool and run fast :)

> nice site, btw. gonna be visiting that every now and then 

Thank you :D I update it fairly often. I've a few things lined up so stay tuned ;)

---

### Post by nerdy_kid on 2010-01-04
nah, i use an air compressor instead!  (with the pressure turned way down of course).  Currently my other desktop (jaunty, 3.2ghz) is running apache for my own use (i dont know HTML so its basicly just a file server), and i have to clean it every 4 months or so as its always on.  I cant believe how much crap i blow out of it.  Cant even see in front of me due to dust LOL

---

### Post by RiceMonster on 2010-01-04
> **FuturePilot said:**
> No. I've moved server installs from one computer into another without any problem. The only thing you'll need to do is delete /etc/udev/rules.d/70-persistent-net.rules or your network won't work. It will get recreated on the next boot with the correct information for the network card.

Yep, udev should check your hardware and load in the correct modules anyway.

---

### Post by pricetech on 2010-01-04
I see 3 PCI and one AGP slot.  If you were closer I'd tell you stop by and pick one up.  I have unused cards here I need to get rid of.

In addition to cleaning, you should cover the expansion slots in the case to keep from interfering with proper airflow.  If you don't have the blanks, duck tape works great.

---

### Post by The Real Dave on 2010-01-04
> **nerdy_kid said:**
> nah, i use an air compressor instead!  (with the pressure turned way down of course).  Currently my other desktop (jaunty, 3.2ghz) is running apache for my own use (i dont know HTML so its basicly just a file server), and i have to clean it every 4 months or so as its always on.  I cant believe how much crap i blow out of it.  Cant even see in front of me due to dust LOL

I clean my main computer every month, and it doesn't even run 24/7. Then again, as you can see on my site, its got quite a few large fans, all of which run flat out. Its a 3Ghz Pentium IV but when its clean it stays at 35C when fully maxed (Folding@Home). When the temp gets to ~40C its time to clean, usually a month or so :) :lolflag:

BTW, just an idea, if that computer is already setup to boot a CD first, you could just download [FreeNAS]("http://freenas.org/freenas") and boot it up. You wouldn't need to configure anything on the server side, it's all done through a WebGUI. You wouldn't be able to install it to the HDD, but you can run it Live, boot the disk, load to RAM and grab config from a USB or floppy. FreeNAS will probably do everything you need, and will scream on that thing. That is considering though that the computer is set to boot the CD first. If it is, it could work out well. The only thing is that on the first boot you'll have to enter your router to find the server's IP, you usually set up a static IP on the server side, but you can do it just as easily though the WebGUI. 

I think it might just do the job for you :)

---

### Post by Dr Belka on 2010-01-04
you should customize the live cd you are using to include ssh by default

---

