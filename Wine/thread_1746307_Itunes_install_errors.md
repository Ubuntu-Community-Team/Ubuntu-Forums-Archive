---
title: "Itunes install errors"
date: 2011-05-01
forum: Wine
---

### Post by garbagecanman on 2011-05-01
Im trying to install itunes on my girlfriends toshiba i just installed 10.10 on and i followed the procedure of downloading the .exe from apples site, latest 10.2 install for windows, then downloaded wine 1.2.2 i think and open the package with wine and it installed but i think said error:7 or something? i can open itunes but it says i wont be able to copy or burn cds???

Thanks

Edit: running WINE 1.3.18, UBUNTU 10.10, stock wine config. Let me know how i can check video drivers and terminal output for further assistance.

---

### Post by cogadh on 2011-05-01
iTunes doesn't work in Wine, you'd be better off using one of the Linux native music manager applications, like Amarok or Rythmbox.

---

### Post by garbagecanman on 2011-05-01
> **cogadh said:**
> iTunes doesn't work in Wine, you'd be better off using one of the Linux native music manager applications, like Amarok or Rythmbox.

like I said other than the cd error it seems to work, and I have to use itunes for my girlfriends iphone....

---

### Post by cogadh on 2011-05-01
You only need iTunes to activate the device, but once activated, iTunes isn't required to sync files with it or to burn CDs, any number of native applications can do that. As for whether or not it works, iTunes is one of the most heavily tested applications in Wine and at most it only ever gets a "silver" rating from Wine's Application Database due to how broken it is in Wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by garbagecanman on 2011-05-01
> **cogadh said:**
> You only need iTunes to activate the device, but once activated, iTunes isn't required to sync files with it or to burn CDs, any number of native applications can do that. As for whether or not it works, iTunes is one of the most heavily tested applications in Wine and at most it only ever gets a "silver" rating from Wine's Application Database due to how broken it is in Wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)


Ok so once i initiate the iphone (give it a name) how can i make sure  [libimobiledevice]("http://linux.softpedia.com/get/Programming/Libraries/libimobiledevice-56062.shtml") is installed and what app works best with iphone/ipod in ubuntu? It seems like i should just set her laptop up with dual boot like mine so she has a small 20gb partion just for itunes...

thanks

---

