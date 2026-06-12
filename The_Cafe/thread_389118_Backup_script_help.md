---
title: "Backup script help"
date: 2007-03-20
forum: The Cafe
---

### Post by PatrickMay16 on 2007-03-20
Hey guys.

I recently wrote a really simple script to automate my weekly backup process. However, since I don't know bash very well at all, it isn't a very good script. 

if anyone can help me improve it, I'd be very grateful.

Here is the script as it is now:
```

echo "beginning"
export NUTLOADER=`date +%a%d%b%Y`
cd ~/
mkdir ~/Desktop/autobackup-$NUTLOADER

####

echo "making texts backup" 
cd ~/
tar cvf texts.tar texts/
rar a texts.rar texts.tar
rm texts.tar
mv texts.rar ~/Desktop/autobackup-$NUTLOADER

####

echo "making webpages backup"
cd ~/
tar cvf webpagesbackup.tar Webpages
rar a webpagesbackup.rar webpagesbackup.tar
rm webpagesbackup.tar
mv webpagesbackup.rar ~/Desktop/autobackup-$NUTLOADER

####

echo "making zsnes backup"
cd ~/.zsnes/
tar cvf zsnesbackup.tar *.zs* *.sp* *.srm *.cfg
7z a zsnesbackup.7z zsnesbackup.tar 
rm zsnesbackup.tar
mv zsnesbackup.7z ~/Desktop/autobackup-$NUTLOADER

####

echo "making epsxe savestate backup"
cd ~/snes9x/epsxe/
tar cvf epsxe_sstate_backup.tar sstates/
rar a epsxe_sstate_backup.rar epsxe_sstate_backup.tar
rm epsxe_sstate_backup.tar
mv epsxe_sstate_backup.rar ~/Desktop/autobackup-$NUTLOADER

####

echo "making MIDI music backup"
echo "midifiles part"
cd ~/midifiles/
tar cvf ~/midifiles.tar *.mid *.MID *.midi *.MIDI penismusic
echo "othermidi part"
cd ~/midifiles/othermidi/
tar cvf ~/othermidi.tar *.mid *.MID *.midi *.MIDI
echo "complete part"
cd ~/
7z a midistuff_backup.7z midifiles.tar othermidi.tar rosegardenfiles/
rm midifiles.tar othermidi.tar 
mv midistuff_backup.7z ~/Desktop/autobackup-$NUTLOADER

####

echo "done, check if everything worked"

```

So, what could be improved? Any suggestions?

---

