---
title: "Apache; access all files, full permissions HOW?"
date: 2011-10-19
forum: Server Platforms
---

### Post by kirollos210993 on 2011-10-19
Hey,

Im running 11.10

I would like to access all files, no matter the owner, through http server (apache), but i dont know how to do it.

Can somebody help me?

I have webmin installed, if you would like me to use that, whatevers easier.

Thank you :D

---

### Post by Dangertux on 2011-10-19
Do you realize the security implications behind what this are?

If apache can access ALL files, regardless of owner, you pretty much just put a rooted box on the network. Is that really what you want to do?

---

### Post by kirollos210993 on 2011-10-19
Hey Dangertux,

yea but whos going to access my server when its just a home server, no body even knows my website. Can you upload with apache though? Ive only been able to just view a directory listing.. anyway, so its unsecure, so lets make it so that they have access to files which i am allowed to access, i.e. i can access through nautilus when i browse my filesystem.

Would it be possible to allow only for them to view all files, no matter the owner, or would that still be unsafe?

---

### Post by Dangertux on 2011-10-19
Well -- the concern comes in with Apache reading things like /etc/shadow- and /etc/passwd even if it can only read those are some things you probably don't want read. 

Yes apache can upload files, enable DAV method PUT and you'll find it works quite nicely.

I really think this is a bad idea. If you're so inclined to do this I'm going to suggest you consult the Apache documentation , hopefully it can persuade you to pursue alternative methods for managing files like SSH or in this case even FTP would be preferable.

---

### Post by kirollos210993 on 2011-10-19
hey, thanks. mmm is there a way to set which directories you want to be seen so then i can choose the directories i want full permissions for? So when i put [http://localhost](http://localhost) in my computer, only the directories specified from the root directories will appear..?

thanks

---

### Post by Dangertux on 2011-10-20
> **kirollos210993 said:**
> hey, thanks. mmm is there a way to set which directories you want to be seen so then i can choose the directories i want full permissions for? So when i put [http://localhost](http://localhost) in my computer, only the directories specified from the root directories will appear..?

thanks

You could in theory if you want to, again this is a BAD idea. 

Add www-data to the group that owns the directories you want read :-/

---

### Post by bodhi.zazen on 2011-10-20
> **kirollos210993 said:**
> Hey Dangertux,

yea but whos going to access my server when its just a home server, no body even knows my website. Can you upload with apache though? Ive only been able to just view a directory listing.. anyway, so its unsecure, so lets make it so that they have access to files which i am allowed to access, i.e. i can access through nautilus when i browse my filesystem.

Would it be possible to allow only for them to view all files, no matter the owner, or would that still be unsafe?

If you are going to want to learn to manage servers, learn to manage them securely.

IMO files in /var/www should be owned by root:www-data 

Files should have permissions of 440

The reason, if for some reason apache is compromised, these permissions are your first line of defense.

> Would it be possible to allow only for them to view all files, no matter the owner, or would that still be unsafe? are famous last words ;)

---

### Post by Dangertux on 2011-10-20
> **bodhi.zazen said:**
> If you are going to want to learn to manage servers, learn to manage them securely.

IMO files in /var/www should be owned by root:www-data 

Files should have permissions of 440

The reason, if for some reason apache is compromised, these permissions are your first line of defense.

 are famous last words ;)

+1 this is good advice.

I'm curious what is it you're trying to accomplish. Surely there has to be a better method.

---

### Post by kirollos210993 on 2011-10-20
Hey everyone,

thanks for the replies,

> If you are going to want to learn to manage servers, learn to manage them securely.

IMO files in /var/www should be owned by root:www-data 

Files should have permissions of 440

The reason, if for some reason apache is compromised, these permissions are your first line of defense.

> 

I'm curious what is it you're trying to accomplish. Surely there has to be a better method. 

hey thanks for the replies. 

Im not really hosting a website or anything, i just want to access my files through that directory listing thing. I know about ftp, but thats too slow from experience, apache is much faster, almost instantly loads. I just want to be able to access my files from any device which can access the internet.

Anyway, thanks guys, i was able to do it from this youtube video ([http://www.youtube.com/watch?v=w1j7WcdUo7g](http://www.youtube.com/watch?v=w1j7WcdUo7g)) just so if anybody needs to do this.. and ill make sure i keep those permissions limited!

but thanks everyone, enjoy your day!

---

