---
title: "Can anyone recommend another forum"
date: 2011-12-01
forum: The Cafe
---

### Post by adnpearce on 2011-12-01
Hi All
 
Ive had 78 views today on my post below but no responses so I guess its a toughie - what forum or website should I refer it to do you think ?
 
Many thanks, Andrew
 
 
 
**Nvidia failed to load kernal module** 
I know this is a simple one but after 3 hours trying stuff from the stickys im afriad i have to ask for help.

Computer worked fine for last year or so then today wont run games or play any sounds from any port. On startup i get low graphics mode warning box saying it cant load the NVIDIA kernal module and that no drivers avialble.

Going into admin/hardware drivers/it shows an NIVID accel graphics driver 'activated and currently in use'

All plugs are corect and mutes turned off - alsamixer confirms this

Going into admin/NVID xserver setting brings up a box saying 'you dont appear to be using the nvis x driver - please edit your x config file (just run nvidia-xconfig' as root) and restart the x server. Ive done the first part of that with a sudo nvidia-xconfig and it just says its backing it up. dont know how to restart the x server (ive tried ctrl/alt/backspace). doesnt fix anything

Also tried downloading latest driver from NVIDIA but when i try to run it in a terminal window (from a copy on the desktop of the .RUN file) it says must be run as root - i dont know what that means sorry. Just running it without the terminal woindow doesnt appear to do anything.

Ive taken this computer overseas full of films to watch and have no TV here - help !

Its an Acer Aspire Revo basic one with NVIDIA ION built in, running Ubuntu 10.04 LTS and please note the Revo is NOT on the internet -anything i want to put onto it has to be downloaded on my windows laptop and moved across by memory stick. 

Incidentally, I think the wireless on the revo has gone down too, or maybe my neighbors have all just turned off their routers ?!? - could this be connected ?

NOte as I say everything was fine a couple of days ago - maybe theres a way to just revert to the setup then ?

cheers, Andrew

---

### Post by IWantFroyo on 2011-12-01
You can try AskUbuntu. 78 views isn't a lot for a problem like this, actually. You should specify what version of Ubuntu you are running, and what card you have.

As for your problem, I think a kernel update broke it. Nvidia has a lot of proprietary stuff, which probably isn't updated as quickly for new kernels as it should be. Really, the easiest thing to do would be to back up your data and reinstall. If you're using an old version, I would advise you to use a newer one.

---

### Post by BC59 on 2011-12-01
It's a forum (A medium for open discussion or voicing of ideas), not a customers support department.

---

### Post by IWantFroyo on 2011-12-01
> **BC59 said:**
> It's a forum (A medium for open discussion or voicing of ideas), not a customers support department.

The main purpose of this forum is to help people with Ubuntu. While the CC is great, it isn't the main focus of this corner of the net.

---

### Post by oldos2er on 2011-12-01
Moved to Community Cafe.

---

### Post by haqking on 2011-12-01
> **BC59 said:**
> It's a forum (A medium for open discussion or voicing of ideas), not a customers support department.

From the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")

> The purpose of the Ubuntu Forums is to provide support for Ubuntu

This forum is more about support than discussion IMO, certain areas of the forum are for discussion.

Cheers

---

### Post by nothingspecial on 2011-12-02
Support posts moved to the support thread here

[http://ubuntuforums.org/showthread.php?t=1889352](http://ubuntuforums.org/showthread.php?t=1889352)

Please put any more support posts there.

---

### Post by OrangeCrate on 2011-12-02
> **adnpearce said:**
> Hi All
 
Ive had 78 views today on my post below but no responses so I guess its a toughie - **what forum or website should I refer it to** do you think ?
 
Many thanks, Andrew
 
<snip>



You could try here:

[http://www.linuxquestions.org/questions/linux-forums-50/](http://www.linuxquestions.org/questions/linux-forums-50/)

---

### Post by kio_http on 2011-12-02
If you want instant help, I would highly recommend the #ubuntu channel on freenode. You are likely to be helped in seconds over there.

Go to webchat.freenode.net or use an IRC client

---

### Post by YourSurrogateGod on 2011-12-02
> **BC59 said:**
> It's a forum (A medium for open discussion or voicing of ideas), not a customers support department.

Heh, not really. :)

Technically, this place is to supply support.  It's just that it's voluntary, no one gets a check every 2 weeks for having answered X number of questions.

And since political discussions are banned "open discussion" is sort of limited. :) :p ;)

---

### Post by drawkcab on 2011-12-02
I would install 11.10.  11.10 + Gnome shell runs really well on my REVO.  

Just choose the upgrade option (i.e. #2 below) during installation and it should preserve your home folder (no guarantees of course).

---

