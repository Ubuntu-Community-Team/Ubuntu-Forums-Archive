---
title: "Ease samba configuration"
date: 2007-12-23
forum: Ubuntu Brainstorm
---

### Post by loa on 2007-12-23
I have an idea that would ease sharing folders over the network with samba. It would mean changing the System -> Administration -> Shared folders window a bit.The idea is that there would be an extra tab there. In that tab, you would be given the ability to enable the smbguest user, and specify the password for it. This would be the equivalent of typing
```
smbpasswd -a smguest
smbpasswd -e smbguest 
```
in a terminal.

There could also be the option to enable other users for this also, but maybe it would be enough with just smbguest? Perhaps also a list of all smb-enabled users?

Also a little notice that this is now the user account that should be used when logging in to this machine via samba would be nice.

It took a long time before I figured out that I needed to do that smbpasswd stuff, and I think this would ease the smb configuration significantly for quite a lot people.

I appreciate any ideas, comments, and constructive criticism about this.

---

### Post by loa on 2007-12-23
Oops, looks like they are already doing something similar in Hardy Heron 8.04. I just tested the alpha 2. It looks a bit confusing and unfinished by now, but it will hopefully improve.

---

### Post by loa on 2007-12-23
Oops again, happened to doublepost...

---

