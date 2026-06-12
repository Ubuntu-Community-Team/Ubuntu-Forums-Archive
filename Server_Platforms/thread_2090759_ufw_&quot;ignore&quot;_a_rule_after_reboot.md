---
title: "ufw &quot;ignore&quot; a rule after reboot"
date: 2012-12-03
forum: Server Platforms
---

### Post by wysiwyg31 on 2012-12-03
Hello !

I have a small PC with ubuntu server on it (10.04)
I have an issue with my ufw configuration and SSH access.

I try to set up an external acces to this machine so I can be connected on it by SSH with my smartphone using connectbot (android)

I have set 3 rules on my ufw:

```
To            Action        From
---            ------        ------
Anywhere        ALLOW        192.168.0.0/24
Anywhere        ALLOW        192.168.1.0/24
OpenSSH         ALLOW        Anywhere
```The 2 first are for my local network (so I dont have to change ufw each time I play with something)
The last is for SSH access from outside.

My router has a port forwarding form port xx to port 22 of this machine.

So I set the rules, tried my SSH connection from local machine : OK
Tried my SSH connection from outside (use connectbot on 3G on my android smartphone): OK

When I reboot the server: 
SSH connexion from local network : OK
SSH connexion from outside : KO !!!!
So I used local connexion to make some diagnostics:
sudo ufw status: give same as before:  ufw is enabled and gives:
```
To            Action        From
---            ------        ------
Anywhere        ALLOW        192.168.0.0/24
Anywhere        ALLOW        192.168.1.0/24
OpenSSH            ALLOW        Anywhere
```I checked in /var/log/ufw.log :  the IP of my smartphone is now blocked !!

If I modify ufw configuration by:
```
sudo service ufw restart
```Outside connexion is working again! (until next reboot)

If I delete and re-add the rule (without restarting) it works to (until next reboot)


So ... what happened ? it looks like ufw starts at reboot but ignore my opening on SSH port.

I tried to had a look in syslog, kern.log, ufw.log but didnt notice anything strange (maybe I missed something).

Any idea ??

---

### Post by darkod on 2012-12-03
I have no idea why ufw would be doing this. But I would recommend you use iptables directly, not ufw which is only a front-end of iptables. And a front-end that doesn't work very good.

Also, you should seriously consider whether you want the SSH to be opened from anywhere. You are opening yourself to attacks.

---

### Post by wysiwyg31 on 2012-12-04
Hello ! 
Well I would prefer stick with ufw if possible. It is "uncomplicated" so I can remember how it works when I want to modify something 6 months later. 
Iptable is too complicated for me. 

Someone told me that it may be some other front end or script that overwrite my ufw settings at boot
But I have no clue how check this (what to search in which log file) and/or check what is launched during boot



Regarding security, what would you suggest ? 
I would like to make my server reachable from my smartphone which as not a fixed IP.
I have set a port forwarding from port xx of my router to port 22 of the server (xx is not 22), I heard it is recommanded even if I guess the security benefit is low.
I have setup fail2ban for SSH and I will disable password login on SSH (and allow only access with keys)

I guess I could make the access a little bit narrower by allowing an access only to YY.**.**.**, considering that my 3G ISP has all IPs starting by YY.

---

### Post by darkod on 2012-12-04
If you access only with keys, that helps the security a lot, I think. Changing the port doesn't help much since I think that any port scanners will detect that your router has an open port xx with the SSH service listening on the other end.
Also, since this is at your home, not at some provider, hopefully no one will bother too much to intend to hack you.

As for using iptables instead of ufw. I did a firewall project few months ago and I too decided to go with ufw because they say it is uncomplicated. Towards the end I realised that iptables would have been much more suited and easier. When googling iptables usage you have to remember that iptables exist since decades ago, and there are many, MANY, "tutorials" that are written for the old days, when using them was more complicated compared to today.

If you only need the few rules you mentioned, ufw might really be a better choice. In my case the machine was not only a firewall but also a router and I noticed that ufw is not that good working with the rules about the forwarded traffic.

---

### Post by wysiwyg31 on 2012-12-05
Ok, situation has changed !

I tried to figure out who could change my firewall rules, and I see that I had installed webmin.

I get in webmin, in firewall section and see that there were some ufw setting there !
in the user rules section, there was only the rules for my local network, not the port 22 open for everyone..

I tried to add it in webmin and press a "reinitialise firewall" thinking it was a kind of "apply my new settings".... :( it is not !!!!
It has reinitialised my firewall :  ufw disabled, iptable reseted with default setting.
ufw does not show up anymore in webmin, only a few options to configure iptable.

I get back in my SSH session, enabled ufw again:  it says me that it is now enable and will be enabled on next boot.

I reboot

after reboot, ufw disabled!
I removed webmin (I dont use it so much and it looks like it is becoming obsolete)

I enable ufw again, it's getting enabled but get disabled again on next reboot.

So I am in a new situation now (dont know if it is better or worse...)

---

### Post by darkod on 2012-12-05
I understand a GUI to administer a server is appealing to many people (I'm not too experienced with command line myself), but I think to install webmin is a very bad idea. In fact, somewhere I read that it's not in the repositories because it makes changes to config files not in the same way as ubuntu makes them.

So, webmin might have left some setting in ufw that is being called on every boot/enable.

Now that webmin is removed, double check if all its settings are removed too or some remain somewhere in the system.

After that, try resetting ufw, if I'm not mistaken it was:
sudo ufw reset

That should remove all settings and rules, and start from new blank ufw. But if you have only remote SSH access to the server, I am not sure if running the reset command leaves ufw disabled or enabled.
If it leaves it enabled and without any of your rules, SSH might not work.
I think it leaves it disabled.

This is what I meant when I said iptables should be preferred choice. :) These front ends use iptables too, but create their own config files and later if things go wrong you don't know where to look. With only iptables it's easy, you flush them and start over again. :)

---

### Post by wysiwyg31 on 2012-12-05
there was still some webmin stuff in /etc/rcX.d/

I deleted them.

I didnt tried a reset of ufw yet but   remove / install it again with apt-get --purge.

I also tried a 
```
sudo update-rc.d ufw defaults
```With no luck, ufw still disabled at boot.


Maybe I will follow your suggestion (regarding iptable), but I would really love to understand why that ](*,) ufw does not start at boot

---

### Post by darkod on 2012-12-05
After deleting the webmin stuff, did you reboot?

And after that try enabling ufw again because if not enabled it will stay disabled at boot until enabled.

If that doesn't work, I really have no idea. You can try the reset as a last option. If even that doesn't work, I'm out of ideas.

---

