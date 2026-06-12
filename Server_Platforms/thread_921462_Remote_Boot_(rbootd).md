---
title: "Remote Boot (rbootd)"
date: 2008-09-16
forum: Server Platforms
---

### Post by Vegan on 2008-09-16
My Old IBM that I am using has the ability like most machines, to be booted from a network. So I was wondering if there is a way to boot from my Linux box to be able to load Windows Setup or Linux as needed.

I saw a page for rbootd but little for Ubuntu.

---

### Post by promodus on 2008-09-16
Yes.

[www.promodus.net/linuxris ]("http://www.promodus.net/linuxris")
Sorry the google apps page ruined the css, I'll try to fix that this evening.

---

### Post by Vegan on 2008-09-16
Any thing easy to deploy, I already have a Windows disk image for unattended setup, and wanted a Linux disk to be the same, for bulk installs.

---

### Post by promodus on 2008-09-16
if you have an image already, use partimage and partimaged (the former being the client, the later being the server daemon)

---

