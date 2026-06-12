---
title: "Can you setup scponly for write-only scp-only usage"
date: 2009-09-30
forum: Server Platforms
---

### Post by all4miller on 2009-09-30
Hi,

Based on this excellent post [http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510) I am trying to extend my scponly setup to cater for the following:

- Create a drop box type setup that only allows user to copy files to the server
- They can never list remote directories
- They can never leave the "incoming" directory
- They can only put files on the server, never copy anything locally
- They can SCP and SFTP is disabled

I'm not sure if this is possible or within the scope of scponly but if somebody has any ideas or maybe even another better way I would appreciate any input.

The reason for this is that clients will be sending sensitive data so I would like to make it near impossible for a 3rd party to get access to uploaded files in the event the clients login details are compromised. Worst case scenario is somebody could create lots of content via a compromised account. If there are better ways for this kind of thing from a security point of view please let me know. I am a complete linux noob ;)

*Using Ubuntu Server Jaunty (9.04)*

Cheers

---

### Post by cdenley on 2009-09-30
This would be tricky, if possible, since ssh usually uses filesystem permissions to restrict file operation. If they can create files, they can delete or list files. ACL's may offer finer control over this, though. It would probably be easier to use an ftp server with SSL encryption. I have a system with a similar function, and I'm currently using [uber-uploader]("http://uber-uploader.sourceforge.net/") with SSL so there aren't any software requirements for users (except a web browser). It is also a much more customizable solution.

---

### Post by all4miller on 2009-09-30
Yeah I started leaning towards something along those lines. Ultimately this data ends up in a web app anyhows, but gets there via an unattended batch process, so maybe sending it via a http post over SSL is just as good. Cool thanks for the input much appreciated.

---

