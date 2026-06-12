---
title: "file server OS only"
date: 2008-07-20
forum: Server Platforms
---

### Post by fast eddie on 2008-07-20
Can someone recommend the best (limited Linux knowledge) Linux OS for a file server for home use?

I have set up a CC server for my music and would like to have another machine set up so I can back up my music and also use as a file server.

I am just looking for a file server and not a web/email/print server at the moment so any suggestions would be welcome although it would be nice to be able to ftp into it from another machine via the internet.

Many thanks for your time and patience,

---

### Post by windependence on 2008-07-20
You can set up Ubuntu server on a headless box and just load OpenSSH and SAMBA on the box. That's all you'll need. The box will talk to Windoze, Linux, and Mac boxes. If you are doing music, you might have a Mac. It works great on my Macbook pro.

For backup, you could try Amanda or Bacula, and they can automatically backup all the machines on your network.

-Tim

---

### Post by hyper_ch on 2008-07-20
I like debian as server

---

### Post by windependence on 2008-07-20
I agree, debian Etch is great also, as well as FreeBSD.

-Tim

---

