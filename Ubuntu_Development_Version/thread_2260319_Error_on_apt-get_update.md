---
title: "Error on apt-get update"
date: 2015-01-10
forum: Ubuntu Development Version
---

### Post by cprofitt on 2015-01-10
I am getting some errors when running apt-get update:

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) vivid/main Sources
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) vivid/main amd64 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) vivid/main i386 Packages
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

----
Not sure if this is normal or not, but thought I would ask.

---

### Post by cariboo on 2015-01-10
The error you're seeing is normal at this stage in development, just comment out the extras repositories in /etc/apt/sources.list, and you won't see the error again.

---

### Post by zika on 2015-01-11
> **cariboo907 said:**
> The error you're seeing is normal at this stage in development, just comment out the extras repositories in /etc/apt/sources.list, and you won't see the error again.Or, as we do for years, use extras for U instead for U+1...

---

### Post by Elfy on 2015-01-13
This shouldn't happen in future.

[lpbug]1409555[/lpbug]

[https://lists.ubuntu.com/archives/technical-board/2015-January/002063.html](https://lists.ubuntu.com/archives/technical-board/2015-January/002063.html)

---

### Post by Ko_Char on 2015-01-13
It feels like failed effort for app showdown. 
Most apps were not even updated for the next version.

---

### Post by grahammechanical on 2015-01-14
> **Ko_Char said:**
> It feels like failed effort for app showdown. 
Most apps were not even updated for the next version.

I have no idea what you are talking about. Your comments certainly do not fit the title of this thread.

The most recent showdown I heard about was a Scopes showdown. I know the competition is now closed but the entries are still being judged. I have heard that quality is very good.

---

### Post by kansasnoob on 2015-01-15
> **Elfy said:**
> This shouldn't happen in future.

[lpbug]1409555[/lpbug]

[https://lists.ubuntu.com/archives/technical-board/2015-January/002063.html](https://lists.ubuntu.com/archives/technical-board/2015-January/002063.html)

Thanks for the info :D

---

