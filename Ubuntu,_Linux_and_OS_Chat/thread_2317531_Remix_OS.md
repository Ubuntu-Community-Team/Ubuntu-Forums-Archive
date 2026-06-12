---
title: "Remix OS"
date: 2016-03-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Kpenguin on 2016-03-17
Hi everyone,
I recently learned about [Remix OS]("http://www.jide.com/en/remixos-for-pc") and was thinking about trying it on my PC. Has anyone had experiences with this OS? I know Android is based on Linux, so I assume that this is based on Linux too. Any ideas on how I would add this to my grub boot entry, etc.? Please just provide feedback on you experiences with it (if any), what you think about this OS, or help as to how I would install it alongside Ubuntu and Windows.

Thanks!
Kpenguin

---

### Post by montag dp on 2016-03-17
Interesting.  It's convergence, but starting from the opposite side that Canonical is doing.  I didn't look at all the descriptions and videos, but I wonder what their plan is for desktop applications.  Are they going to port open source software or try to get the popular vendors to support their platform?

Edit: or, as seems to be the case at the moment, only support Android applications.  I guess it makes sense if it gains enough traction, because then the desktop software vendors will probably just decide to offer Android versions of their applications.

---

### Post by QDR06VV9 on 2016-03-17
Just Downloading now! But what I have found so far... and don't hold me to this just yet but Androidx86 && Remix OS was going to join efforts.
> Android [isn&#8217;t exactly built for a keyboard and mouse]("http://gizmodo.com/google-pixel-c-review-androids-not-ready-for-a-tablet-1747368432#_ga=1.97940058.431406394.1415821409"), but that hasn&#8217;t stopped [some of us from trying]("http://lifehacker.com/how-to-make-an-android-tablet-work-more-like-a-pc-1462061591"). [RemixOS]("http://www.jide.com/en/remixos-for-pc"), from developer [Jide]("http://www.jide.com/en"), wants to change that by adding a desktop, windowed apps, and more to Android. Here&#8217;s how to try out the *very* experimental alpha.
From here: [URL="http://lifehacker.com/how-to-put-android-on-your-desktop-with-remix-os-1752731845"]http://lifehacker.com/how-to-put-android-on-your-desktop-with-remix-os-1752731845
> With rumors that Google might [/URL][merge]("http://www.pcworld.com/article/2998999/chromebooks/google-didnt-just-kill-chrome-os-but-an-android-merger-seems-likely.html") Chrome OS and Android, and Google's desire to add [split-screen multitasking]("http://www.pcworld.com/article/3013797/android/pixel-c-team-promises-split-screen-multitasking-better-tablet-apps-during-reddit-ama.html") to the [Pixel C]("http://www.pcworld.com/video/60183/googles-pixel-c-is-a-killer-android-tablet-on-a-productivity-mission") with future versions of Android, Remix OS might just be a peek at the future of Android.
 This operating system was created by Jide Technology, a company formed by a trio of former Google employees. Last year, they [showed off]("http://www.greenbot.com/article/2865928/this-microsoft-surface-lookalike-runs-a-productive-version-of-android-instead.html")  a Microsoft Surface Pro-like device running Remix OS. Now, they've made  Remix OS available to download, and you can run it yourself on  practically any computer or virtual machine.

 
This is about 2 months old so some other changes could have been made.
[https://www.reddit.com/r/RemixOS/comments/40htwc/you_can_have_remix_os_on_a_partition_of_a/](https://www.reddit.com/r/RemixOS/comments/40htwc/you_can_have_remix_os_on_a_partition_of_a/)  

To dual boot with Windows
[http://www.techdroider.com/2016/01/guide-how-to-dual-boot-remix-os.html](http://www.techdroider.com/2016/01/guide-how-to-dual-boot-remix-os.html)

And another dual boot option
[https://www.reddit.com/r/RemixOS/comments/40eobe/how_to_actually_install_remix_os_onto_your/](https://www.reddit.com/r/RemixOS/comments/40eobe/how_to_actually_install_remix_os_onto_your/)

If it is the same as andoid and grub is already installed I would just use that. (so don't install their grub)

---

### Post by Kpenguin on 2016-03-17
Thanks for your advice and comments.
> **runrickus said:**
> 
If it is the same as android and grub is already installed I would just use that. (so don't install their grub)
So how would I set it up so GRUB recognizes it as another OS? Could I just install the OS on its own partition, then go to Ubuntu and do something like ```
sudo update-grub
```?

---

### Post by QDR06VV9 on 2016-03-17
Just like this...
[http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html](http://www.webupd8.org/2012/03/how-to-dual-boot-android-x86-and-ubuntu.html)

---

### Post by Kpenguin on 2016-03-17
Ah, cool. I'll try this over the weekend. :D

---

### Post by grahammechanical on 2016-03-17
Last year I got fed up trying to install android-x86. I think it needs a partition already formatted as Ext3 otherwise it won't install.

I wanted to use a certain android app that was available for android and Windows phone but not available for Linux. I have since found another way of doing that. Install Chrome and Arc Welder. Download the application's apk file and it is now possible to run an Android app on Ubuntu.

Regards.

---

### Post by sammiev on 2016-03-17
This a new version to the one I tried late last fall. It did not work well in a VM at all.

A full install to my HDD ran not too bad. It picked up all my equipment with no issues.

Will have to take this one for a ride.

---

### Post by QDR06VV9 on 2016-03-18
Ok for this I installed to a Sandisk Ultra 32Gig USB on windows 10 laptop.
After the install Their grub offered to to boot to windows 10 or Remix OS.
First Boot was a little slow...due to configuring the hardware.
When the desktop finally opened I was pleasantly surprised. Sleek Crisp.
So now I went looking around a bit and found no way to install from Google Play. [s]So I headed off to [http://forum.xda-developers.com/remix/remix-os/app-install-google-play-services-remix-t3292087](http://forum.xda-developers.com/remix/remix-os/app-install-google-play-services-remix-t3292087)
And installed a apk that in turn installed the play store[/s]
**That has a bad installer use instead the link Ringi Provided:[https://groups.google.com/forum/#!to...pc/6jsV0ZB8174]("https://groups.google.com/forum/#%21topic/remix-os-for-pc/6jsV0ZB8174")** 
All in All kind of fun to mess with..and should be very polished when done.
And by the way i did see the boot animation show the Androidx86 Logo before the Remix OS Logo.(Just Saying)

---

### Post by xc3RnbFO8P on 2016-03-18
I installed Remix Os on a Surface Pro 3, and it works fine. You have to install Google Service to install apps.
I Installed it on ScanDisk usb 3 pen 32GB, it have to be usb3!
[https://groups.google.com/forum/#!topic/remix-os-for-pc/6jsV0ZB8174](https://groups.google.com/forum/#!topic/remix-os-for-pc/6jsV0ZB8174)  (this is mobile apk)

[[img]https://farm2.staticflickr.com/1535/25629025361_fb48cbbca6_b.jpg[/img]](https://flic.kr/p/F3KskB)

---

### Post by QDR06VV9 on 2016-03-18
Hi Ringi long time no see..lol
As you can see in my post that was done...but maybe that apk was bad I'll try your link.
Also they mention you had to clear data and cache for Google Play Services && Google Network Services.
But the stand out Warning should be..
> **(Don't open Google Play or login any Google App before reboot).  Otherwise, you will see "Error" while you are trying to download  anything.**
As in my case..

---

### Post by xc3RnbFO8P on 2016-03-18
And it works now?

---

### Post by QDR06VV9 on 2016-03-18
He He...Still Downloading the play store but I am sure it will work..has a different look to the one in my link
so i think i will remove that link and use your provided link for further recommends..
Hey before I forget Thanks for the link.
Yeah Baby now we are cooking...installing software as i type this...So Yes it works now

---

### Post by Kpenguin on 2016-03-21
I currently have it up and running on my computer! It works and looks great. I had to edit the GRUB menu entry file differently than the link runrickus provided said, and I also had to disable secure boot. Here's what the menu entry looks like:
```
menuentry "Remix OS" {
set root='(hd0,9)'
linux /RemixOS/kernel quiet root=/dev/ram0 androidboot.hardware=remix_x86_64 acpi_sleep=s3_bios,s3_mode SRC=RemixOS
initrd /RemixOS/initrd.img}
```

Thanks for your help and feedback everyone!

Kpenguin

---

