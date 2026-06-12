---
title: "What's your favorite shell script?(Please post it.)"
date: 2010-09-21
forum: The Cafe
---

### Post by darkstarbyte on 2010-09-21
So far my favorite shell script is now out dated but it used to work fine it would unrar files for me but they built that into the gui. I am unsure how it goes now because I don' use it anymore.

If anyone has a shell script that uses ffmpeg that converts any media format to h.264 please let me know. Also if anyone has one that will compress files to .bz2 i would be grateful.

---

### Post by darkstarbyte on 2010-09-22
I am surprised by how many people don't use shell scripts no response after 1 days.

---

### Post by kevin11951 on 2010-09-23
I found one that coverts a laptop battery into a USP.  In other words, it will check the laptop battery state every "n" minutes ("n" based on the crontab) to see if it is "discharging".  If it is, it shuts down the server/laptop.

```

#!/bin/bash

batt=`grep ^charging\ state /proc/acpi/battery/BAT1/state | sed 's/^charging state[:]  *//'`
if [ $batt = "discharging" ]; then
    halt
fi  

```

It is also VERY easily customized if you can read it and understand what everything does.

I am a sysadmin who converts cheap computers into servers as part of my job, so I may be predisposed to liking this ;).

---

### Post by Windows Nerd on 2010-09-23
> **darkstarbyte said:**
> So far my favorite shell script is now out dated but it used to work fine it would unrar files for me but they built that into the gui. I am unsure how it goes now because I don' use it anymore.

If anyone has a shell script that uses ffmpeg that converts any media format to h.264 please let me know. Also if anyone has one that will compress files to .bz2 i would be grateful.

So hey would you mind posting the concept of the shell script here? I still use the CLI to untar things, but often forget the options for the various formats (.tgz , .bz2, tbz, ect). Yes, I know it is much easier in the GUI, but when you have to click 4 times to open it (and leave the keyboard for your mouse) it is largely a pain in the *** an inefficient.

---

### Post by Bodsda on 2010-09-23
> **Windows Nerd said:**
> So hey would you mind posting the concept of the shell script here? I still use the CLI to untar things, but often forget the options for the various formats (.tgz , .bz2, tbz, ect). Yes, I know it is much easier in the GUI, but when you have to click 4 times to open it (and leave the keyboard for your mouse) it is largely a pain in the *** an inefficient.
 
If you find you keep forgetting all the options, I wrote a cli app to store commands that you can then lookup and reuse.
 
[https://launchpad.net/cheatsheet](https://launchpad.net/cheatsheet)
 
Bodsda

---

### Post by darkstarbyte on 2010-09-23
> **Windows Nerd said:**
> So hey would you mind posting the concept of the shell script here? I still use the CLI to untar things, but often forget the options for the various formats (.tgz , .bz2, tbz, ect). Yes, I know it is much easier in the GUI, but when you have to click 4 times to open it (and leave the keyboard for your mouse) it is largely a pain in the *** an inefficient.

There is a shell script for this but the one I am thinking of you would have to transfer into the directory every time you want to uncompress some thing.
If I write one you may not like it as much as most peoples, but such a shell script most likely won't be bigger than a megabyte if that.

---

### Post by CharlesA on 2010-09-23
I use shell scripts all the time. I don't have any that'll convert video, since I don't do that. :P

I use one to compile drivers for my RAID. :)

---

### Post by Sporkman on 2010-09-23
Tarcrypt!

```
#!/bin/bash -u

CRYPTKEYFILE=/home/user/mykeyfilewitharandompassphrase

function tarcrypt()
{
   OP="${1}"
   SRC="${2}"
   DST="${3}"

   if [ ${#@} -ne 3 ] || ( [ $OP != "e" ] && [ $OP != "d" ] ); then
      echo ""
      echo "Usage:"
      echo ""
      echo "   tarcrypt <mode> <source> <dest>"
      echo ""
      echo "      mode: \"e\" to encrypt, \"d\" to decrypt"
      echo ""
      return 1
   fi
   
   if [ `which ccrypt` == "" ]; then
      echo "Error: \"ccrypt\" needs installed"
      return 1
   fi
   
   if [ ! -e "${SRC}" ]; then
      echo "Error: Source file \"${SRC}\" does not exist"
      return 1
   fi
   
   if [ -e "${DST}" ]; then
      echo "Error: Destination file \"${DST}\" already exists"
      return 1
   fi
   
   if [ ${OP} == "e" ]; then
      tar cvzpfh - "${SRC}" | ccrypt -ef -k "${CRYPTKEYFILE}" > "${DST}"
      return $?
   elif [ ${OP} == "d" ]; then
      ccrypt -df -k "${CRYPTKEYFILE}" < "${SRC}" | tar xvzpfh -
      return $?
   fi

   return 1
}

```

---

### Post by markp1989 on 2010-09-23
> **kevin11951 said:**
> I found one that coverts a laptop battery into a USP.  In other words, it will check the laptop battery state every "n" minutes ("n" based on the crontab) to see if it is "discharging".  If it is, it shuts down the server/laptop.

```

#!/bin/bash

batt=`grep ^charging\ state /proc/acpi/battery/BAT1/state | sed 's/^charging state[:]  *//'`
if [ $batt = "discharging" ]; then
    halt
fi  

```

It is also VERY easily customized if you can read it and understand what everything does.

I am a sysadmin who converts cheap computers into servers as part of my job, so I may be predisposed to liking this ;).

Thats a pretty clever idea :) , i used to use an old eee pc as a web server, 1 day i accidentally unplugged it, and the battery died, and for some reason it hasnt worked since, as soon as i plug it in i get a high pitched noise from the motherboard, power button does nothing. 

Still a cool concept :)

---

### Post by FakeOutdoorsman on 2010-09-23
> **darkstarbyte said:**
> If anyone has a shell script that uses ffmpeg that converts any media format to h.264 please let me know.

Let's make one:
```
#!/bin/sh

# Simple video encoding script
# Usage: ./foo2mkv.sh input.foo output.mk4

# Encode with FFmpeg and libx264:
ffmpeg -i $1 -acodec copy -vcodec libx264 -vpre medium -crf 22 -map_meta_data 0:0 -threads 0 -f matroska $2

# Play a sound when finished:
aplay /usr/share/sounds/alsa/Front_Center.wav
```
Now save as foo2mkv.sh and then make is executable:
```
chmod +x foo2mkv.sh
```
Usage example:
```
./foo2mkv.sh input.avi output.mkv
```
A super simple example.  It copies the audio from the input and re-encodes the video to H.264.  I didn't know if you had any particular options that you required, so I made something fairly generic.  It then plays a sound when finished.  I just found a wav file that most desktop Ubuntu installations should already have, but of course you can change it to anything else.

You'll need to make sure your FFmpeg has libx264 enabled.  That's easy to do:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg[/url]

---

### Post by conundrumx on 2010-09-23
This is actually a function built into my .profile:

```
extract () {
    if [ -f $1 ] ; then
        case $1 in
            *.tar.bz2)   tar xjf $1        ;;
            *.tar.gz)    tar xzf $1     ;;
            *.bz2)       bunzip2 $1       ;;
            *.rar)       unrar x $1     ;;
            *.gz)        gunzip $1     ;;
            *.tar)       tar xf $1        ;;
            *.tbz2)      tar xjf $1      ;;
            *.tgz)       tar xzf $1       ;;
            *.zip)       unzip $1     ;;
            *.Z)         uncompress $1  ;;
            *.7z)        7z x $1    ;;
            *)           echo "'$1' cannot be extracted this way." ;;
        esac
    else
        echo "'$1' is not a valid file."
    fi
}
```

Enjoy.

---

### Post by koenn on 2010-09-23
Here are a few i did a few years ago
[http://users.telenet.be/mydotcom/program/shell/words.htm](http://users.telenet.be/mydotcom/program/shell/words.htm)

my favorites are
- the script to cheat on a "change one letter" game (I used it in a cafe game thread on this forum)

- 99 bottles of beer

---

### Post by darkstarbyte on 2010-09-23
Thanks every one for the shell scripts. Please keep posting.

---

### Post by lkjoel on 2010-09-23
CPanel.sh
Its in Post-Fix your sound! in my signature.

---

### Post by CharlesA on 2010-09-23
First one:

```
#!/bin/bash

###
### vmware.sh
### Script to install VMware Server on Ubuntu 10.04
### See: http://communities.vmware.com/thread/267682
### See: https://help.ubuntu.com/community/VMware/Server
###

VMWARE=VMware-server-2.0.2-203138.x86_64.tar.gz
VMDIR=vmware-server-distrib
# Color Variables
RED='\E[30;31m'
GREEN='\E[30;32m'
YELLOW='\E[30;33m'
BLUE='\E[30;34m'
MAGENTA='\E[30;35m'
CYAN='\E[30;36m'
WHITE='\E[30;37m'
RESET="tput sgr0"

# Install gcc, which is used for compiling vmware kernel modules
apt-get install gcc --assume-yes || { echo -e $RED"Failed to install gcc"; $RESET; exit; }
# Make the patch script executable, if it isn't already
chmod +x patch-vmware_2.6.3x.sh || { echo -e $RED"Failed to change permissions on patch-vmware_2.6.3x.sh"; $RESET; exit; }
# Extract VMware Server archive, else exit
if [ -f $VMWARE ]
then
  echo -e "Extracting VMware Server archive...\c"&& tar -xf $VMWARE && echo -e $GREEN"\t\t\t\t\tDone!"; $RESET
else
  { echo -e $GREEN"VMware Server archive does not exist!"; $RESET; exit; }
fi
# Run the patch script
./patch-vmware_2.6.3x.sh $VMDIR/lib/modules/source/ > /dev/null && echo -e $GREEN"VMware Server patched successfully!"; $RESET
# Install Vmware Server
./$VMDIR/vmware-install.pl || { echo -e $RED"Install of VMware Server Failed"; $RESET; exit; }
```

Second one:

```
#!/bin/bash

###
### rr.sh
### Script to notify me if a reboot is required
### Created by CharlesA
### Tested 8/29/2010
### Updated 8/30/2010
###

BIN=/bin/
USR=/usr/bin/
EMAIL=email@host
CELL=email@host

if [ -f /var/run/reboot-required ]
then
   echo "Reboot Required" | ${USR}mail -s "Reboot Required" $EMAIL $CELL
fi
# eof

```

Third one:

```
#!/bin/bash

###
### smart.sh
### Script to check SMART on all drives
### Created by CharlesA
### Tested 8/29/2010
### Updated 8/29/2010
###

BIN=/bin/
USR=/usr/bin/
HOME=/home/charles/
LOGS=${HOME}logs/
BIN=/bin/
USBIN=/usr/sbin/
EMAIL=email@host
OS="OS Drive"
RAID1="RAID Drive 1"
RAID2="RAID Drive 2"
RAID3="RAID Drive 3"
DOC="Doc Drive"
DVD="DVD Drive"

echo $OS > ${LOGS}smartmon1 && ${USBIN}smartctl -a /dev/sda >> ${LOGS}smartmon1
echo $OS > ${LOGS}results1 && ${BIN}grep "result" ${LOGS}smartmon1 >> ${LOGS}results1

echo $RAID1 > ${LOGS}smartmon2 && ${USBIN}smartctl -a -d hpt,1/1 /dev/sdb >> ${LOGS}smartmon2
echo $RAID1 >> ${LOGS}results2 && ${BIN}grep "result" ${LOGS}smartmon2 >> ${LOGS}results2

echo $RAID2 > ${LOGS}smartmon3 && ${USBIN}smartctl -a -d hpt,1/2 /dev/sdb >> ${LOGS}smartmon3
echo $RAID2 > ${LOGS}results3 && ${BIN}grep "result" ${LOGS}smartmon3 >> ${LOGS}results3

echo $RAID3 > ${LOGS}smartmon4 && ${USBIN}smartctl -a -d hpt,1/3 /dev/sdb >> ${LOGS}smartmon4
echo $RAID3 > ${LOGS}results4 && ${BIN}grep "result" ${LOGS}smartmon4 >> ${LOGS}results4

echo $DOC > ${LOGS}smartmon5 && ${USBIN}smartctl -H /dev/sdc >> ${LOGS}smartmon5
echo $DOC > ${LOGS}results5 && ${BIN}grep "SMART" ${LOGS}smartmon5 >> ${LOGS}results5

echo $DVD > ${LOGS}smartmon6 && ${USBIN}smartctl -H /dev/sdd >> ${LOGS}smartmon6 &&
echo $DVD > ${LOGS}results6 && ${BIN}grep "SMART" ${LOGS}smartmon6 >> ${LOGS}results6

${BIN}cat ${LOGS}result* > ${LOGS}summary
${BIN}cat ${LOGS}smartmon? > ${LOGS}smart.log
${BIN}rm ${LOGS}result* ${LOGS}smartmon*
${BIN}cat ${LOGS}summary | ${USR}mail -s "SMART Status `${BIN}date +%D`" $EMAIL
${BIN}rm ${LOGS}summary
# eof
```

I'm sure they can be cleaned up a bit, and they aren't the best scripts you'll find, but they work for me. ;)

---

### Post by leef on 2010-09-24
```

#!/bin/bash

# boot mod script

### Variables ###

bootdir=/boot/grub
tempfile=/tmp/grubconfig
grubconf=$bootdir/grub.cfg
backup=$grubconf.old
warn=yes
verbose=no

### If verbose print settings ###

case $verbose in yes|y) 
  echo ""
  echo "---== Settings ==---"
  echo ""
  echo -e "Boot Directory: \t\t $bootdir"
  echo -e "Temporary File: \t\t $tempfile"
  echo -e "Grub.cfg Location: \t\t $grubconf"
  echo -e "Backup file location: \t\t $backup"
  echo -e "Warnings Enabled: \t\t $warn"
  echo -e "Verbose: \t\t\t $verbose"
  echo ""
  ;;
esac

### Make Backup ###

case $verbose in yes|y) 
  echo "---== Writting file ==---"
  echo ""
  echo "Making Backup ..."
  ;;
esac

gksudo cp $grubconf $backup
gksudo chmod 666 $backup

### Add file header ###

case $verbose in yes|y) 
  echo "Write file header ..."
  ;;
esac

cat $grubconf | sed '/END \/etc\/grub.d\/.*_debian_theme/ q' > $tempfile
echo "" >> $tempfile 

### Add windows 7 Option ###

case $verbose in yes|y) 
  echo "Write windows section ..."
  ;;
esac

cat $grubconf | grep os-prober | grep BEGIN >> $tempfile
cat $grubconf | sed -n '/Windows 7/,/}/ p' | sed 's/ (loader) (on \/dev\/sda1)//g' >> $tempfile
cat $grubconf | grep os-prober | grep END >> $tempfile
echo "" >> $tempfile 

### Add Ubuntu Option ###

case $verbose in yes|y) 
  echo "Write Ubuntu section ..."
  ;;
esac

cat $grubconf | sed -n '/BEGIN \/etc\/grub.d\/.*_linux /,/}/ p' | sed 's/, with Linux 2.6.*generic//g' >> $tempfile
cat $grubconf | grep -e "linux " | grep END >> $tempfile
echo "" >> $tempfile 

### Add file footer ###

case $verbose in yes|y) 
  echo "Write file footer ..."
  ;;
esac

cat $grubconf | awk '/custom/,0' >> $tempfile

### Warning & preview ###

case $warn in yes|y)

  ## Warning enabled ##

  case $verbose in yes|y) 
    echo ""
    echo "---== Preview file ==---"
    echo ""
    ;;
  esac

  leafpad $tempfile
  zenity --question --text "Does the grub.cfg file look ok?"

  if [ $? = 1 ]; then

    case $verbose in yes|y) 
      echo "Grub configure failed"
      echo "Exiting"
      echo ""
      zenity --warning --text "Grub configure failed!"
      ;;
    esac

    exit 1

  else

    case $verbose in yes|y)
      echo "Grub configure sucessfull"
      echo ""
      echo "---== Writing file ==---"
      echo "done"
      echo ""
      ;;
    esac
  
  gksudo chmod 666 $grubconf
  gksudo cp $tempfile $grubconf
  gksudo chmod 444 $grubconf
  echo "written"

  exit 0

  fi

  ;;
  *)

  ## Warning disabled ##

  case $verbose in yes|y)
    echo "Grub configure sucessfull"
    echo ""
    echo "---== Writing file ==---"
    echo "done"
    echo ""
    ;;
  esac
  
  gksudo chmod 666 $grubconf
  gksudo cp $tempfile $grubconf
  gksudo chmod 444 $grubconf
  echo "written"

  exit 0
  ;;
esac

exit 1

```

A script to re-write the /boot/grub/grub.cfg file so that it defaults to windows and it also removes all the other options such as memcheck and renames ubuntu... to ubuntu and windows...on /dev/sda to just windows 7. The script is based on the idea that you are using windows 7 and ubuntu and also leafpad editor so it's not very flexible but it has saved me lots and lots of time :).

---

### Post by Windows Nerd on 2010-09-24
> **conundrumx said:**
> This is actually a function built into my .profile:

```
extract () {
    if [ -f $1 ] ; then
        case $1 in
            *.tar.bz2)   tar xjf $1        ;;
            *.tar.gz)    tar xzf $1     ;;
            *.bz2)       bunzip2 $1       ;;
            *.rar)       unrar x $1     ;;
            *.gz)        gunzip $1     ;;
            *.tar)       tar xf $1        ;;
            *.tbz2)      tar xjf $1      ;;
            *.tgz)       tar xzf $1       ;;
            *.zip)       unzip $1     ;;
            *.Z)         uncompress $1  ;;
            *.7z)        7z x $1    ;;
            *)           echo "'$1' cannot be extracted this way." ;;
        esac
    else
        echo "'$1' is not a valid file."
    fi
}
```

Enjoy.

Thanks very much. I knew I had seen this script before but never thought to copy it :)

---

### Post by CharlesA on 2010-09-25
> **Windows Nerd said:**
> Thanks very much. I knew I had seen this script before but never thought to copy it :)
I saw that script on shell-fu: [http://www.shell-fu.org/lister.php?id=375](http://www.shell-fu.org/lister.php?id=375)

;)

---

### Post by ironic.demise on 2010-09-26
Simple simple idea for a website (I'm working out the kinks on the temporary variables and the backups... call it beta)
Take a HTML file, Split it into things that are universal for each page, headers, menus, contact info, layouts and throw it into a file seperate to unique stuff such as blogs or photos.

The shell script will compose the files meaning if you ever make a new blog... it's just a simple file with little code and if you ever change the site logo or name, it's a simple change to one file that's rolled out across every page at once.

although... the backing up fails and the #!/bin/bash will always completly void the script.



Here we go:
```

# Set-up
SOURCE=~/Documents/Source/
Target=~/Public/Web_server/
# Backups
cp -r ~/Documents/Backups/Website/9/ ~/Documents/Backups/Website/10/
cp -r ~/Documents/Backups/Website/8/ ~/Documents/Backups/Website/9/
cp -r ~/Documents/Backups/Website/7/ ~/Documents/Backups/Website/8/
cp -r ~/Documents/Backups/Website/6/ ~/Documents/Backups/Website/7/
cp -r ~/Documents/Backups/Website/5/ ~/Documents/Backups/Website/6/
cp -r ~/Documents/Backups/Website/4/ ~/Documents/Backups/Website/5/
cp -r ~/Documents/Backups/Website/3/ ~/Documents/Backups/Website/4/
cp -r ~/Documents/Backups/Website/2/ ~/Documents/Backups/Website/3/
cp -r ~/Documents/Backups/Website/1/ ~/Documents/Backups/Website/2/
cp -r ~/Documents/Source/ ~/Documents/Backups/Website/1/
# Compiling index.html 
cat ~/Documents/Source/html.txt > ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/head.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/body.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/universal.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/index.txt >> ~/Public/Web_server/unacquainted/index.html  
cat ~/Documents/Source/end.txt >> ~/Public/Web_server/unacquainted/index.html  
# Compiling downloads.html 
cat ~/Documents/Source/html.txt > ~/Public/Web_server/unacquainted/downloads.html  
cat ~/Documents/Source/head.txt >> ~/Public/Web_server/unacquainted/downloads.html  
cat ~/Documents/Source/body.txt >> ~/Public/Web_server/unacquainted/downloads.html  
cat ~/Documents/Source/universal.txt >> ~/Public/Web_server/unacquainted/downloads.html  
cat ~/Documents/Source/downloads.txt >> ~/Public/Web_server/unacquainted/downloads.html  
cat ~/Documents/Source/end.txt >> ~/Public/Web_server/unacquainted/downloads.html  
# Compiling gallery.html 
cat ~/Documents/Source/html.txt > ~/Public/Web_server/unacquainted/gallery.html  
cat ~/Documents/Source/head.txt >> ~/Public/Web_server/unacquainted/gallery.html  
cat ~/Documents/Source/body.txt >> ~/Public/Web_server/unacquainted/gallery.html  
cat ~/Documents/Source/universal.txt >> ~/Public/Web_server/unacquainted/gallery.html  
cat ~/Documents/Source/gallery.txt >> ~/Public/Web_server/unacquainted/gallery.html  
cat ~/Documents/Source/end.txt >> ~/Public/Web_server/unacquainted/gallery.html  
# Compiling photos.html  
cat ~/Documents/Source/html.txt > ~/Public/Web_server/unacquainted/photos.html  
cat ~/Documents/Source/head.txt >> ~/Public/Web_server/unacquainted/photos.html  
cat ~/Documents/Source/body.txt >> ~/Public/Web_server/unacquainted/photos.html  
cat ~/Documents/Source/universal.txt >> ~/Public/Web_server/unacquainted/photos.html  
cat ~/Documents/Source/photos.txt >> ~/Public/Web_server/unacquainted/photos.html  
cat ~/Documents/Source/end.txt >> ~/Public/Web_server/unacquainted/photos.html  
# Compiling holiday_photos.html
cat ~/Documents/Source/html.txt > ~/Public/Web_server/unacquainted/holiday_photos.html  
cat ~/Documents/Source/head.txt >> ~/Public/Web_server/unacquainted/holiday_photos.html  
cat ~/Documents/Source/body.txt >> ~/Public/Web_server/unacquainted/holiday_photos.html  
cat ~/Documents/Source/universal.txt >> ~/Public/Web_server/unacquainted/holiday_photos.html  
cat ~/Documents/Source/holiday_photos.txt >> ~/Public/Web_server/unacquainted/holiday_photos.html  
cat ~/Documents/Source/end.txt >> ~/Public/Web_server/unacquainted/holiday_photos.html
```

---

### Post by mobilediesel on 2010-09-26
> **ironic.demise said:**
> Simple simple idea for a website (I'm working out the kinks on the temporary variables and the backups... call it beta)
Take a HTML file, Split it into things that are universal for each page, headers, menus, contact info, layouts and throw it into a file seperate to unique stuff such as blogs or photos.

The shell script will compose the files meaning if you ever make a new blog... it's just a simple file with little code and if you ever change the site logo or name, it's a simple change to one file that's rolled out across every page at once.

although... the backing up fails and the #!/bin/bash will always completely void the script.



Here we go:


I had to simplify that a bit:
```
# Set-up
SOURCE=~/Documents/Source/
Target=~/Public/Web_server/
# Backups
cp -r ~/Documents/Backups/Website/{9,10}/
cp -r ~/Documents/Backups/Website/{8,9}/
cp -r ~/Documents/Backups/Website/{7,8}/
cp -r ~/Documents/Backups/Website/{6,7}/
cp -r ~/Documents/Backups/Website/{5,6}/
cp -r ~/Documents/Backups/Website/{4,5}/
cp -r ~/Documents/Backups/Website/{3,4}/
cp -r ~/Documents/Backups/Website/{2,3}/
cp -r ~/Documents/Backups/Website/{1,2}/
cp -r ~/Documents/{Source,Backups/Website/1}/
# Compiling index.html 
cat ${SOURCE}/{html,head,body,universal,index,end}.txt > ${Target}/unacquainted/index.html  
# Compiling downloads.html 
cat ${SOURCE}/{html,head,body,universal,downloads,end}.txt > ${Target}/unacquainted/downloads.html
# Compiling gallery.html 
cat ${SOURCE}/{html,head,body,universal,gallery,end}.txt > ${Target}/unacquainted/gallery.html
# Compiling photos.html  
cat ${SOURCE}/{html,head,body,universal,photos,end}.txt > ${Target}/unacquainted/photos.html
# Compiling holiday_photos.html
cat ${SOURCE}/{html,head,body,universal,holiday_photos,end}.txt > ${Target}/unacquainted/holiday_photos.html

```

It just does the same thing with less code. It lets Bash do the repetitive parts.

If you're running that via cron, you might have to replace the **~** with the actual path names, eg. replace **~** with **/home/user**.

---

### Post by ironic.demise on 2010-09-28
> **mobilediesel said:**
> I had to simplify that a bit:
```
# Set-up
SOURCE=~/Documents/Source/
Target=~/Public/Web_server/
# Backups
cp -r ~/Documents/Backups/Website/{9,10}/
cp -r ~/Documents/Backups/Website/{8,9}/
cp -r ~/Documents/Backups/Website/{7,8}/
cp -r ~/Documents/Backups/Website/{6,7}/
cp -r ~/Documents/Backups/Website/{5,6}/
cp -r ~/Documents/Backups/Website/{4,5}/
cp -r ~/Documents/Backups/Website/{3,4}/
cp -r ~/Documents/Backups/Website/{2,3}/
cp -r ~/Documents/Backups/Website/{1,2}/
cp -r ~/Documents/{Source,Backups/Website/1}/
# Compiling index.html 
cat ${SOURCE}/{html,head,body,universal,index,end}.txt > ${Target}/unacquainted/index.html  
# Compiling downloads.html 
cat ${SOURCE}/{html,head,body,universal,downloads,end}.txt > ${Target}/unacquainted/downloads.html
# Compiling gallery.html 
cat ${SOURCE}/{html,head,body,universal,gallery,end}.txt > ${Target}/unacquainted/gallery.html
# Compiling photos.html  
cat ${SOURCE}/{html,head,body,universal,photos,end}.txt > ${Target}/unacquainted/photos.html
# Compiling holiday_photos.html
cat ${SOURCE}/{html,head,body,universal,holiday_photos,end}.txt > ${Target}/unacquainted/holiday_photos.html

```

It just does the same thing with less code. It lets Bash do the repetitive parts.

If you're running that via cron, you might have to replace the **~** with the actual path names, eg. replace **~** with **/home/user**.
Well, I'll be!
That's great!

I hate to bother but I'd really appreciate a hand.
I've recently fine-tuned that a bit myself to include some things I would use and to make it more reliable.

Before I checked here of course... do you mind seeing [http://ubuntuforums.org/showthread.php?t=1584173](http://ubuntuforums.org/showthread.php?t=1584173) and giving criticisms?

I'm sorry I'm not very good at programming... I've yet to learn any other programming languages and I'm suffering a LOT on syntax and organization... I have to say even II know that everything I do is still very very messy and... kruft

---

### Post by Windows Nerd on 2010-09-29
> **CharlesA said:**
> I saw that script on shell-fu: [http://www.shell-fu.org/lister.php?id=375](http://www.shell-fu.org/lister.php?id=375)

;)

Thanks for posting the site. One of the persons commenting on there posted an over- the top shell script that seems to have more flexebility:
```
my overly over the top version .. which lets you do 

extract foo.bar | foo.* | *.bar | *  

and provide extract directories with the -p option. i.e.

extract *.tgz -p ./tars

#extract - extract most common compression types
# extract <files>  -p <to path> - to path is optional
# call with foo.bar or foo.* or *.bar or *  
function extract () {  
   local args=("$@")
   local rootpath=$(pwd)
   local cn=0
   local files=()
   for  f in "$@"; do
       case $f in
           "-p")  # path option 
               rootpath=${args[((cn+1))]}  ;
               # echo 'rootpath ->'  "$rootpath" 
               if [[ ! -d "$rootpath/" ]] ; then 
                   echo "$rootpath does not exit, create it ? [yY/nN]" ;
                   read a;
                   if [[ $a == "Y" || $a == "y" ]] ; then
                       mkdir $rootpath;
                   else
                       return 0
                   fi;
               fi 
               ;;
           *)  # default 
               if [[  -f $f  ]]; then
                   # add the file 
                   files=("${files[@]}" "\"$f\"");         
               fi                            
               ;;
       esac
       ((cn++))
   done
   # extract the files 
   for i in $(seq 0 $((${#files[@]} - 1))); do
       # get the filenames
       local f=`echo ${files[$i]} | sed -e 's/"//g'`        
       local fn=`echo ${files[$i]} | sed -e 's/"//g' | sed 's/.*\///'`        
       local local sfx=${f##*.}        
       local drn=$rootpath/`echo $fn | sed -e 's/.'$sfx'//g' | sed -e 's/"//g'`
       local cmd=''
       #drn=$rootpath/$drn
       echo "Extracting -> $f "
       echo "Copy       -> $drn/$fn .."
       # check if dir exists 
       [ -d "$drn" ] || mkdir "$drn"        
       cp -p "$f" "$drn/$fn"
       # extract it 
       pushd "$drn" 1>/dev/null
       echo "Extract    -> $drn/$fn .."
       case ".$sfx" in
           *.t@(gz|lz|xz|)) cmd='tar xzf' ;;
           *.t@(b@(2|z?(2)))) cmd='tar xjf' ;;
           *.t@(a@(z|r?(.@(Z|bz?(2)|gz|lzma|xz))))) cmd='tar xvf' ;;
           *.7z)  cmd='7z x'       ;;
           *.Z)   cmd='uncompress' ;;
           *.bz2) cmd='bunzip2'    ;;
           *.exe) cmd='cabextract' ;;
           *.gz)  cmd='gunzip'     ;;
           *.rar) cmd='unrar x'    ;;
           *.xz)  cmd='unxz'       ;;
           *.zip) cmd='unzip'      ;;            
           *)        echo "'$fn' cannot be extracted via extract()" ;;
       esac        
       #echo "cmd=$cmd"
       [[ $cmd ]] && command $cmd "$fn"
       echo "Remove     -> $drn/$fn .."
       rm -f "$fn"
       popd 1>/dev/null
       echo "  "            
   done
}
```

Thought I'd share it.

Scott

---

### Post by CharlesA on 2010-09-29
Holy crap. I don't even think I can break that one down.

---

### Post by mamamia88 on 2010-09-29
> #! /bin/bash
sudo apt-get update
sudo apt-get upgrade

my only annoyance with ubuntu was loading a gui update manager this makes upgrading the system easy.

---

### Post by cgroza on 2010-09-29
> **mamamia88 said:**
> my only annoyance with ubuntu was loading a gui update manager this makes upgrading the system easy.

Something similar in python but better: 

```
#!/usr/bin/env python
#This script works in a unix bash terminal only. Runing it in IDLE won't execute the apt-get commands.

#import section.
import os
import time

#Definition section.

def notify():
    os.system("notify-send 'Operation Finished'")

def sel():
    sel1=raw_input('Enter:\n1 to Install.\n2 to Remove.\n3 to Upgrade.\n4 to Update.\n5 to Clean.\nq to Quit.\n1/2/3/4/5/q/: ')
    if sel1 == '1':
         install()

    elif sel1 == '2':
         remove()

    elif sel1 == 'q':
         quit

    elif sel1 == '3':
        upgrade()

    elif sel1 == '4':
        update()

    elif sel1 == '5':
        maintain()
             
    else:
         print('Invalid command')
         time.sleep(3)
         os.system('clear')
         sel()



        
def install():
    os.system('clear')
    i = raw_input('Enter app name from repository: ')
    cmd="sudo apt-get install " + i
    os.system(cmd)
    notify()
    raw_input('Press enter to continue.')
    os.system("clear")
    sel()
    
 
            
def remove():
    os.system('clear')
    r = raw_input("Enter app name to remove: ")
    cmd2="sudo apt-get remove "+r
    os.system(cmd2)
    notify()
    raw_input('Press <enter> to continue.')
    os.system("clear")
    sel()


def upgrade():
    os.system('clear')
    raw_input('Press <enter> to upgrade. This will update the repositories also.')
    cmd3="sudo apt-get update && sudo apt-get upgrade"
    os.system(cmd3)
    notify()
    raw_input('Press enter to continue.')
    os.system("clear")
    sel()


def update():
    os.system('clear')
    raw_input("Press <enter> to update.")
    cmd4="sudo apt-get update"
    os.system("sudo apt-get update")
    notify()
    raw_input("Press <enter> to continue.")
    os.system("clear")
    sel()
    

def maintain():
    os.system('clear')
    print('This function deletes the apt chache and removes unused dependencies')
    m = raw_input('Do you wish to continue?n/y: ')


    if m == 'n':
        time.sleep(1)
        os.system('clear')
        sel()

    if m == 'y': pass

    else :
        print('Invalid Command')
        time.sleep(3)
        os.system('clear')
        maintain()


    cmd5=('sudo apt-get clean && sudo apt-get autoremove && sudo apt-get autoclean ')
    os.system(cmd5)
    notify()
    raw_input('Press <eneter> to continue.')
    os.system('clear')
    sel()

    

print('Welcome to my app manager.')

# Definition calling section.

sel()

```

It allows to call apt-get without opening a terminal and do all that typing.

---

### Post by mamamia88 on 2010-09-29
cool little script.  what's the difference between upgrade and update?  I honestly don't mind typing my passord and hitting y every time on my script but yours seems pretty cool as well.  also i get the output "sh: notify-send: not found" at the end.  what could that mean?

---

### Post by cgroza on 2010-09-29
> **mamamia88 said:**
> cool little script.  what's the difference between upgrade and update?  I honestly don't mind typing my passord and hitting y every time on my script but yours seems pretty cool as well.  also i get the output "sh: notify-send: not found" at the end.  what could that mean?

Update just refreshes the repository. Upgrade actually updates the packages. And with that error it means you dont have libnotify installed. That should make a message pop up when the operation is finished.

---

### Post by CharlesA on 2010-09-29
update checks for updated packages, upgrade downloads and installs them.

---

### Post by mamamia88 on 2010-09-29
> **cgroza said:**
> Update just refreshes the repository. Upgrade actually updates the packages.

ah cool thanks

---

### Post by cgroza on 2010-09-29
I don't know what version of Ubuntu you are using but installing this package should solve that error:  libnotify-bin[B]
[]("http://ubuntuforums.org/showthread.php?t=594067")[/B]

---

