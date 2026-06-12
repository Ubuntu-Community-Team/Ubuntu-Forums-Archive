---
title: "Whats your backup scheme?"
date: 2008-02-20
forum: The Cafe
---

### Post by xelapond on 2008-02-20
Well, what are all of your backup schemes?  I just had a flash drive with my latest data on it(stupid me) that recently died.  I lost a lot of useful data, so I have been thinking about some backup schemes, and just wanted to know what everyone else here did.

Here is what I am hoping to do:
[http://ubuntuforums.org/showthread.php?t=702932](http://ubuntuforums.org/showthread.php?t=702932)

---

### Post by Mateo on 2008-02-20
Good topic.  of course, having a home server is probably the best way to go.  Your scenario is interesting.  I was wondering how you planned on having your diff system work.

Currently I use flash drives. I back up stuff like projects i'm working on.  I created a script which tars my directories and then copies them onto the flash drive and also onto a hidden folder on my main hard drive.  This works more or less, usually.  I have to run the script manually though.

---

### Post by xelapond on 2008-02-20
I am sure there would be a way to diff a bunch of files recursively.  I believe git(version control system) does this when you merge 2 large branches.  It will be a very interesting project, anyway.  Do you think that could be a feasible backup scheme?

---

### Post by RebounD11 on 2008-02-20
I use mostly Flash drives and External harddrives, the Flash drives for small files and folders (<16GB) and the external hdd for major backups (since I switched to linux I use it mostly for storing memories - photos, movies,  books anything I want to keep, collect or simply love).

My father uses DVD's, and backup hdd images that he burns on them, he uses DVD-RW's so he can update the backup image, even if he also uses my external hdd if available :)

the home server is also a good idea, remote ones are better but more expensive... your idea is almost paranoid :D however that data must be extremely important to you in which case I think it might be crazy enough to be useful too... for veeeery large amounts of data.

---

### Post by xelapond on 2008-02-20
Ha, yeah, I guess you could look at that as being paranoid about my data, but I already have the servers(READ: decommissioned computers(celeron 2.5Ghz and a 833Mghz G4), they are just not being used at all.  Most of all I i think it would be fun, nobody really NEEDS there data to be that secure, but it would be a fun project.

---

### Post by FuturePilot on 2008-02-20
Backup of /home to my external drive once a week with Sbackup

---

### Post by Polygon on 2008-02-20
```
#!/bin/sh

rdiff-backup --exclude /home/mark/.Trash/ --exclude /home/mark/.thumbnails/ --exclude /home/mark/svn/ --exclude /home/mark/.cache/ --exclude /home/mark/.wine/drive_c/windows/temp/ --exclude /home/mark/.nautilus/saved/ --exclude /home/mark/.java/deployment/cache/ --exclude /home/mark/.metacity/sessions/ --exclude /home/mark/.mozilla/*/Cache/ --exclude /home/mark/.beagle/ /home/mark/ /media/LinuxBackup/Backups/rdiff/

```

i set a cronjob to run this at midnight every day, which makes time-stamped diff's of my home folder which goes to my external 500gb drive.

---

### Post by Mateo on 2008-02-20
You need to put one of the servers into a nuclear fallout shelter, just in case ;)

---

### Post by GSF1200S on 2008-02-20
Ive honestly always been horrible about backing up my stuff, and ive lost countless pictures due to Windows crapping itself, or more than likely, my inability at the time to properly maintain it.

Since moving to Ubuntu about a year ago, im still horrible about backing up, but I dont worry as much knowing that Linux wont just crap itself or get destroyed by some virus, and because I know about LiveCD's, which means only a complete hard drive failure could keep me from my data.

That said, i recently moved to a new 200GB 7200RPM drive for my lappy, and I didnt want to have to reinstall. So, using partimage, I made a copy of my linux partition to my external TB drive, and since then Ive been alot better about throwing music and pictures, etc on the drive as well. 

So, my answer is kind of external hd and kind of software based... Partimage is an AWESOME way to back up a perfectly running system so you dont have to start from scratch if you dont want to...

---

### Post by fedex1993 on 2008-02-20
well right now i use a portbal hard drive and also a home server. The home server is in the works after switching over to openbsd as a router and also as a file server and i love the soft raid idea. The hdd i use for big backups like entire system but also all my favorite files and my .torrent files but some other stuff to

---

### Post by yabbadabbadont on 2008-02-20
CD/DVD copies of not easily replaceable stuff.  tar backups of /home to a second, internal, hard drive once in a while.  tar backup of root filesystem to second drive prior to any major change in the system.  (or every couple of months, whichever comes first)

---

### Post by smartboyathome on 2008-02-20
I don't backup currently, but am looking into installing arch just to make backups and as a recovery system.

---

### Post by igknighted on 2008-02-20
I plan on building a home server with RAID once I have the money.  It will probably be a windows server (I get it all free via MSDNAA haha) because most of the computers at my house are windows vista and I don't want to make that any more complex then it has to be, but I need something.  Right now all my data is on single hard drives.  I have an external, but it's more for storage of data on a disk that can go from my desktop to my laptop, and so when I reformat my OS (every other week or so? :P) the data isn't at risk.

---

### Post by mridkash on 2008-02-21
I'm making a backup script (for fun) which finds all files which are modified after the day you set in calendar. Then according to your preference it selects files to keep, like all files or no hidden files or manual etc. Then it writes the list of files to a text file.
It does not do actual backup as yet.

I'm learning bash scripting. Here's the script. Feel free to modify it to your needs or help me improve it.

[php]#!/bin/bash
# PlusBackup
# Author: Mridul Kashatria

#default
numDays=1            #number of days for incremental backup
numFiles=0        #number of files
prgrssNum=0        #progress number
prgrssPerc=0        #progress Percentage
hiddenFiles="None"    #default value of whether to include hidden files
dateToday=`date +%s`

if [ $# -eq 3 ] ; then    #if cmd-line options are given then accept them
    numDays=$1
    hiddenFiles="$2"
    backupDir="$3"
else                    #else use zenity dialogs to get the info
    chosenDate=`zenity --calendar --date-format %s --text "Files Modified after the Selected Date will be Backed up"`
    numDays=$(expr `expr $dateToday / 86400` - `expr $chosenDate / 86400`)
    hiddenFiles=`zenity --list --text "Select Hidden Files to Include" --radiolist --column "Select" --column "Hidden Files" TRUE "None" FALSE "Some" FALSE "All"` 
    backupDir=`zenity --file-selection --directory --title "Where do you want to Backup Files?"`
    
fi
if cd "$backupDir" 2>/dev/null; then
    mkdir ./config 2>/dev/null
    :> ./config/backup.list # Create and empty the backup.list file
    allFiles=$(find /home -mtime -$numDays | tee >(zenity --progress --pulsate --auto-close --text "Finding Files Modified Since $numDays days...") )
    numFiles=$(echo "$allFiles" | wc -l)

    (        #run in subshell to pipe output in zenity progress
            
    echo "$allFiles" | while read File ; do
        prgrssNum=$(expr $prgrssNum + 1 )
        prgrssPerc=$(expr $prgrssNum \* 100)
        echo `expr $prgrssPerc / $numFiles`
        if [[ -f "$File" ]] ; then        #if $File is regular file
            case "$hiddenFiles" in
                "All" )
                    echo "$File" >> ./config/backup.list
                    ;;
                "Some" )                #TODO Add Functionality to personalize the folders the user wants to backup and create profiles
                    echo "$File" | grep -e "\.mozilla" | grep -v -e "Cache" >> ./config/backup.list
                    echo "$File" | grep -e "\.purple" >> ./config/backup.list
                    echo "$File" | grep -e "\.gnome2" >> ./config/backup.list
                    echo "$File" | grep -e "\.gconf" >> ./config/backup.list
                    echo "$File" | grep -e "\.evolution" >> ./config/backup.list
                    echo "$File" | grep -v -e "[/][.]" >> ./config/backup.list
                    ;;
                "None" )
                    echo "$File" | grep -v -e "[/][.]" >> ./config/backup.list
                    ;;
            esac
        fi
    
    done

    ) | zenity --progress --percentage=0 --auto-close --auto-kill --text "Preparing File List..."

    if [ $? ] ; then
        zenity --info --text "File List Created, `cat ./config/backup.list | wc -l` files found"
    else
        zenity --error --text "Boo Boo"
    fi
fi
#echo $numFiles
#file -N -f - | grep -v directory[/php]

---

### Post by angry_johnnie on 2008-02-21
i keep all my personal stuff --music, videos, documents, pictures-- on a separate, storage only, box, and use remastersys for all the programs.  But, I better learn a more efficient way to back up soon.  The last tiime I ran remastersys I ended up with a 4.2 Gb image, and I suspect I won't be able to squeeze everything into a dvd next time.

---

### Post by frrobert on 2008-02-21
In the office I have two PCs.  One of them has a spare drive that the home directory from both machines is backed up to.  Then I back up that drive to an external drive which I store in the fire safe.

I backup about once a week  except for my active project directory which I backup daily.

---

