---
title: "what is &quot;perldoc Net::FTP&quot; following documentation but dont understand"
date: 2011-01-26
forum: Server Platforms
---

### Post by garethsimpsonuk on 2011-01-26
Hi all I was wondering if someone could help me:

I'm setting up backuppc for backing up over ftp. I have been following this guide: [http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc). The difference is I need to use FTP to backup as opposed to ssh / rsync.

I have followed the guide and instead of using

```
$Conf{XferMethod} = 'rsync';
```

I am using

```
$Conf{XferMethod} = 'ftp';
```

as per: [http://backuppc.sourceforge.net/faq/BackupPC.html](http://backuppc.sourceforge.net/faq/BackupPC.html)


```
ftp

    You need to be running an ftp server on the client machine. The relevant configuration settings are $Conf{FtpShareName}, $Conf{FtpUserName}, $Conf{FtpPasswd}, $Conf{FtpBlockSize}, $Conf{FtpPort}, $Conf{FtpTimeout}, and $Conf{FtpFollowSymlinks}.

You need to set $Conf{ClientCharset} to the client's charset so that file names are correctly converted to utf8. Use "locale charmap" on the client to see its charset.

For linux/unix machines you should not backup "/proc". This directory contains a variety of files that look like regular files but they are special files that don't need to be backed up (eg: /proc/kcore is a regular file that contains physical memory). See $Conf{BackupFilesExclude}. It is safe to back up /dev since it contains mostly character-special and block-special files, which are correctly handed by BackupPC (eg: backing up /dev/hda5 just saves the block-special file information, not the contents of the disk).

Alternatively, rather than backup all the file systems as a single share ("/"), it is easier to restore a single file system if you backup each file system separately. To do this you should list each file system mount point in $Conf{TarShareName} or $Conf{RsyncShareName}, and add the --one-file-system option to $Conf{TarClientCmd} or $Conf{RsyncArgs}. In this case there is no need to exclude /proc explicitly since it looks like a different file system.

Next you should decide whether to run tar over ssh, rsh or nfs. Ssh is the preferred method. Rsh is not secure and therefore not recommended. Nfs will work, but you need to make sure that the BackupPC user (running on the server) has sufficient permissions to read all the files below the nfs mount.

Ssh allows BackupPC to run as a privileged user on the client (eg: root), since it needs sufficient permissions to read all the backup files. Ssh is setup so that BackupPC on the server (an otherwise low privileged user) can ssh as root on the client, without being prompted for a password. There are two common versions of ssh: v1 and v2. Here are some instructions for one way to setup ssh. (Check which version of SSH you have by typing "ssh" or "man ssh".)
```

Everything seems to be working correctly except when a backup is executed I get this:

```
Running: /usr/bin/smbclient \\\\phraseone.co.uk\\C\$ -U  -E -d 1 -c tarmode\ full -Tc -
full backup started for share C$
Xfer PIDs are now 7295,7294
Connection to phraseone.co.uk failed (Error NT_STATUS_UNSUCCESSFUL)
Connection to phraseone.co.uk failed (Error NT_STATUS_UNSUCCESSFUL)
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (No files dumped for share C$)
Backup aborted (No files dumped for share C$)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)
```

As you can see it is showing the smbclient as method of connection. I can get this to say ssh but not FTP, even though  FTP functions are available.

One of the factors that maybe affecting it is this:

```
File::RsyncP

    To use ftp with BackupPC you will need to install three libraries: Net::FTP, Net::FTP::RetrHandle and Net::FTP::AutoReconnect. You can run "perldoc Net::FTP" to see if a particular module is installed.
```

I haven't completed this step properly as I don't quite understand. I guess I need to install those 3 libraried but how? I didn't know what to do so I ran "perldoc Net::FTP" and mocved on. Now I think that the ftp layer isnt working because of this step.

Can someone explain to me what this is and how to install these libraries or if you think I'm barking up the wrong tree.

Any help would be greatly appreciated.

Many thanks

---

### Post by garethsimpsonuk on 2011-01-26
Possibly a bug?...

[http://www.mail-archive.com/backuppc-users@lists.sourceforge.net/msg13995.html](http://www.mail-archive.com/backuppc-users@lists.sourceforge.net/msg13995.html)

---

### Post by garethsimpsonuk on 2011-01-26
The ftp transfer layer is a fairly new feature and the ubuntu package is a bit old now so I compiled from source but now recieve an error in the web gui  about not being able to access  /etc/backuppc/config.pl.

Please tell me how I can get the  user that backuppc runs as to access the config file.

Many thanks

---

### Post by redmk2 on 2011-01-26
> **garethsimpsonuk said:**
> Hi all I was wondering if someone could help me:

I'm setting up backuppc for backing up over ftp. I have been following this guide: [http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc). The difference is I need to use FTP to backup as opposed to ssh / rsync.

I have followed the guide and instead of using

```
$Conf{XferMethod} = 'rsync';
```

I am using

```
$Conf{XferMethod} = 'ftp';
```

as per: [http://backuppc.sourceforge.net/faq/BackupPC.html](http://backuppc.sourceforge.net/faq/BackupPC.html)


```
ftp

    You need to be running an ftp server on the client machine. The relevant configuration settings are $Conf{FtpShareName}, $Conf{FtpUserName}, $Conf{FtpPasswd}, $Conf{FtpBlockSize}, $Conf{FtpPort}, $Conf{FtpTimeout}, and $Conf{FtpFollowSymlinks}.

You need to set $Conf{ClientCharset} to the client's charset so that file names are correctly converted to utf8. Use "locale charmap" on the client to see its charset.

For linux/unix machines you should not backup "/proc". This directory contains a variety of files that look like regular files but they are special files that don't need to be backed up (eg: /proc/kcore is a regular file that contains physical memory). See $Conf{BackupFilesExclude}. It is safe to back up /dev since it contains mostly character-special and block-special files, which are correctly handed by BackupPC (eg: backing up /dev/hda5 just saves the block-special file information, not the contents of the disk).

Alternatively, rather than backup all the file systems as a single share ("/"), it is easier to restore a single file system if you backup each file system separately. To do this you should list each file system mount point in $Conf{TarShareName} or $Conf{RsyncShareName}, and add the --one-file-system option to $Conf{TarClientCmd} or $Conf{RsyncArgs}. In this case there is no need to exclude /proc explicitly since it looks like a different file system.

Next you should decide whether to run tar over ssh, rsh or nfs. Ssh is the preferred method. Rsh is not secure and therefore not recommended. Nfs will work, but you need to make sure that the BackupPC user (running on the server) has sufficient permissions to read all the files below the nfs mount.

Ssh allows BackupPC to run as a privileged user on the client (eg: root), since it needs sufficient permissions to read all the backup files. Ssh is setup so that BackupPC on the server (an otherwise low privileged user) can ssh as root on the client, without being prompted for a password. There are two common versions of ssh: v1 and v2. Here are some instructions for one way to setup ssh. (Check which version of SSH you have by typing "ssh" or "man ssh".)
```

Everything seems to be working correctly except when a backup is executed I get this:

```
Running: /usr/bin/smbclient \\\\phraseone.co.uk\\C\$ -U  -E -d 1 -c tarmode\ full -Tc -
full backup started for share C$
Xfer PIDs are now 7295,7294
Connection to phraseone.co.uk failed (Error NT_STATUS_UNSUCCESSFUL)
Connection to phraseone.co.uk failed (Error NT_STATUS_UNSUCCESSFUL)
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (No files dumped for share C$)
Backup aborted (No files dumped for share C$)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)
```

As you can see it is showing the smbclient as method of connection. I can get this to say ssh but not FTP, even though  FTP functions are available.

One of the factors that maybe affecting it is this:

```
File::RsyncP

    To use ftp with BackupPC you will need to install three libraries: Net::FTP, Net::FTP::RetrHandle and Net::FTP::AutoReconnect. You can run "perldoc Net::FTP" to see if a particular module is installed.
```

I haven't completed this step properly as I don't quite understand. I guess I need to install those 3 libraried but how? I didn't know what to do so I ran "perldoc Net::FTP" and mocved on. Now I think that the ftp layer isnt working because of this step.

Can someone explain to me what this is and how to install these libraries or if you think I'm barking up the wrong tree.

Any help would be greatly appreciated.

Many thanks

The term *perldoc *invokes the PERL documentation (if it's installed) the 3 libraries need to be installed.  My guess is that only the default libs are installed initially.

The whole thing is documented [**_[COLOR="Blue"]here[/COLOR]_**]("http://backuppc.sourceforge.net/faq/BackupPC.html").

Search the above web page for the keyword *perl*.

---

### Post by garethsimpsonuk on 2011-01-27
Ok thanks.

My main problem is that I upgraded to latest stable using a tar.gz but now the user the backuppc runs as doesnt have access to /etc/backuppc/config.pl

Does anyone know how to remedy this?

Thanks

---

### Post by garethsimpsonuk on 2011-01-27
I couldnt fix it so I did a fresh install and used a repo I found here:

[http://www.tolaris.com/apt-repository/](http://www.tolaris.com/apt-repository/)

Now it works perfectly

---

