---
title: "[Ubuntu Budgie]How to set up default application for taking screenshots?"
date: 2016-12-08
forum: Ubuntu/Debian BASED
---

### Post by spectatorx on 2016-12-08
I'm unable to take screenshots by simple pressing printscreen key. I already checked key shortcuts in keyboard settings and printscreen is set to take screenshots so i assume i would need to configure os and set up default application to take screenshots, where can i do this? I've installed gnome-screenshot but simple installing it doesn't fix the problem.

Ubuntu Budgie Remix 16.10 amd64.

---

### Post by vasa1 on 2016-12-08
> **spectatorx said:**
> I'm unable to take screenshots by simple pressing printscreen key. I already checked key shortcuts in keyboard settings and printscreen is set to take screenshots so i assume i would need to configure os and set up default application to take screenshots, where can i do this? I've installed gnome-screenshot but simple installing it doesn't fix the problem.

Ubuntu Budgie Remix 16.10 amd64.

How do you know that you are unable to take screenshots? Is it because you can't find the screenshot you've taken?

---

### Post by spectatorx on 2016-12-08
Yes. No program shows up to let me set name of a screenshot file, no file is being saved in home folder or Pictures folder.

---

### Post by vasa1 on 2016-12-08
Did you run `find` on your home folder to check whether the file is generated in some folder with some name unfamiliar to you?

What happens if you open a terminal and run, for example, ```
gnome-screenshot -wp -f ~/Pictures/"$(date +%Y%m%d%H%M%S)".png
```exactly as shown?

---

### Post by spectatorx on 2016-12-08
> spectator@temp-laptop:~/Downloads$ gnome-screenshot -wp -f ~/Desktop/Screenshots/"$(date +%Y%m%d%H%M%S)".png
** Message: Unable to use GNOME Shell's builtin screenshot interface, resorting to fallback X11.


** (gnome-screenshot:13208): CRITICAL **: Unable to save the screenshot: Error opening file '/home/spectator/Desktop/Screenshots/20161209045210.png': No such file or directory



 This is what i get.


Just in case, here is my gpu driver info:
> spectator@temp-laptop:~$ sudo lshw -c display  *-display                 
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5058(size=8) memory:c0000-dffff




---

### Post by vasa1 on 2016-12-09
I'm very sorry, but I edited the command after I posted it and you used the unedited one. Please look at my post again and try the edited one:```
gnome-screenshot -wp -f ~/Pictures/"$(date +%Y%m%d%H%M%S)".png
```
Thanks!

BTW, there's nothing to worry about re. the first message. The second message is because I specified a destination that exists on *my* machine and not on yours!

---

### Post by spectatorx on 2016-12-09
Yes, now it has saved a screenshot of a terminal window in folder "Pictures", but still also outputted an error message:
> spectator@temp-laptop:~$ gnome-screenshot -wp -f ~/Pictures/"$(date +%Y%m%d%H%M%S)".png** Message: Unable to use GNOME Shell's builtin screenshot interface, resorting to fallback X11.




---

### Post by vasa1 on 2016-12-09
> **spectatorx said:**
> Yes, now it has saved a screenshot of a terminal window in folder "Pictures", but still also outputted an error message:

As I said before, that's not a concern. GNOME apps like to spew messages and errors. See [http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications/](http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications/)

Now that you know gnome-screenshot is functional, you may like to read *man gnome-screenshot* for various options. How exactly you set it up as default depends on your DE and I know nothing about Budgie.

---

### Post by spectatorx on 2016-12-09
It has to be some problem with budgie as i created custom hotkey, i did put your terminal command, bound printscreen key to it and still can't take screenshots with it.

---

### Post by vasa1 on 2016-12-09
> **spectatorx said:**
> It has to be some problem with budgie as i created custom hotkey, i did put your terminal command, bound printscreen key to it and still can't take screenshots with it.

You may have mentioned this elsewhere but where is this Budgie from? Version? How did you install it?

As I said, please look at *man gnome-screenshot* for options that maybe more suitable for you.

---

### Post by spectatorx on 2016-12-09
Ubuntu budgie remix downloaded from their website.

---

### Post by vasa1 on 2016-12-09
> **spectatorx said:**
> Ubuntu budgie remix downloaded from their website.

Maybe they offer some sort of support there? What is the exact link?

---

### Post by spectatorx on 2016-12-09
This seems to be their official website:
[https://budgie-remix.org](https://budgie-remix.org)

And only support i see there is "support us" :P

---

### Post by vasa1 on 2016-12-09
> **spectatorx said:**
> This seems to be their official website:
[https://budgie-remix.org](https://budgie-remix.org)

And only support i see there is "support us" :P

Try [https://gitter.im/ubuntubudgie/community/](https://gitter.im/ubuntubudgie/community/)

---

### Post by davidmohammed on 2016-12-09
PrintScreen via the PrintScrn key is on the TODO list upstream.

Until then - there is a very nice step by step guide on the upstream issue tracker covering this: [https://github.com/budgie-desktop/budgie-desktop/issues/305](https://github.com/budgie-desktop/budgie-desktop/issues/305)

---

