---
title: "[Important] AppArmor profile for Firefox."
date: 2013-04-09
forum: Security
---

### Post by kleenex on 2013-04-09
Hi. Could somebody paste here default Firefox profile created by Jamie Strandboge (Xubuntu 12.04)? Default without any modification. Something is wrong, because in syslog file I'm seeing something like;

```
kernel: [10474.933680] type=1400 audit(1365537556.720:311): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox" name="/home/kleenex/.config/user-dirs.dirs" pid=3685 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
```

Before this situation I saw only;

```
kernel: [ 5486.861120] type=1400 audit(1365422546.141:44): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/nvidiactl" pid=2874 comm="firefox" requested_mask="rw" denied_mask="rw" fsuid=1000 ouid=0
```

I'm asking because after profile reload saving files does not work and option in Firefox menu responsible for choosing location of where I can download/save files is greyed out and unavailable. 

I'm just asking about a Default profile (I do not know from where I can download it). Nothing more, nothing less.

p.s. I've tried a profile from here; [http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html](http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html) and after reload this profile, everything mentioned above start to happen. I've noticed, that apparmor_status command shows;

```
**/usr/lib/firefox/firefox///bin/ps**
/usr/lib/firefox/firefox{,*[^s][^h]}
/usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
/usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
/usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
```

**//bin/ps**? Is it normal? So, after reinstall apparmor-profile, **//bin/ps** entry was not showed again (apparmor_status command) and now I can download file and choose directory in Firefox menu. So it seems, that my problem is solved, but I'm still asking for Default Firefox profile. Could anybody put it here? 

What do you think about profile from this website; [http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html](http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html)

---

