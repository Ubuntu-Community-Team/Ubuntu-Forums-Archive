---
title: "Change the download server in KDE"
date: 2017-01-05
forum: Ubuntu/Debian BASED
---

### Post by jesus-freak on 2017-01-05
I'm sure this will be a quick easy answer for this question but I haven't been able to figure it out. I am running KDE and I need to change the download servers for my system. Normally in Ubuntu you go to "Software & updates" and then scan for the fastest servers. But I have not for the life of me been able to find anything like that in KDE. I am in the Philippines and at this time the ubuntu servers in the Philippines id completely down so I can't install anything.

---

### Post by howefield on 2017-01-05
Open the Software Updater > Click "More" button and open Software Sources.

From there change the Download server to "Other" and choose as you wish.

---

### Post by jesus-freak on 2017-01-05
Hmmmm, thanks so much for the help and the picture!! But I can't seem to find software updater anywhere. I typed it in the menu search, I looked in the settings page and I just can't find it anywhere.

---

### Post by howefield on 2017-01-05
Does

```
sudo -H software-properties-gtk
```

from a terminal window open it ?

---

### Post by vasa1 on 2017-01-05
Or maybe, since it's KDE, Muon Discover?

[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

The third tab in [https://help.ubuntu.com/community/Repositories/Kubuntu?action=AttachFile&do=get&target=muondiscover.png](https://help.ubuntu.com/community/Repositories/Kubuntu?action=AttachFile&do=get&target=muondiscover.png)

A better image maybe [https://help.ubuntu.com/community/Repositories/Kubuntu?action=AttachFile&do=get&target=muondiscoverrepos.png](https://help.ubuntu.com/community/Repositories/Kubuntu?action=AttachFile&do=get&target=muondiscoverrepos.png)

See the dropdown to the right of **Download from:**

---

### Post by jesus-freak on 2017-01-05
No, it doesn't seem to do it

---

### Post by howefield on 2017-01-05
In Kubuntu 16.04 it seems to be in the Applications > System menu ?

---

### Post by jesus-freak on 2017-01-05
Sorry but I think I am running the latest version of plasma and it doesn't use Muon Discover anymore. They have a new software center and I can't find these options in the new software center.

---

### Post by howefield on 2017-01-05
> **jesus-freak said:**
> Sorry but I think I am running the latest version of plasma ....

What exactly are you running, what's the name of the distro / iso file that you used to install ?

---

### Post by jesus-freak on 2017-01-05
I am using KDE Neon which from my understanding it is just Ubuntu with a basic Plasma on top. It comes with very little software pre-installed.

---

### Post by howefield on 2017-01-05
> **jesus-freak said:**
> I am using KDE Neon which from my understanding it is just Ubuntu with a basic Plasma on top. It comes with very little software pre-installed.

So it isn't Ubuntu nor an official flavour.

> Forum: General Help
All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, UbuntuGnome and Ubuntu Mate.

Thread moved to the "*Ubuntu/Debian BASED*" forum.

You could always manually change the source repositories using sed or some such.

I might have an iso file around, I'll boot it up and take a look.

---

### Post by vasa1 on 2017-01-05
> **jesus-freak said:**
> I am using KDE Neon which from my understanding it is just Ubuntu with a basic Plasma on top. It comes with very little software pre-installed.

It's always better to be upfront with what you're using. Please!

---

### Post by howefield on 2017-01-05
> **jesus-freak said:**
> .... It comes with very little software pre-installed.

Looks like you answered your own question, doesn't seem to be a default GUI way of easily changing the download server,  so as mentioned earlier you can certainly manually change your sources.list.

An alternative would be to install software-properties-gtk and use that.

```
sudo apt install software-properties-gtk
```
```
sudo -H software-properties-gtk
```

I'm not sure that is the best way in KDE Neon but having tested it I know it works.

---

### Post by jesus-freak on 2017-01-05
Sorry, I didn't know there would be much difference between Kubuntu and another Ubuntu based KDE distro. Next time I will tell the distro from the start. I don't know if that is the best way but it certainly works well so I am going to say this problem is solved for me :) Thanks so much for your time....... However, I do not know how to mark this thread as solved

---

### Post by howefield on 2017-01-05
> **jesus-freak said:**
> Sorry, I didn't know there would be much difference between Kubuntu and another Ubuntu based KDE distro. Next time I will tell the distro from the start. I don't know if that is the best way but it certainly works well so I am going to say this problem is solved for me :)

Cool, +1.

>  Thanks so much for your time....... However, I do not know how to mark this thread as solved

Near the top of the page just above the first post on the page.. "*Thread Tools*" > "*Mark this thread as solved*"

---

