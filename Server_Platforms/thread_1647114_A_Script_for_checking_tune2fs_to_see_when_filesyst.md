---
title: "A Script for checking tune2fs to see when filesystems were last fsck'ed."
date: 2010-12-16
forum: Server Platforms
---

### Post by hotdoog on 2010-12-16
Hi, I made this script some time ago and have found it quite useful. I hope this is useful to somebody. It has been useful and reliable for me. If you have any problems with it post them and we'll try to make it better.

What it does is run tune2fs -l on all your filesystems then lists the information on when the filesystem was last fsck'ed. This can be useful if you have many filesystems and want to know if maintenance on them is required. I've attached the file which is working for me on my system and also I pasted the script here as a preview.

USAGE:
You must edit line 17 to specify where you want the output text file to be put. You should also edit line 22 with your user name. This script must be run as sudo or root. You must use bash to run it, sh won't work. 

Share and share alike!

```
#!/bin/bash
#
#made by rusl oct 28 2008 GPL
#This is for a system with many mounted filesystems. I made this
#script to quickly get all relevant filesystems info to determine
#if fsck maintenance is a priority.
#email spam-AT-bikesexual-DOT-org with feedback

#can be edited
#this is the selective list of information fields from a TUNE2FS -L output
want='(name|checked|UUID|state|Mount|Maximum|interval|super[-]?block)'
#to display entire tune2fs output for each then uncomment this line
#want=\:

#can be edited
#location for tune2fs summary output file
o=/home/rusl/Desktop/fscked.last

#your user name
#semi-optional (comment out last bit if you want to ignore this)
#so that this file is owned by you rather that root
u=rusl

#number of mounted HDD filesystems (excluding RAM, tmpfs etc)
num=`df |grep dev\/|grep -v devshm | sort | wc -l`

#function to arrange DF filesystems info for tune2fs to read
#simply put a DF output filter.
pro() {
df |grep dev\/| sort | grep -vn devshm | sed -e 's/:/ /'
}

#output file title
echo "FILE SYSTEMS FSCK RELATED INFO --- "`date` > $o
echo "by script: fscked.last.tune2fs.listing.script.sh" >> $o
echo " " >> $o

#repetitive output to file
for ((i=1;i<($num+1);i+=1)) ; do
	echo " "  >> $o ;
	echo "-----filesystem:"$i"-----"  >> $o ;
	pro | grep -w ^$i | awk '{print $7}' >> $o ;
	file -sL `pro | grep -w ^$i | awk '{print $7}'` >> $o ;
	pro | grep -w ^$i | awk '{print $2}'  >> $o ;
	file -sL `pro | grep -w ^$i | awk '{print $2}'` >> $o ;
	sudo tune2fs -l `pro | grep -w ^$i | awk '{print $2}'` 2>&1 | egrep $want >> $o
	done
# I've added the 2>&1 as per http://tldp.org/LDP/abs/html/io-redirection.html plus the string "super[-]?block" to the egrep $want so that stderr errors will show up in the file and not in a terminal somewhere else. It seems to work. I think it won't show any error messages that don't inlude the string superblock or super-block. Not ideal.

#RAID info as a bonus, can be disable by commenting out
#not related to rest of script
echo " " >> $o
echo " " >> $o
echo "RAID INFO --- "`date` >> $o
echo " " >> $o
cat /proc/mdstat  >> $o
#semi-optional (comment out if you want to ignore this)
sudo chown $u $o
sudo chgrp $u $o

```

---

