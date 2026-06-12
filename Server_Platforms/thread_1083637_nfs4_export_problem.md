---
title: "nfs4 export problem"
date: 2009-03-01
forum: Server Platforms
---

### Post by feurio4you on 2009-03-01
Hello,

I have a working nfs4 environment incl. kerberos.

The only problem that remains is that if a user (e.g. www-data) creates a new file on a mounted share the owner and the group of the file are nobody:nogroup instead of www-data:www-data.

What I want is that the file is owned by www-data... How can I accomplish my goal?

my /etc/exports nfs-server: 
/export/my_exported_folder gss/krb5p(rw,async,wdelay,root_squash,no_subtree_check)

my /etc/fstab on the client:
my.client:/my_exported_folder /my/mounted/folder nfs4 rw,hard,intr,proto=tcp,port=2049,sec=krb5p 0 0


Thanks for your help!

---

### Post by HermanAB on 2009-03-01
You need to use user_squash (or all_squash) and then specify a user and group id. Some googling for user_squash will get you going: [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

Here are some more:
[http://www.troubleshooters.com/linux/nfs.htm](http://www.troubleshooters.com/linux/nfs.htm)
[http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-nfs-security.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-nfs-security.html)

Cheers,

Herman

---

