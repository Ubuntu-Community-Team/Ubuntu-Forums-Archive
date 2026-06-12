---
title: "nx server on ubuntu"
date: 2007-02-24
forum: Server Platforms
---

### Post by edoras81 on 2007-02-24
i setup freenx as i found like this:

> 
 FreeNX is a system that allows you to access your desktop from another machine over the internet. You can use this to login graphically to your desktop from a remote location. One example of its use would be to have a FreeNX server set up on your home computer, and graphically logging in to the home computer from your work computer, using a FreeNX client.

Installing the FreeNX server in Ubuntu

You need to add the following source list to your /etc/apt/sources.list file

sudo gedit /etc/apt/sources.list

If you are using Ubuntu Dapper you need to add the following lines

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

Once you add above sources you need to save and exit this file now you need to

You need to authenticate these packages using the following command

wget [http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg](http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg) -O- | sudo apt-key add -

Once you add above sources you need to save and exit this file now you need toYou need to authenticate these packages using the following command

wget [http://seveas.theplayboymansion.net/seveas/1135D466.gpg](http://seveas.theplayboymansion.net/seveas/1135D466.gpg) -O- | sudo apt-key add -

Now you need to update the source list using the following command

sudo apt-get update

Install Freenx server

sudo apt-get install freenx

this will complate all the required packages for freenx.

One more important note is you have to install ssh package in your ubuntu machine because by default freenx server will use port 22 for communicating over ssh.

Install ssh in ubuntu

sudo apt-get install ssh

On some machines or networks, port 22 may be blocked or not allowed. For example, some providers block port 22. To make the SSH server listen on port 877, you can do the following

Edit the file /etc/ssh/sshd_config

sudo gedit /etc/ssh/sshd_config

Find

Port 22

and change it to

Port 877

You then need to restart SSHD. Try

sudo /etc/init.d/ssh restart

Edit the file /etc/nxserver/node.conf

sudo gedit /etc/nxserver/node.conf

Find

# The port number where local &#8217;sshd&#8217; is listening.

#SSHD_PORT=22

and change it to

# The port number where local &#8217;sshd&#8217; is listening.

SSHD_PORT=877

link:[http://www.debianadmin.com/securely-administring-remote-machines-using-freenx-in-ubuntu.html](http://www.debianadmin.com/securely-administring-remote-machines-using-freenx-in-ubuntu.html)

but i can coneect shh but i couldn connect via NX.
what did i missed?
should i need configuration something too ?
is there any succesfull instruction for nxserver for dapper?
i am using dapper. 

regards..

---

### Post by eric_stewart on 2007-02-25
> **edoras81 said:**
> i setup freenx as i found like this:


link:[http://www.debianadmin.com/securely-administring-remote-machines-using-freenx-in-ubuntu.html](http://www.debianadmin.com/securely-administring-remote-machines-using-freenx-in-ubuntu.html)

but i can coneect shh but i couldn connect via NX.
what did i missed?
should i need configuration something too ?
is there any succesfull instruction for nxserver for dapper?
i am using dapper. 

regards..
I'm using NX Server on my Edgy installation.  Had it working under Dapper too.  I installed the NX Server via downloading/installing the RPM directly from the NoMachine site.  I ran into some issues with the NX Client....had to upgrade it since it definitely had some issues connecting to the NX Server when 1st installed.  Other than that though, I had no real issues.  Maybe the secret *is* installing directly from the RPM.

I have some information about my travails with NX Server on my blog:  [www.breezy.ca](www.breezy.ca)  Please feel free to email me at [email]eric@breezy.ca[/email] if you have any questions.

Eric

---

### Post by st0kes on 2007-03-10
Sorry but these instructions don't work. This is what happens:

```
wget http://free.linux.hp.com/~brett/seve...x/1135D466.gpg -O- | sudo apt-key add -

--13:48:03--  http://free.linux.hp.com/~brett/seve...x/1135D466.gpg
           => `-'
Resolving free.linux.hp.com... 192.25.206.17
Connecting to free.linux.hp.com|192.25.206.17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:48:04 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.
```

---

