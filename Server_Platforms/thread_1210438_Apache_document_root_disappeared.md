---
title: "Apache document root disappeared"
date: 2009-07-11
forum: Server Platforms
---

### Post by borahshadow on 2009-07-11
Hi I have a file and webserver that I have monitored by montastic a free uptime monitoring service. I just got an email from montastic letting me know that my site was unreachable. I thought that there must have been a power outage. But then I opened a new tab and tried to access my site. rather than timing out I got this message. > Forbidden

You don't have permission to access / on this server. 

I VPNed in to the server and logged in; nothing seemed different. I decided to try to restart apache and found out that the document root had been deleted. I tried to find it using ls and it appeared to be there (in red) but when trying to access it over samba it was not there. Also I could not cd into the folder. I called the only person who was home with access to the server and asked her if she had done anything to the server. She said that the only thing she had done was rename the music folder from "music" to "Music" but after she had done that it looked like there were fewer items in the root directory.

In summary...
apache cannot see the document root.
ls sees it but shows it as a red color. (I don't know what the colors mean)
samba does not see it.
It disappeared after someone apparently renamed the music folder. (over samba from a windows box)

If someone could shed some light on this it would be great.

Ps. I can restore the folder from a backup but I would like to know why this happened.

PPS. I just noticed that in ls folders are blue, symlinks are light blue, and archives (zip,tar.gz, etc) are red.

---

### Post by gombadi on 2009-07-11
> 
In summary...
apache cannot see the document root.
ls sees it but shows it as a red color. (I don't know what the colors mean)
samba does not see it.
It disappeared after someone apparently renamed the music folder. (over samba from a windows box)


What is your document root?  If it is /var/www then do the following command as it displays much more information -
```

ls -la /var

```

Renaming the Music directory may be related but we don't know where on your file system the apache document root and the samba directories are. Are they the same place?

At a guess I think someone has removed/renamed things and you need to restore from backups.

---

### Post by borahshadow on 2009-07-11
Hmm thanks. That command helped. I had everything located at /data/shared and the document root was at /data/shared/www. With it set up that way I can access it over samba to make changes without adding another samba share declaration.

On my local computer I have the document root at /home/borahshadow/www and then when I synchronize to the server it copies that to /data/shared/borahshadow/www. Then there is (was) a symlink to /data/shared/www somehow that got removed but ls still shows it as this...
> lrwxrwxrwx   1 borahshadow borahshadow        21 2008-03-29 12:48 www -> /data/shared/borahshadow/www

I would like to know possible reasons why ls still shows a trace of it and how it got removed because it still puzzles me, but now all I need to do is recreate the symlink. 

Thanks for telling me to use the -la options to ls. I had forgotten I had it set up that way.

UPDATE:
I just tried to create the symlink doing 
```
cd /data/shared
ln --symbolic /data/shared/borahshadow/www

```
and it returned
ln: creating symbolic link `./www': File exists

hmm I don't really want to do rm www unless I have to.

---

### Post by borahshadow on 2009-07-13
Ok I feel really silly/dumb now but whoever was deciding to capitalize Music also decided to capitalize Borahshadow therefore my symbolic link pointed to nothing so samba didn't show it. It was still there so ls showed it. All fixed now.

---

