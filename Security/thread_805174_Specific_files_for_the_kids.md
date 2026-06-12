---
title: "Specific files for the kids"
date: 2008-05-23
forum: Security
---

### Post by fballem on 2008-05-23
I am setting up a 'family computer' on ubuntu. By the way, I am a newbie, so forgive the really basic question.

I have an NAS in which I have identified some shares - including some specific ones for the kids.

What I would like to have is that when one of the kids logs in, then their share on the NAS is mounted. I was thinking of doing this in the /etc/fstab file, but I have a feeling that is a global file (applicable to all users). Is there an equivalent that I can create for each user and have it execute when they log in.

Many thanks,

---

### Post by yaztromo on 2008-05-24
I don't think there are any user specific equivalents to fstab, someone may correct me on this.

If you don't want to put anything in /etc/fstab then my method would be to put a separate script in each users home folder that mounts their share when they login:

1. Create a folder in each users home directory for their share
```

sudo mkdir /home/tom/homework
sudo mkdir /home/sally/music

```

2. Write individual scripts in a text editor for each user. For example tom's might be
```

#!/bin/sh
mount -t smbfs //home-nas/homework /home/tom/homework -o userid=tom,password=h0mework

```

3. Put the scripts in each corresponding home folder and make them owned and readable by only that user. 
```

sudo mv tomsscript /home/tom/.tomsscript
sudo chown tom:tom /home/tom/.tomsscript
sudo chmod 700 /home/tom/.tomsscript

```

4. Add the script to the users session in Gnome
- Login as tom
- Go to System -> Preferences -> Sessions -> Startup Programs -> Add
- Name Mount toms share
- command /home/tom/.tomsscript

The only problem I can see with this is that the shares aren't unmounted on logout, but the solution would be to have all the folders readable by only the corresponding user using the chmod and chown commands like above.

---

