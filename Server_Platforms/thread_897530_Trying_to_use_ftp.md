---
title: "Trying to use ftp"
date: 2008-08-22
forum: Server Platforms
---

### Post by daggwood on 2008-08-22
Ok. For anyone who has already replied to my other post thank you very much, I am now able to manuver around to directories and stuff in my ubuntu but now i face another chalenge. I want to set up a ftp so I can upload stuff from other computers. I read one tutorial and it told me to load proftpd. I tried but it cant find it. I entered it like this.

apt-get install proftpd mysql       "then in reply i get"
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mysql

What am I doing wrong or is this even the way to go about it. Please help.

Thank you for your comments.

---

### Post by Ximbiot on 2008-08-22
I would just ignore FTP and use scp/sftp, unless you need to make the site public for some reason.  scp/sftp is more secure and should work over your existing SSHD setup.  The command line syntax is almost exactly like `cp', with extensions to connect to the remotehost, like:

[CODE]scp localfilename user@remotehost:newfilename[CODE]

or

[CODE]scp -rp localdirname user@remotehost:newdirname[CODE]

You don't need to specifiy user name if you have the same username on both hosts, as with the SSH client.

There is also a free WinSCP GUI client for any connections you need to make from Windows and I wouldn't be surprised to find a Gnome GUI, but I haven't looked into it.

Derek

---

### Post by livestockPimp on 2008-08-22
you do not need to use mysql for ftp, you can get proftpd to work with PAM users, off memory if security is an issue you can even disable the users from having a shell on the linux server so thier account is purely an FTP account.

---

### Post by daggwood on 2008-08-22
so if I use the scp i can link to my server through a windows based computer

---

### Post by Ximbiot on 2008-08-22
> **daggwood said:**
> so if I use the scp i can link to my server through a windows based computer

Yes.  You can link, probably, from any OS you can get an SSH client running on.  On Windows, I use the GUI WinSCP client, as I said.  WinSCP has drag-and-drop integration with Windows Explorer (though that appears to be broken on Vista) and if you already have PuTTY set up then WinSCP can even use its key agent (Pageant).

---

