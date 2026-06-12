---
title: "Samba share within ecrypted home folder"
date: 2012-05-15
forum: Server Platforms
---

### Post by morrison1977 on 2012-05-15
Is there any way that I can have a share within an encrypted home folder?
I actually want the data within the share to be encrypted and accessible to network users as a safe place to put pii.
Thanks much!

---

### Post by Morbius1 on 2012-05-15
I don't actually know as I have never encrypted my home folder but you could try something:

In your share definition in smb.conf add the following line:
```
force user = morbius
```[COLOR=Blue]*Change morbius to the name of the owner of the home directory.*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```After the remote user is authenticated or if you have this set up as a guest share he will be converted to morbius. Presumably morbius has access to the encrypted directory and so should the remote user.

Anyway, just a thought.

---

### Post by morrison1977 on 2012-05-16
Thanks, I'll give it try.

---

### Post by CharlesA on 2012-05-16
It probably won't work unless the user is logged in.

---

### Post by morrison1977 on 2012-05-18
Well, it is working, I'm not sure if it is working the way I want it to though, my only concern is whether the authentication takes place before it forces the account.  Currently my settings are approximately like this:

[Share_name]
path = /home/username!/share
read only = no
Public = no
writable = yes
valid users = domain\user +domain\user group
force user = username!

So from what I see the local account create the files, which better then it not working at all, but it'd be great if I could see domain credentials so tracking/auditing of file access and ownership could be done.  But my goal has been achieved, files can be stored in an encrypted folder and accessed by users across the network to a share.  Thank you sir.

---

