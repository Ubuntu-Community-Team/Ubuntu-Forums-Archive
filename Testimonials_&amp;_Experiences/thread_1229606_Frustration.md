---
title: "Frustration"
date: 2009-08-02
forum: Testimonials &amp; Experiences
---

### Post by Bigguy2468 on 2009-08-02
Man, sometimes this can be very frustrating.
Is it just me or are most new computers intentionally built to not accomodate Linux?
Seems to me that no matter what distro I download, or what computer I burn it on, there is always something wrong trying to install or or even boot up the LiveCD. Most of the computers in my house are Laptops and most are either HP or Compaq.
Years ago I owned a HP Pavilion Desktop that seemed to love Linux, not so much anymore.
I am starting to think that if I really want to enjoy Linux on a system I am going to have to spec out and build a machine that is specific to Linux. Otherwise, I am probably going to have to buy a different Windows brand computer in order to run Linux.

In most cases I have either problems with the file system being mounted, in the case of LiveCD's, or if I manage to get past that there are major display problems.

---

### Post by Mark Phelps on 2009-08-02
Recent frustrations are a combination of several problems ...

First, laptops are the most difficult to get working on Linux because the OEMs use so much customized hardware and drivers, they generally do NOT supply Linux drivers, and the Linux community is always playing catchup.  So, the newer the laptop, the greater the risk is it using some new hardware for which no Linux drivers yet exist.

Second, OEMs that have traditionally supported Linux have cut costs by ending support early on hardware that is still out there.  Good example of this is AMD/ATI which recently dropped support for all but their newer "HD" video cards.

Third, Canonical keeps switching their driver infrastructure every release or so, making it very hard to keep customizations, especially "hot keys", still working.  For a long time, that was done in the xorg.conf file and used various keymod config files.  Then, with 8.10, they dropped some of that and went with HAL/FDI.  Now, they're dropping that and going with something else.

Then, they've switched from Ext3 to Ext4 -- and some filesystem apps and utilities don't work anymore.  They switched to PulseAudio, and folks started posting about their audio no longer working after upgrading to 9.04.  The dropping of ATI driver support in 9.04 for legacy cards caused lots of folks who forced installations of ATI drivers (presuming that would still work) to not get video anymore.

The third problem caused me to abandon Linux on my Tablet PC because there was simply no way to detect the special keys anymore after 8.04.  BTW, Windows Seven RC, using seven-year-old XP drivers, works just fine!

Then, you have the folks that insist on installing using Wubi in Windows 7, even though that seems to work only on rare occasions.  And when it fails, which it seems to do most of the time, they are quick to blame Ubuntu, or Linux, or ... whatever.  Not themselves, of course, for not confirming that it even DOES work with Windows 7 in advance.

Personally, I think we're seeing a conflict between the desire to use the latest and greatest technical stuff in Ubuntu versus the need to remain stable long enough to let the community catch up. And, I think with the ready availability of MS Windows pre-release products and Linux CDs, we're seeing a great jump in the Linux "community" of nontechnical folks -- who are eager to experiment, but apparently, have no idea what they're doing.

So, basically, I don't think it's really any "harder" to install Linux on a machine today; in fact, I think it's really getting "easier" all the time.  I just think we're seeing a combination of the above, coupled with a huge growth of nontechnical types in the 
"community" -- folks who are eager to complain about how Ubuntu "trashed their PCs" instead of working with us to diagnose and fix their problems.

But, that's just my opinion ...

---

### Post by Tamlynmac on 2009-08-02
Perhaps, purchasing from a Linux site, would eliminate or at least reduce the number of issues one experiences. For example: [URL="http://www.system76.com/"]System 76
[/URL]
Not to mention, Linux sites generally have Linux pre-installed.

Just a thought.

---

### Post by lswb on 2009-08-02
Yeah, but we sure do have pretty notification balloons (even if they do look like they were copied from an older version of MS outlook) not to mention now needing 2 separate applets for shutdown and logout/switch user.

---

### Post by HappyFeet on 2009-08-02
[Zareason]("http://www.zareason.com/shop/home.php") is another company with linux preinstalled.

I build my own computers and have had no problems ever with installing and running linux. Yes, some windows machines are very proprietary, and make life very difficult for wannabe linux users. This is done on purpose. Don't give up though, when there is a will, there is a way.

---

