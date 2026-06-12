---
title: "proprietary software in ubuntu"
date: 2010-09-01
forum: The Cafe
---

### Post by zedfrugnug on 2010-09-01
I've bin telling my girlfriend all about Ubuntu and the idea of free software. She really likes the idea of free software and wants to try Ubuntu.

Now a Debian-fan told her the ubuntu is not all free software, and that it uses binary drivers. 
Also he said this would pose a legal problem when trying to make your own distribution based on ubuntu because it is not all free software, so you can't redistribute without consent of the companies that build the drivers.
My girlfriend was very disappointed.

So what I'd like to know is this:
 1. Is there any non-GPL software on the Ubuntu CD.

 2. Is there any non-GPL software on standard ubuntu installation when I haven't installed restricted drivers or ubuntu restricted extras? 

3. If 1 or 2 are true, would this pose a (hypothetical) legal issue when making your own distribution based on ubuntu?

4. Exactly what non-GPL software is used for ubuntu?

5. How does Ubuntu differ from debian in using proprietary software?

---

### Post by PaulReaver on 2010-09-01
ubuntu is exactly the same in that respect as debian,  no proprietry software is included on the live cd.

       take flash player for example, to install flash you have to enable the canonical partner repo and then install adobe-flashplugin from the repo.

patented software.... like opera, chrome, google earth, skype... etc
some wifi drivers (broadcom)
win32 codecs
libdvdcss2
flash player

if your really interested in debian,  debain 6 should be out in the next couple of months, but to be honest there aren't any legal issues you would need to worry about,  the linux mint guys include codecs and no-one has sued them.... yet.

---

### Post by Spice Weasel on 2010-09-01
Install vrms and run it if you want to find out.

Lots of non-GPL software is used. See BSD + zlib licences.

---

### Post by cascade9 on 2010-09-01
Unless things have changed, there is non-free software on the CD by default. If there wasnt, then things like gobuntu, gnewsense and the"Free Software Only" installer options wouldnt exist. 

You can have a look here for slightly more info (some of which is a long way from current, but it will give you background, if nothing else)- 

[http://www.gnewsense.org/index.php?n=FAQ.FAQ](http://www.gnewsense.org/index.php?n=FAQ.FAQ)

---

### Post by Spice Weasel on 2010-09-01
It's really only binary blobs, and Ubuntu (last time I checked) asks you if you want to install propriety drivers.

---

### Post by XubuRoxMySox on 2010-09-01
Debian is no different from Ubuntu with the non-free stuff. Not on a LiveCD, but enable Debian non-free repos and grab the non-free software right from the repos. The Debian fanboy's righteous indignation towards Ubuntu - for doing the exact same thing Debian does - is misplaced.

-Robin

---

### Post by Dragonbite on 2010-09-01
Heck, after an openSUSE installation the system already had non-free stuff like for Flash and Java flagged for installing on first update/installing new software!  I was surprised by this, and if I didn't notice it when installing I would never have noticed it was happening.

It's not like I wasn't going to install it anyway, but that it took my by such surprise and I do a lot of different installations (openSUSE, Ubuntu and Fedora).

---

### Post by kaldor on 2010-09-01
Ubuntu doesn't contain non-free software by default, but does encourage its use through repositories and proprietary drivers.

Also, just because it is non-GPL does not mean it is not free software. BSD, MIT and MPL are other forms of free licenses. 

The sad fact of the matter is that for me (and many others) 100% libre desktops will NOT cut it.

- I need Flash. I'd use Gnash, but  it is really not "there" yet.

- I need quality 3D acceleration. I can't play Quake or JK with 20 frames per second on free nvidia drivers.

- For online courses and some web applets, I need Java to be reliable. OpenJDK/IcedTea crashes a lot, doesn't let me click on things sometimes, sound disappears, etc.

- Until I find a quality Skype replacement, I'm stuck using that crap.


Once I can install a Linux distro and not need to worry about any of the above, I'll be content.

---

### Post by Dragonbite on 2010-09-01
> **kaldor said:**
> Ubuntu doesn't contain non-free software by default, but does encourage its use through repositories and proprietary drivers.

Also, just because it is non-GPL does not mean it is not free software. BSD, MIT and MPL are other forms of free licenses. 

The sad fact of the matter is that for me (and many others) 100% libre desktops will NOT cut it.

- I need Flash. I'd use Gnash, but  it is really not "there" yet.

- I need quality 3D acceleration. I can't play Quake or JK with 20 frames per second on free nvidia drivers.

- For online courses and some web applets, I need Java to be reliable. OpenJDK/IcedTea crashes a lot, doesn't let me click on things sometimes, sound disappears, etc.

- Until I find a quality Skype replacement, I'm stuck using that crap.


Once I can install a Linux distro and not need to worry about any of the above, I'll be content.

The closest I've gotten has been with Fedora (12 & 13).  Their OpenFWWF keeps me from having to fwcutter the proprietary Broadcom (wireless) driver and if their 3D acceleration for Nouveau or open source ATI drivers works as well then the proprietary version is not needed (I don't do games so I don't have a high requirement).

So the only proprietary things installed on my Fedora box are the applications that I choose (Skype, Flash) but otherwise it is a working platform with FOSS only.

---

### Post by mips on 2010-09-01
There's gNewSense based on Ubuntu.

There was also Gobuntu but that has been incorporated into the mainline distro and you can achieve the same with the "Free Software Only" optional installer.

Even if you use Debian in order to get everything working you will have to add non-free stuff, they are free in terms of money but not GPL, Trademark issues etc.

Either way you are going to end up with non-free components in the distro unless you are a die hard GPL evangelist.

---

### Post by Zorgoth on 2010-09-01
If you want a system with no proprietary software, you should go for Fedora because it tends to have more recent open source drivers (particularly for graphics).

However, on Fedora it takes considerably more effort to install proprietary drivers.

---

### Post by sandyd on 2010-09-01
> **Zorgoth said:**
> If you want a system with no proprietary software, you should go for Fedora because it tends to have more recent open source drivers (particularly for graphics).

However, on Fedora it takes considerably more effort to install proprietary drivers.

go for gentoo. all the propreity components/apps/stuff is masked, and you will have to unmask them before you can install them

---

### Post by mips on 2010-09-01
> **carlee said:**
> go for gentoo. all the propreity components/apps/stuff is masked, and you will have to unmask them before you can install them

Only if you're into S&M :D

Not something I would recommend for a newcomer. My Gentoo days are over I'm glad to say. Just not my thing.

---

### Post by lukeiamyourfather on 2010-09-01
> **zedfrugnug said:**
> 
1. Is there any non-GPL software on the Ubuntu CD.


Yes.

> **zedfrugnug said:**
> 
2. Is there any non-GPL software on standard ubuntu installation when I haven't installed restricted drivers or ubuntu restricted extras? 


Not that I know of but there might be.

> **zedfrugnug said:**
> 
3. If 1 or 2 are true, would this pose a (hypothetical) legal issue when making your own distribution based on ubuntu?


Not sure, you'd have to talk to a lawyer. Though there are quite a few Ubuntu based distributions out there. You might want to talk to those developers to see what they had to do, if anything.

> **zedfrugnug said:**
> 
4. Exactly what non-GPL software is used for ubuntu?


ATi/AMD drivers, nVidia drivers, Adobe Flash player, to name a few. I'm sure there are others.

> **zedfrugnug said:**
> 
5. How does Ubuntu differ from debian in using proprietary software?

Debian includes only free software on the discs and default repositories. This is good for some people like purists who want to use only free software. Though for the general public it can be cumbersome because if you want decent 3D acceleration you have to manually install binary graphics drivers, or if you want to listen to an MP3 or watch a Flash video you have to install software from outside of the default Debian repositories and discs.

There are other things to consider even if software is "free" like does it infringe on any software patents in your region. Also is your girlfriend really going to start an Ubuntu based Linux distribution? If not then thinking about this stuff is a moot point. Just download it and give it a shot. That's the best way to decide what to go with. Try Debian too. :wink:

---

### Post by zedfrugnug on 2010-09-01
Thank you lukeiamyourfather for answering each question separately :)
There is non-GPL on the CD, but not on the installation? Could you explain further?


off course my girlfriend isn't really starting a new distro or anything like that. She was just disappointed that ubuntu is not as 'free' as she thought it was.. 
She really does like the idea of free software:D

I must say I am also a bit disappointed for how difficult it is to find out what non-GPL software is on the ubuntu-CD.
A simple list with software and used licenses would make all the difference.
Not planning on using Debian anytime soon though..

---

### Post by lukeiamyourfather on 2010-09-01
> **zedfrugnug said:**
> 
There is non-GPL on the CD, but not on the installation? Could you explain further?


There are packages on the discs that don't necessarily get installed during a default installation, but can later be installed from the disc or repositories if requested.

> **zedfrugnug said:**
> 
She really does like the idea of free software:D


Maybe Debian or Fedora (also only free software) are the way to go on philosophical grounds if she feels strongly enough about it.

> **zedfrugnug said:**
> 
I must say I am also a bit disappointed for how difficult it is to find out what non-GPL software is on the ubuntu-CD.

Anything in the "partners" repository is proprietary but generally free as in beer. Each package has its own specific license from the developer. For example if you install Oracle (previously Sun) Java from the "partners" repository then you have to agree to a license before it will process the installation.

---

### Post by Zorgoth on 2010-09-01
> **carlee said:**
> go for gentoo. all the propreity components/apps/stuff is masked, and you will have to unmask them before you can install them

Heh.  I only know one person who ever used Gentoo.  He eventually realized that even though with Gentoo he could choose what he wanted on his system, Ubuntu used better compiler optimizations than he did and he couldn't get it to run as fast for what he did (simply because he wasn't as good with gcc as the Ubuntu devs).  He also used to use vim and eventually realized that emacs was better :P

---

### Post by phrostbyte on 2010-09-01
AFIAK, there is no proprietary software in the default Ubuntu install. There may be some binary blobs related to the dial-up modems on the CD. Adobe Flash or any proprietary video drivers are NOT bundled with Ubuntu, and if they where it would arguably be copyright infringement ("piracy").

---

### Post by Khakilang on 2010-09-02
When I first install Ubuntu 8.10 I was looking for driver for my nVidia display card and proprietary  software like flash and some multimedia codec  and I couldn't find any of that. So after googling around I then notice that I have to find and install it myself. As I upgrade to 10.04, Ubuntu give me a choice of installing proprietary software and drivers by install the restricted extras. So it boils down to your choice of whether to install or not the proprietary, non free software. To what I know it doesn't come with any non free software so its matter of choice.

---

### Post by zedfrugnug on 2010-09-02
> **lukeiamyourfather said:**
> There are packages on the discs that don't necessarily get installed during a default installation, but can later be installed from the disc or repositories if requested.



Maybe Debian or Fedora (also only free software) are the way to go on philosophical grounds if she feels strongly enough about it.



Anything in the "partners" repository is proprietary but generally free as in beer. Each package has its own specific license from the developer. For example if you install Oracle (previously Sun) Java from the "partners" repository then you have to agree to a license before it will process the installation.

I tried installing ubuntu restricted extras and restricted graphics drivers running from live-CD without internet-connection. This failed.  So I guess they're not on the CD.

---

### Post by Tibuda on 2010-09-02
> **zedfrugnug said:**
> Now a Debian-fan told her the ubuntu is not all free software, and that it uses binary drivers.
Tell your friend that Debian is also in FSF blacklist. See [http://www.gnu.org/distros/common-distros.html](http://www.gnu.org/distros/common-distros.html)

> Also he said this would pose a legal problem when trying to make your own distribution based on ubuntu because it is not all free software, so you can't redistribute without consent of the companies that build the drivers.
FUD
> My girlfriend was very disappointed.
Why she cares so much?

---

### Post by Dragonbite on 2010-09-02
> **Khakilang said:**
> When I first install Ubuntu 8.10 I was looking for driver for my nVidia display card and proprietary  software like flash and some multimedia codec  and I couldn't find any of that. So after googling around I then notice that I have to find and install it myself. As I upgrade to 10.04, Ubuntu give me a choice of installing proprietary software and drivers by install the restricted extras. So it boils down to your choice of whether to install or not the proprietary, non free software. To what I know it doesn't come with any non free software so its matter of choice.

They place the action on YOU to perform these potentially questionable practices (depending on your country's legal stance, yada, yada, yada..) as a way to protect themselves.

> **danielrmt said:**
> Tell your friend that Debian is also in FSF blacklist. See [http://www.gnu.org/distros/common-distros.html](http://www.gnu.org/distros/common-distros.html)

Thanks for the list.  I wonder how often they review the distributions.  According to them, it seems Fedora is the closest to being pure, and that is largely because of the policy they enforce. > Fedora does have a clear policy about what can be included in the distribution, and it seems to be followed carefully. The policy requires that most software and all fonts be available under a free license, but makes an exception for certain kinds of nonfree firmware. Unfortunately, the decision to allow that firmware in the policy keeps Fedora from meeting the free system distribution guidelines.

Seriously, though, their limitations are not an easy thing to manage AND be useful.  I do applaud Fedora's dedication to FOSS but at the end of the day, it is the usable system that gets turned on regardless.

---

### Post by Zorgoth on 2010-09-02
That FSF blacklist is silly.  openSUSE and Gentoo are condemned only for making it possible to install nonfree software.  Going back to the original definition of free, it seems like having a separate distribution channel for free and nonfree software is actually in a sense more free - it gives users the choice of what they want to use.

---

### Post by Eddie Wilson on 2010-09-02
Ubuntu still catches a lot of grief for not having propritary drivers, codecs, applications and such already installed even tho they make it easy to install those items. And they do that they say to stay out of legal trouble. Many of the Ubuntu spinoffs like LinuxMint install the extras and some people make a big deal out of that fact. I find it no problem to install what I need or want.

---

### Post by Dragonbite on 2010-09-02
> **Eddie Wilson said:**
> Ubuntu still catches a lot of grief for not having propritary drivers, codecs, applications and such already installed even tho they make it easy to install those items. And they do that they say to stay out of legal trouble. Many of the Ubuntu spinoffs like LinuxMint install the extras and some people make a big deal out of that fact. I find it no problem to install what I need or want.

And Ubuntu catches grief from other distributions because they make it so easy to add these proprietary drivers.  Kinda a "damned if you do, damned if you don't" scenario!

---

### Post by sandyd on 2010-09-02
> **Eddie Wilson said:**
> Ubuntu still catches a lot of grief for not having propritary drivers, codecs, applications and such already installed even tho they make it easy to install those items. And they do that they say to stay out of legal trouble. Many of the Ubuntu spinoffs like LinuxMint install the extras and some people make a big deal out of that fact. I find it no problem to install what I need or want.

this shall change in maverick meercat. reading the plans for it, the new installer will offer non-free codecs and other non free stuff as a choice to the user. along with an explanation. I believe its about time they got that in the bag...

---

### Post by Dragonbite on 2010-09-03
> **carlee said:**
> this shall change in maverick meercat. reading the plans for it, the new installer will offer non-free codecs and other non free stuff as a choice to the user. along with an explanation. I believe its about time they got that in the bag...

Are they going to be including OpenFWWF, and the graphics drivers Fedora has which includes 3D acceleration?

Offering them is a good step, only so long as what they are offering is capable. Otherwise, it is like Microsoft offering Windows without a browser, but effectively crippling it so only a few people will actually purchase it.

---

### Post by sandyd on 2010-09-03
> **Dragonbite said:**
> Are they going to be including OpenFWWF, and the graphics drivers Fedora has which includes 3D acceleration?

Offering them is a good step, only so long as what they are offering is capable. Otherwise, it is like Microsoft offering Windows without a browser, but effectively crippling it so only a few people will actually purchase it.

we dont know yet. we dont even know if all of the listed are to be included in the final installer. However, I do hope they include the 3d drivers.

---

