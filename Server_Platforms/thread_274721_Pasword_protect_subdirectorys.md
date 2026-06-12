---
title: "Pasword protect subdirectorys"
date: 2006-10-10
forum: Server Platforms
---

### Post by nibbo on 2006-10-10
Hi

I have a small filehosting service for my friends. In ther directory i want to have one dir named private that is password-protected by apache. I know how to password-protect pages but is there any way to tell apache: In every subdirectory of this dir password-protect the following directory?

---

### Post by kidders on 2006-10-10
Hi there,

I don't think exactly what you're describing is possible, but you could create a collection of .htaccess files and copy them into all the applicable directories ... which would be *almost* the same thing.

Consider a .htaccess that goes something like this:
```

AuthUserFile /var/www/.htpasswd
AuthGroupFile /dev/null
AuthName EnterPassword
AuthType Basic

require user whoever

```

Imagine the directory you want to protect is at /home/whoever/www/private. You could save your .htaccess file as /tmp/crap and try ...

```

for i in /home/*; do if [ ! -e $i/www/private ]; then mkdir $i/www/private; fi; done
for i in /home/*; do sed 's/whoever/'`basename $i`'/' /tmp/crap > $i/www/private/.htaccess; done

```

That way, all your users would have a default .htaccess that they can play with when they get the chance. In the meantime, they would all use /var/www/.htpasswd, that might contain a list of dummy passwords.

There are some important steps that I left out (like chowning and chmoding the new /home/whoever/www/private directories), but I wonder if the general idea would be suitable for you.

**Edit:** I just realised that the commands I suggested are ... well ... completely impenetrable (at least to beginners)!! Here's a quick explanation:

The first "for..." creates /home/<username>/www/private directories that don't already exist. If you were actually going to try this, you'd need to tweak the ownership of each one, and "chmod 701" it.

The second "for..." reads the sample .htaccess I posted over and over, substitutes a username for the word "whoever" (calculated from the path to his home directory), and copies the result into /home/<username>/www/private/.htaccess. Again, in practice, you would need to modify the command to give the file appropriate permissions.

This is just one way of achieving the effect you're after ... let me know if you think it's crap!

---

### Post by nibbo on 2006-10-10
Thanks alot for the tip. I have been messing around alot with passwords so i dont think I will have that much problems.

How come i didnt think about placing .htaccess files in the directorys! Anyway thanks alot man!

Ill test this later tonight and post the result here. If you come up with any improvement to the solution please let me know!

EDIT: Just remembered a thing, won't I have to tell apache, in the main config, to allow modifications from the external .htaccess files?

---

### Post by kidders on 2006-10-10
> If you come up with any improvement to the solution please let me know! I never post anything less than perfection. [-( Improving would be impossible. Hehe (j/k ;) ).

> won't I have to tell apache, in the main config, to allow modifications from the external .htaccess files?
If what you mean is that apache's config might need to be tweaked to let people get full use out of their .htaccess files, then yes. Afaik, you can specify what sorts of things you're prepared to let people do with an "AllowOverride" directive.

---

