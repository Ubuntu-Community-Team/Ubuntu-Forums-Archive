---
title: "Password issue in Ubuntu 9.10"
date: 2010-07-21
forum: Virtualisation
---

### Post by daddyenglish on 2010-07-21
Hi all im new to this forum.

I just inherited a virtual box with Ubuntu ver 9.10 and Windows Server 2003 on it i was given the password to the windows virtual but not for the Ubuntu, can someone help me in changing the present password this i do not have a clue what it is.

Thanks in advance.

---

### Post by pytheas22 on 2010-07-21
I'm not sure what you mean by "virtual box," but I'm assuming you just have a normal physical computer (and that it has nothing to do with VirtualBox, the virtualization application).

Either way, you can change the password on the Ubuntu installation by booting to a live CD, mounting the Ubuntu root file system, and editing the /etc/shadow file.  Look for the line in that file that begins with "root" and change it to this:
```

root:$6$JvIQntPP$XKU8KfO1qehmZoz58lVBH./1R6OJhf5lMKnDja4JsfZXPu79iCFvPsUDsl99hepm1JmNZnu7PmW0MahTwXU251:14811:0:99999:7:::
```

You will then be able to reboot the computer and log into the Ubuntu installation with username *root* and password *passw0rd*.  After logging in, you can change the password to something safer.

---

### Post by snowpine on 2010-07-21
You can also follow this tutorial, no Live CD necessary:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by daddyenglish on 2010-07-22
Thanks for your swift responses but i may not have clarified myself so here i go again.

I have a regular computer with vmware server console running on this computer and i have two images in my inventory windows server 2003 and Ubuntu, i was given the password to the windows image but not for the Ubuntu image so i am asking this question without a recovery cd for ubuntu is there a way to reset the password for this image???

---

### Post by snowpine on 2010-07-22
Did you read the link I posted in #3?

Here it is again: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by pytheas22 on 2010-07-22
Even with a virtual machine, the approach is the same.  I would first refer to the link that snowpine posted and boot your virtual machine to recovery mode (there's no recovery CD needed--you just choose to boot into recovery mode at the boot menu rather than letting it boot into default mode) and try resetting the password that way, which would be easiest.

If for some reason that doesn't work, you can boot the virtual machine with a live "CD" by telling VMware to boot it to an ISO image, but with the virtual hard drive for Ubuntu still attached.  Within the live environment, mount the virtual disk and edit /etc/shadow to change the password.  Then shut down the virtual machine, remove the ISO from the VMware configuration, and boot it normally to its virtual hard disk.

I haven't used anything from VMware in a while so I can't tell you exactly where to click to do all this, but hopefully it's straightforward enough.  If you need more help feel free to ask.

---

### Post by daddyenglish on 2010-07-23
wow wow wow !!!!!!!!!!!!!!

it worked guys thank you all so much
now i know where to go for expert advice

---

