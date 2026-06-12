---
title: "[SOLVED] Networking in VMware Player"
date: 2008-06-23
forum: Virtualisation
---

### Post by msayed2004 on 2008-06-23
I want to use Win XP over VMWare **Player** to [use Nokia PC suite]("http://ubuntuforums.org/showpost.php?p=2671579&postcount=15") ([Virtualbox can't]("http://www.virtualbox.org/ticket/470") & [I found no Linux applications to do the job]("http://ubuntuforums.org/showthread.php?t=688472")).

I installed VMWare Player using the TAR.GZ package following [this topic]("http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710").
I created the machine using [this site]("http://www.easyvmx.com/").
XP installation was slow but successful.
I asked a friend to upload VMWare tools for me & I installed it.

Now I can't connect that Virtual Machine to the web & I can't [share]("http://ubuntuforums.org/showthread.php?t=296668") anything too as the Virtual Ethernet device need a driver & VMWare tools did nothing regarding this !

Any Ideas ?

Thanks.
---
VMWare Player version : 2.0.4 build-93057
VMWare tools version : 7.2.9, build-80004
Guest OS : Win XP Pro SP3

---

### Post by linux6994 on 2008-06-23
From within windows you need to be on the same workgroup as the host pc via samba/smbfs. While the virtual XP is up you should see via Places > Network your virtual machine. You will need to share your Documents in XP also. You will also need to share a folder in Ubuntu. When sharing is working you should also add the printer from XP looking to your Ubuntu.

---

### Post by linux6994 on 2008-06-23
The NIC card driver should be pro2kxp.exe search for it, put it to a cd and install it in your xp.

---

### Post by msayed2004 on 2008-06-23
Thanks for your reply :)> **linux6994 said:**
> From within windows you need to be on the same workgroup as the host pc via samba/smbfs. While the virtual XP is up you should see via Places > Network your virtual machine. You will need to share your Documents in XP also. You will also need to share a folder in Ubuntu. When sharing is working you should also add the printer from XP looking to your Ubuntu.This should be done only after finding a driver.> **linux6994 said:**
> The NIC card driver should be pro2kxp.exe search for it, put it to a cd and install it in your xp.can't find it in that windows.iso file, maybe it is an old one.

---
Is it large in size (I am talking about the driver named pro2kxp.exe) ?
If no can somebody upload it ?
If yes what can I do ?

---

### Post by linux6994 on 2008-06-23
Sorry it can be found here:

[http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=PRO2KXP.EXE&page_nbr=2&lang=eng](http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=PRO2KXP.EXE&page_nbr=2&lang=eng)

---

### Post by msayed2004 on 2008-06-24
Strange driver* but did the job, thanks linux6994 :).


*At the end of the installation the whole VMWare crashed (twice) & after restarting it keyboard related troubles occurred but resolved by restarting the whole PC!

---

