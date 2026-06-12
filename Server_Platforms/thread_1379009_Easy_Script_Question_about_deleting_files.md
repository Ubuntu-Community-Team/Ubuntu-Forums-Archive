---
title: "Easy Script Question about deleting files"
date: 2010-01-12
forum: Server Platforms
---

### Post by Benismyhorse on 2010-01-12
Hi,
am working of a script to turn images into a slideshow, this part of the script is all done and working.
What I am trying to do is copy the images to be converted to a smaller images to another folder. Which works.

However if images in folder 2 and deleted I would like them to be deleted in folder 1 also.

Is this do-able?

Thanks

---

### Post by gobbledigook on 2010-01-12
Hi!

You're post is not entirely clear in what you want to achieve? 

Do you want to integrate the deleting of these files into your script? If so it would be helpful for you to attach the script.

if you want to do this from the cli - the simplest way would be to repeat the rm command for the second folder ie:
```
rm /folder1/jpeg1 /folder1/jpeg2 /folder1/jpeg3

rm /folder1/jpeg1 /folder2/jpeg1 /folder3/jpeg1
```

but i'm sure someone who knows more about this type thing will be along shortly to elaborate ;)

---

### Post by Benismyhorse on 2010-01-12
Hi,
the script copys images from folder 1 to folder 2 to be resize etc.
and this part is working. However if a images is deleted in folder 2 it should also be deleted in folder 1.

Thanks

---

### Post by BkkBonanza on 2010-01-12
How does it get deleted in folder 2? By script or just some user deciding to delete it?

You can use a cron job with a script that compares directories and when a file is missing in folder 2 it deletes it in folder 1.

Something along this lines, (untested code)

```
#!/bin/bash

cd /path_to/folder1
for f in *.jpg; do 
  if [ ! -f /path_to/folder2/$f ]; then
    rm /path_to/folder1/$f
  fi
done
```

Save in file /usr/local/bin/delscan and chmod +x

Then crontab -e and add line,

* * * * * /usr/local/bin/delscan

or use */5 for the first * above for every 5 minutes instead of every minute.

BTW if you're going to try this code then replace the rm command with echo command for testing. That way it outputs info for debugging.
eg.

echo /path_to/folder1/$f > debug.log

---

### Post by Benismyhorse on 2010-01-12
Thanks so much,
Exactly what I was looking for

Thanks:KS:KS

---

