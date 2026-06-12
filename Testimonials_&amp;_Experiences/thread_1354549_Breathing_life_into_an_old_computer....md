---
title: "Breathing life into an old computer..."
date: 2009-12-14
forum: Testimonials &amp; Experiences
---

### Post by rmccutchan on 2009-12-14
I am writing this post from an OLD computer I found on the curb at a neighbors house after they moved out.  It's an old Compaq Presario with the oval shaped face.

I saw a computer and some monitors sitting in front of the neighbors house in the trash this weekend, so I thought there might be some parts I could use from it.  If not, I know someone who sends old computers to a recycling facility and I thought it would be better than letting it go to the landfill.

So I dusted off the inside of the box and hooked everything up, and lo and behold, it groaned to life!  It had windows 98 on it, and someone left a bunch of files on it.  So I thought it would be a good idea to get rid of everything and start over (with Ubuntu, naturally!)

The processor is a Celeron (Coppermine), which I have not heard of, and it has a 15 gig hd and 312 gigs of ram.

I installed Ubuntu 8.04 because I thought it might be a little smaller that 9.10.

Now, I will admit that it is really slow, but that was to be expected.  But, it is a predictable slow.  Each time I click on something, it takes just a couple of seconds before something happens, but it is very deliberate and predictable.  I have a laptop for work with a dual core processor and windows xp, and sometimes it isn't any faster than this old machine.

I am watching the system monitor while I write this post, and it is using 62% of the ram right now, and 50-100% of the processor.  Things are a little choppy, but steady.  It has been up and running for about 48 hours and is just ticking away like clockwork, and I still have 2 desktops to work from!

I would not want to try to do a lot of serious work with this thing, but it is very usable for someone who just needs to check email and do some word processing or spreadsheets.

I also have Puppy Linux on a disk, and it actually runs fairly quickly on this machine.

I only recently discovered Linux this summer, so I wanted to chime in on my appreciation.

---

### Post by running_rabbit07 on 2009-12-14
Now that brings a new meaning to free. That is awesome.

---

### Post by x33a on 2009-12-14
> **rmccutchan said:**
> it has a 15 gig hd and 312 **gigs** of ram.

must be a supercomputer :P.

you could try running slitaz on it.

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by armandh on 2009-12-14
a trip to the hp/compaq site for the manual pdf. and you will find how much and what kind of memory it will support.

max this out as there should be some used cheap about
[from those same recycle guys]

any thing under 512mb is a speed problem [IMHO]

if it has onboard video no room for help here
except the shared mem again
but if it has an AGP card a better [used] card will help 

for a year I ran the family room flat screen @ 1080p from an old 933 P-III copermine with 512 meg and a 128 mg video card DVI out

---

### Post by Bartender on 2009-12-14
The simple act of running System Monitor seems to add quite a bit of overhead.

I've tried this on dozens of PC's and it's always the same.  The older the PC the wider the discrepancy.

Instead of running System Monitor, open a terminal and type 

```
top
```

You'll see significantly lower CPU and MEM usage than System Monitor reports.

I strongly agree with other posters - if you can stuff more RAM into that old rig you'll see an appreciable improvement.  Standard Ubuntu install uses about 300 to 350 MB of RAM just idling.  That doesn't leave you with much.

Or try some of the lighter-weight distros.

Even if you do nothing else to the old PC, it's a great story.  Poor little Compaq, kicked to the curb and destined for the dirt nap, scooped up and given a new home by a Linux user.

---

### Post by terry_gardener on 2009-12-14
if you want to stay with ubuntu. 

then i would suggest installing the minimal cd of ubuntu 9.10 and then install lubuntu-desktop.

sudo apt-get install lubuntu-desktop 

this runs the lxde desktop and it should be alot better.

i have tried this using Virtualbox using 256mb ram as i was going to use it for neighbours acer aspire 3000 laptop. 

lxde is very lightweight and fast. 

this is my recommendation

---

### Post by tgalati4 on 2009-12-14
Or, turn it into a server.

---

### Post by ukripper on 2009-12-14
i would recommend installing lxde desktop on your current ubuntu install. LXDE is in repos all you have to do is run this command:
```
sudo apt-get install lxde
```

once installed. Just logout and at sessions select LXDE and off you go! goodluck

---

### Post by Thocrun on 2009-12-14
> **tgalati4 said:**
> Or, turn it into a server.
I actually have an old compaq presario running ubuntu server 9.04
I use it as a ubuntu file server and print, since I can't talk my granparents into buying me a domain name lol. is it a compaq presario 5000 US?, I bet I could find some documentation on it if you want it. (from hp.com)

---

### Post by Marvin666 on 2009-12-14
[DSL]("http://www.damnsmalllinux.org/") might run pretty fast on it.
The os, and programs need only 50mb, and idling it needs 8mb of ram. You can run almost any program with 128mb of ram, boot from windows, and run from a compact flash drive, or usb flash drive.

---

### Post by rmccutchan on 2009-12-15
I like the idea of turning it into a print server.  My wife has a PC with Vista (she won't let me put Ubuntu on it.  We are both taking classes that require us to use Windows, so I gotta keep Vista), and I obviously have nothing but Ubuntu on mine.  But we just have one printer.

This is uncharted territory for me, but there is only one way to learn:  roll up my sleeves and dig in!

I have a Vonage router, and from that I plugged in a Lynksys wireless router (for my work laptop).  I would like to set up a network with this using the old timer as a print server.  So if anybody has a good tutorial for a newbie, I would greatly appreciate it.

---

### Post by ukripper on 2009-12-15
> **rmccutchan said:**
> I like the idea of turning it into a print server.  My wife has a PC with Vista (she won't let me put Ubuntu on it.  We are both taking classes that require us to use Windows, so I gotta keep Vista), and I obviously have nothing but Ubuntu on mine.  But we just have one printer.

This is uncharted territory for me, but there is only one way to learn:  roll up my sleeves and dig in!

I have a Vonage router, and from that I plugged in a Lynksys wireless router (for my work laptop).  I would like to set up a network with this using the old timer as a print server.  So if anybody has a good tutorial for a newbie, I would greatly appreciate it.

It looks overkill to me for just having a print server with your current setup. But looking at learning perspective, i would say go ahead and setup a server not just a print server but a whole LAMP stack running web, file, print and email servers for the starters.

---

### Post by markwiering on 2013-01-31
Ubuntu is a heavy operating system which will only run smoothly on new computers. If you really want to have a Linux-distribution on that computer, I recommend you to use Puppy Linux.

Personally, I think Windows 98, the old operating system of that computer, is ideal. It's more stable than Windows 95 and Windows ME, it's user friendly, lightweight and compatible with almost all software from that time. You don't really need a Linux-distribution to be able to use that computer: it's just optional.

---

### Post by papibe on 2013-01-31
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

