---
title: "Auto-start virtual machine"
date: 2010-01-14
forum: Virtualisation
---

### Post by fizgig on 2010-01-14
I've seen many threads about this subject both here and on google but I haven't been able to find a solution yet.

I'm running regular ubuntu 9.10 (not the server version but the regular version with the Gnome desktop and so forth).  Ubuntu auto-logins into my main account.

I have a Windows XP VM that works great.  I just want it to load when Ubuntu loads.

I've tried the "Startup Applications" approach with the following commands:

**vboxmanage startvm "XP-Machine" --type gui**
**sleep 10 && vboxmanage startvm "XP-Machine" --type gui**
**su matt -c 'vboxmanage startvm "XP-Machine" --type gui'**
**sleep 10 && su matt -c 'vboxmanage startvm "XP-Machine" --type gui'**

None of them seem to be working.  I can start the VM fine when I'm logged in as myself (matt) with the first or second command above.

There are startup scripts out on the web that seem to be fairly comprehensive.  I tried [vboxtool]("http://vboxtool.svn.sourceforge.net/") and couldn't even get it to start my VM from the command line.  The author says there's a problem with Ubuntu 9.10.

I've even tried installing the closed-source version of virtualbox and tried all of the above but no joy.

Does anyone know an easy way to do this?  It's driving me nuts and I've burned several hours on this.

Thanks

---

### Post by fizgig on 2010-01-16
Please help!  I've burned many more hours since my first post with no luck.

---

### Post by SecretCode on 2010-01-17
You entering the command as VBoxManage, aren't you, not all lowercase?

I haven't tried this myself, but I find the best place for support on VirtualBox is their forums: [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

