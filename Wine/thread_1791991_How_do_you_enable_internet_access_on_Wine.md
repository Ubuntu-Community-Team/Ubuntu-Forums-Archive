---
title: "How do you enable internet access on Wine?"
date: 2011-06-27
forum: Wine
---

### Post by rickyLOLZ on 2011-06-27
Hello guys. I know this is kinda dumb, but, how do you enable internet access in Wine? Thanks.

---

### Post by Tweak42 on 2011-06-28
> **rickyLOLZ said:**
> Hello guys. I know this is kinda dumb, but, how do you enable internet access in Wine? Thanks.

There is no enable or disable because Wine is supposed to **transparently** translate windows apps network calls to the linux network layer and vice versa.  It should not impede any in or outgoing network traffic, for that is the job of the system policies and firewall rules.

Can you be more specific, such as what windows program you are trying to use and what happens when it tries to access the internet?

---

### Post by rickyLOLZ on 2011-06-28
> **Tweak42 said:**
> There is no enable or disable because Wine is supposed to **transparently** translate windows apps network calls to the linux network layer and vice versa.  It should not impede any in or outgoing network traffic, for that is the job of the system policies and firewall rules.

Can you be more specific, such as what windows program you are trying to use and what happens when it tries to access the internet?

Well, i'm using the Bamboo Dock for Windows. And when i try to add a new app it says ''Please check how your internet connection is'' or something...

---

### Post by Tweak42 on 2011-06-28
> **rickyLOLZ said:**
> Well, i'm using the Bamboo Dock for Windows. And when i try to add a new app it says ''Please check how your internet connection is'' or something...

If it's this [BambooDock]("http://bamboodock.wacom.com/#EN") that you are trying, then I think you are out of luck.  

From what I can tell BambooDock is a app used to download and launch specially made Adobe Air applications (also ment for windows) that interface with a Wacom tablet.  Although Linux does have Wacom tablet drivers, I don't know if wine could connect windows apps to the linux tablet drivers.

Furthermore, two weeks ago Adobe dropped Air on linux support,thus eliminating the possibility of somehow extracting and running the Air apps standalone on linux.

If there is a particular app on BambooDock you want, you may be better off looking for a linux native equivalent.

---

### Post by rickyLOLZ on 2011-06-29
> **Tweak42 said:**
> If it's this [BambooDock]("http://bamboodock.wacom.com/#EN") that you are trying, then I think you are out of luck.  

From what I can tell BambooDock is a app used to download and launch specially made Adobe Air applications (also ment for windows) that interface with a Wacom tablet.  Although Linux does have Wacom tablet drivers, I don't know if wine could connect windows apps to the linux tablet drivers.

Furthermore, two weeks ago Adobe dropped Air on linux support,thus eliminating the possibility of somehow extracting and running the Air apps standalone on linux.

If there is a particular app on BambooDock you want, you may be better off looking for a linux native equivalent.

There's no problem if i'm out of luck... I have my tablet working on Ubuntu. ^^

---

### Post by hus787 on 2012-02-03
i wanted to install yahoo messenger, but within the setup when it comes to downloading the messenger the setup stays there as it is saying "Downloading Yahoo! Messenger" and doesn't proceed which logically translates to being unable to download

Okay okay forget what i've written up there, because when i had almost finished writing that, the download got completed and install. Maybe the progress-bar was dysfunctional/not working properly.

PS:adding this so that it might be helpful to someones hunting for a solution

---

### Post by Tweak42 on 2012-02-03
> **hus787 said:**
> i wanted to install yahoo messenger, but within the setup when it comes to downloading the messenger the setup stays there as it is saying "Downloading Yahoo! Messenger" and doesn't proceed which logically translates to being unable to download

Okay okay forget what i've written up there, because when i had almost finished writing that, the download got completed and install. Maybe the progress-bar was dysfunctional/not working properly.

PS:adding this so that it might be helpful to someones hunting for a solution

Good to hear you figure it out.  Please add your experiences with yahoo messenger to the wine appdb for more visibility.

[http://appdb.winehq.org/appview.php?iAppId=29](http://appdb.winehq.org/appview.php?iAppId=29)

---

