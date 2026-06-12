---
title: "[SOLVED] Mounting an SSHFS share"
date: 2007-08-11
forum: Server Platforms
---

### Post by p_quarles on 2007-08-11
I am trying to mount a remote folder onto my desktop using sshfs, and it's not being very cooperative at the moment.

I've done all the basics: installing sshfs to the local machine, invoking fuse, adding myself to the "fuse" group, making fusermount a normal user command, and making a new directory for the mounted remote directory.

I can get it to work by doing this:
```
sudo sshfs me@lan-ip-addr:/home/me /home/me/mountdir
```
But this works only partially: once I try to enter the newly mounted directory, it gives me "permission denied." "Sudo" apparently does not work with "cd," so I had to log in a root before I could access the folder. Once I did, everything was there as it should be.

Obviously, though, I don't want to have to log in as root to do this. 

When I enter the above command without sudo, I get 
```
fusermount: failed to open dev/fuse: permission denied
```
As I said, this is *after* I have done the following
```
sudo chmod +x /usr/bin/fusermount
sudo addgroup *me* fuse
```
One other thing to mention: after successfully mounting the remote directory using sudo, the local directory's information gets completely scrambled: permissions, owner, size, and dates are all listed as "?" Once the remote directory is unmounted, this information returns to its original settings. 

I think I'm doing this right, so I'm perplexed about what's going wrong here. Any help is greatly appreciated.

---

### Post by Jamie Jackson on 2007-08-12
Here are some notes to myself on the subject. Maybe there's something in here that helps.

```

#mount ssh
sudo apt-get install sshfs
sudo mkdir /media/myRemoteMachine/
sudo chown jamie /media/myRemoteMachine
sudo adduser jamie fuse
#logout/login
#get uid and gid
id -u
id -g
#put uid and gid below (mine are 1000 and 1000, respectively)
sshfs -o uid=1000,gid=1000 myRemoteUsername@myRemoteMachine:/ /media/myRemoteMachine
```

---

### Post by p_quarles on 2007-08-12
Thanks much. I'll give this a try when I get a chance.

Without trying it, though, I can say it looks promising. The tutorial I used didn't mention "chown", but now that I think about it that does seem necessary. And "adduser" rather than "addgroup" makes more sense. 

I'll report back soon.

EDIT: Tried it, and it worked. Thanks!
2nd EDIT: Works, except for the fact that the mounted filesystem reports 7.5 terabytes of free space, on a 40 gig hdd. Not a serious problem for my purposes, I just thought it was funny and worth sharing.

---

### Post by Perkins on 2007-08-15
The other thing you can do is make the sshfs mount and unmount programs setuid root.  Simpler, but might not be the best solution on multiuser systems where you don't want just anybody doing it.

---

