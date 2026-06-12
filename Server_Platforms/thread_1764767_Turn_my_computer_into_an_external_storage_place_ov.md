---
title: "Turn my computer into an external storage place over the web?"
date: 2011-05-22
forum: Server Platforms
---

### Post by Pithikos on 2011-05-22
I run Debian on my old computer to use it as a server. Everything is configured properly so that it functions as a web server. Now that summer comes closer I will not be home most of the time and I was thinking to use part of my server to upload/download files. Is there some nice package that provides an easy interface for such a task? I am reffering to something like the wikimedia package but for just downloading/uploading files.

---

### Post by ratcheer on 2011-05-22
ftp?

Tim

---

### Post by kgatan on 2011-05-22
Id recommend AjaXplorer which is an easy to use web gui.
If you dont need web gui then sftp would be my choice.

---

### Post by compmodder26 on 2011-05-22
I would recommend sftp as well.  Your GUI would simply be your file manager.

---

### Post by Pithikos on 2011-05-22
Well I am not sure of how it would work if it happens one day to only have a windows system available under my hands or if I happen to be on a computer that I don' have admin privileges. Then sftp would not work, right? That's why I was thinking of a webgui, to be sure that it will always work no matter what platform I use.

---

### Post by Lars Noodén on 2011-05-22
> **Pithikos said:**
> Well I am not sure of how it would work if it happens one day to only have a windows system available under my hands or if I happen to be on a computer that I don' have admin privileges. Then sftp would not work, right? That's why I was thinking of a webgui, to be sure that it will always work no matter what platform I use.

I'd second the recommendation of using SFTP.  There are a lot of [SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) to choose from.

Even Windows machines, as poor an option as they are, have full-fledged SFTP clients.  Filezilla is one.  You can often run these apps from the temp directory or a USB drive.  There is even a [portable Filezilla](http://portableapps.com/apps/internet/filezilla_portable) designed to be run that way.

---

### Post by ratcheer on 2011-05-22
> **ratcheer said:**
> ftp?

Tim

Sorry, yes, I meant sftp.

Tim

---

