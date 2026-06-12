---
title: "Files from HDD in VM"
date: 2009-03-15
forum: Virtualisation
---

### Post by velja27 on 2009-03-15
Is there a way to use/transfer files from hdd in VirtualBox?

---

### Post by HermanAB on 2009-03-15
Virtualbox has a way to share a host folder with a guest.  However, since that can be hard to get going, I usually use SSH or FTP instead.  

For FTP, install proftp on Linux and FileZilla on Windows.

For SSH, install ssh-server on Linux and FileZilla on Windows.

You can also use NFS and the Microfot Sevices for Unix (NFS) is a free download form Microsoft: 
[http://www.microsoft.com/DownLoads/details.aspx?familyid=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en](http://www.microsoft.com/DownLoads/details.aspx?familyid=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en)

[http://www.aeronetworks.ca/nfs-howto.html](http://www.aeronetworks.ca/nfs-howto.html)

Cheers,

Herman

---

### Post by velja27 on 2009-03-15
Thanks HermanAB,can i use FileZilla instead of proftp?

---

