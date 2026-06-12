---
title: "Need VirtualBox help in Ubuntu 12.04.2 LTS"
date: 2013-04-20
forum: Virtualisation
---

### Post by FulciLives on 2013-04-20
Hello!

So I recently did a clean install of Ubuntu 12.04 LTS (it was 12.04.2 that I downloaded). This is the 64-Bit version!

Installed VirtualBox (from the Ubuntu Software Center) and tried to run my existing Windows 7 install (pointed to the pre-existing VDI file) and when I tried to start it I get this:

[IMG]http://i.imgur.com/5NZNhVB.png[/IMG]
Any ideas?

---

### Post by FulciLives on 2013-04-20
I ended up uninstalling VirtualBox (through the software store) and just downloaded the newest DEB from the Oracle website and now it is working. Go figure.

---

### Post by Cheesemill on 2013-04-20
Have you tried doing what it asks?
What is the output of...
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Krovas on 2013-04-22
> **Cheesemill said:**
> Have you tried doing what it asks?
What is the output of...
```
sudo /etc/init.d/vboxdrv setup
```



```

sudo: /etc/init.d/vboxdrv: command not found
```


and...

```
jupiterjones@thievesguild:~$ sudo dpkg-reconfigure virtualbox-dkms

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-4.1.12 DKMS files...
Building only for 3.5.0-23-generic
Building initial module for 3.5.0-23-generic
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
```

---

### Post by nonamedotc on 2013-04-22
> **FulciLives said:**
> I ended up uninstalling VirtualBox (through the software store) and just downloaded the newest DEB from the Oracle website and now it is working. Go figure.

Just for your information - you can set up apt-get sources for Oracle Virtualbox instead of using *deb files. Updating becomes a lot easier! :)

---

