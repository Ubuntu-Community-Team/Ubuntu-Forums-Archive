---
title: "emailx, how can i send attachments in bash"
date: 2008-10-24
forum: Server Platforms
---

### Post by antirem on 2008-10-24
Hi,
I am trying to make a small bash script that will backup and timestamp a sql file and then send that dump through mailx

I have everything done except for I cant figure out how to get mailx to send... 

Lemme know if you can give me an example on how to use emailx with an attachment!

(I am doing this in media temple and can only use emailx for this)

if any one is interested here is the rest of the code to autoback stuff...
```
#!/bin/bash
TIMESTAMP=`date +%y-%m-%d`

mysqldump -h #SERVER_ADDRESS# -u #USERNAME# -p #PASSWORD# > backup/backup.sql

tar czpf backup/database_backup.$TIMESTAMP.tar.gz backup/backup.sql

#emailx

rm -f backup/backup.sql
```

---

### Post by lykwydchykyn on 2008-10-24
You need to use the "uuencode" command to convert the file into an attachment.  Check the man page of uuencode, it contains an example of how to do this.

---

### Post by antirem on 2008-10-25
```
me@cl25:~$ /usr/bin/uuencode database.tar.gz database.tar.gz > database.tar.gz.txt
me@cl25:~$ mail -s "Attachment" my@email.com < database.tar.gz.txt 
2008-10-24 21:43:26 Failed to get user name for uid 279578
Can't send mail: sendmail process failed with error code 1

```

?

---

### Post by lykwydchykyn on 2008-10-25
Who are you running this script as, and why does your user name say "I have no name!"?
is that your username?

---

### Post by ghostdog74 on 2008-10-25
```

#uuencode file file | mailx -s "subject" recipient@somewhere.com

```

---

### Post by antirem on 2008-10-27
ghostdog: i tired what you had with a <

i put in...
```
#uuencode email.php email.php | mailx -s "subject" my@email.com < email.php

```
email.php being a file in the current directory..

this didnt send it..? am i doing something wrong?

lykwydchykyn: the account is able to run other similar commands

---

### Post by tlcoffee on 2008-10-27
> **antirem said:**
> ghostdog: i tired what you had with a <

i put in...
```
#uuencode email.php email.php | mailx -s "subject" my@email.com < email.php

```email.php being a file in the current directory..

this didnt send it..? am i doing something wrong?

lykwydchykyn: the account is able to run other similar commands


You don't need to add the <

uuencode email.php email.php | mailx -s "subject" [email]my@email.com[/email]
That command pipes the uuencode result in the the email. That will be enough to get what your wanting.

Be sure that you have installed sharutils

sudo apt-get install shareutils

---

### Post by antirem on 2008-10-27
```
User@cl25:~$ uuencode email.php email.php | mailx -s "subject" me@email.com
2008-10-27 16:51:38 Failed to get user name for uid 279578
Can't send mail: sendmail process failed with error code 1

```

I tried to find the error online but did not see much info.

I am using Media Temple and not able/allowed to install things.  (i also dont have sudo and they wont give me su login info)

---

### Post by tlcoffee on 2008-10-27
> **antirem said:**
> ```
User@cl25:~$ uuencode email.php email.php | mailx -s "subject" me@email.com
2008-10-27 16:51:38 Failed to get user name for uid 279578
Can't send mail: sendmail process failed with error code 1

```I tried to find the error online but did not see much info.

I am using Media Temple and not able/allowed to install things.  (i also dont have sudo and they wont give me su login info)

I see. I'm sorry, I didn't realize this was on a hosted server. Your probably using a jailshell that doesn't have permission to use uuencode/mail executables from it.

Your best bet, would be to use a php mail script. I recommend [swiftmailer]("http://www.swiftmailer.org/") and create a php script using that library with the options you want and execute either manually or via cron.

---

### Post by antirem on 2008-10-29
Alright thanks for the help.. I was hoping to make a tutorial on this that wouldnt require php but if it works it works :)

Thanks again.

---

### Post by Wayne_V on 2008-10-30
Note - uuencode is deprecated.   You should use **mpack**  instead.

---

