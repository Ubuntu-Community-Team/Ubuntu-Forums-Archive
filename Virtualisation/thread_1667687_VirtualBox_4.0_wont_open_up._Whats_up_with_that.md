---
title: "VirtualBox 4.0 wont open up. Whats up with that?"
date: 2011-01-15
forum: Virtualisation
---

### Post by ert69 on 2011-01-15
i installed virtualbox 4.0 and have used it for some time now... Recently it just wont open up and I duno what to do.. I've tryed reinstalling, but its still not opening... Any ideas?

---

### Post by sikander3786 on 2011-01-15
Try opening it from the command line and post the output.

Applications > Accessories > Terminal:
```
VirtualBox
```

---

### Post by sikander3786 on 2011-01-15
Try opening it from the command line and post the output.

Applications > Accessories > Terminal:
```
VirtualBox
```

---

### Post by sikander3786 on 2011-01-15
Try opening it from the command line and post the output.

Applications > Accessories > Terminal:
```
VirtualBox
```

---

### Post by ert69 on 2011-01-15
Says this...
```
VirtualBox: supR3HardenedVerifyDir: Cannot trust the directory "/usr/lib/virtualbox": group and/or other writable (st_mode=040775)

```

---

### Post by CharlesA on 2011-01-16
Post the output of this please:

```
ls -ld /usr/lib/virtualbox
```

---

### Post by slooksterpsv on 2011-01-16
In terminal, I would run:

```

sudo apt-get purge virtualbox-4.0

```

Then reinstall.

---

### Post by ert69 on 2011-01-19
> **CharlesA said:**
> Post the output of this please:

```
ls -ld /usr/lib/virtualbox
```

```
ert69@Ubuntu:~$ ls -ld /usr/lib/virtualbox
drwxr-xrwx 5 root root 4096 2011-01-15 22:14 /usr/lib/virtualbox
ert69@Ubuntu:~$ 

```

---

### Post by ert69 on 2011-01-19
> **slooksterpsv said:**
> In terminal, I would run:

```

sudo apt-get purge virtualbox-4.0

```

Then reinstall.

Nope.. tryed that already... says the same thing in terminal.. :S

---

### Post by CharlesA on 2011-01-20
> **ert69 said:**
> ```
ert69@Ubuntu:~$ ls -ld /usr/lib/virtualbox
drwxr-xrwx 5 root root 4096 2011-01-15 22:14 /usr/lib/virtualbox
ert69@Ubuntu:~$ 

```
Yep. That's the problem, it should look like this:

```
charles@thor:~$ ls -ld /usr/lib/virtualbox/
drwxr-xr-x 5 root root 12288 2011-01-19 08:37 /usr/lib/virtualbox/
```

You could use chmod to change it to the correct permissions, but I really hope the permissions inside the directory are ok.

---

### Post by CharlesA on 2011-01-20
> **ert69 said:**
> ```
ert69@Ubuntu:~$ ls -ld /usr/lib/virtualbox
drwxr-xrwx 5 root root 4096 2011-01-15 22:14 /usr/lib/virtualbox
ert69@Ubuntu:~$ 

```
Yep. That's the problem, it should look like this:

```
charles@thor:~$ ls -ld /usr/lib/virtualbox/
drwxr-xr-x 5 root root 12288 2011-01-19 08:37 /usr/lib/virtualbox/
```

You could use chmod to change it to the correct permissions, but I really hope the permissions inside the directory are ok.

---

