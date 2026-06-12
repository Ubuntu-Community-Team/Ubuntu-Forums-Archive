---
title: "password everytime in my sharer folder"
date: 2008-03-09
forum: Virtualisation
---

### Post by ruialexbarbosa on 2008-03-09
Hello,

I created the "S" folder to share files between UBUNTU 7.04 and XP in VMware.

It works ok (sometimes I have problems deleting files in XP but...

My problem is everytime I start XP and want to use the sharer folder, it asks for a password. How can I just make it automatic?

Thanks

---

### Post by fjgaude on 2008-03-09
Did you enter your samba password:

```
sudo smbpasswd -a loginname
```

See if this works.

---

### Post by ruialexbarbosa on 2008-03-09
Just did that, when I reboot XP, it asks for the password again... :(

---

### Post by fjgaude on 2008-03-09
Do you get a screen that gives you options? One that permits you to keep the password for this session, forever?

---

### Post by ruialexbarbosa on 2008-03-09
Nope...In XP, it just asks for the password for the sharer drive

---

### Post by fjgaude on 2008-03-09
One thing, maybe you have the wrong type of password asking program installed.

I use **ssh-askpass-gnome**. This one gives options to store your password in the keyring file so that it knows you are the login user.

I wonder which kind do you have?

---

### Post by popch on 2008-03-09
> **ruialexbarbosa said:**
> 
I created the "S" folder to share files between UBUNTU 7.04 and XP in VMware. (...) everytime I start XP and want to use the sharer folder, it asks for a password.

Is the 'S' folder a drive in MyComputer, i.e. the S: drive? ***If so***, Windows tries to use the same userid and password to connect to that drive as you used to login to windows (if you use a login at all).

Therefore, using the same userid and password to access the S: drive as used for logging in to Windows ought to do the trick.

---

### Post by ruialexbarbosa on 2008-03-09
How do I know which program I have to store/ask my password?

And if I put a password for windows, it will give me exactly the same trouble as to put it for my shared folder only, right? I'd just want to press the red GO button (just an expression).

---

### Post by fjgaude on 2008-03-09
There are two areas of Shares, one in Ubuntu and one in Windows.

When you are in Windows and you try to access a folder that is a share on Ubuntu it is Ubuntu asking for the password.

You do have Samba shares setup in Ubuntu using the System menu?

---

### Post by ruialexbarbosa on 2008-03-09
When I go to Menu - System - Administration - Shared Folders I see the HOME/ALEX/SHARER folder... 

Is this it?

---

### Post by fjgaude on 2008-03-09
Yes... make sure you set the workgroup to a name that you use in Windows. Make sure the read only box is not clicked. That name will be seen in Network menu of Windows, in Explorer, down near the bottom of the file listing.

You likely will have to re-start vmware with its Windows vm before you see the share there.

---

### Post by dcstar on 2008-03-12
> **ruialexbarbosa said:**
> Hello,

I created the "S" folder to share files between UBUNTU 7.04 and XP in VMware.

It works ok (sometimes I have problems deleting files in XP but...

My problem is everytime I start XP and want to use the sharer folder, it asks for a password. How can I just make it automatic?

Thanks

You can edit /etc/samba/smb.conf and make the share accessible by the Guest account, then it may not bother asking for credentials.

There are many (many) options in that file that might do the trick.

---

### Post by ruialexbarbosa on 2008-06-05
Well, after not succeeding LOTS of times, I did it the other way round. I share the XP shared documents folder, instead of the sharer folder.

---

### Post by fjgaude on 2008-06-05
In Ubuntu how do you see the shared folder that is in Windows VM?

---

### Post by fjgaude on 2008-06-05
In Ubuntu how do you see the shared folder that is in Windows VM?

---

### Post by ruialexbarbosa on 2008-06-06
Well, I went to Network and it showed me the xp. It was just a matter of adding the shared folders folder to my file browser links.

I used the XP procedure to make it part of the MSHOME network, I guess this helped...

---

### Post by fjgaude on 2008-06-06
Also, don't forget the password needed on the Ubuntu side:

```
sudo smbpasswd -a <name>
```

Enter your password two or three times and then you should be able to see the Ubuntu shares.

---

