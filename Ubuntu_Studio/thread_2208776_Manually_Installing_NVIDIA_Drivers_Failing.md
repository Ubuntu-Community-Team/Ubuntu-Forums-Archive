---
title: "Manually Installing NVIDIA Drivers Failing"
date: 2014-03-02
forum: Ubuntu Studio
---

### Post by Sylos on 2014-03-02
Hello all.

I have been trying to install Tango Studio "Burning Thread" and more recently also Ubuntu Studio 12.04. The following problem happens with both. 

So, I am trying to install the NVIDIA drivers from the website (jockey shows me nothing to install and the OS bundled drivers never allow Message Signalled Interrupts to be used for the card) and I have hit a problem that has me stumped.

You have to blacklist nouveau in order to do the install - thats fine done it many times before. But now there is a new problem preventing me from doing the install.

Heres what I have done:

Ctrl + Alt + F1 - get to command prompt - 

```
sudo service xdm stop
```

All good. Start the NVIDIA installer. It complains about nouveau and offers to create a blacklist for it. Select yes. It does its thing and tells me to reboot and try again. So I do. But now, Ctrl Alt F1 just gives me a black screen with blinking cursor (no prompt). Cant do anything. So try a different tack:

Remove the NVIDIA created blacklist file. Make my own in /etc/modprobe.d/nvidia-graphics-drivers.conf

```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau off
```

Reboot. Try Ctl Alt F1 again - same story - no prompt.

It seems that any attempt to blacklist nouveau results in killing the ability to use tty. And as I have to run the NVIDIA installer sans graphical service - I'm stuck. It cant be done.

Anyone have any ideas how to get out of this little problem?

Cheers

---

### Post by Sylos on 2014-03-05
Bump

---

### Post by jejeman on 2014-03-05
> OS bundled drivers never allow Message Signalled Interrupts to be used for the cardWhat does this mean? What is your card?

---

### Post by Sylos on 2014-03-05
Hi jejeman.

MSI is a particular way of communicating with the card - it gets it off the IRQ it is currently sharing with my soundcard thus reducing the conflict between the two.

[http://en.wikipedia.org/wiki/Message_Signaled_Interrupts](http://en.wikipedia.org/wiki/Message_Signaled_Interrupts)

Whenever I have tried to enable it when using the NVIDIA drivers from the repos it has never worked. But on my previous build I installed the drivers from teh NVIDIA site and was able to use MSI by adding the options into a .conf file.

As an update to the problem, I have since installed an NVIDIA driver from the X Swat ppa (still doesnt allow MSI) and now tty is not working at all (I assume it is again to do with nouveau not being in use). This is starting to give me the hump. :(

Cheers

EDIT: My card is NVIDIA 7900GTO.

---

### Post by Sylos on 2014-03-06
Well I found a fix for the immediate problem. For anyone having similar issues this is what I did:

```
gksudo gedit /etc/default/grub
```

Then changed the grub_cmdline_linux entry to read:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap"
```

That fixed my tty and I was able to blacklist nouveau and commence the NVIDIA install. Of course, that then failed due to some gcc issue (i think) and I was left with an utterly borked OS -but thats a whole other story. For now I am gonna leave it running nouvea and see how it goes.

Cheers

---

### Post by preliatorlv on 2014-03-07
I'm running an Acer Aspire V3-771G-6485 with an nvidia GT 730M.  after making the edit in the previous post my screen was still blank when hitting Ctrl+Alt+F1.  I was able to enter my username and password, albeit blind, and command reboot which worked.  So it's aparent to me it enters the terminal but does not display.

---

### Post by Bashing-om on 2014-03-07
@ preliatorlv; Hi !

Your situation is different, You might open your own thread if this proves ineffective:

When booting, the initial video driver is a lower level system's driver, once the GUI is started the system tries to activate a higher level means to deal with the greater demands of the graphical environment. Sometimes that means just is not there or available. Help is what the system is asking for.

Your 730M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for installing the drivers: Switchable  graphics issues on Ubuntu 12.04?
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)
There is the BumbleBee project:
[https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee) <- updated:2014-01-24 22:11:56

Versions 13.10/14.04 may be better to use Nvidia-prime.
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Not hopeless 
[INDENT][INDENT]just needs a little bit of help
[/INDENT][/INDENT]

---

