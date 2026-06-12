---
title: "Secure Cloud Backup?"
date: 2009-11-15
forum: The Cafe
---

### Post by kevin11951 on 2009-11-15
Does something like this exist yet?  If not, would you find it useful?

I was bored and started wondering about a secure cloud based backup system, and this is what I came up with...

> What is the Open Virtual Private Cloud Project?

The Open VPC Project is a cloud based backup (like Dropbox or Ubuntu One).  However, all files are encrypted under a password of your choosing before final upload.  Encryption is done using GPG.  The file(s) are individually encrypted using GPG, then they and their md5sum(s) are uploaded to our secure server.  Finally, the uploaded file(s) are checked against their md5sum(s) for safety.

When you view the files by the web interface, the “.gpg” extension is dropped, and when/if you download a file via the web gui, you will be presented with a text box, where you will enter your password.  The server will then un-encrypt the file, and you will download it.  The server will then forget the password instantly.

If you have the client installed on multiple computers, the md5sums and creation/modification date will be used to identify each file as newer or older than their counterparts on other computers.  The files will then be downloaded to the other computers automatically, un-encrypted using your computer's client, and the original file being replaced will be backed up on both server and client.

Both the client and server software will be open source and distributed for users to create private file storage clouds of their own.  Server setup should be as easy as running a shell script and answering a few questions.

Paid support will be provided to businesses and home clients (including private clouds) who want un-interrupted service.

---

### Post by Firestem4 on 2009-11-15
alternatively, you could encrypt your data before syncing it with your cloud-server of choice. 

I won't say much about the idea becausee I don't beleive in hosted cloud computing services.

---

### Post by SLEEPER_V on 2009-11-15
can you guys tell me what the benefit of cloud storage is?  I use an external hd to backup my stuff.  With the inexpensive prices of storage, whats the point?  If its security ( like from fire or water damage) pocket hd have alot of storage and stick it in your pocket,  I dunno, can you guys tell me why you see it as advantageous?

---

### Post by blueshiftoverwatch on 2009-11-16
> **SLEEPER_V said:**
> can you guys tell me what the benefit of cloud storage is?  I use an external hd to backup my stuff.  With the inexpensive prices of storage, whats the point?  If its security ( like from fire or water damage) pocket hd have alot of storage and stick it in your pocket,  I dunno, can you guys tell me why you see it as advantageous?
Also, if you download a file and then upload it to the cloud server for backup your effectively doubling your bandwidth usage. Which, depending on how much bandwidth you already use and who your ISP is, may or may not be an issue.

---

