---
title: "Successful su for yaws by root"
date: 2011-03-30
forum: Security
---

### Post by 23dornot23d on 2011-03-30
Removed yaws ..........

  ...... ran rkhunter but it finds nothing .....

but yaws is still running as root .... in my logs .... am not happy ....... as I have no idea where it came from or why it is running .....

---

### Post by 23dornot23d on 2011-03-31
Did a clean installation of Ubuntu 64bit 10.10 ......... just to be safe ........ not sure if this should have come up 
when doing fresh install or not ....... used my same home directory ...... but got a warning a script was running
at start ...... maybe nothing ....... but will keep a log here in case anyone else gets something similar happening .......


( never seen my entire desktop fall to pieces like it did though - with just opening a XCF file in Gimp 2.7.1 
it is development and it maybe just kicked compiz out ....... but why yasm is running I have no idea
can this get installed easily ...... from another package and if so which one and why does it need it ? ) 

Got this at startup too - probably nothing ,,,,, but I did notice the /bin/sh ..... in the old system was mentioned in the log
so am maybe just being over cautious ...... 

[The bash upgrade discovered that your /bin/sh link points to dash.
As bash for Debian is destined to provide a working /bin/sh (pointing to
/bin/bash) your link will be overwritten by a default link.]
dash is a minimal shell that is primarily meant to  meet POSIX bourne shell standards (i.e. BSD's /bin/sh). It doesn't  support autocompletion or command history.

```

Mar 31 19:00:37 keith-Aspire-7730ZG gdm-session-worker[1568]: pam_unix(gdm-autologin:session): session opened for user keith by (uid=0)
Mar 31 19:00:37 keith-Aspire-7730ZG gdm-session-worker[1568]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Mar 31 19:00:41 keith-Aspire-7730ZG pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Mar 31 19:00:41 keith-Aspire-7730ZG pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Mar 31 19:00:41 keith-Aspire-7730ZG pkexec[1713]: keith: Executing command [USER=root] [TTY=unknown] [CWD=/home/keith] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 1025]
Mar 31 19:00:42 keith-Aspire-7730ZG polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.24 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar 31 19:00:47 keith-Aspire-7730ZG dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=1729 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1349 comm="/usr/sbin/console-kit-daemon))
Mar 31 19:01:14 keith-Aspire-7730ZG sudo:    keith : TTY=unknown ; PWD=/home/keith ; USER=root ; COMMAND=/usr/sbin/synaptic
Mar 31 19:17:01 keith-Aspire-7730ZG CRON[7367]: pam_unix(cron:session): session opened for user root by (uid=0)


```No sign of yaws on the new clean install ...... 

Wondering whether or not to go back into the old system to get the logs ...... finally its gone ..... re-booted after
no sign of it now .....

```

Mar 31 20:33:20 keith-Aspire-7730ZG su[2120]: pam_unix(su:session): session opened for user yaws by (uid=0)
Mar 31 20:33:20 keith-Aspire-7730ZG su[2120]: pam_unix(su:session): session closed for user yaws
Mar 31 20:33:22 keith-Aspire-7730ZG kdm: :0[1216]: pam_unix(kdm:session): session opened for user keith by (uid=0)
Mar 31 20:33:22 keith-Aspire-7730ZG kdm: :0[1216]: pam_ck_connector(kdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 31 20:33:23 keith-Aspire-7730ZG pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Mar 31 20:33:23 keith-Aspire-7730ZG pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Mar 31 20:33:23 keith-Aspire-7730ZG pkexec[2516]: keith: Executing command [USER=root] [TTY=unknown] [CWD=/home/keith] [COMMAND=/usr/sbin/gnome-power-backlight-helper --set-brightness 9]
Mar 31 20:33:23 keith-Aspire-7730ZG polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session12 (system bus name :1.34 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar 31 20:33:26 keith-Aspire-7730ZG dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.39" (uid=1000 pid=2526 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.10" (uid=0 pid=1672 comm="/usr/sbin/console-kit-daemon))
Mar 31 20:36:17 keith-Aspire-7730ZG polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session12 (system bus name :1.34, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar 31 20:36:17 keith-Aspire-7730ZG kdm: :0[1216]: pam_unix(kdm:session): session closed for user keith
Mar 31 20:36:34 keith-Aspire-7730ZG kdm: :0[2709]: pam_unix(kdm:session): session opened for user keith by (uid=0)
Mar 31 20:36:34 keith-Aspire-7730ZG kdm: :0[2709]: pam_ck_connector(kdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 31 20:37:03 keith-Aspire-7730ZG polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session13 (system bus name :1.65 [/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1 -session 101a018c19a17f000130149097700000020880008_1301584117_480363], object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar 31 20:37:07 keith-Aspire-7730ZG dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.69" (uid=1000 pid=3137 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.10" (uid=0 pid=1672 comm="/usr/sbin/console-kit-daemon))
Mar 31 20:38:06 keith-Aspire-7730ZG sudo:    keith : TTY=unknown ; PWD=/home/keith/Documents ; USER=root ; COMMAND=/bin/sh -c /usr/sbin/synaptic
Mar 31 20:40:16 keith-Aspire-7730ZG polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session13 (system bus name :1.65, object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar 31 20:40:17 keith-Aspire-7730ZG kdm: :0[2709]: pam_unix(kdm:session): session closed for user keith
Mar 31 20:40:34 keith-Aspire-7730ZG kdm: :0[3632]: pam_unix(kdm:session): session opened for user keith by (uid=0)
Mar 31 20:40:34 keith-Aspire-7730ZG kdm: :0[3632]: pam_ck_connector(kdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 31 20:40:45 keith-Aspire-7730ZG polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session14 (system bus name :1.91 [/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1 -session 101a018c19a17f000130149097700000020880008_1301596813_902462], object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Mar 31 20:40:46 keith-Aspire-7730ZG dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.94" (uid=1000 pid=4004 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.10" (uid=0 pid=1672 comm="/usr/sbin/console-kit-daemon))


```

Maybe its ok now ...... :(

---

