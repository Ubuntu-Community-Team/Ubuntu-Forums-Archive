---
title: "Running Ubuntu Server &amp; Desktop"
date: 2005-07-28
forum: Server Platforms
---

### Post by t_titschinger on 2005-07-28
Sorry if this post does not belong here.  Are there security risks by using an Ubuntu desktop as a server.  If so, can anyone direct me to more information.  I am currently going through the forum and others as well.

Thanks in advance.

---

### Post by t_titschinger on 2005-07-28
After reading more posts, I think that I have more knowledge.  I want to use my desktop as a home server, but I also want to make it accessible to myself on the internet.  I was also thinking of making it FTP capable so I can upload files from school, etc.  I hope this will help you help me.

---

### Post by relix42 on 2005-07-29
It appears you are asking two different questions,
1) Is ubuntu secure enough to make it a public host on the Internet?
2) How can I setup FTP?

If so, read on.

1) I've read and responded to a lot of questions about 'is such and such distro secure?'.  The answer always is, 'it has more to do with the administrator then the distro'.  Most Linux distributions share a common set of software for securing the machine.  However, if the administrator is not knowledgable enough to configure and maintain these disparate pieces of software, it doesn't matter which distro is used - the machine may be knocked over.  I'm happy to provide more details if you are interested on this topic.

2) There are *lots* of different FTP servers all with their own quirky needs.  However, if security is your concern, you really have only two options - grab one of the more secure FTP servers - such ProFTPD or VSFTPd or utilize SCP or SFTP with ssh.  If it's just you, use the SSH related options.

Hope this helps.

---

### Post by relix42 on 2005-07-29
It appears you are asking two different questions,
1) Is ubuntu secure enough to make it a public host on the Internet?
2) How can I setup FTP?

If so, read on.

1) I've read and responded to a lot of questions about 'is such and such distro secure?'.  The answer always is, 'it has more to do with the administrator then the distro'.  Most Linux distributions share a common set of software for securing the machine.  However, if the administrator is not knowledgable enough to configure and maintain these disparate pieces of software, it doesn't matter which distro is used - the machine may be knocked over.  I'm happy to provide more details if you are interested on this topic.

2) There are *lots* of different FTP servers all with their own quirky needs.  However, if security is your concern, you really have only two options - grab one of the more secure FTP servers - such ProFTPD or VSFTPd or utilize SCP or SFTP with ssh.  If it's just you, use the SSH related options.

Hope this helps.

---

### Post by relix42 on 2005-07-29
It appears you are asking two different questions,
1) Is ubuntu secure enough to make it a public host on the Internet?
2) How can I setup FTP?

If so, read on.

1) I've read and responded to a lot of questions about 'is such and such distro secure?'.  The answer always is, 'it has more to do with the administrator then the distro'.  Most Linux distributions share a common set of software for securing the machine.  However, if the administrator is not knowledgable enough to configure and maintain these disparate pieces of software, it doesn't matter which distro is used - the machine may be knocked over.  I'm happy to provide more details if you are interested on this topic.

2) There are *lots* of different FTP servers all with their own quirky needs.  However, if security is your concern, you really have only two options - grab one of the more secure FTP servers - such ProFTPD or VSFTPd or utilize SCP or SFTP with ssh.  If it's just you, use the SSH related options.

Hope this helps.

---

### Post by relix42 on 2005-07-29
Thinking something is going on with the forums - I have duplicated posts I can't remove.

---

### Post by [pl]ice on 2005-07-29
that's what i'm doing :] i got ftp (still trying to configure it correctly) and soon ssh; and my pc is on adsl non stop... but i would prefer a stand alone box for server(can't afford it...)

---

### Post by t_titschinger on 2005-07-31
I guess that I am asking two q's.  I am more concerned with setting up the proper security rather than the FTP.  I am an intermediate level programmer and can fair well.  I guess I am looking for the config files.  I am searching the web for how-tos and have a couple of books on the way.  Any further guidance on literature would be great.

Thanks in advance

---

### Post by tendo1 on 2005-08-25
[QUOTE=relix42]It appears you are asking two different questions,
1) Is ubuntu secure enough to make it a public host on the Internet?
2) How can I setup FTP?

If so, read on.

1) I've read and responded to a lot of questions about 'is such and such distro secure?'.  The answer always is, 'it has more to do with the administrator then the distro'.  Most Linux distributions share a common set of software for securing the machine.  However, if the administrator is not knowledgable enough to configure and maintain these disparate pieces of software, it doesn't matter which distro is used - the machine may be knocked over.  I'm happy to provide more details if you are interested on this topic.
[/QUOTE]

Hi! I'm interested in this topic.   ;-)

---

