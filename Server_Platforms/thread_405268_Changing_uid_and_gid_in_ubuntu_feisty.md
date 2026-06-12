---
title: "Changing uid and gid in ubuntu feisty"
date: 2007-04-09
forum: Server Platforms
---

### Post by SangLad on 2007-04-09
Dear Ubuntu Forum Users,

I have to begin by saying that this forums have been a great help for me setting up my dual boot MacBook (Ubuntu Feisty and Mac OS X)!

Now, for work, I have been ssh-ing into work to another servers. Both my Mac OS X and servers have the same uid and gid.

However, because I am a novice using Linux, I don't know how to safely change my uid and gid in Linux. Actually, I don't even know how to obtain uid and gid in ubuntu. I want to be very careful changing the uid and gid in my MacBook ubuntu. I don't want to repeat my mistakes from Mac OS X. It was a pain to have resolved the permission issues after I blindedly changed both uid and gid. I ended up not able to open applications and able to write any files...

Just to get all the facts in: My MacBook is only used by me at the moment. No other user account is present.

I would be very grateful, if someone can guide me through how to change both uid and gid in my Ubuntu without affecting the rest of the OS (or change the entire OS, so that my uid and gid  are consistent).

I need to change my uid to 6803 and my gid to 1132. 

Also, I did search the weba nd the forums, but I was not able to get an answer for me to understand...

Thank you for all your help in advance and look for toward to hearing from you all soon!

From Sang

---

### Post by rufius on 2007-04-09
To get your uid/gid in linux you type: ```
id
```

To change your uid and gid, use the following command: ```
usermod -g xxx -u xxx username
```

where 'xxx' are the numbers you want to change to.

---

### Post by SangLad on 2007-04-09
Thank you rufius for your quick reply!

If I follow your instructions (usermod -g xxx -u xxx username), do I have to change any other settings on my ubuntu os? Will all the apps launch without permission issues as well as all the files and be read and write without any permission issues?

Again, thank you for all your help.

From Sang

---

### Post by rufius on 2007-04-09
I don't think you'll have any problems but this is always a good thing to do. This is just to make sure everything is in order by doing a chown. Which entails doing the following: ```
sudo chown -R <user>:<user> /home/<user>
```

where <user> is whatever the username is. This will ensure that those files are owned by that user and will make sure that the UID & GID are updated incase something went wrong with the first command.

---

### Post by SangLad on 2007-04-09
Thanks again. 

I will definitely try, (sudo chown -R <user>:<user> /home/<user>), this evening when I get back home!!

From Sang

---

### Post by SangLad on 2007-04-12
Hi,

I did try the following:

 sudo usermod -g 1132 -u 6803 slee

However, I get an error message saying:

usermod: unknown group 1132

Now, at my work, all my gid is 1132. How can I change my gid to 1132 and uid to 6803?

Thanks again for all your help.

From Sang

---

