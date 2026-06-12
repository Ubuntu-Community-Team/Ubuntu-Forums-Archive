---
title: "Thoughts on low bandwidth installation"
date: 2010-01-24
forum: Testimonials &amp; Experiences
---

### Post by alexgenaud on 2010-01-24
Hi,

I've installed Karmic on multiple machines. Generally it works well, but I've taken note of a few things that don't work as well as I expected. Most importantly, the bandwidth usage is enormous both during and especially after installation.

That the installer downloads language packs without asking is expensive and unacceptable. I copy /var/cache/apt to all machines after installation to reduce download costs. However, the same language packs are downloaded with every installation. Consider (not my case) a user in a remote location of Asia!

Again, I am generally quite happy with Karmic. Here is a rant of complaints:

* (SHIFT) Alt-Tab does not reverse the window selection sequence (as it does in windows) (this has never worked in GNOME/Ubuntu as far as I know)

* Alt-Shift should be the default language switch (not Alt-Alt) as has been the precedent in windows for fifteen years.

* Dragging a window to the edge of the workspace no longer switches workspaces (worked in Jaunty).

* First user does not automatically have access to network configuration (is this a security feature?) even with sudo.

* "User Settings" > (key icon) "Click to make changes": Does not work - I expect a gui-sudo, but nothing happens.

* Home directory encryption failed to reboot in both of my laptops (Compaq/HP nw8240 and Lenovo x200) but worked on various desktop machines.

* Installation downloads language pack without asking (I am in Greenland and install multiple machines, this is expensive and unaccaptable)

* Turning off/removing various start-up apps and services (like CUPS, window candy, or irqbalance) should then inform APT not to install updates for those items. In otherwords, chkconfig should be synched with APT.

* For the future, I am considering adding a new partition just for /var/cache/apt ... which I believe should reduce network usage the next time I upgrade a system. I already rsync this directory to USB.

---

### Post by Tamlynmac on 2010-01-24
> alexgenaud
Again, I am generally quite happy with Karmic. Here is a rant of complaints:

Since this isn't a debating section of the forum,  I will simply say thank you for sharing your experience and wish you well.

Good Luck

---

### Post by abbyhoag on 2010-01-24
> That the installer downloads language packs without asking is expensive and unacceptable. I copy /var/cache/apt to all machines after installation to reduce download costs. However, the same language packs are downloaded with every installation. Consider (not my case) a user in a remote location of Asia!I've installed Karmic a couple of times, on a few different test drives, just to get a feel for how it works, seeing as I am relatively new. During the install, when it comes to downloading and installing things, at the top right corner under the status bar is a button labeled "SKIP". If you click that, it will *surprise!* skip that part of the installation. 

> 
* (SHIFT) Alt-Tab does not reverse the window selection sequence (as it does in windows)Linux is not Windows.


> * Alt-Shift should be the default language switch (not Alt-Alt) as has been the precedent in windows for fifteen years.Linux is not Windows.


> * Home directory encryption failed to reboot in both of my laptops (Compaq/HP nw8240 and Lenovo x200) but worked on various desktop machines.If it works on your desktops, then it seems like a laptop issue, not a Karmic issue. Though without further information, I wouldn't know how to help. You aren't looking for help though, are you?


> * Installation downloads language pack without asking (I am in Greenland and install multiple machines, this is expensive and unacceptable)I've installed Karmic a couple of times, on a few different test drives,  just to get a feel for how it works, seeing as I am relatively new.  During the install, when it comes to downloading and installing things,  at the top right corner under the status bar is a button labeled "SKIP".  If you click that, it will *surprise!* skip that part of the  installation. 



> 
* For the future, I am considering adding a new partition just for /var/cache/apt ... which I believe should reduce network usage the next time I upgrade a system. I already rsync this directory to USB.Sounds good to me.

---

### Post by alexgenaud on 2010-01-24
> **abbyhoag said:**
> During the install, when it comes to downloading and installing things, at the top right corner under the status bar is a button labeled "SKIP". If you click that, it will *surprise!* skip that part of the installation.

Interesting. I have not noticed a 'skip' button. I'll give it a look on a virtual machine. Thanks for the tip.

> **abbyhoag said:**
> 
>> * (SHIFT) Alt-Tab does not reverse the window selection sequence
>> (as it does in windows) (this has never worked in GNOME/Ubuntu
>> as far as I know)
>>
>> * Alt-Shift should be the default language switch (not Alt-Alt)
>> as has been the precedent in windows for fifteen years.

Linux is not Windows.


Thank you less for this observation. :) It is true that Gnome is neither Windows nor Apple, but that hasn't prevented any from duplicating the near-ubiquitous ^Z ^X ^C ^V (1974) precedence from Xerox PARC. Why? Computers serve humans. And humans are creatures of habit, have poor memory, poor context switching, and are slow learners.

Anyway, Alt-Shift-Tab is broken - it's not a matter of copying Windows.

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/150702](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/150702)

My suggestion that Alt-Shift switch keyboard layout IS a matter of copying Windows. Blatantly so.

I've requested Windows POSIX compliance too, but Microsoft isn't listening.

> **abbyhoag said:**
> 
If it works on your desktops, then it seems like a laptop issue, not a Karmic issue. Though without further information, I wouldn't know how to help. You aren't looking for help though, are you?


Yes. It does seem to be a laptop issue (with both of them) and that makes it a Karmic issue! And yes. I am looking for help.

---

### Post by Tamlynmac on 2010-01-24
> alexgenaud
Yes. It does seem to be a laptop issue (with both of them) and that makes it a Karmic issue! And yes. I am looking for help. 	

Since this isn't a support section of the forum, might I suggest you post a thread in the appropriate help section and request assistance.

Good Luck.

---

### Post by abbyhoag on 2010-01-30
> **alexgenaud said:**
> Interesting. I have not noticed a 'skip' button. I'll give it a look on a virtual machine. Thanks for the tip.



You are welcome Alex, I swear it's there. I could be wrong, but I know I have seen it.

Hope you got some of your other issues resolved.

---

### Post by XubuRoxMySox on 2010-01-30
You may also install it *once* and tweak it to perfection on a *single* computer, then use [Remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") to create a LiveCD of your custom-made remix and install it from your remastered copy on all the other machines. The link above is a good tutorial for that.

-Robin

---

### Post by SecretCode on 2010-01-30
> **alexgenaud said:**
> Most importantly, the bandwidth usage is enormous both during and especially after installation.I can give a very strong testimonial for **apt-cacher-ng**. Bandwidth isn't cheap here in SA, but caching all the updates saves a huge amount.

> **alexgenaud said:**
> * (SHIFT) Alt-Tab does not reverse the window selection sequence (as it does in windows) (this has never worked in GNOME/Ubuntu as far as I know)

* Dragging a window to the edge of the workspace no longer switches workspaces (worked in Jaunty).
Both of these work for me, but I can't recall if they worked out of the box, or if I set them in **compizconfig-settings-manager** (ccsm) - also strongly recommended.

---

### Post by alexgenaud on 2010-01-31
Hey Robin, SecretCode et al,

Thanks for the tips. Remastersys sounds very interesting. I'll look into if/when I install more machines (or Lucid). Apt-cacher-ng sounds like something I could use straight away. Though, I've been synching /var/cache/apt (and yum on CentOS) and that seems to work just as well.

I dropped compiz from the old laptop (nw8240) causing me the most headaches - which created new problems while solving others. :) I think I can live with the little issues for a few months before Lucid.

Thanks again,
Alex

---

### Post by XubuRoxMySox on 2010-02-01
> **alexgenaud said:**
> 
I dropped compiz from the old laptop (nw8240) causing me the most headaches - which created new problems while solving others. :) 

Hi Alex!

One trick that might help is to *completely remove* Compiz rather than just disable it, if it's giving you headaches. It has li'l remnants that kinda intrude themselves into other things. At least that worked for me back in Jaunty. 

-Robin

---

