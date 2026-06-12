---
title: "Starting and accessing a cloud image"
date: 2018-02-01
forum: Virtualisation
---

### Post by jamapii on 2018-02-01
Hello,

how can I start and access a running cloud image? (With qemu on a recent non-Ubuntu box, but installed cloud-image-utils 0.27 and genisoimage)

All the blog posts on the internet from 2012-2017 seem completely bogus in various ways. Maybe the syntax and tools change frequently?

One post suggests to create a my-seed.img file and start it with

qemu -hda cloudimg.img -hdb my-seed.img

The only problem, it really is always just an ISO file. And it contains just a literal copy of the #cloud-config file.

I can start the VM with -hda cloudimg.img and -cdrom my-seed.iso, it starts and gives me a login prompt. Also ssh is running.

However, the cloud-config file is always completely ignored, at least no login is ever possible in any way. No matter the content of this file.

Each example or documentation demonstrates a different syntax, with different keywords and different spellings, sometimes "_" and sometimes "-". One is unique in having a plain_text_passwd. One uses a line "chpasswd: { expire: False }". Many others have a syntax with a "users:" category, <indent>"-", name, password (hashed), and a lot of fields that might look like there is a system to it, but seems rather arbitrary on second glance. 

How can I find out if the file is evaluated at all, or if there is a small syntax error that causes it to be ignored?

---

