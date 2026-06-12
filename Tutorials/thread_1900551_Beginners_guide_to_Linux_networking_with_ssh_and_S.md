---
title: "Beginners guide to Linux networking with ssh and SFTP"
date: 2011-12-26
forum: Tutorials
---

### Post by JRV on 2011-12-26
**Sharing files over a network Ubuntu to Ubuntu:**

First you will need to install the openssh-server on every computer you wish to access remotely. The client is installed by default.

You can install it with the command:
```

sudo apt-get install openssh-server

```


Or you can find it in the software center.

**To establish a connection through the GUI:**

Click an empty spot on the desktop to set the global menus. Move the cursor to the upper left and the global menus will appear.

Click on the "File" menu then select "Connect to Server".

Set "Type" to SSH, then fill in the rest of the blanks.

If you are going to create a bookmark for this connection I would recommend not checking the "Remember this password" at this time, if you do it later you will have more options. If you do not wish to create a bookmark you can remember the password or not, which ever you prefer.

Next click the Connect button.

You will get a message that says "The Identity of the remote computer (HOSTNAME (IP address)) is unknown." click "Log in Anyway".  This message will only appear the first time you make the connection.

**To establish a connection from the command line:**

```

nautilus sftp://USER_NAME@HOST_NAME/PATH

```

You will get a message that says "The Identity of the remote computer (HOSTNAME (IP address)) is unknown." click "Log in Anyway".  This message will only appear the first time you make the connection.

When the log in window appears enter your password and choose whether you want the computer to remember it. then click the Connect button.

**Creating a bookmark for your network connection:**

Open your home directory in nautilus.

In the left hand column under Network you will see a line that begins with "SFTP", right click it, and select "Add Bookmark".

A new heading called "Bookmarks" will appear at the top of the left column.
Under it will be the bookmark you just created.

Now you will probably want to right click on the bookmark to rename it.

**Unless you want Windows machines to have access to the Ubuntu machines you do not have to mess with samba.**

--------------------

**Using the ssh command to run a program on the remote computer:**

You can use the ssh command to run a program on another computer on your network and display it locally.

The command looks like this:
```

ssh -X -4 USER_NAME@HOST_NAME PROGRAM

```

The "-X" parameter lets you run graphic programs.  If you do not include it your ssh session will be command line only.  The "-X" must be upper case.

The optional "-4" parameter Forces ssh to use IPv4 addresses only. It speeds up the connection to include it.  

The optional PROGRAM is the program you wish to run. 

Try using the ssh command without specifying a program.
Then try running the xclock program on the remote computer and display it locally.

If you reinstall Ubuntu on one of the computers on your network and use the same host name the keys used by ssh will be wrong.  The easiest way to fix this is to delete the /home/USER_NAME/.ssh/known_hosts file.  Then you will get the first time connection message again and after that everything should work.

This is a simple demonstration of what can be done with the openssh client/server.  It covers most of what you will need for a home network.  If you need more detailed information look in the official Ubuntu documentation here:

[https://help.ubuntu.com/11.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/11.10/serverguide/C/openssh-server.html) 

Or check out the ssh man pages with the command:
```

man ssh

```

Tested on Ubuntu 11.10 (Oneiric)

---

