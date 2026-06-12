---
title: "SSH pass phrases and gnome-keyring"
date: 2008-11-16
forum: Security
---

### Post by robbert on 2008-11-16
Hi,

I'm using a public/private key pair to login without password with SSH on remote machines. I was using libpam-ssh before to get my private key automatically unlocked. After the update to Ubuntu Intrepid I was trying to let gnome-keyring manage all my keys. Once trying to connect to a remote ssh host it asked for my pass phrase and whether I would like it to remember it. I entered it, and said it should remember it.

This is working fine, every time I login on my machine my SSH keys are automatically unlocked and I'm able to login on a remote machine without password.

I'm only bothered where my pass phrase is stored. Using "Applications > Accessories > Password and encryption keys" I'm able to see the SSH key under "my personal keys". But there is nowhere the option to say that it shouldn't remember my pass phrase anymore. 

Under the tab "Passwords" I see that it remembers passwords for my wireless networks. And I'm able to remove those.

So my question is, where does gnome-keyring store my ssh pass phrases? How do I get rid of it remembering them?

---

### Post by lovinglinux on 2008-11-27
```
So my question is, where does gnome-keyring store my ssh pass phrases?
```

It should be in Applications > Accessories > Password and Encryption Keys, under the "Passwords" tab. There should be a "Unlock password for "id_rsa". In my Hardy box it is there and I can delete it, which makes keyring ask for the passphrase again next time I connect to the ssh server.

If you can't find it, you could try disabling the remembering passwords settings in System >> Preferences >> Password and Encryption Settings, under the PGP  Passphrases tab. 

I have the opposite problem. Gnome-keyring doesn't remember the ssh password in my Intrepid machine and changing Password and Encryption Settings does not have any effect.

---

### Post by Luz77 on 2011-10-19
> **lovinglinux said:**
> 
I have the opposite problem. Gnome-keyring doesn't remember the ssh password in my Intrepid machine and changing Password and Encryption Settings does not have any effect.

I know its a late response, but i googled for exactly this and the solution wasn't yet here, so now it comes:
open a console and write [COLOR=Red][B]ssh-add
[/B][/COLOR]

---

