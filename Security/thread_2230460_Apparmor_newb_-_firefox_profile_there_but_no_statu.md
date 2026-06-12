---
title: "Apparmor newb - firefox profile there but no status?"
date: 2014-06-19
forum: Security
---

### Post by jcllings on 2014-06-19
I've never actively used apparmor. Thought I would give it a whirl. Since I use FF and not Chromium, I tried to set it up. 

user@somemachine:/etc/apparmor.d$ !2002
sudo aa-status | grep fire

Hmm... not there. 

user@somemachine:/etc/apparmor.d$ ls -l /etc/apparmor.d/*fire*
-rw-r--r-- 1 root root 4877 Apr 10 14:10 /etc/apparmor.d/usr.bin.firefox

...except that it IS there. Hm... To enable, the online docs say to use aa-enforce except that:

user@somemachine:/etc/apparmor.d$ sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
sudo: aa-enforce: command not found

Clues? Perms are the same for all files in /etc/apparmor.d/

---

### Post by Nobody Nessie on 2014-06-19
I am not sure to have all understood. I thought that firefox was already in enforce mode ? But anyway, you can check first with :

```
user@somemachine: sudo apparmor_status
```

And see if your firefox profile is already in enforce mode or, at least, loaded. If it is not in enforce mode then :

```
user@somemachine: sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

---

### Post by jcllings on 2014-06-19
> **Nobody Nessie said:**
> I am not sure to have all understood. I thought that firefox was already in enforce mode ? But anyway, you can check first with :

```
user@somemachine: sudo apparmor_status
```

And see if your firefox profile is already in enforce mode or, at least, loaded. If it is not in enforce mode then :

```
user@somemachine: sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

Please have a closer look at my post. Both of these have already been tried. 
The first results in no mention of Firefox profile despite the presence of the file. The second results in "aa-enforce: command not found".

---

### Post by Nobody Nessie on 2014-06-19
> **jcllings said:**
> Please have a closer look at my post. Both of these have already been tried.

Yes, that was I have done, I read this :

> **jcllings said:**
> user@somemachine:/etc/apparmor.d$ sudo aa-enforce /etc/apparmor.d/usr.bin.firefox

Good luck, other peoples would surely help you.

---

### Post by jcllings on 2014-06-19
OK, one mystery down. apparmor-utils package was missing.

---

### Post by maglin2 on 2014-06-19
Now that you have apparmor utils you can use the enforce command.

The other way to enable firefox profile is to move the disable file for firefox from /etc/apparmor.d/disable to somewhere else, then reboot.

---

