---
title: "Compile &quot;OpenShot Video Editor&quot;?"
date: 2009-05-26
forum: Ubuntu Studio
---

### Post by Puzzlenoise on 2009-05-26
Hello!

I was searching for a videoeditor that would do what I need to. Kdenlive always crashes, and Cinelerra isn't what I want. I tried many others, but I didn't like them. However, [OpenShot Video Editor]("http://www.openshotvideo.com/") looks promising.

Problem: There is no .deb-package, I have to do it myself. 
Problem #2: I don't know how I should do that... so I need help and ask here. ^__^

How can I compile that?

Thanks for every help I can get.

---

### Post by rylleman on 2009-05-27
A [build wizard]("http://www.openshotvideo.com/2009/05/openshot-build-wizard-its-magic.html") has just been released for Openshot!

I haven't tried it myself yet since it wants to reinstall ffmpeg, MLT etc. and I'm in the middle of a production, not wanting to risk anything.

---

### Post by Puzzlenoise on 2009-05-27
I downloaded the package now. If I open the "python"-thing, I just get something like a "readme"... :(

What do I have to do with those files?

---

### Post by rylleman on 2009-05-27
unpack and in a terminal run python install.py

---

### Post by Gary.M on 2009-05-27
Installed and running. Promising. If it has a couple of simple transitions added, dissolve, fade etc it would do what I want most of the time.

---

### Post by JonOomph on 2009-05-29
Hi, I am the creator of OpenShot and just wanted to say that our project is still very early, and we haven't made any official releases yet.  Some features, such as transitions and key frame animation are still on the drawing board.

However, we are stable enough for users to install and evaluate.  I would like to encourage anyone who is interested in OpenShot to follow our blog ([http://www.openshotvideo.com](http://www.openshotvideo.com)) and install OpenShot via our build wizard ([https://launchpad.net/openshot/+download](https://launchpad.net/openshot/+download)).

There is no better way to support open-source projects than participating, sending feedback, and requesting features.  Hope to hear some feedback from you guys soon.  Thanks!

---

### Post by Gary.M on 2009-05-30
It seems that after the wizard has compiled and installed, the components added, or versions of, render kdenlive unusable. It crashes on start every time now. It was previously fine.

Is there by chance a reverse script to deinstall?

I'd like to keep an eye on openshot, but probably better in a virtual machine for now.

---

### Post by 3rdalbum on 2009-05-31
> **Gary.M said:**
> It seems that after the wizard has compiled and installed, the components added, or versions of, render kdenlive unusable. It crashes on start every time now. It was previously fine.

From the looks of it, Openshot uses MLT, which Kdenlive also uses. Openshot has probably overwritten Kdenlive's version of MLT.

> Is there by chance a reverse script to deinstall?

I don't think any such uninstall script would put back Kdenlive's preferred version of MLT, but you can go into Synaptic and mark all MLT-related packages for reinstallation. This is the one instance where merely reinstalling software is useful :-)

---

### Post by arnab_das on 2009-10-29
i think the best way to install it is via ubuntu tweak, that way uninstalling is easier as well.

---

