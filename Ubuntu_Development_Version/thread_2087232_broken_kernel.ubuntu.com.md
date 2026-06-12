---
title: "broken kernel.ubuntu.com"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by dino99 on 2012-11-23
today i cant open that url, seems the server is down.

---

### Post by zika on 2012-11-23
> **dino99 said:**
> today i cant open that url, seems the server is down.
Try again... ;)

---

### Post by dino99 on 2012-11-23
> **zika said:**
> Try again... ;)

yeah now its opened again :P

---

### Post by zika on 2012-11-23
> **dino99 said:**
> yeah now its opened again :P
But, due to downtime probably:
[https://www.youtube.com/watch?v=Reqc38YW81w](https://www.youtube.com/watch?v=Reqc38YW81w)

---

### Post by VinDSL on 2012-11-23
> **zika said:**
> But, due to downtime probably:
[https://www.youtube.com/watch?v=Reqc38YW81w](https://www.youtube.com/watch?v=Reqc38YW81w)
Bwahahahaha!  :D

[https://www.youtube.com/user/VinDSL](https://www.youtube.com/user/VinDSL)

---

### Post by zika on 2012-11-23
> **VinDSL said:**
> Bwahahahaha!  :D

[https://www.youtube.com/user/VinDSL](https://www.youtube.com/user/VinDSL)
WHZGUD2:lowlatency... Not in mainline...

---

### Post by VinDSL on 2012-11-23
> **zika said:**
> WHZGUD2:lowlatency... Not in mainline...
Hehehehe! OMG!:lolflag:

Stop! My sides are hurting!

---

### Post by JMB74 on 2012-11-24
Still having problems I think.

---

### Post by dino99 on 2012-11-24
> **JMB74 said:**
> Still having problems I think.

yes, today its off it seems :(
what is strange, even not getting timeout

---

### Post by Doug S on 2012-11-24
> **dino99 said:**
> yes, today its off it seems :(
what is strange, even not getting timeoutYes, the server is actually there and responding, but it is as though it does so under extreme duress. For example it takes about 3 seconds to reply to an opening SYN packet. Meanwhile, the requester has decided to try again and a cycle of getting nowhere seems to follow. I do see rare ACK packets, but mostly just SYN ACK packets, and all at extremely low rates. Maybe a packet from kernel.ubuntu.com every 6 to 60 seconds, with one burst yesterday of 4 packets in 4 seconds.

---

### Post by ventrical on 2012-11-24
> **dino99 said:**
> yes, today its off it seems :(
what is strange, even not getting timeout


ahhhh .. thanks .. I had wondered why I could not get those kernel pages to come up.

---

### Post by ventrical on 2012-11-24
> **VinDSL said:**
> Bwahahahaha!  :D

[https://www.youtube.com/user/VinDSL](https://www.youtube.com/user/VinDSL)

Oy Vey !!  Vin!! Whahappednmon? :)

---

### Post by VinDSL on 2012-11-24
My old friend...

[http://www.downforeveryoneorjustme.com/kernel.ubuntu.com](http://www.downforeveryoneorjustme.com/kernel.ubuntu.com)

---

### Post by VinDSL on 2012-11-24
> **ventrical said:**
> Oy Vey !!  Vin!! Whahappednmon? :)
I'm been bitten by the "[dubstep]("https://duckduckgo.com/?q=what+is+dubstep")" bug, that's all.

Great music, when banging out code... :D

Shuffling is just too distracting!

Example:  [https://www.youtube.com/watch?v=eD7Jsqw9dyw](https://www.youtube.com/watch?v=eD7Jsqw9dyw)

---

### Post by ventrical on 2012-11-25
> **VinDSL said:**
> My old friend...

[http://www.downforeveryoneorjustme.com/kernel.ubuntu.com](http://www.downforeveryoneorjustme.com/kernel.ubuntu.com)


Thanks Vin.. I thought it was just me :)  Actually .. I thought I was being deliberately blocked... weird eh? :)

I thought at least there would be an error but it just kept spinning.

Regards..

---

### Post by ventrical on 2012-11-25
At least now there is an error. Must have been a serious crash.

---

### Post by Doug S on 2012-11-25
> **ventrical said:**
> At least now there is an error. Must have been a serious crash. Yes, now the site is immediately refusing to allow a port 80 TCP session to open. It is immediately replying with a RST packet. previously this> I thought at least there would be an error but it just kept spinning. 
was because the site was trying, but due to whatever issue, not really getting anywhere. The session would never really open and never timeout (well sometimes it would timeout).
Agreed, it must have been a serious issue.

---

### Post by dino99 on 2012-11-26
Hopes that someone from ubuntu will restore that url.

---

### Post by JMB74 on 2012-11-26
> **dino99 said:**
> Hopes that someone from ubuntu will restore that url.

Well, they are probably going to HAVE to do something, as it also hosted all the public ubuntu kernel development git repositories.

They are also stone dead at the moment.

---

### Post by zika on 2012-11-26
It is back! Now we have to wait just for compile...

---

### Post by ventrical on 2012-11-26
It's working again.

---

### Post by zika on 2012-11-27
It is getting filled with kernels... Good work girls and boys. Thank You...
Off to try rc7...

---

### Post by paul_in_london on 2012-11-27
Yep, just checked and rc7 mainline is here;

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/)

---

### Post by ventrical on 2012-11-27
ventrical@ventrical-PY028AA-ABA-A1106N:~$ uname -a
Linux ventrical-PY028AA-ABA-A1106N 3.7.0-030700rc7-generic #201211252135 SMP Mon Nov 26 02:35:53 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$

---

### Post by VinDSL on 2012-11-27
> **paul_in_london said:**
> Yep, just checked and rc7 mainline is here;

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/)
Drat!  I had my fingers crossed, but still no scanner goodness...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-27-nov-2012-5(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-nov-2012-5.png")[/INDENT]


The situation I'm in reminds me of installing network printers.

When printers et al. get janky, in my experience, you're better off just doing a wash, rinse, and restyle.  But, scanner setups are so contrived, especially when you start adding scanner front-ends, fax servers & fax clients, and so forth, and so on -- I cannot seem to get a handle on it.

The funny thing is, I have a *feeling* I'll be forced to do a fresh UbuRR install, just to get my scanner back.  LoL!  :D

---

### Post by ventrical on 2012-11-27
My CanonMP520 and HPC4180 are working on all of my machines , both 32 and 64 bit.

---

### Post by ventrical on 2012-11-27
Here's my old Epson beast flatbed. I'll try that and see what happens.

---

### Post by ventrical on 2012-11-27
Worked just great.

edit* ..whoops .. sorry .. off topic.

---

### Post by VinDSL on 2012-12-01
Okay, I give up...

What's "prestable" mean :confused:

More [PC]("https://s13-us2.ixquick-proxy.com/do/spg/highlight.pl?ah=1&l=english&cat=web&c=hf&q=political+correctness&rl=NONE&u=https:%2F%2Fen.wikipedia.org%2Fwiki%2FPolitical_correctness&rid=LILNPONQKSMK&hlq=https%3A%2F%2Fs13-us2.startpage.com%2Fdo%2Fsearch&mtflag_ac=0&mtabp=-1&mtcmd=process_search&mtlanguage=english&mtenginecount=1&mtpl=chrome&mtx=0&mty=0&mtcat=web&mtlui=english&mtsuggeston=0") obfuscation?!?!?!?

---

### Post by ventrical on 2012-12-01
I am not 100% sure but I think it may be like those Mexican Jumping Beans :) When you just let them sit there then all is well , but, as soon as you warm them up in your hand they start jumping!  So a pre-stable kernel may act like a jumping bean once in a while. :)

---

### Post by zika on 2012-12-01
Or, it might be quite opposite: that might be a kernel that has only stable stuff and it will converge to a stable one... 999/996 could be called unstable (chronically) and this one might be a repository for sane stuff...

---

### Post by VinDSL on 2012-12-01
> **ventrical said:**
> I am not 100% sure but I think it may be like those Mexican Jumping Beans :)

> **zika said:**
> Or, it might be quite opposite: that might be a kernel that has only stable stuff and it will converge to a stable one... 999/996 could be called unstable...
Oh, okay. 

May I suggest they call it linux-50-50-90-mjb?

Mexican Jumping Bean patch. 50/50 chance it'll work; 90% chance it won't.  :D

---

### Post by JMB74 on 2012-12-01
> **VinDSL said:**
> Okay, I give up...

What's "prestable" mean :confused:

I presume it is a build of the kernel tree that will become the next stable point release of that series.

i.e. the 3.6.y build would contain what has been committed as fixes for the 3.6 kernel since 3.6.x was released.

---

### Post by ventrical on 2012-12-01
> **VinDSL said:**
> Oh, okay. 

May I suggest they call it linux-50-50-90-mjb?

Mexican Jumping Bean patch. 50/50 chance it'll work; 90% chance it won't.  :D


    I have to admit that the word  'prestable' is new to me . I thought at first it was the combination of 'presto' and 'able' so my first inclination was to think that is was a kernel with super-fast abilities and hidden tools for elite testers.

:)

Regards..

@zika... yes .. you may be correct zika (as you mostly are 99% of the time ) :) lol

---

### Post by zika on 2012-12-01
> **ventrical said:**
> @zika... yes .. you may be correct zika (as you mostly are 99% of the time ) :) lolYou're making me blush...
[https://www.youtube.com/watch?v=DEC8nqT6Rrk](https://www.youtube.com/watch?v=DEC8nqT6Rrk)

---

### Post by ventrical on 2012-12-01
> **zika said:**
> You're making me blush...
[https://www.youtube.com/watch?v=DEC8nqT6Rrk](https://www.youtube.com/watch?v=DEC8nqT6Rrk)


;)

---

### Post by VinDSL on 2012-12-02
> **ventrical said:**
> I have to admit that the word  'prestable' is new to me [...]
I'm bored!

I'm gonna try one, and see if I can blow up Raring.  Bwahahahaha!   :twisted:

BBL

**LATER**

Bah!  Total waste of time!

Works fine...

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Sun Dec  2 15:14:59 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.6.7-999-generic
Unity Release: unity 6.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0.901+git20121123+server-1.13-branch.c0e68f8e-0ubuntu0ricotz~quantal

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

I'll do a ~proposed update and see if I can break something...  LoL!  :D

---

### Post by ventrical on 2012-12-02
lol:)  Thats what I'm doing right now. i am going to install the latest rc on 12.04 and see if I can bust Compiz.

Geesh .. it was getting sleepy around here   hehehe :)

---

### Post by CharlesA on 2012-12-03
Closed at request of OP.

---

