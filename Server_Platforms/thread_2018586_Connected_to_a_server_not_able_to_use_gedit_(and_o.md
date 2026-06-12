---
title: "Connected to a server: not able to use gedit (and other graphical interfaces)"
date: 2012-07-06
forum: Server Platforms
---

### Post by Soonick on 2012-07-06
Hello to everyone.
Let me start off by saying I'm not familiar with servers and shells, but I have a very general question.
I am starting to work in a cluster of a given institute and for the first time I have connected to a server to "surf" between the network and the data.
So, for the most, I have just written on the terminal some scripts that I have found in the general instructions of the system.
However, when I am connected with my laptop in this server, I can not use graphical interfaces/tools.
For example, I can not open a document by using gedit, or gv.
I post the returned errors:
```

isdc_rev2> gedit isgri_gc.lst 
(gedit:31615): Gtk-WARNING **: cannot open display: 
isdc_rev2> gv isgri_gc.lst
gv: Unable to open the display.

```

Since I have to use other graphical tools, and I can not until now, my question is: do you know a possible explanation for this kind of trouble?

Sorry for my inaccuracies.
Thanks in advance.

---

### Post by hawkmage on 2012-07-06
I assume that you are "logging in" to the server from a different system via ssh.  

If this is the case then you will need to be running an X server your local system and use X11 tunnelling on the ssh connection.  

If your local system is Windows try installing XMing for the X server and if you are using PuTTY for your ssh client then either edit the connection profile you use to enable X11 tunnelling or if you are starting PuTTY from the command line use the -X option to enable it.

If your local system is Linux then just use the -X option on fht essh commend to enable X11 tunnelling.  

If you are running Apple OS X you will first make sure that you have the X11 server installed on your Mac and then use the -X option on the ssh command.

---

### Post by Soonick on 2012-07-06
Hi hawkmage.
Thank you for the reply.

You are right: I log in via ssh.
I use ubuntu on my laptop, so I log in via the command:
```

ssh -XY username@servername
```
I use this "formula" just because someone told me to do that.

What do you mean when you say:
" If your local system is Linux then just use the -X option on fht essh commend to enable X11 tunnelling" ?

---

### Post by trundlenut on 2012-07-06
> **Soonick said:**
> Hi hawkmage.
Thank you for the reply.

You are right: I log in via ssh.
I use ubuntu on my laptop, so I log in via the command:
```

ssh -XY username@servername
```
I use this "formula" just because someone told me to do that.

What do you mean when you say:
" If your local system is Linux then just use the -X option on fht essh commend to enable X11 tunnelling" ?

I would suspect that the server you are connecting to doesn't have an x-server installed, therefore gedit etc. won't work.

Nano is a CLI alternative to gedit which is straightforward to use, there are others but we may find ourselves neck deep in opinions if we go down that route.

---

### Post by Cheesehead on 2012-07-06
Try the 'sshfs' package. It will make the server files appear on your system like a another drive. You can use your local applications (like gedit) to manipulate those files.

No changes are needed on the server.
Do the following on your local machine (the client):
```
 # Setup
sudo apt-get install sshfs                # Install the sshfs package
sudo gpasswd -a $USER fuse                # Add yourself to the fuse group
sudo mkdir /media/server-mountpoint       # Create the mountpoint

 # Daily use
sshfs username@servername /media/server   # Mount the server files via ssh
 # The server should appear in your file manager. Do your work
fusermount -u /media/server               # Unmount the server files

```

A good tutorial on how to use sshfs is at [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)
- You can add sshfs volumes to fstab, so your server files will appear at login automatically.
- Since the connection will terminate is idle too long, some users add a keepalive signal.

---

### Post by hawkmage on 2012-07-06
> **Soonick said:**
> Hi hawkmage.
Thank you for the reply.

You are right: I log in via ssh.
I use ubuntu on my laptop, so I log in via the command:
```

ssh -XY username@servername
```I use this "formula" just because someone told me to do that.

What do you mean when you say:
" If your local system is Linux then just use the -X option on fht essh commend to enable X11 tunnelling" ?
Why are you using -XY?  -X enables X11 tuneling using xauth for security.  -Y enables a trusted X11 tunneling.  I am not sure what the effect of using both will be.

What I was trying to say was that if your laptop is running Linux you just need to use the -X option on the ssh command when you connect to the server to enable X11 tunneling.

---

### Post by Soonick on 2012-07-07
Thanks a lot for the suggestions.
However, some problems remain.
The sshfs setup part is ok:
```

nedu@nedu:~$ sudo apt-get install sshfs
[sudo] password for nedu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  sshfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 43,7kB of archives.
After this operation, 160kB of additional disk space will be used.
Get: 1 http://it.archive.ubuntu.com/ubuntu/ lucid/main sshfs 2.2-1build1 [43,7kB]
Fetched 43,7kB in 0s (74,7kB/s)
Selezionato il pacchetto sshfs.
(Lettura del database... 198324 file e directory attualmente installati.)
Estrazione di sshfs (da .../sshfs_2.2-1build1_amd64.deb)...
Elaborazione dei trigger per man-db...
Configurazione di sshfs (2.2-1build1)...
nedu@nedu:~$ sudo gpasswd -a $USER fuse
Aggiunta dell'utente nedu al gruppo fuse
nedu@nedu:~$ sudo mkdir /media/server-mountpoint
nedu@nedu:~$

```But I receive error messages when I try to mount the server files:
```

nedu@nedu:~$ sshfs username@servername /media/server
missing host
see `sshfs -h' for usage
nedu@nedu:~$

```What am I going wrong? O:)
Maybe do I need to be already connected to the server before to execute the setup commands?
Or maybe is $USER just an example for my username?

---

### Post by SeijiSensei on 2012-07-07
Might I suggest simply becoming comfortable with a text-based editor like nano?  Log into the server with SSH, then run "nano /path/to/file".  If you're editing a file owned by the administrative, or "root" user, you need to use "sudo nano /path/to/file", and your account must have administrative privileges on the remote machine.

Most all of the commands in nano consist of "control-key" sequences, where you hold down Ctrl and hit a key.  "Ctrl-X" exits, for instance.  The control key will be represented by the carat ("^") in the help at the bottom of the nano screen.  So "Ctrl-X" will appear as "^X" there.  

Nano is not my favorite editor, but it's a good choice for novices because it has those help listings.

---

### Post by Soonick on 2012-07-07
Hi Sensei.
I know nano, and I have already edited some documents.
But I also need other graphical tools, not only for text documents, but for analysis tools that need a graphical environment.
Thank you anyway.

---

### Post by |{urse on 2012-07-07
Yeah, as mentioned abouve you're going to need to ask the administrator to install xserver and enable x tunneling.

---

### Post by Soonick on 2012-07-08
Nevertheless, I think that other users connected on the same server are capable to use graphical tools.
So I don't think it is a problem of the kind you describe.
But I am a very beginner, so I will try to ask.

Thank you.

Ok, maybe some further useful informations.
If I login with -X, then I receive the following error:
```

Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.

```

Instead, if log in with -Y I receive only:
```

Warning: No xauth data; using fake authentication data for X11 forwarding.

```

I hope this can be useful.

PS:
maybe also this:
```

> xterm
xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set

```

---

