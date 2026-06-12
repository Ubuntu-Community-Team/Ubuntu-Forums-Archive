---
title: "Best way to upload files to web server from windows"
date: 2009-10-14
forum: Server Platforms
---

### Post by shlumph on 2009-10-14
Hi,

I'm real new to Ubuntu, and Linux in general. I'd like to set up a dedicated web server using Ubuntu Server.

My question is, generally, what's the best way to move project files from my development machine (Windows Vista) to the Ubuntu Server? They are in the same LAN.

Should I use PuTTY and move the files via SSH? Should I set up FTP? What's the best way to do things?


Thanks.

---

### Post by Kolipoki on 2009-10-14
Try WinSCP.

---

### Post by karlson on 2009-10-14
> **shlumph said:**
> Hi,

I'm real new to Ubuntu, and Linux in general. I'd like to set up a dedicated web server using Ubuntu Server.

My question is, generally, what's the best way to move project files from my development machine (Windows Vista) to the Ubuntu Server? They are in the same LAN.

Should I use PuTTY and move the files via SSH? Should I set up FTP? What's the best way to do things?


Thanks.

Whichever better suits your fancy.:P

PuTTY's pscp, WinSCP will work.  For FTP you might need to configure the FTP server on your machine.

---

### Post by shlumph on 2009-10-14
Sweet, - I just tried out WinSCP and it worked flawlessly. Thanks.

---

