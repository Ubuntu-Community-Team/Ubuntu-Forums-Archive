---
title: "Setting up an Ubuntu WINS server"
date: 2008-10-08
forum: Server Platforms
---

### Post by jonathanmotes on 2008-10-08
I'm trying to set up a computer (running Ubuntu 8.04) as a WINS server on my network. I've been configuring the /etc/samba/smb.conf file and can't seem to get it to work. Does anyone know how to do this?

Also, I've read in a couple of places that the computer that provides WINS services cannot do name translation (with WINS) and file sharing at the same time. Is that true?

And another question: Once I get the server set up as a WINS server, can I access the server itself by name?

Thanks a lot!

---

### Post by sefs on 2009-08-27
Wins is set up in samba by putting the below in /etc/samba/smb.conf

```

wins support = yes
name resolve order = wins lmhosts bcast hosts

```

I think you probably have to access it by IP.

In windows 2003 server they give the option of setting up all kinds of services 2 of which are WINS and File Server.  They allow you to set them up together and does not try to stop you, so from that I gather that a wins server and file server can be on the same box.

---

