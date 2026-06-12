---
title: "WebGUI file manager"
date: 2011-06-13
forum: Server Platforms
---

### Post by Jimmyhead521 on 2011-06-13
Hello

I'm after a WebGUI file manager which runs on another port rather than port 80 (already have a Apache installed)

But i want to be able to access and edit files from the web, rather using FTP client etc..

Is anyone aware of any?

Thanks in advance guys :popcorn:

---

### Post by donniezazen on 2011-06-13
I use [http://www.ajaxplorer.info/wordpress/](http://www.ajaxplorer.info/wordpress/)

---

### Post by Lars Noodén on 2011-06-13
I would recommend avoiding both FTP and the Web GUI.  

You can use SFTP instead, which is more secure and you already have one or more [graphical SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) at hand.

---

### Post by donniezazen on 2011-06-13
> **Lars Noodén said:**
> I would recommend avoiding both FTP and the Web GUI.  

You can use SFTP instead, which is more secure and you already have one or more [graphical SFTP clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) at hand.

Isn't encryption going to slow down large file transfer considerably.

---

### Post by Lars Noodén on 2011-06-13
> **soham_1207 said:**
> Isn't encryption going to slow down large file transfer considerably.

Not noticeably unless you are running some very, very old processor from the early 1990's / late 1980's.

---

### Post by donniezazen on 2011-06-13
> **Lars Noodén said:**
> Not noticeably unless you are running some very, very old processor from the early 1990's / late 1980's.

That's good to know. I will check them out later today. Ajaxplorer is any ways giving me hard time setting up user/group permissions. And it does really nice web streaming but i guess i hate converting my videos to MP4 format. It takes hell of a time. Subsonic is good for audio and video streaming.

---

### Post by donniezazen on 2011-06-13
Their is a file manager inbuilt in webmin which i use to make changes to configuration files.

---

