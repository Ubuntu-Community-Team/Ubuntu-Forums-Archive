---
title: "How do you arrange your /var/www?"
date: 2009-06-15
forum: Server Platforms
---

### Post by Kareeser on 2009-06-15
I've been flip-flopping between how I manage the directories served on the web from my web server.

On the one hand, I could have everything dumped in /var/www/, and have individual folders therein corresponding to each user...

However, the folder's files needs o+r in order to be served by www-data, which means they could technically be copied and read, introducing a security risk.

The other option is to jail FTP sessions to user's home directories, and serve www directories from users' home directories.

... but then technically one could still copy the contents of a folder over to another directory to peruse at leisure... hmm.

So, how do you handle multiple users' data?

---

### Post by arstanj on 2009-06-15
/var/www/html/sites/DOMAIN.COM/ - home folder
/var/www/html/sites/DOMAIN.COM/www - html folder
/var/www/html/sites/DOMAIN.COM/logs - logs

proftpd with jail to home directory.

---

### Post by hictio on 2009-06-15
I usually go like this:

/var/www/
/var/www.ssl/
 
With the sites inside those directories.

---

### Post by ActiveFrost on 2009-06-15
```
/var/www/domain/public/
/var/www/domain/data/
/var/www/domain/data/logs/
/var/www/domain/data/error_pages/
```

Have been using this structure for a while and .. works great for me :)

---

### Post by Kareeser on 2009-06-15
I see... but how do you deal with curious users who try to navigate out of their assigned folder? What permissions do you use for their folders?

**arstanj**, if you jail the users in their home directories, then they can't leave ~... so how could they navigate to /var/www, since even symlinks won't work?

---

### Post by Bachstelze on 2009-06-15
> **Kareeser said:**
> **arstanj**, if you jail the users in their home directories, then they can't leave ~... so how could they navigate to /var/www, since even symlinks won't work?

The home directory of a user does not necessarily have to be /home/username. ;) It can be anything, so you can just set /var/www/somesite.org as the home directory of the user to whom somesite.org belongs, and jail him in it. You can also use the [font="monospace"]bind[/font] option to [font="monospace"]mount[/font].

And of course you can also put the website root in /home/username/www.

---

### Post by Kareeser on 2009-06-21
I see... I never thought of it that way! Thanks for your replies, everybody, and especially **HymnToLife**.

---

### Post by R.Bucky on 2009-06-22
i have thought about a jail, but recently purchased a new server and feel pretty darned good about my RAID1 install with hot spare. When I created my partitions, I placed my distribution files on one partition. Then, I created an entire partition for the server files. I host 3 web sites and have them configured like:

/directory/domain1
/directory/domain2
/directory/domain3
/directory/Music - contains music files for my streaming media server

I control 'fishing' in my directories by restricting users with the default file.

---

### Post by windependence on 2009-06-23
You can always use an .htaccess file to control user access if these are private sites.

Personally, I use the Unix style and just separate my sites:

/var/www/htdocs/site.com
/var/www/htdocs/site2.com

...and so on. Of course, all my sites are public.

-Tim

---

