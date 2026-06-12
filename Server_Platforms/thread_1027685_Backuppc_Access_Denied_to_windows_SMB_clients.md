---
title: "Backuppc Access Denied to windows SMB clients"
date: 2009-01-01
forum: Server Platforms
---

### Post by Clark3934 on 2009-01-01
So for the past few days I have been trying everything I could think of to get my backuppc to work on my home network.  I am basically using a ubuntu 8.10 box to attempt to backup several windows (XP/vista) pc's on the network.

I order to simplify things, I have been trying to focus on getting on backup to work.  This particular machine runs windows xp professional.  Its netbios name is 'clarks-desktop'.

I have entered the username and password correctly into my backuppc set up, and am attempting to access the C$ administrative share.  My credentials in the conf file (and on the web gui) are correct, I just cannot figure out why it is not connecting. 

Here is a sample of my log file:
```
Contents of file /var/lib/backuppc/pc/clarks-desktop/XferLOG.bad.z, modified 2009-01-01 15:06:47

Running: /usr/bin/smbclient \\\\clarks-desktop\\C\$ -U Clark -E -d 1 -c tarmode\ full -Tc -
full backup started for share C$
Xfer PIDs are now 15971,15970
timeout connecting to 192.168.1.146:445
timeout connecting to 192.168.1.146:139
Connection to clarks-desktop failed (Error NT_STATUS_ACCESS_DENIED)
timeout connecting to 192.168.1.146:445
timeout connecting to 192.168.1.146:139
Connection to clarks-desktop failed (Error NT_STATUS_ACCESS_DENIED)
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (No files dumped for share C$)
Backup aborted (No files dumped for share C$)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)
```

I can ping the machine fine, and I assume it doesn't show up in the ubuntu graphical network browser because it is a "secret windows share".  clarks-desktop shows up in smbtree when I add superfluous shares to the network, but disappears when I leave C$ as the only share available (so, I assume it to be working correctly, as its just not visible because it's not supposed to be visible).

I followed advice given here: [https://bugs.launchpad.net/ubuntu/+source/backuppc/+bug/283652](https://bugs.launchpad.net/ubuntu/+source/backuppc/+bug/283652) which states that I should remove the -N flag from the ```
    $Conf{SmbClientFullCmd}
    $Conf{SmbClientIncrCmd}, and
    $Conf{SmbClientRestoreCmd}
```
strings because it interferes with the login process and causes it to log-in anonymously.  I think (?) this solved part of my problem, because previous backuppc logs indicated that it was trying to log in anonymously.

Does anyone have any suggestions to make this work?  I have followed all of the guides on the documentation (see: [https://help.ubuntu.com/community/BackupPC/smb](https://help.ubuntu.com/community/BackupPC/smb) and [https://help.ubuntu.com/community/BackupPC](https://help.ubuntu.com/community/BackupPC)), but they mention nothing of resolving the problem.

Hopefully this can be resolved!  Thanks in advance.

---

### Post by Clark3934 on 2009-01-02
So, I have had no luck resolving this problem.  After removing the "-N" flag from the smbclient's command, I am beginning to think it is a window's permissions problem, having nothing to due with the backuppc client.

To summarize my permissions.  The windows xp pro machine has one account, named "Clark" with full administrative access.  There is no guest account or any other accounts on the machine (to my knowledge).  

When trying to log in through backuppc I use the client pc's username "Clark" with its associated password.  This does not work.  I have also tried using the username "clarks-desktop\clark" which has also failed.

Is there some special thing I need to do to access the C$ administrative share remotely?  I am able to access it from another windows machine by going to start > run and entering "\\clarks-desktop\c$" and entering username "Clark" with the corresponding password.

I cannot figure out for the life of my why this is not working with backuppc.  Is there a way I can test login with SMB client so I may further isolate the problem?  Thanks.

---

### Post by aappddeevv on 2009-10-18
I had the same problem. You can try smbclient -d2 -U yourvistausername \\\\yourvistamachine\\C\$ on the command line and see if you can connect. Ensure you have file sharing on in the network and sharing control center as well as password protected sharing for safety.  smbtree -U youvistausername is another test you can run.  This tests your samba connection.

Problem 1: If these fail with 139, 445 access errors or NT_STATUS_ACCESS_DENIED errors then you are probably having the vista problem described here: [http://support.microsoft.com/kb/947232](http://support.microsoft.com/kb/947232).  If you create a new password protected share and test the above commands and it works then the token problem is probably the issue.

You can get around all of this by defining your own share and own permissions/access on the c drive.

Problem 2: I also had to do the -N removal as you describe. I think a newer version of backuppc fixes this but I am not sure.


My backuppc user was added as a member of the backup operators group using a management control panel.

---

