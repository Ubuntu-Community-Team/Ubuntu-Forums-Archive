---
title: "Strange (unknown) authorization request without me triggering anything"
date: 2020-11-11
forum: Security
---

### Post by jobe77x on 2020-11-11
[https://dropbox.gr1.se/2020-11-11 08.19.54.png](https://dropbox.gr1.se/2020-11-11 08.19.54.png)
This authorization request has appeared on 2 of my servers that's monitoring webpages.

I have not installed or modified anything, and they appeared 2 days apart (and messeded upp a total of 17 hours of work)

anybody knows what it is, and why it had the audacity to disturb me like this?

---

### Post by EuclideanCoffee on 2020-11-11
From this information, I can only assume that a process is triggering this popup because it doesn't run as root. We need to figure out what is the cause.

Few questions. Is this on a computer that is publicly available like a cloud service or a server accessible to the Internet? Could you provide the log where this event occurs?

/var/log/auth.log

---

### Post by jobe77x on 2020-11-11
```
Nov 11 03:49:49 gizmobox1 pkexec[2900025]: gizmo: Executing command [USER=root] [TTY=unknown] [CWD=/home/gizmo] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Nov 11 04:05:41 gizmobox1 pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Nov 11 04:05:41 gizmobox1 pkexec[2917992]: gizmo: Executing command [USER=root] [TTY=unknown] [CWD=/home/gizmo] [COMMAND=/usr/lib/update-notifier/package-system-locked]ion): session opened for user root by (uid=0)
Nov 11 03:10:01 gizmobox1 CRON[2856524]: pam_unix(cron:session): session closed for user root
Nov 11 03:17:02 gizmobox1 CRON[2864131]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 11 03:17:02 gizmobox1 CRON[2864131]: pam_unix(cron:session): session closed for user root


Nov 11 04:17:01 gizmobox1 CRON[2931037]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 11 04:17:01 gizmobox1 CRON[2931037]: pam_unix(cron:session): session closed for user root
Nov 11 05:17:02 gizmobox1 CRON[3000485]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 11 05:17:02 gizmobox1 CRON[3000485]: pam_unix(cron:session): session closed for user root
Nov 11 06:17:02 gizmobox1 CRON[3069040]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 11 06:17:02 gizmobox1 CRON[3069040]: pam_unix(cron:session): session closed for user root
Nov 11 06:25:01 gizmobox1 CRON[3077967]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 11 06:25:01 gizmobox1 CRON[3077967]: pam_unix(cron:session): session closed for user root
Nov 11 06:52:45 gizmobox1 dbus-daemon[500]: [system] Failed to activate service 'org.freedesktop.PackageKit': timed out (service_start_timeout=25000ms)
Nov 11 07:01:38 gizmobox1 dbus-daemon[500]: [system] Failed to activate service 'org.freedesktop.nm_dispatcher': timed out (service_start_timeout=25000ms
```

---

### Post by EuclideanCoffee on 2020-11-11
Have you modified your sudors file? See this for information:

[https://unix.stackexchange.com/questions/181558/error-no-tty-present-and-no-askpass-program-specified-tty-unknown-pwd-u](https://unix.stackexchange.com/questions/181558/error-no-tty-present-and-no-askpass-program-specified-tty-unknown-pwd-u)

 For some reason you have requiretty set in your sudoers file. Since it's disabled by default it was set either by your distro, administrator, or you.
  See [this answer]("https://unix.stackexchange.com/q/79960") for how to disable requiretty for a single command.

If not, let us know. You can post your sudoers file as proof would help.

---

### Post by jobe77x on 2020-11-11
This is a clean installation of xubuntu 20.10, I've only added imagemagick, shutter and xdotool..

My /etc/sudoers.d/  is completely empty.. (never worked with sudoers before)

---

### Post by EuclideanCoffee on 2020-11-11
Ah. Please use 20.04 LTS release instead and see if the issue exists.

---

### Post by DuckHook on 2020-11-11
Hello jobe77x,

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Also, please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

---

