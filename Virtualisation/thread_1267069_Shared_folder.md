---
title: "Shared folder"
date: 2009-09-15
forum: Virtualisation
---

### Post by HalfCrackedTech on 2009-09-15
How can I access information in share folder?

---

### Post by amac777 on 2009-09-15
You might need to explain more about what kind of a shared folder it is. But take a look at Places->Connect to Server first too. You can select the service type there and that includes Windows share and FTP folders which are pretty common. 

Another way is you can also access windows and ftp shares in nautilus directly by typing in the address box:

smb://server-name
[ftp://server-name](ftp://server-name)

---

### Post by HalfCrackedTech on 2009-09-15
I am talking about the shared folder in VB.  How do I gain access to the folder I assign?

---

### Post by falconindy on 2009-09-15
You can map it from the command line:
```
net use x: \\VBOXSVR\share-name /persistent:yes
```
Or you can navigate to it via Explorer -> Entire Network -> VirtualBox Shared Folders.

---

