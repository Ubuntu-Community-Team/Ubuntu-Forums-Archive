---
title: "Sudoers issue on 12.04 beta 4"
date: 2012-04-05
forum: Security
---

### Post by cesera on 2012-04-05
Was directed here from the Ubuntu +1 forum.
I seem to have run into an issue with sudo on lubuntu 12.04 beta 2. I have added the following  line to sudoers (using "sudo visudo"), but I still get prompted for a  sudo password when using truecrypt or fsck.
```
userid    ALL=(ALL) NOPASSWD: /usr/bin/truecrypt, /sbin/fsck -a
```I know there are security implications and things with that line, but  the issue is that is should allow me to run truecrypt and fsck -a  without typing in my password and it doesn't seem to work.

---

### Post by matt_symes on 2012-04-05
Hi

> **cesera said:**
> Was directed here from the Ubuntu +1 forum.
I seem to have run into an issue with sudo on lubuntu 12.04 beta 2. I have added the following  line to sudoers (using "sudo visudo"), but I still get prompted for a  sudo password when using truecrypt or fsck.
```
userid    ALL=(ALL) NOPASSWD: /usr/bin/truecrypt, /sbin/fsck -a
```I know there are security implications and things with that line, but  the issue is that is should allow me to run truecrypt and fsck -a  without typing in my password and it doesn't seem to work.

This is from mine

```
matthew ALL=NOPASSWD: /usr/bin/apt-get, /usr/sbin/iotop
```

Check out

```
man sudoers
```

for more information. The man pages can be better than internet tutorials.

Kind regards

---

### Post by Cheesemill on 2012-04-05
Can you post your full /etc/sudoers file so we can take a look.

---

### Post by cesera on 2012-04-06
Here is a copy of my sudoers file, had to add the .txt extension to get it to upload. Most of the file is just the default file, I have only added the one line. I have had a long look at the man page and can't find anything wrong. I presume it is something simple that I have missed, so any clues would be appreciated.

Thanks,
Kees

---

### Post by Cheesemill on 2012-04-06
The only suggestion that I have is to try moving your added line to the bottom of the file, then log off / log on and try again.

Edit - Another suggestion, try removing the spaces so it reads as follows:
```
kees     ALL=(ALL)NOPASSWD:/usr/bin/truecrypt,/sbin/fsck -a
```

---

### Post by Soul-Sing on 2012-04-07
```
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
```
bottomline please

via ```
sudo visudo
```

---

### Post by cesera on 2012-04-07
> **Cheesemill said:**
> The only suggestion that I have is to try moving your added line to the bottom of the file, then log off / log on and try again.

Edit - Another suggestion, try removing the spaces so it reads as follows:
```
kees     ALL=(ALL)NOPASSWD:/usr/bin/truecrypt,/sbin/fsck -a
```

Did both and that did the trick. Just don't understand why it has to be at the bottom of the file, have looked at the man page again and not sure what difference it makes in this case. I am not using any thing that needs to be set before I include it.

Thanks you very much.

---

### Post by cesera on 2012-04-07
> **leoquant said:**
> ```
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
```bottomline please

That would work as well, but not for the 'fsck -a', which I like to include otherwise I have to enter my password whenever checking the truecrypt volumes.

Thanks for your help.

---

### Post by Cheesemill on 2012-04-07
> **cesera said:**
> Did both and that did the trick. Just don't understand why it has to be at the bottom of the file, have looked at the man page again and not sure what difference it makes in this case. I am not using any thing that needs to be set before I include it.

Thanks you very much.

Statements in the sudoers file get applied in the order the occur in the file, and override any conflicting statements above them. In your original attempt, the nopasswd statement was being applied properly, but then being overidden by the '%sudo    ALL=(ALL:ALL) ALL' statement at the bottom of the file, which  meant that anyone in the sudo group had to supply a passward for all commands.

Hope this makes sense :)

---

### Post by cesera on 2012-04-10
> **Cheesemill said:**
> Statements in the sudoers file get applied in the order the occur in the file, and override any conflicting statements above them. In your original attempt, the nopasswd statement was being applied properly, but then being overidden by the '%sudo    ALL=(ALL:ALL) ALL' statement at the bottom of the file, which  meant that anyone in the sudo group had to supply a passward for all commands.

Hope this makes sense :)

That makes lots of sense. Thanks for clarifying that.

---

### Post by rahuldg on 2012-07-22
> **Cheesemill said:**
> Statements in the sudoers file get applied in the order the occur in the file, and override any conflicting statements above them. In your original attempt, the nopasswd statement was being applied properly, but then being overidden by the '%sudo    ALL=(ALL:ALL) ALL' statement at the bottom of the file, which  meant that anyone in the sudo group had to supply a passward for all commands.

Hope this makes sense :)

Thank you very much.
I was been wasting a lot of time on making the sudo work.
Commenting that group done it.

---

