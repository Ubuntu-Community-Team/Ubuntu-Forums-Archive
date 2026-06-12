---
title: "Command to ouput Ubuntu version?"
date: 2008-07-04
forum: The Cafe
---

### Post by elmer_42 on 2008-07-04
Is there a command that will output the current version of Ubuntu, e.g. "8.04.1" or "Ubuntu 8.04.1"?

---

### Post by logos34 on 2008-07-04
lsb_release -a

uname -a

---

### Post by p_quarles on 2008-07-04
Either one of:
```
cat /etc/issue
```
or 
```
lsb_release -a
```
should give you the version number and code-name.

---

### Post by kevin11951 on 2008-07-04
> **elmer_42 said:**
> Is there a command that will output the current version of Ubuntu, e.g. "8.04.1" or "Ubuntu 8.04.1"?

well if you hit Ctrl + Alt + F1, it tells you (Ctrl + Alt + F7 to go back)

---

### Post by elmer_42 on 2008-07-04
Thanks, guys!

---

### Post by Silpheed2K on 2008-07-04
While we're at it.. what's the shortcut keys to the system monitor?
I'd really like to pull that up in CPU hogging situations.

---

### Post by kevin11951 on 2008-07-04
> **Silpheed2K said:**
> While we're at it.. what's the shortcut keys to the system monitor?
I'd really like to pull that up in CPU hogging situations.

i would LOVE to know that!

---

### Post by Dr Small on 2008-07-04
> **Silpheed2K said:**
> While we're at it.. what's the shortcut keys to the system monitor?
I'd really like to pull that up in CPU hogging situations.
That would be easy on Openbox. Write your own keybind for it. For GNOME, on the otherhand...

---

### Post by Tigershell on 2008-07-04
> **Silpheed2K said:**
> While we're at it.. what's the shortcut keys to the system monitor?
I'd really like to pull that up in CPU hogging situations.

Set a shortcut key to gnome-system-monitor

---

### Post by kevin11951 on 2008-07-04
> **Tigershell said:**
> Set a shortcut key to gnome-system-monitor

how...?

---

### Post by Tigershell on 2008-07-04
> **kevin11951 said:**
> how...?

Ah crap.. was thinking of xfce.. sorry. :popcorn:

**Edit: This link might help;**
[create-custom-keyboard-shortcuts-in-linux]("http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/") :)

---

