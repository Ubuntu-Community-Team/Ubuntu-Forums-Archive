---
title: "Creating a secure unix-based file server"
date: 2009-10-25
forum: Server Platforms
---

### Post by wedjat on 2009-10-25
Being a DYI-type certainly makes things a lot more difficult. Especially when you don't really know much of the subject to start with.

I'm desperately running out of disk space on my laptop, but instead of getting an(other) external hard drive I've decided to scrach up a cheap, small, power-efficient and quiet computer to serve me as a file server.

My knowledge on both linux systems and servers is quite limited, altough I couldn't call myself a complete rookie. What I need is a dedicated multimedia/backup server, that can act as a network hard drive to other computers, and that can be securely and easily accessed from remote computers, preferably without any additional applications or setting on the remote end.

Thus my questions are:

- Which distribution would suit my needs best?
- Where can I find information to set a system like that up?
- Is all that in one package even possible?

Any help will be greatly appreciated! I don't expect anyone to give any step-by-step-like instructions, links or subject so research should do.

Thanks!
wedjat

---

### Post by J V on 2009-10-25
Ubuntu is a *linux* OS, not unix...

If you want to use a linux system for that it should be fairly easy, install an FTP and rsync and all you need is to forward the port from your router and you've got it done...

```
sudo apt-get install vsftpd
# Setup according to https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html#vsftpd-ftp-server-configuration
sudo apt-get install grsync
****# now forward the router port
```

---

### Post by wedjat on 2009-10-25
> **J V said:**
> Ubuntu is a *linux* OS, not unix...

If you want to use a linux system for that it should be fairly easy, install an FTP and rsync and all you need is to forward the port from your router and you've got it done...

I said I wasn't too experienced ;) Thanks for the correction though. How secure is that, and how would I access it remotely? Through the IP-address?

---

### Post by J V on 2009-10-25
Yes you would access through the IP adress...

If you use public keys rather than a simple password, its as secure as it gets...

Grsync is just to quickly keep your files backed up, and runs at intervals, the FTP is less secure, but using a public key (Don't know how, probably a bit of SSH fiddling) unless someone gets physical access to your computer they won't have access to the server...

Note also that if you use an encrypted private directory to store your keys even if they did have access to your PC then they would need to know your password to use it. (by the time they crack it you will have changed keys...)

Edit: Yes you would need to use openSSH rather than FTP, ftp is unencrypted (Anyone can read or alter data in transit) but SSH is encrypted...

VSFTPD package does something like that? Not an expert on encrypted data transfer :/

I would just install openssh and read a ton of guides :)

---

### Post by Sporkman on 2009-10-25
Check out [http://www.freenas.org/](http://www.freenas.org/) , which btw *is* unix (not linux). ;)

Never used it myself, but it gets rave reviews around here.

---

### Post by windependence on 2009-10-26
+1 for FreeNAS. Great product. Supports everything you want with a web interface. Even includes a lightweight web server.

-Tim

---

### Post by wedjat on 2009-10-26
Hey, thanks for the FreeNAS suggestion! Just downloaded it but haven't tried it yet, altough I dare say it seems to be just what I'm looking for.

---

