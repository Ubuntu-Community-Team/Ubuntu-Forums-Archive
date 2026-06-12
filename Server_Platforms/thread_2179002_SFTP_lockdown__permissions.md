---
title: "SFTP lockdown / permissions"
date: 2013-10-06
forum: Server Platforms
---

### Post by banedon on 2013-10-06
Hi guys

My education in ubuntu server is increasing by the day (thanks to the help I get here and a monumental amount of googling!).

Now that I'm getting my head around how linux/unix permissions work, I've added SFTP (for wordpress plugins so only on my internal network for the moment) and am trying to lock down what can be seen and done.
I followed [this]("http://blog.srmklive.com/2013/04/24/how-to-setup-sftp-server-ftp-over-ssh-in-ubuntu/") handy guide which showed how to enable sftp, but then proceeded to get me to put chmod 777 on the uploads folder... which would enable read / write / execute for everyone in the world.  From what I've read and my own knowledge this is not a good thing.

Looking around there seems to be a myriad of people saying that I need to modify various files to lock things down.
However, I was hoping I could do it with CHMOD.
So far I have the SFTPUSER user account and the SFTPUSERS group created and set with the following permissions on the sftp home directory:
664  (d rw- rw- r--) SFTPUSERS:SFTPUSER
This isn't working out too well as it denies me the ability to run commands - even to CD to the directory (you can't SUDO CD it seems!).
I suspect this is because the execute bit isn't set for the owner so I think I need to add that. However, I was hoping to deny the execute ability, but I think I'm going to have to do it anyway (wordpress alone will probbaly need it).

My question: If I change things to 774 will this cause a security issue?
And could I safely deny SFTP from the /home folder so the session cannot see up the directory tree?  I'd try it but I fear borking it all.
Please let me know what you think - even if it's to say I'm barking up the wrong tree and need to make config file modifications.

Many thanks

---

### Post by Lars Noodén on 2013-10-06
Directories generally must have 'x' set to be useful.  If you are very worried about executables, you could make a separate disk partition for that directory and mount it [noexec](http://manpages.ubuntu.com/manpages/raring/en/man8/mount.8.html).  

You can deny SFTP users access to the /home directory by chrooting them to another directory, either their home directory or something else, using [ChrootDirectory](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html).  The difficult part of that is that the chroot target must be owned by root and not writeable by any other user or group.  The same restriction does not apply to files or subdirectories there, but it does make it inconvenient to work within the chroot without modifying behavior.

---

