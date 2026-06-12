---
title: "Odd graphic mode for guest Ubuntu 12.04"
date: 2012-09-17
forum: Virtualisation
---

### Post by deragon on 2012-09-17
Greetings,

I have a VM that I am not using often.  It worked a few months ago.  Then I believe that I changed the vm's video card to vmvga and said to myself it will be enabled on the next reboot.  Then I forgot about it.  This week, I logged into the VM and to my surpise, it would not respond to any of my input devices (keyboard or mouse).  I looked at the configuration and noticed that it was set on vmvga.  I changed it to the good old 'cirrus' card emulator which used to work, but now it does not anymore.  Unity shows with only one color with vertical bars, suggesting that the video mode is wrong.  I tried Unity, Unity 2D and XFCE and all 3 environments suffer from this problem.

Following, the screenshot of the guest image:

[[IMG]http://www3.picturepush.com/photo/a/9738171/640/9738171.png[/IMG]](http://picturepush.com/public/9738171)

I am probably not the first suffering of such a problem.  However, I do not know what too look for on the net, what keywords to use to describe this problem.  If you know what this condition is called, please inform me.  If you have the solution to fix this, even better.  This is a kvm guest Ubuntu 12.04 running on a host Ubuntu 10.04.  I tried other graphic card emulators to no avail.

Best regards,
Deragon.

---

### Post by deragon on 2013-02-13
Greetings,

I resolved the issue by deleting the /etc/X11/xorg.conf file and restarting X11.

Best regards,
Deragon

---

