---
title: "Password Management?"
date: 2007-01-26
forum: Server Platforms
---

### Post by vicarious on 2007-01-26
Password and key management seems to be kind of a mess. Right now I have 
- my user password for login/GDM/screensaver/sudo
- Firefox's custom password manager for websites 
- Thunderbird's password manager to start email 
- gpg-agent to manage my gpg keys
- ssh-agent to manage my ssh keys
- gnome-keyring to for network manager/samba, and 
- gpass for everything else.

It looks like gnome-keyring is eventually going to be able to manage most of these (I hope?) but I looked at the readme and found this:
> The library libgnome-keyring is used by applications to integrate with
the gnome keyring system. However, at this point the library hasn't been
tested and used enought (sic) to consider the API to be publically
exposed. Therefore [b]use of libgnome-keyring is at the moment limited to
internal use in the gnome desktop[/b]. However, we hope that the
gnome-keyring API will turn out useful and good, so that later it
can be made public for any application to use.

Does this mean the API is not finalized and shouldn't be used by (non-Gnome) developers?

Also, if anyone has any tips to safely shorten my list up top, let me know. :)

---

