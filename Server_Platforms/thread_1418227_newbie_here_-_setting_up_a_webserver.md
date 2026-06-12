---
title: "newbie here - setting up a webserver"
date: 2010-02-28
forum: Server Platforms
---

### Post by Turiko on 2010-02-28
first of all: i'm a complete newbie at hosting, and i've only used ubuntu's console a bit before. I am trying to get an ubuntu system up with remote access that will host a single asp.net website.

I have installed apache and mono. I can access the site, but when i do, all i get is a directory listing. Opening any of the .aspx files results in a 403 - forbidden error.

I have left the various files in apache's sites-available and sites-enabled alone; all i did was delete the default.html file, put in my website and enable the mono mod (with sudo a2enmod mod_mono).

I've gone through 2 or three tutorials, but none of them got me a working solution. I've undone all of the changes i did, because with these changes, apache wouldn't even restart anymore.

Is there anyone that can help me? I don't know anything about how apache works, and i can't rely on the tutorials i find...

---

### Post by hhacckerr on 2010-02-28
Check to make sure that Apache has permission to read and execute the files. Just chmod the files to 755, and it should probably fix your problems.

---

### Post by junke1990 on 2010-02-28
try 
```
sudo chmod u=rwx,go=rx /var/www/FILE
```


**by far not the smartest thing to do!!!!** 
but this will fix all your permission problems:

```
sudo chmod -R ugo+rwx /var/www
```

give all the rights to everybody, to all the files in /var/www and beneath it.

---

### Post by Turiko on 2010-03-01
Thank you, that fixed the permissions. But, now i still have a directory listing rather then an actual site. When clicking through on the .aspx files, they get downloaded rather then opened.

I guess this is a problem with mono not serving the .aspx pages, but i really do not know where to look. The only uncommented line in /etc/apache2/mods-enabled.conf is this:

Include /etc/mono-server2/mono-server2-hosts.conf

And that file is the default one, which i have not edited.

I may be looking i nthe wrong direction, but i really don't know where else to look. It looks like a problem with mono.

---

### Post by tlsarles on 2010-03-01
Simply guessing here, but you may need a connector that allows Apache and Mono to 'see' each other, as it seems that the ASPX files are being treated as simple files, rather than being executed by Mono as they should. Should check your Apache config and see if there is a reference to a mono module

---

### Post by Turiko on 2010-03-01
after some more googling, i found i had to enable the mod_mono_auto module.

Now i get a HTTP 500 error.

System.InvalidOperationException: Process has not been started.

I have found a lot of fixes about gmcs being missing, but from what i understand, this is the C# compiler. I am using VB.net on my asp.net pages, and i think mono should be able to compile vb.net code. So, is there a module out there i would need to install to have vb.net up and running?

---

