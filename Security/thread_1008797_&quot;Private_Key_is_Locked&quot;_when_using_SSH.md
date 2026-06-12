---
title: "&quot;Private Key is Locked&quot; when using SSH"
date: 2008-12-11
forum: Security
---

### Post by LordKelvan on 2008-12-11
Hi:

I'm not sure if this is the proper forum to post this problem in, so if it isn't, please move it to the appropriate place.

I've set up password-less ssh logins on a few remote servers, and everything was working fine.  Then recently, when I tried to SSH to one, this dialog box pops up that says:

"An application is trying to access the private key id_rsa, but it is locked"

It then gives me options to unlock it.  I didn't try because I was worried about potential security issues.  So I clicked "Deny", the dialog disappears, and I suppose naturally, I have to enter a password to login (i.e., password-less SSH login no longer works).  

In order to make SSH behave like it had before, I ran:

```
ssh-add -D
```

to remove all identities, and then ran:

```
ssh-add
```

to re-add my identity.  

I would greatly appreciate it if someone could tell me:

[LIST=1]
[*]what caused the original change in behaviour
[*]why the above steps "fixed" it
[*]what does "unlocking" the private key do
[/LIST] 

My current theory (more of hunch :)) is that there is a "lifetime" associated with identities, and it just so happened that mine had expired.  If this is so, could people also tell me where this lifetime is specified?

Cheers,
LK

---

### Post by m_l17 on 2008-12-11
I'm having a similar issue. I'm getting the same pop-up. But I'm using a key with a password. 

I get this strange behavior:

If I enter the correct password, it will not accept it. But if I try again right after it works without the pop-up poping up again and letting me login without the password that goes with the key.

I found this in launcpad.net:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/187127]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/187127")

I tried:

```
sudo gconftool-2 --set -t bool /apps/gnome-keyring/daemon-components/ssh false
```

But still got the same problem. The only thing that worked was:

```
sudo killall gnome-keyring-daemon
```

But I don't know if the above will affect something else, for now things seem ok.

Things where working just fine yesterday. I haven't done anything, like any major update or install.

I have another system and it's not having this problem. The one with this issue is 32bit and the other is 64bit. Both are running Xubuntu 8.10. 

I will like to know what is causing this? And if killing gnome-keyring-daemon will cause more problems?

---

### Post by LordKelvan on 2009-01-23
Can anyone help?

---

### Post by danmmr on 2010-05-10
I believe this is happening because the gnome-keyring daemon is managing the ssh keys (it shouldn't do this since ssh already has an agent).  You can tell the daemon to stop doing this by issuing this command:

sudo gconftool-2 --set -t bool /apps/gnome-keyring/daemon-components/ssh false


There is more info here:  [http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)


I think this fixed the problem for me.  I say think because a system update occurred at the same time.   Good luck.

Cheers

---

