---
title: "Share folder over internet"
date: 2009-11-30
forum: Server Platforms
---

### Post by boyofford on 2009-11-30
Hi, 

Not sure what I need to do to enable this, but want to create a folder on my computer that I can take files from and add files to over the internet, what are my options? I want it to be as secure as possible.
Don't need to remotely control the computer though.

Using ubuntu juanty desktop version.

Thanks all!!!
Rich

---

### Post by pi4r0n on 2009-11-30
> **boyofford said:**
> Hi, 
 
Not sure what I need to do to enable this, but want to create a folder on my computer that I can take files from and add files to over the internet, what are my options? I want it to be as secure as possible.
Don't need to remotely control the computer though.
 
Using ubuntu juanty desktop version.
 
Thanks all!!!
Rich
 
[**Ubuntu ONE**]("https://one.ubuntu.com/") might be the best option for you.

---

### Post by BkkBonanza on 2009-11-30
I think Ubuntu One will work as long as you plan to access from Ubuntu. If you want more general access (ie. from Windows machines or Apple) then Dropbox may suit you better. I haven't used Ubuntu One - maybe it allows web browser access as well and if that works for you then you could use it anywhere. I do know that Dropbox uses SSL and encrypts data on their server and does support web browser access (using a password). 

However, either of these options works by copying your files to their server. If you want just direct access then use an sftp (secure ftp) client. It can access your server as long as you have sshd running (OpenSSH daemon, available in Synaptics but not installed by default). You would need to take care to secure that - there are several posts here to help with that. Running ssh is secure but will be more hassle to setup than a solution like Ubuntu One or Dropbox.

---

### Post by boyofford on 2009-12-02
Cheers for heads up on dropbox, that will suit me for now, easy to setup too! did look at ubuntu one, but as i was working on a xp comp at work at time dropbox suited me.
Plus like the way you can direct link to files and send to others for download, very handy as 2gb storage.

Thanks again!

---

