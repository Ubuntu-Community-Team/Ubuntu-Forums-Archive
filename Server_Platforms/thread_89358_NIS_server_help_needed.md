---
title: "NIS server help needed"
date: 2005-11-12
forum: Server Platforms
---

### Post by sparhawk on 2005-11-12
I work in the systems intergration department of my company and I had all of the technicians switch to ubuntu and so far I have loved it. Problem is we are a Microsoft partner so have some Microsoft systems still running. Until I convince my bosses that we should switch completely to open source we must put up with a mixed enviroment. I have decided to set up services for Unix on the windows servers and want AD to sync with the Linux users and groups. I think the best way to do this is through NFS and NIS. I was woundering if there is a NIS server primer or config guide out there for ubuntu. I think I have it configured right on my MS DC's but my linux box is another story... I am not even quite sure where to start. Any help would be welcome and if anyone thinks nfs and nis is not the way to go I would love to hear alternatives and why they think so.

Thanks,

One voice among millions for Linux

---

### Post by unixnorks on 2005-11-12
> I have decided to set up services for Unix on the windows servers and want AD to sync with the Linux users and groups.

NIS are obsolete and insecure, try use LDAP but it takes a lot of effort to configure.. Well i believe to the wisdom that, good things deserved good price.. :)

---

### Post by sparhawk on 2005-11-12
[QUOTE=unixnorks]NIS are obsolete and insecure, try use LDAP but it takes a lot of effort to configure.. Well i believe to the wisdom that, good things deserved good price.. :)[/QUOTE]


OK then... Any guide online for setting up ldap to sync with my linux boxes?

---

### Post by sparhawk on 2005-11-12
OK so I have now found articles to set up Ldap and also some with a Samba/winbind solution... anyone know of any reason I should try the one over the other to authenticate to AD?

---

### Post by unixnorks on 2005-11-14
> OK so I have now found articles to set up Ldap and also some with a Samba/winbind solution... anyone know of any reason I should try the one over the other to authenticate to AD?

doesnt matter at all... but if you are not so sure of what you are going to do have a trip to this site

[http://www.acay.com.au/~oscarp/tutor/](http://www.acay.com.au/~oscarp/tutor/)

---

