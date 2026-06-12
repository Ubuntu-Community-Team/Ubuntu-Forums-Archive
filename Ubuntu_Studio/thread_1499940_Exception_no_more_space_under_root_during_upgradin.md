---
title: "Exception no more space under root during upgrading"
date: 2010-06-02
forum: Ubuntu Studio
---

### Post by Flik Shen on 2010-06-02
Hi,

I try to upgrade Ubuntu Studio from 8.04 to 10.04.
I have downloaded the alternative ISO image and mount it.
It seems work fine after I ran command [gksu "sh /cdrom/cdromupgrade"] using Alt+F2.
However it stuck in the second step and raise an exception that "Space is not enough under root partition and 4192M is expected".
I double check the disk space and found as following.
/dev/mapper/pdc_dgbbagea1
                       9698348   7065792   2143780  77% /
varrun                 1892232       124   1892108   1% /var/run
varlock                1892232         0   1892232   0% /var/lock
udev                   1892232        72   1892160   1% /dev
devshm                 1892232       108   1892124   1% /dev/shm
lrm                    1892232     44984   1847248   3% /lib/modules/2.6.24-23-generic/volatile

I install pure Ubuntu system and root partition is on RAID 1.
My system is built on AMD Sprider platform with CPU AMD 9650/Chipset AMD 790GP.
What could I do next to manage to upgrade?

Thanks and best regards,
Flik

---

### Post by psy-man on 2010-06-03
Hi 
Can you not just use the update manager to upgrade to 10.04?

---

### Post by sgx on 2010-06-04
You might post your question at 

[www.linuxquestions.org](www.linuxquestions.org)

Raid users that can help will be more common there.
Cheers

---

### Post by Flik Shen on 2010-06-07
> **psy-man said:**
> Hi 
Can you not just use the update manager to upgrade to 10.04?
I am newbie to ubuntu.
could you please detail how to upgrade without using update manager?

Thx a lot.
Flik

---

### Post by Flik Shen on 2010-06-07
> **sgx said:**
> You might post your question at 

[www.linuxquestions.org]("http://www.linuxquestions.org")

Raid users that can help will be more common there.
Cheers
Thank you for your suggestion.
I will try my question there.

---

### Post by sgx on 2010-06-07
> **Flik Shen said:**
> I am newbie to ubuntu.
could you please detail how to upgrade without using update manager?

Thx a lot.
Flik
apt is the command, with lots of good options, detailed here:

[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

sudo synaptic

opens a nice gui for apt, allowing precise selection of what
to add or remove, and what sources you wish to choose from, with
the default software repositories at your fingertips. Click the
reload button, then select from the list on the left side for new
software.

dpkg is a command related to both synaptic and apt, able to install software packages which you already have.

sudo dpkg -i patchage_0.2.3-2.1_i386.deb

----------------------------------------------------------------------------

apt-get install patchage

would, when online, search the repositories for a match of patchage, and
download and install it, or if other software was needed, would
ask your permission before proceeding (the exact name of the match generally has no numbers, or just the first number, so if it happened to be named

patchage2_0.2.3-2.1_i386.deb then

apt-get install patchage2

Cheers

---

### Post by Flik Shen on 2010-06-15
Hi friends,

I gave it up and re-install Ubuntu 10.04.
It seems really complex to adjust size of partitions when they are on RAID.

Next time maybe I can try it after I fully backup all things.

Cheers!

---

