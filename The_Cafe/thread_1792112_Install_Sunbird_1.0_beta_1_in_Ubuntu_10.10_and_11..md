---
title: "Install Sunbird 1.0 beta 1 in Ubuntu 10.10 and 11.04"
date: 2011-06-27
forum: The Cafe
---

### Post by TuxLyn on 2011-06-27
Hey guys I wrote small script to install sunbird in ubuntu. This script is inspired by this following post ([http://ubuntuforums.org/showthread.php?t=278206](http://ubuntuforums.org/showthread.php?t=278206)) and specificaly "nightfrost" coder. Thanks for your great contribution "nightfrost".

The bash script I wrote detects architecture of your ubuntu, if its 64bit or 32bit and downloads package specific to that architecture. Only 64bit (x86_64) and 32bit (i686) are supported right now. Then it extras the package, installs is in proper directories and installs menu shortcut. Also have very simple removal script too.

Anyways, check it out on TLG blog @ [http://www.thelinuxgeeks.info/install-sunbird-1-0-beta-1-in-ubuntu-10-10-and-11-04/](http://www.thelinuxgeeks.info/install-sunbird-1-0-beta-1-in-ubuntu-10-10-and-11-04/)

I will write simple installer for lighting plugin soon too. So keep checking TLG :) Thanks guys. Thank you to Ubuntu Forum community that made this possible.

---

### Post by Docaltmed on 2011-06-27
I'm not sure that I get it. Is Sunbird a stand-alone Lightning?

---

### Post by TuxLyn on 2011-06-27
@Docaltmed, Sunbird is stand-alone yes. It was removed from default ubuntu repos. Lighting is a plugin for thunderbird, and its possible to download it from thunderbird plugins page here, [https://addons.mozilla.org/en-US/thunderbird/addon/lightning/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/)

So no need for lighting installer after all. But stand-alone Sunbird installer needed for people who would like to use it without having to open your Thunderbird client for calendar/appointments. I prefer stand-alone version my self.

---

### Post by sydbat on 2011-06-27
I didn't know they still made Sunbird.

According to the Mozilla site "**[We recommend upgrading to Thunderbird 3 and Lightning 1.0 beta2.]("http://www.mozilla.org/projects/calendar/sunbird/")**".

Also, it hasn't been maintained since last fall (2010).

---

### Post by Bandit on 2011-06-27
> **sydbat said:**
> I didn't know they still made Sunbird.

I didnt know anyone needed a script to install it. Just put it in /opt and create a symlink in your /usr/bin folder.. Not rocket science...

---

### Post by TuxLyn on 2011-06-28
@Bandit, this script is for people that don't know how to do this them self =) Not every one is equally smart buddy.

---

