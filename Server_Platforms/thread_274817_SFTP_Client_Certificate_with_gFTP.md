---
title: "SFTP Client Certificate with gFTP"
date: 2006-10-10
forum: Server Platforms
---

### Post by justmoon on 2006-10-10
I have my server set up so it identifies the SSH client via a client certificate. On the client side I've only recently switched to Linux, before I was using Putty and Filezilla under Windows.

Putty was easy to setup under Ubuntu Dapper and works just fine. As I prefer native apps I thought I'd try gFTP instead of running Filezilla under WINE.

So how can I get gFTP to recognize my key file? I figure it would be easiest to use Putty as it's SSH2 backend, but I can't find a HOWTO on that anywhere.

Can anyone point me in the right direction, please?

---

### Post by justmoon on 2006-10-10
Nevermind. I got it.

For everyone else with the same problem:

I followed the article at [http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html) and created a new keypair.

If you want to keep your old key, you can probably use puttygen to convert it to the right format.

When you have the key, put it at ~/.ssh/identity and chmod it 600. gFTP will automatically find it and use the password as the passphrase for the key.

Have fun.

---

