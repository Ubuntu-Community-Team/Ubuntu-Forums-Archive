---
title: "Ubuntu's extended ECO system is letting it down (Packages not maintained by Ubuntu"
date: 2013-06-08
forum: Ubuntu, Linux and OS Chat
---

### Post by LegacyOS on 2013-06-08
[B]Hello those who have the power to feed info to main developers of Ubuntu.
[/B]I develop Legacy OS Linux for the poor and in no way is this a plug to get Ubuntu users interested in trying Legacy and in reality if your Hardware runs Ubuntu then you have no need for Legacy OS. I only mention this as I know as a developer that a lot of work goes into making a release stable and usable.
My 77 year old father has a 64 bit Winows 8 Laptop he installed Ubuntu 13.04 on by himself. A week ago he wanted to convert a video to a different format so I installed  Avidemux and restricted extras and processed to do the conversion. As it was a two pass conversion the first pass went fine. After 45 minutes Avidemux crashed and we got a segment fault from the "lame" executable as Avidemux tried to convert the audio expect of video. Inexperienced Users would blame Avidemux and tell their friends "Don't use Avidemux as it crashes in Ubuntu 13.04" it degrades Avidemux's reputation and Linux on a whole for being an Operating System whose Apps are broken.
Now is it the "lame" developers fault? maybe? I think the real truth lies somewhere in the updates that occurred within Ubuntu's main core of packages. As ubuntu's focus was to make the Packages they maintain compatible with each other for 13.04, the fact that their actions made "lame" incompatible with at least their 64 bit version of Ubuntu 13.04 on all or maybe just certain hardware would never has occurred to them.
This raises the real reason I'm posting this. Ubuntu's eco system must extend past its current level. Imagine I buy a Ubuntu tablet when it's released having taken the extra risk over ipad and Android on an unproven product only to discover when I install extra Apps their broken.
Ubuntu and Mark must at all costs product a product that exceeds those offered by Apple and Google. This really is a one shot deal. Microsoft has discovered with the Windows Phone that buyers ask their friends and family what their using and almost all of them say they brought Apple or Android. I love the fact that Microsoft are being treated like a second rate cousin or even worse forgotten all together in consumers minds when buying phones. Now they know what it feels like for those trying to release products that fail due to no fault of their own.

I love Linux with all heart and know it will become the Desktop system of choice in the future. Behind the scenes it taking over the worlds infrastructure.

What Ubuntu, Redhat, SuSe, Debian etc developers have to do is communicate with those developers writing packages like "lame" to compile them against new releases to confirm they don't break before making them available. It is a mammoth task which requires 1000's of users help to complete.
Yes there are bug lists, LTS releases which gives a release more time to mature in to something stable and usable. Maybe 12.04.4 will have fixed most problems but hey here comes 14.04 to start the cycle again.

Before thinking Ubuntu TV, Phone and Tablet I hope the Ubuntu team really test the most commonly install packages current outside their maintained repository to confirm they don't segment fault etc. Here for the first time is the ability for Ubuntu to have full control over the Hardware Ubuntu will be installed on. Just imagine Libre Office, Firefox, VLC, XBMC to name a few segment faulted on someone's new shiny Ubuntu tablet! Would the user feel great about their purchase? You know and I know that Ubuntu won't let this happen. They need to use the same mentality for the next level of Apps as well. If my favorite app was Mypaint to discover it segment faulted would be just as unforgivable in my mind as finding Libre Office didn't work as this was the reason I brought the Tablet in the first place.

Lastly while this appears to be my first time posting here, this is not the case I just forgot what user login I used in the past.

This post isn't for my benefit as Legacy OS doesn't segment fault while converting video's with Avidemux. It's advice for Mark and Ubuntu in general.
Mark Bloody test your new exciting Products and if you want to release in a curtain time frame employ more testers to allow for the release of a product that makes Apple, Google stand up and take note there's a new player in town. OH yea I forgot to mention that other software conpany that was popular awhile back, can't seem to recall its name? LOL!

---

### Post by zombifier25 on 2013-06-08
It's not Ubuntu's job to make sure that apps outside of the repository works. Why should they? If they crash, it's the developers' fault.

It IS their job though, if a package in the repo does not work (such as, almost every apps you mentioned). But this is a job they have been doing for a long time now, testing all packages so that they work. Have you really investigated the Avidemux crash, or you just posted it here? If you have a problem, post so that other people can help (also take note that 13.04 is not LTS, and I doubt they will use a non-LTS version on the tablet)

---

### Post by LegacyOS on 2013-06-08
Hello zombifier25,
I require no help to fix anything. It is in Ubuntu's interest to extend their support for any package that will find its way on to their tablet / phone. Maybe not allow a package in to the repositories related to the tablet and phone unless they are 100% tested by the programmer who created the app. 

I control and test every app that is included in Legacy OS. If I can do it why can't a company with $$$$ like Ubuntu. lame affects not just Avidemux but countless other multimedia apps in Ubuntu's respository. Fix lame fixes so much more. I want user's to say "Ubuntu just Works" not it works most of the time.

---

### Post by 3rdalbum on 2013-06-09
I'd agree with the LegacyOS guy. You can't guarantee that a program will work fully in any given version of Ubuntu. Sometimes it's the developer's fault, or to be more precise it's that the programmer has abandoned their interest in the program and no longer maintains it to be sure that all its functions still work in new versions of Linux distros. Sometimes it's Ubuntu's fault for setting a wrong configuration option in a dependency. Sometimes it's an unrelated developer's fault, for instance, FFMPEG changed its encoder names **yet again** and broke all programs that use ffmpeg.

It doesn't matter that "Oh, this has been fixed in the latest development build of Ubuntu 13.10" - if it doesn't work in a supported version, that's a big fail. And I see it quite often. And I also have to admit that I'm guilty of the "developer abandoned their program" sin. Doesn't mean that I haven't let Ubuntu down.

---

### Post by FakeOutdoorsman on 2013-06-09
> **3rdalbum said:**
> Sometimes it's an unrelated developer's fault, for instance, FFMPEG changed its encoder names **yet again** and broke all programs that use ffmpeg.

I can't recall a time when the name of any encoder in ffmpeg has ever been changed. Or did you mean something else?

---

