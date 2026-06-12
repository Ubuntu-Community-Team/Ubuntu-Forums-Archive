---
title: "Apache2 Symlink Problem"
date: 2005-05-30
forum: Server Platforms
---

### Post by drx on 2005-05-30
Hello,

i installed the apache2 and apache2-common packages -- now Apache2 will return a "forbidden" error for all symlinks. Searching the web i could not find appropriate help as other distributions seem to have the FollowSymlinks directive disabled by default. The usual hint is to set this directive. But in Ubuntu, it is the default. In apache2.conf and the default virtual host conf, FollowSymlinks is enabled everywhere.

I have put several symlinks to directories into /var/www ...

Would appreciate any help!
Greetings,
drx

---

### Post by Mez on 2005-05-30
for some reason when i installed apache, it installed apache and apache2, so you may want to check if both are installed, and check the settings for the apache not apache2

---

### Post by Mez on 2005-05-30
also, make sure that you have permisisons set up so that the user apache is running as can access those symlinks.

---

### Post by drx on 2005-05-30
[QUOTE=Mez]also, make sure that you have permisisons set up so that the user apache is running as can access those symlinks.[/QUOTE]

Hi Mez, apache 1.x is not on my system. I also noticed it was there once, but i purged the package and made a new clean apache2 install. The symlinks have correct access rights, actually for everybody.

I cannot explain it. Would it help to post the config files here?

Best greets,
drx

---

### Post by drx on 2005-06-04
Hi, i am still looking for a solution, so i cheekily post this to make the thread go up in the "last post" ordered list. ;)

---

### Post by GrumpySimon on 2005-06-04
Check your httpd.conf - you should have a section like this:
```

<Directory /usr/local/httpd/htdocs>
   Options Indexes FollowSymLinks
</Directory>

```

Basically, you need to add FollowSymLinks to all the <Directory> blocks you want sym links to be followed in. 

Next, make sure that the directories that are symlinked are world readable (if Apache can't read the files in the directory, it can't link to them, and you'll get a 403).

--Simon

---

### Post by LordHunter317 on 2005-06-04
On symlinks, it's the permissions on the destination file that matter, the link always has 777 permissions, and they are ignored.

This is most likely a configuration issue.  Post your /etc/apache2/sites-enabled/000-default, as that's the likely issue.

---

### Post by drx on 2005-06-17
Oh no, i found the source of the problem now after some time trying the config files without any success.

The problem was that all the directories in which the symlinked directory is nested need the correct permissions, too!

So if something is in /home/drx/projects/web/pulpov/ and the symlink points to the pulpov directory, not only this directory but "web", "projects" and "drx" need to be changed for correct permissions.

(Probably this means that i should store my web projects in better places than i do now, i basically have to set read access to nearly everything now.)

I hope this will help somebody to solve symlink weirdness.

Thanks to Mez, GrumpySimon and LordHunter317 for offering help. Probably this symlink behaviour is basic Unix knowledge so nobody came to the idea that i made this wrong.

Best greetings,
drx

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=drx]Oh no, i found the source of the problem now after some time trying the config files without any success.

The problem was that all the directories in which the symlinked directory is nested need the correct permissions, too!

So if something is in /home/drx/projects/web/pulpov/ and the symlink points to the pulpov directory, not only this directory but "web", "projects" and "drx" need to be changed for correct permissions.

(Probably this means that i should store my web projects in better places than i do now, i basically have to set read access to nearly everything now.)

I hope this will help somebody to solve symlink weirdness.

Thanks to Mez, GrumpySimon and LordHunter317 for offering help. Probably this symlink behaviour is basic Unix knowledge so nobody came to the idea that i made this wrong.

Best greetings,
drx[/QUOTE]
 Apache doesn't need read access on the parent directories, mearly access (bit x or 1).

---

### Post by sandoz on 2008-03-11
> Apache doesn't need read access on the parent directories, merely access (bit x or 1).

But this means that the user apache (or www-data or whatever) can read files inside all parent directories if she knows the name of the file and the file got accidentally read permissions for apache (or world).

> (Probably this means that i should store my web projects in better places than i do now [...] )

Yes, definitely!

Just for the record,
sandoz

---

