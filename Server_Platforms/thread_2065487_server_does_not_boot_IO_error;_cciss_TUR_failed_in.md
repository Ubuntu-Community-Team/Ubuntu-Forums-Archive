---
title: "server does not boot: I/O error; cciss TUR failed in CCISS_GETLUNINFO"
date: 2012-10-02
forum: Server Platforms
---

### Post by surfer on 2012-10-02
hello

i have a server with ubuntu precise installed. up to now it booted perfectly well but after the last upgrade it does not anymore.

during the boot process i see error messages like

```
- end_request: I/O error, dev dm-0, sector 123456
- Error: inappropriate ioctl for device
- cciss TUR failed in CCISS_GETLUNINFO: inaproppriate ioctl for device
```

the server boots and i see the login prompt. when i enter the username and hit 'return', i see several end_request error messages and get a fresh login prompt. i can not log in!

the filesystem is ok; i can boot into the rescue mode without any problem.

i also booted with a live system (i use FAI and can log in via ssh). i checked all the filesystems and they are ok.

i saw a [similar post]("http://ubuntuforums.org/showthread.php?t=1879206") but without any answer.

any ideas how to fix this?

---

### Post by hasan.akgoz on 2012-10-02
What is the hardware specs? Are you using RAID?

---

### Post by surfer on 2012-10-02
it's a hp blade system. i do not use any raid.

(i can get you more details about the hardware; what are you interested in?)

---

### Post by surfer on 2012-10-02
i just saw a new error message:
```
device-mapper: table: 252:0: multipath: error getting device
```

does anyone know what that means? and more importantly: how i can fix it?

---

### Post by surfer on 2012-10-02
ok, it was a multipath issue. i had to blacklist the local disks:
```
# /etc/multipath.conf

blacklist {

    devnode "^sd[a-c]"

}


```

that did the trick.

---

### Post by hasan.akgoz on 2012-10-02
I hope you'll get better soon. interesting problem :)

---

