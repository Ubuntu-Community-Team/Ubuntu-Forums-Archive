---
title: "working with files in etc cp no stat"
date: 2008-07-14
forum: Server Platforms
---

### Post by bucksquare on 2008-07-14
now i want to configure the server components found instructions flurdy.comdocs/postfix
asks to cp file to etc can't do it 

thanks

---

### Post by windependence on 2008-07-14
Can you post the error you are getting?

Try using sudo cp.

-Tim

---

### Post by bucksquare on 2008-07-14
$ cp /usr/share/doc/shorewall-common/default-config/interfaces /etc/shorewall/
cp: cannot create regular file `/etc/shorewall/interfaces': Permission denied


i tried to add  file to etc/shorewall can't no permissions
i tried to move a file i created and saved to desktop can't no premissions

is there drop n drag files like the mac

thanks

---

### Post by jpkotta on 2008-07-15
/etc is where settings for the whole system go.  Since they affect everything, not all users can modify them.  You have to use sudo to gain the priviledges necessary to write there.

```

cd /etc/shorewal
sudo cp interfaces interfaces.bck # backup the original
sudo cp /usr/share/doc/shorewall-common/default-config/interfaces .

```

---

