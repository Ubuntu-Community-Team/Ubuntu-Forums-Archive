---
title: "Migrating From Mandriva 2006"
date: 2006-05-15
forum: The Cafe
---

### Post by ArchStanton on 2006-05-15
Here's a bit of background on what I'm doing.

A year ago I bought a new computer, and gave my older computer to my wife to use. This computer is about 6 years old (P3 800, 384MB, ATI Rage Pro). Windows 98 was completely disabled due to browser hijacks and the like, so I thought I would give Linux a try. After some research I went with Mandriva 2005 and KDE. I thought it worked quite well. We recently moved some stuff around the house and I installed a wireless router and usb adapter. I couldn't get them to work with 2005, so I upgraded the system to Mandriva 2006. I managed to get it working with the addition of some other piece of software which I can't recall the name of. Since the upgrade to 2006, the video is very glitchy, and I can't get the sound to work. So here are my questions . . .

How easy is it to migrate over to Kubuntu?
Can I just install overtop of Mandriva or will I need to set up from scratch?
What is the wireless networking support like?
Should I stick with KDE and use Kubuntu, or use Ubuntu?

Anything else I should consider?

---

### Post by ComplexNumber on 2006-05-15
> so I upgraded the system to Mandriva 2006. you're a more daring man than me. 


>  Should I stick with KDE and use Kubuntu, or use Ubuntu? go with ubuntu. its a lot more stable than kubuntu, and it will be much easier for you in the long run.

---

### Post by ArchStanton on 2006-05-15
[QUOTE=ComplexNumber]you're a more daring man than me.[/QUOTE]

hmmm . . . that bad huh?

Straight up Ubuntu it is!.

ok, So I remembered the router/adapter I got. It's a Blitzz. They are out of business. This is the software I used to get the adapter running: [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)
They only offer a 30 day trial. so I'm gonna have to get a new adapter, or find something else that will get it to work. It also seems to only work with Breezy, and I was planning on using Dapper Drake.

---

### Post by ComplexNumber on 2006-05-15
they may have sorted out the stability problems with mandriva 2006 by now, but it seems like my less than pleasent experienes with it are the rule rather than the exception. 

dapper drake should be available some time soon from shipit on the ubuntu website, so that may be an option for you. otherwise, ubuntu breezy is very stable, but the software isn't as up to date.

---

### Post by ArchStanton on 2006-05-15
I downloaded and ran the Dapper Live CD. I'm at work, so it is yet to be seen if it will work on my wifes computer, but these are my thoughts so far . . .

Wow. Why didn't I go with Ubuntu in the first place? Probably because I had never heard of it.

---

### Post by mips on 2006-05-15
Whats wrong with Kubuntu ? Stable as anyting else.

You might wanna try a lighter DM like xfce (Xubuntu) on a lower spec machine, will make it fly.

---

### Post by ShanghaiTeej on 2006-05-15
If you have enough hard drive space, install ubuntu (just because, in my experience at least,  it is a little more stable), then install xubuntu-desktop and kubuntu-desktop and try them all.

---

### Post by ArchStanton on 2006-05-16
I think I may need to post this in another forum now.

Ubuntu didn't work. Not at all. Zero, zilch. :(

Trying to boot up the live cd, and it crashed. First it came up with a series of errors that looked like there were bad sectors on the hard drive. I booted Mandriva and chaecked the hardrive, and it seems to have found errors (it flashed something yellow text and then rebooted and scanned again). So it seems that it fixed the errors. This time it got to the point of "Loading CD User Ubuntu" and then went to a blank screen. Left it there for about 10 minutes and nothing happened. So maybe there is a bigger problem with the hard drive? I disabled all of the hard drives in CMOS and tried to boot the live cd straight from RAM, but the same problem. I turned off the printer and disconnected the USB wireless adapter and tried again, just to see, and the same problem. I tried one more time with everything back on, and recieved the same errors about the hdd.

I am going to try breezy live tonight. Perhaps Dapper Drake is just not stable enough for an old machine. Or is it that it designed for newer machines and Xubuntu would work best? I find KDE to be fairly slow at times, especially since the upgrade (or should I say downgrade) to Mandriva 2006.

These are the things the computer is used for . . .
Surfing the net . . . (especially flash, because my 4 year old is addicted to barbie.com)
Instant Messaging
Playing Music
Watching DVD's
Open Office
Checking Email

Thats it, nothing else.

I'm just gonna download and burn them all today, and then I can boot off the live cd's until one works for me.

---

### Post by Lord Illidan on 2006-05-16
Did you burn the CD well?
4x to 6x seems the best speed.

Also, if all else fails, Beatrix Linux might be a good idea for you... suits your needs. *[http://www.watsky.net/](http://www.watsky.net/)*

---

### Post by ArchStanton on 2006-05-16
I burned at the max speed, I'm far to impatient. :)

However, I ran the live cd on my computer here at work with no problems. I will slow it down in the future just to be sure.

Dl'ing Beatrix. Thansk for the advice. These one cd live distro's are nice becuase you can try before you bite it installing an os that won't work on your computer.

---

### Post by ArchStanton on 2006-05-16
whoops, double post. Sorry.

---

### Post by Klaidas on 2006-05-17
Migrating to (K)Ubuntu will be VERY easy. I remember I had mandriva once. Then I tried Ubuntu. Heh, deleted mandriva immediately after that! :mrgreen:

---

### Post by ArchStanton on 2006-05-17
Well, it hasn't been so easy for me. I think I need to start a technical support thread . . .

---

### Post by ArchStanton on 2006-05-22
OK, so I have almost fully completed the transition. Lord Illidan was right, I re-burned the cd at 4x and everything worked fine. Had to do some fiddleing with the sound card, but it wasn't working in mandrake at all.

My last problem is that there are 2 harddrives in the system that I can't access. They are both windows drives. I get this message when I try to access them from the "Computer" file browser:

Unable to mount the selected volume.
error: device /dev/hdb1 is not removable
error: could not execute pmount

I checked out System/Administration/Disks, but nothing in there seemed to be of any use. Any suggestions?

---

