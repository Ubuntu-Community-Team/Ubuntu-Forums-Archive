---
title: "Help: Which to install Precise Pangolin OR Raring Ringtail?"
date: 2013-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by gencon on 2013-05-18
I've been using Lucid Lynx LTS since it was released, but since its desktop support has now ended I am going to do a clean install, so I have a choice...

Should I install Ubuntu 12.04 LTS Precise Pangolin OR 13.04 Raring Ringtail on my desktop? Either way it will be a clean install from DVD of the 64 bit version.

I can't seem to find any clear descriptions of how they actually differ. Various threads on ubuntuforums have confused the issue for me, some say 13.04 is fantastic, others that it is not... BUT I can't find any direct comparison between the 2 versions which is strange because they are the 2 versions on offer on the ubuntu.com download desktop page.

Can I have so advice about what the pros and cons are? [I know 13.04 offers no LTS, but that's not a major concern for me now.]

Many thanks.

---

### Post by ibjsb4 on 2013-05-18
12o4 is supported for 5 years.

13o4 is supported for 9 months.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by gencon on 2013-05-18
Yes I know the support time lengths and I should have said that I've already read the release notes of both.

What I'm after is more of a *general user experience* difference between the 2, rather than a technical difference telling me which version numbers of various pieces of software the releases offer. e.g. LibreOffice 3.5.4 (Precise) vs LibreOffice 4.0 (Raring) won't really make any odds to me.

Cheers.

---

### Post by grahammechanical on 2013-05-18
They are the two versions on offer because they are the latest Long Term Support release and the latest Standard release. The answer for the situation that you are in is to download and burn the ISO image of each version and run it as a live session. Then you will see for yourself. I cannot understand those people who upgrade and then say they do not like what they have got and can they go back to what they had without re-installing. We do not pay for Ubuntu. So, what prevents us from seeing for ourselves in a live session and making an informed decision.

You should also be aware that installing 13.04 will mean that you will have to upgrade or fresh install 13.10 and the same for 14.04. The nine months support period for Standard releases is not sufficient to by-pass the next version of Ubuntu.

The basic pattern of Unity is the same in both versions but the Dash is much quicker. Memory usage as measured by System Monitor is much less, down from near 70% on 1GB of RAM to just above 50%. The icons have been designed by an expert. The utilities have been refined. Additional Drivers is no longer in its own utility but a tab in Software Sources now called Software & Updates. Many of the utilities are much less complicated and easier to use. Software Updater gives more human descriptions of what the packages do.

Much work has been done on Compiz but the Nvidia video drivers are not to be trusted. For this reason I do not recommend installing third party software until after installation of either 12.04 or 13.04. And I have done many test installations. Many of the Compiz special effects have been removed from 13.04 but will can install through the software centre not only Ubuntu Restricted Extras but also compiz-plugins-extras. So, the wobbly windows effect I lost in 12.10 is now back in 13.04. Thank you community.

In 13.04 we get a selection video drivers to experiment with. Nouveau is much, much better. I prefer to use it over Nvidia. Once anyone installs 13.04 they start on the convergence path to Unity touch. Anyone staying on 12.04 and upgrading to 14.04 or 16.04 is going to get a bigger cultural shock than those right now upgrading from 10.04 to 12.04. Believe me folks. Do not lose touch with developments in Ubuntu and come back after a few months/years and expect things to be the same.

Oh, nearly forgot. In 13.04 we get Grub 2. Yes I know we were told that we had Grub 2 some years ago but it was actually Grub 1.99. The difference? Sub-menus. All those old kernels and recovery mode are now in a sub-menu call Advance Options for Ubuntu. You don't get that in the old 12.04 but you may get in it 12.04.2 which is the latest 12.04 download. Much better Grub menu.

Regards.

---

### Post by bela42 on 2013-05-18
Since you are replacing LTS, IMHO stick with LTS. It mostly depends on your usage patterns, though.

I've upgraded from 12.04 to 12.10, which did work, but left me with a buggy system. Third party drivers and even Virtual Box OSE kernel modules failed to compile after each kernel update because a dependency to the correct kernel headers was missing.

Upgrading to 13.04 made the very same system completely unusable - no Unity anymore. I did a fresh install that fixed this but I still see so many errors in ACPI, grub and kernel: kernel errors logged during bootup, grub without menu timeout and failing to switch off after shutdown. Booting from grub prompt to ldm needs about a minute now. None of these bugs were present in previous releases.

My aged Notebook OTOH did upgrade without problems since 12.04, even though it does use the notorious broadcomm wifi chip set... It needs ages to start up, but then everything seems OK - except the fan running at full speed frequently. Also not the case in previous releases, of course.

I can hardly see much improvement in the last two releases. I hope 14.04 will be a good release, but my exceptions are low.

---

### Post by craig10x on 2013-05-18
Run both in live session and decide from there...i prefer 13.04 as it has a lot of unity improvements and other things and just feels more snappy...

---

### Post by buzzingrobot on 2013-05-18
The two are very much the same.  The advantages of LTS are the long-term security and bug fixes.  The advantage of 13.04 is a bit more polish and some new Unity features.

If you hate to change installations, know all your apps will work just fine, for the duration, on LTS, and don't care about the new stuff added to 13.04, then the obvious choice is LTS. 

Subjectively, in terms of reliability and error alerts (too many), I didn't see any significant difference. The LTS seems a tad more responsive.

---

### Post by Primefalcon on 2013-05-18
14.04 is a lot nicer user experience, but for me at least it was laggy as heck after about 1-2 hours and needed rebooting... so if you have nvidia graphics I'd say stick with 12.04 as I suspect that was the big issue

---

### Post by 3rdalbum on 2013-05-19
I'm still on 12.04, but I've kept track of the later versions.

12.10 has Amazon search built-into the Dash, and when you visit certain websites you are asked if you want to add them to the Launcher.

13.04 has that, plus some Unity speed improvements.

13.04 has only a very short period of support, so you'll be upgrading to 13.10 almost before you know it. That, along with the lack of interesting new features in 12.10 and 13.04, is what's keeping me on 12.04.

Also, 12.04 is the last version to include Unity 2D, and also the last version to support ATI Radeon HD 2000-4000 with proprietary drivers. What this means is, you are stuck with open-source drivers for ATI cards before the HD 5000 series if you use 12.10 or later. If the open-source driver doesn't have much 3D support, your Unity desktop will be pretty slow because the 3D rendering will happen on your CPU. If you used 12.04 you'd have access to the proprietary drivers, or be able to use Unity 2D.

---

### Post by ikt on 2013-05-19
why not both?

I run 12.04 on my desktop and 13.04 on my laptop.

---

