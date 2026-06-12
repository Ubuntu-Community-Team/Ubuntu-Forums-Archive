---
title: "(K)Ubuntu Feisty - A disappointment"
date: 2007-04-21
forum: Testimonials &amp; Experiences
---

### Post by The Keeper on 2007-04-21
Today I've been using both Ubuntu and Kubuntu variations of Feisty. I have to say that I am very disappointed at Ubuntu's ability to provide stable and bug-free releases at launch. Here's my verdict on (K)Ubuntu's shortcomings starting with Ubuntu.

**Ubuntu**
- For the first time in Feisty, the open-source R300 ATI-driver finally works on my Radeon X850. Previously all I got was a black screen until I installed fglrx drivers. Unfortunately the R300 driver causes random freezing in Ubuntu, a cold reboot was required when a freeze occurred. Installing the fglrx drivers solved the problem.

- Audigy 2 ZS doesn't work out of the box in Ubuntu. First I need to blacklist the modules that are loaded for my disabled on-board audio. After that Audigy still didn't work until after I fiddled around with mixer settings and audio started to work suddenly. For the record, master or pcm volumes weren't muted. It has been said many times in these forums that unselecting "Audigy Analog/Digital Output Jack" solves the problem. Well it doesn't. While sound didn't work at first even though it was selected, sound started working after the setting was unselected and re-selected again. Additionally this problem also affects Ubuntu liveCD where there seems to be about 30% change for audio to work when liveCD's Gnome starts.

- ubuntu-restricted-extras depends on msttcorefonts. While those fonts may see some use in word processing applications, many websites become hideously ugly in their fonts once msttcorefonts are installed. Apparently font smoothing just doesn't work properly on MS fonts under linux. Websites look so much better with standard (K)Ubuntu fonts, even though not as good as in Windows XP/Vista or OS X. And what's with ubuntu-restricted-extras omitting gstreamer0.10-plugins-bad and -multiverse?

- For some reason I couldn't get DVD's to mount at first. I had to insert a CD into the drive, eject it and then insert a DVD to get it mounted. I thought this was an isolated incident until I tried Kubuntu.

- Totem is ill suited to play DVD's. It doesn't seem to support DVD menus at all making it totally useless for viewing DVD's. Not acceptable for the default video playback application. For the first time WMV/WMA worked pretty well without w32codecs in gstreamer. But WMV streaming sometimes causes video corruption, definitely better than no WMV/WMA support though.

**Kubuntu**
- Kubuntu has a horrid support for in-browser streaming media playback. I had to install Totem and gstreamer plugins to get decent support for whatever streaming media websites have. Not only that but libxine (libxine1-plugins metapackage) seems to have very poor support for streaming media as it refused to play majority of said media in Kaffeine. When it comes to media playback support, today gstreamer wins libxine hands down.

- When I tried to test DVD playback, I couldn't get any DVD's to mount, including data DVD's. Not even the trick I used in Ubuntu helped. So I searched these forums and found out that there was a DVD mounting bug in Debian Etch, it was patched before Feisty was released but the patch never made it to Feisty. Seriously, what the heck? A bug like this is major and isn't fixed before release? Well, I got DVD mounting to work by creating a new link to DVD device to desktop.

- Both the open-source R300-driver and Audigy has been working for me under Kubuntu fine ever since I installed Kubuntu. I haven't installed fglrx or blacklisted on-board audio modules.

- Unfortunately for Kubuntu, for some reason co-operation between Ubuntu and Kubuntu teams seems to be somewhat lacking because Kubuntu always seems to be missing a few new Ubuntu features. This time missing from Kubuntu is restricted device manager at least. Haven't found more than that but I've only used Kubuntu for a short time.

**Conclusion**
It feels like this supposedly beginner friendly distro's developers put everything they have into developing new features and improving old, but in the end does testing half-assedly resulting in a buggy release. Perhaps 6 month development cycle just isn't enough to test and stabilize a whole distro even though that may be the case with a desktop environment (Gnome)?

If it would mean stable and very bug-free releases right from the start, I wouldn't mind waiting 12 months between releases. Doubling the time for development cycle would also double the time used for testing after feature freezes. Just my two-eu-cents.

It also has me wondering why the two most critical of the issues I encountered in Ubuntu weren't present in Kubuntu. With these bugs present, Ubuntu still isn't yet ready to replace Windows XP, Kubuntu is much closer to achieving that goal but is shadowed by always lacking some new features that made it to Ubuntu. Edgy had a shorter development cycle which was also shown in the quality as it too had a lot of bugs when it was released, many of those weren't even fixed and are still present in Feisty, albeit maybe slightly different. But this time Ubuntu developers don't have an excuse, Feisty had full 6 month development cycle which according to them, should provide enough time to create a rock solid distro.

Well, here's hoping Gutsy Gibbon shows some guts and provides us a rock solid distro worth recommending to everyone.


Edit: Addendum to the original post. The R300 driver also causes freezing under Kubuntu, but happens a lot more rarely than under Ubuntu.

---

