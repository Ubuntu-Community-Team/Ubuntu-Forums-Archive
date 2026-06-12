---
title: "first linux experience"
date: 2007-12-29
forum: Testimonials &amp; Experiences
---

### Post by tbzep on 2007-12-29
I got a little bored recently so I downloaded the ubuntu 7.10 live ISO and the xubuntu alternate ISO and burned them a couple nights ago.  I fooled with the live boot to see if I might like playing with linux.  It was intriguing so I dug out some old components and threw together a PIII 550 system with 128mb ram and proceeded to load xubuntu on a reformatted drive.

It's pretty slow with such miniscule resources, but I've got it running. So far, I've been able to find out how to load conky and I've mixed and match code from various versions that I liked to get mine looking like I want.  I've loaded samba and whacked away at it to get it to share files and printers with the XP computers in the house. Now it's the official print server.  

It's not intuitive to me yet, but I can see that it will eventually be a much more customizable system than WinBlows.  What cool stuff should I try next?  Remember, I'm running super low on resources, so I usually type in a command or click the mouse and sit back and sip on my cold drink for a while until it gets done.  :biggrin:

Once I get fairly competent with it, I plan to switch or at least go to dual boot with the other computers. I'll just have to decide which flavor of ubuntu to use.

---

### Post by armandh on 2007-12-29
you will find 256 meg makes a HUGE difference

---

### Post by freebeer on 2007-12-29
Well, if your rig can handle a little more RAM, that's what I'd do to it next.  You should be able to pick up used ram for maybe $10-$20 and that'll give you the extra head-room the system needs.  After that you probably can do just about anything.

---

### Post by tbzep on 2007-12-29
I've got two sticks of 512mb ordered.  That will put me at the old board's max.  It felt weird ordering ram for a 66mhz FSB.  :lolflag:

---

### Post by Tristicus on 2007-12-29
Haha. I was (well, am still until I can get this other heap to start working) running on a P3 500mhz with 256mb (MAXED OUT I think lol) and it was running, but slow.

---

### Post by tbzep on 2007-12-30
I just installed dmidecode.  Looks like I have a 100mhz FSB instead of 66.  I have two 64mb sticks of PC100 in it now, so I expect (hope) it will handle the 512mb sticks.

I looked up the motherboard specs on the net and it claims it will handle 512mb PC133 sticks, but the dmidecode data shows a max of 256mb in each slot. :-k

---

### Post by tgalati4 on 2007-12-30
The motherboard chipset will determine the max RAM.  If it's an Intel 440BX then typically you are limited to 256 MB per slot.  These were common chipsets for PIII's of that era.

You may get away with one 512 stick.  The limitation has to do with the number of discrete memory chips on the RAM stick.  So yes, it may handle a 512 PC133, but perhaps only one of them.  Only testing will tell.  Regardless, set up some swap space on your harddisk and you will do OK with 512 MB.

---

### Post by tbzep on 2007-12-30
I've now had it running all weekend.  The biggest hurdle was tweaking the printer to be accessible by Windows boxes due to the user/password.  Thanks to the wealth of info on the forum, I was able to change a single word in the smb.conf file to open it up.  

I've been poking around looking at ways to make things a little easier to get to, and fooling with themes.  From the looks of the available software, I'll be digging through that stuff for weeks to see what I might like to install.  If not for the rest of my family, and having to use MS products at work, I don't think I'd care if I ever saw a MS product again.

---

### Post by ukripper on 2007-12-31
To run xubuntu/*buntu properly, you do need 256MB RAM atleast. Consult to your motherboard manual first before you do anything as older hardware were restricted to 128MB support only

---

### Post by tbzep on 2007-12-31
I'm looking foward to seeing how the memory improves performance.  Still waiting on that little brown truck.

Right now, I'm reading up on installing ubuntu as a dual boot system on the main desktop and laptop computers.  I can't get rid of Windows because of the wife and kids, but I'm ready to jump ship, personally.

---

### Post by RavUn on 2007-12-31
I'm in the same boat as you... I have an old PIII that my dad brought home from work.  I was going to experiment with the ubuntu LAMP server but it took too much time learning only on CLI while I was working and schooling.  Once finals were over I decided to just throw a desktop on there and have Ubuntu 7.10 right now.

I got the conky setup and the terminal as the background and a pretty cool theme... I just don't know what else to do.  It's too slow to do much (can't use compiz or anything) but at least it has 384 MB RAM.  Firefox is the only thing that slows it down.  

I want to setup my main PC to dual-boot and I've got another PC that I've rebuilt with 1 GB SDRAM and I think the  Sempron 3000+ processor (don't remember now!).  I want to have fun with that, just have to buy the power supply.  

Right now I'm just trying to find stuff to do in the future on my faster machines.  Maybe I'll get some emulators on this slow one for the time being and just play games.

---

### Post by sloggerkhan on 2007-12-31
If firefox is what slows down the thing, why not try a lightweight browser?
The only one I can think of at the moment is dillo, but there are a number of them designed for low-resource computers.

If you like tinkering, maybe even check out something like puppy linux or damn small linux, they might at least give you some software ideas for what to run on low end machines.

---

### Post by armandh on 2008-01-01
I have a 800 P-III 256 meg mem 100 fsb that plays dvds without apparent skip [decent graphics card.] where a 133 fsb 766mhz  810i on board video sucks with shared 256meg it is just finding that sweet spot.

---

