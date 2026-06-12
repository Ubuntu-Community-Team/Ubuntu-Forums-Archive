---
title: "Trying to get permissions to ICAClient folder"
date: 2010-06-02
forum: Security
---

### Post by dhoenisch on 2010-06-02
Hi all, I am killing my brain here trying to figure this out.  I am an admin on my Ubuntu 10.04 machine, and I am trying to copy a certificate to my /usr/lib/ICAClient folder, per another post on getting Citrix to work, but I am denied access.  I tried giving myself full access to the /usr folder by using the command sudo chown username /usr -R, and it seems to have given me full access to everything except the /ICAClent folder.  Can anyone shed some light on this for me please?

Thanks,
Dan

----- EDIT  -----

Never mind, I figured it out.  After I did the above, I had to right-click on that folder, go to properties, and assign read and write rights to that folder.  Weird that I didn't have to do that for any other folder but that one.

---

