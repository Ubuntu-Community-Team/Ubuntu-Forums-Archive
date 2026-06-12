---
title: "Need help setting up kino"
date: 2006-02-02
forum: The Cafe
---

### Post by drmcclure on 2006-02-02
How do get around the raw1394 permission and loading problem when try to run Kino?  Thanks

---

### Post by eeclark on 2006-02-02
put yourself in the Disks group and also in the Video group (although you might already be in that one)
This has to do with udev (i think)

It worked for me.

You might want to try Main Actor too.  (it costs but you can use the demo for free)

---

### Post by drmcclure on 2006-02-02
[QUOTE=eeclark]put yourself in the Disks group and also in the Video group (although you might already be in that one)
This has to do with udev (i think)

It worked for me.

You might want to try Main Actor too.  (it costs but you can use the demo for free)[/QUOTE]
how do I put myself in both groups?  I've changed the group in my permissions file from disk to video.

---

### Post by eeclark on 2006-02-02
system-->administration-->users and groups
click on the groups tab
check the Show all users and groups checkbox
select group header (to sort by alpha)
select disk
select properties
select member
select Add

---

