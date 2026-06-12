---
title: "Utopic final Beta testing is now in progress"
date: 2014-09-23
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-09-23
Most of the images are now available on the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/324/builds](http://iso.qa.ubuntu.com/qatracker/milestones/324/builds)

You can rest assured that there will be several rebuilds before Thursday.

If you're so inclined join the fun and please report any bugs on the QA Tracker :D

---

### Post by Elfy on 2014-09-23
just a quick note - if you try with a vm I am more or less completely positive that you'll get a whack from [lpbug]1371651[/lpbug]

---

### Post by ventrical on 2014-09-24
Still no normal startup boot screen, ie; Try Ubuntu , Install Ubuntu.

Just 

boot: live, live-install .. etc... is that what they mean by bug [lpbug]1325801[/lpbug]?

---

### Post by Elfy on 2014-09-24
> **ventrical said:**
> Still no normal startup boot screen, ie; Try Ubuntu , Install Ubuntu.

Just 

boot: live, live-install .. etc... is that what they mean by bug [lpbug]1325801[/lpbug]?

re that bug - I'm not sure, I know that I get that com32 issue from unetbootin and have to *unetbootindefault* from the boot: prompt it drops to

---

### Post by sammiev on 2014-09-24
> **Elfy said:**
> re that bug - I'm not sure, I know that I get that com32 issue from unetbootin and have to *unetbootindefault* from the boot: prompt it drops to

Like wise when I tried it yesterday. Got away with ---try1. Otherwise no issues.

---

### Post by kansasnoob on 2014-09-24
No rebuild yet :shock:

This is unusual with only about 27 hours to go.

---

### Post by ventrical on 2014-09-24
> **kansasnoob said:**
> No rebuild yet :shock:

This is unusual with only about 27 hours to go.

It's impossible to do any of the live boot test cases with the way the .isos are booting up !

Family?. Where?

---

### Post by kansasnoob on 2014-09-24
> **ventrical said:**
> It's impossible to do any of the live boot test cases with the way the .isos are booting up !

Family?. Where?

And the installer is almost unusable. Sure we "in_the_know" old-timers can work around it, but I've never seen quite such a mess.

---

### Post by christopher9 on 2014-09-24
I backed down to 14.04....too much drama!  Seems to get worse with each software update....good thing Mate Desktop works with 14.04 LTS!

---

### Post by Elfy on 2014-09-25
> **ventrical said:**
> It's impossible to do any of the live boot test cases with the way the .isos are booting up !

Family?. Where?

Bit over the top :)

I've booted it fine with a vm - I can't reboot without starting lightdm or changing it to use systemd 

Booting from USB is an issue yes :)

---

### Post by ventrical on 2014-09-25
> **Elfy said:**
> Bit over the top :)

I've booted it fine with a vm - I can't reboot without starting lightdm or changing it to use systemd 

Booting from USB is an issue yes :)

 Oh ... it boots fine (here) and installs just fine but , as I mentioned above, (and quoted the test case). We can't perform these test cases unless it boots into a working Ubiquity. This problem has been systemic throughout this development cycle. As kansasnoob mentioned "we_in_the_know oldtimers" can navigate around the problem but this is not the point I am trying to make. The q/a tracker is asking us to perform test cases that are not possible in some instances, especially at startup/boot-up.

Regards..

---

### Post by Elfy on 2014-09-25
Then I hope you're marking the tracker as a fail :)

---

### Post by lamb123 on 2014-09-25
I tried last beta and was unable to boot: com32 or something

Is it fixed now?

---

### Post by ventrical on 2014-09-25
> **Elfy said:**
> Then I hope you're marking the tracker as a fail :)

Yessir .. of course I did :)

[http://ubuntuforums.org/showthread.php?t=2245567](http://ubuntuforums.org/showthread.php?t=2245567)

---

### Post by kansasnoob on 2014-09-25
> **lamb123 said:**
> I tried last beta and was unable to boot: com32 or something

Is it fixed now?

No. They seem to still be stuck on the 20140923 images and they're still borked :(

Unless they pull off a miracle I hope they have the good sense to just delay the final Beta. It's a bummer for us independent QA testers - I mean it's virtually impossible to complete the needed tests in this short of a time frame.

---

### Post by ventrical on 2014-09-25
> **kansasnoob said:**
> No. They seem to still be stuck on the 20140923 images and they're still borked :(

Unless they pull off a miracle I hope they have the good sense to just delay the final Beta. It's a bummer for us independent QA testers - I mean it's virtually impossible to complete the needed tests in this short of a time frame.
+1

I hope the devs are listening.

---

### Post by ventrical on 2014-09-25
> **lamb123 said:**
> I tried last beta and was unable to boot: com32 or something

Is it fixed now?

In most cases  if you hit the Tab key it will give you the command line options;

boot: live, live-install..etc.

After typing in 'live' <Enter>, the live version of Utopic will load up. But we want to test the newer Ubiquity pre-empt and that's just not there atm. Hasn't been most of this cycle, It was there much earlier on but we've been stuck with this 'pink elephant' (no offence to elephants) for months now.

---

### Post by lamb123 on 2014-09-25
still nothing...oh well

---

### Post by kansasnoob on 2014-09-25
Ubuntu GNOME just marked theirs READY ](*,)

That does it for me ................... if they consider that mess READY this'll be my last QA testing cycle :mad:

---

### Post by Elfy on 2014-09-25
I suspect that we'll be having to make Xubuntu ready as well - the bugs *we're* seeing won't be fixed this side of 'in about 2 hours' 

Certainly the lightdm/linux/plymouth bug won't be

---

### Post by Elfy on 2014-09-25
> **Elfy said:**
> I suspect that we'll be having to make Xubuntu ready as well - the bugs *we're* seeing won't be fixed this side of 'in about 2 hours' 

Certainly the lightdm/linux/plymouth bug won't be

<infinity> elfy: Yeah, we're going to ignore that issue and fix it ASAP after the beta.

As suspected :)

---

### Post by kansasnoob on 2014-09-25
My proposal for the Ubuntu GNOME Utopic Beta 2 release notes:

[https://lists.launchpad.net/ubuntugnome-qa/msg00559.html](https://lists.launchpad.net/ubuntugnome-qa/msg00559.html)

> I realize the state of the current iso images is beyond our control, at least the upgrade tests passed OK though, but I'm quite serious when I say this;


The Utopic Beta 2 Release notes should simply recommend using the Beta 1 images or upgrading from Trusty (perhaps with a reminder to 'ppa-purge' any PPA's in use). In their current state the images should NOT be used for anything but "entire disc" installs when there is only one disc installed in the machine and the plan is to erase all existing data and OS's on the machine.


Sorry to come across as a Debbie Downer but those are just the facts as I see them.



---

### Post by ventrical on 2014-09-25
Just zsynced utopic-desktop-i386.iso.

Tried it .. same ..

boot:

---

### Post by ventrical on 2014-09-25
This is 14.10 from the May 20th .iso

Boots just beautifully.:)

---

### Post by stoneguy on 2014-09-25
For anyone really twitchy for something to test, here's beta2 for [ Ubuntu-MATE-Remix]("http://linux.softpedia.com/get/Linux-Distributions/Ubuntu-MATE-Remix-103505.shtml")

---

### Post by sammiev on 2014-09-25
Found another bug with Xubuntu, No lock on the VPN icon when using wired connection ( but is working correctly - just eye candy ). All is fine on wireless.

---

### Post by sammiev on 2014-09-26
Well I was setting up a new computer to and tried gnome 14.10 using Unetbootin which would not even boot. Then tried Startup Boot Creator and I had full menu and everything worked as it should. Never had Unetbootin fail and Startup Boot Creator work.

---

### Post by kansasnoob on 2014-09-27
> **sammiev said:**
> Well I was setting up a new computer to and tried gnome 14.10 using Unetbootin which would not even boot. Then tried Startup Boot Creator and I had full menu and everything worked as it should. Never had Unetbootin fail and Startup Boot Creator work.

Odd, I've had just the opposite experience:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1325801)

I'm Erick Brunzell on Launchpad if you care to plow through all of that. If you have a Launchpad account and your experiences are different than mine you should say so there.

---

### Post by sammiev on 2014-09-28
> **kansasnoob said:**
> Odd, I've had just the opposite experience:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1325801)

I'm Erick Brunzell on Launchpad if you care to plow through all of that. If you have a Launchpad account and your experiences are different than mine you should say so there.

Done

---

### Post by kansasnoob on 2014-09-28
> **sammiev said:**
> Done

Thanks. The devs working on that need to know that different users are encountering different behavior. In my case the only failures have occurred when creating a live Utopic USB with 'usb-creator' in either Trusty or Precise.

---

### Post by syntaxerror74 on 2014-09-30
First of all, I was really "pretty p....d off..."
Just after doing the Final Beta upgrade on my Lubuntu Utopic, I could no longer log in graphically into my PC as a regular user (**root worked** though). Of course, (regular) username+pw worked, too, but not at the graphical login screen. Screen went black, and I always got warped back to the screen where I were before. 

The solution was to *cat* ~*/.xsession-errors* ! It turned out that I had defined an array of constants in my ~/.profile as a test, which apparently was no longer accepted after the upgrade (complaining about something like "'(' unexpected" IIRC). (However I'm seriously wondering why this GOT parsed in .profile without a hitch shortly before the upgrade?!)

---

### Post by slickymaster on 2014-09-30
I can't honestly understand why are you > pretty p....d off...
Utopic 14.10 is in development, hence unstable and so busted images are/ought to be expected during development.

---

### Post by syntaxerror74 on 2014-09-30
You might understand when you hear that the upgrade from Trusty to Utopic (Alpha2) was one of the smoothest I've ever experienced...

---

### Post by ventrical on 2014-09-30
I updated a system the other day and lost network-manager. Also .. it has switched to llvmpipe about 6 weeks ago but now it is back to normal Unity 3D with an Intel driver that I've never heard of before - so busted stuff is expected about this time but it should clean up soon as final release is only about two weeks away.

Regards..

---

### Post by Frogs Hair on 2014-09-30
I installed Friday 9-26 so no updates until Monday. Since then there has been over 50 packages updated  , but nothing unusual to report so far.

---

### Post by christopher9 on 2014-09-30
Ubuntu Mate 14.10 Beta2 installed for nearly a week now with 0 issues....

---

### Post by ventrical on 2014-09-30
> **Frogs Hair said:**
> I installed Friday 9-26 so no updates until Monday. Since then there has been over 50 packages updated  , but nothing unusual to report so far.

My problem was with an ethernet cable and a D-Link router. Since todays update and fix it's back to llvmpipe but I just use Gnome-Metacity on that machine until I install a new nVidia card. The nouveau-intel driver seems not to be working and it keeps piping over to llvmpipe.  gnome-metacity is not really that bad. It fact when Unity goes south or gets borked, gnome-metacity seems a more reliable alternative.

---

### Post by Frogs Hair on 2014-09-30
> **ventrical said:**
> My problem was with an ethernet cable and a D-Link router. Since todays update and fix it's back to llvmpipe but I just use Gnome-Metacity on that machine until I install a new nVidia card. The nouveau-intel driver seems not to be working and it keeps piping over to llvmpipe.  gnome-metacity is not really that bad. It fact when Unity goes south or gets borked, gnome-metacity seems a more reliable alternative.

I'm running Unity and the Gnome Shell 3.12 on an AMD x II CPU, 8 series nVidia graphics card with nouveau drivers.

---

