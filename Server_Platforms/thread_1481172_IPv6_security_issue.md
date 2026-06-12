---
title: "IPv6: security issue?"
date: 2010-05-12
forum: Server Platforms
---

### Post by Saorex on 2010-05-12
Hi guys.

I recently installed my first Ubuntu Server (10.04) where I work. It is used as a LAMP server for the corporate intranet (on which I deploy Web apps, being a software engineer). I also installed a Subversion server on it, something I had been missing since I work here.

Anyway. This morning an IT guy came to me asking if IPv6 could easily be disabled on that server because it might be a security threat. I guess he might be true as our firewall (for what I know) only monitor IPv4 traffic. But again, I'm not sure.

Do you guys think this could really be an issue, and if yes, how can I disable it? I've read about modifying GRUB but this means restarting the server, which I would prefer not to.

Thanks a lot for your help and time.

Matt

---

### Post by arrrghhh on 2010-05-12
Perhaps this [Ubuntu guide](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) can help.

---

### Post by Saorex on 2010-05-12
Thanks. I tried this command as suggested:

```
lsmod | grep inet6
```

and got no output. Though ifconfig gives me this:

```
inet6 addr: fe80::250:56ff:fe89:4222/64 Scope:Link
```

Should I still perform this:

```
sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases
```

as recommend by the guide?

---

### Post by arrrghhh on 2010-05-12
Hrm... well those are conflicting results.  I'm not sure, honestly.  If ```
lsmod | grep inet6
``` returned nothing, according to the guide IPV6 s/b disabled.

---

### Post by Saorex on 2010-05-12
I just found this other command:

```
ip a | grep inet6
```

and got the following output:

```
    inet6 ::1/128 scope host
    inet6 fe80::250:56ff:fe89:4222/64 scope link

```

Just like ifconfig returned. I guess I'll follow the guide and see if anything changes after the reboot (which I'll have to do tonight though).

Thanks again.

---- EDIT ----

Mmmmm... when I go to /etc/modprobe.d/, I find no aliases file and therefore cannot add "alias net-pf-10 off" in it. Should I create one then?

---

### Post by arrrghhh on 2010-05-12
Yes, simply create the alias.

---

### Post by benderisgreat on 2010-05-12
add ipv6.disable=1 to the  GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```
and run update-grub before you reboot
this is assuming you use grub2 with which ubuntu 10 comes with. If you've upgraded and are using grub 'legacy' then I would just edit /boot/grub/menu.lst and add ipv6.disable=1 to the kernel line.

---

### Post by arrrghhh on 2010-05-12
IMHO the easiest way to do it is the method benderisgreat mentioned.

---

### Post by Saorex on 2010-05-17
I see. I just edited the file (/etc/default/grub) without rebooting, now the line is:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet ipv6.disable=1"
```

After seeing other examples, values must be separated by a space, if I understand correctly.

I will reboot as soon as I can and let you know if it worked.

---

### Post by Saorex on 2010-07-06
Hi guys. Just wanted to let you know it worked perfectly. Thanks for your help.

---

