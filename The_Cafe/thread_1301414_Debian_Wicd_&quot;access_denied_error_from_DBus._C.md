---
title: "Debian: Wicd &quot;access denied error from DBus. Check your user is in netdev group&quot;"
date: 2009-10-26
forum: The Cafe
---

### Post by hanzj on 2009-10-26
Hello,
My main desktop comp uses Ubuntu, but I use Debian on my netbook.


I've just done

```
sudo apt-get update && sudo apt-get upgrade
```
.

and when I restarted my computer (debian version 5.0) I get this message:


> WICD
Unable to contact the Wicd daemon due to an access denied error from DBus. Please check that your user is in the **netdev** group.


Wicd is my wireless connection program. I think what happened when i ran apt-get upgrade is that the wicd got updated to the latest (1.6.2.2) version.

How can I fix this? Thank you.

---

### Post by Icehuck on 2009-10-26
> **hanzj said:**
> Hello,
My main desktop comp uses Ubuntu, but I use Debian on my netbook.


I've just done

```
sudo apt-get update && sudo apt-get upgrade
```
.

and when I restarted my computer (debian version 5.0) I get this message:





Wicd is my wireless connection program. I think what happened when i ran apt-get upgrade is that the wicd got updated to the latest (1.6.2.2) version.

How can I fix this? Thank you.

Are you a part of the netdev group? If not try adding yourself to it?

---

### Post by cariboo on 2009-10-26
TO find out what groups your user is a member of, open a terminal and type 

```
groups
```

To add yourself to a group type:

```
sudo gpasswd -a <username> netdev
```

---

### Post by hanzj on 2009-10-26
cariboo907,
thank you.
I did 
```
groups
``` but did not see my username (the username I used to log onto the debian netbook.
But I knew what it was and did
> sudo gpasswd -a <username> netdev.

I then did 
> wicd-client and it works A-OK!


Thank you, my fellow Ubuntu user, for helping me with this question re: my debian comp.
8-) 8-)

---

