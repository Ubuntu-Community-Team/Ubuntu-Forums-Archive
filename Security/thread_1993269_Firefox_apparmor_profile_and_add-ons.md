---
title: "Firefox apparmor profile and add-ons"
date: 2012-06-01
forum: Security
---

### Post by Bluenoser81 on 2012-06-01
I'm running 12.04 and I just started getting my hands dirty with apparmor. I installed the default apparmor profile for Firefox, set it to enforce and restarted. Everything appeared to be working fine, but I noticed ads and flash were displaying the next time I used Firefox (after a reboot). I checked my add-ons and discovered that neither Adblock nor Noscript were in the list (odd...) of installed add-ons, so I redownloaded them and installed them again. I restarted Firefox and the same thing, ads and flash ads were back--so I checked my add-ons and the same two add-ons I had just installed had disappeared again. I think it is my apparmor profile because I just set my default Firefox apparmor profile to "complain" instead of "enforce," and now my add-ons are suddenly back and working fine. What am I doing wrong? I'm attaching a screenshot that might give some more information, hopefully.

---

### Post by Hungry Man on 2012-06-01
Your AppArmor profile is likely not allowing read access to some extension folder.

Run aa-logprof and it'll tell you what's being blocked.

---

### Post by Bluenoser81 on 2012-06-02
I've notice the following entries from the apparmor.d./usr.bin.firefox profile: 

```


  # noisy
  deny @{MOZ_LIBDIR}/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,
  deny /var/cache/fontconfig/ w,
  deny @{HOME}/.local/share/recently-used.xbel r,

  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny @{MOZ_LIBDIR}/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,


```Looks like it is denying write access for addons, is that correct? Should I just remove that line in the #noisy section? 

I've tried aa-prof while running Firefox:

```

craig@xlappy:/etc/apparmor.d$ aa-logprof firefox
Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.

```I'm not sure how aa-logprof is used (tried "man aa-logprof"). Do I set Firefox to enforce, play with a bit, and then run aa-logprof? I'm confused.

---

### Post by Hungry Man on 2012-06-02
You should remove those denies probably. IF you aren't getting anything in aa-logprof it means that the profile's quieting rejections with deny rules.

---

### Post by Bluenoser81 on 2012-06-02
That worked, thanks! This apparmor rabbit hole is deep indeed...

---

### Post by Hungry Man on 2012-06-03
It gets easier with practice.

---

