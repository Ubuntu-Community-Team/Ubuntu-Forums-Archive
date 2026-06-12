---
title: "Ubuntu Pro - packages download only, not install"
date: 2024-03-27
forum: Server Platforms
---

### Post by ecrosby on 2024-03-27
When using Ubuntu Pro licensing, is there still an option to just download updates without installing([I]apt-get install --download-only)?
[/I]The reason I ask is because I have a number of servers that have no connection at all to the internet and I would like the ability to just download all available packages to a machine, put them on a thumb drive (security scanned, of course), make it available on another server for all my servers to copy over and then just run a *dpkg -i *.deb* on that offline server to offline install all the packages in that folder containing the downloaded packages.

---

### Post by Xian on 2024-03-27
Where does this get you?

apt-get upgrade --download-only

---

### Post by ecrosby on 2024-03-28
> **Xian said:**
> Where does this get you?

apt-get upgrade --download-only

I'll try that. But, does that also include all required dependencies?

---

### Post by #&amp;thj^% on 2024-03-28
> **ecrosby said:**
> But, does that also include all required dependencies?

It will if you use apt  or aptitude to install them. It's the tool you use when installing them that pulls in any dependencies.

---

### Post by LHammonds on 2024-03-29
Total guess here but can you create a repository server, update it and then carry it around to your various locations and have your offsite servers pull from it?  Assuming the offsite area has a LAN you can plug into.

---

