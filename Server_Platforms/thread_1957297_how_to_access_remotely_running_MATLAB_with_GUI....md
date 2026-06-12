---
title: "how to access remotely running MATLAB with GUI...?"
date: 2012-04-12
forum: Server Platforms
---

### Post by durga4dps on 2012-04-12
I have used linux screen command to save a session but facing following problem:

%screen
%matlab  (Matlab pop-up window appeared)

Then i have pressed ctrl+a and ctrl+d.
%exit
logout
........................
Again i have established a connection to remote server and re-attached to previous session. Typing ps -a , i have seen that matlab is running but **cannot access the matlab GUI**. I am using **ssh client from windows machine** and Xming X server.

Please help!!!!!

---

### Post by papibe on 2012-04-12
Hi durga4dps. Welcome to the forums!

AFAIK, you need 2 things to run the metlab gui in Windows:
[LIST=1]
[*]Use X11 port forwarding on your ssh connection, and
[*]Keep the ssh connection alive (do not logout).
[/LIST]
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1935661&highlight=matlab") with a similar concern.
Regards.

---

