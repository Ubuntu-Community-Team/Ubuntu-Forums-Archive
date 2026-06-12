---
title: "Looking for best solution remote user file share (with restrictions ala samba)?"
date: 2009-11-16
forum: Server Platforms
---

### Post by photoman355 on 2009-11-16
Hi 

I'm setting up my first Ubuntu server for my work.  I've setup samba and configured each user/group with the desired level of access for my LAN.  Essentially the users only need to access files, they don't need to run anything.

I want to find the best solution to allow the users secure remote access over the internet but maintain the access restrictions that samba allows.

I installed openssh as a possible solution and have this working but one drawback is users are not locked to the share directories and can see the entire server directory tree.  

Is there any way to lock them to the share directories or is there a better solution for my needs?'

Thanks for your help.

---

### Post by photoman355 on 2009-11-17
Bump

---

### Post by Lars Noodén on 2009-11-17
Why not have them connect directly with Samba?

If you do want to use openssh then you could tunnel the Samba connection.  They'd be connecting via samba to their local machine, and that would be forwarded to the server.


Or if you want to use SFTP, then you can chroot the users as well as lock them into the sftp-subsystem.  

```

Match Group sambausers
  ChrootDirectory /samba/%u
  # or ChrootDirectory /samba/
  ForceCommand internal-sftp
  # PasswordAuthentication no

```

For the example above, you can create a group called samba users and then put those that should connect into that group.  With PasswordAuthentication dset to "no", you can force use of keys for authentication.  

As far as sftp clients go you have obviously the built-in, text-based sftp client they have that came with their os.  

sshfs uses sftp, so that will work.  

For a GUI sftp client, there are FileZilla and Konqueror.  I have heard that Nautilus works, too.  For OS X you have also Cyberduck.

---

### Post by photoman355 on 2009-11-18
Hi Lars, 

Thanks for your reply.  

I'm running 8.04LTS with OpenSSH 4.7p1.  I know there have been some upgrades to openssh since to do with chrooting, is the chrootdirectory function available under my version?

I better explain a bit more about what i'm trying to achieve to check your response is the right solution.

The office will run a local ethernet network where users on cross platform systems (Mainly Win/Mac) can connect to the samba shares.  The samba shares are split into different user groups which give users access to the shares depending on what group they belong to.  

What i'm trying to achive is give these users access to the shares remotely when they are working away from the office and maintain the group permission structure I defined in samba.  The connection will have to be secure and passwords/security keys are a must.

---

### Post by Lars Noodén on 2009-11-19
> **photoman355 said:**
> 
I'm running 8.04LTS with OpenSSH 4.7p1.  I know there have been some upgrades to openssh since to do with chrooting, is the chrootdirectory function available under my version?


No.  File a bug report asking for a [backport](https://help.ubuntu.com/community/UbuntuBackports) to LTS.  Post the link here.  In the grand scheme of things it's a fairly small task for a package maintainer.

Alternately, you can try [apt-pinning](https://help.ubuntu.com/community/PinningHowto) to grab openssh-server from a more recent edition of Ubuntu Server.  

> **photoman355 said:**
> 

I better explain a bit more about what i'm trying to achieve to check your response is the right solution...
  The connection will have to be secure and passwords/security keys are a must.

It will be *your* response ultimately that is the right or wrong solution.  I can only toss ideas up or point you to various possibilities.  

If you turn off password authentication, except maybe for a select group, then key-based authentication will be required.  That can be used to tunnel the samba connection.  If you need tcp ports   137, 138, 139 and 445:

ssh 

```

PasswordAuthentication no

Match Group photomanhelpers
  PasswordAuthentication yes

Match Group *, !photomanhelpers
  PasswordAuthentication no
  ChrootDirectory %h

```

If you know they will be always connecting from a specific host or ip address, then you can use **permitopen** to limit login attempts.

See also
[http://www.osmanoglu.org/index.php/computing/31-tunnelingsambathroughssh](http://www.osmanoglu.org/index.php/computing/31-tunnelingsambathroughssh)
[http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php)
[https://calomel.org/samba_optimize.html](https://calomel.org/samba_optimize.html)

You can make the port forwarding request automatic using LocalForward in either the user's ssh_config file or as an option in the arguments used when launching the connection.  The latter inside a script usually or in a desktop icon's properties. e.g. 

ssh -fgnqN -o 'LocalForward 10139 127.0.0.1:139'  sambahost.example.org

or 

```

ssh -i ~/.ssh/samba_rsa_key  \
  -fgnqN \
  -L 10137:localhost:137  \
  -L 10138:localhost:138  \
  -L 10139:localhost:139  \
  -L 10445:localhost:445  \
sambahost.example.org

```

YMMV

---

### Post by spikyjt on 2009-11-19
Or you could set up [OpenVPN]("http://openvpn.net") which is cross platform.

---

