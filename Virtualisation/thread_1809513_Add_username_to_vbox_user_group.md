---
title: "Add username to vbox user group?"
date: 2011-07-21
forum: Virtualisation
---

### Post by Gael33 on 2011-07-21
Could someone help me to add my username to the vbox user group?
Simple step by step instructions please. I am by no means a techie :)

Thanks. 

Gael.

---

### Post by howefield on 2011-07-21
1. Press the meta key, search for and open the Users and Groups application.

2. Press manage groups button.

3. Scroll down to vboxusers line, highlight it and press the properties button.

4. Check the box next to the users name you wish to add and press OK.

5. Enter your password when prompted and close/OK your way back out.

You'll likely need to logout or reboot for the changes to take effect.


Or use the terminal command

```
sudo adduser username vboxusers
```

substituting username with the correct user name.

---

### Post by Gael33 on 2011-07-22
Hi, I used the terminal and it told me that my username was already in the vboxusers. I guess that is good, eh?

However, you say press the Meta Key ... I have no idea what a Meta key is or where to find it. Would you please point me in the direction of where I should find the Meta key? The rest of your instructions I think (hope) I can manage :)

Thanks for responding.

Gael.

---

### Post by howefield on 2011-07-22
Hi,

The meta key is generally the one with the Windows flag on it, bottom left corner of the keyboard between Ctrl and Alt.

Also known as the Super key.

---

### Post by Gael33 on 2011-07-22
Hi, I tried pressing the 'Meta' key ... the one with the windows flag on it. Unfortunately, nothing happened. Can you give me any more instructions?

I am using Ubuntu 11.04 Natty, with VirtualBox 4.04 with the latest Extension Pack 4.08 running Windows XP.

---

### Post by howefield on 2011-07-22
With you running Natty, I assumed that you were using the Unity interface, the meta key opens the dash so that you can search for applications, in this case Users and Groups :)

If you are using Ubuntu Classic, it should be System > Administration > Users and Groups.

---

### Post by haqking on 2011-07-22
> **Gael33 said:**
> Hi, I tried pressing the 'Meta' key ... the one with the windows flag on it. Unfortunately, nothing happened. Can you give me any more instructions?

I am using Ubuntu 11.04 Natty, with VirtualBox 4.04 with the latest Extension Pack 4.08 running Windows XP.


users and groups

manage groups, highlight vboxusers and make sure you are in the group.

and the latest Vbox is 4.1 and extension pack to go with it.

---

### Post by Gael33 on 2011-07-22
Thanks to everyone who gave advice ... the problem is now solved.

Gael.

---

