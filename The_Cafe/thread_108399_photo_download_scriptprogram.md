---
title: "photo download script/program"
date: 2005-12-26
forum: The Cafe
---

### Post by jocke1s on 2005-12-26
Hi all,

In XP I used a software called DOWNLOADER PRO from [www.breezesys.com](www.breezesys.com).
It is a nice program to download my digital camera photos, rename them
and put them in folders on the fly based on exif data. Fast as hell and very easy to use.

Now:
I am looking for a replacement on ubuntu to download from my usb reader. So no actual camera support is needed.
* Have to be able to download and rename. Example IMG123.jpg will be renamed to 20051226_IMG123_01.jpg and put in folder /photo/2005/2005_12/2005_12_26
* Need to be fast

I actually don't think it exist anything useful in linux so I am prepared to write my own script using some exif cabable utility etc..

Anyone got any ideas for software or script?

Best regards
Joakim

---

### Post by anil_robo on 2005-12-26
WHen I plug in my digicam in Ubuntu, it automatically detects it, mounts it, shows preview of all photos, and asks me where should I keep it. It also gives me an option of which folder, and if I want to rename the files. I don't know what package it is, but it's included with Ubuntu by default. Try it.

---

### Post by jocke1s on 2005-12-26
I have tried many of the common programs. The options in the default ubuntu ones are not sufficient. And its SLOOOOOW.

I need to be able to download up to 4 Gb and it needs to automatically rename and create subfolders based on exif data on the run without user intervention.

/Joakim

---

### Post by xmastree on 2005-12-26
I think that writing your own script is the only answer. Programs are available for reading exif tags if you search synaptic for exif you'll see them.

exif, for example:
```
$ exif -t DateTime dsc_0844.jpg
EXIF entry 'Date and Time' (0x132, 'Date and Time') exists in IFD '0':
Tag: 0x132 ('DateTime')
  Format: 2 ('Ascii')
  Components: 20
  Size: 20
  Value: 2005:12:22 21:10:57
$

```

Then it's simply a matter of reading the date from the exif (assuming it's that date rather than the system date you want), create a folder for it and copy the filename to it with its new name.

Yeah, simple really. :rolleyes: 

Good luck, and remember to post it here so we can all use it. :)

---

### Post by dcraven on 2005-12-26
I'd probably write this in Python using PIL. I can't imagine it would be too difficult.

HTH,
~djc

---

### Post by jocke1s on 2005-12-26
Ok I spent an hour to write this VERY ROUGH bash script. It uses jhead for exif data.

As it is written it takes all pictures ending with JPG, rename them and moves them to folders based on when the picture was taken. If no exif data exists you are prompted for year/mont/day.

If by chance anyone uses this and has the energy to add some functionality or error checks etc please let me know :)

Regards
Joakim

ps I have tried it one time on 1Gb of files and It worked perfectly.

-----------------------------------------------------------
#!/bin/bash
#
#
#
echo "This script will rename and move all JPG files in current folder. Continue Y/N?"
read -e answer
if [ $answer == "Y" ];
then
folder="/home/joakim/PICTURES"
for files in *.JPG
do
year=`jhead $files | grep "Date/Time    :"  2>/dev/null | awk '{print substr($0,16)}' | awk '{print substr($0,1,4)}'`
  if test -z "$year"
    then
        echo "$files"
    echo "Exif info is missing. Please add date information: "
    echo -n "Enter year: "
    read -e year
    echo "Enter month: "
    read -e month
    echo "Enter day: "
    read -e day
    basename=`echo ${files%\.JPG}`
    model="unknown"
    else
    year=`jhead $files | grep "Date/Time    :"  | awk '{print substr($0,16)}' | awk '{print substr($0,1,4)}'`
    month=`jhead $files | grep "Date/Time    :"  | awk '{print substr($0,16)}' | awk '{print substr($0,6,2)}'`
    day=`jhead $files | grep "Date/Time    :"  | awk '{print substr($0,16)}' | awk '{print substr($0,9,2)}'`
    basename=`echo ${files%\.JPG}`
    model=`jhead $files | grep "Camera model :"  | awk '{print substr($0,16)}' | awk '{print $3}'`
    fi
  filename=$basename"_"$year$month$day"_"$model"_01.jpg"
  if test -a $filename
    then
    echo "File $files will be changed to $filename which allready exists..."
    exit
  fi
mkdir $folder"/"$year 2>/dev/null
mkdir $folder"/"$year"/"$month 2>/dev/null
mkdir $folder"/"$year"/"$month"/"$day 2>/dev/null
mv $files $folder"/"$year"/"$month"/"$day"/"$filename
done
else
echo "bye"
fi
------------------------------------------------------------------

---

