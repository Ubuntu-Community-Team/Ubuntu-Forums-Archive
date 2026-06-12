---
title: "accessing shared xp folders from command line"
date: 2008-04-05
forum: Security Discussions
---

### Post by samona on 2008-04-05
```
sudo mount -t ntfs -o username=mike,password=**** //192.168.1.102/music /mnt/win
```

Hi all,

I need help in trying to access a shared folder on Windows XP from the command line.  When i type the above code I get a

```
Failed to access '//192.168.1.102/music': No such file or directory
```

Any help will be greatly appreciated.  Thanks!

---

### Post by p_quarles on 2008-04-05
In order to access files across a network, you will need to use a networking protocol of some sort. This is true of any type of filesystem, including NTFS. The protocol for networking Windows and *nix machines is Samba.

---

### Post by samona on 2008-04-05
You don't need Samba to access a shared file on a Windows machine, but you do need Samba to access a linux shared folder from a windows machine.  

Also, I can access the shared folder using the GUI.  I just want to know how to do it using the command line for security purposes.

---

### Post by HermanAB on 2008-04-06
Read up on samba and smbclient.

For example: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

### Post by pseudo-random on 2008-04-06
You need** smbfs**. Search the fourms for a tut.

---

### Post by HermanAB on 2008-04-06
Smbfs is deprecated.  The new one is cifs.

---

