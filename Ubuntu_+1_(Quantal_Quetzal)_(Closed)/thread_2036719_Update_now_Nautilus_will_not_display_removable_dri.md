---
title: "Update now Nautilus will not display removable drives"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-08-02
"Dread apt-get update" killed me again, nautilus displays only home folder and will not display removable volumes or file system.  No top line for plugging in /boot for example.

re-install of nautilus no help, had to synaptic completely remove nautilus and re-install.  

Sort of running.  Does not have the "file system" option.  

This is an August 1 A3 install and I wasn't anxious to re-install just yet.

Oh, well, I just plug in /boot on the top line.

Another anklebiter.

Jerry

---

### Post by irv on 2012-08-02
I know what you are saying. Hate when this happens.

Maybe one more thing you can try is to reboot into the recovery mode and run repair all broken packages. It is worth a try before doing any re-installs.

---

### Post by jerrylamos on 2012-08-02
"Dread apt-get update" killed me again, nautilus displays only home folder and will not display removable volumes or file system.  No top line for plugging in /boot for example.

re-install of nautilus no help, had to synaptic completely remove nautilus and re-install.  

Sort of running.  Does not have the "file system" option.  

This is an August 1 A3 install and I wasn't anxious to re-install just yet.

Oh, well, I just plug in /boot on the top line.

Another anklebiter.

Jerry

---

### Post by wheeze on 2012-08-02
I was having problems with Nautilus not displaying a link to my other internal drive until I installed gnome-disk-utility. Might help?

---

### Post by irv on 2012-08-02
> **wheeze said:**
> I was having problems with Nautilus not displaying a link to my other internal drive until I installed gnome-disk-utility. Might help?

By the way, I just started using Marlin an am trying to get away from using Nautilus. I even set Marlin to be my default file manager. I like the way it works with the Dash. It even lets me open it as Root right from the Dash.

---

### Post by pressureman on 2012-08-02
No problems here with a fully up to date system. Removable drives are displayed just as they always were.

I'm not exactly pleased with the latest developments in Nautilus either, but the sky isn't falling yet...

---

### Post by jerrylamos on 2012-08-02
> **irv said:**
> By the way, I just started using Marlin an am trying to get away from using Nautilus. I even set Marlin to be my default file manager. I like the way it works with the Dash. It even lets me open it as Root right from the Dash.

How did you install "Marlin"?

I did apt-cache marlin and apt-cache Marlin with no results.

My alternate is pcmanfm which is also infamous for launchpad bugs.

Jerry

---

### Post by kjbox on 2012-08-02
[http://www.unixmen.com/how-to-install-marlin-file-manager-on-ubuntu-and-linuxmint-nautilus-alternative/](http://www.unixmen.com/how-to-install-marlin-file-manager-on-ubuntu-and-linuxmint-nautilus-alternative/)

---

### Post by jbicha on 2012-08-02
Jerry, did you try Nautilus after rebooting?

Marlin is not in the Ubuntu repositories.

---

### Post by mc4man on 2012-08-02
> **pressureman said:**
> No problems here with a fully up to date system. Removable drives are displayed just as they always were.

I'm not exactly pleased with the latest developments in Nautilus either, but the sky isn't falling yet...
I've sen no issue with devices here either - there was a gvfs upgrade but it presented no issue

What theme/session are you using?, notice some symbolic icons a bit different than here inc. the arrows, like your's better.

While waiting for ubuntu to adjust light-themes for nautilus, (assuming they will), have started a little fool around with the nautilus toobar, ect.
Would like your arrows better & have been trying to shrink the toolbar height, managed to shave a few px off though would like some more removed
May or may not keep the arrows in 1 gtk box or separate, (if I add an up box then they'd likely need to be separate

---

### Post by QIII on 2012-08-02
Just updated 5 minutes ago (Ubuntu, not Xubuntu).  No issues.

This sort of sucks when everyone sees something different.  Hard to pin down.

---

### Post by Harry33 on 2012-08-03
I have one issue with nautilus.
My setup is a 64-bit, quadcore AMD 3,2 GHz and Nvidia 285 GTX.
The system is fully updated up to this very day.
My desktop is gnome-shell with gnome-classic fallback, no unity for me.
I am not using any additional PPA's currently.

Still my nautilus does not show edit - preferencies.

---

### Post by cariboo on 2012-08-03
Edit->Preferences has been removed from Nautilus. This has nothing to do with Unity, Nautilus is a part of he Gnome project.

See the screenshot.

---

### Post by wheeze on 2012-08-03
I was able to get to Nautilus preferences in GNOME Shell by clicking on the application's button in the task bar. Usually this only shows a Quit command for most apps but I found a larger menu there in Nautilus' case with Preferences available.

Not sure how you'd do it in Unity having not used that DE much.

---

### Post by irv on 2012-08-03
> **jerrylamos said:**
> How did you install "Marlin"?

I did apt-cache marlin and apt-cache Marlin with no results.

My alternate is pcmanfm which is also infamous for launchpad bugs.

Jerry
Are you still using 9.10. That's what it says in your profile. If this is true do a google search with "Installing Marlin in Ubuntu (version number).
I am using 12.04, and I used these commands.
```
sudo add-apt-repository ppa:marlin-devs/marlin-daily  
 sudo apt-get update  
 sudo apt-get install marlin 
```
Found them [HERE!]("http://www.techlw.com/2012/02/install-marlin-file-browser-on-ubuntu.html")

---

### Post by irv on 2012-08-03
By the way Nautilus 3.4.2 running under 12.04 with Unity shows the Preferences Under the edit menu.
[ATTACH]222197[/ATTACH]

---

### Post by vasa1 on 2012-08-03
But this thread is about Quantal (12.10) testing.

---

### Post by Harry33 on 2012-08-03
> **cariboo907 said:**
> Edit->Preferences has been removed from Nautilus. This has nothing to do with Unity, Nautilus is a part of he Gnome project.

See the screenshot.

Actually I did not claim it has anything to with Unity, I do not even have it installed.
I am using Gnome-shell and I cannot find preferences there.

However, I found it from the panel (task bar) just like Wheeze just mentioned.
Thanks for him.

---

### Post by irv on 2012-08-03
> **vasa1 said:**
> But this thread is about Quantal (12.10) testing.

Sorry, I missed the Alpha 3 in the OP.
I did all the Alpha/beta testing in 12.04, and was going to do the same with 12.10. But I have been having some problems with 12.04 locking up on me so I am trying to get this problems fix first.

---

### Post by P-I H on 2012-08-03
In Unity you left click Home in the upper panel to get a menu which include preferences

---

### Post by mc4man on 2012-08-03
In regards to edit > preferences which isn't all that useful anyway - 
it's still in nautilus, only that GS doesn't show it as preferences was added to the app menu.

In unity* it's still in the edit menu along with the currently small app menu & obviously in a classic session just in the edit menu.

---

### Post by irv on 2012-08-04
This is worth reading even thought it is dealing with Mint.
[http://www.webupd8.org/2012/08/nemo-linux-mint-team-forks-nautilus.html]("http://www.webupd8.org/2012/08/nemo-linux-mint-team-forks-nautilus.html")

---

### Post by jerrylamos on 2012-08-04
> Are you still using 9.10. That's what it says in your profile, Actually I forgot how to update my profile.  I'm usually on the latest unstable busted Ubuntu....

Jerry

---

### Post by irv on 2012-08-04
> **jerrylamos said:**
> Actually I forgot how to update my profile.  I'm usually on the latest unstable busted Ubuntu....

Jerry

Goto CP and then to Edit User Detail.
[ATTACH]222253[/ATTACH]

Then set your Ubuntu Distro.
[ATTACH]222254[/ATTACH]

---

