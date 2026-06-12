---
title: "Virtualbox file sharing"
date: 2010-07-18
forum: Virtualisation
---

### Post by dellsguy67 on 2010-07-18
Help, I'm having an awful time right now with sharing folders...

I'm running XP on my PC, w/ the newest Virtualbox (3.2.6) running Ubuntu 10.04. I have searched Virtualbox forums and these forums, as well as youtube and other sites. no tutorials have cracked the problem of sharing a folder between the 2 OS's. 

Can someone please help? I'm not very good w/ terminal, but I'm learning slowly. I have installed the Vbox tools or whatever, still w/ no success. Please, use dummy-speak. 

Thank you in advance

---

### Post by epic93 on 2010-07-18
First, create a shared folder with virtualbox in windows.

Open up a terminal in the linux guest

```
mkdir ~/mnt
mount -t vboxsf Files /tmp/mnt
```

Replace mnt with whatever you want to call the folder that will hold the shared files, and replace Files with the name of the shared folder that you created with VirtualBox.

---

### Post by Dedoimedo on 2010-07-19
You will need to install guest additions. Did you do that?

See these two:

[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

[http://www.dedoimedo.com/computers/virtualbox-network-sharing.html](http://www.dedoimedo.com/computers/virtualbox-network-sharing.html)


I hope this helps.

Dedoimedo

---

### Post by dellsguy67 on 2010-07-19
thanks guys - this is on my work pc and i will try later today

---

### Post by dellsguy67 on 2010-07-19
> **epic93 said:**
> First, create a shared folder with virtualbox in windows.

Open up a terminal in the linux guest

```
mkdir ~/mnt
mount -t vboxsf Files /tmp/mnt
```

Replace mnt with whatever you want to call the folder that will hold the shared files, and replace Files with the name of the shared folder that you created with VirtualBox.

this did not work. it said: "mounting failed with the error: No such file or directory"

haven't tried the other option yet..

---

### Post by dellsguy67 on 2010-07-19
> **Dedoimedo said:**
> You will need to install guest additions. Did you do that?

See these two:

[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

[http://www.dedoimedo.com/computers/virtualbox-network-sharing.html](http://www.dedoimedo.com/computers/virtualbox-network-sharing.html)


I hope this helps.

Dedoimedo

your tutorials are awesome and i learned a few things, but i get the error:

/sbin/mount.vboxsf: mounting failed with the error: no such file or directory

the windows shared folder is c:\shared and on ubuntu it is /home/user/shared

i don't get what i'm doing wrong, but its f'n irritating! LOL

---

### Post by TheFu on 2010-07-19
> **dellsguy67 said:**
> /sbin/mount.vboxsf: mounting failed with the error: no such file or directory

the windows shared folder is c:\shared and on ubuntu it is /home/user/shared

i don't get what i'm doing wrong, but its f'n irritating! LOL

First, it appears you haven't installed the Guest Additions inside the client. You need to do that first.
Second, the name of the shared directory on the hostOS only matters to the mount command exactly as you typed it.  It is doubtful that you called it "c:\shared". I'd guess you may have called it "Shared" instead inside the VirtualBox interface.  Inside the client, when you use the mount command, you need to specify that mount point **exactly** as you typed it in the vbox interface, not with the name the host calls it.

This [http://jdpfu.com:82/2008/10/26/virtualbox-host-drive-access](http://jdpfu.com:82/2008/10/26/virtualbox-host-drive-access) may be helpful for someone too.

---

### Post by dellsguy67 on 2010-07-20
> **TheFu said:**
> First, it appears you haven't installed the Guest Additions inside the client. You need to do that first.
Second, the name of the shared directory on the hostOS only matters to the mount command exactly as you typed it.  It is doubtful that you called it "c:\shared". I'd guess you may have called it "Shared" instead inside the VirtualBox interface.  Inside the client, when you use the mount command, you need to specify that mount point **exactly** as you typed it in the vbox interface, not with the name the host calls it.

This [http://jdpfu.com:82/2008/10/26/virtualbox-host-drive-access](http://jdpfu.com:82/2008/10/26/virtualbox-host-drive-access) may be helpful for someone too.

why is it doubtful i named it c:\shared? That is exactly what I named it because i was going for simple and basic to just get sharing to work.

---

### Post by dellsguy67 on 2010-07-20
how can you tell guest additions isn't installed?

---

### Post by dellsguy67 on 2010-07-20
IT WORKS!

TheFu was correct to a degree about Guest Additions...It was installed but needed a reboot. I manually did it and ran the commands in Dedoimedo's 2nd link and BOOM it worked. You guys just solved about 3 days of headache for me! Thank you!

---

