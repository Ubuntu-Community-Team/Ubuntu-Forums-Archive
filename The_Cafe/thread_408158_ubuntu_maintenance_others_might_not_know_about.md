---
title: "ubuntu maintenance others might not know about"
date: 2007-04-13
forum: The Cafe
---

### Post by Mateo on 2007-04-13
this thread is for maintenance related topics in ubuntu.  What are some things you do to maintain your computer that others might not consider or know about?  Here's a couple for me:

1)  Clean out your root Trash!  This is something I forget about, but you actually do delete some stuff while in root from time to time.  This can quickly build up in the trash and take up a lot of space.  Since it's not easy to delete some of the files in nautilus, this the best way to do it:

```
sudo -i
rm -rf /root/.Trash/*
```

2)  Clean out your ~/.thumbnails folder!!  If you use nautilus, that is.  This is something I didn't realize until recently, but thumbnails take up a lot of memory (obviously, since they are images).  Mine was up to almost 100 megabytes.  Unfortunately, when you have thousands of files, neither nautilus nor rm will delete them all at once.  This is what I did:

```
rm -f a*
rm -f b*
```

so that it only deletes a few dozen at a time and will work.
------------------------------

Any other maintenance suggestions?

---

### Post by aysiu on 2007-04-13
```
rm -rf *
``` is not something I'd *ever* recommend someone to type in the terminal. That can be extremely dangerous.

---

### Post by Mateo on 2007-04-13
not as long as you are in the correct directory ;)

---

### Post by tscook on 2007-04-13
Xubuntu doesn't automatically include update-notifier, which was really useful.

Just install it via apt and run it once and will run from there on out.

---

### Post by amohanty on 2007-04-13
> 
1) Clean out your root Trash! This is something I forget about, but you actually do delete some stuff while in root from time to time. This can quickly build up in the trash and take up a lot of space. Since it's not easy to delete some of the files in nautilus, this the best way to do it:


You should not need to do that unless you use nautilus in sudo mode. Something I would not recommend. root really should not be deleting files, unless said files were created accidentally or due to a crash etc. In which case as aysiu said _never_ use *, always do an explcit delete using **rm filename**

> 2) Clean out your ~/.thumbnails folder!! If you use nautilus, that is. This is something I didn't realize until recently, but thumbnails take up a lot of memory (obviously, since they are images). Mine was up to almost 100 megabytes. Unfortunately, when you have thousands of files, neither nautilus nor rm will delete them all at once. This is what I did:


In your nautilus preferences, you can turn it off or make the fiel sizes really small (I set mine to 100K).

HTH
AM

---

### Post by Mateo on 2007-04-13
> **amohanty said:**
> You should not need to do that unless you use nautilus in sudo mode. Something I would not recommend. root really should not be deleting files, unless said files were created accidentally or due to a crash etc. In which case as aysiu said _never_ use *, always do an explcit delete using **rm filename**

root has a trash can just like the users do.  it gets files in it.  you can use root nautilus but it won't be able to delete all of the file.

you can delete them name by name, if you want to waste a lot of your time.



> In your nautilus preferences, you can turn it off or make the fiel sizes really small (I set mine to 100K).

HTH
AM

nah, i like the thumbnails.  i just like to clean them out once in a great while.  a lot of the thumbnails are for files that aren't even on my computer any more.

---

### Post by Mateo on 2007-04-13
> **tscook said:**
> Xubuntu doesn't automatically include update-notifier, which was really useful.

Just install it via apt and run it once and will run from there on out.

yeah, is that the tray icon (orange)?  i actually took that off my computer.  i don't want to upgrade every other day, and i don't want to look at the tray icon all the time.  but it is good for maintenance for some people.

---

### Post by amohanty on 2007-04-13
> root has a trash can just like the users do. it gets files in it. you can use root nautilus but it won't be able to delete all of the file.


AFAIK that should not happen until you actually use nautilus in sudo mode, at which time a whole bunch of stuff will be created. Could be wrong though. Will check on that.

Thanks.
AM

---

### Post by amac777 on 2007-04-13
> **Mateo said:**
> not as long as you are in the correct directory ;)

I second aysiu's opinion that you should never type 'rm -rf *'.

Even if you change into the *correct* directory first.... 

The reason is that as you get used to doing repeated commands you will often type them very quickly, even in advance of your brain processing the output from the computer. What happens if you get going quickly with your commands and the following occurs:

# cd /root/.trash
/root/.trash: No such file or directory ...
#rm -rf *

---

### Post by Mateo on 2007-04-13
> **amac777 said:**
> I second aysiu's opinion that you should never type 'rm -rf *'.

Even if you change into the *correct* directory first.... 

The reason is that as you get used to doing repeated commands you will often type them very quickly, even in advance of your brain processing the output from the computer. What happens if you get going quickly with your commands and the following occurs:

# cd /root/.trash
/root/.trash: No such file or directory ...
#rm -rf *

well you should be careful, of course.  But there is no other way to get all of the files (that i've read so far).  if you know of a safer way, i'd like to hear it.

by the way, you're going to start out in the /root/ directory anyways, so worst case scenario you still only delete the configuration files in that directory.

still, there is nothing wrong with rm -rf * when you are in the right directory.

---

### Post by amac777 on 2007-04-13
> **Mateo said:**
> well you should be careful, of course.  But there is no other way to get all of the files (that i've read so far).  if you know of a safer way, i'd like to hear it. 

Sorry, I should have put a safer way in my last post to show you what I meant. It's safer to put the directory you want to totally wipe out with its subdirectories within the command:

#rm -rf /root/.Trash

That will avoid the nasty problem I described above and will still erase /root/.Trash along with all the files and subdirectories.

---

### Post by amohanty on 2007-04-13
I think I posted this somewhere earlier but this is what I use. Even in sudo mode it will dump all files in the users trash

use **del ...** to delete
use **del -p ** to purge

```
#! /bin/bash

delete() {
  if [ $# -gt 0 ]; then
    for f in $@; do
      if [[ -f $f || -h $f ]]; then
        mv --backup=numbered -f $f ~/.Trash
      elif [ -d $f ]; then
        local tmp
        tmp=$(echo $f | sed -e 's/\///g')
        mv -f $f ~/.Trash/$tmp.$(date +%m%d%y.%H%M%S)
      else 
        echo $f not found.
      fi      
    done
  fi
}

rm_all_in_dir() {
  count=0
  OFS=$IFS
  IFS='
'
  for f in $(/bin/ls -1 -a $1); do
    if [[ $f != '.' && $f != '..' ]]; then
      /bin/rm -rf $1/$f
      let count=count+1
    fi
  done
  echo $count files and dirs deleted.
  IFS=$OFS
}

purge() {
  local -a del_array
  idx=0
  OFS=$IFS
  IFS='
'
  echo Select file\(s\) to delete or type a to delete all:
  for f in $(/bin/ls -1 -A ~/.Trash); do
    echo $(( $idx+1 )). $f
    del_array[idx]=$(echo ~/.Trash/$f)
    let idx=idx+1
  done
  read reply
  if [[ $reply != '' && $reply = 'a' ]]; then
    rm_all_in_dir ~/.Trash
  else
    multi=$(echo $reply | grep ,)
    if [ ! -z $multi ]; then
      del_file_idxs=$(echo $multi | sed 's/,/\n/g')
      cnt=0
      for i in $del_file_idxs; do
        /bin/rm -rf ${del_array[$(( $i-1 ))]}
        let cnt=cnt+1
      done
      echo $cnt files and dirs purged.
    fi
  fi
  IFS=$OFS
}

while getopts prf name; do
  case $name in
  p) 
    purge
    exit 0
    ;;
  r|f|*)
    shift $[$OPTIND-1]
    ;;
  esac
done

if [ $# -gt 0 ]; then
  delete $@
fi
exit 1


```

AM

---

### Post by Mateo on 2007-04-13
> **amac777 said:**
> Sorry, I should have put a safer way in my last post to show you what I meant. It's safer to put the directory you want to totally wipe out with its subdirectories within the command:

#rm -rf /root/.Trash

That will avoid the nasty problem I described above and will still erase /root/.Trash along with all the files and subdirectories.

hmm, that's close.  if you can think of a way to adjust this so that it doesn't delete the .Trash folder, but does delete everything in the trash folder (including the subfolders), i will change my initial post with this way instead.

---

### Post by zanglang on 2007-04-13
This command works great for deleting old thumbnails. :) I have noatime enabled for my partitions so it tends to overdelete, but running it once a while does free up lots of otherwise useless space.
```
find ~/.thumbnails -type f -atime +14 -delete
```

Edit: This works for gzipped log files. As a regular user I don't have a need for them, so might as well free up a few megabytes.
```
sudo find /var/log -type f -name *.gz -delete
```

---

### Post by Mateo on 2007-04-13
wow, thanks zanglang.  i'm going to have to try that now.  sounds a lot easier than what i was doing.  not sure if i understand it though...

---

### Post by amohanty on 2007-04-13
[http://www.opengroup.org/onlinepubs/009695399/utilities/find.html](http://www.opengroup.org/onlinepubs/009695399/utilities/find.html)

---

### Post by amac777 on 2007-04-13
> **Mateo said:**
> hmm, that's close.  if you can think of a way to adjust this so that it doesn't delete the .Trash folder, but does delete everything in the trash folder (including the subfolders), i will change my initial post with this way instead.

Add a /* at the end like this:

#rm -rf /root/.Trash/*

That will leave the directory .Trash but delete files and subdirectories within it.

Probably still going to be people that recommend safer ways. I'd be interested in seeing them too.

---

### Post by Mateo on 2007-04-13
thanks, i'm changing the original post now.

---

### Post by guitarmaniac on 2007-04-13
why not just use shift+delete if you are using nautilus as root to delete something? Save all the hassle of difficult commands, but then again I just feel more comfortable if I only use the terminal when I need to.

---

### Post by amac777 on 2007-04-15
> **Mateo said:**
> yeah, is that the tray icon (orange)?  i actually took that off my computer.  i don't want to upgrade every other day, and i don't want to look at the tray icon all the time.  but it is good for maintenance for some people.

BTW, for those of you who do download updates, or if you install lots of programs using apt-get, after they are installed the .deb file is still cached on your hard disk and taking up space. To clean up these unnecessary files:

sudo apt-get clean

This will automatically remove all the unnecessary cached .deb files from apt-get. If you install lots of programs or updates,  periodically running this command will save lots of space.

---

### Post by Mateo on 2007-04-22
good idea amac777.  would it be possible to give your user permission to run this command?  just the apt-get clean (not apt-get install or apt-get remove)?  if so, you can set up a cronjob that does it automatically once a month or so...

or maybe that wouldn't be necessary.  can't you put scripts in some cron directory that will automatically do them, or does that require permissions as well?

---

### Post by reacocard on 2007-04-22
> **amac777 said:**
> BTW, for those of you who do download updates, or if you install lots of programs using apt-get, after they are installed the .deb file is still cached on your hard disk and taking up space. To clean up these unnecessary files:

sudo apt-get clean

This will automatically remove all the unnecessary cached .deb files from apt-get. If you install lots of programs or updates,  periodically running this command will save lots of space.

Or you can use
```
sudo apt-get autoclean
```
Which only removes debs that are no longer in any repository. It's more useful with devel releases or with 3rd-party repos than with Ubuntu's stable repos, but it's a nice option nonetheless.

---

