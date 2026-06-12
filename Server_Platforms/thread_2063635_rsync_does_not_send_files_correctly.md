---
title: "rsync does not send files correctly"
date: 2012-09-27
forum: Server Platforms
---

### Post by dipique on 2012-09-27
Hello all.  I'm a relative *nix noob, but to save money at work I decided to put in an Ubuntu server as a fileserver so that we could use it as a web server as well.  Things have been going all right, except for that I discovered this weird issue today:

I run rsync nightly to a remote server.  The update is one-directional--I don't need to pull anything back over, I just dump the local server's files to a remote server.  Cron runs nightly (as root) and runs the backup sh script.

Today, I noticed that files weren't being backed up, and hadn't been for a little while, so I ran the backup script by itself, using the command:

```
sudo sh /scripts/backup
```

It did the weirdest thing... it listed all the new and changed files... and then it was done.  Now, the connection between the two servers is a T1, so I knew the 1.2GB ISO file I stuck on the server today wasn't tranferred in a few seconds.  So I switched on the verbose switch on rsync and re-ran.  Here's the script (pared down for the sake of simplicity):


```
#Establish time
echo "Job start time:"
date

echo "----------------------------"
date
echo "Backing up Working share..."
rsync -arv /data/Working/    /mnt/abc/Working/

echo ""
date
echo "Backing up Accounting share..."
rsync -arv /data/Accounting/ /mnt/abc/Accounting/

#Establish finish time
echo "--------------------------"
echo "Job end time:"
date

#Complete
echo "Back up complete."
```

The "mnt" directory is a group of remote server directory mounted via mount.cifs.  I am able to browse these directories, enumerate /open/copy files, etc.  The connection appears just fine.

So then I run the backup script, and I get output like this:

```
Thu Sep 27 12:30:44 EDT 2012
Backing up IT share...
sending incremental file list
Software/
Software/OS and Images/
Software/OS and Images/ubcd511.iso
Software/Productivity/
Software/Tools & Utilities/
Software/Tools & Utilities/System Information Utilities/
Software/Tools & Utilities/System Information Utilities/SysinternalsSuite.zip

sent 13134695137 bytes  received 2206 bytes  81836120.52 bytes/sec
total size is 44466830195  speedup is 3.39

```

81 MEGABYTES PER SECOND!  !!

Of course, I knew that wasn't right, so I checked the destination and sure enough none of the changes were actually applied.

Anybody have any idea what's going on?

Dan

---

### Post by lykwydchykyn on 2012-09-27
Are you quite sure the destination point is actually mounted?  What does the output of "mount" (with no arguments) tell you?

If it weren't, rsync would just be copying to the local disk, which would explain the speed.

If the script had run at some point when the remote system wasn't mounted, and data had been copied into the mount points, subsequent attempts to mount the remote server may have failed since the mount point wasn't empty.

That's my theory.

---

### Post by rubylaser on 2012-09-27
Personally, I wouldn't rely on mounts over a T1.  I would be using [passwordless SSH with keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") and modify the script as such.

```
#Establish time
if ping -c 1 remote_ip
then
  echo "Job start time:"
  date

  echo "----------------------------"
  date
  echo "Backing up Working share..."
  rsync -arv /data/Working/    root@remote_ip:/path/to/files/Working/

  echo ""
  date
  echo "Backing up Accounting share..."
  rsync -arv /data/Accounting/ root@remote_ip:/path/to/files/Accounting/

  #Establish finish time
  echo "--------------------------"
  echo "Job end time:"
  date

  #Complete
  echo "Back up complete."
else
  echo "=====The remote server is down====="
  echo "setup email alert here" 
fi

```

This way you know your files are going to the correct spot.  Also, it will check before it runs to ensure that the remote server is up.  If it's not, it should send you an email so you can troubleshoot the problem.

---

### Post by dipique on 2012-09-28
> **lykwydchykyn said:**
> Are you quite sure the destination point is actually mounted?  What does the output of "mount" (with no arguments) tell you?

If it weren't, rsync would just be copying to the local disk, which would explain the speed.

If the script had run at some point when the remote system wasn't mounted, and data had been copied into the mount points, subsequent attempts to mount the remote server may have failed since the mount point wasn't empty.

That's my theory.

Thanks for the replies.  As always happens, I solved my problem after posting this.  I restarted the server (it hadn't restarted in a couple weeks) and everything started working fine.

What confuses me is that I could traverse the remote directories--which is completely different from the behavior I typically see if the remote server disconnect.  Hmm.

What is the rationale for using SSH rather than mount points?

Thank you!

Dan

EDIT:  I'm backing up to a Windows file server, if that makes a difference.

---

### Post by rubylaser on 2012-09-28
> **dipique said:**
> Thanks for the replies.  As always happens, I solved my problem after posting this.  I restarted the server (it hadn't restarted in a couple weeks) and everything started working fine.

What confuses me is that I could traverse the remote directories--which is completely different from the behavior I typically see if the remote server disconnect.  Hmm.

What is the rationale for using SSH rather than mount points?

Thank you!

Dan

You have to create a path for a mount point, in your case /mnt/abc/Working/ and /mnt/abc/Accouting/.  If your remote share is not available, or isn't mounted, that path is still available on the original machine.  You could believe that your backup is successful, but you're only backing up to the original machine. 

The way I posted would ensure the remote host is available and then would backup to it if it was.  Also, you would receive an email if it was not available.  None of those factors are being prevented in your current implementation.

---

### Post by dipique on 2012-09-28
> **rubylaser said:**
> You have to create a path for a mount point, in your case /mnt/abc/Working/ and /mnt/abc/Accouting/.  If your remote share is not available, or isn't mounted, that path is still available on the original machine.  You could believe that your backup is successful, but you're only backing up to the original machine. 

The way I posted would ensure the remote host is available and then would backup to it if it was.  Also, you would receive an email if it was not available.  None of those factors are being prevented in your current implementation.

I see.  Could you give me some guidance in terms of how to set that up on a Windows server?  Or point me in the right direction?

Dan

---

### Post by lykwydchykyn on 2012-09-28
> **rubylaser said:**
> Personally, I wouldn't rely on mounts over a T1.  I would be using [passwordless SSH with keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") and modify the script as such.


I use this method as well; it seems a more direct approach than mounting a drive, which has potential issues as I highlighted.

No idea how to set that up on Windows, other than that you need to install an SSH server with SCP and SFTP support enabled.  A quick google shows that there are a number to choose from.

---

