---
title: "openssh bug?"
date: 2010-05-07
forum: Server Platforms
---

### Post by ivlivs on 2010-05-07
Hello, I saw this happening on my 8.04 server with openssh-server 1:4.7p1-8ubuntu1.2:

- I create a file on the server;
- as superuser I change the owner of the file to another user;
- I open an ssh connection with Nautilus from a 10.04 desktop, edit and save the file (say with gedit);
- I look at the permissions and I own the file again.

Is this a bug? Can anyone else reproduce it? If yes, please file the bug on Launchpad; I was unable to do it without graphic environment.
The same happens when changing group.

---

### Post by volkswagner on 2010-05-08
I am not sure if this is a bug.

I can confirm the same behaviour.

I have a remote server running 8.04.  I created a .txt file using nano inside my home directory.  After saving the file it was set to user:group=root:root.

I then Opened a ssh session with Nautilus on my 9.04 Desktop.  I edited the file, after saving it owner:group went to myusername:myusername.

I then performed the same thing with a file outside my home directory.  When trying to save the file with Nautilus, I was denied permission to change the file.

I think the action is normal, provided your are within your /home directory.  Is this happening inside your /home/user directory?

---

### Post by ivlivs on 2010-05-08
It is happening also on a web server directory where I wanted to apply ownership user:www-data and mode 640. After a modification files become owned by user:user and not readable by the web server any more.

---

