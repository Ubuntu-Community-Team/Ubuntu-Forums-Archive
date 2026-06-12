---
title: "running out of space when running this cmd"
date: 2011-04-04
forum: Server Platforms
---

### Post by Foeburner on 2011-04-04
I'm using 10.10 with duplicity and when I run this cmd ```
duplicity --encrypt-key "########" --sign-key "########" /media/backup/ scp://username@x.x.x.x/home/username/backup
```
I use up all the space available in my root partition. The root partition is only 8GB total and about 4GB free usually. 

all help is appreciated. 

Thanks!

---

### Post by Foeburner on 2011-04-06
Just found that duplicity is caching files in my home directory (which is understandble). 

Any way I can redirect where to cache these files? 

My root partition is only 8GB and my var partition is 600GB. 

Should I enlarge my root partition instead?

---

### Post by BkkBonanza on 2011-04-06
If you want to have files cached on the var partition then you can simply use a symbolic link. 

eg. if the place where files are cached is /home/user/.cache then you can do,

```
sudo mkdir /var/mycache
sudo chown user /var/mycache
mv /home/user/.cache/* /var/mycache
rmdir /home/user/.cache
ln -s /var/mycache /home/user/.cache
```

where mycache is just some name I made up, and user is your userid.

Now any files written in /home/user/.cache actually get stored under /var/mycache.

Also note, rather than increasing your root partition it makes more sense to create a new home partition and mount it on home.

When you create a new mount be sure to copy pre-existing files before mounting or else they will seem to vanish under the mount. They're still there though.

---

### Post by Foeburner on 2011-04-06
Thanks!!

When I tried ```
mv /home/user/.cache/* /var/mycache
```

I got this output:
```
mv: cannot open `/home/user/.cache/motd.legal-displayed' for reading: Input/output error

```

of course, i removed my username from above.

I googled what this motd could be and read that it's unnecessary. Could I remove the folder?

---

### Post by BkkBonanza on 2011-04-06
That's odd. I gather this is an input file for the motd message that appears at login. I don't see why it wouldn't be readable though. Mine is 0 byte and obviously contains no "message". It doesn't appear to have any special flags. 

You can probably just delete it and make a new one in the new location using touch.

touch /var/mycache/motd.legal-displayed

---

### Post by Foeburner on 2011-04-07
so i deleted that file and ran the cmd again. 

This is the output:
```
mv: cannot stat `/home/afuentes/.cache/*': No such file or directory
```

I tried running it as 
```
sudo su
```

same output but i clearly see it in nautilus.

---

### Post by Foeburner on 2011-04-07
```
mv: cannot stat `/home/user/.cache/*': No such file or directory
```

Hmmm, I just noticed that I deleted everything in the .cache folder before getting a reply from you. 

Could that be the cause of the output? Could I start doing the other cmds or am I stuck until I'm able to move this folder over?

---

### Post by Foeburner on 2011-04-07
Nvm I got it!

so if I understand ur cmds, you had me create the mycache folder, move the contents of the .cache folder over to /var/mycache/ then delete the .cache and then added the symbolic link back to mimic .cache folder.

So even if I deleted the items in the .cache folder before, it wouldnt affect me because /var/mycache is now my .cache folder. 

Awesome!!! 

Thank you so much!!!

---

