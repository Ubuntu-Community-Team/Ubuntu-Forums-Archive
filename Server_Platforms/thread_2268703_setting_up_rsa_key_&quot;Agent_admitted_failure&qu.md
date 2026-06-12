---
title: "setting up rsa key: &quot;Agent admitted failure&quot; error"
date: 2015-03-10
forum: Server Platforms
---

### Post by Drone4four on 2015-03-10
I’m trying to get autocomplete to work in my cloud server (DigitalOcean Droplet) using scp from my remote local client.  [This stackexchange conversation]("http://unix.stackexchange.com/questions/33336/how-to-enable-autocompletion-for-remote-paths-when-using-scp") indicates to me that I have to set up an ssh-agent.  Quoting from one reply: > You'll need to have passwordless authentication set up, i.e. with a key that's already loaded in ssh-agent.  So I need to set up rsa.  I found a guide for two tutorials on the DigitalOcean community pages.  [Here is the one I used]("https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets").  I followed it closely.  It worked the first time, but afterwards I decided to start over because I wanted to set my ssh-agent on my server up for the regular user rather than for the root user.  So I reached the conclusion of the guide once again (with the regular user instead of root user) but now it gives me this: ```
$ ssh <server>
Agent admitted failure to sign using the key.
<server>'s password: 
$
```
Please note that I swapped out the real user name and used ‘user’ as a placeholder .  Here is a copy and paste of all the commands I inputted, along with their output (again with sensitive identifying information redacted:
```

$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (~/.ssh/id_rsa): 
~/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in ~/.ssh/id_rsa.
Your public key has been saved in ~/.ssh/id_rsa.pub.
The key fingerprint is:
1c:[redacted]
The key's randomart image is:
+--[ RSA 2048]----+
|   		   |
|      |
|   [redacted] .|
|    		|
|     		|
|      		|
|                 |
|                 |
|                 |
+-----------------+
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1y..........[redacted] ......................................................................................................
$ cat ~/.ssh/id_rsa.pub | ssh <server> "cat >> ~/.ssh/authorized_keys"
<server>'s password: 
$ ssh <server>
Agent admitted failure to sign using the key.
$

```
Anyways, what could I be doing wrong?  I figure I didn’t erase the previous rsa key correctly or something.  I tried setting up for rsa for the root user again, but it gives me the same Agent admitted failure.

---

### Post by darkod on 2015-03-11
I'm not a ssh expert so I may not be able to help much with that error. I assume you googled it?

Just a few points for the future.
1. You never needed to create new key on the local machine. You can use the same key to login to different remote machines and as a different user. You should have used the same key.
2. The best way I have found to transfer a key securely to the remote machine is:
ssh-copy-id user@remotehost
That takes care of everything.

SSH is designed to be a very secure access so be careful trying to change/redo keys etc because it might think someone is trying to hack in and it gets defensive real fast.

What I suggest:
On the local machine go into your .ssh folder and delete all existing key files (unless you have some other keys there you want to keep). Then create a new rsa key of 1024 or 2048 bits, as you wish.
On the remote machine enter as both root and as 'user' and in .ssh delete the authorized_keys file (again, unless there is a key there you want to keep). Then from the local machine try the ssh-copy-id.

Another thing, if you want to do any kind of automation, don't set a passphrase when creating the rsa key. Otherwise you will need some kind of script to send the pass too. Having a pass on ssh key is good practice but it's not used when doing automation.

---

### Post by Drone4four on 2015-03-12
Yes I used Google. That's how I came across the stackexchange correspondence.  

On my local machine I navigated to ~/.ssh and removed all three files present.  I did the same for both .ssh directories as root user and as regular user.  I generated a key and left the pass phrase empty.   From my local shell I inputted: cat ~/.ssh/id_rsa.pub | ssh root@<remotehost> "cat >> ~/.ssh/authorized_keys" . I also tried your ssh-copy-id root@remotehost . The result? On first login it returns:

```
localhost:~$ ssh <remotehost>
The authenticity of host '[ip]' can't be established.
ECDSA key fingerprint is 95: [ redacted ] :b8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '<remotehost>' (ECDSA) to the list of known hosts.
<remotehost>'s password: 
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-46-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Mar 12 21:51:38 EDT 2015

  System load:  0.0                Processes:           98
  Usage of /:   19.2% of 19.56GB   Users logged in:     1
  Memory usage: 37%                IP address for eth0: 192.241.186.74
  Swap usage:   0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/

*** System restart required ***
Last login: Thu Mar 12 21:51:39 2015 from [ ip ]
root@remotehost :~# 
```

Notice that the server still prompts me for a root password? So rather than getting the “Agent admitted failure to sign using the key.” like I used to, its now saying: “Warning: Permanently added '<remotehost>' (ECDSA) to the list of known hosts.” 

I Googled ECDSA and discovered a cryptographic algorithm used to secure connections, similar to rsa.
  
Upon second login, it just asks for a password now and skips everything about ECDSA and there is no trace of that agent admission.  I think this means I am back where I started.  If ssh is behaving defensively, I'd feel sorta foolish asking about how to get around these defenses.

On Google I also found a nifty easy-rsa tool which is a part of the OpenVPN project.  The documentation is detailed, but it looks like I'll have to spend quite a few Sunday afternoons tinkering with easy-rsa before I get to where I want to go.

---

### Post by steeldriver on 2015-03-12
Is it really ssh <remotehost> or is it ssh root@remotehost? if so you will need to generate the keypair for/as root

---

### Post by Drone4four on 2015-03-13
When I typed <remotehost> I meant root@remotehost.  I was inconsistent every time I refereed to my server.  Sorry for the confusion.  I'll be sure to be consistent in the future.  I did generate a key pair for/as root.

---

### Post by darkod on 2015-03-13
Ok, that's progress. The authenticity question is expected when you connect to a host the first time so that's no error. After you say yes and it remembers the host it never asks you again.

The key login still doesn't work hence it's asking you to enter the password. The next thing to check are permissions. SSH is very strict so that it can be safe so it wants the permissions of the .ssh folder to be 700 and of the files inside 600. However ssh-keygen seems not to do that and instead the file permissions are the default of your home folder. To make sure they are correct do the following. I assume you are running commands from your home folder so I am leaving out the ~ in the path.
```
chmod 700 .ssh
cd .ssh
chmod 600 *
```

That should set correct permissions. Try the login now. If it still doesn't work I'm not sure if you need to do the same on the remote host too so that the authorized_keys file has 600 too. You can try that if the above didn't work.

---

### Post by Drone4four on 2015-03-13
I can now ssh into my remote host from my local machine without having to enter a password.  I found a guide called &#8220;[3 Steps to Perform SSH Login Without Password Using ssh-keygen & ssh-copy-id]("http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/")&#8221; by Googling ssh-copy-id.  It was the second link.

Changing permissions wasn&#8217;t necessary. But cheers all the same.  

Thank-you **darkod** + **steeldriver**

---

