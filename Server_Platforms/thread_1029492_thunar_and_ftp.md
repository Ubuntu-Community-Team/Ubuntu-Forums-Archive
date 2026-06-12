---
title: "thunar and ftp"
date: 2009-01-03
forum: Server Platforms
---

### Post by maclenin on 2009-01-03
Will thunar ever be blessed with FTP capability?

---

### Post by altonbr on 2009-11-13
I'd like to second this question... Can't find anything online.

---

### Post by Simian Man on 2009-11-13
You can do this with a combination of Thunar, Gigolo and gvfs.  Use Gigolo to mount network drives (including FTP and SSH), which will mount them in .gvfs and then you can open them with Thunar.

This is the setup I use and it works well, not quite so easy as with nautilus though.

---

### Post by maclenin on 2009-11-14
I have since found a happy balance among thunar / midnight commander / ye olde command line - all work perfectly for me....

Thanks for the notes!

---

### Post by Phil Urich on 2011-04-29
It's in Thunar's FAQ: [http://thunar.xfce.org/pwiki/documentation/faq#when_will_it_support_sambanetwork_browsing]("http://thunar.xfce.org/pwiki/documentation/faq#when_will_it_support_sambanetwork_browsing")  Short answer: never. Part of why I prefer Dolphin and Konqueror.

---

### Post by tupfzom on 2012-12-10
Just for the record, if someone finds this by searching (as I did): Thunar *does* work as an FTP client (as well as SSH/SFTP or Samba) - see the [Wiki page]("http://wiki.archlinux.org/index.php/Thunar#Using_Thunar_to_browse_remote_locations").

---

### Post by maclenin on 2012-12-12
**tupfzom!**

Schön dank for the update / reference!

---

