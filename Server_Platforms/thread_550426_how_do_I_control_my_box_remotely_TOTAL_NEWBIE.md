---
title: "how do I control my box remotely? TOTAL NEWBIE"
date: 2007-09-13
forum: Server Platforms
---

### Post by bone2006 on 2007-09-13
I installed ubuntu server on a system and I'm ready to learn on getting it going.  The problem is that I'm sharing a keyboard, mouse and monitor.  

How would I set it up so that I can do all the work remotely?  My setup is that I'm going through a buffalo router with dd-wrt on it and I'm on the other computer now and I'm able to ping it.

I haven't done anything to the system, just installed it as LAMPS and I made sure I could ping it from another computer, which I can.

Thanks in advance

---

### Post by inphektion on 2007-09-13
just install openssh server and ssh into it.  Being a server you don't need any remote GUI access.

---

### Post by bone2006 on 2007-09-13
thanks

---

### Post by tgalati4 on 2007-09-13
>ssh -2 -Y yourusername@yourcomputername

(password for yourusername)

>firefox &  (assuming your are running on another Linux machine with an Xserver running)

If ssh is not working, then reestablish your password on the server machine:

>sudo passwd

>sudo passwd yourusrname

---

### Post by scrooge_74 on 2007-09-13
example your user on client is john and you have a john user in the server you can go ahead and ssh clientip and give the password for john user in the server

If you dont have a john user in the server, but a steve user you then type

ssh steve@ipofserver and give steve's password

---

### Post by bone2006 on 2007-09-13
Thanks I was able to get in with
ssh -l username ip

I'm guessing this is good enough?  Thanks so much every one

---

### Post by scrooge_74 on 2007-09-14
Sure you can latter on get onto doing remote desktop using ssh is lots of fun to be able to work from any PC around your network

---

### Post by bone2006 on 2007-09-14
I'm having an issue with editing file and uploading files that have permission on the ubuntu server edition.  I never created a root account, because I've been using sudo.  Is it recommended to create a root account for ubuntu server editition?

I've been loggin as user with the terminal ssh and I do type in sudo when needed, but for transferring files I've been using filezilla, but I'm having issues since I'm not logged in as root, not sure if there's a way around this or if I should create the root user?

---

### Post by inphektion on 2007-09-14
ssh in as the user ( not root ).  Once in you can type sudo -i <enter> and then your password and you are effectively root.  then do whatever you like.  No reason to create a "root" acct.

---

### Post by bone2006 on 2007-09-14
That's not such a problem, what about transferring file?  I

---

### Post by scrooge_74 on 2007-09-16
scp source_file  targetuser@server:/home/destination

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/scp](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/scp)

---

### Post by eggdeng on 2007-09-16
You can also do this in graphical mode by going to Places->Connect to Server and filling in the appropriate values for
Service type: SSH 
Server: [remote_IP]
User: [remote_user]
This will mount the remote box on your desktop.

---

### Post by scrooge_74 on 2007-09-16
correct, but sometimes is just quicker to do from the command line

---

### Post by bone2006 on 2007-09-16
> **eggdeng said:**
> You can also do this in graphical mode by going to Places->Connect to Server and filling in the appropriate values for
Service type: SSH 
Server: [remote_IP]
User: [remote_user]
This will mount the remote box on your desktop.

I've been looking hard for this in linux mint, which is what I'm mostly using when I connect to the ubuntu server and can't seem to find this "places" or anything about connecting to server.  When it opens up is there a name for this utility, so that I can try to type it in the terminal and see if it's install.

Thanks

---

### Post by scrooge_74 on 2007-09-16
you can also set the exports on the server so you can mount the drive on your client PC

---

### Post by eggdeng on 2007-09-16
> Is there a name for this utility? It seems to be a well-kept secret. You might find it though in Add to Panel -> Utilities.

---

### Post by bone2006 on 2007-09-16
> **scrooge_74 said:**
> you can also set the exports on the server so you can mount the drive on your client PC

how would you go about doing that please?

I tried adding to panel, it adds, but as soon as I enter information it disappears when I click connect and the help has been removed

---

### Post by eggdeng on 2007-09-16
When the the dialogue box disappears, if you have entered the information correctly, you should see a new folder on your desktop. 
Another alternative is to use sshfs to mount the remote file locally. There is a simple howto at [https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS")

---

### Post by bone2006 on 2007-09-16
Thanks for the help
It didn't show the shortcut on my desktop, but since it was mounted I went and navigated and found in.  
Appreciate it.

---

