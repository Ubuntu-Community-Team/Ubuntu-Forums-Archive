---
title: "Right-click (context) menus not working on application top bars in GNOME Shell 3.29"
date: 2018-08-15
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2018-08-15
Further to my post [here]("https://ubuntuforums.org/showthread.php?t=2398305&p=13791467&viewfull=1#post13791467"), where I referred to a problem which doesn't seem to have affected anyone else, I've spent a lot of time over the past day or two looking at why I lost the context menus when right-clicking on application top bars. It's something that I use all the time so I felt rather lost without them. I could right-click on the desktop and on application windows so I know that my mouse was not at fault.

I installed from the latest daily ISO in KVM and even with the latest updates everything worked as it should. On my main PC I upgraded the GNOME Shell packages that I had held back and the problem reappeared. It wasn't a settings issue as it affected all three users that I had set up. So I downgraded the offending packages again and all was well. From what I could see it was just the gnome-shell and gnome-shell-common packages that were causing this problem.

I then went back to the KVM installation to check the right-click menu worked and it did and continued to do so with further updates. So I thought this would be a good time for a full reinstall but I again found that still the right-click menu failed to appear. Why does it work in KVM and not directly on my PC?

I then installed Ubuntu 18.04.1 and again all is well. Anyway after eight years of running the development release on a daily basis I've reverted to the current LTS, something that I was thinking about doing anyway, as I am busy with other things in Ubuntu. But I would love to know the where the problem lies as my findings just do not make any sense.

---

### Post by jbicha on 2018-08-15
Have you tried disabling any extra GNOME Shell extensions you installed?

---

### Post by PaulW2U on 2018-08-15
Are you saying that was the cause or just something I could have tried?  It seems strange that an extension could disable a right-click menu. And no-one else affected?

I've now gone back to 18.04 so it's not something that I can try now. From memory my additional users on my original installation would only have had access to the system extensions that are available with vanilla-gnome-desktop was installed. My main user would have had a few extra installed or updated from extensions.gnome.org and therefore placed in .local/share etc.

My KVM installation had the default Ubuntu extensions plus I think just Openweather.

The short-lived 18.10 installation would only have had the default Ubuntu extensions plus any that were left over in .local/share as I reused my home partition. I probably didn't check the other users as I would have had to have set them up and I can't remember doing so.

I don't regret reinstalling and moving away from 18.10 (for now anyway) as I was finding everything was starting to slow down especially small applications taking a long time to start. The latest mutter update definitely caused my PC to lock up after the first reboot and I seem to remember something similar in KVM too. All too much to deal with when I have other things I want or need to do.

---

### Post by #&amp;thj^% on 2018-08-15
> **PaulW2U said:**
> 
The short-lived 18.10 installation would only have had the default Ubuntu extensions plus any that were left over in .local/share as I reused my home partition. I probably didn't check the other users as I would have had to have set them up and I can't remember doing so.

**_I don't regret reinstalling and moving away from 18.10 (for now anyway) as I was finding everything was starting to slow down especially small applications taking a long time to start. _**The latest mutter update definitely caused my PC to lock up after the first reboot and I seem to remember something similar in KVM too. All too much to deal with when I have other things I want or need to do.

+1 Sadly I have to agree. :(

---

### Post by PaulW2U on 2018-10-02
Update:

Using today's daily ISO (20181002) I have tracked down the issue which was nothing to do with extensions or existing settings but an issue with the new version of GNOME, i.e. 3.30. Ubuntu 18.04, GNOME 3.28 works correctly. It seems that the problem exists only when I use my laptop with an external monitor in "Join displays" mode. Perhaps that's why no-one else saw the issue.

Bug reported: [Window titlebar context menus fail to appear in "Join displays" dual monitor mode]("https://launchpad.net/bugs/1795623").

---

### Post by PaulW2U on 2018-10-02
Second update:

Within an hour of setting up this installation, reporting a bug and writing the previous post I get an update, gnome-shell 3.30.0-3ubuntu1, which fixes this long standing issue (for me). :D

---

