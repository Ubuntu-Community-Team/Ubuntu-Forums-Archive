---
title: "should I just format and reinstall Windows??"
date: 2007-04-05
forum: The Cafe
---

### Post by billdotson on 2007-04-05
I formatted and reinstalled Windows XP Professional SP2 just about two days ago.  I had formatted and installed Windows with the intention of using a ghost program to backup my Windows install after I had installed all of my games, drivers and other apps.  I have used PartImage to restore once or twice to see if it would work and the second time I got a bad block error when trying to restore.  Should I reformat and start over again and just use Device Image to backup my install?  If I run chkdsk then that should show me if there are any errors shouldn't it?  And if chkdsk returns no errors I should be fine right?  I do have all of the (Windows) updates installed so that I could fix the Internet explorer script error thing.  I didn't install the WGA update, so I don't know if installing those updates was bad or not..

BTW, w/ Device Image can I back up a partition instead of the entire HDD?  Like if I have a 170GB partition can I just copy the /dev/sda that that partition is or do I have to backup the entire 250GB HDD?  

Also, if I want to get a fully clean XP install to backup should I install the Windows automatic updates (with the exception of the WGA update)?  Or should I not install any of the updates and install all the drivers needed and all my apps that I know don't have any bugs?  

So I would install:
all my PC games
firefox and thunderbird
7-zip archive manager
PowerCinema DVD player
Roxio Easy Media Creator 7
TVersity
ffdshow
GIMPshop
latest GTK 
Steam
python 2.5 and latest pygame libs
BCL easypdf printer driver (to make PDFs of documents, images)
Google Earth
Spybot Search and Destroy
AVG Free
Opera
Democracy Player
Adobe Reader 8.0

Since I have noticed some bugs w/ Gaim for instance I would not install it before making a backup device image.

So to use Device Image I guess I just need to install zsplit and uzsplit on Ubuntu and do it from there.  I don't want to split the image into 4.7GB sizes or anything like that.  I just want to have one big device image on my external HDD.

Thanks again.  Btw FOSS rocks!  I would be paying ~$70 for a ghost program otherwise.

---

### Post by DoctorMO on 2007-04-05
Oooh dunno, if it was ubuntu and not windows then I'd recommend an install with your home folders in another partition and perhaps your usr dir on yet another partition that would at least solve your ghosting palaver.

But I'm not a windows expert and this isn't a windows forum, *shrug* so I really dunno.

---

