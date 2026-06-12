---
title: "Secure Online Folder"
date: 2008-05-07
forum: Security
---

### Post by TorchlightJay on 2008-05-07
Hello,

I am currently running a desktop with Ubuntu 8.04 on it. This is my personal desktop, I use it day in and day out usually and it has most of my files. I want to put my important common files on this desktop and turn it into a file server but still use it like a regular computer. I have a notebook that I carry around and it has a smaller hard drive than my desktop so I'd like to keep my files on the desktop and access it remotely. I have two questions.

One) Is it a good idea to use a computer regularly and have it as a file server?

Two) How can I create an online file folder and make it secure/encrypted? What tools do I need? What is the procedure/theory behind it? Are there any good tutorials? 

Any advice will help. Thanks everyone.

---

### Post by pytheas22 on 2008-05-07
1. I don't see why you couldn't use it as a file server.  The only downfalls are slower access times (because of network) and increased strain on your hard disks, but I don't think either would be a huge problem.

2. this depends on what exactly your needs are.  Probably the best way to securely access files remotely is by using ssh (there are loads of information on this if you search for it, and it's extremely easy to set up).  ssh, however, will only allow you to log in on to a remote machine via the command line, not graphically, although you can use it to open an X server and run nautilus without too much trouble (i.e. you effectively can use ssh for a graphical connection if you want, although there are other more efficient, though not necessarily more secure, ways of doing this).  The benefits of this are that it's efficient and fast, especially if you are not using a graphical interface, and it's an encrypted, secure connection--meaning that only people who know your password (or, if you want to be even safer, your ssh key) can access the connection, and any traffic that gets intercepted will be unreadable to people without the key.

Otherwise I'm not sure how secure you can make a connection to a remote folder.  I think there are ways to encrypt samba, but I can't tell you how myself.  If the connection is only going to be on your local network and you're using wireless, a good WPA key should keep everything private, at least for people who don't know the key.  If you need to access your file server from out on the Internet somewhere, it will be more difficult to keep things secure.

---

### Post by TorchlightJay on 2008-05-07
Cool, I currently use SSH and I also use webmin, either is fine but I was hoping I could do a more efficient way. I currently own a domain via godaddy and I was going to point it to this machine (yes I have a static IP). I was wanting to set it up to where I can access the folder easily in a graphical setup from my file manager or maybe a better web interface. Is this at all possible. 

Thanks.

---

### Post by Biochem on 2008-05-07
I personnaly use openvpn to connect to my computer with NFS as a remote server. IMHO it works better than sshfs (trouble with saving files).

Also having a Dyndns account helps a lot when the isp change my IP adresse

---

### Post by pytheas22 on 2008-05-07
> Cool, I currently use SSH and I also use webmin, either is fine but I was hoping I could do a more efficient way. I currently own a domain via godaddy and I was going to point it to this machine (yes I have a static IP). I was wanting to set it up to where I can access the folder easily in a graphical setup from my file manager or maybe a better web interface. Is this at all possible.

In that case, if you're going to also be using your machine to host a website, you might also want to take some general security precautions to keep it safe.  Make sure you have a good firewall, and you might want to look into something like [OSSEC]("http://www.ossec.net") to monitor and auto-respond to attacks from the open Internet.

Otherwise, you could easily create a basic interface for accessing your files via the website by dragging (or symlinking) whatever you want to have available remotely into the /var/www directory.  This would make them accessible by calling your domain name in a web browser.  I'm sure there are prettier ways to do this, as well.

---

### Post by TorchlightJay on 2008-05-07
Sounds like a cool idea. If i were to do this, would I install NFS server and OpenVPN on the machine that I am trying to access? Is it relatively easy to setup?

---

### Post by pytheas22 on 2008-05-07
> Sounds like a cool idea. If i were to do this, would I install NFS server and OpenVPN on the machine that I am trying to access? Is it relatively easy to setup?

You mean if you were to access your files in /var/www via a website, or if you were to set up NFS and OpenVPN (which the more I think about it is probably a more flexible and safer solution than running a web server just to access your personal files)?

---

### Post by TorchlightJay on 2008-05-07
Well I'd rather be secure. I do want to run Apache2 on this machine but not to host a public site. It's more or less just for me and maybe a few friends. But that is separate more or less from what I am trying to accomplish in terms of my file sharing. If there were a web interface for openVPN or something, that'd be cool but I want the most secure and flexible solution for my situation.

---

### Post by Biochem on 2008-05-07
Openvpn is very secure. It will create an encrypted virtual lan. Then what you do with it or how you share your data on it is just the same as when you connect to your router. Samba and nfs have to be configured to listen to the vpn ip adress and I guess it's the same thing for apache.

---

### Post by hyper_ch on 2008-05-08
well, if anyone get hold of the other computer then all your data is not secured... is that a problem for you? If so, then you will have to work with file encryption.

---

### Post by TorchlightJay on 2008-05-08
Exactly. That's my issue. I want to be able to access my data but I want it to be safe. My concern is that if I do a hard drive encryption, I won't be able to access my files. I am not sure how encryption works in that aspect. By locking the files/hard drive, wouldn't that cause the files to be inaccessible via online interaction? Maybe I am wrong or seeing it the wrong way. 

Now let's say I want to setup OpenVPN, am I able to set it up on this machine or do I have to set it up on another machine in my office (I have a server and a second workstation)? What client software do I need to connect to the machine? Which should I go with, NFS or Samba and do I set that up on the machine? 

When dealing with encryption, what software do I want to use? Also, does anyone know of good tutorials for any of this? Some sites make no sense, some are alright, I prefer the one that is alright. 

Thanks everyone.

---

### Post by hyper_ch on 2008-05-08
what kind of control do you have over the remote computer?

---

### Post by Biochem on 2008-05-08
> **TorchlightJay said:**
> 
Now let's say I want to setup OpenVPN, am I able to set it up on this machine or do I have to set it up on another machine in my office (I have a server and a second workstation)? What client software do I need to connect to the machine? Which should I go with, NFS or Samba and do I set that up on the machine? 
Thanks everyone.

You would have to setup a openvpn server on your file server AND setup client on every machine that would connect to it. So it is not a viable option lets say if you wanted to connect from a random computer (like school lab, etc) for that sftp (a ssh server) is a better option. Also sftp can be used with winscp portable so you don't need to install any software on the client. However you would have to bring the file locally to work on it.

Have a look at **_[www.openvpn.org](www.openvpn.org)_** for more information
For the most simple setup (1 desktop and 1 laptop):
[http://openvpn.net/index.php/documentation/miscellaneous/static-key-mini-howto.html](http://openvpn.net/index.php/documentation/miscellaneous/static-key-mini-howto.html)

But you can also scale up to a 1 server and many clients really easily (requires a lot more reading though).

---

### Post by TorchlightJay on 2008-05-08
I think I understand what you are getting at. I think I'll set up both environments. I want to use openVPN as a main thing (i really only want a few computers to have access) but maybe the sftp as a fallback or for just general files that I publicly want to share (but be secure on that same token). What software can I put on my ubuntu server to setup the sftp?

Thanks

---

### Post by Biochem on 2008-05-08
sftp is just a file transfer alyer on top of ssh, a remote access and management protocol. Here is some interesting reading.

To install and configure:
[https://help.ubuntu.com/community/SSHHowto#head-90d4cebb755ef6257069e1302c37455999176d82](https://help.ubuntu.com/community/SSHHowto#head-90d4cebb755ef6257069e1302c37455999176d82)

For More advanced option (I personally sware on key authentification):
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

To jail user in their home folder and restrict shell access:
[http://ubuntuforums.org/showthread.php?t=451510&highlight=sftp+chroot](http://ubuntuforums.org/showthread.php?t=451510&highlight=sftp+chroot)

---

### Post by hyper_ch on 2008-05-09
Secure file transfer/vpn does not solve all the issues... anyone who can get access to that machine will then have the data available. So, if you can use disk encryption on there... either encrypt a partition with dm_crypt/lusk or make an encrypted file container with truecrypt.

---

### Post by Vivaldi Gloria on 2008-05-13
> **TorchlightJay said:**
> I was wanting to set it up to where I can access the folder easily in a graphical setup from my file manager or maybe a better web interface. Is this at all possible. 

Thanks.

I regularly use sshfs to mount a remote directory as a local one. I use the command

```
sshfs user@remote.machine:/remote.dir /where/to/mount -o allow_other
```

Now the remote directory becomes no different than a regular local directory.

Very easy.

---

