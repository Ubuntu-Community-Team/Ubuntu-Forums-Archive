---
title: "[SOLVED] Moblock at boot?"
date: 2008-10-29
forum: Security
---

### Post by Kain000 on 2008-10-29
Hey everyone,
I was a bit worried about my protection using P2P torrenting apps, So i require RC4 encryption for azureus and stay off the public IP network.  For a little extra protection I installed MoBlock to help block potential "spys" from connecting to my computer.   
My question is wether MoBlock will run in the background by default from boot up or if I need to configure it to do so, and if not Do I need to be starting MoBlock control each time for it to work. 

As I understood it MoBlock control was a frontend to help you configure and perform maintience on it with a GUI rather than threw the command line.  I would think that it runs from boot, but I dont see it under the processes when I check my system monitor.    
In it's text configuration file it lists it's init runlevel as 0.    
should I change this to 5 as it's the graphical login that I use when I boot up?  I thought 0 was the system halt/reboot level.

Any help would be very apriciated!

thankyou

---

### Post by mikewhatever on 2008-10-29
Do you need the to configure the settings at every bootup? Probably not. Once configured, the settings are applied to iptabled, the kernel based firewall, hence not moblock process.

---

### Post by lovinglinux on 2008-10-29
> **Kain000 said:**
> Hey everyone,
I was a bit worried about my protection using P2P torrenting apps, So i require RC4 encryption for azureus and stay off the public IP network.  For a little extra protection I installed MoBlock to help block potential "spys" from connecting to my computer.   
My question is wether MoBlock will run in the background by default from boot up or if I need to configure it to do so, and if not Do I need to be starting MoBlock control each time for it to work. 

As I understood it MoBlock control was a frontend to help you configure and perform maintience on it with a GUI rather than threw the command line.  I would think that it runs from boot, but I dont see it under the processes when I check my system monitor.    
In it's text configuration file it lists it's init runlevel as 0.    
should I change this to 5 as it's the graphical login that I use when I boot up?  I thought 0 was the system halt/reboot level.

Any help would be very apriciated!

thankyou

Moblock is just CLI. What you refer as GUI is Mobloquer, not moblock-control. 

If you are not using the GUI, you can configure moblock to start at boot editing the file /etc/moblock/moblock.conf or /etc/default/moblock. I would recommend editing the second one, since it is loaded after moblock.conf and override any settings in the first one (if you change them). Mobloquer also uses /etc/default/moblock to save it's options.

The section you need to edit (/etc/moblock/moblock.conf) or add (/etc/default/moblock) is below:

```
# Turn on/off automatic start
# Note: this tells the MoBlock init script from starting on "start". Therefore
# MoBlock will not be started at system boot. The same behaviour can be achieved
# by removing/tweaking the init file and the links pointing to it. You can do
# this manually or by using an application such as rcconf.
# 0 - Don´t start MoBlock at system boot
# 1 - Start MoBlock at system boot (default)
MOBLOCK_INIT="1"
```

You don't need the GUI to be loaded at boot to be protected (you don't even need it at all, if you like cli), but Mobloquer also has an option to activate moblock at boot (it simply add MOBLOCK_INIT="1" to /etc/default/moblock). Once you have configured moblock to run at boot editing the configuration file or using Mobloquer's gui, you are already protected. Actually, I guess this is set by default.

You should read the [[COLOR="Red"]**General MoBlock thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=803183"). It has some important info about how it works and how to use it together with other iptable managers (firewalls).

---

### Post by jre on 2008-10-30
lovinglinux is completely correct.

Further:
"moblock-control test" will do a simple test if it is running.
"moblock-control status" will show you the iptables rules (MoBlock depends on traffic being sent to NFQUEUE) and if the daemon is running.
If you want to check the running processes: look for "moblock".

---

