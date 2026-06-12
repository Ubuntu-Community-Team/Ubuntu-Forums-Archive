---
title: "Ubuntu Server 8.10 cannot resolve host"
date: 2009-02-16
forum: Server Platforms
---

### Post by wvw on 2009-02-16
Hello

I have installed Ubuntu Server 8.10 some time ago. All went smooth 'cept for the machine name I entered during setup was abbreviated. After the installation I noticed the name is not what I typed in and went into /etc/hostname and changed it to what I initially typed in. This has now caused me some headaches as I keep getting the message below when I execute certain commands using sudo:

sudo: unable to resolve host ourintranetserver1

I can solve this problem by reinstalling as there's not yet anything important on the server, but I would like to try and fix the problem to learn, so I can fix it if I encounter it again in the future. I cannot recall what Ubuntu named the server after the setup so I cannot revert back to that name.

Does anyone have any iedeas?

Thanks in advance
wvw

---

### Post by Phlee on 2009-02-16
Please post your:

```
cat /etc/hosts
```

---

### Post by unixeducation on 2009-02-17
What does this command say?

```

hostname -f

```

---

