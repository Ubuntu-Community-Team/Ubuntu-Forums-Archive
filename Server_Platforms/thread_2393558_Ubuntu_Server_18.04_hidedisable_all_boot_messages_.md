---
title: "Ubuntu Server 18.04 hide/disable all boot messages (kiosk mode)"
date: 2018-06-05
forum: Server Platforms
---

### Post by donlucacorleone on 2018-06-05
I've just installed Ubuntu Server 18.04 LTS on my Intel NUC PC.

  I'd like to make it a kiosk system, running only Chrome (for example).
  [B]
How can I suppress / hide / disable all these messages  printed to the monitor? I'd like to be black screen from power on to  (e.g.) Chrome.

[/B]

  I did follow [Ubuntu Server 16.04.02 with Splash Screen and Kiosk mode]("https://askubuntu.com/questions/924993/ubuntu-server-16-04-02-with-splash-screen-and-kiosk-mode/925002#925002?newreg=12674bb463c44ef385b9e45a7deda8ee") and other tutorials like that. But there's something new in 18.04 (I think) that prevents me for getting things done.

  
[LIST=1]
[*]**Grub**. Editing GRUB_CMDLINE_LINUX_DEFAULT didn't change anything, I had to edit GRUB_CMDLINE_LINUX instead. Is it ok?

  GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet" 
[*]**Welcome / MOTD / login messages** 
[/LIST]
  No way to avoid them! The closest I got was to remove /etc/update-motd.d/ folder so I only saw something like:[INDENT]   Ubuntu 18.04 LTS nuc tty1
      nuc login: kiosk (automatic login)
      Last login: [...]
      kiosk@nuc:~$

 [/INDENT]
(Note: I disabled autorun script for actually seeing these messages, otherwise they're too fast to catch.)

  
Ideally all those outputs should disappear in order to boot just  black, from power on to Chrome. And back of course: from Chrome to power  off, but that's another story.

  [B]
Which files should take care of them?[/B]

  **How can I reach a completely silent / quiet boot?**

---

