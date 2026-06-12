---
title: "ubuntu one running when shutting down"
date: 2011-07-14
forum: Ubuntu One (CLOSED)
---

### Post by atomizer on 2011-07-14
When I shut down my computer, a message appears which says that ubuntu one is still running.

I am not signed in at ubuntu one (haven't done that yet on this install)

what's up with this message?

Am on ubuntu 11.04

---

### Post by duanedesign on 2011-07-15
If you want to prevent the ubuntuone-syncdaemon process from starting their are two options. One is for if you have an Ubuntu One Account (SSO account). The other is if you do not have access to the 'Services' tab on the Ubuntu One Control Panel.

[B]With Ubuntu One Account
[/B]The syncdaemon process should not start if under 'Services' on the U1 Preferences Panel, the 'File Syncronization' checkbox is not checked.

If I do the following, the ubuntuone-syncdaemon process stops and will not show up again, even after restarts:

   1. Open System->Preferences->Ubuntu One (Natty:Click Ubuntu One logo in the launcher)
   2. Click on the "Services" tab
   3. Click off the "File Synchronization" checkbox

I can see the ubuntuone-syncdaemon process disappear from System Monitor immediately after I check off that checkbox.

[B]No SSO/Ubuntu One account
[/B]
1. Open the menu on the very top right, the one you use to shutdown, restart, etc., and click 'System Settings'

2. Click on 'Startup Applications'.

3. Scroll down and uncheck Ubuntu One.

This should prevent the ubuntuone-syncdaemon process from starting. You can confirm this after a restart by running the following command:

```
ps aux | grep 'ubu'
```

respectfully,
duanedesign

---

