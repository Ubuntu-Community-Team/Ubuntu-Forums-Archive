---
title: "10 Rocking Features in 10 Days: Better Hardware Support"
date: 2007-10-15
forum: The Fridge Discussions
---

### Post by TheFridge on 2007-10-15
Yesterday we took a look at the new Firefox plugin work. Today we turn to one of the most vexing of questions for many Linux users: hardware support and all that it means.
 **Why is hardware so vexing?**
 Basically, there is a lot of hardware and each requires a driver. People keep making new pieces and types of hardware and people keep buying it. All this means keeping up to date is a constant  struggle, although projects like the [Linux Driver Project]("http://www.linuxdriverproject.org/twiki/bin/view") are helping change that. 
 **So I have a shiny new piece of hardware, how do I make it work?**
 For the most part, hardware auto-detection has just worked for many Ubuntu releases. In fact, Ubuntu 4.10 (Warty Warthog) was the first major distro to ship with the  so-called Utopia stack, which allowed autodetection of many pieces of hardware via [HAL]("http://www.linuxdriverproject.org/twiki/bin/view").
 However there have been a few types of commonly used hardware causing problems on linux desktops: printers, video cards, winmodems (also called software modems) and wireless cards.
 **So what is this about printers?**
 With Ubuntu 7.10, the addition of system-config-printer has meant that the kind of auto-detection common with USB sticks and other similar kinds of hardware now comes to printers. Just plug in your printer and watch it work:
 [IMG]https://wiki.ubuntu.com/GutsyGibbon/Beta?action=AttachFile&do=get&target=printer-auto-detection.png[/IMG]
 **And now what about winmodems and wireless cards?**
 With the addition of the Restricted Drivers Manager in Ubuntu 7.04, you could easily enable and disable the restricted or non-free drivers for those pesky video cards from ATI and Nvidia, as well as those of us stuck with Atheros wireless cards.
 Now with 7.10, that one click goodness has been extended to Broadcom wireless cards and Winmodems, allowing you to install the firmware for these cards, although you will need an existing network connection to do this.
 When you first start your computers, the Restricted Drivers Manager will tell you if you have any hardware that might require such drivers:
[IMG]https://wiki.ubuntu.com/GutsyGibbon/Beta?action=AttachFile&do=get&target=r-m-newdrivers.png[/IMG]
 That&#8217;s all for today. See you tomorrow when we talk about Apparmor. Until then!
 

[More...](http://fridge.ubuntu.com/node/1173)

---

