---
title: "can't install guest additions in 11.10"
date: 2011-10-15
forum: Virtualisation
---

### Post by ilantal on 2011-10-15
I updated from 11.04 to 11.10 and I can't use guest additions (which I had been using previously). The link points to

[http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso)

and the error message is:

Not Found
The requested object does not exist on this server. The link you followed is either outdated, inaccurate, or the server has been instructed not to let you have it. 

Does anybody know where it is?
Thanks,
Ilan

---

### Post by Tanker Bob on 2011-10-15
Weltall has a patch on [his blog here](http://weltall.heliohost.org/wordpress/2011/05/14/running-vmware-workstation-player-on-linux-2-6-39-updated/) under the Update 4 heading. I think that's what your looking for.

---

### Post by ilantal on 2011-10-16
Thanks for the reply Tanker Bob, but I can't manage to implement the suggestion. The suggestion may be for a slightly different product, vmware where I am using VirtualBox.
They suggest patching a file with an extension of vmx. The nearest thing I can find is vmx.h and that talks about version 2, not 7.1.4 or 7.1.5.

In short, I am still searching for a solution.

Thanks,
Ilan

---

### Post by westie457 on 2011-10-16
Go to here for a complete list of virtualbox downloads. You should be able to find what you are looking for. [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

---

### Post by ilantal on 2011-10-16
Thanks westie. I have VirtualBox running with the version I got with 11.10. It is just the guest additions which are not installed. The surprising thing is that VirtualBox seems to run fine without it. Maybe I don't need it anymore? I forget what it is supposed to give me.

I removed it to remove the error messages and now it definitely knows that it isn't there. Just when I go to add guest additions, it can't find it.

I have VirtualBox set up to cover both of my dual monitors and I originally put in guest additions to allow the dual monitors at full screen. Now VirtualBox knows how to handle the hardware without guest additions. Perhaps it is telling me that the old version is no longer necessary? (How does it get the link to the old version?)

All the mess happened in the upgrade from 11.04 to 11.10.
Ilan

---

### Post by PaulInBHC on 2011-10-16
Guest additions is required for file sharing. Maybe that is what you had it for.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

---

### Post by haqking on 2011-10-16
See this thread i posted in a couple of weeks ago.

[http://ubuntuforums.org/showthread.php?p=11296831](http://ubuntuforums.org/showthread.php?p=11296831)

you probably need:

```
sudo apt-get install virtualbox-ose-guest-utils
```

then a reboot

---

### Post by ilantal on 2011-10-17
Thanks for the help! The one thing which is great about Ubuntu is all the help you get. Ugh, to remember the ugly days with Microsoft....

Yesterday I think I found the answer. While I did indeed remove guest additions as far as Linux is concerned, Microsoft is another story. I went into their Control Panel, Add Remove Software and guess what? Thar she blows! The reason it wouldn't let me reinstall was that Microsoft already had it installed.

Although I haven't yet removed it from Microsoft, it all makes more sense now. If I remove it from Microsoft Add Remove Software, then I should be able to reinstall it.

Ilan

---

