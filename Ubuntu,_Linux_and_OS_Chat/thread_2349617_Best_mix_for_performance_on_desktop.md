---
title: "Best mix for performance on desktop"
date: 2017-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by makouser on 2017-01-16
OK, so here's my dilemma. I have a fairly old Acer with a T7500 Core 2 Duo processor and 3gb ram.  Also a Radeon graphics card, but that's another story.

For the past 7 or 8 years I have always used Ubuntu Desktop and followed their DEs unquestioning. Lately I've been wondering just how much horsepower I'm using that give me no benefit.

I seldom use anything other than Chrome. That's where I need the performance. If I do do anything using other tools it's so infrequent that performance is not an issue.

So where do I get the best bang for my buck, saving on actual linux processing (if there is any bloat) in the desktop version, by using a different distro. Maybe even the server ubuntu is leaner?

Or do I look at lighter processing DEs? 

I can see that lighter footprint DEs will use less RAM, but I don't think I'm struggling there. 

System monitor shows about 70% RAM used with 3 tabs open. Swap is single figure percentage.

I know we're all quite sad here trying to squeeze every last ounce out of tired old PCs, and it is satisfying to a degree, but would I be better off just sending this one off to be recycled and buying something with an i5 and 8gb ram for an example?

Thanks.

Edit: typo

---

### Post by #&amp;thj^% on 2017-01-16
Well the gain with new hardware would be an enjoyable difference...but that said "to squeeze every last ounce out of tired old PCs"
Have you yet tried XFCE (xubuntu) or even LXDE (lubuntu) or even MATE (Ubuntu Mate)...If not... I would check those three out before sending it out to the recycler first.
Just my 2cents worth.:)

---

### Post by Irihapeti on 2017-01-16
I would agree with using a lighter desktop, so that you save the horsepower for where it's really needed.

I have an old EeePC900, which less powerful than your current machine. Granted, I don't run Chrome on it, but I can run Firefox and LibreOffice. I use a custom Openbox DE. In your case, Xubuntu or Lubuntu, as suggested by 1fallen, should give you a similar result. It can't hurt to try, anyway.

---

### Post by makouser on 2017-01-16
Thanks both. I suppose i should have just gone with the standard recommendations. Over thinking it really I suppose. The idea that I could shave chunks out of the linux and gain some performance is a bit like re-inventing the wheel.

I have tried Lubuntu briefly, and I have to admit it was quite sprightly. I just didn't persevere with finding my way around it, and my frustrations made me switch back to 'full fat' ubuntu. Think I had some driver issues IIRC.

One of my concerns with these 'buntus is updates. Am I right in thinking that the software updater is looking at the same repositories so will get the updates the same time that ubuntu does? It'll just be DE patches that might be a bit slower. That said I guess these are all pretty good now and not too much of a target for the bad guys anyway. 

I've got a 16.10 Lubuntu image here ready to use, so perhaps I'll give it another go.

---

### Post by #&amp;thj^% on 2017-01-16
> =makouser;13595428 Am I right in thinking that the software updater is looking at the same repositories so will get the updates the same time that ubuntu does? It'll just be DE patches that might be a bit slower. That said I guess these are all pretty good now and not too much of a target for the bad guys anyway. 

I've got a 16.10 Lubuntu image here ready to use, so perhaps I'll give it another go.

Yes they pull from the same Repos and maybe extras specific to the Environment you choose.
The Difference will be in the EOL Ubuntu LTS is 5 Years and the flavors will be a 3 Year supported EOL.

---

### Post by makouser on 2017-01-17
Just tried the Live version and had another little explore. I remember now what gave me grief. It was power management.

I don't remember the exact situation, but suspend etc worked fine on Ubuntu 12, 13, maybe even 14, then it all went wrong. It's well documented the 'black screen after resume'. Well it fixed itself with some recent updates, probably kernel.

Now Lubuntu 16.10 won't come back from suspend. Dunno if I upgrade the kernel to the same as I run on Ubuntu it'll work. If I can do it on the Live version I'll give it a try when I have time.

---

### Post by mastablasta on 2017-01-17
you can install (add) desktops to your current working ubuntu and then swtich on login. you can install the full desktop (e.g. fulll Lubuntu) or just the DE files (e.g. only files needed to run LXDE). if you install from minimal .iso and just add XFCE + you change the theme to a more flat 2D one it will also work a lot faster than default xubunut. but you may miss some apps present in Xubuntu and need to add them later on.

windows managers such as IceWM, jwm, openbox are even lighter on resoruces. not just ram, but GPU and CPU as well.

let's not even start with the tabbed desktop like i3. they are flying. if you use only chrome you can open just chrome and that's it. no menues, no major indicators that take system resoruces...

server edition is CLI only (even installer) and comes with various services. other than that it is the same as the desktop only without the desktop part.

---

### Post by makouser on 2017-01-17
I have tried LXDE in addition to Unity, but that wasn't achieving what I was hoping to do with a 'smaller' linux underneath. If indeed that had any benefit. I have read that Lubuntu does have less running services.

I quite like the idea of the minimal Lubuntu install, then add just the DE with no tools. 

Just had a look at the kernel versions. Ubuntu is 4.8.4-34, and Lubuntu Live is -22. Would that account for resume failing? Don't really want to go to the trouble of installing, updating, only to find it doesn't resume. Maybe when there's a bad night on TV:-)

As a matter of interest, If I install Lubuntu presumably I could install ubuntu-desktop and get Unity! That would/could be best of both worlds.

---

### Post by mastablasta on 2017-01-17
minimal iso: [SIZE=2]https://help.ubuntu.com/community/Installation/MinimalCD[/SIZE]
guide to minimal install: [SIZE=2]https://help.ubuntu.com/community/Installation/MinimalCD[/SIZE]

> **makouser said:**
>  

Just had a look at the kernel versions. Ubuntu is 4.8.4-34, and Lubuntu Live is -22. Would that account for resume failing? Don't really want to go to the trouble of installing, updating, only to find it doesn't resume. Maybe when there's a bad night on TV:-)



it could be. the suspend is to do with power management. either ubutnu is using a different power management or it has different drivers (newer kernel). but easy come, easy go. even if it all work it might not with the next kernel upgrade. .1 releases on LTS keep same kernel, higher point releases change it. 

> 
As a matter of interest, If I install Lubuntu presumably I could install ubuntu-desktop and get Unity! That would/could be best of both worlds.

with ubuntu-desktop you will install the whole Ubuntu just as you would do it from Ubuntu install disk.

---

### Post by HermanAB on 2017-01-17
Well, the fastest Debian based distribution is Lubuntu, but it is put to shame by Slackware.

Nothing beats Slackware for raw speed.  There are various reasons for that.  However, note that if you don't have a guru beard yet, then you should install Absolute Linux, which is a Slackware based desktop distribution which is easy to install.  Installing regular Slackware is non-trivial and may require a multiple tries before you get it right.

---

### Post by makouser on 2017-01-17
> **HermanAB said:**
> Well, the fastest Debian based distribution is Lubuntu, but it is put to shame by Slackware.

Nothing beats Slackware for raw speed.  There are various reasons for that.  However, note that if you don't have a guru beard yet, then you should install Absolute Linux, which is a Slackware based desktop distribution which is easy to install.  Installing regular Slackware is non-trivial and may require a multiple tries before you get it right.

Well I do have a beard, but it is quite clipped - so Absolute would probably be best:(.  I shall take a look. Thanks.

---

### Post by makouser on 2017-01-17
I like the look of Absolute, but will have to take a very deep breath to try and install it! 

Researching it has prompted the thought that as my main weapon is Google Chrome, it is probably this that is the limiting factor. What ever else I'm running or have installed is probably academic as it's Chrome that the processor has to turn over. 

Then there's the internet connection...

Perhaps I should just move house to somewhere I can get fiber into the home. 

Scope creep?? ;-)

---

### Post by HermanAB on 2017-01-17
As with all things Linux, run the ISO first and see whether you can handle it - or install it in a VM - before you really install it.

Also see this maybe:
[http://www.aeronetworks.ca/2016/06/slackware-linux.html](http://www.aeronetworks.ca/2016/06/slackware-linux.html)

---

### Post by Kris_M on 2017-01-17
I read through this but I did not get just exactly you want to be faster - graphics? browser tab refresh time? Games? Libre? ...

---

### Post by makouser on 2017-01-18
I do 99% of my work in Google Chrome. To be honest it is quite acceptable. But as with all (probably) nerdy types, I love to tinker. Wouldn't life be so much sweeter if that 1.5 second delay was just a second? ;-)

When I do anything with the linux/ubuntu/unity tools it's so infrequent that my brain is the slowest factor, not the laptop so no lightweight distro will help there!

As in my last post, I'm beginning to think that Chrome runs as fast as it can on this box, and changing things to get faster boot, or less ram (if I'm not swapping now), etc isn't going to change poor old Chrome. I just need a faster PC :-).

---

### Post by Bucky Ball on 2017-01-18
[Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") or Lubuntu-core. Install, install Synaptic Package Manager and then install Chrome (or Chromium). Or just do the latter via a terminal.

[Here's the ISO]("https://unit193.net/xubuntu/core/"). Used to be 16.04 LTS there but now changed to 16.10. The other is probably still about somewhere. [More info]("https://unit193.net/xubuntu/"). 

I always used the mini.iso and installed xfce4 and whatever I need previously. Xubuntu-core takes a bit of the work out of it and gets me to where I was going more quicky so use that now. Don't bother with the server edition. Not what you want. If you're going there, use the mini.iso.

---

### Post by HermanAB on 2017-01-18
In general, Ubuntu is pretty snappy compared to say Redhat Fedora, because Ubuntu doesn't use SELinux - which slows everything down tremendously.  

However, on the same machine, where Ubuntu would be quick to react to user input, Slackware would be instantaneous.  It is pretty shocking how bad the performance of the mainstream distros have become over the years, due to multiple layers of useless crap that have been added to it.

Also, the simpler the OS, the easier it is to tinker with it.  Slack is super simple and therefore a little crude, but great for tinkering.  Note that Slack doesn't necessarily look crude - I run KDE on it.

So why the heck am I on these forums?  The majority of my machines run Ubuntu, I have an Ubuntu Mirror Server with everything, some machines run Fedora, one runs BSD, my main personal machine is a Macbook Pro and there is even a (closed!) Windows laptop next to me - so I use whatever works.  The Slackware forums are nice, but it may take 2 to 3 years to get an answer to a question...

---

### Post by mastablasta on 2017-01-18
> **HermanAB said:**
> 
However, on the same machine, where Ubuntu would be quick to react to user input, Slackware would be instantaneous.  It is pretty shocking how bad the performance of the mainstream distros have become over the years, due to multiple layers of useless crap that have been added to it.

interestingly Debian is also more responsive. I rememeber in the time of XFCE Chrunchbang Linux (debian based version) - the thing ran so fast on a resoruce limited PC (224Mb ram,32Mb GPU, 1,2 Ghz single core AMD64) i couldn't believe it. At the time Lubuntu would crawl on that for some reason, while Xubutnu was a no go. i tried some other distros, but they were too limited or ran slow. 

but Chrunchbang XFCE ran just fine and it had all a for desktop user that ubutnu had, playing Flash videos, libre Office (or was it openoffice at the time?!)... it was way faster than default Windows XP which took 30 minutes to boot and worked a lot better, so we kept it. the install is still there somewhere, i but i didn't have the need for that old PC.

---

### Post by Kris_M on 2017-01-18
> **makouser said:**
> I do 99% of my work in Google Chrome. To be honest it is quite acceptable. But as with all (probably) nerdy types, I love to tinker. Wouldn't life be so much sweeter if that 1.5 second delay was just a second? ;-)

When I do anything with the linux/ubuntu/unity tools it's so infrequent that my brain is the slowest factor, not the laptop so no lightweight distro will help there!

As in my last post, I'm beginning to think that Chrome runs as fast as it can on this box, and changing things to get faster boot, or less ram (if I'm not swapping now), etc isn't going to change poor old Chrome. I just need a faster PC :-).

More ram? faster cpu?

---

### Post by makouser on 2017-01-18
> **Kris_M said:**
> More ram? faster cpu?

Well I'm not swapping now so ram is sufficient. I assume a faster cpu would do the trick, but I don't think that's a possibility - it's a laptop.

---

### Post by dragonfly41 on 2017-01-18
Try GNOME/Flashback to remove overhead of Unity .. 

[http://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/#](http://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/#)

I also have older generation laptop with Core2 Duo and only 3 GB RAM.

I use tab managers in Chromium Web Browser (OneTab) to keep RAM usage within limits.   And I shut down other applications when not in use.

I also have Google Chrome but it no longer supports 32bit and it is not in use.

[http://askubuntu.com/questions/745699/how-should-i-go-about-installing-chrome-on-ubuntu-14-04-32bit](http://askubuntu.com/questions/745699/how-should-i-go-about-installing-chrome-on-ubuntu-14-04-32bit)

However, after years of using Core 2 Duo, only recently I learned that it supports 32bit and 64bit. 
 So I'll wait until I install Ubuntu 16.04 64bit in due course.

---

### Post by Kris_M on 2017-01-18
cool.  I am not familiar with cache mgt in Google Chrome.  In FF I choose to clear just the cache on every boot. Makes things faster and I know I'm getting a fresh copy of the site. Just a thought...  Good luck!!!

---

### Post by HermanAB on 2017-01-18
The best bang for your buck would be a SSD instead of a HDD.  An SSD makes a machine enormously much faster.

---

### Post by Kris_M on 2017-01-18
Yes! +1

---

### Post by makouser on 2017-03-05
So, after a bit of a delay I'm thinking I will go the SSD route. Having done a bit of research I found [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) which goes through what optimisation is best for SSDs. What's the view here? Is this necessary, nice to do, not required at all? It all sounds quite convincing.

---

### Post by makouser on 2017-03-24
Just to close off the thread, I have installed a SSD. I followed the optimisation instructions from the link above, and all I can say is it's awesome! It boots in seconds. 

The only thing I can't figure out, is after installing 16:10 from the same media, the suspend or rather resume doesn't work. This has been an ongoing problem (Radeon HD2400) for ages but had been stable and working for some time. Now it's stopped again. Just can't think why that would be with a change of disk. Anyway. It shuts down and reboots so quickly it's not really an issue now:-)

---

### Post by fastbyte01 on 2017-03-24
If you can upgrade your hardware with an SSD and if possible a little more RAM and then try ubuntu MATE. And all your problems are easily solved. ;)

---

### Post by speedwell68 on 2017-03-24
If you just use Chrome why not turn it into a Chromebook...

[https://www.neverware.com/#introtext-3](https://www.neverware.com/#introtext-3)

---

### Post by pete5 on 2017-03-31
I have the suspend problem with Lubuntu 16.10  on a HP 15-f024wm. Still looking for a solution.

---

### Post by makouser on 2017-04-01
> **pete5 said:**
> I have the suspend problem with Lubuntu 16.10  on a HP 15-f024wm. Still looking for a solution.

Can anyone explain how the suspend/resume works? I assume the problem is driver related, and therefore linked to the kernel and not the distro.

My assumption is that it is the driver failing to reinitialise the driver/video, but I could well have it all wrong in my mind.;)

Edit:

Just tested it again. Symptoms have changed. Previously it would resume, and all the lights would display but the screen was black, and as far as i could see it was unresponsive to keyboard.

Now it tries to resume, lights flash then go out. Pressing the power (normal not 5 second hold) does a cold restart, bios, fsck etc.

So maybe not the video driver. Can't imagine what the difference with SSD could be but that is the change (other than full install) that made it stop resuming.

---

