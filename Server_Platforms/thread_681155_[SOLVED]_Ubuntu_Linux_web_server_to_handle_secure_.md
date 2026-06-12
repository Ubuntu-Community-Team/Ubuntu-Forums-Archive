---
title: "[SOLVED] Ubuntu Linux web server to handle secure Linux and windows files for various"
date: 2008-01-28
forum: Server Platforms
---

### Post by CyberDean on 2008-01-28
As a new Linux user, 1 1/2 weeks, reading everything I can, I need assistance to setup a Linux web server as a secure file server for a few users.  Each user will have a user's area, secure, to store files and backups where no other user has access.  Users can be in various locations, or a user can be traveling from state to state with access needed through the internet to the server. Users could use windows file or linux files.  Can a user update the file that is located on the server.  No other options will be implemented at this time, but may in the future.  The server will be Linux web or internet server, disk for the operating software with backup capabilities and data disk in Raid1 or Raid5 configuration.

In summary: 1. What is the best Linux server software for internet access? 2. The best security software?  3. Will windows and Linux files reside on the same disk or partition? 4. Software for real time update of files currently on the server and to move the files to and from the server? 5. What have I not thought of?

Sorry for no more details, I am trying to keep it simple.

Thanks for any help.

---

### Post by Maxtorm on 2008-01-28
If you want simple, I would suggest using SCP. This involves installing nothing more than SSH on the Ubuntu server housing your files.
```
sudo apt-get install ssh
```
User administration is native -- i.e. add a user to the Ubuntu server and that user is automatically a valid SSH user. By default, new users will be limited to their own home directory.

Windows clients will be able to use WinSCP ([http://winscp.net/](http://winscp.net/)) and Linux users can use scp from the command line. If Linux users want/need a gui, they can install secpanel.

1. SSH is secure.
2. It's widely recognized as the defacto standard for securely transmitting data.
3. Yes, Windows and Linux can store files on the same disk/partition. This is not be confused with storing in native Windows/Linux formats such as NTFS/ext3 respectively. However, that is irrelevant to the end user.
4. scp / WinSCP
5. Can't think of anything.

---

### Post by CyberDean on 2008-01-29
Thanks so much.  I had read so many articles I was starting to confuse myself.  I now have a direction to go forward.

---

