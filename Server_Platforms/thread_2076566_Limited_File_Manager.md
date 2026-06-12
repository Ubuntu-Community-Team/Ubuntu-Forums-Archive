---
title: "Limited File Manager?"
date: 2012-10-26
forum: Server Platforms
---

### Post by shumes on 2012-10-26
I am a teacher in a school in Texas. One of the classes I teach is Web Technologies where they learn to create web pages in various ways. I have a Ubuntu 12.04.1 server running in my room with full admin rights. It is running Apache 2 web server with a site running on it. 
Here is my issue. I have created a sub level for the class and would like to give the students access to upload their own files. However, I do not want them to have full access to the server or any other directories on the server other than the class directory. It also needs to be a web based manager. Is this possible and what is recommended?

---

### Post by nothingspecial on 2012-10-26
*Thread moved to **Server Platforms**.*

---

### Post by Lars Noodén on 2012-10-26
One way to allow uploads with a graphical client would be to use SFTP.  It's not web-based but will do the job graphically nonetheless.  Clients include Nautilus, Dolphin and FileZilla.  It's easy to restrict access to SFTP and prohibit shell access.  

It's also rather easy to chroot users to specific directories.

---

