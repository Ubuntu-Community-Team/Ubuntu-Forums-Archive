---
title: "Linux-iscsi.org on 9.04 Server"
date: 2009-05-31
forum: Server Platforms
---

### Post by reactive on 2009-05-31
I'm currently using the Enterprise iSCSI target from the standard rep's to host iSCSI targets for a Windows 2003/2008 cluster. I want to be able to achieve a failover file server using Server 2008 and iSCSI but the enterprise target doesn't support persistant reservations required for clustered disks in 2008.

According to linux-iscsi.org they support everything I need but I have no idea how to install this on ubuntu and their documentation isn't really helpful. 

Can anyone offer any advice on how I could get this working?

Thanks
-Matt

---

### Post by windependence on 2009-05-31
Take a look at [FreeNAS]("http://www.freenas.org/"). It's BSD based, but IMHO that is actually better.

-Tim

---

### Post by reactive on 2009-05-31
To use an iSCSI clustered disk in Server 2008 the target needs to support SCSI-3 reservations. Anything based on the enterprise iSCSI target won't work.

See here -
[http://up2v.wordpress.com/2009/05/08/iscsi-software-targets-for-windows-server-2008-clustering/](http://up2v.wordpress.com/2009/05/08/iscsi-software-targets-for-windows-server-2008-clustering/)

The linux-iSCSI target says it fully supports the SCSI-3 reservations... I just need to figure out how to set it up.

---

### Post by srinivasank on 2010-06-02
Can you please outline the steps to setup Linux-iscsi if you were able to?

Thanks,
sk

---

### Post by flickerfly on 2010-12-28
I'm also interested in seeing if this is workable.

---

