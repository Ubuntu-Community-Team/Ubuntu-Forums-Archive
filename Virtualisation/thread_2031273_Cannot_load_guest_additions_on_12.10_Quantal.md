---
title: "Cannot load guest additions on 12.10 Quantal"
date: 2012-07-21
forum: Virtualisation
---

### Post by Paddy Landau on 2012-07-21
I have loaded 12.10 Quantal Quetzal 64-bit in Virtual Box (host is 12.04 64-bit).

12.10 is fully updated.

Virtual Box and the Guest Extensions are the latest [noparse](4.1.18)[/noparse] from the VB website.

The problem is that I cannot load the Guest Additions in the virtual machine. When I try to do so (Devices > Install Guest Additions), the 12.10 Launcher tells me that there is an Autorun Prompt &#8212; but the prompt does not appear, even if I click on the icon!

Screen-shot:
[attach]221598[/attach]

Do you know what I can do about this prompt not appearing?

---

### Post by CharlesA on 2012-07-21
You can try installing the guest additions from the terminal.

Did you have anything listed under additional drivers? I ended up using the guest additions from there on my 12.04 box.

---

### Post by Paddy Landau on 2012-07-22
> **CharlesA said:**
> You can try installing the guest additions from the terminal.
Do you know how to do that?

The only way I know is to use the VirtualBox menu > Devices > Install Guest Additions.

> **CharlesA said:**
> Did you have anything listed under additional drivers? I ended up using the guest additions from there on my 12.04 box.
Well, on 12.10, Additional Drivers (jockey-gtk) is replaced by software-properties. Unfortunately, [a bug prevents software-properties from running]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1026066"). :(

---

### Post by CharlesA on 2012-07-22
> **Paddy Landau said:**
> Do you know how to do that?

The only way I know is to use the VirtualBox menu > Devices > Install Guest Additions.

That just mounts the iso. ;)

Open a terminal and cd to /media/VBOXADDITIONS_WHATEVER

Then run:

```
sudo ./VBoxLinuxAdditions.run
```


> Well, on 12.10, Additional Drivers (jockey-gtk) is replaced by software-properties. Unfortunately, [a bug prevents software-properties from running]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1026066"). :(

D'oh!

---

### Post by Paddy Landau on 2012-07-22
Ah, there is a fix for the bug. I get this on the Additional Drivers:
[attach]221619[/attach]
I am using 64-bit PUE, not 32-bit DKMS, so the proposed device is not suitable (unless I have misunderstood what it means).

EDIT: I just missed your post. I'll try your suggestion and post back with the results.

---

### Post by Paddy Landau on 2012-07-22
I have reported the [Autoprompt Run bug]("https://bugs.launchpad.net/ubuntu/+bug/1027627").

In 12.10, I see that the media are now loaded in [FONT=Lucida Console]/run/media[/FONT], which means they are in RAM.

Your method worked to install the Guest Additions. Unfortunately they do not work. They are installed; if I try to re-install, the process first removes the previous installation. They just do not work.

Thank you for your time.

I'll see if I can find anything on the Virtual Box website.

---

### Post by CharlesA on 2012-07-22
Hrm, they might not support 12.10, depending on which version of virtualbox you are using. I was using 4.1.18 from virtualbox.org, but I haven't tried installing 12.10 on it.

---

### Post by Paddy Landau on 2012-07-22
> **CharlesA said:**
> ... they might not support 12.10...
True. I have posted a [question on the VB forums]("https://forums.virtualbox.org/viewtopic.php?f=3&t=50573"). Let's hope something comes of it. I am involved in helping with the manual, and the Guest Additions make it much more usable.

---

