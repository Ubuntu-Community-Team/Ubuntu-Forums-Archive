---
title: "Encrypted remote drive over NFS"
date: 2009-05-02
forum: Security
---

### Post by tomtar on 2009-05-02
Guys,

Here is scenario:
- two machines in LAN: server (let's call it "remote") and desktop (called "local" from now on)
- both machines are debian-like systems
- remote machine hosts NFS service

I would like to have nfs share mounted on a local machine. It's 3 minutes job so far... 
But then I would like to have this share encrypted. And what would be ideal is that the remote machine (which hosts the share) has no visibility to files. I don't want to decrypt this drive on remote machine at any stage. Local machine should be the only one with full visibility to decrypted files.

Any ideas? Please enlighten me. Thanks in advance!

Regards,
tomtar

---

### Post by HermanAB on 2009-05-02
I think all you need to do is share the device node (for example /dev/sdb) in /etc/exports.

Try it and see - I can't try it right now - busy installing a new machine.

Hmm, I was curious and it doesn't work:
"exportfs: Warning: /dev/hdb1 is neither a directory nor a file.
     remote access will fail"

What will work, is if you don't encrypt the whole partition, but rather create a an encrypted filesystem in a file and export the directory that it is in.

---

