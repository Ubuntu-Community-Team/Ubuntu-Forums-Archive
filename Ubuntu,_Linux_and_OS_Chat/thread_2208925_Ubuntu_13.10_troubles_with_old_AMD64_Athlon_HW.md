---
title: "Ubuntu 13.10 troubles with old AMD64 Athlon HW"
date: 2014-03-03
forum: Ubuntu, Linux and OS Chat
---

### Post by QdFPLGz on 2014-03-03
Hi all,
      
      I thought of letting off a bit of steam to ease my frustrations.... :)
      
I've an old Acer Aspire latop with AMD AthlonXP 64bit dual core proc, 1Gb RAM, 160GB hdd, nvidia geforce integrated chipset and broadcom wireless.
It was running ubuntu 10.04 32bit very well and was just solid. I       know I know, i'm an outdated guy,
      but hey, it runs fast and i've had zero problem to date on that       setup.

      Yesterday, I thought I would upgrade my linux laptop       to the latest 64 bit ubuntu 13.10.
      Little did I know it would lead to insane frustration. I've been       very lucky with linux so far, in that everything used to work will
      TILL NOW i.e. hehe.
      
      So me thinks - "if i install 64 bit latest ubuntu, i will get       double speed" - ahhaha that has to be the biggest joke.
      I go ahead and download 64bit ubuntu 13.10 iso.
      Using Unetbootin I create bootable usb, plug it in and install.
      
      After install, I see that ubu64 is using gallium nvidia opensrc       drivers, which provides a good full screen res,
      but 3d acceleration is slow. I also notice Unity is a damned and       doomed UI, it is utterly slow and useless.
      Anyway, my main idea was I will install my broadcom and nvidia       graphics drivers, then install the cinnamon window mgr
      and kick out unity. I'd seen Cinnamon in action and had liked it.
      
      So first, i look for the usual 'additional hw drivers' thing in       ubuntu - ITS NOT THERE!
      heck, so then i see if i can install the drv pkg .deb from       synaptic - SYNAPTIC IS ALSO NOT THERE!
      heck, i go to software centre, which takes an age to open (in fact       everything takes an age to open in ubu64 unity UI).
      then search for synaptic and here is the thing, there is no       'install' button !!!!, only one 'get info' button.
      Anyway, i double click on synaptic, and it asks - "this requires       the use of 'universal' source" - what the hell ! 
      How will any new user understand what the heck that means ? Anyway       I say 'yes'.
      Now there is some progress bar, but it does not progress       much.....screw it i say, and i kill the damned thing.
      Open terminal - 'sudo apt-get install synaptic' - gives error msg,       saying  "/var/cache/apt...blah blah locked'.
      Logout login again and hit the cmd, this time it installs -       finally !
      Now I open up synaptic, and reload the repos, I see that the 'additional hw drivers'         section has been moved here. - heck ?
        Anyway i see my broadcom STA 802.11 listed, and i click that         & select 'apply changes' , again progress bar starts and 
        then no progress.... what? Not again!!!
        So I close it, restart synaptic, search for the bcm43xx-kernel-src         pkg and install it manually,
        this builds and installs the wireless .ko driver.
        I then reboot and bang!!! kernel crash - good old         cfg80211/mac80211/workqueue stack dump.
        God !, I use pen drive, reboot to live cd OS, search for the         bcm43xx .ko driver (thankfully during install I had observed the         path),
        and delete it. After reboot , system now boots into the desktop.
        Then I search the net for how to's.
        Seems simple enough - you must install NOT the "bcm43xx-kernel-src" but the         "bcm-fwcutter" pkgs.
        What in gods name is fw cutter? How will an ordinary user know         that cutting the fw will result in wifi working ?
And what is the meaning of cutting firmware ?
        This is absolutely horrible. No wonder many people hate linux         for day to day use!
        Anyway, after installing it and rebooting, i get wifi working.
        So now I install nvidia drivers and reboot. But still unity is         running very very slowly....
        Anyway, i install the cinnamon pkgs and logout and log in to a         cinnamon desktop session..only only, it DOES NOT START UP.
        says - 'cinnamon crashed etc...'.  or freezes on the first click.
        Hell, I got fed up and install plain ol' gnome and login to         that.
        Now this runs well, but still not as fast as my 32bit old         ubu10.04 - still don't know why? Why is 64bit so slow ?
        Anyway I think i will install compiz on this and get back my ol'         desktop.
        But heck even compiz is slow. effects are in slow motion, worthless....
        
        By now i've wasted atleast 3-4hrs.....
        
        Okay, what is the solution - ditch the goddamned ubuntu and go         for linux mint.
        Again I download linux mint 15 64bit.
        Install it and again redownload the drivers etc...
        This linux mint 15 has 'cinnamon' as the default window mgr.
        I see that it is faster than unity, but still slow.
        If i do some multitasking, it becomes slow, very frustrating.
        
        What I thought would take a max. of 3 hrs, took up more than         10hrs of my time.
        
        What is wrong in todays software world that every new ver. is slower         than the prev ver. ?
        I don't know what to do now, I think I will install MATE (linux         mint's plain ol gnome environment)
        and then install compiz on it and see. If this is still slow (as         I expect it to be)
        I will go back, back in time and install ubu10.04 64 bit. If         this is also slow - again as I expect it to be,
        I will rewind further back in time and go back to ubu10.04 32         bit and restore everything the way it was manually.
        Or i may try an XFCE desktop, I have heard its 'blazing' fast -         ******** ! Not till I've tested it and certify it as 'blazing'..
        Note: linux desperately needs better testing             of its existing code base, rather than release a new ver.             every 6 odd months.
Also, it desperately needs to             learn from windoze and get a good device & driver             manager.

---

### Post by David D. on 2014-03-03
Welcome to the forums.  Sorry to hear that you had such a bad experience.  I understand your need to vent.

Your computer just meets the MINIMUM system requirements for 13.10, so your system will be slow, especially with Unity.  As an alternative you may like Xubuntu better than Ubuntu as it is lighter in it's requirements and is closer to what you are used to using.

---

### Post by mastablasta on 2014-03-03
are you sure it's the OS that is slow and not your computer? :-)

Try Xubuntu. The reason for slowness is the graphics card. Unity is 3D accelerated now as is Cinnamon. so without a good GPU things will be slow...

luckly there should be gnome panel available, in 12.04 there is Unity 2D.

regarding hardware drivers. before it was jockey, but that had to be replaced. the hardware drivers is now in software center in sources.

Unity (as well as cinnamon) was a response to Gnome3 which i still do not quite  get it.

---

### Post by mörgæs on 2014-03-03
If you have only 1 GB of memory I recommend a 32 bit ISO, also if your processor is 64 bit. 
Lubuntu 13.10 is worth considering.

---

### Post by Bashing-om on 2014-03-03
QdFPLGz: Hi !

My 2 cents worth: I am running 13.10 on dual core Athlon system, and it screams as compared to earlier versions. The difference is, I do have 4 Gigs of ram, and an old ATI graphics card (open source driver).

I was very impressed with 13.10 when I installed it . -much faster !

[INDENT][INDENT]that's my story -> and
[/INDENT][/INDENT]

---

### Post by QdFPLGz on 2014-03-03
Good to know it does run well on other systems.
I have now installed Xubuntu 13.10 64 bit, and it really is 'blazing' fast !
Compiz also works, but seems to crash some times.
Could be some compiz plugin which is causing this, will need to find out which one and disable it.
But I think the days of me using Ubuntu on this particular hw are gone :( 
I'll stick with Xubuntu.

---

### Post by Bashing-om on 2014-03-03
QdFPLGz; Great !

Pleased you are up and running.

On the compiz issue, open a new thread to gain a greater audience to those familiar with that issue.

As this issue is completed, please mark this thread solved : 1st post -> thread tools

and
[INDENT][INDENT]any 'buntu is better
[INDENT][INDENT]than no ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT]

---

