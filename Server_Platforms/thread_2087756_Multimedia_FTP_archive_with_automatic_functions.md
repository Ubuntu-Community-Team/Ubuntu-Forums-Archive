---
title: "Multimedia FTP archive with automatic functions"
date: 2012-11-24
forum: Server Platforms
---

### Post by mrblonde1369 on 2012-11-24
Hi everybody,

first of all I hope I've posted this in the correct section.

Now, I am trying to build an Ubuntu server and I would like to ask you Ubuntu fellows some help/advice.

I have been using Ubuntu for almost 6 years now, so I don't consider myself a total newbie, although I'm no expert at all.

As of now, I would need to create an FTP server for a multimedia project I am working on (an independent movie), and I am trying to understand what the best (and easiest) solution would be.

This is what I have in mind, and I would like the server to do:

1-	FTP secure server with multi-user login. On a 1.5TB harddisk, I need to have one "archive" folder (where the files are stored) and one "incoming" folder (with one subfolder for each user), where my colleagues can upload files.
	e.g.

hddroot
-->"archive"
-->"incoming"
------>user01
------>user02
------>user03

Each one of my colleague:
	- only has access to the "incoming" folder
	- can see and access all the users subfolders (user01, user02 etc..) BUT
	- can only modify files and upload files into his subfolder (user01 can only modify 			upload to user01)

It would be great to have detailed stats for each user, something like the functions I have seen in glftpd (screenshots [https://en.wikipedia.org/wiki/Glftpd](https://en.wikipedia.org/wiki/Glftpd) )


2-	Automatic MD5 sum. Once a user has finished uploading a file in his folder (e.g. "incoming"/user01), the file is automatically copied into the "archive" folder, and an MD5 file checksum is created.


3-	Once a day, a list of all the folder/files in the "archive" folder is created, complete with MD5sum and mediainfo details. The results are output to a single html file (similar to cdcat output) and the html file is automatically uploaded onto another server.


Can anyone offer some help/suggestions on how to start building such a thing? Is there anything "more-or-less" readymade? A series of already-made scripts?

Many thanks in advance to anyone who will answer.

---

### Post by sandyd on 2012-11-26
> **mrblonde1369 said:**
> Hi everybody,

first of all I hope I've posted this in the correct section.

Now, I am trying to build an Ubuntu server and I would like to ask you Ubuntu fellows some help/advice.

I have been using Ubuntu for almost 6 years now, so I don't consider myself a total newbie, although I'm no expert at all.

As of now, I would need to create an FTP server for a multimedia project I am working on (an independent movie), and I am trying to understand what the best (and easiest) solution would be.

This is what I have in mind, and I would like the server to do:

1-	FTP secure server with multi-user login. On a 1.5TB harddisk, I need to have one "archive" folder (where the files are stored) and one "incoming" folder (with one subfolder for each user), where my colleagues can upload files.
	e.g.

hddroot
-->"archive"
-->"incoming"
------>user01
------>user02
------>user03

Each one of my colleague:
	- only has access to the "incoming" folder
	- can see and access all the users subfolders (user01, user02 etc..) BUT
	- can only modify files and upload files into his subfolder (user01 can only modify 			upload to user01)

It would be great to have detailed stats for each user, something like the functions I have seen in glftpd (screenshots [https://en.wikipedia.org/wiki/Glftpd](https://en.wikipedia.org/wiki/Glftpd) )


2-	Automatic MD5 sum. Once a user has finished uploading a file in his folder (e.g. "incoming"/user01), the file is automatically copied into the "archive" folder, and an MD5 file checksum is created.


3-	Once a day, a list of all the folder/files in the "archive" folder is created, complete with MD5sum and mediainfo details. The results are output to a single html file (similar to cdcat output) and the html file is automatically uploaded onto another server.


Can anyone offer some help/suggestions on how to start building such a thing? Is there anything "more-or-less" readymade? A series of already-made scripts?

Many thanks in advance to anyone who will answer.
1. Use pure-ftpd w/ puredb and user accounts on the server, or proftpd with user accounts.

Set the home directory of the accounts to /incoming/userxxx, and make sure its chowned to the user, and given a chmod of 700
2. No idea
3. Cron job (with root permissions, otherwise it will not be able to access the /incoming/userxxx folders!)

---

### Post by thnewguy on 2012-11-26
With step #2, creating an md5sum of each file and copying it to the archived folder, I suggest a small script run from a cron job. Each minute the cron job could do something like....

```

#!/bin/bash
cd /incoming
find . -newer my_file -exec cp {} /archive \;
find . -newer my_file -exec md5sum {} > /archive/{}.checksum \;
touch my_file

```

You'll have to tweak it a little, but the general idea is the "find" command will look for each file in the directory which is _newer_ than a file called my_file. After the check is complete the modified time of my_file is updated.

There are better ways to do this using C and placing watches on the contents of a directory, but the above script will probably work well enough for what you are doing.

---

### Post by mrblonde1369 on 2012-12-11
thanks a lot for your help, I finally managed to write some very easy scripts to accomplish everything !:popcorn:

---

