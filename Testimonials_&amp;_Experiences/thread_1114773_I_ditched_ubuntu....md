---
title: "I ditched ubuntu..."
date: 2009-04-03
forum: Testimonials &amp; Experiences
---

### Post by mashcaster on 2009-04-03
I use Linux for work and not as a hobby, so I needed a reliable operating system.  When I use gimp, while I am in the middle of editing an image, gimp would just vanish for no reason which I could see.  This would result in me loosing my work. When I would be using Ooo, x server would sometimes freeze, again loosing my work. These are just 2 of the many examples I have experienced with ubuntu

Then I tried out Debian Stable and to my surprise, I never booted up ubuntu 8.10 again.  Because ubuntu is based on Debian SID (unstable), I found no problems installing and using Debian Stable at all.  OK, there are a few frilly bits missing, but I am happy to give up frilly bits for stability any time.

I can now use gimp, without worrying about loosing my work, I can now use the desktop, without worrying about it freezing.  I've had  my computer on for a few months now and NOTHING has ever frozen, crashed, or disappeared.

Amazing.

So, I was wondering if there will be an ubuntu based on Debian Stable?

---

### Post by albandy on 2009-04-03
use LTS versions.

---

### Post by ibuclaw on 2009-04-03
Debian Lenny 5.0 is actually a midway point between Ubuntu Hardy 8.04 and Ubuntu Intrepid 8.10.

It is both good and bad at the same time... But what I've found is that its main benefit is that it allows greater development freedom when it comes to upgrading certain elements of the system per-say.
Then again, intrepid is IMO very stable now than what it originally was when it was first rolled out.

Hardy, for stablility, is the better OS, but I say that because of it's use of the 2.6.24 kernel (arguably the last kernel which actually supported NViDIA drivers without artifacts or glitches).

---

### Post by Dejai on 2009-04-03
A distro is what you make of it, they can usually be moulded to suit your needs. If Debian fits your needs thats fine, there is nothing wrong with using Debian maybe it just clicks with your configuration better. Maybe you should try LTS or wait till jaunty comes out of beta and give it a go.

---

### Post by ibuclaw on 2009-04-03
> **mashcaster said:**
> 
Then I tried out Debian Stable and to my surprise, I never booted up ubuntu 8.10 again.  Because ubuntu is based on Debian SID (unstable), I found no problems installing and using Debian Stable at all.  OK, there are a few frilly bits missing, but I am happy to give up frilly bits for stability any time.


As for the **frilly** bits, here is my **/etc/apt/sources.list** file
```

# Lenny Main
deb http://ftp.uk.debian.org/debian/ lenny main contrib non-free
deb-src http://ftp.uk.debian.org/debian/ lenny main contrib non-free

# Lenny Security
deb http://security.debian.org/ lenny/updates main contrib non-free
deb-src http://security.debian.org/ lenny/updates main contrib non-free

# Testing release
deb http://ftp.uk.debian.org/debian/ testing main contrib non-free

# Compiz
deb http://download.tuxfamily.org/shames/debian-lenny/desktopfx/unstable/ ./

# Audio/Video/Codecs
deb http://www.debian-multimedia.org lenny main
deb http://www.debian-multimedia.org testing main

# VirtualBox
deb http://download.virtualbox.org/virtualbox/debian lenny non-free

```

You will inevitably notice that I'm tied to the **testing** release also.
To get around you apt trying to **upgrading your entire system to testing**, then do this:
```

su -c 'touch /etc/apt/preferences'
su -c 'ln -s /etc/apt/preferences /var/lib/synaptic/preferences'
su -c 'gedit /etc/apt/preferences'

```
(In Debian, you use your root password)

Then paste this into gedit:
```
Package: *
Pin: release a=testing
Pin-Priority: 200
```
then Save+Quit.

Also, if you are wanting to use Restricted Drivers, you are required to install them yourself. Maintaining them is simple in the event of a kernel upgrade: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Regards
Iain

---

### Post by mashcaster on 2009-04-03
Maybe Ubuntu just doesn't agree with my hardware???

> **albandy said:**
> use LTS versions.

I have used LTS for a long time, but it is still based on Debian Unstable.  Also apparently the LTS releases don't mean they are necessarily more stable, it just means they are supported longer.

> **tinivole said:**
> Debian Lenny 5.0 is actually a midway point between Ubuntu Hardy 8.04 and Ubuntu Intrepid 8.10.

It is both good and bad at the same time... But what I've found is that its main benefit is that it allows greater development freedom when it comes to upgrading certain elements of the system per-say.
Then again, intrepid is IMO very stable now than what it originally was when it was first rolled out.

Hardy, for stablility, is the better OS, but I say that because of it's use of the 2.6.24 kernel (arguably the last kernel which actually supported NViDIA drivers without artifacts or glitches).

I am using the nvidia drivers with debian stable and it works perfectly.  Ok, it was a little more than a point and click install, but still straight forward.

> **Dejai said:**
> A distro is what you make of it, they can usually be moulded to suit your needs. If Debian fits your needs thats fine, there is nothing wrong with using Debian maybe it just clicks with your configuration better. Maybe you should try LTS or wait till jaunty comes out of beta and give it a go.

Yes, I think maybe the ubuntu customisations don't work well with my hardware causing it to freeze and crash a lot.  I don't get this problem with debian stable.

> **tinivole said:**
> As for the **frilly** bits, here is my **/etc/apt/sources.list** file
```

# Lenny Main
deb http://ftp.uk.debian.org/debian/ lenny main contrib non-free
deb-src http://ftp.uk.debian.org/debian/ lenny main contrib non-free

# Lenny Security
deb http://security.debian.org/ lenny/updates main contrib non-free
deb-src http://security.debian.org/ lenny/updates main contrib non-free

# Testing release
deb http://ftp.uk.debian.org/debian/ testing main contrib non-free

# Compiz
deb http://download.tuxfamily.org/shames/debian-lenny/desktopfx/unstable/ ./

# Audio/Video/Codecs
deb http://www.debian-multimedia.org lenny main
deb http://www.debian-multimedia.org testing main

# VirtualBox
deb http://download.virtualbox.org/virtualbox/debian lenny non-free

```

You will inevitably notice that I'm tied to the **testing** release also.
To get around you apt trying to **upgrading your entire system to testing**, then do this:
```

su -c 'touch /etc/apt/preferences'
su -c 'ln -s /etc/apt/preferences /var/lib/synaptic/preferences'
su -c 'gedit /etc/apt/preferences'

```
(In Debian, you use your root password)

Then paste this into gedit:
```
Package: *
Pin: release a=testing
Pin-Priority: 200
```
then Save+Quit.

Also, if you are wanting to use Restricted Drivers, you are required to install them yourself. Maintaining them is simple in the event of a kernel upgrade: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Regards
Iain

My sources.list file is something like this

> # Lenny Main
deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) lenny main contrib non-free
deb-src [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) lenny main contrib non-free

# Lenny Security
deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

# Audio/Video/Codecs
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main

How stable is compiz on debian stable?

I've never tried it because I "thought" it was too unstable based on my experience with compiz fusion on ubuntu.

---

### Post by ibuclaw on 2009-04-03
> **mashcaster said:**
> Maybe Ubuntu just doesn't agree with my hardware???

That would be understandable ... The Ubuntu kernel, although similar, is contains quite a few different elements to the Debian one, and built with some extraneous modules.
> **mashcaster said:**
> 
I have used LTS for a long time, but it is still based on Debian Unstable.  Also apparently the LTS releases don't mean they are necessarily more stable, it just means they are supported longer.

Yes an no. I've already said this once, but let me just clarify for you:

Ubuntu Hardy Kernel Version: **2.6.24**
Debian Lenny Kernel Version: **2.6.26**
Ubuntu Intrepid Kernel Version: **2.6.27**

Ubuntu Hardy Gnome Version: **2.22.3**
Debian Lenny Gnome Version: **2.22.2**
Ubuntu Intrepid Gnome Version: **2.24.1**

Give or take, Debian Lenny is about on par with Ubuntu Hardy. I installed both at around the same time last year (when Hardy was in Alpha and Debian was still in Beta), both have been consistently as stable as each other across all my Desktops and Laptops.

Also, don't go about thinking that everything is taken from Debian Unstable... Alot of what goes into Ubuntu actually comes from the **testing** repository, and upgraded as the unstable packages are stablised in a short space of time.
> **mashcaster said:**
> 
I am using the nvidia drivers with debian stable and it works perfectly.  Ok, it was a little more than a point and click install, but still straight forward.

Excellent!
> **mashcaster said:**
> 
Yes, I think maybe the ubuntu customisations don't work well with my hardware causing it to freeze and crash a lot.  I don't get this problem with debian stable.

It's always very difficult to tell just what is the root of this, especially if you don't know where to start.
> **mashcaster said:**
> 
My sources.list file is something like this

Excellent.
> **mashcaster said:**
> 
How stable is compiz on debian stable?

I've never tried it because I "thought" it was too unstable based on my experience with compiz fusion on ubuntu.
Compiz has always been very stable for me. Then again, I am a "**light effects**" user. I don't see the need to have a cube, fish, and water/fire effects flying everywhere, too distracting, and /do-not-want.

I have already vouched that what I already have in place on my desktop install is already very stable, but don't take my word for it, considering the unfortunate time you've had with Ubuntu thus far!

The compiz repository I've supplied above is excellent, in my opinion, but use it at your own discretion.

Regards
Iain

---

### Post by wolfen69 on 2009-04-03
as usual, your mileage may vary. but i find ubuntu to be very stable. i am using jaunty right now, and have not had any problems. and i am a power user with 4-5 things going on at once. it has been perfect. but that's the way it is with distros. one man's perfection is another man's nightmare. use what works for you, and be happy you have a choice.

---

### Post by albinootje on 2009-04-03
> **tinivole said:**
> 
(In Debian, you use your root password)

First thing I do after a Debian installation is to install sudo :)

---

### Post by brayden13 on 2009-04-03
> **tinivole said:**
> 
Hardy, for stablility, is the better OS, but I say that because of it's use of the 2.6.24 kernel (arguably the last kernel which actually supported NViDIA drivers without artifacts or glitches).

what are you talking about? I have Nvidia and it works fine with ubuntu 8.10.

---

### Post by Tamlynmac on 2009-04-03
> mashcaster

I can now use gimp, without worrying about loosing my work, I can now use the desktop, without worrying about it freezing. I've had my computer on for a few months now and NOTHING has ever frozen, crashed, or disappeared.

I've never  experienced any issues of instability with Ubuntu. However, if Debian works on your system then "USE WHAT WORKS". I think we can all agree that the answer is simple - it's an OS's not a life long commitment or generally life threatening. 

I for one am pleased you found a solution to your problems and can only hope others read your testimonial. Your reaction to the issues was logical, instead of giving up you choose to seek an alternative.

Instead of bashing Ubuntu, you accepted the fact that it was not compatible with your system. Many could learn from your experience.

Thank for your intelligent, reasonable and insightful testimonial. It was refreshing.

---

### Post by solwic on 2009-04-04
> **Tamlynmac said:**
>  I think we can all agree that the answer is simple - it's an OS's not a life long commitment or generally life threatening. 



I'm pretty sure you're brushing up against blasphemy there, old friend.  Didn't you know that Linux is more than just a kernel, and Ubuntu is more than just an OS?  It's a philosophy; a way of life.  Choosing Ubuntu over Debian (like choosing apples over, well, apples) ***_IS_*** a life long commitment **_*AND*_** life threatening!

Gee, you old people are really out of touch....


[SIZE="1"][COLOR="Red"]*NOTE:  For the humor impaired, this post is made in the fullest sense of sarcasm and tongue-in-cheek satire.  Please do not take it seriously.  I'm begging you.[/COLOR][/SIZE]

---

### Post by wolfen69 on 2009-04-04
> **brayden13 said:**
> what are you talking about? I have Nvidia and it works fine with ubuntu 8.10.

yeah, some people think that if it happens to them, it must happen to everyone. a sad way to go through life-assuming.

---

### Post by solwic on 2009-04-04
> **wolfen69 said:**
> yeah, some people think that if it happens to them, it must happen to everyone. a sad way to go through life-assuming.

Isn't it, though?

:)

---

### Post by Tamlynmac on 2009-04-04
> jrock612
Gee, you old people are really out of touch....

Really, I'm not the one wolfen69 thinks is lame. :P

---

### Post by ibuclaw on 2009-04-04
> **brayden13 said:**
> what are you talking about? I have Nvidia and it works fine with ubuntu 8.10.
"Fine" is precisely my point. :)

On Hardy, it worked brilliantly...

Then the 2.6.25 kernels came rolling out, to which they removed some old deprecated hooks that no one used anymore... and it is of no coincidence that the NViDIA proprietary driver was using those hooks!

So 2.6.25 kernels had completely broken NViDIA support ...
2.6.26 kernels were no better when they came about next, since NViDIA was still lagging behind, and this was 2 months before Intrepid was set to be released!

Infact, afaik, one of the reasons the NViDIA drivers even worked to a standable degree in Ubuntu (albeit, with the odd artifact, glitch, or damaged screen refresh here or there) - at least, when Intrepid was finally incarnated in October - was due to the work of one NViDIA developer who has his hand in the Xorg project.


Don't get me wrong, though, NViDIA have got half there act turned around and now support the .25, .26 and .27 kernels with varying degrees, based on what version of Xorg you are using. I also still have an Intrepid Machine, that I use daily for work purposes, but whenever I come back to Hardy on the odd occasion, I am very quick to pick out just what I was missing ...

---

