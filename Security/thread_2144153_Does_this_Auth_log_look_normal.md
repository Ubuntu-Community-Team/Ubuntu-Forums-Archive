---
title: "Does this Auth log look normal?"
date: 2013-05-11
forum: Security
---

### Post by Stef700 on 2013-05-11
Hi,

I am new to Ubuntu and Linux and and just starting to get to grips with security. Please see below a_ copy of my Auth log after a normal startup_. I suppose I was slightly perturbed because it is rather full of "lightdm" stuff - Auth log spam? ;) - Can I just ignore this Lightdm stuff? 

Also the items at 

11:16:58 Rejected send message...
11:17:24 Registered authentication agent... and...
11:17:27 Rejected send message... 

Are these normal?

I am trying not to be paranoid about such things as key loggers etc....
Do you think the below log (full) is pretty normal/typical or not... ?

Many thanks,
Stef
(12.04 64bit)
```

May 11 11:16:57 desktop lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0) 
 

 May 11 11:16:57 desktop lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0 
 

 May 11 11:16:58 desktop lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "sg" 
 

 May 11 11:16:58 desktop dbus[900]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.27" (uid=104 pid=1634 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1368 comm="/usr/sbin/console-kit-daemon --no-daemon ") 
 

 May 11 11:17:01 desktop CRON[1713]: pam_unix(cron:session): session opened for user root by (uid=0) 
 

 May 11 11:17:01 desktop CRON[1713]: pam_unix(cron:session): session closed for user root 
 

 May 11 11:17:23 desktop lightdm: pam_unix(lightdm:session): session closed for user lightdm 
 

 May 11 11:17:23 desktop lightdm: pam_unix(lightdm:session): session opened for user sg by (uid=0) 
 

 May 11 11:17:23 desktop lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0 
 

 May 11 11:17:24 desktop polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.45 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) 
 

 May 11 11:17:27 desktop dbus[900]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=1975 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1368 comm="/usr/sbin/console-kit-daemon --no-daemon ")
```

---

### Post by 2F4U on 2013-05-11
LightDM is the login manager used in Ubuntu, so this doesn't look like an issue to me. If you find attempts to login as root, they should make you suspicious unless these attempts are initiated by you. The root login from the log excerpt comes from cron and therefore looks ok.

---

### Post by Stef700 on 2013-05-11
Ok thanks,

So I can ignore all the lightdm stuff (for users lightdm and sg) and the CRON stuff user root
This just leaves these three messages.... Anything to be concerned about here?
 
```

 May 11 11:16:58 desktop dbus[900]: [system] Rejected send message, 2  matched rules; type="method_call", sender=":1.27" (uid=104 pid=1634  comm="/usr/lib/indicator-datetime/indicator-datetime-ser")  interface="org.freedesktop.DBus.Properties" member="GetAll" error  name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1368  comm="/usr/sbin/console-kit-daemon --no-daemon ") 
 
 May 11 11:17:24 desktop polkitd(authority=local): Registered  Authentication Agent for  unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.45  [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1],  object path /org/gnome/PolicyKit1/AuthenticationAgent, locale  en_GB.UTF-8) 
 
 May 11 11:17:27 desktop dbus[900]: [system] Rejected send message, 2  matched rules; type="method_call", sender=":1.59" (uid=1000 pid=1975  comm="/usr/lib/indicator-datetime/indicator-datetime-ser")  interface="org.freedesktop.DBus.Properties" member="GetAll" error  name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1368  comm="/usr/sbin/console-kit-daemon --no-daemon ")
```

---

### Post by matt_symes on 2013-05-11
Hi Stef700.

Please use code tags when adding any log files into your posts or pasting any text from the terminal.

It makes is much easier to read.

To use code tags, highlight the text you want to appear in code tags, in your post, and hit the # button about where you type your text.

I have edited your two posts to help you out.

Kind regards

---

### Post by Stef700 on 2013-05-15
Thanks for the head's up regarding the CODE meta tags....

re the Auth log, and after reading up a bit about DBUS, all I conclude is that it is some sort of interprocess communication failure maybe because of insufficient privileges or wot not ...

I will continue to read and learn more about ubuntu security....

Thanks,

Stef (Still not paranoid) 
;-)

---

