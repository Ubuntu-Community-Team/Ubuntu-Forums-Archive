---
title: "How to check folder size from terminal?"
date: 2006-06-11
forum: Server Platforms
---

### Post by skafiskafnjak on 2006-06-11
How can I check folder size from command line and how to check free available space on whole drive?

Thanks

---

### Post by dermotti on 2006-06-11
df -h

du -h

---

### Post by FizDev on 2006-06-11
For the folder size, I don't know, but for the total free space, type
```
df
```

---

### Post by dermotti on 2006-06-11
**df -h** is better imho :-)

---

### Post by FizDev on 2006-06-11
I've just found for the folder size, type :
```
du foldername
```
;)

Edit : Doh! Just found out that dermotti was faster =(

---

