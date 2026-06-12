---
title: "java installation error ubuntu 10.04 server edition"
date: 2010-07-02
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-02
I am using Ubuntu 10.04 Server edition as a Virtual Machine on one of my system.On KVM.
```

uname -a
 2.6.32-23-server #37-Ubuntu SMP Fri Jun 11 09:11:11 UTC 2010 x86_64 GNU/Linux

```

I needed java 1.5 for some program.So I downloaded it from Oracles website the Linux package for Java 1.5 [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter")

then did
a chmod +x java_ee_sdk-5_01-linux.bin
and tried 
```

 ./java_ee_sdk-5_01-linux.bin 
-bash: ./java_ee_sdk-5_01-linux.bin: No such file or directory

```

[Googled]("http://www.google.co.in/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=-bash:+./java_ee_sdk-5_01-linux.bin:+No+such+file+or+directory") it tried a link on Ubuntu forums [here ]("http://www.uluga.ubuntuforums.org/showthread.php?t=1355252&page=2")
the link is solved but it did not helped me much.
Some other forums I got that this problem can be solved by some method like 

```

ln -s libstdc++.so.6.0.8 libstdc++.so.5

```

in my case it was libstdc++.so.6       libstdc++.so.6.0.13 
so I did 

```

ln -s /usr/lib/libstdc++.so.6.0.8 /usr/lib/libstdc++.so.5

```

did a apt-get dist-upgrade rebooted but did not solved my problem.
So what should I do or check now ?

---

### Post by sh1ny on 2010-07-02
Are you sure you need the EE SDK ? Or just the runtime ?

The link for the java doesn't work here, what did you choose from this link : 

[http://java.sun.com/products/archive/](http://java.sun.com/products/archive/)

I want to try to reproduce this on my pc.

---

### Post by tapas_mishra on 2010-07-02
I am using a Learning Management System known as Sakai to install the requirements are given here
[http://confluence.sakaiproject.org/display/DOC/Install+Guide+-+Binary+Install+(2.6)]("http://confluence.sakaiproject.org/display/DOC/Install+Guide+-+Binary+Install+(2.6)")
so which on the link you gave is for me ?
I am using Ubuntu 10.04 server edition

---

### Post by sh1ny on 2010-07-02
JDK/JRE - 5.0

Just click the "GO" button . It should get you to download 5.0.22.

EDIT : Download the JDK release.
EDIT2 : Make sure you download the appropriate arch - if you installed 32bit ubuntu server use the "Linux" option to download, if you're running a 64bit Ubuntu - select the "Linux x64" option before starting the download. 

This is the exact file you want :

 jdk-1_5_0_22-linux-amd64.bin

---

### Post by sh1ny on 2010-07-02
On a side note - Sakai 2.7 runs on java 6 ? Why not use that instead ?

---

