---
title: "Did a user escalate from guest?"
date: 2012-03-08
forum: Security
---

### Post by Ms. Daisy on 2012-03-08
I'm hoping that my inexperience has simply led me to a place of paranoia (again).  But the following logs look to me like a script created a guest account, escalated to root, then deleted the account. No one with physical access to the computer did this. This can't be a system process, can it?

Here is the sys log

```
Mar  6 18:30:31 daisy-comp groupadd[2977]: group added to /etc/group: name=guest-pCQQHK, GID=128
Mar  6 18:30:31 daisy-comp groupadd[2977]: group added to /etc/gshadow: name=guest-pCQQHK
Mar  6 18:30:31 daisy-comp groupadd[2977]: new group: name=guest-pCQQHK, GID=128
Mar  6 18:30:32 daisy-comp useradd[2981]: new user: name=guest-pCQQHK, UID=114, GID=128, home=/, shell=/bin/bash
Mar  6 18:30:32 daisy-comp usermod[2986]: change user 'guest-pCQQHK' password
Mar  6 18:30:32 daisy-comp chage[2991]: changed password expiry for guest-pCQQHK
Mar  6 18:30:32 daisy-comp chfn[2994]: changed user 'guest-pCQQHK' information
Mar  6 18:30:32 daisy-comp usermod[3002]: change user 'guest-pCQQHK' home from '/' to '/tmp/guest-pCQQHK'
Mar  6 18:30:32 daisy-comp su[3007]: Successful su for guest-pCQQHK by root
Mar  6 18:30:32 daisy-comp su[3007]: + ??? root:guest-pCQQHK
Mar  6 18:30:32 daisy-comp su[3007]: pam_unix(su:session): session opened for user guest-pCQQHK by (uid=0)
Mar  6 18:30:32 daisy-comp su[3007]: pam_unix(su:session): session closed for user guest-pCQQHK
Mar  6 18:30:32 daisy-comp lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-pCQQHK by (uid=0)
Mar  6 18:30:32 daisy-comp lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :1



Mar  6 21:51:59 daisy-comp userdel[4318]: delete user 'guest-pCQQHK'
Mar  6 21:51:59 daisy-comp userdel[4318]: removed group 'guest-pCQQHK' owned by 'guest-pCQQHK'
Mar  6 21:51:59 daisy-comp lightdm: pam_unix(lightdm-autologin:session): session closed for user guest-pCQQHK
Mar  6 21:51:59 daisy-comp lightdm: pam_env(lightdm-autologin:setcred): No such user!?
Mar  6 21:51:59 daisy-comp lightdm: pam_env(lightdm-autologin:setcred): No such user!?
```

---

### Post by Blackra1n on 2012-03-08
This is normal lightdm related behaviour. See: [http://www.hkepc.com/forum/viewthread.php?tid=1746592](http://www.hkepc.com/forum/viewthread.php?tid=1746592)

---

### Post by CharlesA on 2012-03-08
> **Blackra1n said:**
> This is normal lightdm related behaviour. See: [http://www.hkepc.com/forum/viewthread.php?tid=1746592](http://www.hkepc.com/forum/viewthread.php?tid=1746592)
Here's the same link [translated from Chinese to English]("http://translate.google.com/translate?hl=en&sl=zh-CN&tl=en&u=http%3A%2F%2Fwww.hkepc.com%2Fforum%2Fviewthread.php%3Ftid%3D1746592").

---

### Post by Diametric on 2012-03-08
Daisy - check out this thread:  [http://ubuntuforums.org/showthread.php?t=1937283](http://ubuntuforums.org/showthread.php?t=1937283)

The link mentioned in the thread discusses how lightdm is a "user"...it's worht noting how this can affect your system.

Cheers!

---

### Post by Ms. Daisy on 2012-03-08
I think we can conclude from that that Google doesn't speak Chinese very well. LOL
 
OK, so according to the wiki, [lightdm ]("https://wiki.ubuntu.com/LightDM")"The most user visible aspect of the display manager is the login screen, however it also manages the X servers and facilitates remote logins using the XDMCP protocol." 
 
And according to the chinese link- Each time you login to a guest account, lightdm creates a new random guest account. 
 
So now my question is did the random guest account access root? This little bit makes it look like it did
```
Mar  6 18:30:32 daisy-comp su[3007]: Successful su for guest-pCQQHK by root
Mar  6 18:30:32 daisy-comp su[3007]: + ??? root:guest-pCQQHK 
```

---

### Post by CharlesA on 2012-03-08
Lol, I suppose it's the same as any other computed-based translation - stuff gets lost in translation. :p

I was going to check on my Ubuntu VM, but It turned out that I only have 10.04 on it, not the newer versions. I can check it out later today, when I get home, but this line looks odd:

```
Mar  6 18:30:32 daisy-comp su[3007]: + ??? root:guest-pCQQHK
```

It looked like it switched user to guest and then did something. Was there anything listed in auth.log?

---

### Post by Ms. Daisy on 2012-03-08
Hmm.  It kinda looks like lightdm continued with its thing although apparmor didn't seem to want it to.

```
kern log

Mar  6 18:30:33 daisy-comp kernel: [  946.710998] audit_printk_skb: 12 callbacks suppressed
Mar  6 18:30:33 daisy-comp kernel: [  946.711002] type=1400 audit(1331076633.213:25): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm-guest-session-wrapper" name="/proc/3095/cmdline" pid=3083 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=114 ouid=0
(4 more like this)

Mar  6 18:30:34 daisy-comp kernel: [  947.682876] type=1400 audit(1331076634.185:30): apparmor="DENIED" operation="open" parent=3035 profile="/usr/lib/lightdm/lightdm-guest-session-wrapper" name="/etc/compizconfig/upgrades/com.canonical.unity.unity.01.upgrade" pid=3136 comm="compiz" requested_mask="c" denied_mask="c" fsuid=114 ouid=0
Mar  6 18:30:36 daisy-comp kernel: [  950.240919] type=1400 audit(1331076636.741:31): apparmor="DENIED" operation="open" parent=3035 profile="/usr/lib/lightdm/lightdm-guest-session-wrapper" name="/etc/compizconfig/upgrades/com.canonical.unity.unity.02.upgrade" pid=3136 comm="compiz" requested_mask="c" denied_mask="c" fsuid=114 ouid=0
Mar  6 18:30:38 daisy-comp kernel: [  952.115807] type=1400 audit(1331076638.617:32): apparmor="DENIED" operation="open" parent=3136 profile="/usr/lib/lightdm/lightdm-guest-session-wrapper" name="/proc/1/stat" pid=3180 comm="killall" requested_mask="r" denied_mask="r" fsuid=114 ouid=0
(10 more exactly like that)




auth log

Mar  6 18:30:32 daisy-comp su[3007]: Successful su for guest-pCQQHK by root
Mar  6 18:30:32 daisy-comp su[3007]: + ??? root:guest-pCQQHK
Mar  6 18:30:32 daisy-comp su[3007]: pam_unix(su:session): session opened for user guest-pCQQHK by (uid=0)
Mar  6 18:30:32 daisy-comp su[3007]: pam_unix(su:session): session closed for user guest-pCQQHK
Mar  6 18:30:32 daisy-comp lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-pCQQHK by (uid=0)
Mar  6 18:30:32 daisy-comp lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :1
Mar  6 18:30:36 daisy-comp polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session20 (system bus name :1.113 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar  6 18:30:40 daisy-comp dbus[1021]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.120" (uid=114 pid=3220 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1329 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Mar  6 19:17:01 daisy-comp CRON[3956]: pam_unix(cron:session): session opened for user root by (uid=0)
``` I don't think it's the bug that Diametric posted. I can switch users after hibernate.

---

### Post by Dangertux on 2012-03-08
The log entry your siting is the other way around root is dropping privs tp guest after creating the random user and setting its user policies.

Hope this helps

---

### Post by Ms. Daisy on 2012-03-08
Yes it does, thanks!

---

