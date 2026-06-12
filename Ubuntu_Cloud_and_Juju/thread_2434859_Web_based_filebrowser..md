---
title: "Web based filebrowser."
date: 2020-01-12
forum: Ubuntu Cloud and Juju
---

### Post by Arunomi on 2020-01-12
Hi, I'm new to servers and I'm trying to set up a server.

I have installed samba to start a file server but I'm finding it a bit laggy to browse around and clean out all old files.
I then read that a whenever i try to look in folders withe pictures the client downloads the pic and makes a thumbnail and withe a loot och pic that is no good.

I read that in a web-based file browser the operation around the files stays on the server so I found a web-based file browser "https://filebrowser.xyz/". This one is nice and works well but it doesn't create thumbnails for the pic's and it's hard to find information on how to set it up and configure it.

So my question is if there is someone that has experience with this file browser and can point me in the right direction to get it to create thumbnails, or if there is another solution out there that could work for me?

Best regards Sean

---

### Post by TheFu on 2020-01-12
If you want a web-based file access tool, perhaps something like owncloud or nextcloud or seafile would fit?  Those have well-understood methods and are actively used.  Different directories in nextcloud can be setup to behave like dropbox, though not all need to be. There's also a gallery addon - 1-click install.  I'm running about 20 addons from the gallery to chat to video conferencing to calendaring to email integration.  Most are 1-click installs once the base server is setup and working.  I don't trust web-servers enough to allow read-write access to most files.  I only allow read-only access most of the time.  Only files uploaded from a client using the web interface are read-write on my system.

Another option is to use sftp, which is enabled for free whenever the openssh-server is installed on any Unix machine.  Every Linux file manager supports sftp:// URLs. For Windows, there is WinSCP.  With ssh, there are lots of other options too - like sshfs, scp, or just using ssh to remote in and behaving like you are on the system directly, because you are.

Thumbnails are a setting on the client browser, right?  If you don't want that, disable it.  If you want them pre-built, there are lots of image tools that can to it, but you'll need to create the thumbnails in the correct location, with the correct filenames yourself. Should be a pretty easy bash script. I'd use convert, which is part of the Imagemagick tool.  [https://www.imagemagick.org/Usage/thumbnails/#storage](https://www.imagemagick.org/Usage/thumbnails/#storage) has examples with **mogrify** and **convert**. Or you could make an index with a page of thumbnails and filenames for each.  Open that in 1 window and do your clean up in a different window.

Also, Samba is not the best protocol to be used between Unix systems. NFS is for many reasons.

---

### Post by Arunomi on 2020-01-12
Is there a way to get nfs working in windows 10 home?

---

### Post by SeijiSensei on 2020-01-12
I'd install openssh-server on the server and WinSCP on the Windows client.

---

