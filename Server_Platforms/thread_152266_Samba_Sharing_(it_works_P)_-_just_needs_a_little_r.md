---
title: "Samba Sharing (it works :P) - just needs a little reconfiguring :)"
date: 2006-03-29
forum: Server Platforms
---

### Post by Cyorxamp on 2006-03-29
Hi,

My server box shares my largest hard disk known as the MediaDisk (or /mediadisk) so that my other computers can access the files on it (mainly things downloaded from the net, not stuff I have created myself).

I have been using Samba (and SWAT to administrate it... please no comments about SWAT in this thread) to share it but I have been finding it difficult to do something.

I want to share MediaDisk as read only to everybody on the network (as in no need to log-in either for the computer or the share) but also I want the ability to log-in as 'cyorxamp' (root would be fine also) so that I can have have read/write abilty.

I have foxed with options for an unbelievable amount of time and now I have gone back to 'everyone has write access' settings (which work).

The following is a link to my current samba config file.

[http://cyorxamp.info/smb.conf](http://cyorxamp.info/smb.conf)

I really hope someone out there knows how to do this!
Despite looking at the manuals - everything I try fails in one way of the other!

Thanx!

---

### Post by Iowan on 2006-03-30
Probably a more elegant way exists, but one option would seem to be editing the permissions for the /mediadisk directory.  Change the owner (chown) to **cyorxamp**, **chmod** to give the owner write privileges.  There is a Samba command which about the same thing - but my book is at home (and I'm not). With it, you can specify which user(s) have write access to the share.

---

### Post by Cyorxamp on 2006-03-30
Nope sorry,

I did what you said and even without logging into the share I can still write to it.

---

### Post by Iowan on 2006-03-30
What happens if you set **read only = yes**?

---

### Post by Cyorxamp on 2006-03-30
Then wether I identify myself as Cyorxamp or not to the server, it still means I can only read not write.

---

### Post by Iowan on 2006-03-31
Try adding **write list = cyorxamp** below the **read only = yes**.

If that doesn't work, try :
[B]read only = no
write list = cyorxamp[/B]

From [http://www.server-resources.com/samba.html]("http://www.server-resources.com/samba.html")
> 
[public]
comment = Public Stuff
path = /home/samba
public = yes
writable = yes
printable = no
write list = @techies

So, here we see that anybody can come in, and that the directory is not printable, but that it can be written to. The secret here is that the write list variable tells samba *who* can write to it; in this case it's only the people who belong to the group called techies. You can put usernames there, instead of the @group thing, and the result is that only the users mentioned can write to that dir, but this can become a maintainance nightmare if you have people moving in and out of the group that can/should write to that share.

---

### Post by Cyorxamp on 2006-03-31
Ok I tried both of your 'read only' and 'writable' options and they did not help but I did try that URL you gave and based my configuration file on it exactly...

[http://pastebin.com/633076](http://pastebin.com/633076)


However without having logged in as 'cyorxamp' anywhere -- I can STILL write files in this share!

---

### Post by Iowan on 2006-03-31
Well... I wonder if replacing **public = yes** with **guest ok = yes** would work?  The link suggests otherwise, but it's an option to check.  Another option might be **read list = guest**.  That "should" restrict guests (users without accounts) to read-only.  
From what I've read, the **read only = yes**  together with the **write list = cyorxamp** should have accomplished what you want...

---

### Post by LordHunter317 on 2006-04-01
No.  Stop guessing.

Setting 'read only=yes' and 'write user = bob' will work.  I know it works.  'write user' always overrides.

However, *there should be no need to override smb.conf in this situation.*.  Give your user ownership and read/write over all the files.  Give group and other read-only permissions via chmod.  You're done.  Samba always obeys filesystem permissions unless you did something fishy.

---

### Post by Cyorxamp on 2006-04-02
Ok... what if I were to say that /mediadisk (the thing I am sharing) is a FAT32 partition?

Does that make any difference?

---

### Post by LordHunter317 on 2006-04-02
[QUOTE=Cyorxamp]Does that make any difference?[/QUOTE]It does in the sense that chown/chmod don't work on it, so you can't change file permissions that way.

In which case, you'll need to configure everything through smb.conf and possibly use 'force user' and/or 'force group' to control who samba does file accesses as.

---

### Post by Cyorxamp on 2006-04-02
Does anyone know of a good example of a smb.conf file where those have been used?  Samba seems rather retarded at this point.

---

### Post by mellowdave on 2006-04-05
yeah one of the absolute most commonly used and relied upon applications in the *nix world is retarded...

heheh 

operator headspace and timing.

---

