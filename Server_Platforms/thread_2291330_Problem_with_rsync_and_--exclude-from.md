---
title: "Problem with rsync and --exclude-from"
date: 2015-08-19
forum: Server Platforms
---

### Post by Anton_de_Goede on 2015-08-19
I had a working rsync command and changed it a bit to sync over SSH to my qnap. The strange thing is that it stops working properly if I add --exclude from. So the following command works:

sudo rsync -ave ssh --stats --progress --log-file=/home/xxx/scripts/backups/logs/rsync.log.$(date +%Y%m%d%H%m%S) /var/data/ admin@10.10.10.120:/volume1/Data/

but the same version with -exclude-from does not work.

sudo rsync -ave ssh --stats --progress --exclude-from '/home/xxx/scripts/backups/exclude.txt' --log-file=/home/xxx/scripts/backups/logs/rsync.log.$(date +%Y%m%d%H%m%S) /var/data/ admin@10.10.10.120:/volume1/Data/

I get the following error for each file:
rsync: failed to set permissions on "[filenames]": Operation not permitted (1)

I also tried to just use a separate --exclude-from for each directory instead of a exclude file but it gives the same result.

Can anyone tell me why this is happening?

---

### Post by SeijiSensei on 2015-08-19
> rsync: failed to set permissions on "[filenames]": Operation not permitted (1)

Do you have the word "[filenames]" in the exclusion list?  My lists consist of directories and globs like this:
```

proc/
sys/
*.jpg

```

If you still cannot get it to work, post the contents of the exclusion file.

---

### Post by Anton_de_Goede on 2015-08-19
I meant with "[filenames]" that that's the place of the filenames in the errors. Here's the content of exclude.txt:

/aanlevering
/uitwissel
.TemporaryItems
.DS_Store

---

### Post by Dennis N on 2015-08-19
```
sudo rsync -ave ssh --stats --progress [COLOR="#FF0000"]--exclude-from '/home/xxx/scripts/backups/exclude.txt'[/COLOR] --log-file=/home/xxx/scripts/backups/logs/rsync.log.$(date +%Y%m%d%H%m%S) /var/data/ admin@10.10.10.120:/volume1/Data/
```
In your rsync command (above),

[FONT=Courier New]**--exclude-from '/home/xxx/scripts/backups/exclude.txt'**[/FONT]

should be:

[FONT=Courier New]**--exclude-from=/home/xxx/scripts/backups/exclude.txt**[/FONT]

---

### Post by papibe on 2015-08-19
Hi Anton_de_Goede. Welcome to the forum ):P

Is there files from multiple users and groups in /var/data?

Is admin in 10.10.10.120 the root user?

Regards.

---

### Post by Anton_de_Goede on 2015-08-20
Thx [**[COLOR=#000000]Dennis N[/COLOR]**]("http://ubuntuforums.org/member.php?u=321222").. I tried but no difference :-(

---

### Post by Anton_de_Goede on 2015-08-20
> **papibe said:**
> Hi Anton_de_Goede. Welcome to the forum ):P

Is there files from multiple users and groups in /var/data?

Is admin in 10.10.10.120 the root user?

Regards.

No multiple groups in /var/data. It's all the same group. Admin is indeed the root user of 10.10.10.120. 

The strange this is the excludes do work because, regardless the errors, it does not try to sync the excludes folders. The errors I get in detail are:

rsync: failed to set permissions on "/volume1/Data/fonts/Adobe font Folio XI/Western Fonts/Monotype Modern Std/ModernMTStd-BoldItalic.otf": Operation not permitted (1)

And again, this only happens with the --exclude-from part in de command.

---

### Post by Skaperen on 2015-08-20
in the case of running without the excludes, does it succeed to set permissions of "/volume1/Data/fonts/Adobe font Folio XI/Western Fonts/Monotype Modern Std/ModernMTStd-BoldItalic.otf" ?

maybe without the excludes it does not get to "/volume1/Data/fonts/Adobe font Folio XI/Western Fonts/Monotype Modern Std/ModernMTStd-BoldItalic.otf" due to issues with the files intended to be excluded or maybe this message is lost or obscured.

---

### Post by Anton_de_Goede on 2015-08-21
> **Skaperen said:**
> in the case of running without the excludes, does it succeed to set permissions of "/volume1/Data/fonts/Adobe font Folio XI/Western Fonts/Monotype Modern Std/ModernMTStd-BoldItalic.otf" ?

maybe without the excludes it does not get to "/volume1/Data/fonts/Adobe font Folio XI/Western Fonts/Monotype Modern Std/ModernMTStd-BoldItalic.otf" due to issues with the files intended to be excluded or maybe this message is lost or obscured.

In both cases it syncs the example file above (it's not part of the exclude). As I said, the part of excluding does work because the directories in the exclude do not get synced.

---

