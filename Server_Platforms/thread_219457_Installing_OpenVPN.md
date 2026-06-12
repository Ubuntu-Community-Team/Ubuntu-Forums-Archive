---
title: "Installing OpenVPN"
date: 2006-07-20
forum: Server Platforms
---

### Post by Diwil on 2006-07-20
Hello, I just started using Ubuntu Linux (dapper) for the first time, and I should install OpenVPN for work purposes.

However, after googling for it, websites pointed me to using apt-get for installation. My apt-get can't seem to find openvpn when I try. Are there some source lists I need to update or add or how should I go about this? I'd rather not install it through the tarball, since in a case of dependancies and uninstallation I'd be pretty helpless.

I tried "apt-get update", but still no result. Any input on this matter would be highly appreciated. Thanx.

---

### Post by Beatinu on 2006-07-20
The OpenVPN package is in the universe repository. You need to uncomment a line in /etc/apt/sources.list to use this repository. 
Try "aptitude update" and "aptitude install openvpn" after you have uncommented the appropriate line.

---

### Post by Diwil on 2006-07-20
Thanx, it worked!

---

