---
title: "Web access to Server"
date: 2008-04-03
forum: Server Platforms
---

### Post by chrisbish on 2008-04-03
Basicly what I have done is set up a Samba file sharing server on my home network. Everything works fine and now i would like to know if there is a way to access it and copy & past files from & to the server from work/school etc.

Is this possible and are there any guides on how to do it?

I was thinking ftp using a dyndns but i dont know were to start.


>  happypig:

lightweight server
I've got an old 500mhz pentium III machine that I'd like to use as a lightweight server.
I'm thinking of installing ubuntu and samba (and anything else I find out I need as I go along).
Once installed and working it's probably going to go into the garage (I will administer it using VNC)and I'd like it to be as frugal as possible; would it be possible to remove the graphics card to save power and for it still to work ?

I also plan on sticking my server once evrything is sorted out in the roof of my garage.
It's quite dusty up there and in the summer its very humid. Would water cooling be a good idear?

---

### Post by ryazkhan on 2008-04-03
I would say SSH is the best way to dowload/upload files securly. You can setup VPN server in ur ubuntu server and then access it from your school etc, this way you will be able to browse your shares etc and will be able to dowload/upload copy&past to/from etc. FTP by default use port 21 and it is not secure because there is no encryption and it send/receive clear text anyone can see that and you dont want to do that. Good point to start is SSH :)

---

### Post by njparton on 2008-04-03
Yep, install openssh-sever in ubnutu and then an ssh client on the computer wherever you want to access it from. putty is a good ssh client for windows.  Are you allowed to install stuff at work or school?
 
I wouldn't put your sever in a dusty and hot/humid environment if you could help it.

---

### Post by chrisbish on 2008-04-03
ok so SSH and VPN thankyou very much

i dont supose you could link me to some good guides on how to do this?

Is this one any good? [http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)

---

### Post by chrisbish on 2008-04-03
> **njparton said:**
> Are you allowed to install stuff at work or school?


 I was planing on using some portable .exe file like putty

---

### Post by Dr Small on 2008-04-03
+1 for SSH.
Here is a wiki article on SSH:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

And Advanced SSH:
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Also, try to keep the server in a cool atmostphere of around 30-40% Humidity.

Dr Small

---

### Post by chrisbish on 2008-04-03
are there any easy copy/past kind of guides , im no good in the terminal.

so far i have done this [http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)

---

### Post by hyper_ch on 2008-04-03
ssh:

(1) forward port 22 form your router to your fileserver

(2) setup openssh-server on the fileserver
```

sudo apt-get install openssh-server

```

(3) connect to it with a ssh/scp capable program.
- On linux I love Konqueror very much. Enter there in the address bar:  fish://user@ip
- On windows I like WinSCP a lot (freeware)

or

on linux you can mount that remote fileserver into your linux tree with SSHFS

---

### Post by Dr Small on 2008-04-03
gFTP can also connect via SSH with the SSH2 Protocol, and then of course, you can connect to it in the terminal with:
```
ssh user@host
```

Dr Small

---

### Post by chrisbish on 2008-04-03
i can't seem to forward port 22 the router says it's in use.

---

### Post by chrisbish on 2008-04-03
do i just give it another port number?

---

### Post by hyper_ch on 2008-04-03
edit the ssh config file... either it's a file in /etc or /etc/ssh* somewhere

---

### Post by chrisbish on 2008-04-03
ok ive change the port number in teh config file

im using WinSCP.

for the username i presume i enter my username i use to login and the password for it.
what about this private key file do i need this?

---

### Post by chrisbish on 2008-04-03
all i get is a network conection error. maybe this is because im using a computer on my network and trying to use the router ip address.

ill try this tomorro on a computer out side the lan.

in the hostname field would i be able to enter a dyndns url in there? as i have a dynamic ip address which it gets given randomly every week or so. this would then be easyer that remembering all the new i.p numbers.

---

### Post by hyper_ch on 2008-04-03
well, if you've changed the port name you need to restart the ssh server an yuo need also to tell winscp to use the new port...

as for login, you use your normal system username and password from teh machine you want to log into.

---

### Post by chrisbish on 2008-04-03
i did restart it and thats when i got the error
i changed the port and used my username and password i use for login in too.

im still getting that netwrok error: connection refused

---

### Post by ryazkhan on 2008-04-18
I am sure you got SSH working up to this point but if you still looking here are codes to do that. It will install SSH serve for you
```
sudo apt-get install openssh-server
```
To install client for SSH on ubuntu
```
sudo apt-get install gftp 
```
this program can use many port so you have to specify which port you want to use before connection to you server
For window follow this:

[https://www.hvcc.edu/clc/documentation/phoneaccess/secureshell.html]("https://www.hvcc.edu/clc/documentation/phoneaccess/secureshell.html")
I have bunch of files like this which are just ready to go I can let you use those if you still not getting it

For VPN Server setup follow this:

[http://pigtail.net/nicholas/pptp/]("http://pigtail.net/nicholas/pptp/")

What version of ubuntu you are using ?
Port forwarding can be done by going into your route and all port 22 if you want to use ssh to your ubuntu machine which has ssh server installed on it
connection refused:
are you getting any other connectivity to internet?

---

