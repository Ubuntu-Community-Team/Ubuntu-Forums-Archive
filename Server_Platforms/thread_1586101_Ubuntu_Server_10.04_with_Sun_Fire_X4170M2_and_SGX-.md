---
title: "Ubuntu Server 10.04 with Sun Fire X4170M2 and SGX-SAS6-R-INT-Z RAID"
date: 2010-10-01
forum: Server Platforms
---

### Post by jeremyrandall on 2010-10-01
Hi all,

I'm looking to use Ubuntu Server 10.04 on a Sun Fire X4170M2 server with a Sun RAID card; the RAID card part number SGX-SAS6-R-INT-Z.

Could anyone help me find out if this RAID controller is supported by 10.04 Server?

Thanks,

Jeremy

---

### Post by the_original_billq on 2010-10-01
> **jeremyrandall said:**
> Hi all,

I'm looking to use Ubuntu Server 10.04 on a Sun Fire X4170M2 server with a Sun RAID card; the RAID card part number SGX-SAS6-R-INT-Z.

Could anyone help me find out if this RAID controller is supported by 10.04 Server?

Thanks,

Jeremy

I believe that's an LSI RAID controller.

Boot live, and look at /proc/mdstat.  If it's there, lucid knows what it is...


[EDIT]
I just found this, though it looks like RHEL and SuSE are the only Linux games in town 8-|

[http://www.lsi.com/support/sun/sg_x_sas6-r-int-z.html](http://www.lsi.com/support/sun/sg_x_sas6-r-int-z.html)
[/EDIT]

-Bill

---

### Post by jeremyrandall on 2010-10-01
Thanks.  I haven't actually purchased the server yet; trying to find out ahead of time how well it will work.  The Sun guys can only really give information about Solaris and Oracle Linux, so hopefully someone out there has tried this.

---

