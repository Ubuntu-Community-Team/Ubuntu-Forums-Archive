---
title: "Move Folders Older than X, excluding one folder"
date: 2011-06-02
forum: Server Platforms
---

### Post by firegs on 2011-06-02
Hey there!

I'm trying to set up a backup system. I have a directory filled with dirs like:

e47382
e23745
e45765
q567543
o54674

...etc., and I'd like to write a script that looks at the last time those folders were modified (and NOT based on any dates for the files inside those folders) and move them.

There's one small problem, theres a folder called "~Holiday Cardz" in the same directory as the others, which i need to be excluded from the search. 

I've looked allllll over the place, and I cannot find anything that works. Every command I try either spits out nothing, or spits out EVERYTHING. This is getting really frustrating, and I could really use any help. 

Major appreciation in advanced.

```
find . -mtime +7 -type f -path ./~* -prune | rsync -av --dry-run --files-from=- . /home/labop/servers/jabba/lifepicsserverBackUp

```

This is what I have been using. Unfortunately, this still looks at all the folders and the sub folders, and doesnt exclude the one ~Holiday Cardz folder. >.<

Also, the find is returning results of files inside those sub directories. I dont want to move files based on when they were created or modified, just the date the containing folder is. For example:

e324895\ - 5/17/2011
e324895\IMAGE - 5/17/2011
e324895\IMAGE\IMG_233.JPG - 3/21/2011
e324895\IMAGE\IMG_234.JPG - 6/1/2011
..etc..

In this scenario, wouldn't the command normally move IMG_233.JPG, but not IMG_234.JPG because 234 was edited/modified within 7 days? I want to only move based on the initial folder's last modified date, in this case e324895, based on the 5/17/2011 date.

~Sam

---

### Post by ruffEdgz on 2011-06-02
Ok, so what I'm getting is:
[LIST]
[*] Look for directories modified 8 or more days ago (thats what the +7 actually means)
[*] exclude "Holiday Cardz" from the move
[/LIST]

Try this command for a test drive:
```

sudo find . -maxdepth 1 -mtime +7 -type d | egrep -v "^.$" | while read line; do  rsync -avv --dry-run --exclude="Holiday\ Cardz.*" $line /home/labop/servers/jabba/lifepicsserverBackUp; done

```
I did a small test on my side with some of my data and the dry-run did what it was supposed to for me.

Hope that works out for you.

---

### Post by firegs on 2011-06-02
I got some access denied and permission errors, but once that was all straightened out, it works flawlessly!

```
cd /home/labop/servers/lifepicsserver | find . -maxdepth 1 -mtime +7 -type d | sudo egrep -v "^.$" | while read line; do  rsync -avv --exclude="Holiday\ Cardz.*" $line /home/labop/servers/jabba/lifepicsserverBackUp; done

```

---

### Post by firegs on 2011-06-02
What if I wanted to delete the files from the source once the files have been copied over?

---

### Post by ruffEdgz on 2011-06-02
Sorry for the late response but the solution to this wasn't very easy because of the "space" in the directory "Holiday Cardz" and how you don't want that data to be removed.

Take this code and place it into an executable file so you can run at any time.

```

#!/bin/bash
IFS=$'\n'
source_dir="/home/labop/servers/lifepicsserver/"
dest_dir="/home/labop/servers/jabba/lifepicsserverBackUp/"

dir_select=($(find $source_dir -maxdepth 1 -mtime +7 -type d | egrep -v "^$source_dir$"))

rsync -avv --exclude="*Holiday\ Cardz" $source_dir $dest_dir

for i in "${dir_select[@]}"; do
        if [ ! $(echo $i | egrep "*Holiday\ Cardz") ]; then
                rm -rf $i
        fi
done

```

I did some tests on my own computer first to make sure it will work and I made it to look at the directories you asked. Make sure you do make a backup of the information if you can before executing just in case.

Cheers!

---

### Post by firegs on 2011-06-03
I ran:

```

vim lpsb.sh
*pasted code*
:wq
chmod 777 lpsb.sh
sh lpsb.sh
```

returned:

```
lpsb.sh: 6: Syntax error: "(" unexpected
```
:(

---

### Post by firegs on 2011-06-03
I ran just 

```

./lpsb.sh
```

and it started to work, but it first makes copies of ALL folders in /home/labop/servers/lifepicsserver/ to /home/labop/servers/jabba/lifepicsserverBackUp/, and then starts to copy all the files over, regardless of date. =(

---

### Post by firegs on 2011-06-03
It seems like after it copies everything, it does delete from the source, but that means it has copied some 44gb (all folders) first, then deletes. Is there any way to NOT copy everything from /home/labop/servers/jabba/copytest/ first?

---

### Post by ruffEdgz on 2011-06-03
So when you do the following command, does it grab what you need it to grab?
```
find /home/labop/servers/lifepicsserver/ -maxdepth 1 -mtime +7 -type d | egrep -v "^/home/labop/servers/lifepicsserver/$"
```

And if you run the dry run rsync below, does that copy the directories/files you need it to?
```
rsync -avv -n --exclude="*Holiday\ Cardz" /home/labop/servers/lifepicsserver/ /home/labop/servers/jabba/lifepicsserverBackUp/
```

Sorry for the stupid questions on my end but since I can't see your directory hierarchy in front of me, I just need to see if some of the commands the script is running does what you need it to do.

---

### Post by firegs on 2011-06-03
The first command looks like it works, but the rsync looks like its copying all files. Since I cant scroll up and see everything, looking at the last few files/folders, like o912961H for example, was modified on 6/1, but it copies. =(

---

### Post by ruffEdgz on 2011-06-03
So here is what I am doing in my test.

Directory Hierarchy: 
```

/home/dummy/test_dir/
   |
   |___ .../dir1/
   |          |__file1
   |          
   |___ .../dir2/
   |          |__file2
   |
   |___ .../dir3/
   |          |__file3
   |
   |___ .../Holiday Cardz/

/home/dummy/test_dir2/

```

I did the following command for a dummy rsync with the output:
```

rsync -avv -n --exclude="*Holiday\ Cardz" /home/dummy/test_dir/ /home/dummy/test_dir2/

sending incremental file list
[sender] hiding directory Holiday Cardz because of pattern *Holiday\ Cardz
delta-transmission disabled for local transfer or --whole-file
./
dir1/
dir1/file1
dir2/
dir2/file2
dir3/
dir3/file3
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 154 bytes  received 36 bytes  380.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)

```
So just from this example and making this work the way you need it, the command seems to be working the way you need it. If you can help me out with some examples of what you are trying to accomplish, then I can take a look at it further.

Cheers!

---

### Post by firegs on 2011-06-03
Ah, okay, perhaps I didnt clarify.
```

/home/dummy/test_dir/
   |
   |___ .../dir1/                  - modified date 6/1/2011
   |          |__/IMAGE/           - modified date 6/1/2011
   |          |    |_________file1 - modified date 5/30/2011
   |          |    |_________file2 - modified date 4/22/2011
   |          |    |_________file3 - modified date 2/12/2011
   |          |__/MISC/            - modified date 6/1/2011 
   |               |_________file1 - modified date 6/1/2011
   |
   |
   |___ .../dir2/                  - modified date 5/20/2011
   |          |__/IMAGE/           - modified date 5/20/2011
   |          |    |_________file1 - modified date 5/1/2011
   |          |    |_________file2 - modified date 5/1/2011
   |          |    |_________file3 - modified date 6/1/2011
   |          |__/MISC/            - modified date 5/20/2011
   |               |_________file1 - modified date 5/20/2011
   |
   |
   |___ .../~Holiday Cardz/         - modified date 6/1/2011

/home/dummy/test_dir2/

```


That's an example of what I'm dealing with. I need to have the script look at the date modified of the "root" folders for each print job (thats what these are btw). A root folder being "dir1" and "dir2", or the o912961H folders ive been referring to. Sometimes, the files in those folders like file1-3, etc (which are JPG's) have modified dates that are WAY older than the Print Job was created, because thats the date the pictures were taken. 

So, what i need to do is look at the roots, determine if they're older than 7 days (IGNORING everything inside of them), if they are 7 days or older, copy the entire folder (with everything inside) to another server. Once that's done, delete said copied folders from the source, or server 1.

So right now, the rsync is copying alll of the root folders. I need it to only copy ones last modified later than 7 days (which in my example would only be dir2, and then copy everything inside Dir2 to the server. (And of course, keeping file structure)

And of course, I need to skip "~Holiday Cardz", because I need to write another script that does the same thing as this one (back up to another server then delete from the source) but files only older than 21 days instead of 7.

Sounds easy, no? xD
~Sam

---

### Post by ruffEdgz on 2011-06-03
Sweet, that makes more sense and after looking over my script again, I did find the problem (must of had the case of the Mondays).

Code below will only grab the directory that were not modified in the past 7 days and move that directory to the destination server you asked for.
```

#!/bin/bash
IFS=$'\n'
source_dir="/home/labop/servers/lifepicsserver"
dest_dir="/home/labop/servers/jabba/lifepicsserverBackUp"
dir_select=($(find $source_dir -maxdepth 1 -mtime 6 -type d | egrep -v "^$source_dir$"))

for line in ${dir_select[@]}; do
        rsync -avv --exclude="**Holiday\ Cardz" $line $dest_dir
        if [ ! $(echo $line | egrep "*Holiday\ Cardz") ]; then
                rm -rf $line
        fi
done

```
****NOTE**** Since this script deletes, like below, please make a backup if you can then execute the script ****NOTE****

Once you like this, I can also do the request about the "~Holiday Cardz" quoted below in the same script (just want to make sure this works
> 
And of course, I need to skip "~Holiday Cardz", because I need to write another script that does the same thing as this one (back up to another server then delete from the source) but files only older than 21 days instead of 7.


Cheers!

---

### Post by firegs on 2011-06-03
Hey there again,

I really do appreciate the help - its going to be a life safer! I'm not at the office again until Monday, but I will try it out then and give the feedback. Thanks again, in advance!

~Sam :popcorn:

---

### Post by firegs on 2011-06-06
Hey there,

Just tested it out. 

```
labop@ubuntu-box:~$ sudo ./lpsb.sh
sending incremental file list
delta-transmission disabled for local transfer or --whole-file
16770777/
16770777/16770777_4x6 Print_Glossy__001(6).jpg
16770777/16770777_4x6 Print_Glossy__002(6).jpg
16770777/16770777_4x6 Print_Glossy__003(6).jpg
16770777/16770777_4x6 Print_Glossy__004(6).jpg
16770777/16770777_4x6 Print_Glossy__005(6).jpg
16770777/16770777_4x6 Print_Glossy__006(6).jpg
16770777/16770777_4x6 Print_Glossy__007(6).jpg
16770777/16770777_4x6 Print_Glossy__008(6).jpg
16770777/16770777_4x6 Print_Glossy__009(6).jpg
16770777/16770777_4x6 Print_Glossy__010(6).jpg
16770777/16770777_4x6 Print_Glossy__011(6).jpg
16770777/16770777_4x6 Print_Glossy__012(6).jpg
16770777/16770777_4x6 Print_Glossy__013(6).jpg
16770777/16770777_4x6 Print_Glossy__014(6).jpg
16770777/16770777_4x6 Print_Glossy__015(6).jpg
16770777/16770777_4x6 Print_Glossy__016(6).jpg
16770777/16770777_4x6 Print_Glossy__017(6).jpg
16770777/16770777_4x6 Print_Glossy__018(6).jpg
16770777/16770777_4x6 Print_Glossy__019(6).jpg
16770777/16770777_4x6 Print_Glossy__020(6).jpg
16770777/16770777_4x6 Print_Glossy__021(6).jpg
16770777/16770777_4x6 Print_Glossy__022(6).jpg
16770777/16770777_4x6 Print_Glossy__023(6).jpg
16770777/16770777_4x6 Print_Glossy__024(6).jpg
16770777/16770777_4x6 Print_Glossy__025(6).jpg
16770777/16770777_4x6 Print_Glossy__026(6).jpg
total: matches=0  hash_hits=0  false_alarms=0 data=53946187

sent 53954395 bytes  received 510 bytes  8300754.62 bytes/sec
total size is 53946187  speedup is 1.00
labop@ubuntu-box:~$ sudo ./lpsb.sh
labop@ubuntu-box:~$ sudo ./lpsb.sh

```

It only copied one folder D:

I tried to run it again, but it just returned nothing. Any ideas?

---

### Post by ruffEdgz on 2011-06-06
So if you do the following command, how many directories would be backed up?
```
find /home/labop/servers/lifepicsserver -maxdepth 1 -mtime 6 -type d | egrep -v "^/home/labop/servers/lifepicsserver$"
```

---

