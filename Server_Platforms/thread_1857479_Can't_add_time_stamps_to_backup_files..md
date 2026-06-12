---
title: "Can't add time stamps to backup files."
date: 2011-10-10
forum: Server Platforms
---

### Post by pepsifx357 on 2011-10-10
I'm trying to create a partial backup using a "script" that is triggered by cron every afternoon at 12:00pm.  I made this script from various information around the web, including how to add the date in the file name.

Here is my script:

```
tar cvpjf /mnt/linux-backup/Linux-Partial-Backup.$(date +%c).tar.bz2 --exclude=/var/log/* /var
```

When I run this, the output file is named: "Linux-Partial-Backup.MON"

I need it to be: "Linux-Partial-Backup-Monday-13:00.tar.gz"

How can I do that?

Thanks.

---

### Post by ajgreeny on 2011-10-10
Cron is more limited than bash and I wondered if the variable of $(date +%c) was not being dealt with correctly, though I do not know why that should be, as I use $(date +%F_%H-%M) in a script run with cron and it works well.

Might the spaces in the variable output present a problem?  I have no idea why they should, and I'm thinking aloud here, and possibly talking out of the back of my head, but it just seems odd that it will not work as it should.

However to test things out I have just changed my script, which records radio streams, to the same variable as yours, $(date +%c), and my output file is named just **Mon**, whereas with my original variable it is properly named as **2011-10-10_17-17-music.wav**

Just for info, here's my script's command
```
#!/bin/bash
/usr/bin/mplayer -cache 2048 <url> -vc null -vo null -ao pcm:fast:waveheader:file=/home/andrew/Radio/$(date +%F_%H-%M)-music.wav
```I do not understand this!  Very weird.

---

### Post by WasMeHere on 2011-10-10
I think it is because of the spaces in the date format. Try with quotes, **"$(date +%c)"**, or use the method described by ajgreeny!

Have fun
Olle

---

### Post by pepsifx357 on 2011-10-10
Here's what I did to get it to work.

```
tar cvpjf /mnt/linux-backup/$(date +%A@%H-%M-%S).tar.bz2 --exclude=/var/log/* /var

```

Now the file looks like this:  "Monday@12-07-25.tar"

I wanted it to be: "Monday@12:07:25.tar" but when I put the colon instead of hyphen, it wouldn't work.  At all.

It works now, so I guess that's all I can ask it to do.  lol

Thanks for the help. :)

---

### Post by WasMeHere on 2011-10-10
I guess colons are not allowed in filenames.

Everyday learning something new, having fun
Olle

---

### Post by ajgreeny on 2011-10-10
It is obviously rather like using **$(date +%x)**  for the date variable which gives the locale's date representation with figures separated with /, (e.g., 12/31/99) and I was aware the / is not allowed in the file name.  Using that variable, no file is saved at all, not even a badly named one.

---

### Post by pepsifx357 on 2011-10-10
> **ajgreeny said:**
> It is obviously rather like using **$(date +%x)**  for the date variable which gives the locale's date representation with figures separated with /, (e.g., 12/31/99) and I was aware the / is not allowed in the file name.  Using that variable, no file is saved at all, not even a badly named one.


That's exactly why it didn't work.  The output error showed 12/00/00, no such file name.. blah blah whatever.

I didn't realize though that the variables changed the format.  I just though it spit out a number and you could add your own seperator.

---

### Post by pepsifx357 on 2011-10-11
Now I have a new problem.  Whenever the partial backup occurs it doesn't back up everything that it's supposed to.

I have the script in /usr/bin/, so when i manually run it using:

```
sudo partbackup
```

It runs and backs up the entire /var directory.

When cron runs it, is backs up an 18KB tar file that is un-openable.

The only thing I can think of, is that I didn't add "#!/bin/bash" and the beginning of the script.  Maybe that is the problem?

I'm assuming cron doesn't have bash as a shell and the /bin/bash lets it know which one to use?  Is this right?

---

### Post by WasMeHere on 2011-10-11
By default *cron* runs *sh* which is actually *dash* in Ubuntu (a simple shell).  See *man sh*. So try "#!/bin/bash" and the beginning of the script :-)

If is does not help, keep trying, because it is so easy to refer to something not included in the simple environment of cron.

---

### Post by Jonathan L on 2011-10-12
> **pepsifx357 said:**
> Now I have a new problem.  Whenever the partial backup occurs it doesn't back up everything that it's supposed to.

I have the script in /usr/bin/, so when i manually run it using:

```
sudo partbackup
```It runs and backs up the entire /var directory.

When cron runs it, is backs up an 18KB tar file that is un-openable.

The only thing I can think of, is that I didn't add "#!/bin/bash" and the beginning of the script.  Maybe that is the problem?

I'm assuming cron doesn't have bash as a shell and the /bin/bash lets it know which one to use?  Is this right?

Hi Pepsi

I notice a number of things with your scripts which made me want to help: especially as you're making backups.

1.  There's nothing wrong of itself with having colons in filenames, but many programs, including tar, understand the colon specially as meaning a file over a network.  In general best not to have them.  (The only truly forbidden characters are '/' and '\0', but frankly if you ever find yourself moving files around from one computer to another it's a really good idea to avoid the special characters for Windows and Macintosh, and the tricky characters in Unix.  Stick with [FONT=Courier New]a-zA-Z0-9._-[/FONT] and you'll save yourself hours and hours with your scripts.)

2.  You've got some issues with quoting, which is what was causing the problem when you had a space in your filename.  If you want spaces in your filename, you need double or single quotes.  But I'd strongly suggest solid filenames with plain characters. Additionally, you need to quote the --exclude wildcard expression or it will be expanded at the wrong time.  Shell quoting and expansion is tricky, but reading and re-reading the man page on the subject is helpful.  In brief $ works inside double-quotes but not single-quotes; quoting prevents word splitting on the spaces and wildcard-expansion on the asterisks.

3.  You might consider putting your script in /usr/local/bin, not /usr/bin, as it will help you find it again when you upgrade your system.

4.  You don't need the #! stuff at the top of your file: if missing, the file will be interpreted as a shell script.  It's good form however, to have it, but use #!/bin/sh for portability

5.  As you are backing things up the script needs to be run as root, which in this case means you need to use root's crontab.  Remember that the crontab has a very small PATH environment variable, so it's quite usual to have full paths for the script.

6.  It's a good idea to have logging on somehow somewhere so you can see things.

7.  Dates in filenames: I really, really, recommend a format like YYYYMMDD-HHMMSS, as these sort nicely.  For backups I've often used hostname__filesystem__date.tar.gz

8.  For backups, it's great if you have a list of files in the backup, separate from the tar file, as that can be very large.


Altogether then:

Root's crontab (ie, "sudo crontab -e") is
```
0 13 * * * sh /usr/local/bin/partbackup.sh
```/usr/local/bin/partbackup.sh is
```

#!/bin/sh

set -e

STAMP="`date +'%Y%m%d-%H%M00'`"
BASE="/tmp/backup-$STAMP"
cd /
tar cfj "$BASE.tar.bz2" --exclude="var/log/*" var
tar tvfj "$BASE.tar.bz2" > "$BASE.ls"
```note -e which says script is to exit if any command fails.  In practice this means if the tar c fails, there will be no tar t and the absence of the .ls file will tell you something went wrong which you need to investigate.  The reason for faking the seconds to 00 is because cron sometimes will get around to this command at :00 seconds past the hour, sometimes :01, sometimes :02 and it can be irritating in your filenames.  Use of variables ensures that everything is consistent.  The double quotes around the STAMP and BASE mean you can have spaces in there if you insist.  The double quotes around "BIG*" means that the expansion is done by tar, not the shell.  The cd / is to allow you to have relative names for the tar c command and avoid the warning you'd otherwise get.

files get made like this:
```
-rw-r--r-- 1 root root  289 2011-10-12 12:41 backup-20111012-124100.tar.bz2
-rw-r--r-- 1 root root  316 2011-10-12 12:41 backup-20111012-124100.ls
```Was tested on Ubuntu 10.04.

Hope that's of some use to you.

Kind regards,
Jonathan.

---

### Post by pepsifx357 on 2011-10-14
Wow...Thanks for that info.  I'll be working on this at sometime today!

---

