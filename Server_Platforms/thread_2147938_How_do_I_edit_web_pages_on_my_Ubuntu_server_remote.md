---
title: "How do I edit web pages on my Ubuntu server remotely with Windows?"
date: 2013-05-23
forum: Server Platforms
---

### Post by dan40 on 2013-05-23
Hi, I'm just curious, is there an app for Windows that I can get that will allow me to manage websites on my Ubuntu server from a remote location?

The reason I ask is because if I'm on the road and I need to make a change, I can quickly open my laptop and edit the page remotely.  Will something like ExpressionWeb or FrontPage (although outdated) allow me to remotely manage pages on my Ubuntu server?

Thanks for any help!

---

### Post by pqwoerituytrueiwoq on 2013-05-23
if you run a ftp server on the ubuntu server you should be able to use any number of ftp clients, you may be able to find a ssh client for windows, then you could edit with nano

---

### Post by dan40 on 2013-05-23
Thanks, I was looking more for a wysiwyg editor for Windows that will allow me to connect to my Ubuntu server and edit pages on-the-fly.  I don't think I want to edit web pages with nano!

---

### Post by ubu_dynamite on 2013-05-23
I,m guesing you mean a html editor.
[http://en.wikipedia.org/wiki/Comparison_of_HTML_editors](http://en.wikipedia.org/wiki/Comparison_of_HTML_editors)

Some of those have builtin ftp client you will need a ftp server running on the server to connect to.
Or use a separate ftp client to upload the modified files.

If you have ssh access to the machine i recommand using ssh/sftp instead.

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Server Platforms**.*

---

### Post by josephmills on 2013-05-23
I use a couple of different IDE's for things related to web If I need to alter on the fly I use 
[http://www.sublimetext.com/](http://www.sublimetext.com/)
this works alright as it has the ablity to alter files on the fly 
I also use qtcreator sometimes. just depends TBH what I am trying to do. I do know that I do not like dreamweaver or visual studio and them sorta things

---

