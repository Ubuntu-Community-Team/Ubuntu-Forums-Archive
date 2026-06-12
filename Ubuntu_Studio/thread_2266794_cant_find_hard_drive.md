---
title: "cant find hard drive"
date: 2015-02-25
forum: Ubuntu Studio
---

### Post by Francis_Dunnery on 2015-02-25
I am using the kdenlive video editor for the first time. my external hard drive is mounted and i have access to it via the browse network filing system but when i press 'add file'  in the video editor it only allows me to see as far back as the home menu. my external hard disk is not available on the add file from the kdenlive program. the external drive is working fine, i can access it no problem. how do i get the kedenlive program to see my external drive?

---

### Post by lukeiamyourfather on 2015-02-25
Is this an external hard drive or a network share? If it's a external hard drive it should show up under /media in the file browser. If it's a network share consider adding it to /etc/fstab and mount it in an easily accessible path.

---

### Post by Francis_Dunnery on 2015-02-25
ha I love you linux guys , you crack me up. you guys always presume that us green newbies know what you are talking about . 
adding it to /etc/fstab  .... now what the hell does that mean ha ha

---

### Post by lukeiamyourfather on 2015-02-25
Assuming we're talking about a network share this article discusses what I suggested.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Also check out this article on Wikipedia.

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by Francis_Dunnery on 2015-02-25
Oh man, that is waaaaaaaaaaaaaaaaaaaay above my head. I appreciate your help but I'm afraid I m out of my league this one. 
Pit just seems weird to me that my shared network drive can be seen and accessed from the desktop but not from with a program menu. How weird.

---

