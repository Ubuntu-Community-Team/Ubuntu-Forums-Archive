---
title: "how to connect to sftp and open a files"
date: 2016-04-26
forum: Server Platforms
---

### Post by matt082606 on 2016-04-26
I currently use Dreamweaver as well. To do this I use a virtual machine. There are times I can't escape the VM (AutoCad, PLC software, etc.), but this should be one of the times when I can.

What I need is very simple:
A text editor that can open files and synchronize with an SFTP server.

Due to the nature of how we develop (java front end - php mysql backend) we need to have multiple people working on various parts of web applications at a time. Dreamweaver solves this very easily. We make backups and have an internal sort of SVN. We each connect and can edit js, php, json, css, etc. files. I have tried to get eclipse to work with Jcraft SFTP plugin, I have tried Netbeans with various plugins. I CANNOT figure this out. To me it should be incredibly simple to even add SFTP to Sublime text. I don't need auto-complete though that would be nice, but I do need syntax coloring and tabs and rudimentary syntax checking.

Can anyone point me to the guide that tells me step by step how to make a connection to my sftp and open a file? 

I have spent a week now searching and trying different things to accomplish this very basic task. I don't get how the plugins on these two most recommended IDEs work. there are no new menus, no new options, it's as if they were never installed in the first place.

Thanks for the help.

---

### Post by Bucky Ball on 2016-04-26
*Post moved to own thread.*

---

### Post by matt082606 on 2016-04-26
I finally found my answer.
For anyone beating their head against the wall to replace Dreamweaver with a Linux solution here it is:

1) DO NOT INSTALL ECLIPSE FROM REPO (it is very old)

2) Goto eclipse.org and download the latest version, or at least Mars.2 

3) install 

4) Goto help-> Install new software... 
    Choose Mars repository, search for Remote System Explorer and install it from General Purpose tools

5) Change project view to Remote systems

6) Close local and right click-> New-> Connection

7) Set up the connection and you are now operating on the sever via SFTP

I hope this helps others, and that includes the original question, but my post was moved from that original thread about this same topic.

---

