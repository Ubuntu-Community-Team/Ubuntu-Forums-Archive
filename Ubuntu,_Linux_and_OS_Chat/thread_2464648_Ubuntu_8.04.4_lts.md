---
title: "Ubuntu 8.04.4 lts"
date: 2021-07-07
forum: Ubuntu, Linux and OS Chat
---

### Post by gordie692 on 2021-07-07
Hey guys just a little question I downloaded and put Ubuntu 8.04.4 on flash drive and thinking on installing it on my drive this was my first distro I installed getting starting would I be okay to use it just throwing it out there

---

### Post by yetimon_64 on 2021-07-07
That particular release (desktop) went "end of life" on the 12th of May 2011; the server version had 2 extra years of support and went EOL in 2013. That equates to 10 years of no updates/security fixes for that code for the desktop release. Definitely not a good idea to let it anywhere near an internet connection in my opinion being such old and unsupported code.

If I were to experiment with such an old release I would tend to install it in a virtual machine, eg. virtualbox if possible, with the VM isolated from any internet connectivity through the settings of the VM software. I definitely wouldn't do a bare metal install with such an old release myself.

---

### Post by monkeybrain20122 on 2021-07-07
Maybe you meant 18.04?

---

### Post by grahammechanical on 2021-07-08
If your hardware is newer than Ubuntu 8.04 then Ubuntu may not have drivers for your hardware. This will be a problem especially for the video card. But as an experiment it might be educational to try it.

I once experimented by installing my first version of Ubuntu (07.04 LTS) and then upgrading to each following LTS version. I think I got as far as 11.04 LTS before the screen graphics got so messed up it was not worth going any further.

Regards

---

### Post by gordie692 on 2021-07-08
Thanks guys sorry that questionaire I liked that release and they even had the beginning sound when it opened to the desktop like windows I kinda knew the answer but thought with open code maybe 

thanks guys

---

### Post by TheFu on 2021-07-08
Non-supported OS releases should only be used if your goal is to be hacked or you want to practice cracking in a disconnected network lab environment.
Today, someone new to Linux should run Ubuntu 20.04 Desktop LTS or one of the officially supported 20.04 versions.  

A basic understanding of Ubuntu LTS releases will go a long way.  Follow the numbers.

LTS release happens April (04) of even years (2018, 2020, 2022, .... ). You get the idea. That means an LTS version is "{even year}.04".  For desktops it gets a little complicated since most flavors get 3 yrs of support only, but the core Ubuntu 20.04 Desktop which uses Gnome3 for the DE gets 5 yrs of support.  Some programs that we might install could have 0 yrs, 1 yr, 3, yrs or 5 yrs of support.  There is a command to get the list of unsupported programs. 20.04 changed the command.

There are a few *.ubuntu.com websites that explain this in greater detail and each DE release (Lubuntu/Xubuntu/Ubuntu-Mate/Kubuntu/.... ) has their own support policies.  Be certain you understand what the flavor you choose has for support and set a reminder in your calendar to update 3 months before support ends .... or July 2022, if you want to move to 22.04 LTS next year. I usually delay my main desktop until late June after the LTS is released. For servers, I tend to delay a year or more.

---

### Post by dddman on 2021-07-08
Isn't this why we have Ubuntu MATE?  It mimic's 8.04 using the old gnome2.  Right?

---

### Post by monkeybrain20122 on 2021-07-08
You can easily reactivate the login sound [https://askubuntu.com/questions/1232364/how-to-enable-startup-sound-on-ubuntu-20-04](https://askubuntu.com/questions/1232364/how-to-enable-startup-sound-on-ubuntu-20-04)

---

