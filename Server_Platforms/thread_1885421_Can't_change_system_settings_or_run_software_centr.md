---
title: "Can't change system settings or run software centre"
date: 2011-11-23
forum: Server Platforms
---

### Post by MikkyX on 2011-11-23
'lo all,
I've just installed Ubuntu Server 11.10 x86 and I've also installed Unity as I prefer to do most of my work in a graphical environment (this is an in-house development server, not live or production - don't worry!)

I've created a user account which has Administrator access and I can use the Terminal within Unity to su / sudo and do things as root.

However, somewhere along the line I think I've broken a few things...

1. I can only manage the network connections via the command line - the icon in the top bar shows an empty signal indicator and says "device not managed". 

2. I can't change most system settings. Where an Unlock button appears, I cannot click it.

3. I cannot run Software Center unless I use a terminal and run sudo software-center - shouldn't I be able to run this as myself instead of needing root?!

4. I click the Dash Home icon and I cannot search for or run any apps I've installed (e.g. SVN Workbench) - I CAN run Chromium but I already put that in the launcher on the side of the screen.

5. I would like to enable services such as VNC etc. but there doesn't appear to be any options in System Settings to manage things like this?

6. When I try to reboot or shut down via the cog in the top right, it goes to the login screen instead of performing the requested action.

I realise this is unsupported by Ubuntu themselves (or Canonical) but I could use help if possible - thanks!

---

### Post by neomaximus2k on 2011-11-23
well personally i'd remove the GUI and install the Gnome one see if you have the same issues, at least then you can narrow it down to the GUI or something else

---

### Post by MikkyX on 2011-11-23
Forgive my lack of knowledge in this regard but how would I go about doing that?

---

### Post by sandyd on 2011-11-23
> **MikkyX said:**
> Forgive my lack of knowledge in this regard but how would I go about doing that?

Install the "ubuntu-desktop" package.

> **MikkyX said:**
> 'lo all,
I've just installed Ubuntu Server 11.10 x86 and I've also installed Unity as I prefer to do most of my work in a graphical environment (this is an in-house development server, not live or production - don't worry!)

I've created a user account which has Administrator access and I can use the Terminal within Unity to su / sudo and do things as root.

However, somewhere along the line I think I've broken a few things...

1. I can only manage the network connections via the command line - the icon in the top bar shows an empty signal indicator and says "device not managed". 

2. I can't change most system settings. Where an Unlock button appears, I cannot click it.

3. I cannot run Software Center unless I use a terminal and run sudo software-center - shouldn't I be able to run this as myself instead of needing root?!

4. I click the Dash Home icon and I cannot search for or run any apps I've installed (e.g. SVN Workbench) - I CAN run Chromium but I already put that in the launcher on the side of the screen.

5. I would like to enable services such as VNC etc. but there doesn't appear to be any options in System Settings to manage things like this?

6. When I try to reboot or shut down via the cog in the top right, it goes to the login screen instead of performing the requested action.

I realise this is unsupported by Ubuntu themselves (or Canonical) but I could use help if possible - thanks!
Gnome uses NetworkManager - something that is not included in the server edition of Ubuntu cause it drives server administrators insane. (their used to using ip/ipconfig)/etc/network/*

---

