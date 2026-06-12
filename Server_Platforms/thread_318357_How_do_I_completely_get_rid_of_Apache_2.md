---
title: "How do I completely get rid of Apache 2"
date: 2006-12-13
forum: Server Platforms
---

### Post by computec on 2006-12-13
How do I completely get rid of Apache 2?
I have uninstalled anything that I see that relates to Apache 2 and installed Apache 1.3.34
but I still have all the Apache2 files and folders in the same places...
I used aptitude to uninstall 2 and install 1.x and it said it worked right.
How do I make sure Apache 2 is really uninstalled?
How do I get rid of the unneeded files and folders left behind by Apache2?

Thanks,

Alan
(Real Linux Newbie)  :-D

---

### Post by tturrisi on 2006-12-15
How do I completely get rid of Apache 2?
apt-get --purge remove apache2

How do I make sure Apache 2 is really uninstalled?
[http://localhost](http://localhost) or [http://lan-ip-address](http://lan-ip-address)

How do I get rid of the unneeded files and folders left behind by Apache2?
delete them
keep in mind that apache install will still make an /etc/apache2 dir w/ some files, but the config will be /etc/apache/httpd.conf

---

### Post by computec on 2006-12-15
Thanks...
I ran apt-get --purge remove apache2 and it said it was not installed but I still have all the files and folders... It also said I had files that was not removed and that I should use autoremove, but I'm not sure if I need those files since I have already installed Apache 1.x.

I have already installed Apache 1.x so localhost gets that server.

I am still a Linux newbie... I'm not sure how to delete the files and folders via the terminal command line and since Ubuntu doesn't let me login as root I don't have permission to delete them.

keep in mind that apache install will still make an /etc/apache2 dir w/ some files, but the config will be /etc/apache/httpd.conf
Do you mean Apache2 install will make the /etc/apache2 dir w/ some files?
What about Apache 1.x? Should it be /etc/apache/ I have both dirs and both httpd.conf files
When I open [http://localhost](http://localhost) it tells me that it is running Apache/1.3.34

---

### Post by tturrisi on 2006-12-16
yes, apache1 makes the apache2 dir. 

to delete files do:
~# cd /directory-you-want-to-go-to
~# sudo rm file-you-want-to-remove
enter your-password

to create a root password so can logon as root:
~# sudo passwd root
follow the prompts

note: if create a root password and then logon as root to admin the server it is wise to then do:
~# logout
when finished.  The neat thing is that one need not ever logon for the servers to be functional & running.  My server is running 24/7 with no one ever logged on.  This way, no one can get into the comp & do stuff, such as kids, family members, curious friends, etc.

here's a handy list of commands to use:
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by computec on 2006-12-16
Thanks... That explains a lot... BIG help...

I really like the idea of the servers running with no one logged in.

The rm command won't let me delete the dir if it still has files in it.
Is there a easy way to delete a whole dir... files and all...

---

### Post by jvc26 on 2006-12-16
Are all the files in the directory belonging to Apache2? Because it may be possible to change the folder permissions:

```

sudo chmod -R +rwx [directory]

```

Where [directory] is the directory which you want to delete.
This will change the folder permissions recursively so that all the files and folders permissions within that directory are changed so that all users can read, write and execute. At which point you can just go to the file in nautilus and right click delete it.

I'm still fairly new to this, so I'd wait for this possibility to be checked by a more experienced user, but I think this may be a solution?

Il

---

### Post by computec on 2006-12-16
I'm not sure if they belong to Apache2 or 1.x.

I am learning something new all the time...
I didn't even think about changing the permissions...

That's an idea, but I may just try to uninstall Apache 1 and 2 and see what's left...

I'm trying to learn how to do this without doing a complete OS reinstall
However I have another machine installing right now so I can compare the two to each other.

You may be right but like you said maybe a more experienced user will have some comments also...

Thanks

---

### Post by chrisfay on 2006-12-16
> The rm command won't let me delete the dir if it still has files in it.
Is there a easy way to delete a whole dir... files and all...

You need to execute 'rm' recursively to remove a directory. If you wanted to remove /var/www/site you would run:

```
sudo rm -R /var/www/site
```

Regardless of directory and file permissions, this will remove the folder as long as you have sudo access.

If you think you still have apache2 files leftover after a --purge, you can run:

```
locate apache2
```

...to see just how many. You can then either manually remove them or choose another option.

If you're concerned you have both packages 'running', run:

```
ps aux | grep apache2
```

....if all you get back is your grep command, then apache2 is not running and you just need to remove the files, if you want.

---

### Post by computec on 2006-12-19
Thanks for the reply...
 I have learned a lot in the last few days...
I removed Apache 1 and 2 and got things working right.

But now I'm having a big problem getting frontpage ext to work with Apache 2.0.  :( 

I have apxs in the /etc/sbin but I thought the fp_install wants it in the /etc/bin so I copied it and now I have it in both places. I'm not sure but the fp_install may have to have apxs2 but I can't seem to find it anywhere for Ubuntu Debian. I found the rpm and used alien to convert it but it want install... It comes back with errors... I think it didn't convert right... 

HELP>>>>>>>>>>>.....   :-D

---

