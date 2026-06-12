---
title: "Mailx Issues after upgrade"
date: 2010-05-12
forum: Server Platforms
---

### Post by rmccarri on 2010-05-12
Hi Everyone,
I recently upgraded our web server to 10.04 and it seems that mailx was replaced by heirloom-mailx.  I have a script that dumps and emails all of our MySQL databases to me for backup.

After installing heirloom-mailx to replace it, the script is not functioning properly.  The email portion of the orginal script was along these lines:

```
(uuencode file1.sql file1.sql; uuencode file2.sql file2.sql) | mail -s "MySQL Dumps" me@mydoman.com
```

It seems that heirloom-mailx doesn't support multiple attached files in such a manner (I only get the last file in the email and all of the other files go to stdout), so I changed it to something like this:

```
tar xzvf dumps.tar.gz
uuencode dumps.tar.gz dumps.tar.gz | mail -s "MySQL Dumps" me@mydoman.com
```

This sends the file over email, but when the attached file is saved in Evolution and extracted with archive manager, it seems to not make it OK and gives the following message:

```
gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
```

If I directly send the file over, it's fine, so it isn't a problem with the compression or packaging or anything.  Does anyone have any suggestions for a fix?
Thanks in advance!
Rob

---

