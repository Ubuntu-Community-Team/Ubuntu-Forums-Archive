---
title: "Sharing files in an encrypted home directory"
date: 2011-09-04
forum: Security
---

### Post by inclusivedisjunction on 2011-09-04
Is there a way to share a subdirectory without moving it to an unencrypted parent? I'd like to find a way to do the following:

1. Use a specific subdirectory (ie. /home/username/share) as the document root for an HTTP server.
2. Be able to connect to an FTP server with a different username and password and access a specific directory, such as /home/username/share

I thought that if I created symlinks, the daemons should be able to follow them when I was logged in, but they don't seem to work, even if I set the permissions on the directory to give read access to everyone.

P.S. - I'm using Kubuntu 11.04; I can't change what distro my profile says I'm using, probably because I have less than 50 posts.

---

### Post by bodhi.zazen on 2011-09-05
If the user is logged in , $HOME will be decrypted, otherwise it will be encrypted.

I suggest moving the data elsewhere and/or an alternate encryption scheme and/or an alternate data sharing protocol, ftp is notoriously insecure, I would use ssh / sftp.

---

### Post by inclusivedisjunction on 2011-09-05
The symlinks don't work even if I am logged in...

The reason I wanted to use FTP is because the application I want to use (WiiMC) only supports SMB and FTP. The FTP server isn't open to the internet, so I'm not worried about that kind of exploit. I'm more worried about the hypothetical Gestapo (or a mischievous sibling) copying the username and password from the WiiMC configuration files. Even if WiiMC did support SSH/SCP, *they* would still be able to copy the username+pass or public key. I wanted the credentials to be useless for decrypting my home directory so that I only need to make sure I am logged out to be safe.

Although now that I think about it, if the Gestapo come while I'm viewing content on the Wii...

---

