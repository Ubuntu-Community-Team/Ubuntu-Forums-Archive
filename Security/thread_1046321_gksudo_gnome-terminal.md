---
title: "gksudo gnome-terminal"
date: 2009-01-21
forum: Security
---

### Post by jlochhead on 2009-01-21
Hi everyone,

I recently discovered that you can enable a root terminal by making a shortcut for gksudo gnome-terminal.

I totally agree with Ubuntu's no su policy, but sometimes it gets tedious typing out sudo all the time if I am doing lots of sudo related operations in the CLI. 

[B]Does anyone know if there would be any security concerns related to me doing this? 
[/B]

Thanks

---

### Post by cdenley on 2009-01-21
> **jlochhead said:**
> Hi everyone,

I recently discovered that you can enable a root terminal by making a shortcut for gksudo gnome-terminal.

I totally agree with Ubuntu's no su policy, but sometimes it gets tedious typing out sudo all the time if I am doing lots of sudo related operations in the CLI. 

[B]Does anyone know if there would be any security concerns related to me doing this? 
[/B]

Thanks

Why not use "sudo -s" whenever you need a root shell? Whenever anything is running as root there is a security concern. The idea is to use the root account as little as possible.

---

### Post by jlochhead on 2009-01-21
Ok cheers, that is something else I didn't know.

---

### Post by jerome1232 on 2009-01-21
or sudo -i
The only differences in sudo -s and sudo -i is this 
```
sudo -s
echo $HOME
/home/jeremy
exit
sudo -i
echo $HOME
/root
```
Well i'm sure there are other environment variables that are different. I guess I like sudo -i because I don't want x program making files in my $HOME that are owned by root.

---

