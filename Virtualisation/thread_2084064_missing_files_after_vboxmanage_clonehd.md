---
title: "missing files after vboxmanage clonehd"
date: 2012-11-14
forum: Virtualisation
---

### Post by robinls on 2012-11-14
I had a virtualbox (4.1.8) .vdi file that was ubuntu server (12.04) running on windows server 2008. I used vboxmanage clonehd [path to vdi] ouput.img --format RAW to clone the drive then used a live cd to perform a dd if=[path to output.img] of=/dev/sda. When I finished I knew the nics would not be recognized so I deleted /etc/udev/rules.d/70-persistent-net.rules rebooted and all seemed fine. By fine I mean the now physical machine booted allowed me to log into both the console and putty into it. It had the right static ip, correct hostname, Apache was running time for a frosty beverage of your choice right?? Well... I had a set of web scripts in the /home/[user]/www directory.  They are gone. So far what I have found is that the symbolic link that was sitting at /var/www is gone and the aforementioned directory does not exist.  I am thinking this is something simple I missed but what? When you clone the .vdi file that is like cloning a hard drive. Those files did not sit on a network share and all the other custom configuration I did to the ubuntu server came across fine. So, what happened??  
Signed,
Confused admin in Austin

---

### Post by robinls on 2012-11-15
Thanks to mpack in the virtualbox forums for the fix to this.  To try to help others with this problem when you convert a VM to a physical machine if you have snapshots you must first merge the snapshots into the base .vdi file. Then you can follow the rest of the procedures... doh!
Good luck.

---

