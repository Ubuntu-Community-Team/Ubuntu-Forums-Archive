---
title: "Change the System76 Driver"
date: 2007-12-07
forum: System76 Support
---

### Post by palintheus on 2007-12-07
Some minor issues with the driver that I think would be good ideas.

1. Please make the installation of included programs separate from any driver, updates, or fixes. There are some applications that I have to remove *every* time I have to run the driver since it is recommended that we hit both install and restore.

2. Please prompt the user for some things and/or take a note from the Update Manager and Add/Remove and give us the option of watching what is being done is a terminal type box. I would still like some kind of prompts to confirm some things.

3. Please have the driver check to see if things are already done, or improve the system already in place. When I was having sound issues and had to run the driver several times. I had the same line for the plug-in 5-7 times at the end of my alsa-config file.

:popcorn:

Thanks!!

---

### Post by thomasaaron on 2007-12-07
> 1. Please make the installation of included programs separate from any driver, updates, or fixes. There are some applications that I have to remove *every* time I have to run the driver since it is recommended that we hit both install and restore.

It is not recommended that you run the restore and install functions. Install runs just the drivers. Restore is a total restore (software included). The one exception to that is that Restore will drop in a fresh xorg.conf. We don't do that in the install function because if someone has customized the xorg.conf, we don't want running the drivers to hose their customizations.

> 2. Please prompt the user for some things and/or take a note from the Update Manager and Add/Remove and give us the option of watching what is being done is a terminal type box. I would still like some kind of prompts to confirm some things.

Actually, that is in the works. Not sure when it will be available, but it is most definitely a goal for the driver.

> 3. Please have the driver check to see if things are already done, or improve the system already in place. When I was having sound issues and had to run the driver several times. I had the same line for the plug-in 5-7 times at the end of my alsa-config file.

That has been fixed in the driver that is coming out in the next day or two.

---

### Post by palintheus on 2007-12-07
1. IMO there should be a 'Restore your xorg.conf' button and keep all app installs separate.

2. hmm, when you say its a goal, how high is it on the priority list.

3. great!

---

### Post by thomasaaron on 2007-12-07
Moderately high. It is not a perfomance issue, so there definitely isn't a break-neck rush to get it done. But we've had a lot of requests for it. You can't blame folks for wanting to know what's being done to their computers, right?

There are some python terminal libraries  that Carl is trying to integrate into the driver that would do the trick. I wouldn't be surprised if it came out in the next version of the driver (after the one that is about to be released).

---

### Post by asmiller-ke6seh on 2007-12-07
I appreciate you guys.

I am looking forward to each Driver update. Just like Ubuntu, each release gets better and better.

---

