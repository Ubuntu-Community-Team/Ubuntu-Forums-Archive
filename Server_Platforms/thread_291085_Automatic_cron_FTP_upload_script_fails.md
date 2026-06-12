---
title: "Automatic cron FTP upload script fails"
date: 2006-11-02
forum: Server Platforms
---

### Post by Rocketeer on 2006-11-02
Hello,
I finished this script some time ago, but it seemd not to work.
It's target is to check a directory if it has files in it (and subdirectories) and then upload each file by ftp over the internet (at 2am).
Last night was the first live test, but it failed. After two files, the script stopped uploading and I don't know where the error is (i do logs nows)

However, due to the fact this seems to be a simple job, which certainly has been done by a lot of people, I would like to see professional solutions.

Here's the short script:

#!/bin/sh
cd /home/user/g2upload/
ftp -i -n hochlager.ch <<EOT
user [email]user@somedomain.ch[/email] password
lcd /home/user/g2upload/
mput *
quit
EOT
rm /home/user/g2upload/*

---

### Post by Rocketeer on 2006-11-03
Following script solved a lot of my problems, I hope some of you can use it too....

```
#!/bin/sh
cd /local/source/directory/
ncftpput -mRDD -u USERACCOUNT -p PASSWORD ftp.somedomain.com /remote/upload/path *
```


What it does:
Upload every [*] file (and directoy => [R]) in /local/source/directory/ to the ftp.somedomain.com/remote/upload/path and after successful upload deletes the file/directory [DD]

---

