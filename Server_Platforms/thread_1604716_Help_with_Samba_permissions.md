---
title: "Help with Samba permissions"
date: 2010-10-24
forum: Server Platforms
---

### Post by Ambiorix3 on 2010-10-24
Hey everyone,

i'm setting up a home file server and i need some help with permissions. I'll explain my situation.

I have a computer with ubuntu server 10.10 installed. 

I have 2 users:
- sysadmin (the account for me to work with)
- daniel (the account for my dad) which doesn't have a system password, only a samba password.


I have 3 harddisks:

1) 250GB: main harddisk with ubuntu installed
2) 1000GB: used to store data
3) 1000GB: used to store backups



I have 1 folder on the data harddisk on which i want my dad to store his files. I want him to only be able to see his folder, not the rest of the harddisk. 

This is what my permissions look like:

[IMG]http://img46.imageshack.us/img46/3476/permissionsmountpoints.png[/IMG]

and the permissions inside de Data harddisk:

[IMG]http://img525.imageshack.us/img525/1010/permissionsdata.png[/IMG]

and the contents of smb.conf:

[IMG]http://img217.imageshack.us/img217/3112/contentssmbconf.png[/IMG]


I as sysadmin can access everything, but my dad can't access the folder daniel, or if i change the permissions he can access both the whole data harddisk and his folder. I want him to just access his folder "daniel" but unable to see the contents of the disk.

I've played with the permissions and looked at multiple tutorials of samba but can't seem to figure this out. Is it even possible and if yes, how?


Thank you,


Ambiorix

---

### Post by Boondoklife on 2010-10-24
I am a bit confused as to what your current error or problem is, it sounds like you are trying to limit what is viewable via the network shares browsing. Could you please clarify what you are currently getting.

Here are a couple of docs that I bookmark and use when configuring samba:

[LIST]
[*][http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)
[*][http://permissions-calculator.org/symbolic/](http://permissions-calculator.org/symbolic/)
[/LIST]

---

### Post by Ambiorix3 on 2010-10-24
So what i want is to let a user have full rights on a folder on a harddisk, but no rights on the rest of the harddisk (not to view the contents, not to write, nothing)

---

### Post by Boondoklife on 2010-10-24
> **Ambiorix3 said:**
> So what i want is to let a user have full rights on a folder on a harddisk, but no rights on the rest of the harddisk (not to view the contents, not to write, nothing)

I already know what you "want", I need to know what is currently "happening". Your permissions are a good start but check out the first link as it outlines what you are looking for.

---

### Post by Ambiorix3 on 2010-10-24
What is happing is that the user "daniel" cannot access the folder /mnt/Data/Daniel without him having the rights to view the contents of /mnt/Data/. I have to make him co-owner of the full harddisk to let him access his folder.

I've looked at the link you gave me, it didn't really teach me anything new relevant to my problem.

I'm starting to think this can only be achieved with a separate partition but if this is true then i feel like the linux permission system is kind of limited. (I'm not saying the windows system is better but i would expect more from linux).

---

### Post by Morbius1 on 2010-10-24
I really don't like shares within shares as you are attempting to do but for the life of me I don't see why this won't work.

I was able to temporarily reproduce your error but only because the partition was mounted with ownership of root - plugdev and daniel was not a member of the plugdev group. The only way that would happen in your situation is if daniel was not a member of the daniel group. I don't see how that would be possible. 

As a sanity check you might want to see if daniel is a member of the daniel group:
```
id daniel
```

---

### Post by Boondoklife on 2010-10-24
All you should have to do is as follows for folders:
/mnt/data you need to give r and x permissions so it can be opened.
```
chmod u+rwx,g+rx-w,o-rwx
```/mnt/data/daniel should look like this
```
chmod u+rwx,g+rwx,o-rwx
```for files in /mnt/data/daniel:
```
chmod  u+rw-x,g+rw-x,o-rwx
```your smb.conf is rather limited at best, try:

```
[daniel]
comment= whatever
browseable = no
read only = no
guest ok = no
valid users = daniel
write users = daniel
```This is not a limitation of linux as I have multiple shares with multiple security reqs, all on the same partition. It looks like it is just a permissions issue that you need to correct.

Now if you are also trying to do this from a shell then that is why daniel will need +rx for the Data folder, so it can get to the daniel folder in the first place. It is really good practice to make your smb.conf mirror what your current permissions are in the filesystem. What you are trying to do would circumvent the permission in the filesystem, not saying that it can not be done, just that it is not best practice.

---

### Post by luvshines on 2010-10-24
Just noticed that your [Data] share has 'valider users' instead of 'valid users'. Is that a typo ??
Maybe that typo will not enforce sysadmin access only

---

### Post by Ambiorix3 on 2010-10-24
Thank you for all the replies. I managed to find the solution thanks to Boondoklife. Indeed, the user daniel has to have rx permissions to the data disk so he can access it, but in the smb.conf file i have to set him as invalid user so he can't map de drive directly.


For me this is SOLVED

---

### Post by Morbius1 on 2010-10-24
But daniel already had rwx group access to the Data partititon:
> This is what my permissions look like:

[IMG]http://img46.imageshack.us/img46/3476/permissionsmountpoints.png[/IMG]And he already had rwx group access to his assigned directory:
> and the permissions inside de Data harddisk:

[IMG]http://img525.imageshack.us/img525/1010/permissionsdata.png[/IMG]What is it I'm missing?

---

### Post by Ambiorix3 on 2010-10-24
Maybe the typo i corrected. The strange part is, is that it works like 90% of the time. I think windows (i'm mapping the drives on a windows machine to test it out) has issues with authentication when i map/unmap drives too fast. 

All i can say is that in theory my setup should work and it does so thanks all :)

---

