---
title: "Samba and Firestarter again"
date: 2008-01-18
forum: Server Platforms
---

### Post by wflott on 2008-01-18
I have read all most all the post on the Ubuntu forums about Samba and Firestarter.  Tried to follow all the ideas in Dsmalley's post.  Still can't get PCs in our system to see  or access the Samba file server.  The Samba server has a fixed ip.  I want to grant access to all computers within our system therefore I have an access allowed line such as xxx.xxx.0.0/24.  

On Samba I have security = user with encripted passwords.  The server is not serving as a WINS server.  I have addressed our system WINS server in the SAMBA configuration file.

One question I have is if I am using Security=user do I need to be running Winbind and if so, why?

I had this system up and running with the previous version of Kubuntu using Guarddog, but I am failing miserably with current version of Ubuntu and Firestater.

I think we all need a simple how-to for Samba with Firestater both of a simple home system behind a router and a larger business lan.

Thanks for any help that you can offer so I can get this system up and running before Tuesday of next week.

---

### Post by wflott on 2008-01-18
Forgot to note in my earlier post that I have FTP and SSH2 passing through Firestarter without a problem.

---

