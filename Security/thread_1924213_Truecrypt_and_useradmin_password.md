---
title: "Truecrypt and user/admin password"
date: 2012-02-12
forum: Security
---

### Post by nick roto on 2012-02-12
I created a Truecrypt folder on a flash drive in Win7 that I want to read on my Ubuntu system. I select the file and when I attempt to mount it it asks for the password (which is all I need to do on Windows). Ubuntu then asks me for the user or administrator password. Fair enough, but if I give it the password of the Standard User account I'm in OR the Administrator password (the one I'm asked for when trying to install new software) I get the response "Failed to obtain Administrator privileges". I'm confused (and not aware that I have any other passwords) - I'm a novice user by the way. Help would be appreciated.

---

### Post by nick roto on 2012-02-12
Further research suggests I need to get the privilege as the Root user so need the Sudo command. As a newcomer I'm struggling to understand the exact command(s) to use and when to use it. In fact, do I have to do the whole mounting procedure in Terminal rather than use Truecrypt's own user interface?

---

### Post by nick roto on 2012-02-12
Ah, I see I should explain that I created the Truecrypt folder in Windows and now wish to open it in Ubuntu. Had I created it in Ubuntu I would have been asked about cross-platform use and admin password. Is it too late - do I need to start by creating the folder under Unix to use it on both? That would be a nuisance now but advice would be appreciated, thanks.

---

### Post by Dave_L on 2012-02-12
To allow mounting of a truecrypt volume by non-root users, I added a user group 'truecrypt' and added the following to /etc/sudoers via visudo:

```
# Users in the truecrypt group are allowed to run TrueCrypt as root.
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
```

---

### Post by nick roto on 2012-02-12
That feels like the answer Dave, thanks. Being very new to Unix I'll first need to understand user groups etc. I think there'll be some tutorials. Getting to grips with terminal speak is a challenge for newbies.

---

### Post by Dave_L on 2012-02-12
To add a new user group:

System >> Administration >> Users and Groups >> Manage Groups >> Add

(That's for Ubuntu 10.04. For a newer version, it may be different.)

-----

To edit /etc/sudoers, in a terminal, type in the command:

```
sudo visudo
```

That will open the file in an editor.  Paste the two lines (from my previous post) at the bottom of the file, then save the file.

Before doing that, you might want to make a backup of the file:

```
sudo cp -a /etc/sudoers /etc/sudoers.bak
```

---

### Post by nick roto on 2012-02-13
Thanks again Dave.
Yes, it is different. You can't manage groups anymore from the standard  interface in 11.10, you have to add new graphical i/f stuff or master  more terminal commands (groupadd?). Hopefully I'll get there soon.
Nick
P.S. There is much I already love about Ubuntu but it is really tiresome in other respects.  Windows ought not to be able to live with it but it isn't going to make  progress in popular use until it avoids the inevitable descent into  techie-ness. But it feels so close!

---

### Post by Megaptera on 2012-02-13
Hi nick roto,
I may have missed this but have you installed TrueCrypt in Ubuntu? Just asking just in case!!

---

### Post by nick roto on 2012-02-13
Yes M, but the volume I want to read was created in Win7.

---

### Post by Megaptera on 2012-02-13
So was mine (in Vista) but no probs with TrueCrypt *installed* in Ubuntu 10.04.3 so I just wondered if that could be a cause. Oh well ...

---

### Post by Dave_L on 2012-02-13
Megaptera:

I assumed the issue the OP is asking about (the need to provide the admin password) is a security feature, not a problem.

From the Truecrypt change log:

> Linux: When running without administrator privileges, TrueCrypt automatically attempts to elevate its access rights (if necessary) using the sudo command. The Linux version of TrueCrypt no longer supports the set-euid root mode of execution. These changes also prevent all discovered and undiscovered (if any) security issues related to the set-euid root mode of execution, including an issue affecting all previous Linux versions of TrueCrypt where a local non-administrator user could cause a denial of service or gain administrator privileges.

So I showed him how to modify sudoers to avoid having to enter the password, as I had done myself.

Maybe I'm wrong, and there's another solution?

---

### Post by nick roto on 2012-02-14
Actually Dave, I don't mind entering another password during the process, especially if it keeps Ubuntu ahead of game as far as security is concerned. The problem is that I'm offered the prompt and a box to enter the admin password, as I would be if I wanted to install new software, but it won't accept the password.
I understand (after some more reading) some of the issues about elevating privileges though I don't yet know enough to understand whether your method leaves me potentially exposed and for how long. I will get there but I wish I didn't have to learn quite so much at this early stage of my Unix life.
Is anyone able to clarify whether starting again by creating a Truecrypt folder on the memory stick in Ubuntu (which apparently asks for the Admin password during setup), then using it in Windows to store files, then reading those files again in Ubuntu would work without recourse to Sudo (and more delving into Unix guts)?

---

### Post by Dave_L on 2012-02-14
It should be simple enough to test that by creating a small Truecrypt container, e.g. 1mb, from Ubuntu.  Then check whether you can read and write to it from both Ubuntu and Windows.

What are the permissions of the Truecrypt container on the memory stick, as seen from Ubuntu? Is it owned by "root"?

---

### Post by nick roto on 2012-02-14
The instructions given here ([http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/](http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/)) led me to think that creating the volume in Ubuntu first might make a difference. However, the dialogue about cross-platform use no longer occurs so that doesn't help.
I don't know how to go about answering your question Dave.

---

