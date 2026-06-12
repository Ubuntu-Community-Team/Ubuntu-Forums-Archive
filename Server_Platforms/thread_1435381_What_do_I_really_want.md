---
title: "What do I really want?"
date: 2010-03-21
forum: Server Platforms
---

### Post by Ceadda on 2010-03-21
I don't know what is required to do these activities, or if it is even possible.

I have Ubuntu 9.10 server installed and several computers running a mix of ubuntu, 7 and vista. 

I'd like to be able to have all my media on my server and be able to access it from my within my network and outside of my network. 

-stream audio and video
-download and upload any sort of file I need from where ever I am

I know the latter of the two would be setting up some sort of ftp on my server like proftpd. Being able to stream audio and video is my main goal here. 

Do I need to install a desktop on my server to be able to do this?

The same drive with all of my media will be the one I would like to download and upload too.

Thank you kindly for any advice you can give me in this matter.

---

### Post by GregBrannon on 2010-03-21
You've got a good start on defining what you want.  What you NEED to get to what you want might be the bigger question.  Why don't you start by getting your local network setup - all machines talking to and sharing with each other across wired and wireless (as you choose) - and then build on that?

---

### Post by km0r3 on 2010-03-21
[Here]("http://www.makeuseof.com/tag/using-your-linux-computer-as-a-media-server-part-2/") is a list of programs which facilitate setting up your server to serve Audio (and/or Video) over the Network.

Actually doing a Google query with keywords like "Ubuntu Media Server" or "Ubuntu Stream Audio Video" gives me quite some useful results. I suggest you giving that a try, too.
> 
I know the latter of the two would be setting up some sort of ftp on my server like proftpd. Being able to stream audio and video is my main goal here.Depends. FTP is quite "ugly". ugly for you needs, and insecure, too. If you trust your network environment then the latter point doesn't quite play a big role, but I consider checking out [Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") or [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").
If you insist on using something FTP-like try SFTP. The secure version of FTP.

If you have Windows clients accessing files from your server I'd suggest using Samba.
> 
Do I need to install a desktop on my server to be able to do this?You can do that quite well from the Terminal, too, if you don't lack experience.

**Questions?** Ask.

---

### Post by Ceadda on 2010-03-21
This is the sort of direction I was looking for. Thank you. It's funny I got so caught up in other aspects of this (server) that I didn't even think about searching simple keywords.

---

### Post by km0r3 on 2010-03-21
> **Ceadda said:**
> This is the sort of direction I was looking for. Thank you. It's funny I got so caught up in other aspects of this (server) that I didn't even think about searching simple keywords.
Don't worry. :) I had just the same feelings some time ago like you have.

---

### Post by ris8 on 2010-03-21
I put Ubuntu as a file server (Samba). The windows machines have their "my music" (and "my documents", "my pictures", etc) on the server, so everything is shared.
I also put a virtual XP machine on the server for running the "my movies" server (very nice software to organize your DVD collection, but windows only).
You can use the virtual machine for any non-linux software you need, while keeping the reliability/uptime of the linux file server.

---

### Post by HermanAB on 2010-03-22
Note that it is easier to make NFS (services for UNIX) work on Windows, than to make SMB (Samba) work on Linux.

---

### Post by errrata on 2010-03-22
I would think for security you wouldn't want nfs or samba to be available over the internet. An ftp server should be safe for uploading files and a web server (apache) is a quick and easy way to serve files.

---

### Post by km0r3 on 2010-03-22
> **errrata said:**
> ...and a web server (apache) is a quick and easy way to serve files.
Quick and easy way: yes. Most convenient? Depends.

Using a Web Server for sharing files which you rarely change and mostly use for lecture only over a network would be ... OK. But when you constantly modify the files, change the tree structure, etc. on the server.. using FTP.. is just very painful in my opinion.

You can show me otherwise, though. I'm always curious about learning new things. :)

---

### Post by dudumomo on 2010-03-22
What about something like AjaxPlorer ?
An explorer through http/https (Demo: [www.ajaxplorer.info/demo/](www.ajaxplorer.info/demo/) log: demo///demo)

---

### Post by errrata on 2010-03-22
The web server can will give a simple directory listing of folders without an index.html page which you can set as the same directory for ftp. In the end web servers are really just fancy file servers.

---

### Post by Ceadda on 2010-03-23
This is all really great thank you.:D

---

### Post by Ceadda on 2010-03-23
> **dudumomo said:**
> What about something like AjaxPlorer ?
An explorer through http/https (Demo: [www.ajaxplorer.info/demo/](www.ajaxplorer.info/demo/) log: demo///demo)

This is an interesting program. I actually used your blog for some advice before posting this thread. It was really helpful, just wasn't the direction I was going with my server.

---

