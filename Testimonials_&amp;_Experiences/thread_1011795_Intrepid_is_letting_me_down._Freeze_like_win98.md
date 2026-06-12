---
title: "Intrepid is letting me down. Freeze like win98"
date: 2008-12-15
forum: Testimonials &amp; Experiences
---

### Post by nickdbliss on 2008-12-15
It has been a month since i am using intrepid. i must say i am not impressed as much as i was with hardy. Yesterday, after startup i was clicking on application to open amarok and poof it froze. That came as a big shock for me. I had these issues with win98 long time back. This is crazy. 

I dual boot with xp as i have to play some games. it never freeze on it. Right now i am using linux and it is working fine but doing a lot of processing. i can hear my harddisk which i normally dont hear. They say it is something to ACPI etc. but i guess i need to switch back to hardy immediately. lol. Cheers. Intrepid is a failure for me.

---

### Post by solwic on 2008-12-15
> **nickdbliss said:**
> It has been a month since i am using intrepid. i must say i am not impressed as much as i was with hardy. Yesterday, after startup i was clicking on application to open amarok and poof it froze. That came as a big shock for me. I had these issues with win98 long time back. This is crazy. 

I dual boot with xp as i have to play some games. it never freeze on it. Right now i am using linux and it is working fine but doing a lot of processing. i can hear my harddisk which i normally dont hear. They say it is something to ACPI etc. but i guess i need to switch back to hardy immediately. lol. Cheers. Intrepid is a failure for me.

I read that it was that way for a lot of people.  

Personally, I had Kubuntu 8.10 and it hung left and right, too, especially once I updated to KDE4.2  I love Kubuntu, but I got tired of the freezing really quickly, and so went back to regular Ubuntu Ibex, which fixed all the problems I was having.

The key point to remember is to use whatever works for you.  Hardy is an LTS, so it's always a good choice until the next one comes out.  :)

Good luck!

---

### Post by albinootje on 2008-12-15
My impression is that Ubuntu Intrepid Ibex was a bit of a rush release.

I was surprised to install the Galeon web-browser, and to be greeted right away with a warning popup message "myportal is not a registered protocol".

I'm also a bit surprised that, despite the apparent rush, Openoffice.org 3.0 didn't get included in 8.10.

I'm using 8.10 on my desktop since a few weeks now, and i've installed it on a laptop of a colleague, but i think i will try to backport totem for the new BBC-plugin, and stick to Hardy Heron on all the Linux-workstations at work. :)

---

### Post by solwic on 2008-12-15
> **albinootje said:**
> My impression is that Ubuntu Intrepid Ibex was a bit of a rush release.

I was surprised to install the Galeon web-browser, and to be greeted right away with a warning popup message "myportal is not a registered protocol".

I'm also a bit surprised that, despite the apparent rush, Openoffice.org 3.0 didn't get included in 8.10.

I'm using 8.10 on my desktop since a few weeks now, and i've installed it on a laptop of a colleague, but i think i will try to backport totem for the new BBC-plugin, and stick to Hardy Heron on all the Linux-workstations at work. :)

It feels a bit rushed, but as I've said on the forums before, I've got some pretty generic hardware (e-Machines W3400 desktop with an ATI X1300 PCI-E video card) so I'm usually one of the lucky ones in the hardware crapshoot since Hardy (the first to fully support my vid card properly).

And I've never heard of this "Galeon" web browser...but I'm going to look it up.  I'm looking for an alternative to Firefox - but Opera doesn't look that good to me, and I don't like Konqueror much either.

As for OOo 3...I'm with you, my friend.  I'm a writer, so I spend a LOT of time in Open Office.  I tried to install 3.0 and ended up hosing my whole system, so I'll wait till it's supported in the repos...but it would've been nice to have it included with Ibex. 

Ah well, there's always 9.04!  :)

---

### Post by albinootje on 2008-12-15
> **jrock612 said:**
> 
And I've never heard of this "Galeon" web browser...but I'm going to look it up.  I'm looking for an alternative to Firefox - but Opera doesn't look that good to me, and I don't like Konqueror much either.


I'm used to installing Galeon and Epiphany-browser (There's also a game in Linux called Epiphany, hence the name) and Konqueror to have some quick choice of web-browsers.

I always use Firefox but sometimes i need some alternative because Firefox can be annoying sometimes with a "persistent cache" of pages, and i don't have the clear-cache add-on installed everywhere.
In those cases i can fire up an alternative browser which doesn't have those things in the cache, it is also handy to verify whether a problem is caused by a website or by the browser.

But Galeon and Epiphany-browser, although both based on Mozilla or Firefox, don't have the add-ons that Firefox has.
And i want adblock plus and no-script for daily usage.
In fact, during moments without adblock-plus and no-script, i'm sometimes shocked to see advertsiments on nice webpages which i have been using for years.

In other words, i'm not promoting Galeon, nor Epiphany-browser for daily usage, unless you don't care about advertisements and a lot of choice with add-ons.

And I've installed Openoffice 3.0 for some of my users. Downloaded the deb packages from an Openoffice mirror. First carefully removed the Openoffice 2.4 completely, and then installed 3.0
One of the users told me he's happier with 3.0

---

### Post by 3rdalbum on 2008-12-15
Before blaming Ubuntu for freezes, try disabling your proprietary graphics card drivers.

---

### Post by solwic on 2008-12-15
> **albinootje said:**
> 
And I've installed Openoffice 3.0 for some of my users. Downloaded the deb packages from an Openoffice mirror. First carefully removed the Openoffice 2.4 completely, and then installed 3.0
One of the users told me he's happier with 3.0

I'm almost ready to try again.  Last time I tried, using the OpenOffice repos, I was using Kubuntu.  Someone said the updates in the OOo repo were bad, and I tried using the deb from the website, but by then I'd borked the system. 

Of course, lots of other things that *didn't* work on Kubuntu seem to work in Ubuntu, so maybe I'll try again.  

The command to remove OOo 2.4...what was it?

---

### Post by zero244 on 2008-12-15
I agree that in my experience most freezes are related to video card drivers.
If your having sporadic freeze up I would look at the possbility of a video card driver as the source.
I am still using Edgy with Beryl 2 which runs perfectly on my hardware.
Ive looked at Intrepid and from the live cd it ran fine. In fact it ran very fast even running it from the Live CD.

---

### Post by albinootje on 2008-12-15
> **jrock612 said:**
> 
The command to remove OOo 2.4...what was it?

I followed this howto :
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

but instead of the risky "sudo apt-get remove openoffice*.*"

i've done a dpkg -l 
and from that selected all openoffice packages i wanted to remove
with sudo apt-get remove --purge

I just looked at the bash history of 4 workstations i've installed it on, but it's already gone in the history, otherwise i would have copy&pasted it here.

---

### Post by solwic on 2008-12-15
> **albinootje said:**
> I followed this howto :
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

but instead of the risky "sudo apt-get remove openoffice*.*"

i've done a dpkg -l 
and from that selected all openoffice packages i wanted to remove
with sudo apt-get remove --purge

I just looked at the bash history of 4 workstations i've installed it on, but it's already gone in the history, otherwise i would have copy&pasted it here.

Cool, thanks.  I might just give it a try right now.  Out of curiosity, what version of Ubuntu are you running?

---

### Post by albinootje on 2008-12-15
> **jrock612 said:**
> Cool, thanks.  I might just give it a try right now.  Out of curiosity, what version of Ubuntu are you running?

At home i'm using 8.10 on my desktop since a few weeks. 
(After i had an ArchLinux + Ubuntu Hardy dual-boot). But the desktops at work with Openoffice 3.0 are Hardy installations.

And I'm planning to use Ubuntu 8.04 in VirtualBox, because it's handy to have to help some Hardy users at work.
(I really like VirtualBox, the only thing i miss a little bit in it is the build-in host-bridge that VMware has).

---

### Post by solwic on 2008-12-15
> **albinootje said:**
> At home i'm using 8.10 on my desktop since a few weeks. 
(After i had an ArchLinux + Ubuntu Hardy dual-boot). But the desktops at work with Openoffice 3.0 are Hardy installations.

And I'm planning to use Ubuntu 8.04 in VirtualBox, because it's handy to have to help some Hardy users at work.
(I really like VirtualBox, the only thing i miss a little bit in it is the build-in host-bridge that VMware has).

Worked like a charm!  I'm beginning to think that it wasn't a problem with OpenOffice, but a problem with KDE.  A few things I tried with Kubuntu that didn't work are working without a hiccup in Ubuntu.  

Anyway, thanks a million.  And for the record, I used the 
```

sudo apt-get remove openoffice*.*

```
command  and it worked fine.  

Again...thanks!  :)

---

### Post by albinootje on 2008-12-15
The "sudo apt-get remove openoffice*.*" removes way too much in my opinion.
(and the *.* reminds me of the ancient 8.3 characters DOS times.. ;-)

But cool that Openoffice 3.0 now works for you! :)

---

### Post by nickdbliss on 2008-12-16
> **3rdalbum said:**
> Before blaming Ubuntu for freezes, try disabling your proprietary graphics card drivers.

I agree with you on that. couse it was a problem on my friend's laptop. But i use open source drivers. So problem is something else. Anyways thanks for the info 3rdalbum. I am already running hardy now. And it works like a charm after updates. wheww.

---

