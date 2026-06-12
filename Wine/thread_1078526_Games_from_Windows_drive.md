---
title: "Games from Windows drive"
date: 2009-02-23
forum: Wine
---

### Post by Argama on 2009-02-23
Hi, 
I recently wanted to try and get started to play games on my Ubuntu using Wine. All of my games are installed on my D drive same drive as my Ubuntu 8.04 is installed (Windows on C drive) but I cant browse my D drive using Wine so I cant get to my games. Can anyone help plz? :)

---

### Post by konqueror7 on 2009-02-23
if i understand what you mean, you can just run it via terminal,
```
wine /media/Games/CS/CS.exe
```

or you can explore your drive and just right click it and select "open with wine"

---

### Post by Argama on 2009-02-23
Thanks, but thats the problem I cant browse my D drive :s

---

### Post by xzero1 on 2009-02-23
Maybe wine may not be configured. Run winecfg in a terminal and add your D: drive.

---

### Post by cogadh on 2009-02-23
Wine is not designed to run application that are installed in Windows, it is designed to install and run applications within Linux. In order to properly use your Windows games, you need to install them with Wine first. From the [Wine FAQ]("http://wiki.winehq.org/FAQ"):
> **I have lots of applications already installed in Windows. How do I run them in Wine?**

Short answer: You have to install them in Wine just like you did in Windows. Applications usually have a setup or installer program.

Long answer: Some applications can be copied from Windows to Wine and still work, but don't try this unless you like tinkering under the hood of your car while it's running.

Wine is not designed to interact with an existing Windows installation.

WARNING: Do not try to configure Wine to point to your actual Windows C:\ drive. This will break your Windows and require a reinstall. We have tried to make this hard to do so you probably cannot do it by accident. If you do manage this, Wine may or may not continue to operate, but your Windows install will be 100% dead due to critical parts of it being overwritten. The only way to fix Windows after this has happened is to reinstall it. 

As for why you can't "see" your Windows drive, it sounds to me like you are using a Wubi install (installed within Windows), so it cannot see the drive the virtual file system resides on. That is by design and I don't think there is any way around it.

---

### Post by konqueror7 on 2009-02-23
i mean not browsing within wine's open dialog, rather on on your native ubuntu, explore in nautilus and run it with wine...

---

### Post by cogadh on 2009-02-23
If this is a Wubi install and the applications you are browsing for are on the same Windows drive as Ubuntu's virtual file system, it doesn't matter how you are browsing, Ubuntu and Wine still can't "see" the contents of that drive. Besides, trying to run Windows apps with Wine that way still might not work, since many Windows apps rely on registry entries that are not found unless the app is actually installed in Linux through Wine.

---

### Post by konqueror7 on 2009-02-24
ah, so you want to make your drive d seen permanently in  wine? is that it?
go to Applications > Wine > Configure Wine, then on the drives tab, select either 'Auto-Detect' or manually add your drive...

sorry i misunderstood your need...;)

---

### Post by Argama on 2009-02-26
Thanks for the replies! I m gone try it :).
Thanks all.

---

### Post by Meow27 on 2009-02-26
for some games, doing copypasta from drive c to Wine's drive c works.

in ubuntu you usually can right click and run the program with wine smack off the bat

---

