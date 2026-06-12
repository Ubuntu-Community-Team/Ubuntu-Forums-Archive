---
title: "Ubuntu server kills connections every 5 -10 minutes."
date: 2008-12-23
forum: Server Platforms
---

### Post by vibemanslim on 2008-12-23
Hello fellow Ubuntu users. I am having an issue with my server. I am using the latest release of Ubuntu Server (8.10 Intrepid Ibex.
Every 5-10 minutes I lose all connectivity to the system. Apache, FTP, and SSH. I have checked the logs and services. They 're all clean.](*,)

Any Ideas?

---

### Post by cariboo on 2008-12-23
Dmesg should show you what is happening, at hte prompt type:

```
dmesg | tail -n 10
```

Will print out the last ten lines of dmesg. or 

```
dmesg | grep <nicdriver>
```

where <nicdriver> is your network card driver.

Jim

---

### Post by deeq on 2008-12-24
Same problem [http://ubuntuforums.org/showthread.php?t=806614]("http://ubuntuforums.org/showthread.php?t=806614")

---

### Post by vibemanslim on 2008-12-24
> **cariboo907 said:**
> Dmesg should show you what is happening, at hte prompt type:

```
dmesg | tail -n 10
```

Will print out the last ten lines of dmesg. or 

```
dmesg | grep <nicdriver>
```

where <nicdriver> is your network card driver.

Jim
Hmmmm ...... I entered this command and everything looks good. 

eth0: registered as <GENERIC NIC>
eth0: link up
eth0: no IPv6 routers present

---

### Post by vibemanslim on 2008-12-24
> **deeq said:**
> Same problem [http://ubuntuforums.org/showthread.php?t=806614]("http://ubuntuforums.org/showthread.php?t=806614")
I think that guy had a problem with his main board. My systems are virtual.

---

### Post by vibemanslim on 2008-12-24
BTW... Thank you for help... I am hoping that with all the brain power out there, this issue can be resolved.

---

