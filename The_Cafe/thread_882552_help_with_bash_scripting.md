---
title: "help with bash scripting"
date: 2008-08-07
forum: The Cafe
---

### Post by akiratheoni on 2008-08-07
I'm an admin on a forum that needs a bash script that'll be used on a crontab.

Here's the scenario... the file structure looks like this:

exchange/backups/
exchange/backups/sites_0:00_8-01-08.txt
exchange/backups/sites_1:00_8-01-08.txt
exchange/backups/sites_2:00_8-01-08.txt
exchange/backups/sites_3:00_8-01-08.txt
exchange/sites.txt
exchange/admin.php
exchange/index.php

As you can see, the sites.txt in the exchange/ folder is backed up hourly. 

Now, for some reason there's an error in the index.php file (not quite sure what it is) that renames the sites.txt to sites_.txt and thus breaks everything >.<

When the sites.txt is renamed to sites_.txt, everything in the sites.txt is lost and it's a blank file.

So basically I need to code a script that every hour it will check if "sites_.txt" exists, and if it does, restore the most recent sites.txt back up and delete the sites_.txt

I was only able to create a bash script that would back up sites.txt... I'm a complete noob at bash scripting. And this is completely out of my league, I have no idea how to do this.

It would be great though if someone did this and if they explained what each line does (it's not necessary though... but I do want to learn bash scripting)

Thanks everyone. If this is in the wrong forum, move it to the appropriate one :P thanks. If there's any questions or any confusion, please ask them and I'll clear it up so you can help.

---

### Post by master5o1 on 2008-08-07
I do believe that bash could be like this:


cp exchange/sites.txt exchange/backups/sites_[time and date function].txt


that is just a simple copy command but idk really.
also, wouldn't it make *more* sense to have the backups dated as sites_yyyy-mm-dd_hh-mm-ss.txt so that the least changing numbers are closer to the beginning of the filename.

ps:

```

!#/bin/bash

cp exchange/sites.txt exchange/backups/sites_**[date&time]**.txt

```

blah blah maybe like that

---

### Post by akiratheoni on 2008-08-07
Thanks for the help. Your way makes it a lot simpler, I'll just have it copy the latest back up into the sites.txt every hour or so.

But the only question I have is, how do I have the script grab the most recent copy of the backup? Thanks again, your help is appreciated. I was over complicating things :P so your way makes it a lot easier.

---

### Post by clash on 2008-08-07
something like this perhaps

```
!#/bin/bash
COUNT=0
while [ $COUNT = 0 ]; (loop forever) 
do
if [ -e "dir/sites_.txt" ] (if sites_.txt exists)
     then
        cp dir/sites.txt dir/sites_date&time.txt (make a timestamped copy)
     fi
sleep 10 (10 seconds or whatever)
done
```

But honestly. Wouldn't it be better to fix the problem in the php instead of using a hack ?

edit -> Why not post the relevant section of php here ?

---

### Post by akiratheoni on 2008-08-07
> **clash said:**
> something like this perhaps

```
!#/bin/bash
COUNT=0
while [ $COUNT = 0 ]; (loop forever) 
do
if [ -e "dir/sites_.txt" ] (if sites_.txt exists)
     then
        cp dir/sites.txt dir/sites_date&time.txt (make a timestamped copy)
     fi
sleep 10 (10 seconds or whatever)
done
```

But honestly. Wouldn't it be better to fix the problem in the php instead of using a hack ?

edit -> Why not post the relevant section of php here ?

The guy who wrote the PHP code is on vacation for like two weeks >.< and seeing as I don't know any PHP, I wouldn't know which section of the PHP to put (and the other admin of the site is really paranoid and might not like me posting the code here...)

---

### Post by akiratheoni on 2008-08-07
Okay, I'll post what I believe are the relevant portions of the php code:

```
$file = fopen("sites.txt", "r");
$newfile = fopen("sites_.txt", "w");
$total = intval(fgets($file));
$highest = intval(fgets($file));
```

That's near the beginning... this one is near the end:

```
// Finish things up
fclose($file);
fclose($newfile);
unlink("sites.txt");
rename("sites_.txt", "sites.txt");
```

Like I said I don't know any PHP but I looked up the fopen function on php.net and it said it opens a file. It's kind of weird because around the beginning of the php code, it attempts to open up the sites_.txt... but when that function is run (as far as I know), the only .txt file that should exist is sites.txt, therefore it's opening a non-existent file. I'm not sure if there's an issue with that since I don't know about php but that's just what I've observed.

---

