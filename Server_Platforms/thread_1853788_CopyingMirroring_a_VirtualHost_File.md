---
title: "Copying/Mirroring a VirtualHost File"
date: 2011-10-03
forum: Server Platforms
---

### Post by tts5 on 2011-10-03
We currently operate multiple LAMP servers (clustered) and have several VirtualHosts. Right now, we host Apache's /etc/apache2/sites-available directory on an NFS server and have each web server mount that directory on boot (to both sites-available and sites-enabled).

The net effect is that any configuration settings added in sites-available become immediately enabled (no need for a2ensite).

Is there a better/more semantic way to handle this? We don't want to have to SCP the file between servers (SPOF). Currently, our NFS server is dual-redundant. Is that the best bet?

---

### Post by SeijiSensei on 2011-10-03
I'm not sure I understand what the problem is.  Are you worried about what happens if the NFS server goes offline?

How about a script running in cron that checks for the existence of the main server every minute?  If it's gone, have the script mount the backup.  

Maybe something from the [Linux-HA project]("http://www.linux-ha.org/doc/users-guide/users-guide.html") might be useful?

---

### Post by tts5 on 2011-10-03
> **SeijiSensei said:**
> I'm not sure I understand what the problem is.  Are you worried about what happens if the NFS server goes offline?

How about a script running in cron that checks for the existence of the main server every minute?  If it's gone, have the script mount the backup.  

Maybe something from the [Linux-HA project]("http://www.linux-ha.org/doc/users-guide/users-guide.html") might be useful?

Like your idea about using a cron script. I guess my question is whether mounting the Apache VirtualHost scripts via NFS is the best way to do it.

---

### Post by Ryan Dwyer on 2011-10-03
There's a few ways you could do this.

One would be to run rsync on a 1 minute cron. However, this means every server in the cluster has to answer the rsync request every minute which isn't ideal. This does have the benefit of being centrally managed though.

Another solution would be to change the Apache start function (in /etc/init.d/apache2 or wherever it lives these days) so it rsync/SCPs the file from your master server before starting the daemon. You would want to make sure that the cluster's vhost files don't get changed if there are connectivity issues to the master though. You could set this up for the reload function too.

---

### Post by SeijiSensei on 2011-10-03
Another option is to drop the NFS mount from time to time and copy the files to the underlying directory with rsync.  Remember that if you mount a remote share on top of /var/www, any files already existing in that directory are simply unavailable, not destroyed.  So if the client's /var/www is an up-to-date snapshot of the server's /var/www, a failure by the NFS server simply exposes the underlying directory's files to the operating system.

---

