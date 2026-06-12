---
title: "unlock private key"
date: 2008-07-01
forum: Security
---

### Post by rgrig on 2008-07-01
After the latest update there is a window that asks me the passphrase to unlock the private key when I try to use ssh. Thank you, but no thanks, I prefer to use ssh-agent myself and control its lifetime. How do I get rid of that window?

---

### Post by Biochem on 2008-07-01
I had the same problem a while ago. Unfortunately I'm not sure how I solved it. It has to do with your key being stored in a keyring somewhere. On Ubuntu I think seahorse is the default. Have a look in the password tab. if you ssh password is there I think deleting it will do the trick.

---

### Post by rgrig on 2008-07-04
I removed seahorse completely and the window still appears :(

---

### Post by Biochem on 2008-07-04
Ok the other thing i did at the same time configure my ssh client to use different keys for specific server. Maybe renaming the keyfile was the trick.

in ~/.ssh
rename id_rsa

then create a file named config containing

Host *    # can be specific server(s) 
IdentityFile ~/.ssh/renamed_id_rsa

for more configuration option
man ssh_config

---

### Post by _Narcisse_ on 2008-10-24
Just in case : 

I think it's a bug, you need to disable SSH agent support in Gnome Keyring. 

[http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)

That's how I worked it out.

---

### Post by nubdora on 2008-10-24
> **_Narcisse_ said:**
> Just in case : 

I think it's a bug, you need to disable SSH agent support in Gnome Keyring. 

[http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)

That's how I worked it out.

+1

When I read this, Gnome Keyring was the first thing that came to mind since rgrig stated, *"After the latest update..."*

---

### Post by _Narcisse_ on 2008-10-24
On my side, I always got this annoying pop-up with Hardy Heron.
I thought I had messed up with SSH keys.
I didn't know about Keyring until I found this bug report :

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/187127](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/187127)

---

