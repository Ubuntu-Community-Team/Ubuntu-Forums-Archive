---
title: "Can't remove Ubuntu One - missing &quot;Password&quot; menu item"
date: 2013-06-27
forum: Ubuntu One (CLOSED)
---

### Post by Scooby-2 on 2013-06-27
I have a desktop PC running Ubuntu 10.04.4 LTS with Xfce and a laptop running Ubuntu 12.04.2 LTS with Gnome. They had both been sharing the same files with Ubuntu One without problems for ages which allowed me to edit the same files on either machine and the latest changes made were always applied. However, some while back the PC stopped connecting to Ubuntu One (without showing any errors), though I wasn't aware of changing anything. The laptop still connects and syncs fine. The log files revealed nothing so I'm trying to remove the Ubuntu One software from the PC as per [this link]("https://answers.launchpad.net/ubuntuone-client/+faq/778") but I do not have the entry "Passwords and Encryption Keys" in the Accessories menu referenced in step 6. Ultimately I want to try and reinstall Ubuntu One. Interestingly the laptop is also missing the exact same menu entry so I guess I am the common link....:confused: Any ideas, anyone?

---

### Post by Irihapeti on 2013-06-27
The problem with the PC is that 10.04 is end-of-life and unsupported. See [http://ubuntuforums.org/showthread.php?t=2150538](http://ubuntuforums.org/showthread.php?t=2150538) and [https://bugs.launchpad.net/ubuntuone-client/+bug/462828?comments=all](https://bugs.launchpad.net/ubuntuone-client/+bug/462828?comments=all) for further details.

Bottom line: you'll need to upgrade the PC to a later version.

---

### Post by Scooby-2 on 2013-06-28
@Irihapeti

[COLOR=#C61919]****[/COLOR]
Thank you very much for your prompt response and the informative links. I knew I kept getting the message that "new release precise is available" but I have kept putting it off... This will push me into backing up my data and doing a release upgrade. Maybe this weekend....

---

### Post by Scooby-2 on 2013-07-01
I'm now on 12.04 and now having different problems - auth fail message and then, "Sorry, an error has occurred and Ubuntu One needs to close" every time I try to run it. I'll do some research and make the appropriate post if I can't find any help.

Thanks again to Irihapeti.

This thread can be closed, but I don't seem to have the option (presumably privileges) to do so.

Incidentally, I still don't have the "Passwords and Encryption Keys" in the Accessories menu that I originally had the problem with under 10.04....

---

### Post by Irihapeti on 2013-07-01
You're welcome.

You may need to remove and reinstall U1 completely. There are instructions for doing that on the U1 website. That involves removing the configuration and keys in your home directory, not just the software. (You may not need to remove the software at all, actually.)

I think that seahorse is installed by default on 12.04 Try entering "seahorse" in the dash if on unity, or look for "passwords and keys" (or something similar) in the system-preferences menu if using gnome-fallback.

If it's not there, sudo apt-get install seahorse should install it.

To mark a thread solved, edit the first message, go to "go to advanced" and select the solved tag. Then save.

---

### Post by Scooby-2 on 2013-07-02
As [**[COLOR=#C61919][B]Irihapeti**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=346442") correctly stated:

```
sudo apt-get install seahorse
```

added a menu entry "Passwords & Keys" in the Gnome Settings menu. 

FYI I ran the same command on my laptop - which is also missing the "Passwords & Encryption Keys" menu item - and it told me that seaorse was already installed and at the latest version. At least I now know I can type "seahorse" on the command line to run it.

Thanks again to Irihapeti.

---

