---
title: "Changing File Time Stamp (Bash Script)"
date: 2010-01-06
forum: Server Platforms
---

### Post by chj-se on 2010-01-06
I need some help recovering from a "slight" screwup. We just moved 3 TB of data from one RAID Array to another. Low lever archive files. This was done with a regular cp (for some reason) and now we have lost all the timestamps on the files, and we urgently need to get the timestamps back on these files. 

We are running Ubuntu 9.10 Server and we have mounted the following

1. /mnt/old-raid   ##Old raid from the old server
2. /mnt/new-raid  ##New raid on the server

I know we can read out the timestamp on the old server using the command stat -c '%Y' <<filname>>

I know we can change the timestamp of the file, using the command touch -d '<<date>>'

To get from the stat -c date to the input date in touch we need to use date -d @<<timestamp>> +'%d %b %Y %R'

So my question is, how can I create a loop that will list all files in a folder, get their timestamp and update the old timestamp with the new?

Clear as mud?

---

### Post by BkkBonanza on 2010-01-06
Have a look at rsync. There is an option to preserve timestamps. If you rsync the files from the old to the new it won't have to copy them all again but it should update the timestamps to match the old ones.

rsync -vtpr /mnt/old-raid /mnt/new-raid

v = verbose
t = preserve times
p = preserve perms
r = recurse subdirs

Should do what you want pretty quick.

---

### Post by chj-se on 2010-01-06
It was really slow using rsync, I have a script that runs the timestamp change, but need a way to execute it on all file

```
#!/bin/bash
#
BASE_OLD=/mnt/old-raid
BASE_NEW=/mnt/new-raid

TS=$(stat -c '%Y' "${BASE_OLD}${*}")

TIMESTAMP=$(date -d @${TS} +'%d %b %Y %R')

touch -d "${TIMESTAMP}" "${BASE_NEW}${*}"
exit
```

---

### Post by BkkBonanza on 2010-01-06
That's odd. It shouldn't be slow at all. Maybe you weren't aware that it checks all the files first and then once it's built a list it updates. So it may appear at first to not be doing anything.

Anyway, for your script all you need to do is put your code in a loop on the filespec. Google "bash for loop".

Try like this, as an example how to get full paths listed,

```
for f in `rsync -r /mnt/old-raid | cut -c 44-`; do
  echo /mnt/new-raid/$f;
done
```

---

### Post by chj-se on 2010-01-06
God it working... Thanks.

Got it working. Thanks for the support.

```

#!/bin/bash
#
BASE_OLD=/mnt/old-raid
BASE_NEW=/mnt/new-raid

cd $BASE_OLD
find . -type f |
while read fname
do
$BASE_NEW/${fname}

TS=$(stat -c '%Y' "${BASE_OLD}/${fname}")


TIMESTAMP=$(date -d @${TS} +'%d %b %Y %R')

touch -d "${TIMESTAMP}" "${BASE_NEW}/${fname}"

echo "${BASE_NEW}/${fname}"

done

```

---

### Post by alexey2011 on 2012-03-29
Hi 
i found misprint or error in you script:

TIMESTAMP=$(date -d @${TS} +'%d %b %Y %R') 
need to be changed to:
TIMESTAMP=$(date -d @${TS} +'%d %b %Y %T')
or even to
TIMESTAMP=$(date -d @${TS})

otherwise you will lose seconds in you destination dir.
and i did rewrite you script, because original gave me some errors:

#!/bin/bash
# change timestamp accordingly to original directory of files
BASE_OLD=/old_dir
BASE_NEW=/new_dir
cd $BASE_OLD
find . -type f |
while read fname
do
TS=$(stat -c '%Y' "${BASE_OLD}/${fname}")
TIMESTAMP=$(date -d @${TS})
touch -m -d "${TIMESTAMP}" "${BASE_NEW}/${fname}"
echo "${BASE_NEW}/${fname}"
done

---

### Post by Habitual on 2012-03-29
Says solved but this may help others in the same pickle.

[http://www.go2linux.org/linux/2010/12/how-copy-file-permissions-one-file-another-872](http://www.go2linux.org/linux/2010/12/how-copy-file-permissions-one-file-another-872)

---

