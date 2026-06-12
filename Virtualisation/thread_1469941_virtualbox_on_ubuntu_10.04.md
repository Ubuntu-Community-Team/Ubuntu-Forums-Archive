---
title: "virtualbox on ubuntu 10.04"
date: 2010-05-02
forum: Virtualisation
---

### Post by black3agl3 on 2010-05-02
can one install sun virtual box on ubuntu 10.04?

---

### Post by greenfrog on 2010-05-02
Yes, it works great.

There is now a version for lucid lynx

---

### Post by Scunizi on 2010-05-02
get it direct from Virtualbox.org.. before installing install build-essential and dkms

---

### Post by John Bean on 2010-05-02
> **black3agl3 said:**
> can one install sun virtual box on ubuntu 10.04?

First thing I installed, so I could run my existing VMs :-)

---

### Post by CharlesA on 2010-05-02
Get it from the karmic repo over at virtualbox.org. Works fine.

---

### Post by manco on 2010-05-03
Is the version at VirtualBox.org the OSE or PUEL?

Back in 9.10 I was using PUEL I believe.  USB worked almost out of the box (had to add myself to the group "vboxusers"

---

### Post by John Bean on 2010-05-03
> **manco said:**
> Is the version at VirtualBox.org the OSE or PUEL?

Back in 9.10 I was using PUEL I believe.  USB worked almost out of the box (had to add myself to the group "vboxusers"

The Ubuntu repository version is OSE, which is what I'm using this time. Under Jaunty I used the closed-source version from Sun's repository but at the launch of 10.4 Sun had no Lucid repo version available. I may (but probably not) switch to it if and when it eventually appears. Sun have both available (of course) at virtualbox.org if you want to roll your own rather than use a repo.

About USB: yes, it more or less works most of the time but I often found it was unreliable with some devices used by a XP guest so I more or less stopped using it.

---

### Post by Dimison on 2010-05-03
I faced a problem in my office with Ubuntu 10.04 (amd64) & VirtualBox.
I downloaded the amd64 release, tried to install xp but everything goes "subzero" and freezes! I cannot do anything less than a reset...
I also tried the one from software center, but still the same.

Does anyone knows a possible solution?

:confused:

---

### Post by Dimison on 2010-05-04
I tried also with the beta version of Vbox but still the same problem...

I will probably do a fresh install and try again...

Any ideas???

---

### Post by RazorV on 2010-05-04
Maybe I'm missing something here, but that would be nothing new since I'm still new to Ubuntu.  But the Version of VB at Sun's website avail for download is ONLY for Ubuntu 9.10?  Where are you guys getting a version of VB for Ubuntu 10.04 Lucid?

thanks and please excuse my ignorance.  I'm going to do a clean install of Lucid and it is mandatory that I run VB for XP proprietary apps. used for work.

Thanks for all the replies...

---

### Post by nerdy_kid on 2010-05-04
> **RazorV said:**
> Maybe I'm missing something here, but that would be nothing new since I'm still new to Ubuntu.  But the Version of VB at Sun's website avail for download is ONLY for Ubuntu 9.10?  Where are you guys getting a version of VB for Ubuntu 10.04 Lucid?

thanks and please excuse my ignorance.  I'm going to do a clean install of Lucid and it is mandatory that I run VB for XP proprietary apps. used for work.

Thanks for all the replies...

just use the karmic version, wont kill anything ;)  i am and it works fine.  I had a little issues with usb, had to add myself to the vboxusers group and had to chmod g+rw /dev/vboxdrv but now everythings pretty :D

---

### Post by RazorV on 2010-05-04
Great thanks for the info.  I thought I was missing something for min.  Thanks again for the udpate!

Cheers,
Greg
Sarasota, FL

---

### Post by Dimison on 2010-05-04
try beta for Lucid from [http://forums.virtualbox.org/viewtopic.php?f=15&t=30286](http://forums.virtualbox.org/viewtopic.php?f=15&t=30286)

:)

---

### Post by goldshirt9 on 2010-05-04
any difference between this and vmware.

---

### Post by John Bean on 2010-05-04
> **goldshirt9 said:**
> any difference between this and vmware.

You mean other than they're completely different products? In that case - no ;-)

---

### Post by Ginsu543 on 2010-05-04
One is free as in beer and the other isn't? I've heard VMWare has more features (and it should, considering you have to pay for it), but for running Windows XP in a VM guest on my Ubuntu host, VirtualBox has been nothing but phenomenal. I have been running VirtualBox PUEL for Karmic on my Lucid, but I don't see any problems at all so far. I can still sync my iPhone on iTunes (which is what I use Windows for primarily), so I'm good.

---

### Post by Scunizi on 2010-05-04
The PUEL version of Virtualbox and VMWare are both "non-free".. the vbox version isn't because of the usb support and maybe some other code.  That's the primary difference between the PUEL version and the -ose version (free).

VMWare Server is also at no cost.  I ran that for a couple of years while they were in the middle of 2 different control interfaces.. one standard program based vs. web browser access.  I found VMWare to be too heavy and didn't really see the advantage for running a single VM at a time.  Might be different if you were running multiple VM's on a 64 bit system with gabs of RAM and HD space..

---

### Post by Ginsu543 on 2010-05-04
That's why I said free as in beer and not free as in speech. I meant that VirtualBox is no-cost (not that it was FOSS). In any case, I've used VirtualBox for a while now, and I heartily recommend it.

---

### Post by Scunizi on 2010-05-04
+1 for me with Virtualbox as well.

---

### Post by BrainStorms on 2010-05-04
I used VMware Server 1.0.x and 2.0.x, plus VMware Player 2.0.x & 2.5.x on Ubuntu.  Then I tried VirtualBox -- and never looked back.  I highly recommend VirtualBox over VMware's products.

VMware Server is overkill for the average user, unless you need to run/administer a collection of machines.  For running one virtualize machine, it's too complicated and klunky, takes too many windows, and the newer version has to run through a web browser...

VMware Player was better.. but has a few troublesome shortcomings.  One, it cannot create its own VMs; you have to either download one from a third party source or install/run VMware Server to make one for you.  Second, it does not install the VMware Tools (drivers); it doesn't even come with them!  You have to either have VMware Server do it, or get a trial copy of VMware Workstation and extract them (then copy to a CD and manually install in your VM).

No thanks!  Too much admin and hurdle-jumping -- and which is too much to ask of the average user.  VMware Player seems intended to be a product that lets users of the professional versions take their VMs home with them -- not to be a "one-and-only" VM tool.

VirtualBox handles everything: Can create a VM, has a great interface for configuring VMs, automates tool/driver installation, and has decent (real) hardware support.  Plus, you can catalog & even run multiple VMs at the same time -- in a much more elegant fashion.

Otherwise, they're much the same in terms of features & performance.  It's just that VB makes it soooooo much easier to get something up & running.

---

### Post by goldshirt9 on 2010-05-08
well that answered my question.:lolflag:

thanks for that :p

---

### Post by Funkey Monkey on 2010-05-12
Hello Guys,

I got USB to work on my 10.4 Host for VirtualBox.

[LIST=1] I am "pretty" sure that I did not download the OSE version
As per [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")
I added the following to my sources list
```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free 
```
then did ```
sudo apt-get update
sudo apt-get install virtualbox-3.1

```[/LIST]

[LIST=2]Added myself to the vboxusers group[/LIST]

[LIST=3] I installed GuestAdditions[/LIST]

[LIST=4] Read [URL=https://help.ubuntu.com/community/VirtualBox/[/URL] but it says don't follow the instructions for 10.4[/LIST]

[LIST=5] Then used the following code ```
sudo hald --daemon=no
```
[/LIST]

Now go add the usb device open VB -> Settings (for the specific VM) -> USB -> Tick everything --> Then add the decive "FILTER" its a button to the right


PS. I really hope this helps someone...

---

### Post by John Bean on 2010-05-12
Hmm. I installed the non-free version from the Lucid repository yesterday and USB works fine for me without having to run hald... which is what I expected having read the release notes.

---

### Post by Funkey Monkey on 2010-05-13
> **John Bean said:**
> Hmm. I installed the non-free version from the Lucid repository yesterday and USB works fine for me without having to run hald... which is what I expected having read the release notes.

Thanks for the heads up... 

After sudo apt-get update and then sudo apt-get upgrade

I no longer need the hald trick per my previous post above.

---

### Post by John Bean on 2010-05-13
Thank goodness for that. I was beginning to think that mine must be working by magic when I read your post :-)

---

### Post by Funkey Monkey on 2010-05-14
> **John Bean said:**
> Thank goodness for that. I was beginning to think that mine must be working by magic when I read your post :-)

I must confess that I was more than a little annoyed with your post seeing as I googled my ***-off looking for why my VB is not picking up my usb devices.

But yeah thats life, at least we don't have to bother with the Hald trick...

BIG THANKS to the people that fixed the issue, you are HEROES.

(I think we can close this tread now)

---

### Post by 2boats on 2010-05-15
Don't close it yet, please.  I installed Virtualbox, then Windows xp, did all of the upates and everything looked great.  USB doesn't work....read all sorts of posts, the Vbox manual, forums etc.  Seems the most like answer is adding user name to vboxusers.  I get 
adduser: The group `vboxusers' does not exist.

Any suggestions on a next step would be greatly appreciated.  I've been at this for about 6 hours now and would hate to start over if I don't have to.

:(

---

### Post by John Bean on 2010-05-15
> **2boats said:**
> The group `vboxusers' does not exist.

Please explain exactly how (ie the installation method) and what (ie which version) you installed, including the source of the installation. There are various versions of virtualbox from a variety of sources, so it's important to be very specific.

---

### Post by 2boats on 2010-05-15
Thanks for the response.  I closed my eyes and uninstalled the version I'd used. (Virtualbox 0SE from Applications - Ubuntu software centre)  I reinstalled from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) using GDebi Pakage Installer. (My virtual machine was still there!)  Watching the terminal and using the help index I was able to add username to the Vboxusers group.  USB wasn't working yet but now I can go back and try some of the other fixes or I might be able to get around needing it by using a shared folder.

Thanks again!

Reboot fixed all!!:)

---

### Post by John Bean on 2010-05-16
> **2boats said:**
> Reboot fixed all!!:)

Splendid :-)

One point though, it's much better to add the virtualbox repository and use apt to install it rather than manually installing from a downloaded .deb as it sounds like you did. 

The instructions to add the repository are on the download page [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) under "Debian based Distributions".

---

