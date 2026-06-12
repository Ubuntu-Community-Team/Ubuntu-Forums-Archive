---
title: "Ftp or other access to /var/www?"
date: 2006-06-16
forum: Server Platforms
---

### Post by Ixzat on 2006-06-16
Is there any way that i can get ftp access, or any other access like dav or something to access my /var/ww on my server? 

I want to do this because i want to be able to edit my site from other machines instead of having to ssh in and edit them with nano everytime.

This will mostly be done on my internal network, i tried using samba for this, however, when i tried to set force user/group to www-data i get read access, but no write access.

---

### Post by localzuk on 2006-06-16
Why not use sftp? If you have ssh enabled already this should do the job fine. Many development apps already support connecting via sftp.

If not, what do you mean by 'when i tried to set force user/group to www-data'? Where did you do this?

---

### Post by Ixzat on 2006-06-16
I just tried sftp, i set up a password with the user www-data, and everything worked fine untill i tried to save or delete a document. Seems like i just got read access, is there a way to fix this, that would solve my problem.

And as for 'when i tried to set force user/group to www-data'?, i did it in smb.conf...

---

### Post by localzuk on 2006-06-16
Does www-data have write permissions to the files?

---

### Post by LordHunter317 on 2006-06-16
***Never ever, ever access the system as www-data interactively***

With the exception of a few system accounts in a few cases (postgres, being the biggest example) ***Never, ever, EVER use a daemon account in an interactive context.***

It's bad.  Dangerous.  Don't do it.  The account was dedicated to teh daemon for a reason.

Anyway, just connect as yourself.  If you're the one maintaining /var/www, then you should own /var/www and have write access there.  Grant apache read access via the world set of bits (the last one).  If your umask doesn't have '7' for the last bit, it should get them automatically.  If not, change the permissions to be suitable.

---

### Post by Ixzat on 2006-06-16
Well, i removed the password again from www-data as i could not use it i thought i could.

The problem is though, that apache sometimes need to write to files since i´m using some php scripts on my site. And if i make the /var/www dir chowned by me, apache wont be able to do so, right? Or is that what you mean by "If your umask doesn't have '7' for the last bit"? 

Just to make sure that i will do everything right here, chown /var/www to me, both my user and group, or just my user?
Set chmod something like 747 to the whole /var/www?

And just another question, what do you mean by "it should get them automatically. If not, change the permissions to be suitable."? How can i set the system this way?

Sorry if this is a stupid question, ife been using linux on and off for a few years, but i never really got the hang of file permissions and such.

---

### Post by LordHunter317 on 2006-06-16
[QUOTE=Ixzat]The problem is though, that apache sometimes need to write to files since i´m using some php scripts on my site.[/quote]So give it write access to those specific directories.  It should not have write-access *anywhere* unless it absoultely needs it.  And if you can, I'd move those writable areas outside the webroot anyway.

> And if i make the /var/www dir chowned by me, apache wont be able to do so, right?No, that's not true in the least.  It only needs write on the last directory in question.

>  Or is that what you mean by "If your umask doesn't have '7' for the last bit"? No.

> Just to make sure that i will do everything right here, chown /var/www to me, both my user and group, or just my user?Either/or.

> Set chmod something like 747 to the whole /var/www?No, because that would screw up execute permissions on your files.  Something like:```
sudo chown -R me.me /var/www
sudo chmod u=rwX,g=rX,o=rX
```Is suitable.

> And just another question, what do you mean by "it should get them automatically.If your umask is set correctly (umask determines what permissions are *not* present) then www-data will automatically get read access to the files.  If it doesn't, you can always just run chmod and grant them.

---

### Post by Ixzat on 2006-06-17
Thank you for your reply, i think i got a little more understanding for how file permissions really work now.

Once again, thank you for all your help!

---

