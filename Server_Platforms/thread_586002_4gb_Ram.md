---
title: "4gb Ram?"
date: 2007-10-21
forum: Server Platforms
---

### Post by trmentry on 2007-10-21
I'm planning on rebuilding my server and installing it with 4g ram.   I know with 32bit OS that Ubuntu will only use 4g.  WIll it see the 4g and not make any swap, or will it still create a bit of swap and I not get the full 4g?

The reason is, my server currently has 1g.  And when I run more than 1 virtual machine with vmware on it, I tend to swap.  Not all that much for me to really care, but just would rather things stay in ram.

Things I currently run.
o Apache2 w/ PHP
o MySQL 5
o Sendmail
o Vmware Server
o Teamspeak
o sabnzbd or hellanzb
o finch (pidgin for ncurses)
o midnight commander from time to time

I'm not against installing a 64bit version as long as all my programs/services will work.  

TIA

---

### Post by conjur3r on 2007-10-22
On my system with 4G, it only sees about 3.2G of ram.  It is the same when I boot into Windows too.  I just tried 64bits over the weekend and it sees all 4G of it but have reverted back to 32bits due to incompatibilities to some of the important software I needed.

It's always good practice to create a swap whether or not it will need it.  There is more chance that it will be used sometime in the future if not right away.

---

### Post by /etc/init.d/ on 2007-10-22
As the other poster said, 32-bit will not see more than 3.2GB of RAM.  If you're getting some swapping with 1 GB, 3.2 GB will mean you probably will see little or no swapping, but the other ~800MB of RAM will be  wasted unless you use 64-bit.

---

### Post by kerry_s on 2007-10-22
> **trmentry said:**
> I'm planning on rebuilding my server and installing it with 4g ram.   I know with 32bit OS that Ubuntu will only use 4g.  WIll it see the 4g and not make any swap, or will it still create a bit of swap and I not get the full 4g?

The reason is, my server currently has 1g.  And when I run more than 1 virtual machine with vmware on it, I tend to swap.  Not all that much for me to really care, but just would rather things stay in ram.

Things I currently run.
o Apache2 w/ PHP
o MySQL 5
o Sendmail
o Vmware Server
o Teamspeak
o sabnzbd or hellanzb
o finch (pidgin for ncurses)
o midnight commander from time to time

I'm not against installing a 64bit version as long as all my programs/services will work.  

TIA

you can use a program called swapd(apt-get install swapd) in place of a swap partion and force your system to use ram till more is needed then it will create and use a swap file, then delete it when no longer used.

---

### Post by zorkerz on 2007-10-22
so my computer has 4 gigs of ram in it. Im running 32bit gutsy. It only recognizes about 2.95 gigs of ram. Is there a way to get it up closer to 3.2 or am I possibly at my max already?

And is there anywhere I can find out more about the swapp partition. Is there any point in me having one if I have enough ram?

thanks for your knowledge

---

### Post by jrharvey on 2007-10-22
If you are going to run virtual machines then I would definitely recommend going 64 bit. I tried virtual box on 32 and 64 bit and believe me that you want all 4G of that ram to be used. 64 bit Ubuntu runs virtual machines much faster for me and I'm sure its the same on your machine.

---

### Post by jrharvey on 2007-10-22
Also, 64bit is a little bit more work but it is worth it in the end.

---

### Post by zorkerz on 2007-10-22
So tell me I have an intel core 2 duo at 2.2 ghz it was my understanding that this is only a 32 bit processor. Am I wrong? can I run 64 but ubuntu on it?

---

### Post by jrharvey on 2007-10-22
I have an intel core 2 duo at 2.0G and it runs 64 bit just fine.

---

### Post by jrharvey on 2007-10-22
I THINK (but i might be wrong) that the intel core duo was 32 bit and the core2 was 64. I may be wrong here though since i know very little about processors and how those things work. Im still convinved aliens gave us those. Haha, just kidding. :)

---

### Post by jrharvey on 2007-10-22
Ok Yes, the Core2 is 64 bit, regardless of whether its duo or quad. I just saw it on intel site.

---

### Post by parkland on 2007-12-19
I just got an LG laptop with 4GB and centrino duo, can i run ubuntu 64?

---

### Post by rsambuca on 2007-12-19
> **parkland said:**
> I just got an LG laptop with 4GB and centrino duo, can i run ubuntu 64?

We would need to know the chip model, since Centrino Duo's can be either 32bit or 64bit.

---

### Post by LaRoza on 2007-12-19
> **parkland said:**
> I just got an LG laptop with 4GB and centrino duo, can i run ubuntu 64?

If it came with 4 GB of RAM, it had better be 64 bit, as a 32 bit processor can't use all of that.

---

### Post by rsambuca on 2007-12-19
Yeah, presumably!  Actually, anything made after July 26th, 2006 carrying the name Centrino Duo will be 64bit.

---

