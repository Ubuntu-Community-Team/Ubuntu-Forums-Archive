---
title: "x11 apps = snap apps"
date: 2016-05-11
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2016-05-11
The command "snap find" shows something called x11-apps. Search for it in Ubuntu Software ( x11 apps) and we get a list of snap apps that are suitable for the desktop. And one developer has been quick off the mark with the app called Audovia. I do not have the skill set to use it but I would credit it as possibly the first useful snap app to be available for Unity 7.

So, we now have an easy way of seeing the progress in snap packaging x11 applications.

Regards

---

### Post by ventrical on 2016-05-11
What the ...:)

```


Name      Version  Rev  Developer
x11-apps  1        2    chadmiller
ventrical@ventrical-MS-7798:~$ snap list
Name         Version               Rev  Developer
ubuntu-core  16.04+20160419.20-55  109  canonical
x11-apps     1                     2    chadmiller
ventrical@ventrical-MS-7798:~$ 

```

Is xpad one of these apps because it came up in the unity dash.

---

### Post by grahammechanical on 2016-05-11
I did not install the x11-apps snap package. I saw it listed in snap find and searched for it in Ubuntu Software and that is when I noticed that searching for x11 apps lists those snaps with a GUI.

[https://launchpad.net/xpad](https://launchpad.net/xpad)

I think that Xpad is a genuine X app. How did that get installed on your system?

Regards

---

### Post by ventrical on 2016-05-11
> **grahammechanical said:**
> I did not install the x11-apps snap package. I saw it listed in snap find and searched for it in Ubuntu Software and that is when I noticed that searching for x11 apps lists those snaps with a GUI.

[https://launchpad.net/xpad](https://launchpad.net/xpad)

I think that Xpad is a genuine X app. How did that get installed on your system?

Regards

I just did :

```

sudo snap install x11-apps

```

It is not on any of my other installs of unity8 with libertine..but , honestly I am not 100% sure.

Regards..

---

### Post by grahammechanical on 2016-05-12
A new X 11 app snap has appeared in Ubuntu Software bringing the total to 6. keepassx-elopio.

---

### Post by mikodo on 2016-05-24
Whoa! KeePassX got my attention. Serious stuff, not superfluous "let's see if we can make a widget for panel", or whatever.

---

### Post by grahammechanical on 2016-05-24
The snap repository also has these snaps by the same author but they don't show up in Ubuntu software. Perhaps because they are command line?

vault-elopio: kpcli-elopio; keepassx-elopio.

---

### Post by ventrical on 2016-05-25
Installed it but no icon to run it.

Regards..

---

### Post by ventrical on 2016-06-07
Ok.. update: Running my unity8 session with libertines and firefox and other deb packages installed through Libertine I decided to look at all my apps and noticed 'XApps'  (which are x11 apps). I clicked it and it brought me to  legacy containers and I was able to run firefox... so that  what x11-apps is for :) I am typing in firefox now in unity8 yak. The wild beast yak. :)


Regards..

---

### Post by ventrical on 2016-08-01
> **grahammechanical said:**
> The command "snap find" shows something called x11-apps. Search for it in Ubuntu Software ( x11 apps) and we get a list of snap apps that are suitable for the desktop. And one developer has been quick off the mark with the app called Audovia. I do not have the skill set to use it but I would credit it as possibly the first useful snap app to be available for Unity 7.

So, we now have an easy way of seeing the progress in snap packaging x11 applications.

Regards

That is the app that is supposed to run with Libertine .. and all of a sudden it is  gone from all my installs. So if you want to run apps like firefox in containers on Unity7 you need the x11-apps snap.

regards..

---

