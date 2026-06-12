---
title: "Recently made the switch to Ubuntu from Windows 8.. loving it so far!"
date: 2015-03-24
forum: Ubuntu, Linux and OS Chat
---

### Post by stephan12 on 2015-03-24
I have been using Ubuntu for the last ten days and have to say that I am really impressed so far. I'm still in the stage that everything is new so even just installing something like Conky is a great experience and I feel teaches me a lot about how to use the terminal and navigate through files correctly. Everything has been working flawlessly except for a few crashes here and there. Occasionally I get worried about following some of the tutorials online. I am often just typing out character by character a command and installing software from a repo that I don't know what it is.. What can I do about this?

Also how do I rename myself on these forums? Can't say I'm too happy with "stephan12". :|

---

### Post by Bucky Ball on 2015-03-24
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Glad to hear you're enjoying Ubuntu and the learning curve. 

As for changing your username, please post three alternatives in [***Forum Feedback & Help***]("http://ubuntuforums.org/forumdisplay.php?f=48") and one of the admins will deal with it for you. ;)

Always look in the Software Centre prior to installing random repos (PPAs). PPAs you will find online are generally not officially supported or checked by Ubuntu and you *use at your own risk*. Often, the version of an app tested and supported in your release is already in the official repositories. Best to install from their if you can as then the installed app be updated as required with your regular updates. 

Same applies to .tar and .deb files you might find about the place. These will generally not be updated (and not by the normal updates as you've installed manually). In most cases, you would need to update these manually.

For max stability, try and stick with the official repos and manually install PPAs and anything else you find sparingly (as they may break your machine or your updating capability). 

Good luck. ;)

PS: Which release of Ubuntu are you using? Just another point: if you do an online upgrade from one release to the next (as opposed to a clean install) having a heap of manually installed PPAs enabled has a great chance of breaking the upgrade. Either disable them or don't install them in the first place prior to doing the upgrade.

---

### Post by stephan12 on 2015-03-24
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Glad to hear you're enjoying Ubuntu and the learning curve. 

As for changing your username, please post in [***Forum Feedback & Help***]("http://ubuntuforums.org/forumdisplay.php?f=48") and one of the admins will deal with it for you. ;)

Always look in the Software Centre first prior to installing random repos (PPAs). PPAs you will find online are generally not officially supported or checked by Ubuntu and you *use at your own risk*. Often, the version of an app tested and supported in your release is already in the official repositories. Best to install from their if you can. It will be updated as required with your regular updates. 

Same applies to .tar and .deb files you might find about the place. These will generally not be updated (and not by the normal updates as you've installed manually). In most cases, you would need to update these manually.

Thanks for the quick reply. Good idea, I haven't been using the Software Centre as much as I should I just love the feeling of installing software directly from the terminal, I'll start doing that more.

I'm currently experiencing an annoying crash whenever I go to rename a folder. I've had to hard reset my computer twice.. any ideas what could be causing this?

---

### Post by Bucky Ball on 2015-03-24
Installing from the terminal? That's fine. The choice is yours. Software Centre (and you may enjoy Synaptics Package Manager more as more detail) uses apt-get and is a 'front-end' or GUI for it really. For instance, if you wanted to install Synaptic PM, you could use Software Centre, or you could open a terminal and:

```
sudo apt-get install synaptic
```

You can by-pass SCentre and use the terminal to install anything in the repos. Just use 'sudo apt-get install <package_name>'. Generally, the package name is obvious, but sometimes you may need to look up what its 'terminal' name is. ;)

PS: Also, I never use Software Updater. If you want to update in a terminal, just:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Always use the 'sudo apt-get update' command FIRST.

---

### Post by deadflowr on 2015-03-24
> [COLOR=#000000]As for changing your username, please post three alternatives in [/COLOR][***Forum Feedback & Help***]("http://ubuntuforums.org/forumdisplay.php?f=48")[COLOR=#000000] and one of the admins will deal with it for you. [/COLOR]:wink:
You'd probably be better off posting your username request in the [B][Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").
[/B]
That way only you and an admin can post, leaving outsiders who have nothing to do with your request unable to post.

---

### Post by Bucky Ball on 2015-03-24
> **deadflowr said:**
> You'd probably be better off posting your username request in the [B][Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").
[/B]
That way only you and an admin can post, leaving outsiders who have nothing to do with your request unable to post.

Quite right! Thanks, my mistake, still not properly awake here. ;)

---

### Post by stephan12 on 2015-03-24
Awesome thanks for the tips.

Is there anyway that I can see what applications I've installed today? My laptop isn't running as well as it was yesterday and I'm thinking it was some software I've installed.

---

### Post by deadflowr on 2015-03-24
> **stephan12 said:**
> Awesome thanks for the tips.

Is there anyway that I can see what applications I've installed today? My laptop isn't running as well as it was yesterday and I'm thinking it was some software I've installed.
There are other ways, but an easy one is open the software center and click on History in the top panel/toolbar.
it'll list by date.

---

