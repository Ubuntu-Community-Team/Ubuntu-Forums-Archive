---
title: "Music Duplicate Finder (I wrote this and I am still working on it)"
date: 2009-09-25
forum: The Cafe
---

### Post by altech6983 on 2009-09-25
Okay this is a preliminary script that works and is to be considered alpha stage. Right now all it can do is match exact matches in title, artist, bitrate (+ or - some percent), and length (plus or minus some percent) on mp3's (I know not all that important). I know y'all wanted this script so I am working on it, I am a little slow but I wanted to post something so you would know that I am indeed working on it. I did a total rewrite from what I had to make it more modularized so that I could expand it easier. 

HERE COMES THE IMPORTANT PART!!!!
THIS IS TO BE CONSIDERED ALPHA STAGE AND IT IS POTENTIALLY DANGEROUS TO YOUR FILES. THIS SCRIPT HAS THE ABILITY TO ERASE ANY FILE THAT BELONGS TO THE OWNER WHO RAN THE SCRIPT. I HAVE DONE SOME TESTING BUT IT WAS VERY PRELIMINARY, IF YOU AREN'T GREAT WITH COMPUTERS YOU SHOULD NOT TRY THIS SCRIPT. 

IF YOU DO TRY THIS SCRIPT PLEASE MAKE SURE YOU HAVE A BACKUP OF THE FOLDER YOU ARE RUNNING IT ON. 

OH and I AM NOT RESPONABLE FOR ANY DAMAGES THAT MAY OCCUR TO YOUR COMPUTER OR OTHER HARDWARE BECAUSE OF MY SCRIPT, USE AT YOUR OWN RISK.

Now that that is done, to run the script, copy it to a file and name it something.py, then execute it as a python script in the terminal (if you do not know how to run the script, please don't ask, you probably don't understand or know the risk that this script poses if it should malfunction, I will give full instructions when it is in a safer stage).  

It will put up a prompt asking for the path to the music folder, it is not recursive as of right now so they have to be in one folder. THIS IS VERY IMPORT (I haven't figured out a way to make it not matter), when you enter the path it MUST BE ABSOLUTE and it MUST END WITH A FORWARD SLASH. Ex. /home/altech6983/music/mp3/
If you have a space in the path then you will need to use quotes, I haven't tried it with quotes but it should work.

It should run then and remove the files that are either a) when the bitrates are close (<1000) it removes the one with the shortest length or b) or the one with the lowest bitrate.

Here is a quick overview of what it can and can't do.

It can:
-------
Remove files based on exact matches with title and artist (based on the worst quality one)
Filter out files so that only mp3's are taken in, so you do not have to worry about filtering it out for the script.

It can not:
-----------
Remove files based on close matches
Be recursive, all files must reside inside one folder with no deeper levels
Have a non-absolute path given to it
Figure out that l33t is equal to leet (same as rule one)
Do other files that are not mp3
Probably a lot of other things that you want it to do.

If you encounter any errors post them so that I can figure them out.
Also, everything on the can not list I plan to add to it but list some features that you would like to see in it, I will make a list and put it on the first page.

Requirements
------------
You must have mutagen for python installed (it can be done through synaptic)
And of course python

```
'''
Created on Sep 10, 2009

@author: coldfission(=altech6983)
'''
import os, mutagen, math
from mutagen.easyid3 import EasyID3

def info(filelist, info):
    temp = EasyID3(filelist)
    return temp[info]
def length(filelist):
    return mutagen.File(filelist).info.length
def bitrate(filelist):
    return mutagen.File(filelist).info.bitrate

print "Please input the directory you would like to scan for mp3 duplicates:"
basepath = raw_input()
os.chdir(basepath)

rawfilename = os.listdir('./') #Creates a variable containing all files in current directory

i = -1
while i < (len(rawfilename)-1):
    i = i + 1
    if rawfilename[i].endswith(".mp3"): #Makes sure that what it takes in is a mp3 file
        pass
    else:
        rawfilename.pop(i)
        i = i - 1
        
filelist = []
titlelist = []
artistlist = []
lengthlist = []
bitratelist = []
filelist.append(rawfilename[0])
titlelist.append(info(rawfilename[0], "title"))
artistlist.append(info(rawfilename[0], "artist"))
lengthlist.append(length(rawfilename[0]))
bitratelist.append(bitrate(rawfilename[0]))

i=0
while i < (len(rawfilename)-1):
    i = i + 1
    if info(rawfilename[i], "title") in titlelist: #Checks for title match
        indexL = titlelist.index(info(rawfilename[i], "title"))
        indexR = i
        if artistlist[indexL] == info(rawfilename[indexR], "artist"): #If there was a title match, checks for artist match
            if ((round(lengthlist[indexL])-5) <= round(length(rawfilename[indexR]))) and ((round(lengthlist[indexL])+5) >= round(length(rawfilename[indexR]))):
                if math.fabs(bitrate(rawfilename[indexR]) - bitratelist[indexL]) < 1000:
                    if lengthlist[indexL] >= length(rawfilename[indexR]):
                        #Delete rawfilename[indexR] from the rawfilename list and from the hard drive
                        path = basepath + rawfilename[indexR]
                        #os.remove(path)
                        rawfilename.pop(indexR)
                        i = i - 1
                    elif lengthlist[indexL] < length(rawfilename[indexR]):
                        #Delete filelist[indexL] from the filelist list and from the hard drive
                        path = basepath + filelist[indexL]
                        #os.remove(path)
                        filelist.pop(indexL)
                elif math.fabs(bitrate(rawfilename[indexR]) - bitratelist[indexL]) >= 1000:
                    if bitratelist[indexL] >= bitrate(rawfilename[indexR]):
                        #Delete rawfilename[indexR] from the rawfilename list and from the hard drive
                        path = basepath + rawfilename[indexR]
                        #os.remove(path)
                        rawfilename.pop(indexR)
                        i = i - 1
                    elif bitratelist[indexL] < bitrate(rawfilename[indexR]):
                        #Delete filelist[indexL] from the filelist list and from the hard drive
                        path = basepath + filelist[indexL]
                        #os.remove(path)
                        filelist.pop(indexL)
                        
    filelist.append(rawfilename[i]) #It was not in the list so append it
    titlelist.append(info(rawfilename[i], "title"))
    artistlist.append(info(rawfilename[i], "artist"))
    lengthlist.append(length(rawfilename[i]))
    bitratelist.append(bitrate(rawfilename[i]))
```

---

