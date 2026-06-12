---
title: "crwxrwxrwx  what means the &quot;c&quot; at the beginning"
date: 2009-04-28
forum: Server Platforms
---

### Post by nise8181 on 2009-04-28
I try to configure a pbx (asterisk) and get into trouble about an warning which says that the pbx has no permission to access /dev/dsp

Now I am asking me what means "c" at the beginning of priviledge information and who is "audio". Beside that I cannot see any impacts on how asterisk (running under root) doesn't get a permission to that file:

# ls -l /dev/dsp
crwxrwxrwx 1 root audio 14, 3 2008-12-01 20:25 /dev/dsp

any help?

---

### Post by ussndmac on 2009-04-28
The first character can be any of these:

d = directory
- = regular file
l = symbolic link
s = Unix domain socket
p = named pipe
c = character device file
b = block device file

---

### Post by geirha on 2009-04-28
It means it's a character device. [http://en.wikipedia.org/wiki/Device_file_system#Character_devices](http://en.wikipedia.org/wiki/Device_file_system#Character_devices)

---

