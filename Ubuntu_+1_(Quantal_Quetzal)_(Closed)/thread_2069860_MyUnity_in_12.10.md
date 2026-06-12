---
title: "MyUnity in 12.10"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Keshav2050 on 2012-10-11
I've recently upgraded to ubuntu 12.10 and tried to install MyUnity, but followed the steps for 11.10. Since then I'm getting an error when I type 'sudo apt-get update' as:


[B]W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found[/B]

what should I do to remove those errors? I even didn't know how to install MyUnity in 12.04.

---

### Post by nothingspecial on 2012-10-11
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by Warprunner on 2012-10-11
> **Keshav2050 said:**
> I've recently upgraded to ubuntu 12.10 and tried to install MyUnity, but followed the steps for 11.10. Since then I'm getting an error when I type 'sudo apt-get update' as:


[B]W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found[/B]

what should I do to remove those errors? I even didn't know how to install MyUnity in 12.04.

So you tried to install ver 11 over the top of 12?

---

### Post by cariboo on 2012-10-11
Myunity has been removed form the repositories, because it is broken. Once the author comes up with a new version, it should be available. 

Hopefully, it won't be dependent on gambas any more.

---

### Post by Keshav2050 on 2012-10-12
But how to remove the errors? Or undo what I have done.

---

### Post by philinux on 2012-10-12
> **Keshav2050 said:**
> But how to remove the errors? Or undo what I have done.

Remove the ppa's from Software Sources.

---

### Post by Keshav2050 on 2012-10-12
Thanks, I removed them from the software sources of Ubuntu Software Center.

---

