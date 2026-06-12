---
title: "humax pvr9200t file transfer ubuntu 7.10"
date: 2008-01-12
forum: Tutorials
---

### Post by jimbo54321 on 2008-01-12
i have struggled with this problem for months now. it has been the only reason i ever boot to windows, but finally after gathering data and advice from various sources i  got it working under ubuntu 7.10. see attachment

This is how i did it:

1. install libqt4-dev, libusb-dev and build-essential in synaptic package manager
2. download and extract source code from [http://www.andrewdsmith.plus.com/hummy/](http://www.andrewdsmith.plus.com/hummy/)
3. Open terminal  and navigate to the extracted humax directory.
4. Run "qmake-qt4 humaxGui.pro" ( ubuntu 7.10)
5. Run "make".
6. Run sudo /wherever the humax folder is/humax/humaxGui to open software as root
7. Connect USB cable between PC and PVR.
8. click connect on software
9. hopefully your all done

I am by no means an expert at linux or the command shell. I have spent months trawling various forums to get this working. all i have done is listed the steps i took. if these do not work for you then sorry i probably cannot help,

---

### Post by laidback on 2008-01-13
Wow well done. I've just been lent a Humax box and reading through other forums on the Humax/Linux issue I came to the conclusion that this wasn't possible. Might give this a go. Thanks very much.

---

### Post by uggeli on 2008-02-16
I got humaxgui connected to my humax pvr9200t, when using sudo as mentioned in first message. But What I don't see, is any saved programs on my humax box. So do you have any idea what could cause this, and what would be the solution?

PS. What would be best solution to try to get humaxgui working when using as user, not with sudo?

---

### Post by jimbo54321 on 2008-02-17
are you definatly viewing D2: drive on humax D1: shows music etc and is usually blank.

---

### Post by uggeli on 2008-02-17
I have tried both, first it was D2 by default and it seemed to be empty. Tested it again and yeah, D2 seems as empty. It connect ok though and shows Serial number etc. of the humax box.

---

### Post by nickswift on 2008-03-23
I have the same problem with the client not correctly parsing data from the Hummy.

Turning the debugging on I can see data relating to recorded programmes being received by the client but its not parsing them correctly.

I have a TS model - don't know if a firmware change may have broken something. Device information seems to mostly work although the recording status is intermittent.

Nick

---

### Post by KenHagan on 2008-11-22
> **jimbo54321 said:**
> i have struggled with this problem for months now. it has been the only reason i ever boot to windows, but finally after gathering data and advice from various sources i  got it working under ubuntu 7.10. see attachment

This is how i did it: (snip)

I struggled for about half an hour and found your post, which worked. (on Hardy, so it is still working) Thanks!

---

### Post by s6pnj on 2008-11-30
Hi, I am trying this on Ibex (8.10) and can get as far as loading the software and running the humaxGui by clicking on the icon in a File Browser window.  When I click the 'connect' icon, it tells me that it 'Failed to connect to the device'.  I'm unable to run the program from the terminal with sudo as it tells me to in the first post.  Does anyone have any ideas please?

---

### Post by s6pnj on 2008-11-30
Well I've now got the program running so all is well there, but I can't see any file on the Humax now, similar to the post above.  I can connect and change between D1 and D2 but see no files.  In the status window I get:


Connected.

HUMAX Co., Ltd.            

HUMAX PVR Mass Storage (V1.0)

Serial No :534A1E013031

Any clues?

---

### Post by jimbo54321 on 2008-12-02
the link to sourcre code appears to be wrong on web site above the link is [http://www.andrewdsmith.plus.com/hummy/humaxGui%20V1.00.src.tar.gz](http://www.andrewdsmith.plus.com/hummy/humaxGui%20V1.00.src.tar.gz)
for stable v1.00

---

### Post by Slartibartfast_zzr on 2009-01-01
Hello, has anyone who was having the problems seeing the file lists on the humax cured their problem. I have the same issue and also only need Windows for this function currently.

Thanks,

Keith

---

### Post by BIS on 2009-01-31
Hi,

Dunno if this helps - I had the same issue, and this is what solved it for me.

Get the latest snapshot (beta), at this time of writing (Jan.31 2009) the one I used was the snapshot located here (111K): [http://www.andrewdsmith.plus.com/hummy/humaxGui%20snapshot.13122006.tar.gz](http://www.andrewdsmith.plus.com/hummy/humaxGui%20snapshot.13122006.tar.gz)

(patience, page loads slowly)

Download that one, extract it and:

- sudo qmake-qt4 humaxGui.pro (note the qt4 - do not just run qmake)

- sudo make

- Connect USB cable

Browse to the folder where humaxGui is located

- gksudo (not sudo!!) ./humaxGui (do not forget the ./)

Connect and you should see the folder contents of D2.

Hope this helps.

---

### Post by theinnercityhippy on 2009-03-02
Hello,

Is anyone using this program interested in helping to maintain it get the Linux functionality right?

I have emailed the developer listed in the AUTHOR.txt file but don't know if it is still an active link as development seems to have stopped back in 2006. I've found a few bugs (one that created an 18GB plain text file in my home folder) and was wondering if anyone had the necessary C++ skills to help me to iron them out then release it back as a linux specific fork away from the windows version (as that seems to work ok). It is released under the GPL so it is OK to do this.

Unfortunately, though I possess some skills and a little time, I'm not sure I have enough of either to do this alone,

Any takers?

(ps -- this might sway it, have had very fast transfers (25mins for feature film) on several occasions whilst testing and recovery mode working - all down to playing with the combinations of block sizes)

(pps -- for those who can't connect successfully, I have found this to be the order in which you plug things in/switch them on for best results.)
Initially have Humax unit switched off (I tend to use the switch at the back for extra sureness but this isn't necessary)
 
1 - Boot your computer
2 - Start Software as root
3 - Plug in Humax
4 - Turn Humax on
5 - optional - press menu button on controller (seems to freak out more if it's trying to display a program at the same time as connecting)
6 - Press the connect button in HumaxGUI
7 - List of programs should now appear in D2. Remember only to do one at a time as the temporary files needed by linux to map the drive will not be cleaned up otherwise and will confuse the poor thing!

---

### Post by Slartibartfast_zzr on 2009-03-10
Hi Bis,

Thanks for the info. This  helped me to get the app. running. However, it seems to increase the bad sectors transfered as it goes on, such that it can transfer small files ok, but films are impossible. I am trying to play around with different block sizes etc.. to see if that helps. If anyone can help that would be great.

Thanks,

Slartibartfast

---

### Post by Slartibartfast_zzr on 2009-04-07
Found the problem!:p Found that I could not download reliably under Linux or Windows, with any type of program. A bit of googling found that with the latest firmware (vs. 21) this does happen unless you disable the tuners. This can be done either by 1.removing the aerial, 2. putting the box into the manual search menu page, or 3. pressing the games button. Hey Presto! fully working and reliable downloads. Just for anyones info.

Thanks for the previous help,

Slatibartfast

---

### Post by nigmac on 2009-06-20
Does anyone have this working under Jaunty? I'm new to Ubuntu and I'd like to get this working so I can do away with my windows partition. I can get the gui working and it says connected. When I turn logging on, (from what I can decipher) it sees the recordings on my Humax but the GUi shows nothing. Anyone got any ideas?

---

### Post by tonytiger on 2009-12-29
Hi,
I tried humaxGui without success. It doesn't show any files on humax. Tried with sudo and gksudo.

Is there any progress with this? Or is there a way to just mount humax without any GUI? I think using console is in any case much easier.

Thanks!

-Tony

---

### Post by refdoc on 2013-01-27
For what it is worth, the advice by the OP works still just fine on Ubuntu 12.10

---

