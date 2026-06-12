---
title: "login screen for moblin remix?"
date: 2010-05-01
forum: Ubuntu Moblin Remix
---

### Post by elyse on 2010-05-01
I bought a Dell mini with moblin installed a couple of weeks ago. I mostly like the user interface, but the fact that there is no documented way to enable a login screen or screen locker is just unacceptable -- even my Palm Pre has better security than that.

The default installation includes a Login Screen settings app, but it does not work. It calls gdmsetup, which is apparently shipped broken (googling produces bug reports with the identical symptoms for prerelease 9.10 gdm). And in any case, even though many of the config files reference gdm, it doesn't seem to be actually used. 

ps -ef |grep gdm returns nothing

I found instructions for getting gdm to actually function on one of the upstream moblin forums, but the steps include editing /etc/inittab and /etc/sysconfig/desktop neither of which exist in modern Ubuntu. Unfortunately, documentation on how to make equivalent changes in upstart config files also does not exist in modern Ubuntu. 

There doesn't seem to be any meaningful documentation available for uxlaunch, either, which is what apparently supercedes gdm in moblin.

/etc/init/uxlaunch.conf has a line that mentions gdm, but it is commented out. 

# initctl emit starting-dm DM=gdm

And the startup code in /etc/init/gdm.conf is commented out.

#start on (filesystem 
#         and started hal
#         and tty-device-added KERNEL=tty7
#         and (graphics-device-added or stopped udevtrigger))

Can anyone tell me whether it would be safe to uncomment the gdm start code and comment out the uxlaunch startcode? I would rather not make my new toy unbootable, and since CTL-ALT-F1 and company do not work in moblin I am concerned that they have somehow broken the ability to satisfy the tty-device-added requirement for starting gdm.

Thanks 
Elyse

---

