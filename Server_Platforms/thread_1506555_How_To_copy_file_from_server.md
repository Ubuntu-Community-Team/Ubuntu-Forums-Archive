---
title: "How To copy file from server?"
date: 2010-06-10
forum: Server Platforms
---

### Post by freesparks on 2010-06-10
Hello all,
  
   Being fairly new to navigating around Linux in a server environment, I simply want to copy a file from the server to a file in my home directory on my laptop.  I connected successfully using vpnc  and then used ssh to connect to the server.  Now, all I want to do is copy a file that I see on the server's home directory to my home directory on my laptop.  Been reading on commands like > scp as well all using > sftp.  However, I don't want to use these commands unless I am comfortable with them because the file that I am copying is a big file and I don't want to lose it.  Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by nikomo on 2010-06-10
What OS is your laptop using? If Ubuntu, you can just "Connect to Server" from the menus and copy the file through a nice GUI. It basically makes the server look like a disk drive in Nautilus so it's like copying any other file.

Sure, not the most "elite hacker" style of doing it but hey it works.

---

### Post by freesparks on 2010-06-10
Hello nikomo,

   Thank you so much.  I'm such a thud i just remembered reading about it somewhere and reading it for myself.  Thank you so much, it worked perfectly.  It would still be nice to know how to do this properly through the command line though.  I'm trying to get out of the GUI habits and get over the fear of the command line.

Best Regards,

freesparks

Thanks a lot!!!

---

### Post by Neezer on 2010-06-10
This link might be helpful if you want to know the real "hacker" way to do it....quite frankly, I use the connect to server method much more because I have bookmarks saved so it is only a click away.

To each his own...

[http://ubuntumanual.org/posts/154/copy-files-remotely-using-scp-in-ubuntu](http://ubuntumanual.org/posts/154/copy-files-remotely-using-scp-in-ubuntu)

---

