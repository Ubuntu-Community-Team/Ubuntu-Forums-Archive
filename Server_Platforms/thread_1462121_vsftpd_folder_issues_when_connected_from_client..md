---
title: "vsftpd folder issues when connected from client."
date: 2010-04-25
forum: Server Platforms
---

### Post by Leaderone on 2010-04-25
Greetings :)
 
I have installed vsftp with ssl. The conf file is pretty basic, and it allowes me to log on with local users.
 
But my issue is, when connecting with eg Filezilla, it connects fine, but it outputs my files and folders with a date and time stamp in front of my folder.
 
So lets say I have a folder locally called "FILES", the output from client will be APRIL 23 14:30. So when I try to enter I get error 550.
 
But if I manually send a CWD command, CWD FILES, the clients succesfully changes the folder.
 
If I create a directory with the client, lets say FILES2, the folder is created, output is correct, and I can enter the new folder FILES2. If I exit the folder, it gets the timestamp and I cant access it anymore.
 
Anyone seen that before?
 
 
Thanks in advance.

---

