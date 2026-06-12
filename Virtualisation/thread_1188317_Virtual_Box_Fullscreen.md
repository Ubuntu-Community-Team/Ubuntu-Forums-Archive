---
title: "Virtual Box Fullscreen"
date: 2009-06-15
forum: Virtualisation
---

### Post by Mister LinOx on 2009-06-15
Okay. I am having to use XP on this temporary computer and since I can't really install Ubuntu, I am running it through Virtual Box. Everything is working fine except for the small window and still the same size at full screen with only a black border. 

I have went to [http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu](http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu)  and at the bottom it tells how to install guest additions, but it says I can't open ./VBoxLinuxAdditions.run 

So, can you guys give me steps to get it into fullscreen? I hate using XP. :P


```

codey@VBox:~$ cd /media/cdrom0
codey@VBox:/media/cdrom0$ sudo sh ./VBoxLinuxAdditions.run
[sudo] password for codey: 
sh: Can't open ./VBoxLinuxAdditions.run

```

This is what happened in the Terminal.

---

### Post by Mister LinOx on 2009-06-15
Nevermind. I fixed it. What had happened was when I clicked 'Install Guest Additions...' it opened BEHIND all of the windows I had opened and it need permission. :P Mods, you can lock this.

---

