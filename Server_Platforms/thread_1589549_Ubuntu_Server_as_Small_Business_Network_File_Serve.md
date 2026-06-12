---
title: "Ubuntu Server as Small Business Network File Server?"
date: 2010-10-06
forum: Server Platforms
---

### Post by SpoonfedCivic on 2010-10-06
I'm the network admin for a diesel company based out of Springfield, MO and recently got the idea to create a file server on our network.  And I want to use Ubuntu Server 64bit for the OS.  I'm still very new to Unix/Linux based OS in general, so I have been doing a lot of reading and note taking.  What I wish to do is so:

Create a storage drive on the file server and call it, (I: ) and create folders for each employee on (I: ).  Then I want the [My Documents] on each workstation mapped to (I: ) on the file server.  So when an employee logs into their workstation, that username and password connects to their specific folder on (I: ).  To where everything they save in their [My Documents] is instantly saved on the (I: ) drive of the file server.  Then I should be able to go into the group policies and set a storage limit on their folder.  

From what I have read and gathered so far, I should be able to do this in Ubuntu Server with SAMBA.  Is this correct?  This is all I know so far, if I'm wrong please direct me to the proper area so I can get this setup to do what I wish.  Thanks ahead of time.

---

### Post by SeijiSensei on 2010-10-06
Yes, although *nix treats drives very differently than Windows.  Basically all filesystems are mounted into the directory tree.  So suppose you have a server with two hard drives, one that holds the Ubuntu OS, and another that you're going to share with the network.

The second drive will appear to the operating system as /dev/sdb.  If you have a single partition on the drive, Linux will see it as /dev/sdb1.  Since you want this filesystem to have employee-specific folders, you'll probably want to mount it as the /home directory in Linux.  So you'll have the root partition / and everything below it except /home on one drive, and /home on the other.  By default Samba exports each user's home directory as \\server\username.  

The mapping to I: happens on the Windows client.  You'd use "map a network drive" to assign the exported share \\server\username to I:.  

The server doesn't need much in the way of hardware to handle this task.  You could set this up on an old PC and test it out first.  64-bit probably doesn't matter either, unless you're supporting hundreds and hundreds of users where the ability to address > 3GB of memory might be useful.

You'll need to look into the complexities of passwords and the relationship between Samba user accounts and their corresponding accounts in Linux (see the instructions for the directive "unix password sync" in Samba's configuration file /etc/samba/smb.conf for details.)

---

### Post by dtfinch on 2010-10-06
We have private shares that map automatically to the right location. So someone goes to "\\servername\private" and they see just their own folder, created automatically on their first access. We're not using quotas though.
```
[private]
    path = /store/private/%u
    read only = No
    root preexec = mkdir /store/private/%u; chown %u /store/private/%u
```

We also have a DFS root on Samba so that all of our common network shares appear together under one drive.

---

### Post by SeijiSensei on 2010-10-06
> **dtfinch said:**
> We have private shares that map automatically to the right location. So someone goes to "\\servername\private" and they see just their own folder, created automatically on their first access. We're not using quotas though.

That's an elegant solution.  Does each user still have a separate Samba password?

---

### Post by dtfinch on 2010-10-06
> **SeijiSensei said:**
> That's an elegant solution.  Does each user still have a separate Samba password?
Yes.

We're not using LDAP and we haven't integrated our samba servers with our active directory domain yet, so we're still creating users the old fashioned way. Creating the linux user with useradd, assigning them to groups with usermod, then setting their samba login with smbpasswd. So long as it matches their domain login, Windows logs them in automatically when they try to connect.

---

### Post by SpoonfedCivic on 2010-10-07
Is there like a How To on this somewhere?  Like a step by step?  It does not seem all that difficult but a how to would be pretty nice haha.  Thanks for all of your help so far.

---

### Post by SeijiSensei on 2010-10-07
[https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html)

---

### Post by SpoonfedCivic on 2010-10-07
> **SeijiSensei said:**
> [https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html](https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html)

Thanks once again!  You guys are a great help, so far one of the best forums I have joined!

---

### Post by cc48510 on 2010-12-30
> **dtfinch said:**
> We have private shares that map automatically to the right location. So someone goes to "\\servername\private" and they see just their own folder, created automatically on their first access. We're not using quotas though.
```
[private]
    path = /store/private/%u
    read only = No
    root preexec = mkdir /store/private/%u; chown %u /store/private/%u
```

We also have a DFS root on Samba so that all of our common network shares appear together under one drive.

How did you do DFS with Samba ? Does it support DFS Replication or only DFS Namespaces ?

---

### Post by dtfinch on 2010-12-30
To enable it, you need "host msdfs = yes" in your global section, and "host msdfs = yes" on the share that'll host the dfs root. Then create symlinks for each linked share. [http://www.samba.org/samba/docs/using_samba/ch08.html#samba2-CHP-8-SECT-7](http://www.samba.org/samba/docs/using_samba/ch08.html#samba2-CHP-8-SECT-7)

I haven't used Windows Server's DFS, but Samba's, as we're using it, would be equivalent to a standalone namespace. We just use it to combine several network shares on several servers into one drive letter, and minimize effort and downtime when we need to move a share to a new server. There's no built-in replication, though there are several alternatives none of which I've tried.

---

