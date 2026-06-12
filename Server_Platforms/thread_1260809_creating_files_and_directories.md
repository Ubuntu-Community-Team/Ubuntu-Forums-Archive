---
title: "creating files and directories"
date: 2009-09-08
forum: Server Platforms
---

### Post by krraleigh on 2009-09-08
I read an article a while back that showed me how to stop files and folders from being created in a directory, and I can't remember where I found it or what I should search on. What I want to do is log in via winscm and be able to upload or create files and directories
 
Right now to create directories for my web server I am logging in using openssh and using adduser and adding the paths to my sites-available. And ultimately I have a new folder for each website that I am hosting.
 
I am thinking this is to complicated and that all I really need to do is use /var/www and setup my files for the different websites in here. I am thinking that it is probably a better approach on all fronts but I am not sure why.
 
Anyway I need to be able to log in using winscm and up load new directories and files and right now I don't have permission. Can you advise on this simple issue? I am sure that this question has been asked many times I am just not sure on how to search for it.
 
And if you have time would you care to lend your wisdom on setting up under /var/www or adduser newUser with the end result being /newUser/www
 
 
any insight is always appreciated :guitar:
 
thanx for your time
Kevin

---

### Post by krraleigh on 2009-09-08
I figured out that I needed to chmod the home directory to 777 and the webroot to 777 to get winscm to let me upload files.
 
The other question on the wisdom of creating new users instead of using /var/www/newuser is still of interest. So if any of you busy folk out there have time I would appreciate your input
 
Kevin:popcorn:

---

### Post by terazen on 2009-09-08
Would `adduser --home /var/www/something` be what you are looking for?  Read the man pages for useradd/adduser for other options.  If you have a couple of default things you do it may be easier to just write a script to add the user and the folders.

Also, I wouldn't necessarily chmod 777.  You might want to add your winscm user to a group and give the group permissions to /var/www.  Then maybe chmod 764...

---

### Post by scorp123 on 2009-09-08
> **krraleigh said:**
> webroot to 777 to get winscm to let me upload files. Hey nice!!!! **[COLOR="Red"]A _world-writable_ web root folder![/COLOR]** :D

Can you give me your web site's name please? I have some illegal porn I want to upload somewhere. Just give me the name of your web site please? You don't even need to give me any username or any password. The permissions up there pretty much make sure that me and my 1200 or so spammer friends in North Korea and China can write into that directory too in any case. Nice job!! Thanks so much. ):P

It's really hard to find many open web servers these days, you know? With those security-minded people everywhere me and my spam-spreading friends really have a hard time finding web sites that we can take over. But hey --- now we have found you and your lax permissions. Nice job! It makes our lives sooo much easier.

Oh ... You do know a good lawyer, right? You see, some of the stuff we're going to upload onto your server is highly illegal in your area (oh well: actually on the entire friggin' planet I guess??) ... But because it's your web server they are going to bust you ... Not us. We will remain in the shades and will leave the spotlight and all the attention to you. Isn't that great? You get all the action while we have to sit back and watch ...  Oh, unfortunately it will not be possible for us to share any verdicts with you. Sorry about that. But I am sure you will find plenty of new buddies behind those bars ... (hint: when you're in the showers, don't pick up the soap .... )

End of sarcasm.

Sorry if the above was rude. But I hope you now realise what you just did? You not only opened a big security hole on your system out of your lack of knowledge ... you also publicly announced it to the entire world. So anyone keen on finding a badly protected web server now just has to find you. Done. One more web server under someone else's control.

So I strongly suggest you learn what "chmod 777" really means and never ever do that again if you're not 100% sure such lax permissions are really needed. OK?

---

### Post by Sporkman on 2009-09-09
> **scorp123 said:**
> Hey nice!!!! **[COLOR="Red"]A _world-writable_ web root folder![/COLOR]** :D

Can you give me your web site's name please? I have some illegal porn I want to upload somewhere.

...or some php files. :)

Ditto what he said, you want to be very careful in setting up permissions on web-served or any internet-accessible directories.

---

### Post by Bachstelze on 2009-09-09
> **scorp123 said:**
> Hey nice!!!! **[COLOR="Red"]A _world-writable_ web root folder![/COLOR]** :D

Can you give me your web site's name please? I have some illegal porn I want to upload somewhere.

[http://open.fkraiem.org](http://open.fkraiem.org)

DocumentRoot is chmodded 777. I'm waiting for you. :)

---

### Post by scorp123 on 2009-09-09
> **HymnToLife said:**
> [http://open.fkraiem.org](http://open.fkraiem.org)

DocumentRoot is chmodded 777. I'm waiting for you. :) I'll tell it to my friend "bitchecker" ... :D

Read & enjoy:
[http://www.disk919.com/bb2/bitchecker.html](http://www.disk919.com/bb2/bitchecker.html)

(Yes, apparently this really happened ... ](*,) :lolflag: )

---

