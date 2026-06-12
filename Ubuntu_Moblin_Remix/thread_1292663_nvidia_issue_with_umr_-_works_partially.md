---
title: "nvidia issue with umr - works partially"
date: 2009-10-16
forum: Ubuntu Moblin Remix
---

### Post by klaus.h on 2009-10-16
Hi! I am new here, sorry for making some noise.

I have a point-of-view netbook with nvidia ion graphics 

* Ubuntu on ION works fine.
* UMR works with standard driver, but slow
-> UMR on ION works fast but partially: The menu bar works, but the white desktop area stays blank

I checked out the umr image with 2.6.31-13-generic kernel, to install the proprietary nvidia driver using Envy tool I updated to 2.6.31-14-generic. Result see above.

The 2.6.31-14 image did not install.

Any suggestions what to do?

Thanks a lot

---

### Post by igknighted on 2009-10-16
You definitely need the proprietary driver.  The Moblin interface requires 3d acceleration, so nv and nouveu are out.

As for getting the proprietary driver to work, a couple thoughts:

1) have you tried the version from the repo's? Is there an ION driver in there even?

2) do you have the kernel headers and build-essential packages installed?  Envy will have to build against the kernel and will need those tools.

3) If you've done the above and it still fails, could you run envy from the CLI and post the specific error it outputs?

4) If all of the above fail, read this: [http://lists.moblin.org/pipermail/dev/2009-June/005051.html](http://lists.moblin.org/pipermail/dev/2009-June/005051.html).  I doubt this is the issue, because this package was from the Fedora-based Moblin release, and not Ubuntu's xserver.  But it is possibly an issue in Ubuntu as well.

EDIT: Unfortunately, since Moblin is an Intel project, there hasn't been much work into getting the proprietary drivers working with them.  Not to mention, almost all atom-based netbooks had intel graphics until ION came out recently, so there may be bugs that simply haven't been worked out yet.  If there was an open nvidia driver...

---

### Post by klaus.h on 2009-10-16
Hi, thanks for the quick reply - I did 1 to 3,

running the proprietary nvidia driver does work, I will look into 4 ... thanks for the hint.

(Remark: the funny thing is, basically it works, because the top menue is here and is functioning. Just the application icons are missing - thus I think it is more a desktop issue ...)

---

### Post by P4man on 2009-11-08
Did you get it to work? I tried the moblin remix on my desktop with an nvidia 7900 card. Without drivers its unbearably slow, with restricted drivers I get the same as you; the interface seems to work mostly but all screens are empty and white... :(

Shame, as I wouldnt mind running this on my laptop otherwise, but since its also got a nvidia card Im not even gonna bother for now.

---

### Post by demoneivo on 2009-11-16
Hi all!

I have also tried to install ubuntu moblin remix on my unibody macbook
When istalled, everything was laggy and the system was pretty unusable
I decided to install restricted nvidia driver (my macbook has a 9400M nvidia chipset) and after the reboot, the top bar was perfect and the system smooth but i only saw white pages when clicking on the top (myzone/application etc.etc...)
I tried clicking browser and the application itself works!! I could write text and navigate easily..

Does anybody know what the problem is?

---

### Post by P4man on 2009-11-17
the problem is intel ;)
moblin was written by intel initially specifically for their hardware, it includes intel gpu drivers. So far it just doesnt seem to work properly with any onther videocards.

---

### Post by demoneivo on 2009-11-17
> **P4man said:**
> the problem is intel ;)
moblin was written by intel initially specifically for their hardware, it includes intel gpu drivers. So far it just doesnt seem to work properly with any onther videocards.

I think that the problem is in the graphical environment and the graphical libraries...
Even if Intel released moblin for intel integrated video chipset, in Ubuntu Moblin Remix all restricted drivers are available (in our case NVIDIA drivers).
So the problem can be in this drivers (not intended to use in moblin graphical environment) or in the graphical environment (not intended to be used on Nvidia video chipset).

Do you know possible solutions?

---

### Post by P4man on 2009-11-17
> **demoneivo said:**
> I think that the problem is in the graphical environment and the graphical libraries...
Even if Intel released moblin for intel integrated video chipset, in Ubuntu Moblin Remix all restricted drivers are available (in our case NVIDIA drivers).
So the problem can be in this drivers (not intended to use in moblin graphical environment) or in the graphical environment (not intended to be used on Nvidia video chipset).

Do you know possible solutions?

Dont think there is one at this point, certainly not with the ubuntu remix. I wanted to try Mandriva  2010 which can load Moblin as one of its desktop managers, but I havent succeeded yet as the mandriva live cd won't boot on my system for some odd reason.

---

### Post by demoneivo on 2009-11-17
> **P4man said:**
> Dont think there is one at this point, certainly not with the ubuntu remix. I wanted to try Mandriva  2010 which can load Moblin as one of its desktop managers, but I havent succeeded yet as the mandriva live cd won't boot on my system for some odd reason.

If ypu succed in installing mandriva, can you please let me know if you succeed to load moblin?
I will also try mandriva 2010 :D
I want moblin interface on my macbook in order to use it as a sort of small media center...

PS. I found this website, please read the last post..
[www.madeo.co/uk/?p=40](www.madeo.co/uk/?p=40)
Moblin developpers suggest to uninstall nvidia restricted drivers and to use free driver and libraries but in this way the system is slow and buggy.
The most important thing is this letter is the fact that developpers admits that there is a problem in clutter-glx implementation 
"It seems that NVIDIA's proprietary libraries for acceleration such as
/usr/lib/libGL.so.190.42
/usr/lib/xorg/modules/extensions/libglx.so.190.42
make troubles with clutter-glx implementation."

At least we now what the problem is! ;)

The s

---

### Post by maubp on 2010-01-29
I've been trying both the "official" Mobile 2.1 and the Ubuntu Mobile Remix of Karmic on an Acer Aspire Revo 3600 (with nVidia ION graphics) and it is very very slow, and won't complete the nVidia driver installation :(

---

