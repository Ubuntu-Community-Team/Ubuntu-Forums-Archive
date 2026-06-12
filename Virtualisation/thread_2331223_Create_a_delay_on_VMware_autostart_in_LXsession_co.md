---
title: "Create a delay on VMware autostart in LXsession configuration"
date: 2016-07-19
forum: Virtualisation
---

### Post by nixin72 on 2016-07-19
Hi, I'm trying to create a VMware-Horizon-View workstation using a computer running Lubuntu 14.04 i386 and I'm running into a couple issues. 

I've added vmware-view to LXsession configuration and it's getting run fine on boot. However, when I restart my system, when vmware-view loads, I get an error message saying "**Error: couldn't resolve host name**". I believe this is because my computer is loading into vmware-view before my computer is obtaining an IP address. It's the same error I've gotten before running vmware on windows thin-PC systems, but I can't recall exactly. 

To resolve the issue, I want to add a 6 second delay to my autostart applications. That way my computer has time to obtain an IP address, and then open up vmware-view and connect to the server. I'm running vmware-horizon-client v4.1.0 and the server is running vmware-horizon-client v5.5. I don't think that would be relevant at all, since the question is more generally how do I delay an autostart sequence, but just incase it changes things. 

How could I go about adding this delay in the autostart? 

Thank you so much!

---

### Post by MAFoElffen on 2016-07-20
If you want to have something not start until your networking is up... then adding a delay to startup is the wrong logic path...

Instead, you would add it to the end of your networking scripts located in /etc/network/if-up.d/

But another way to test and resolve that would be to  set static IP's. Then there would be no delay caused by dhcp.

---

### Post by nixin72 on 2016-07-20
Out of curiosity, what would the problem be with delaying the the vmware's autostart? I'll take your word for it that it's not a great approach, I'm just not sure why.

I can't set it to static IP because the computers I'm doing this for are being used across different subnets. The idea is to create dumb terminals so that if one stops working, we can swap it out with another box and troubleshoot the one that broke somewhere else, without taking up other people's time. I also need to take this computer and build an image out of it to dump on dozens of other computers, and I can't go and set a static IP for some 60+ computers...

Which script would I edit, and what would I add to it? There's 4 scripts in the folder: "000resovconf", "ntpdate", "upstart" and "wpasupplicant".

---

### Post by vasa1 on 2016-07-20
> **nixin72 said:**
> ... How could I go about adding this delay in the autostart? 
...
For a general route, see [URL="https://ubuntuforums.org/showthread.php?t=2024713"]Delay lxpanel autostart in Lubuntu
[/URL]

---

