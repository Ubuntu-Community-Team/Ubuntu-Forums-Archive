---
title: "Remote access to shares through Apache?"
date: 2005-12-10
forum: Server Platforms
---

### Post by Mujaheiden on 2005-12-10
I've installed apache, and it works properly. Now i would like to set up a directory like [http://localhost/music/](http://localhost/music/) which redirects internally to my mp3 folder, which is on another partition, eg. not in /var/www/.

Is this possible? Is this in some way a securty hazard?

---

### Post by cactus on 2005-12-10
as root:
ln -s /path/to/mp3s /var/www/music

then just make sure your mp3s are readable to the apache process. you should be golden.

---

### Post by LordHunter317 on 2005-12-11
Using ln is not preferable to setting up an Alias in the appropriate part of  httpd.conf or your specific sites file:```
Alias /srv/mp3 /music
<Directory /srv/mp3>
Option Indexes
Order allow,deny
Allow from All
</Directory>
```This has the specific advantage that you can set apache specific configuration directly, which you cannot do with a symlink unless you use .htaccess.  Which isn't preferable unless you must.

---

### Post by cactus on 2005-12-11
Semantics. 
If you don't need to any special configurations, then it doesn't really matter.

And using ln is very often how large virtual hosting companies set up the vhosts. 
They just symlink the user's apache vhost directory to an inode in the user's home directory..

/me shrugs
but either way should work.

---

### Post by bursto22 on 2005-12-11
Take note that the ubuntu starters guide does something slightly goofy with the alias syntax and the above quote by lord hunter is best i think but i would also still check the starter's guide

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=cactus]Semantics. 
If you don't need to any special configurations, then it doesn't really matter.[/quote]Yes, but many people don't even realize they can do it that way, which is why when helping people online, it's always prudent to show the best way unless there are other factors.

> And using ln is very often how large virtual hosting companies set up the vhosts. 
They just symlink the user's apache vhost directory to an inode in the user's home directory..That's a different situation.  Apache doesn't use that symlink.

---

### Post by cactus on 2005-12-12
[QUOTE=LordHunter317]That's a different situation.  Apache doesn't use that symlink.[/QUOTE]

It doesn't?
Sure it does...

/var/www/vhosts/site.domain.net -> /home/user123/site.domain.net

I have seen many hosting companies use such a setup. True, many others symlink in the other direction, but that wasn't really the case I was talking about.

But in the grand scheme of things, this doesn't really matter at all. The solution you presented to the user is quite workable. 
*shrug*

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=cactus]It doesn't?
Sure it does...[/quote]You described it going the other way.  From /home/user to /var/www/vhosts.  That is why I was confused.


> I have seen many hosting companies use such a setup.They also expect the user to use .htaccess within that directory since the specific directives applied are beyond them.  In that case, symlinks provide no difference from aliases.

---

### Post by cactus on 2005-12-12
oops. yeah. looks like my original text about symlink direction was a tad misleading.
>_<

note to self: dont try to make sense when you are tired.. ;)

---

### Post by Mujaheiden on 2006-03-14
Hi again.
Thanks for the elaborate discussion, HTTP shares work fllalessly now. I just wonder; can't I not make a public FTP for the same thing? Again coming to my music collection, I would like people who have my address to be able to grab entire folders, and FTP is the way to go there. So I dont need accounts, write acces, etc. Any more thoughts on how to plunge forward here?

---

### Post by brok3n on 2006-03-15
[QUOTE=Mujaheiden]Hi again.
Thanks for the elaborate discussion, HTTP shares work fllalessly now. I just wonder; can't I not make a public FTP for the same thing? Again coming to my music collection, I would like people who have my address to be able to grab entire folders, and FTP is the way to go there. So I dont need accounts, write acces, etc. Any more thoughts on how to plunge forward here?[/QUOTE]

You should try [http://ampache.org]("http://ampache.org") for your music playing needs. I've got that running at home and it works great. 

As for the FTP side of it, just set up FTP accounts and have the accounts default directory point to your music share's directory so when they log in all they have access to is your music share.

---

### Post by Mujaheiden on 2006-03-18
OK, to answer my own question;

I followed the instructions for Vsftpd on [http://www.ubuntuforums.org/showpost.php?p=501728&postcount=1](http://www.ubuntuforums.org/showpost.php?p=501728&postcount=1)

changed ownership of /home/ftp to regular user (example; samurai - I dont get why this wasnt in the previous instruction)

```
sudo chown samurai /home/ftp
```
and mounted my music share
```
cd  /home/ftp
mkdir music
sudo mount --bind /path/to/mp3s /home/ftp/music
```

To **permanently** mount your shares, you need to alter the /etc/fstab according to the changes which you now made to the /etc/mtab file, in my case
```
#added for public ftp 
/path/to/mp3s /home/ftp/music none rw,bind 0 0
```

done!

---

### Post by saads on 2006-03-20
Mujaheiden, did u figure out how to unmount the drives?  Once i bind them i can't unmount them - even after stopping the vsftpd server:

```
$ sudo umount --force d/
umount2: Device or resource busy
umount: /home/ftp/d: device is busy
umount2: Device or resource busy
umount: /home/ftp/d: device is busy

```

---

