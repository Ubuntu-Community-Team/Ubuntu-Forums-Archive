---
title: "[SOLVED] vmware server console not working after upgrade to hardy"
date: 2008-04-28
forum: Virtualisation
---

### Post by trmentry on 2008-04-28
I just upgraded to Hardy on my laptop.  Everything seems to be working fine.  Except vmware-server-console doesn't run.

I figured I needed to reinstall it so I re-ran the pl script.  It says it installed fine.  But when I run it I get the following:

```

$ vmware-server-console
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

I'm not sure how to proceed on this.  Any pointers?

Thanks

---

### Post by bollix47 on 2008-04-28
Have a look at [_this post_]("http://ubuntuforums.org/showpost.php?p=4357442&postcount=10").

In particular there are a couple of ln commands near the bottom of the post that may help.

---

### Post by trmentry on 2008-04-28
Nope.  Those symlinks didn't appear to help.  Get the same errors as above. :(

Thanks though


This is just for the client console not for the server itself.  I have the server running on another box, so just need the client on my laptop.

---

### Post by bollix47 on 2008-04-28
[_This post_]("http://ubuntuforums.org/showpost.php?p=4712011&postcount=58") in the same thread shows errors similar to yours.  You could try copying the mentioned files.

---

### Post by trmentry on 2008-04-28
```

# cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
cp: `/lib/libgcc_s.so.1' and `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1' are the same file

# cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
cp: `/usr/lib/libpng12.so.0' and `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0' are the same file


```

---

### Post by trmentry on 2008-04-28
Also is there a clean way to uninstall the vmware-server-console?   I'm not wanting to manually do it unless necessary as I have vmware workstation working and dont' want to bork it by removing the wrong files.

---

### Post by trmentry on 2008-04-29
Found this **[ here](http://whocares.de/2008/02/25/running-vmware-server-console-on-ubuntu-hardy/)**  that had the answer that worked for me to get it working.  

```

cd /usr/lib/vmware-server-console/lib/libgcc_s.so.1

mv libgcc_s.so.1 libgcc_s.so.1.org

cd ../libpng12.so.0

mv libpng12.so.0 libpng12.so.0.org


```

---

### Post by mangeli on 2008-05-02
Those commands work for me, but I had to use sudo before.

---

### Post by trmentry on 2008-05-02
> **mangeli said:**
> Those commands work for me, but I had to use sudo before.

Yah... sorry about that... I was root when I did it and forgot about sudo.

---

### Post by jcolley on 2008-05-13
Those commands as sudo work for me also

---

### Post by MystaMax on 2008-05-19
Just chiming in...

 The steps provided by trmentry in the [post above]("http://ubuntuforums.org/showpost.php?p=4838586&postcount=7"), worked flawlessly! Thanks. I was trying to get vmware-server-console installed on a fresh hardy install, and this did the trick!

BTW, does anyone know if the vmware server icons were added when installed? If so? where?

---

### Post by bollix47 on 2008-05-19
Mine shows up under Applications > Other

---

### Post by trmentry on 2008-05-20
> **MystaMax said:**
> Just chiming in...

BTW, does anyone know if the vmware server icons were added when installed? If so? where?

This is the icon I used.

/usr/lib/vmware-server-console/share/pixmaps/console.png

---

### Post by jml75 on 2008-08-25
Thanx!

Fixed the problem for me to!

---

### Post by motin on 2008-09-04
Yes this solved it for me (having installed only the vmware server console):

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware-server-console/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server-console/lib/libpng12.so.0/
```

---

### Post by maschicago on 2008-09-07
Thanks, this solved the problem for me as well.

---

### Post by yopensource on 2009-01-15
> **motin said:**
> Yes this solved it for me (having installed only the vmware server console):

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware-server-console/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server-console/lib/libpng12.so.0/
```

It works!:guitar: great thanks

---

### Post by GonZo on 2009-03-09
works like a charm for me too! thanks!!

---

### Post by walom on 2009-04-03
> **motin said:**
> Yes this solved it for me (having installed only the vmware server console):

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware-server-console/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server-console/lib/libpng12.so.0/
```

Tried the OP's suggestions and after failing to solve my problem tried Motin's. Works like a charm now.

---

### Post by doronunu on 2009-05-21
for all the people who can work only with sudo just change the premissions
of the new files to 777 and you can run it as regular user

---

