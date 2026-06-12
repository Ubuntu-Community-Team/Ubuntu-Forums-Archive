---
title: "UEC image management"
date: 2011-04-28
forum: Ubuntu Cloud and Juju
---

### Post by shahin on 2011-04-28
Greetings-
   From looking at [http://open.eucalyptus.com/wiki/EucalyptusImageManagement_v1.6]("http://open.eucalyptus.com/wiki/EucalyptusImageManagement_v1.6")I see the following comment: “Note that all users may upload and register images (depending on access granted to them by the Eucalyptus administrator), but only the admin user may ever upload/register kernels or ramdisks.” Does this mean that I have to be in root mode before I can upload and register images? I tried to do this by first issuing the command sudo -i, but then all of my environment variables in eucarc file no longer exist, and I can not even source the file again in root mode.  How do I make sure I have the right permissions and the environment variables to use Euca2ools?

---

### Post by kim0 on 2011-05-03
Hi there
Note that "admin" does not mean "root" on the local machine. It means that when you create a user using the Eucalyptus web interface, you mark that user as admin in the web UI afaik

---

