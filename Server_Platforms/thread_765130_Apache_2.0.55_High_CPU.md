---
title: "Apache 2.0.55 High CPU"
date: 2008-04-24
forum: Server Platforms
---

### Post by terazen on 2008-04-24
I have a server that has a high cpu usage issue and I'm looking for guidance where to go from here.  I made a little cronjob to output cpu usage of apache to a file to see what's going on.

The apache2 process after getting restarted uses almost no cpu except when serving pages.  Then after a day or so it starts using 0.1% cpu constantly and slowly goes up every few minutes.  I restarted apache 7 days ago and now it's sitting solid at 84-86% cpu.  The server has been setup the same for about a year and just recently started doing this.

I've tried tweaking the prefork.c module settings with no luck.  After that I'm not sure what else to look for.  I'm open to ideas!

Thanks!

---

### Post by terazen on 2008-04-24
Just wanted to update... Went ahead and restarted apache2 again because ssh was starting to lag.  The problem will no doubt come back soon enough if anyone has any suggestions.  Thanks.

---

### Post by gtdaqua on 2008-04-25
i remember that certain versions of Apache have a memory leak. Search the forums/internet. How much swap have you configured?

---

### Post by niten on 2008-04-25
I had the same problem.  It turned out that I'd kept my old php.ini file; when I replaced it with the new one (in the same directory, php.ini.ucf-something) Apache fixed itself.

I had to do the same thing for /etc/php5/cli/php.ini.

---

### Post by terazen on 2008-04-25
Thanks for the replies!  GtdAqua, The swap size is 9GB according to /var/log/dmesg.  I didn't do the original install so I'm not sure for what purpose it's that large.  Also it's a 3.6Ghz machine with 4GB Ram.

Niten, I only could find 1 php.ini file and it's in /etc/php5/apache2.  So I renamed php.ini to php.ini.original and then replaced php.ini with php.ini.recommended.  Then I changed post_max_size and upload_max_filesize to 10mb since that's all I remember ever doing to the original and restarted apache.

I'll look into the memory leak possibility while I wait to see if the php.ini change helped.  Shouldn't take long...the cpu was at 24% when I logged in just now already!

Thanks again for yalls suggestions.

---

### Post by gtdaqua on 2008-04-26
> 
The swap size is 9GB according to /var/log/dmesg. I didn't do the original install so I'm not sure for what purpose it's that large. Also it's a 3.6Ghz machine with 4GB Ram.


You can see the swap size by typing 'free' in terminal.

Swap must always by atleast 1.5 times the physical size and max at twice the size. Your performance might degrade when you have used up your physical RAM. 

Try to reconfigure your swap drive. You have to boot in recovery mode and make adjustments to partitions. Or you can simply boot with Hiren's Boot CD and resize the swap partition and re-initialize in Ubuntu. I had to do this once on my server.

Add: type 'uptime' in terminal and apart from the actual system uptime, you will also see the system load averages of 1, 5 and 15 minutes. Keep monitoring to see if your performance is degrading or just stabilized.

---

### Post by terazen on 2008-04-29
Thanks for the responses yall.  I think I finally got it figured.  From my cronjob script running to check cpu usage once a minute I noticed a pattern starting that the problem always started on the 2nd or 3rd minute of the hour, not on any particular hour.  So I looked at the crontab and there just so happened to be a wget for moodle's cron.php 1 minute prior.  I changed it to run on the 42nd minute and the apache problem happened on the 43rd minute last night about 7:43.  So this morning I changed the syntax of the moodle cron.php crontab entry, from moodle docs they recommend 2 ways to type it, and the problem seems to be gone.

Also for anyone who may have the same problem I had about 220GB of logfiles in /var/log/mysql over the last 2 weeks.  Tons of recurring 101MB files every 23 minutes.  This also seems to have went away this morning immediately after I retyped the crontab.

Wierd thing is that moodle crontab entry has been the same for over a year.  Ughh Whatever.

Thanks for all the suggestions.  When I get time to upgrade to 8.04 LTS (more like backup and reinstall) I'll be doing a few things differently.  Searching for performance tweaks and whatnot there are a lot of things that could have been done before that I'll make sure to get to!

---

### Post by quake74 on 2008-05-01
I do also have the same high cpu problem, but I have no swap issue, since it's barely used. Where can I find a good php.ini to try? (I also have only one in that dir.)

---

### Post by terazen on 2008-05-01
I found it by running > sudo find / -name php.ini* and found these three files php.ini.recommended, php.ini.paranoid, and php.ini-dist.

---

### Post by quake74 on 2008-05-15
I tried different php.ini but the problem is still there. In the meantime, I also upgraded to Hardy and I still have the same problem. Very frustrating... Any suggestions?

Edit: Actually, even after I issue "sudo /etc/init.d/apache2 stop" the processes are still running and eating cpu...

---

### Post by terazen on 2008-05-15
Need some more info about your setup to see if the problem is something I can help with or someone else who reads this thread.

Is it constantly running high cpu or does the problem start at (seemingly) random times?  Also what type of webpages are you serving?  Any virtual sites or non-standard modules enabled?

From my experience so far php based sites like moodle/drupal/wordpress can hammer cpu pretty good so if you have one of those gotta check their sites/docs because it might be a problem with that and not apache.

---

### Post by Versusnja on 2010-01-08
How old was your original php.ini that you neede to replace it?
I have mince since Hardy, now I'm on Jaunty.
Same high CPU load from apache here...
I have about 4500 visitors on my web page daily, but it shouldn't be a problem, I think.

I have 2.4 dual core CPU and 1Gb RAM with 2 GB swap (swap not used at all).

---

