---
title: "[SOLVED] Downloading from Apache2 configured website fails"
date: 2008-10-24
forum: Server Platforms
---

### Post by noctris on 2008-10-24
Hi Guys,

I'm a first time poster here and have been breaking my head over a very strange error i've been having:

I have a webserver running internally for a couple of our sites (crm etc) and have been trying to setup an extra virtual host to host a couple of thousand files which our tech department needs to be able to download. Now this site is up and running and you can browse through the directories, but whenever you try to download a file from it ( between 5 and 300 Mb), it complete's immediatly and is only like 12,4 Kb large on disk.. 

Has anyone had this issue before ? I just can't figure it out. All help / input welcome !

Kind regards,

Noctris

---

### Post by noctris on 2008-10-24
P.S: in the access.log for apache2, it just says 200 as reply so i am guessing it finds the file...

---

### Post by noctris on 2008-10-26
Ok.. so after A LOT of digging, turns out that EnableSendfile in Apache2.2 is broken when using CIFS / Samba shares as your document root..

This has as effect that Apache2 cannot send more than a few kilobytes of a file mounted over CIFS or Samba.  This causes most web browsers to choke when downloading, anything larger than a small HTML file.  Wget will eventually succeed, attempting to get the file repeatedly, accessing a few kilobytes at a time. 


Disabling sendfile functionality on the directories in question provided 
an adequate workaround. 

I hope i can help someone else with this aswell..

---

