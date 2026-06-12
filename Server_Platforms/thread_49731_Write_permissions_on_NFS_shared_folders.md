---
title: "Write permissions on NFS shared folders"
date: 2005-07-17
forum: Server Platforms
---

### Post by robojamie on 2005-07-17
I'm wanting to share my home folder with a Mac OS X client on my home network. This is what I have in my /etc/exports:

[FONT=Courier New]/home/robojamie *(async,rw)[/FONT]

I'm mounting the share with this command: 

[FONT=Courier New]sudo mount -o -P 192.168.0.1:/home/robojamie  /Users/robojamie/linux[/FONT]

I don't have write permissions on the folder. I thought the rw option in /etc/exports would give me write permission. What else do I need to do to get write permission?

---

### Post by emperor on 2005-07-17
You will need to have the same numerical UID on both machines. Do they match?

Not sure why the -o (options) is specified when no options are specified!

---

### Post by robojamie on 2005-07-17
Thank you! I got it to work... I had to do a little reading on UID's though

---

