---
title: "Not a directory?"
date: 2011-05-19
forum: Server Platforms
---

### Post by garyjmellor on 2011-05-19
Hello
 
I'm a little confused. I used wget to download a file. When it was downloading, according to the output, it placed it into what I thought was a directory called 'download'. However, when it finished and I tried to cd into it using 'cd download' I get '-bash: cd: download:  Not a directory'. When I type 'ls' it clearly lists 'download' as being in my working directory. Why isn't this working? I'm new to Ubuntu Server (currently using 11.04 Natty) so it is defintely a fault between the keyboard and the seat :o) Can someone point me in the right direction please?
 
Regards
 
Gary.

---

### Post by Grenage on 2011-05-19
Howdy ;)

What it means is that what you have downloaded is a *file*, and not a *directory.*

---

### Post by garyjmellor on 2011-05-19
Hi grenage,
 
Thank you for your reply. The file I downloaded is supposed to be a .zip. I assumed (wrongly I realise) that this .zip was placed into the download directory. I pointed wget at this location: [http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip/download](http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip/download) and I can now see why it saved it as 'download'. However, what I need is the .zip. If I point my browser on my desktop at: [http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip]("http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip/download") it fails. I'm not stumped as to how to get the zip file I need. Any ideas?
 
Thanks
 
Gary.

---

### Post by garyjmellor on 2011-05-19
Problem solved - I did what I said I did in my browser and it worked fine :o)

---

### Post by Grenage on 2011-05-19
> **garyjmellor said:**
> Hi grenage,
 
Thank you for your reply. The file I downloaded is supposed to be a .zip. I assumed (wrongly I realise) that this .zip was placed into the download directory. I pointed wget at this location: [http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip/download](http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip/download) and I can now see why it saved it as 'download'. However, what I need is the .zip. If I point my browser on my desktop at: [http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip]("http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip/download") it fails. I'm not stumped as to how to get the zip file I need. Any ideas?
 
Thanks
 
Gary.

Hi Gary,

Did you try copying the URL of the *direct link* hyperlink? For example, this works for me:

```
wget http://downloads.sourceforge.net/project/subsonic/subsonic/4.4/subsonic-4.4-war.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fsubsonic%2Ffiles%2Fsubsonic%2F4.4%2Fsubsonic-4.4-war.zip%2Fdownload&ts=1305817653&use_mirror=leaseweb
```

How large is the file you downloaded? It's possible that the name of the original file simply hasn't been preserved.

This also works for me:

```
wget http://sourceforge.net/projects/subsonic/files/subsonic/4.4/subsonic-4.4-war.zip
```

---

### Post by Grenage on 2011-05-19
> **garyjmellor said:**
> Problem solved - I did what I said I did in my browser and it worked fine :o)

Glad you got what you need. :)

---

### Post by RivetingScholar on 2011-05-19
Wget streams the file from the webserver. Webpages, like this one, aren't always displayed with the traditional file naming convention (i.e. file.extension). Quite often, querystrings or rewrites are used (e.g. showthread.php?t=1762600, showthread.php/t/1762600/). Whenever you wget a file like this, wget ends up naming the file with the webserver's naming convention.

Many websites have scripts that stream files from a database (e.g. download-zip-file.php?id=1); so, you end up with the same problem even regardless of the filetype. You might be able to get aroung this by using a command like:

```
wget http://website.com/retarded-naming-convention-for-zip.php?id=1 >> 1.zip 
```Though, I have not tried this. Sometimes I just use wildcards to rename these files.

---

