---
title: "View remote network via SSH &quot;proxy&quot;?"
date: 2007-05-24
forum: Server Platforms
---

### Post by fyl2u on 2007-05-24
Hi,

I'm on my home computer running Feisty Fawn. (I'll call it PC 1)

At work I've set up another computer, also with FF, (PC2) and have used the terminal on  PC1 to connect to PC2 via SSH.

Is it possible to use PC2 as a proxy / gateway to access another computer (PC 3) on the same network?

I've got some files that I need on PC3 that are shared on the work network but the SSH is set up to direct to PC2.

Thanks in advance.

Phil

---

### Post by ninocass on 2007-05-24
You could SSH into PC2 and the SSH into PC3

or

you could use SSH to tunnel an FTP/SSH connection to the remote computer i think that would work

---

### Post by mitch.c on 2007-05-24
If you use ssh on all your machines, you can use agent fowarding to get from one machine through another. I can access 3 of my machines via ssh from the Internet in this manner. For example:

Laptop -> Internet -> PC-1 -> PC-2
Laptop -> Internet -> PC-1 -> PC-3

My router forwards all ssh requests to PC-1

I make my ssh connection from Laptop to PC-1. Agent forwarding lets me then connect from my PC-1 ssh session to PC-2 or PC-3

In my case I have the following entry in ~/.ssh/config on Laptop
```
# ~/.ssh/config
ForwardAgent yes
```

Then, I use ssh-add to add my key to the ssh-agent on Laptop for ssh sessions.

Is that what you had in mind?

---

### Post by fyl2u on 2007-05-24
Unfortunately there's no ssh on PC3.

I've just managed to get it using smbclient and I can see the files I want, but they've got spaces in the filename.

I presume I have to use the "get" command to transfer them?

It's trying but I can't seem to get around the problem of there being spaces in the filenames.


P.S. thanks for your speedy replies.

---

### Post by ninocass on 2007-05-24
Edit: just read your spaces problem you need to delimit them so

the quick brown fox

becomes

the\ quick\ brown\ fox



Okay ive just tested SSH tunneling on my computers for VNC.

Ill show you an example for FTP on PC3 with ip 10.0.0.3


Set up putty on your work computer with the following tunnel

sourceport :123
destination:10.0.0.3:21
Destination: Local

now SSH into PC1 using this tunnel

On your work pc start an FTP client and connect to

localhost:123

What will happen is putty will take over the ftp connections and fire it down the SSH tunnel where it gets redirected to 10.0.0.3

great thing is as its over SSH its all encrypted and you dont need to open any extra ports on your firewall

:)

---

### Post by fyl2u on 2007-05-24
> **ninocass said:**
> Edit: just read your spaces problem you need to delimit them so

the quick brown fox

becomes

the\ quick\ brown\ fox



oh, really? so it's not "%20" for a space?

what would it be for...

the quick, brown, fox

?

the\ quick,\ brown,\ fox 

or do the commas need translating somehow too?


edit: hmmn, nope... NT_STATUS_OBJECT_NAME_NOT_FOUND opening remote file \shared\the\

---

### Post by dbott67 on 2007-05-24
You could do as ninocass says (ssh into PC2 and then from PC2, ssh into PC3).  Then use scp (secure copy to move files to and 'fro) -or- you could use [NX Machine]("http://www.nomachine.com/download.php") to connect to your work machine and then use VNC Viewer to connect to the desktop of the other computer (Windows, Linux, OSX, etc).

When I'm at work, I use the NX Client to connect to my Ubuntu computer at home.  From there, I use [WinSCP]("http://winscp.net/eng/index.php") to move files back and forth; I also use VNC Viewer to connect to my other machines on my home network (XP, OSX, CentOS).

I prefer NX over tunneling VNC over SSH because it's much faster.

All of this happens securely over port 22 using SSH.

-Dave

---

### Post by ninocass on 2007-05-24
if your access the files in linux you should be able to type the first few chars and then tab to auto complete.  to practise make a files in your home directory using gnome call it "test file , , " then go into the terminal type tes and then press tab it will autocomplete to:

[code]
 cat test\ file\ \,\ \,
[\code]

TBH samba shares are more hassle than theyre worth id just set up an FTP and tunnel over DNS more secure

---


the advantage of the tunneling is its 1 step, only 1 connection plus if you save it in putty you just need to connect :)

---

### Post by fyl2u on 2007-05-24
> **ninocass said:**
> if your access the files in linux you should be able to type the first few chars and then tab to auto complete.  to practise make a files in your home directory using gnome call it "test file , , " then go into the terminal type tes and then press tab it will autocomplete to:

[code]
 cat test\ file\ \,\ \,
[\code]

TBH samba shares are more hassle than theyre worth id just set up an FTP and tunnel over DNS more secure

---


the advantage of the tunneling is its 1 step, only 1 connection plus if you save it in putty you just need to connect :)

For some reason the tab thing doesn't work when I'm in smbclient, I tried that first :-?

It doesn't seem to like using the "\" character in smbclient either - it looks like it thinks it's a directory name.

OK, I'll scrap the smbclient idea.

Is it possible to set up the ftp on it from here or would I have to be at work to do that?

Currently PC2 is set up as an FTP server so when I ftp://[workIPaddress] it takes me to my ftp folder on PC2.

Is that going to make things tricky?

---

### Post by fyl2u on 2007-05-24
P.S. if it's relevant, PC3 is a mac :-)


just to reiterate: PC1 and PC2 are running Ubuntu FF, PC3 is a mac running OSX


edit: I was mistaken - there IS ssh on the mac (PC3)

I've just managed to get in on ssh, but the "dir" command doesn't seem to work :-?

now I'm REALLY confused :-D


edit2: that's because in Darwin it's "ls" not "dir" :-)

getting there I think... :-D

---

### Post by ninocass on 2007-05-24
no when your set the ssh tunnel the localport can be anything it doesnt matter but make it something non standard so a high port is usually good.

You will more than likely need to be at work, what services are running on PC3.

If theres VNC/RDP/SSH you can tunnel those over SSH and RDP into the machine.

---

### Post by Soybean on 2007-05-24
Wait... can you get files from PC3 onto PC2 right now? And if so, how are you doing it?

However it is, you can probably tunnel it over SSH one way or another. Although, you might want to check at work to make sure they don't mind. SSH tunnels into a relatively secure network can make network admins very angry. ;)

---

### Post by ninocass on 2007-05-24
> **Soybean said:**
> Wait... can you get files from PC3 onto PC2 right now? And if so, how are you doing it?

However it is, you can probably tunnel it over SSH one way or another. Although, you might want to check at work to make sure they don't mind. SSH tunnels into a relatively secure network can make network admins very angry. ;)

My motto is if they didn't want it the should have blocked it :D

Im not so hot on macs so i cant really offer any advice on connecting or setting up an FTP service

---

### Post by fyl2u on 2007-05-24
OK, the tab function works now (hooray!)

I typed this from the appropriate directory:

scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.135


192.168.1.135 is the internal network address of the Ubuntu machine, PC2

any idea where it might've copied it to? :-D

I tried adding directory structure to the ip address...


scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.135/home/phil/
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.135/root/home/phil/
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.135/phil/
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc //192.168.135/home/phil/
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.135//home/phil/

but it says "....is not a directory"

...or is there a better way of doing this?

:-d

Thanks again for all your help everyone, sorry for being such a noob :-)

---

### Post by fyl2u on 2007-05-24
> **Soybean said:**
> Wait... can you get files from PC3 onto PC2 right now? And if so, how are you doing it?

However it is, you can probably tunnel it over SSH one way or another. Although, you might want to check at work to make sure they don't mind. SSH tunnels into a relatively secure network can make network admins very angry. ;)

:-)

I AM the network admin :-D


It's a very small (and up til this week, uncomplicated) network :-D

---

### Post by Soybean on 2007-05-24
Heh... I think you may have copied it to a file called "192.168.135" ;)

You need a colon in between the server and the path for scp.

```
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.1.135**:**/home/phil/
```
Might also need a username. 
```
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc phil@192.168.1.135**:**/home/phil/
```

Edit:
> **fyl2u said:**
> I AM the network admin :-D
Heh...well, then, you probably don't have to worry about it. ;)

---

### Post by ninocass on 2007-05-24
a nice SCP tutorial

[http://www.sherryneal.com/weblog/archives/000089.php](http://www.sherryneal.com/weblog/archives/000089.php)

---

### Post by fyl2u on 2007-05-24
> **Soybean said:**
> Heh... I think you may have copied it to a file called "192.168.135" ;)

You need a colon in between the server and the path for scp.

```
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc 192.168.1.135**:**/home/phil/
```
Might also need a username. 
```
scp The\ quick\ -\ brown\,\ fox\,\ jumped\ over.doc phil@192.168.1.135**:**/home/phil/
```

Edit:

Heh...well, then, you probably don't have to worry about it. ;)

aha - a new error message now :-)

ssh: 192.168.135: No address associated with nodename
lost connection

---

### Post by dbott67 on 2007-05-24
I don't want to derail the current direction of the thread (i.e. using the command line to scp files back & forth), but if you still have troubles & if you have Gnome installed on the linux machines, you can use gFTP to copy files via SCP.

Here's a screenshot of my Ubuntu box (feisty) connected to OSX (192.168.1.109) using gFTP.

If you can setup port-forwarding at work to forward some arbitrary port to the OSX client, you can connect directly to it using gFTP.  For example:

1. Forward port 22 to your linux box at work so that you can still access it using SSH or gFTP.
2. Forward port 2222 (or whatever) to port 22 on your OSX box.  

When you're at home, instead of SSHing (or gFTPing) to port 22 on your firewall, connect to port 2222 and you should have access to the OSX box.

-Dave

---

### Post by fyl2u on 2007-05-24
I've got it...


1. from my machine - ssh into PC2:  ssh [ipaddress]
2. ```
scp Phil@192.168.1.2:"~/shared/The\ Quick\ -\ Brown\,\ fox\,\ jumped\ over.doc" /home/phil/tq-bfjo.doc
```

that's got it :-D


thanks for your help everyone, we got there in the end :-D

---

