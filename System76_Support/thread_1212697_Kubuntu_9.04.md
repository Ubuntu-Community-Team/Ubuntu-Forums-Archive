---
title: "Kubuntu 9.04?"
date: 2009-07-14
forum: System76 Support
---

### Post by wrender on 2009-07-14
Im running Kubuntu 8.10 very happily on my Serval Pro.

I am looking and wiping and installing the latest 9.04 but was wondering how it it went for others? I heard there was some things to do with wifi for some people.

---

### Post by decoherence on 2009-07-14
> **wrender said:**
> Im running Kubuntu 8.10 very happily on my Serval Pro.

I am looking and wiping and installing the latest 9.04 but was wondering how it it went for others? I heard there was some things to do with wifi for some people.

I was not happy with the Kubuntu 9.04 until I got a more up to date version of KDE from the PPA [here]("http://www.kubuntu.org/news/kde-4.2.4").

Wireless worked for me with that version, but when I updated to Karmic testing, it broke. If it breaks for you, try using wicd instead of NetworkManager. Works fine for me!

---

### Post by wrender on 2009-07-14
I keep seeing wicd being mentioned... how does that relate to kubuntu, what is involved and do I need to worry about it?

Does the kde upgrade to 4.2.4 make things ok?

---

### Post by decoherence on 2009-07-14
> **wrender said:**
> I keep seeing wicd being mentioned... how does that relate to kubuntu, what is involved and do I need to worry about it?

Does the kde upgrade to 4.2.4 make things ok?

wicd is an alternative to NetworkManager. They are both network connection managers -- basically the interface for your network connections, wireless and wired. Ubuntu and Kubuntu use NetworkManager as their network connection managers, but they also offer wicd as an alternative. wicd often works when NetworkManager doesn't.

If you can connect via wired, you shouldn't have to worry. Do the upgrade, and if wireless breaks, hook up to the wired network, run Synaptic and install wicd. It will un-install NetworkManager and and set itself up to run. You might have to log out and back in to get it going.

The interface is different from what you'd be used to with the NetworkManager plasmoid, but it's still pretty straight-forward.

If you can't connect via wired, I suggest you get wicd and make sure it works before doing the upgrade.

---

### Post by 3Miro on 2009-07-14
In my opinion KDE 4.2 is a much better environment than Gnome, however, Kubuntu has many issues. For one, I could never figure out the network manager (I figured out the Gnome one), so under KDE I just use wicd.

Ubuntu is a Gnome distribution, when I was using KDE I had trouble with many applications not working properly. In 9.04 I had many sound issues and at the end I stopped using KDE.

Keep that in mind.

---

### Post by tabibito on 2009-07-14
You can also use gnome's network-manager applet as an alternative, especially if you are using a broadband modem. You currently can't setup your broadband modem through wicd and KDE network manager plasmoid.

---

### Post by wrender on 2009-07-14
Thank you for all the help I will give it a shot and see how it goes.

---

### Post by wrender on 2009-07-15
I did the upgrade and things seemed good however it was creepy in that there were things that definitely did not belong. ie adept. 

So did a fresh install. video card, sound network and touch pad all worked out of box. The special laptop keys do not all work... i guess i will try the system 76 drivers. 

For checking sake all I have to do is download the deb file and install right?

---

### Post by wrender on 2009-07-15
it appears the brightness keys are the ones not working with even with the drivers installed.

---

### Post by wrender on 2009-07-15
Anyone have luck with the brightness keys with kubuntu 9.04. They worked with 8.10.

Any ideas how to correct this?

---

### Post by tabibito on 2009-08-04
Mine is working fine... though there is no on-screen indicator showing up.

---

### Post by wrender on 2009-08-05
What did you do to get it working? Because I have kubuntu all updated and the system 76 drivers installed. The other function keys seems to work but the screen brightness does not.:confused:

At least it is set to full brightness by default...

---

### Post by wrender on 2009-08-05
I downloaded the latest sys76 deb file and it installed all good... but I realised I do not have the syst76 repo set-up. Does that matter?

ps. How do I setup the repo because when I try the online instructions it does not work for me.

I go to edit sources and add.. then i try popping in

> [http://planet76.com/repositories/](http://planet76.com/repositories/) ./

the window mentions it is looking for something like 

> deb [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main

Im confused.

---

### Post by jdb on 2009-08-05
> **wrender said:**
> I downloaded the latest sys76 deb file and it installed all good... but I realised I do not have the syst76 repo set-up. Does that matter?

ps. How do I setup the repo because when I try the online instructions it does not work for me.

I go to edit sources and add.. then i try popping in



the window mentions it is looking for something like 



Im confused.

Not having it in the repos just means that if it's updated you'll have to manually download it.

After you install system76 you have to run it.
I don't know where the menu is in Kubuntu, but if you can't find it, typing

```
system76-driver
```

from the shell will run it.

jdb

---

### Post by thomasaaron on 2009-08-06
If you click the Restore Tab and the Restore Button, it will set its own repositories up in your sources list.

---

### Post by wrender on 2009-08-06
So install is different than restore in that restore will add the repos?

---

### Post by thomasaaron on 2009-08-06
Right. Typically, if we want to add an application (we used to install gnucash for instance), we would do that through the restore functionality as well. But we rarely do that anymore.

---

### Post by wrender on 2009-08-07
Interesting.... did the restore and have the repos setup now.

Still no luck with the brightness keys.... sigh. Wonder what tabibito did differently.

---

