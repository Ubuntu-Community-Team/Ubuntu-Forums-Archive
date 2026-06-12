---
title: "Can I mount ext3 partitions with samba?"
date: 2008-06-01
forum: Server Platforms
---

### Post by Twizzle on 2008-06-01
I have Samba running as I have an NTFS drive in a server I share with a windows machine. I would also like /var/www from the server automounted in my desktop machine when I start it up.

Can I do the same as I did with the NTFS partition and add the necessary line to fstab. I have seen people talk about NFS instead but can I do both at once and what will be better?

---

### Post by conjur3r on 2008-06-01
It doesn't matter what the file system type is for samba to share it. All you need to do is create a new samba share for /var/www in your case. Nfs is ideal in an environment where sharing is required by *nix boxes. You can have both samba and nfs running at the same time if you so choose but the easiest option for you is toadd another share to samba.

---

### Post by Twizzle on 2008-06-01
Thankyou. I have now done that but keep running into a small problem. My /www share appears to be locked. I have

```
 sudo chmod -R 777 /var/www 
```

on the server which seems to sort it but if I try to drop a folder into the /www share I get error messages. It will create the folder but automatically lock it!

Is there any way to prevent this?

---

### Post by Prospero2006 on 2008-06-01
The profile entry for /var/www in /etc/samba/smb.conf
can be modified for read only or read-write based on which
user is logged in. 

Have you checked this file over carefully?

---

### Post by Twizzle on 2008-06-01
Right at the bottom of smb.conf is:

```
 [www]
             revalidate = yes
             user = john
             create mode = 777
             path = /var/www
             directory mode = 777 
```

I am using a mix of webmin and ssh to setup my server, and this part was done through webmin.

---

### Post by conjur3r on 2008-06-02
Try adding

writable = yes

underneath the directory mode statement you have.  Restart Samba for changes to occur.

---

### Post by Twizzle on 2008-06-02
Still does not work im afraid.

Thanks for the help though

---

