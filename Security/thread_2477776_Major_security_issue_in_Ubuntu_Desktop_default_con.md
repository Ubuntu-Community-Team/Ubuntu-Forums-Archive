---
title: "Major security issue in Ubuntu Desktop default config - Removable Media"
date: 2022-08-07
forum: Security
---

### Post by 9dor on 2022-08-07
Dear Ubuntu Developers and Contributers,

There is a MAJOR SECURITY VULNERABILITY in Ubuntu Desktop since release 18.04 !

 Recently I used Ubuntu 22.04 LTS and noticed that the issue still exist!


 I don&#8217;t know the reason for it, but default values for &#8220;Removable Media&#8221; are VERY Risky!
It will automatically run the software which is attached to the removable media.
Why? Why has Ubuntu still didn&#8217;t disable that option?


 The following is the default configuration (the &#8220;bad&#8221; configuration):
[COLOR=unset]https://imgur.com/XXXQlV2[/COLOR]

The following is the configuration which Ubuntu ***should*** be having (it is **the fix to the problem**):
[https://imgur.com/a/0JeM6ve](https://imgur.com/a/0JeM6ve)

Please change the default configurations for Ubuntu!

---

### Post by TheFu on 2022-08-07
> **9dor said:**
> Dear Ubuntu Developers and Contributers,

Nobody here fits that description.  This is an end-user to end-user forum.  

Any automatic mounting of storage is a huge risk, but nearly every desktop distro has that enabled by default.  We can disable it, if it doesn't fit our needs.
> The point to mount is the power to destroy.
always remember that. It is as true today as it was 40 yrs ago.

---

### Post by arraybolt3 on 2022-08-08
I don't deny that this could be bad in certain circumstances, but... really plugging ANY unknown USB device into your system is a bad bad bad **BAAAAAD** idea even if software autorun isn't enabled and automounting is disabled. USB Killer devices exist. So do little USB gadgets that look like a keyboard to the OS and can dump payloads. There's even phone charger cables that can log your keystrokes and allow a nearby attacker to inject keystrokes into the system. So if you're plugging unknown USB devices into your computer, you've got a pretty significant risk already, without even having to bring automount and autorun into the picture. The only real attack vector this problem would allow would be if someone horked your USB drive, stuck Bad Stuff on it and then set it back on your desk, or put a random USB drive out in a spot that would make you tempted to insert it into the system to check if it was yours' or someone else's important data.

Also I don't think that option actually does what it says it does? I mean, maybe? A previous post about this issue seemed to suggest that this wasn't actually an autorun feature (multiple trusted people on the forums said this), and it got assigned a low priority on the bug report on Launchpad, so it might not be as bad as it sounds. I may check to see if it does what it looks like, but I don't think it will.

---

