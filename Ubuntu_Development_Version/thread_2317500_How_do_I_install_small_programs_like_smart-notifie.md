---
title: "How do I install small programs like smart-notifier?"
date: 2016-03-17
forum: Ubuntu Development Version
---

### Post by unflavored on 2016-03-17
I installed a daily release of 16.04.  I want to install smart-notifier, but when I search for it in the new Gnome Software, it's not there.  It used to be available in the old Ubuntu Software Center.

---

### Post by howefield on 2016-03-17
Easiest way would be to use the terminal.

```
sudo apt update
```
```
sudo apt install smart-notifer
```

---

### Post by unflavored on 2016-03-17
Thank you.  Is there any plan to add this functionality to the new Gnome Software?

---

### Post by P-I H on 2016-03-17
Packages available in the system are missing in gnome-software. I made a new installation yesterday and at least these were missing lm-sensors, fancontrol and hardinfo. You can of course use sudo apt install, sudo apt-get install or synaptic. 
There were also other problems. After an installation was made the status field showed remove, but only for a brief moment, and then showed install again. Most confusing, did it install or not. After installation of some downloaded packages the text "Could not find 'Application name'" was shown. Examples are Chrome, Dropbox and Steam. Dropbox and Steam was possible to start from the Dash, but in case the user don't know, this is a serious problem. Chrome was very well hidden. The workaround I found was to open a terminal, run the command google-chrome and then lock Chrome to the Launcher.

---

### Post by unflavored on 2016-03-17
> **P-I H said:**
> Packages available in the system are missing in gnome-software. I made a new installation yesterday and at least these were missing lm-sensors, fancontrol and hardinfo. You can of course use sudo apt install, sudo apt-get install or synaptic.   I found one more workaround ```
sudo apt-get install software-center
```

---

### Post by buzzingrobot on 2016-03-17
There is only one package manager in Ubuntu. The Software Center, Gnome Software, Synaptic, apt, gdebi, etc., etc., all are different front ends that use that package manager.

The material that Gnome Software displays for a package must be created, vetted, etc. Given the number of packages in Canonical's repos, it's no surprise that at this point -- weeks before release -- some of that work is not finished.

Fedora has included Gnome Software for at least a couple of releases and experienced the same thing.

---

### Post by ajgreeny on 2016-03-17
If you like a GUI package manager with all the bells and whistles, every package shown (except maybe the paid for ones) and giving just about as much information as terminal, I suggest, and always use, synaptic.

It is the best package manager for all debian based OSs in my opinion, and one I find very hard to manage without.

---

### Post by grahammechanical on 2016-03-17
In the few weeks since I installed Gnome Software through a PPA it has gone from being a store without any products on the shelf to being a store that has prospects for being a useful place to obtain what is needed.

We can help improve Gnome Software. I mean the application  and it usefulness in Ubuntu and not Gnome apps in general. Oh, you know what I mean!

[http://mhall119.com/2016/03/help-make-gnome-software-beautiful/](http://mhall119.com/2016/03/help-make-gnome-software-beautiful/)

Regards.

---

### Post by unflavored on 2016-03-17
> **buzzingrobot said:**
> There is only one package manager in Ubuntu. The Software Center, Gnome Software, Synaptic, apt, gdebi, etc., etc., all are different front ends that use that package manager.  I'll probably avoid it, but what is Ubuntu's underlying package manager called?  > **buzzingrobot said:**
> Fedora has included Gnome Software for at least a couple of releases and experienced the same thing.  Speaking of Fedora, [I found they have this option.](http://www.iwillfolo.com/gnome-software-center-is-missing-apps-on-fedora-22-what-to-do/)  ```
gsettings set org.gnome.software require-appdata false
```  It's supposed to make Gnome Software show programs that don't have AppData.  But when I do it on Ubuntu it just says   ```
No such key 'require-appdata'
```  I will try synaptic too.

---

### Post by oldos2er on 2016-03-18
> what is Ubuntu's underlying package manager called?

[APT]("https://en.wikipedia.org/wiki/Advanced_Packaging_Tool").

---

