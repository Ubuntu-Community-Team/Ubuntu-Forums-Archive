---
title: "PHP lock access to previous folders"
date: 2008-11-09
forum: Server Platforms
---

### Post by micdhack on 2008-11-09
I have a web server and i would like to give people access to specific ftp folders. I want to give the users the opportunity to use php as well.
Since php has some commands like exec, fopen, include i am afraid that maybe users will try to "hack" the server by accessing previous directories than the ones assigned to them. 
For example they can create a php script that open a file in ../bla bla or worse exec("rm -r ../*") which may result in deleting all other users directories if the structure is "/ftp/<userdir>".
I dont want to disable commands such as exec and other cause i have php scripts and i need them. 
So is there a way that php can be locked and the root directory will be locked to each user's directory?
Note that these scripts will be executed from apache and not from ssh, so probably user and group owner for all directories that users will have will be the same.

---

