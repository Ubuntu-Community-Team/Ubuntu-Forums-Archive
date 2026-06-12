---
title: "Cronjob to delete cache files"
date: 2010-02-03
forum: Server Platforms
---

### Post by wattaman on 2010-02-03
Hi!
How can I set a cronjob to delete the cache files? I've enabled the mod disk cache in apache and I know I must delete the cache files once in a while, just don't know how. Also, where do I add the following instructions, in the cache.load file or in the disk_cache.load file:
[HTML]CacheMinFileSize 64
CacheMaxFileSize 64000[/HTML]
I want to limit the size of files that mod cache should cache.
Thank you!

---

### Post by hemimaniac on 2010-02-03
well for the cron job you could use something like this;


*****  <user>   find /path/to/files/* -type f -mtime +5 -exec rm -r {} \; > /dev/null

-type is for what the find command is looking for, ie directories, files symlinks etc.

-mtime is for the time from the mod date, one could also use -ctime for creation

+5 just an example in this instance it is five days

have a look at the find man as the find command imo is one of the most powerful ones you can turn loose in a *unix rig

also there is this neato little page i came across for helping write contrab jobs, check it out [here]("http://www.htmlbasix.com/crontab.shtml")

as for the limiter, I honestly don't know, sorry

---

### Post by BkkBonanza on 2010-02-04
You're going to want to put those Cache directives in the same place you put CacheRoot. If you didn't put CacheRoot then according to the docs it won't work. It needs that to know where to store cached files.

As long as Apache can find the directives it should be good. So you could put them in /etc/apache2/apache2.conf or you could put them inside specific VirtualHost directives to only apply to that host. So that would mean putting them in the config for a specific site_available file. If you have config files for each module then sure, put them there, in mods_availble. As long as Apache gets them they should be ok, wherever they are.

Regarding the cronjob I think your should add the job for your admin user or perhaps as your www-data user. But I don't think there's any need to run the job every minute as the post above suggests. You can run it once a day using "0 0 * * *" (at midnight) for the timing. To set up a cron as a specific user you can use,

sudo crontab -e -u www-data

and then add the line as suggested above but without a user.

0 0 * * * find /path/to/files/* -type f -mtime +5 -exec rm -r {} \; > /dev/null

for /path/to/files you want to use the same path that you use in your CacheRoot directive. eg. /var/tmp/www-cache/* or wherever you decide to keep the cahced files.

---

### Post by wattaman on 2010-02-04
Before I'll make something stutid and delete something else (:p) I one to know one more thing: How can I be sure of the location of cache directory?
So far I've found this */var/cache/apache2/mod_disk_cache* that I suspect is the one, still.. I was hoping I can see somewhere written, black on white, maybe in a configuration file or something, the location of the cache directory.
Thank you!

---

### Post by BkkBonanza on 2010-02-04
You should see a conf directive called CacheRoot that sets where to store the cache files.

---

### Post by wattaman on 2010-02-04
I have in /etc/apache2/mods-available/disk_cache.conf which contains:
[HTML]<IfModule mod_disk_cache.c>
# cache cleaning is done by htcacheclean, which can be configured in
# /etc/default/apache2
#
# For further information, see the comments in that file, 
# /usr/share/doc/apache2.2-common/README.Debian, and the htcacheclean(8)
# man page.

	# This path must be the same as the one in /etc/default/apache2
        CacheRoot /var/cache/apache2/mod_disk_cache

        CacheEnable disk /

        CacheDirLevels 5
        CacheDirLength 3
</IfModule>[/HTML]
So, the cache directory is here [I]/var/cache/apache2/mod_disk_cache
[/I].
Problem solved.
Thanks, guys!

---

### Post by wattaman on 2010-02-04
Sorry, must reopen this. The *0 0 * * * find /path/to/files/* -type f -mtime +5 -exec rm -r {} \; > /dev/null* doesn't seem to work and I'd like to use this instead, has more options, too:
"htcacheclean -d -n -t -p /var/cache/apache2/mod_disk_cache -l 10240M -i /dev/null" (as I've read here [http://httpd.apache.org/docs/2.3/programs/htcacheclean.html](http://httpd.apache.org/docs/2.3/programs/htcacheclean.html))
It should work as a cron but it doesn't, instead it displays this every time I run it as cron:
[HTML]Output from command htcacheclean -d -n -t -p /var/cache/apache2/mod_disk_cache -l 10240M -i /dev/null ..

htcacheclean -- program for cleaning the disk cache.
Usage: htcacheclean [-Dvtrn] -pPATH -lLIMIT
       htcacheclean [-nti] -dINTERVAL -pPATH -lLIMIT

Options:
  -d   Daemonize and repeat cache cleaning every INTERVAL minutes.
       This option is mutually exclusive with the -D, -v and -r
       options.

  -D   Do a dry run and don't delete anything. This option is mutually
       exclusive with the -d option.

  -v   Be verbose and print statistics. This option is mutually
       exclusive with the -d option.

  -r   Clean thoroughly. This assumes that the Apache web server is 
       not running. This option is mutually exclusive with the -d
       option and implies -t.

  -n   Be nice. This causes slower processing in favour of other
       processes.

  -t   Delete all empty directories. By default only cache files are
       removed, however with some configurations the large number of
       directories created may require attention.

  -p   Specify PATH as the root directory of the disk cache.

  -l   Specify LIMIT as the total disk cache size limit. Attach 'K'
       or 'M' to the number for specifying KBytes or MBytes.

  -i   Be intelligent and run only when there was a modification of
       the disk cache. This option is only possible together with the
       -d option.[/HTML]
... the cache folder remains intact (and huge :))
Any suggestions on how to use the htcacheclean?
Thanks!

---

### Post by BkkBonanza on 2010-02-04
The /dev/null part at the end needs to have ">" in front, eg.

> /dev/null

This is a redirect that sends output to nowhere, prevents an email being sent. If you don't have the > the program will see it an an argument and likely fail with usage info.

You can also leave it off, especially at first, as it may be useful to get cron mail telling you the clean was working.

Note also, important, you do not want to run with -d (daemonize) in a cron script. Daemonize means "stay in the background and keep running", so doing this periodically will start many daemons and makes no sense. If you want to use -d it will stay in the background and watch your cache every few minutes, so you don't need cron. In this case you put this line in your /etc/rc.local so that it starts upon boot and keeps running in the background.

-d also requires an interval in minutes, eg. -d5 

Do you really want a 10GB cache? That seems huge to me.

---

### Post by wattaman on 2010-02-05
Doesn't work. It displays the same info, but nothing else. This is my cron now: *htcacheclean -n -t -p /var/cache/apache2/mod_disk_cache -l 10240M -i > /dev/null* I've tried without the > /dev/null but still nothing.
:(
About the space, probably I don't, I just don't know how much I need ... I suppose is better to test various configs

---

### Post by BkkBonanza on 2010-02-05
Try it on the command line until you get good results. It must be something wrong with the arguments passed. Maybe try no space between -p and path. The docs seem to indicate no space. Same with -l limit. Whatever works at the command line should work as well in cron or /etc/rc.local.

Also with cron it's good idea to specify the whole path to commands to be sure you don't have path related problems. So you can use,

whereis htcacheclean

to find it's location eg. /usr/bin and then put full path,

/usr/bin/htcacheclean in the cron.

You should always test cron commands on the command line first anyway to be sure they work manually before automating.

Re: 10GB. If you have the space then sure why not. After you've run for a while you can use,

du -h --max-depth=1  /path/to/cache

to see how much space you're using.

---

### Post by wattaman on 2010-02-05
Tried everything with htcacheclean, didn't work.
I've tried the *find /var/cache/apache2/mod_disk_cache/* -type f -mtime +5 -exec rm -r {} \; > /dev/null* and the server crashed. I have access to a recovery console but honestly don't know what to do with it. I'll ask the hosting company for support, maybe nothing is lost and they can power it up again.... hopefully the way it was.

---

### Post by wattaman on 2010-02-07
I finally fixed the server, but in the end I had to deactivate the disk_cache module.
It appears that one of the commands I've tried to clean the cache somehow caused block errors on the HDD. I've managed to start the rescue console from my hosting panel and fix the drive with the e2fsck command.
After that the htcacheclean just kept starting thought it wasn't programmed to so I deactivated it (don't remember what config file, just had to choose between yes, no and auto and I set it no) then I also deactivated the disk_cache module.
Everything is back the way it was, I still have the cached files from apache but the folder is too big and I don't want to risk crashing the server again to empty it, I have space on HDD anyway.

All this story reminds me of that: *if it ain't broken, don't fixed it*... also, not that I don't apreciate your help, guys, but: if you want to do something good, do it yourself :lolflag:

Thanks!

---

