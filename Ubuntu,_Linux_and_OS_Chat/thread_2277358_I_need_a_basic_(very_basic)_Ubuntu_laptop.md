---
title: "I need a basic (very basic) Ubuntu laptop"
date: 2015-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by mcarrara2 on 2015-05-08
I am the IT director for a small charter school in New Mexico.  Also being frugal(OK ckeap)  when I found a stack of older laptops in the basement I knew there had to be a use for them.  Most are Del D520's and a few HP 530's.  All of at least a gig of RAM.  They can run Windows 7 and the Chrome browser, which we used for the recently completed online testing.  I was thinking of converting them to a basic, VERY basic Ubuntu based laptop.  The only thing I want to run is Chrome.  I have been running Ubuntu server with the command line for at least seven years, but have never looked at the GUI.  

I remember in my youth that the GUI sits on top of the windows manager which is on top of X something.  But it is all fuzzy(I'm talking the late 1990's).  I was envisioning something like a Chromebook. The students turn it on and all they see is Chrome, and all they can do is use Chrome.  I am a minimalist, and come from the old school Unix way of thinking, do one thing and do it well.  I don't need all the bells and whistles of a full blown GUI.  I don't need access to dozens of educational software.  All I want and need is Chrome.

How can I do that with Ubuntu?

---

### Post by v3.xx on 2015-05-08
Its called Kiosh.

Never done it myself.

[https://www.google.com/search?client=ubuntu&channel=fs&q=kiosk+linux&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=kiosk+linux&ie=utf-8&oe=utf-8)

---

### Post by kennethwrede on 2015-05-08
I think it depends on how big effort you want to do. The easy and lazy way is to install a regular desktop and only use the guest account. The user can do more things then surf the web, but nothing will be saved on the machine itself. (I think they can use usb-drives if they like, but i'm not sure.)

But if I where to set up a cumputer that only, and only, can browse, then I should do like this.
1) Install at basic Ubuntu with the minimal CD. It will not have any GUI.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

2) Then install the xorg and a simple desktop (Openbox, fluxbox or similar.) and a graphical loginmanager/displaymanager. (LightDM or the far smaler slim.) Have a look at this link for ideas, you can install them at ubuntu as well.
[https://wiki.archlinux.org/index.php/Display_manager](https://wiki.archlinux.org/index.php/Display_manager).

3) Make sure that all important updates is installed automatically, and that see to that "apt-get autoremove" is run every week or so.

4) Give them a user account, or make sure that the guest account works as I want. (Like internet/wifi/usb-modems, printers, usb-ports and other important devices.) I think the important questions is if they shall save anything

5) Install Chrome and whatever I want them to use. (And some basic decorations, like a wallpaper with Feh. The default gray background can take the mood out of anyone.)

Good luck!

/Kenneth

---

### Post by gordintoronto on 2015-05-08
The simplest thing is to install 32-bit Xubuntu 14.04, bring it up to date, install Synaptic Package Manager, use it to install the Restricted Extras, use "web browser" (firefox) to download Chrome, then install it. Zero command-line.

---

### Post by mcarrara2 on 2015-05-11
Thanks.  This looks like exactly what I am looking for.

Mark

---

### Post by Bucky Ball on 2015-05-11
> **gordintoronto said:**
> The simplest thing is to install 32-bit Xubuntu 14.04, bring it up to date, install Synaptic Package Manager, use it to install the Restricted Extras, use "web browser" (firefox) to download Chrome, then install it. Zero command-line.

Yes, this is good. You could also go slimmer. A minimal install and install just a desktop environment like xfce4 or lxde (or just a window manager even) and Chrome. That's it. That would equate to one command line at the first boot of the new install (you may want to add a few other things, but they can be added to that one line). What you end up with is the Ubuntu kernel, a desktop environment and Chrome (would be easier to install Chromium-browser and Pepperflash as they are both in the repositories already, think you need to add a PPA for Chrome).

Here's a couple of links:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Good luck. Sounds like fun (I only use minimal installs myself). ;)

---

### Post by v3.xx on 2015-05-11
> Yes, this is good. You could also go slimmer. A minimal install and install just a desktop environment
Going that route, I think I would be tempted to go with no DM/WM.  I would think xinitrc could be set to boot to browser.  Don't know for sure, never tried that.

Guest session would be an easy way to go.

A mini install is a bit harder, but you sound capable of the task.

No dm or wm would be difficult for someone new, there is a learning curve.

Good luck :)

---

### Post by SurfaceUnits on 2015-05-11
MakuluLinux kicks off the 9 series with Xfce, which  comes in two flavors. A Normal edition and a Lite edition. The Normal  edition sports all the Makulu magic that users have come to love. It  sports a very beautiful and feature rich desktop, easy to use, easy to  navigate. Comes packed with everyday software ready to use out of the  box, It is fast, it is rock solid stable. The Lite edition sports the  same look and feel the Normal edition does, but comes with almost no  software installed, just all the backend basics already setup, it clocks  in at 693MB, small enough to fit on a CD and leaves the power in the  users hands to install their own selection of software.

---

### Post by Bucky Ball on 2015-05-11
Makulu Linux looks like fun and I might try it out myself, but don't like the chances of support if things go pear-shaped. [Here's]("http://makululinux.com/forums/") their forum. Not real active. You might be able to pick up support on Debian forums (best chance) or in the Debian sub-section here (chances not fantastic). 

If I were running this out on a bunch of machines that needed to be stable I think I'd be going for an OS with a wide-user base, pro-active development by more than a handful of people and a very active support community. Expect a learning curve anyway, but expect a steeper one if you choose something more 'boutique' that is used by a thousand or two people. If you're soaked in Debian and code in your sleep, then that would be another story, but if that were the case you probably wouldn't be posting this question here ... ;)

---

### Post by SurfaceUnits on 2015-05-11
[h=3][Snappy Ubuntu Core]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB8QFjAA&url=http%3A%2F%2Fdeveloper.ubuntu.com%2Fsnappy%2F&ei=9-xQVc-NOcHTsAWy1oCYBQ&usg=AFQjCNHiT6m0yn-nsrl5A42X1KiSzsi_lg&bvm=bv.92885102,d.b2w")[/h]

---

### Post by mattharris4 on 2015-05-12
Unfortunately most of this is beyond my knowledge.  However, since these computers have only 1GB of RAM if anything from Canonical will work it is the LXDE GUI which is what Lubuntu is based on.  My understanding is that a minimum install requires a person to manually select and install a GUI.  With a normal Lubuntu install some websites will bump up the RAM used to over 1GB which would be a problem.  Usually I would recommend adding RAM to 2GB but for a school with possibly 500 plus students with 500 plus computers that could get costly.  Also, without the usual programs taking up RAM in the background (even when they aren't being run, I can note several programs on the list of operations in my system monitor) and just a minimal install, the kernel, LXDE, wireless card support and Chrome (or Firefox) on these computers you may just slide under the 1GB mark when surfing the web with these computers.

If you are willing to consider non-Canonical OSes Puppy Linux would certainly come in under 1GB with Chrome but I don't know if it is possible to do a minimum install with that OS plus Chrome and wireless card support.  You would likely have to contact Barry Kauler (the original creator of Puppy) to discuss this, I don't recall seeing a minimum install option on that OSes website and I have looked at it pretty thoroughly.  However, Barry made Puppy so it is easier to write your own version customized to what you need, there are tens of "Puplets" out there in the wild already.  I don't recall one geared to what you need but maybe Barry and/or someone supporting that OS (there are only a few programmers supporting Puppy itself -- and even fewer supporting the Puplets, my understanding is that there are about 100 programmers employed by Canonical) can point you in the right direction.

Good luck with this.  I hope something can work with these computers so your school isn't forced to purchase new or recently refurbed computers to do what you need them to do.

---

### Post by v3.xx on 2015-05-12
Lxde is a nice choice, but I think the bottom line is going to be the browser.  No matter what flavor of *buntu or install method is used, ff and/or chrome will still be the resource users.  I think a lighter browser will be needed.

---

### Post by mcarrara2 on 2015-05-12
> **Bucky Ball said:**
>  (would be easier to install Chromium-browser and Pepperflash as they are both in the repositories already, think you need to add a PPA for Chrome).


Good luck. Sounds like fun (I only use minimal installs myself). ;)

What is the Chromium browser and Peperflash?  I had thought about installing the Chromium OS, but I know Ubuntu so I thought this way would be better?

BTW I posted in a general help forum, but I ended up in this chat forum.  Sorry if I am breaking rules, I have no idea how it happened.

Mark

---

### Post by craig10x on 2015-05-12
Chromium is the open source development version of google chrome web browser...Chrome already has pepperflash (adobe flash) in it where as chromium doesn't and it has to be added on separately (which is why i prefer chrome myself). Chromium OS or Chrome OS is the chrome operating system, which is based on linux and uses the chrome browser...So, we are talking two different things...
Using Chrome browser or Chromium Browser is not the same as having a computer that runs Chrome Os which is using the browser PLUS their operating system...

Adobe no longer makes a linux version of flash, so when you run firefox, you are using the old (last provided) flash from 2 years ago which only gets security updates but no new version...Google Chrome web browser's advantage is they have an agreement with adobe to provided the lastest versions for their pepperflash plug in, so with Chrome you always have the latest flash...

---

### Post by Bucky Ball on 2015-05-12
> **mcarrara2 said:**
> What is the Chromium browser and Peperflash?  I had thought about installing the Chromium OS, but I know Ubuntu so I thought this way would be better?

BTW I posted in a general help forum, but I ended up in this chat forum.  Sorry if I am breaking rules, I have no idea how it happened.

Mark

Apologies. I did it way back and forget to mention, so:

*Thread moved to **Ubuntu, Linux and OS Chat**. *

Better late than never. :)

It is pretty easy to install Pepperflash and Chromium from the repositories. You search for chromium-browser and pepperflashplugin-nonfree (probably) in Synaptic Package Manager, tick them, apply to install them, and that's it.

---

### Post by Mike_Walsh on 2015-05-12
> **mattharris4 said:**
>  If you are willing to consider non-Canonical OSes Puppy Linux would certainly come in under 1GB with Chrome but I don't know if it is possible to do a minimum install with that OS plus Chrome and wireless card support.  You would likely have to contact Barry Kauler (the original creator of Puppy) to discuss this, I don't recall seeing a minimum install option on that OSes website and I have looked at it pretty thoroughly.  However, Barry made Puppy so it is easier to write your own version customized to what you need, there are tens of "Puplets" out there in the wild already.  I don't recall one geared to what you need but maybe Barry and/or someone supporting that OS (there are only a few programmers supporting Puppy itself -- and even fewer supporting the Puplets, my understanding is that there are about 100 programmers employed by Canonical) can point you in the right direction.Good luck with this.  I hope something can work with these computers so your school isn't forced to purchase new or recently refurbed computers to do what you need them to do.

Puppy certainly counts as lightweight. Average size weighs in at anywhere between 180MB-perhaps 280/300 MB on some of the new 64-bit developments. But, despite running 3  'Pups' myself, I must agree with mattharris here. The Puppies, although supported by a thriving community, don't have much in the way of full-time development staff. Barry Kauler largely retired from developing Puppy back in early 2013, and the majority of development work has been taken on by perhaps half-a-dozen others.

They're amazingly capable, though. I run one of these, 'Tahrpup' (based on Trusty), on an ancient Dell Inspiron 1100 from 2002. Pentium 4, 1 GB of RAM, 20 GB hard drive. And it runs at a respectable speed. It's certainly quicker than the Win XP that originally came with it.

But Puppy's big snag is that it runs permanently as root..! Have a read of this, to understand Barry's thinking on this point:-

[http://puppylinux.com/technical/root.htm](http://puppylinux.com/technical/root.htm)

There are mitigations to this aspect, however. Internet apps can be run as user 'spot', which does restrict the possibilities of infection to a large extent. And Chromium is very easy to install. Some of the community members have developed .pets (the Puppy file format for apps), and .sfs files of Chromium, which include the pepperflash-plugin already installed and ready to go (sfs files can be loaded 'on-the-fly' as it were, and don't have to be permanently installed...only 'loaded', as & when required). It's this capability that also makes them incredibly easy to upgrade to the most up-to-date versions.

'Tahrpup' can be found here:-

[http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/)

You'll want the 4th line from the bottom. or the 2nd line if the CPU's on your machines don't support PAE. Burn to CD in the usual way, and 'test-drive' it; see what you think.


Regards,

Mike. :)

---

### Post by user1397 on 2015-05-12
> **v3.xx said:**
> Going that route, I think I would be tempted to go with no DM/WM.  I would think xinitrc could be set to boot to browser.  Don't know for sure, never tried that.

Guest session would be an easy way to go.

A mini install is a bit harder, but you sound capable of the task.

No dm or wm would be difficult for someone new, there is a learning curve.

Good luck :)
Pretty sure you need at least a WM to display any GUI programs, so just xorg, a WM, and chrome like mentioned earlier.  Pretty sure you can't set xinitrc to boot to browser directly.  Again, *pretty sure*&#8203; :P

---

### Post by night_sky2 on 2015-05-13
With 1GB of RAM you'll be fine with Lubuntu 14.04. There is some useful apps preloaded (Firefox browser, word precessor, video player, graphic editor ect all carefully selected for ligthweight purposes) and personally that's where I would go. You get full support from the community, frequent update and a OS that is low on ressources, so that it can bring back old hardware to life.

---

