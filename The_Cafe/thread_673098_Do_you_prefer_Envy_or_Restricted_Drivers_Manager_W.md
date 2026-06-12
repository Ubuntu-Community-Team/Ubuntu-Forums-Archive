---
title: "Do you prefer Envy or Restricted Drivers Manager? What have been your experiences?"
date: 2008-01-20
forum: The Cafe
---

### Post by aysiu on 2008-01-20
In [this support thread](http://ubuntuforums.org/showthread.php?t=673077), some people are recommending Envy to install Nvidia drivers. Others are recommending Restricted Drivers Manager. No one yet has mentioned manually installing the Nvidia driver from the Nvidia site yourself.

Having tried both methods myself and not having been able to see the difference, I'm curious what other people's experiences have been. Please vote in the poll and explain a bit if you'd like about your choice.

Thanks for your time. I look forward to being educated!

---

### Post by doorknob60 on 2008-01-20
I don't see a poll, but I've always used Envy. I don't know why but I used to think it installed a better driver than the Restricted Driver Manager, so I used Envy instead, but it works fine for me :)

---

### Post by John.Michael.Kane on 2008-01-20
I have tested envy, and the restricted driver manager before, and they both have their uses.

I think users resort to envy to get the latest driver. Then there are those who might use it if they do not have time to install manually or do not understand how to install their drivers manually.

I currently use the below command from a  terminal followed by a system reboot.
```
sudo nvidia-glx-config enable
```

---

### Post by meborc on 2008-01-20
i have tried both... i have a 8600m gt nvidia card, i get 6200 fps with glxgears using restricted drivers manager and 4500 fps using envy

my experience was much more painless using RDM then it was when using envy, after trying envy and seeing that i was better of with RDM, i ran into trouble when i tried to uninstall the drivers using envy... i had a lot of problems and ended up reinstalling the os as i couldn't quite figure out why i was not able to swith back to RDM after uninstalling envy even after numerous reboots (all requested by the RDM) 

in my view, RDM is just so much better in bringing 3D support to the user without any hassle with better output

...thats my story

---

### Post by fatality_uk on 2008-01-20
Used both. Find envy's one click approach slightly easier.

---

### Post by getaboat on 2008-01-20
On dapper every core upgrade means X falls over. Thank goodness for Envy. It always works and always digs me out the poo. Alberto Milone for pope!

---

### Post by Kingsley on 2008-01-20
I have never used Envy, so I guess my preference would be Restricted Drivers Manager.

---

### Post by aysiu on 2008-01-20
> **fatality_uk said:**
> Used both. Find envy's one click approach slightly easier.
Can you explain what you mean by that exactly?

I've used both as well, and the Restricted Drivers Manager seemed a "one-click approach" to me as well. I'm confused. How many clicks did you have to do for RDM?

---

### Post by brunovecchi on 2008-01-20
I've only used RDM. In the past, I used Automatix. I look forward to this thread getting bigger, I was wondering lately if I should try to fish a newer driver with an external application such as Envy. I'll wait and let the people speak!

---

### Post by Gigamo on 2008-01-20
On my previous installs I've used envy as well. That installed the newest 169.07 nvidia driver. However, this time I tried the RDM method, which was even easier, and installed 100.14.19 driver version. To my surprise, this driver runs everything smoother.

---

### Post by Kosimo on 2008-01-20
I use Envy, since It assures me that I'm installing the very latest release.

Does restricted driver install this latest release of every ATI or nVidia drivers?

---

### Post by -grubby on 2008-01-20
I've tried both. Envy doesn't work. The restricted drivers manager manages to get it installed but it doesn't work. So I always end up having to install nvidia-glx-new myself. (BTW I have an NVIDIA Geforce 6100)

---

### Post by LO Matt on 2008-01-20
I've used both.  I had problems w/ Envy.  I was having a problem and I tried using envy for the driver instead of the restricted manager.  It installed fine, and didn't fix my issue (it was something unrelated).  When I wanted to go back to Restricted Drivers Manager, something broke and RDM couldn't use the nvidia driver.  Using envy now, but I'd just rather use an ubuntu feature vs. a 3rd party script.  Plus now I gotta remember "sudo envy -<can't remember the option>" when I do a kernel upgrade.  It's easier to click a checkbox, ya know?

YMMV w/ envy.  Envy does have it's place, and especially before gusty, it's just for folks who need a newer driver than ubuntu supplies.  But I've installed the drivers manually w/ the nvidia script and it's not that hard.  :cool:

---

### Post by ~LoKe on 2008-01-20
Restricted manager has never worked for me.  Envy stopped working.  Now I install the drivers myself.

---

### Post by CCNA_student on 2008-01-20
I have never used Envy and the Restricted Drivers Manager worked fine for my ATI X300.

---

### Post by FuturePilot on 2008-01-20
I've used both. Envy is nice for getting the latest driver as it takes care of completely remove previous versions and making sure the install goes as smoothly as possible. However when a new kernel comes through you have to reinstall the driver. An easy task but it might be an inconvenience for some. So although I do like Envy since it makes something that was previously confusing and complicated extremely easy, I'd prefer to stay with the Restricted Driver Manager since it's just easier to manage especially for new users since you don't have to worry about those kernel updates.

---

### Post by Tristam Green on 2008-01-20
Used both; I've had problems with Envy not liking my compiz-fusion/emerald setup.  So I swapped back to RDM and it worked fine.

---

### Post by kostkon on 2008-01-20
I always use the *Restricted Drivers Manager*.

Now about *Envy*; I have to say it is a very useful application, for the type of people that always want the latest version of their graphics card driver. 

Although there is a negative side of it, that always causes support headaches here at the forums. 

**I totally disagree with so many members here, who lightheartedly recommend to new users to use *Envy*, without informing them that every time there will be a Kernel update (or a *Xorg* update?), they will loose their desktop.**

Then a update happens, and the forums are full of people saying: 
> Oh, I lost my desktop! The only thing I see is a black screen!
> Why is this happening to me?!
> Ubuntu is crappy!

A negative image for Ubuntu is being created in the mind of many people every time this situation happens.

Thus, I believe all of us here at the forums we have to set the record straight, and decide that every time we help a new user, we inform him/her of the consequences of using *Envy*.

---

### Post by plun on 2008-01-20
> New users tend to favor immediate functionality over long-term ideological gains, so if you have an Nvidia graphics card, you may want to install the Nvidia drivers for it.

Well I am "low educated" and uses real 3D drivers on my high performance nVidia card

Both Envy and RM are broken for Hardy... manual install with
the "old fashioned method". "nema problema" just boring after every
X or kernel change :---)

:)

---

### Post by forrestcupp on 2008-01-20
I've tried both and neither work for me.  I have an ATI Radeon HD 2600 and the supported drivers don't work for it.  I have to get the latest from AMD manually.

---

### Post by Gigamo on 2008-01-20
I'm thinking to install the latest driver from nvidia manually. Can I install it over the driver I insatlled with RDM? Or should I uninstall the old one first?

---

### Post by kevdog on 2008-01-20
I just wish I had an NVIDIA card to try all three methods :(

---

### Post by NullHead on 2008-01-20
I've tried all three ways to get the driver, and I like over all installing the binary from Nvidia's website. With a simple ```
sudo ./Nvidia*
```

---

### Post by thecapuchin on 2008-01-20
Having tried both the RDM and Envy for both Nvidia and ATI cards, I would have to choose Envy every time.  I've never had anything but trouble with the RDM and Envy works flawlessly.

Nvidia 7600GS, ATI X600 Mobility, Radeon 9600.  All three of these have worked great with Envy.

---

### Post by conehead77 on 2008-01-20
I have a ati X700 and used only RDM. Works fine but no compiz obviously.

Next week a nvidia7600gt arrives and i will try envy because i heard it "should" run better. Didnt know about the kernel update thingy yet though.

---

### Post by roachk71 on 2008-01-20
I've used both Envy and Restricted Drivers Manager in Gutsy, but prefer the latter. Envy simply didn't work.

I'm using Dapper at the moment, since Gutsy kept crashing and having file system problems on my machine. Tried the nVidia driver in the repos, but later realized better performance using the proprietary driver directly from the nVidia site.

---

### Post by Anduu on 2008-01-20
My experience...

I started off with the restricted driver and it worked just fine.

I then encountered the no TTYs bug which I attempted to fix via a how- to which gave me my TTYs back however my system would hang trying to get back to the desktop.

I decided to give Envy a shot and everything was back to normal.

Performance wise they are pretty even.The restricted driver...being older...I think has some *minor* issues

---

### Post by DoktorSeven on 2008-01-20
I compile my own kernel (special needs...) and prefer to compile the NVidia module source from the repos that way and modify my custom xorg.conf to enable it.

Ubuntu doesn't set things up automatically the way I need it.

---

### Post by rajeev1204 on 2008-01-21
I use good old synaptic.

sudo nvidia-glx-config enable  :)


Still no luck?

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by PartisanEntity on 2008-01-21
I have tried all three methods, Envy, restricted drivers and manual installation. I have settled with restricted drivers because it is the least hassle.

---

### Post by samwyse on 2008-01-21
I installed nvidia-glx from the repos. The manager doesn't launch on my Kubuntu. I don't want to do the old way of having to reinstall the driver everytime there's a kernel update which apparently is what will happen with Envy.

---

### Post by bomanizer on 2008-01-21
Restricted Driver Manager.

Why? I try to minimize "3rd party support". If it's in the menus, then I'll use it.

---

