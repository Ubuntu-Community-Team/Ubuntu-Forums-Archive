---
title: "Accessing files over sftp"
date: 2009-05-26
forum: Server Platforms
---

### Post by ensou on 2009-05-26
Hi,

I set up my server so that /home/Web/www was present for public access to the web server. Over sftp with user Web, I am unable to replace files in the /home/Web/www/html folder (only delete and upload), and unable to do ANYTHING other than view in /home/Web/www/html/*/ (only read). Why is this? How can I fix it? I can't chmod over ftp because it says permission denied.

I do have access to the server box, but it is in another location.

---

### Post by albinootje on 2009-05-26
> **ensou said:**
>  Over sftp with user Web, I am unable to replace files in the /home/Web/www/html folder 

Did you set the permissions properly ? You can log in via ssh, and perform :
```

ls -la /home/Web/www |less  (to check the ownership)
sudo chown -R Web /home/Web

```
And I'm surprised that your user is called "Web" because that would be a bad username :
```

$ sudo adduser Web

adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX or NAME_REGEX_SYSTEM.

```

---

### Post by ensou on 2009-05-26
> **albinootje said:**
> Did you set the permissions properly ? You can log in via ssh, and perform :
```

ls -la /home/Web/www |less  (to check the ownership)
sudo chown -R Web /home/Web

```
It won't let me log in as Web over ssh...
> 
And I'm surprised that your user is called "Web" because that would be a bad username :

It's not actually called Web, i am just using that for the sake of keeping it simple (it's really a bunch of random letters)

---

### Post by albinootje on 2009-05-26
> **ensou said:**
> It won't let me log in as Web over ssh...

You wrote that you have set up that server, so then I assume you have the possibility to change those permissions in some other way, 
or contact the administrators of that box to do it for you.

---

### Post by ensou on 2009-05-26
> **albinootje said:**
> You wrote that you have set up that server, so then I assume you have the possibility to change those permissions in some other way, 
or contact the administrators of that box to do it for you.

Yes, yes, I can. And I am at it right now. 

So I see for the main folder it says (after doing ls -la /home/Web/www |less  suggested above)
```
-rwxr-xr-x  1 Web Web
```

and for the ones I can't do anything in

```
-rwxr-xr-x  1 Web root
```

Not sure what to do.

---

### Post by albinootje on 2009-05-26
> **ensou said:**
>  So I see for the main folder it says (after doing ls -la /home/Web/www 

If your user is the owner of files, then it should be possible to edit them, or overwrite them.

What sftp client are you using ? Nautilus, Konqueror, gftp, WinSCP, or.. ?

---

### Post by ensou on 2009-05-26
> **albinootje said:**
> If your user is the owner of files, then it should be possible to edit them, or overwrite them.

What sftp client are you using ? Nautilus, Konqueror, gftp, WinSCP, or.. ?

Well perhaps root being in there means something?

I am using WinSCP

---

