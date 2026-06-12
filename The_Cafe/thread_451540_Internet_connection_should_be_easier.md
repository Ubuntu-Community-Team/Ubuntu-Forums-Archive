---
title: "Internet connection should be easier"
date: 2007-05-22
forum: The Cafe
---

### Post by helltone on 2007-05-22
Hello!

I have a suggestion but didn't find exactly where to post it... the Community Cafe perhaps??

I think Ubuntu would be better if the first time I connected to internet connection was easier. The only internet connection I have is a VPN wireless at the university. It was kinda hard to connect for the first time.

My experience: I had to download ndiswrapper, some drivers for my intel next-gen wireless-n, plus some libraries like liblzo2-2 and then openvpn. Put everything in the usb key of a friend...

I know intel drivers are proprietary... wonder if ubuntu doesn't include them because of that...

But at least there should be a .iso somewhere with "ubuntu + whatever may be critical to connect to internet for the first time, even if it is proprietary".

Thanks
Helltone

---

### Post by dca on 2007-05-22
In certain distro(s) ndiswrapper can be a pain...  Other OS(s) would have similar results.  If you installed Intel wireless driver(s) on a WinXP machine some config would still be necessary.  The biggest deal is to get the default driver config utility to play nice w/ WinXP's native wireless config utility by killing one of the off just so you can get on the net.

---

### Post by prizrak on 2007-05-22
VPN is nasty, very nasty. Your card is too new that's the real problem, with 802.11n you'd have problems in any OS.

---

### Post by bonzodog on 2007-05-22
Ubuntu does connect to the net first time if you have a wired ethernet connection. In fact, it does it during install.

However, Wireless remains one of the few things about Linux in general that still requires a lot of tweaking to get working.

The reason that you had to use ndiswrapper was to make linux use the windows driver, as there is no native linux driver for your particular make and model of card.

Some wireless cards work out of the box, as the manufacturers have produced Linux Drivers, or open-sourced their code, so a native linux kernel mode driver was available.

How ever, some don't , and thats when you have to tweak the system to get it working.

---

### Post by [h2o] on 2007-05-22
I must be lucky, because I have never had any wireless issues with Linux at all.

Also, I find it a bit strange that som many universities use complicated setups for using wireless. The university I attend use open access points but directs anyone trying to use it to a login page, where you login and can start surfing.

---

### Post by igknighted on 2007-05-22
Wireless N hasn't been standardized yet, so its a major crapshoot.  I would avoid it for some time yet, windows or Linux.  Also, the issue with wireless is with the hardware manufacturers.  Without any kind of driver for linux from them, there isn't much we can do.

---

### Post by Irishpolyglot on 2007-05-22
Hello Helltone! 

I just saw your post and it's shown me some light at the end of the tunnel!!!! I installed Ubuntu almost a week ago but still have no choice but to access the net on the wired connection 'cause I have the exact same card as you. I've posted questions on this forum all over the weekend and am slowly edging my way along to a solution... (I am currently about to try to install the drivers through NDISwrapper)

I wanted to ask you if you could tell me where you got the drivers for that intel wireless card?? I have the exact same one (intel next-gen wireless-n mini-card). On the DELL website I can only find ones for the 3945ABG and the 4965AGN - is that second one ours? What's this about  the liblzo-22 library and openvpn?? I haven't gotten that far and really don't want want to have to figure out all out bit by bit. You'd be saving my life if you could give me some tips!! Seriously! Even if you have just a second to give me an outline of what is needed you'd be saving me so much hassle (that I'm sure you had to go through too...)

I'm new in Linux so it's like pulling teeth trying to get this wireless card to work, while learning my way around the new OS at the same time...

Thanks so much for your help man!!

---

