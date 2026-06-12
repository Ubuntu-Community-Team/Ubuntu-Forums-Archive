---
title: "LAMP Backup and Restore"
date: 2012-11-19
forum: Server Platforms
---

### Post by Bynw on 2012-11-19
Hi.

I've looked online in several places on backing up a server. And unfortunately it's just not clicking with me. It's a simple LAMP setup with a couple of vhosts. Using PHP, mySQL and wordpress.

I would like to back everything up. The sites, the databases, and all content, config information. And then move it to another host so when it is restored on the new host. Nothing is lost. No user logins or site content.

But I just get confused when looking this information up online in other places. I just need a quick simple solution.

Thank you.

---

### Post by spynappels on 2012-11-19
I'm not sure about the Wordpress thing, but for the rest, you'd want to use mysqldump to backup the database, rsync to backup the sqldump, html and php pages and Apache config files to a remote location, and then a script on the remote location to restore everything to the correct places and restore the database.

This can all be scripted easily enough in Bash or shell of your choice and run from cron.

Google mysqldump and rsync, or read through the man pages, if you're not sure what to do, ask and I'll try to help further.

---

### Post by thnewguy on 2012-11-19
I would recommend, as the above poster stated, using mysqldump to make a snapshot of the database. Then copy the database files and the Wordpress directory tree to another location using rsync. Wordpress stores uploaded photos and such inside its directory tree instead of inside the database so it's important to back up your Wordpress files on a regular basis.

---

### Post by Bynw on 2012-11-19
I want to back up all databases. So I found this example online.

```


mysqldump -u root -p PASSWORD --all-databases > /path/to/dump.sql


```

However, when I enter that. I get a small file created which just gives usage information.

Usage: mysqldump [OPTIONS] database [tables]
OR     mysqldump [OPTIONS] --databases [OPTIONS] DB1 [DB2 DB3...]
OR     mysqldump [OPTIONS] --all-databases [OPTIONS]
For more options, use mysqldump --help

Not the dump of the database.

---

### Post by Bynw on 2012-11-19
Got the dump to work by changing it to:


```


mysqldump --user=root --password --all-databases > /path/to/all-database.sql


```

---

### Post by spynappels on 2012-11-20
> **Bynw said:**
> 
mysqldump -u root -p PASSWORD --all-databases > /path/to/dump.sql


I know you got it to work, but the error in the syntax above is the space between -p and PASSWORD, you should have used this:
```
mysqldump -u root -pPASSWORD --all-databases > /path/to/dump.sql
```
You seem to have got the idea anyway. Have yo looked at rsync yet? Took me a while to get my head around the syntax, but it's quite easy when you practice it a bit.

---

### Post by HugoSerrano on 2012-11-20
Careful with that rsync practice. Don't do it in your production environment.
You can sync an empty folder over the website.

---

### Post by spynappels on 2012-11-20
> **HugoSerrano said:**
> Careful with that rsync practice. Don't do it in your production environment.
You can sync an empty folder over the website.

Good point, I should have made that clearer, thanks.

---

### Post by SeijiSensei on 2012-11-20
I strongly recommend use the -n switch with rsync while you are troubleshooting.  If you use "rsync -avn source target" you'll see a complete list of the files that would have been transferred so you can check that the paths are correct.  Once you are happy with the results, remove the "n" so rsync can do its magic.

---

### Post by Bynw on 2012-11-20
I did try the rsync to make copies of the files. Looks like it preserves permissions, does it preserve ownership as well?

---

### Post by SeijiSensei on 2012-11-21
If you use the "-a" switch it preserves both permissions and (numeric) ownerships.  

"man rsync" tells you all you need to know.

---

### Post by Bynw on 2012-11-23
Thanks all for the assistance. Got both backups to work.

---

