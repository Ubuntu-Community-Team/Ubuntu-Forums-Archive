---
title: "Ubuntu Server 10.10 vs 10.04"
date: 2010-09-15
forum: Server Platforms
---

### Post by AmrineA on 2010-09-15
I need to create at least one Ubuntu server, and possibly more in the future. What I'm wondering is if I should create it using 10.10 when it comes out or use 10.04 since it has LTS. Are there any new feature in 10.10 that could be worth taking advantage of for a server? The first server will be used for an SFTP server.

---

### Post by CharlesA on 2010-09-15
I'd stick with 10.04, since it's LTS.

That's what I am doing. 

I haven't really kept up with 10.10, but you could just stick with 10.04 unless something doesn't work with it.

---

### Post by Bachstelze on 2010-09-15
Maverick has OpenSSH 5.5, which brings some [new]("http://openssh.org/txt/release-5.4") [features]("http://openssh.org/txt/release-5.5") over the version in Lucid (5.3). Read through them and see if there's something you want, otherwise you can stay with Lucid.

---

### Post by CharlesA on 2010-09-15
Hrm. I wonder if it's possible to add that version of OpenSSH to Lucid.

---

### Post by Bachstelze on 2010-09-15
> **CharlesA said:**
> Hrm. I wonder if it's possible to add that version of OpenSSH to Lucid.

It is certainly possible to backport it or install it from the Maverick repos, but it will make it harder to track bug fixes.

---

### Post by CharlesA on 2010-09-15
> **Bachstelze said:**
> It is certainly possible to backport it or install it from the Maverick repos, but it will make it harder to track bug fixes.

Figured as much. :)

I'll just stick with 5.3.

---

