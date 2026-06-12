---
title: "HOWTO: Install Lightscribe"
date: 2008-05-27
forum: Tutorials
---

### Post by GreatGariny on 2008-05-27
[SIZE="3"][SIZE="3"]This guide will help you install the base Lightscribe software and the 4L Disk Labeling software on a 32-bit or 64-bit Ubuntu install.

You can download the latest Lightscribe System Software from: [http://www.lightscribe.com/downloadsection/linux/](http://www.lightscribe.com/downloadsection/linux/)
and the latest LaCie 4L Labeling Software from: [http://www.lacie.com/us/support/drivers/driver.htm?id=10094](http://www.lacie.com/us/support/drivers/driver.htm?id=10094)
If you follow this guide to the letter, you will download software that is perhaps older than the versions above.  Updated versions may include support for more types of drives.  If you choose to go with the latest and untested versions, update the version numbers in the commands below.

[/SIZE][SIZE="3"]
Open a terminal.[/SIZE]
[SIZE="3"]_1. Create a temporary workspace in your home directory._[/SIZE]
[SIZE="2"]Note: You can delete this directory when you are finished installing the software.[/SIZE]
```
mkdir workspace
cd workspace
```
[SIZE="3"]_2. Download the 32-bit .deb files and an icon for Lightscribe_[/SIZE]
```
wget http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb
wget http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb
wget http://lawrencecomputing.dyn-o-saur.com/lightscribe/lightscribe.png
```
3. _Install the .deb files in the console with the force-architecture flag on 64-bit systems_
**[SIZE="2"]Important: Make sure to do these steps in this order (lightscribe then 4L)[/SIZE]**
[SIZE="2"]*For 32-bit:*[/SIZE]
```
sudo dpkg -i lightscribe-1.12.37.1-linux-2.6-intel.deb
sudo dpkg -i 4l_1.0-r6_i386.deb
```
[SIZE="2"]*For 64-bit:*[/SIZE]
```
sudo dpkg --force-architecture -i lightscribe-1.12.37.1-linux-2.6-intel.deb
sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb
```
[U]
4. Fix the missing liblightscribe.so.1 error[/U]
```
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig
```
[SIZE="2"]Note: The program should run now. You can test this by running:[/SIZE]
```
gksudo 4L-gui
```
_5. Copy the icon file into Ubuntu's shared icon directory_
```
sudo cp lightscribe.png /usr/share/pixmaps/4L-gui.png
```
_6. Create a shortcut to launch the 4L Disk Labeler as root_
[SIZE="2"]a. Right Click on the Ubuntu Menu Bar and choose Edit Menus.
b. In the left pane labeled menus choose either "Sound & Video" or "System Tools".
c. Then, click new item.
Enter this information into the window:[/SIZE]
```
Type: Application
Name: Lightscribe
Command: gksudo 4L-gui
Comment: Label a disc with Lightscribe
```
[SIZE="2"]Note: You can automatically generate an icon by leaving out the gksudo from "gksudo 4L-gui" in the command field. You must add gksudo to the command or the program will not be able to burn discs. Ubuntu will search for an icon in /usr/share/pixmaps with the same name as the command. Alternatively, you can click the spring icon and browse for the Lightscribe icon.[/SIZE]
[SIZE="2"]
Note: You can burn a label twice if it is not dark enough. Don't worry about the orientation of the disc, the drive will align it for you.[/SIZE][/SIZE]

---

### Post by james7dean on 2008-08-19
Hi,
   With reference to your guide.
When i enter the command 
 sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

i am informed that 
ln: target `/usr/lib32/' is not a directory: No such file or directory

 This is also true of
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

What can i do to remedy this ?

I continued with the rest of the install and can launch and use Lacie
However when i come to print my lightscribe drive is not recognised .
 
    Your help would be much appreciated
              Thanks ,
                         James

---

### Post by binbash on 2008-08-19
> **james7dean said:**
> Hi,
   With reference to your guide.
When i enter the command 
 sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

i am informed that 
ln: target `/usr/lib32/' is not a directory: No such file or directory

 This is also true of
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

What can i do to remedy this ?

I continued with the rest of the install and can launch and use Lacie
However when i come to print my lightscribe drive is not recognised .
 
    Your help would be much appreciated
              Thanks ,
                         James

This is also my problem.I can't link them

---

### Post by james7dean on 2008-08-27
> **binbash said:**
> This is also my problem.I can't link them

 Hi binbash,
             I managed to get my lightscribe working , apparently if you have Ubuntu 7.04 or newer, you need to install the old c library.

enter this code into the terminal :-
      sudo apt-get install libstdc++5
 
it will then ask for your password, enter it and the library is installed
 
  After doing this my lightscribe drive was finally recognised by Lacie lightscribe labeller

hope this works for u,
 
    James
:)

---

### Post by Crafty Kisses on 2008-09-05
Good information in here, nice tutorial.

---

### Post by phenest on 2008-11-10
Since installing Intrepid, the software no longer starts. Literally, nothing happens. Worked fine with Hardy.

---

### Post by Sumogrind on 2008-11-15
Thanks for the great tutorial GreatGariny, I've never installed an app this easily without synaptic before. 

The only thing I had to do different was to download the lightscribe .deb file from: 

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

Because when I entered:

```
wget http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb
```

I got:

```
HTTP request sent, awaiting response... 404 Not Found
```

And then of course I used:

```
sudo dpkg --force-architecture -i lightscribe-1.14.32.1-linux-2.6-intel.deb
```

Instead of:
```

sudo dpkg --force-architecture -i lightscribe-1.12.37.1-linux-2.6-intel.deb
```

and all worked well after that, thanks for going to the trouble of walking through the creation of the shortcut in the menu too. \\:D/ 

This is my first post, I hope I am making sense.

---

### Post by red_team316 on 2008-11-15
I can also confirm the 404 error, but I am trying to get the
```

wget http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

```
which is the latest version. I sent in a tech support report notifying them of the problem, so hopefully it will be fixed soon.

...actually as I type this, it appears that the download from the site is back up, but the wget still oddly fails...
```

wget http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb
--20:34:54--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb
           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.

```


Oh, nice howto btw.

You can adjust the contrast to make your labels darker by doing "sudo /usr/lib/lightscribe/elcu.sh"
```

jpg@kubuntu-hardy-64-box:~$ sudo /usr/lib/lightscribe/elcu.sh
Current contrast setting: Enhanced

MODIFY CONTRAST SETTINGS:
1 This will make your labels darker, but you will experience a longer label time
2 This will reset your LightScribe contrast to default factory settings
Select new setting: 1

Enhanced settings applied.

```

---

### Post by red_team316 on 2008-11-17
Tech support did contact me. Here's the reply:
[quote="Tech Support"]
Hello *****,

Thank you for your feedback.

We recently experienced problems with some of the download links.

I have tested the link and it is seem to be working properly.You may need to Refresh your browser and delete cookies and temp files.

Also, make sure you are not using an old URL, try the following:

For the RPM package:

[http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.rpm](http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.rpm)

For the DEB package:

[http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb)

Best Regards,
John Matthews

**re: DLP
[/quote]

I did create a bash script with a loop and here is the script as well as the output:
The output shows that it had to try to download 20 times before it would actually work. I also sent the script and output to them so hopefully they can dig into it deeper. The download does work sometimes, but sometimes not, so the bash loop script is the way to go until they get the download 100% fixed. Hope this helps some people. 

**bash download script with download loop**
```

#!/bin/sh

# Color Codes
red='\e[0;31m'
blue='\e[0;34m'
endColor='\e[0m'
COUNT=1


wget http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb
# Check the deb was downloaded, else keep trying to download it...
while [ ! -e lightscribe-1.14.32.1-linux-2.6-intel.deb ]
do
    echo -e "${red}Download Failed. Attempt #"$COUNT" Retrying...${endColor}"

    wget http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb
    let COUNT=COUNT+1
done

echo -e "${blue}Lightscribe System Software installer was successfully downloaded.${endColor}"

```
**output**
```

jpg@kubuntu-hardy-64-box:~/Desktop/lightscribe/temp$ bash loop.sh
--20:24:48--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #1 Retrying...
--20:24:50--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #2 Retrying...
--20:24:51--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #3 Retrying...
--20:24:52--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #4 Retrying...
--20:24:54--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #5 Retrying...
--20:24:55--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #6 Retrying...
--20:24:57--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #7 Retrying...
--20:24:58--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #8 Retrying...
--20:25:00--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #9 Retrying...
--20:25:07--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #10 Retrying...
--20:25:09--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #11 Retrying...
--20:25:11--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #12 Retrying...
--20:25:13--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #13 Retrying...
--20:25:14--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #14 Retrying...
--20:25:21--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #15 Retrying...
--20:25:27--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #16 Retrying...
--20:25:29--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #17 Retrying...
--20:25:30--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #18 Retrying...
--20:25:41--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #19 Retrying...
--20:25:43--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... failed: Name or service not known.
Download Failed. Attempt #20 Retrying...
--20:25:44--  http://download.lightscribe.com/ls/lightscribe-1.14.32.1-linux-2.6-intel.deb

           => `lightscribe-1.14.32.1-linux-2.6-intel.deb'
Resolving download.lightscribe.com... 220.130.117.55, 220.130.117.61
Connecting to download.lightscribe.com|220.130.117.55|:80... connected.

HTTP request sent, awaiting response... 200 OK
Length: 505,592 (494K) [application/binary]

100%[====================================>] 505,592      106.07K/s    ETA 00:00

20:25:53 (98.61 KB/s) - `lightscribe-1.14.32.1-linux-2.6-intel.deb' saved [505592/505592]

Lightscribe System Software installer was successfully downloaded.
jpg@kubuntu-hardy-64-box:~/Desktop/lightscribe/temp$

```

---

### Post by Brazman on 2008-11-22
Just installed Ubuntu 8.10 intrepid x64 with Win Vista 64. Installation went smooth. Came across problems with dual 8800 GT video cards and lightscribe. Solved both issues. The BusId had to be added to my xorg.conf file and my video was corrected. For lightscribe, sudo apt-get install libstdc++5 corrected my problem with 4L-gui not recognizing my dvd lightscribe writer. Thanks to all who put this information on the forums. Greatly appreciated. 

System: Asus P5N-D motherboard, 4gig DDR2 nvidia SLI memory, dual 8800 GT EVGA video cards, Intel Quadcore 6700.

---

### Post by 2hot6ft2 on 2008-11-25
Thanks GreatGariny for a great how to. I was starting to wonder if I had made the right choice or not by going with the 64 bit OS and loosing the LightScribe feature.
:guitar:

---

### Post by 2hot6ft2 on 2008-11-26
It's installed but I can't type anything into it to put on the disc. It will let me choose a picture but that's it.

Any ideas?

---

### Post by red_team316 on 2008-11-26
> **2hot6ft2 said:**
> It's installed but I can't type anything into it to put on the disc. It will let me choose a picture but that's it.

Any ideas?

Lacie is like that. Try the Simple lightscribe labeler instead if thats what your looking for. It's available for download on the lightscribe website.

---

### Post by 2hot6ft2 on 2008-11-26
> **red_team316 said:**
> Lacie is like that. Try the Simple lightscribe labeler instead if thats what your looking for. It's available for download on the lightscribe website.

The problem there is I'm running 64 bit and they only have it for 32 bit unless someone can walk me thru how to install it on my 64 bit system.

---

### Post by red_team316 on 2008-11-26
Lacie works fine on 64-bit, read the first post about that. I'm not sure if the simple labeler does or not...

---

### Post by High_Speed on 2009-03-16
Has anyone been able to get the latest lightscribe engine to install under intrepid (8.10) 64 bit?  Apparently the version referenced in the guide is no longer available for download, and I tried downloading the latest version from the lightscribe site and I get the following errors:

```
highspeed@diablo:~/workspace$ sudo dpkg --force-architecture -i lightscribe-1.18.2.1-linux-2.6-intel.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 138804 files and directories currently installed.)
Unpacking lightscribe (from lightscribe-1.18.2.1-linux-2.6-intel.deb) ...
dpkg: error processing lightscribe-1.18.2.1-linux-2.6-intel.deb (--install):
 trying to overwrite `/usr/lib/libstdc++.so.5.0.7', which is also in package libstdc++5
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 lightscribe-1.18.2.1-linux-2.6-intel.deb
```

---

### Post by Eagle-Owl on 2009-03-18
Hi Guys I'm new here. 
does anyone have a link to download :

lightscribe-1.12.37.1-linux-2.6-intel.deb

it is not available on lightscribe downloads page anymore. They have only the latest version: 

lightscribe-1.18.2.1-linux-2.6-intel.deb

Which returns an error on installation. 

I really appreciate the help.

---

### Post by uniko on 2009-03-19
You can get the lightscribe package to install if you remove libstdc++5 package first. On my system it removed acroread package too, which I don't use anyway, Evince is fine by me. Didn't try to install acroread package again though.

---

### Post by High_Speed on 2009-03-19
> **uniko said:**
> You can get the lightscribe package to install if you remove libstdc++5 package first. On my system it removed acroread package too, which I don't use anyway, Evince is fine by me. Didn't try to install acroread package again though.

Okay, I could do without Adobe reader, as I don't even have it installed anyway, and don't see need for it.  But what else do I risk breaking if I remove libstdc++5?  Isn't that pretty important (thought it was the general c+ compiler)?  

Then again...could I remove it, install and get lightscribe working...then install libstdc++5 back?  Is that safe?  I'm not sure.....

---

### Post by uniko on 2009-03-20
> **High_Speed said:**
> Okay, I could do without Adobe reader, as I don't even have it installed anyway, and don't see need for it.  But what else do I risk breaking if I remove libstdc++5?  Isn't that pretty important (thought it was the general c+ compiler)?  

Then again...could I remove it, install and get lightscribe working...then install libstdc++5 back?  Is that safe?  I'm not sure.....

Yes libstdc++ is important. Libstdc++5 is older version available from universe, as Libstdc++6 is the current one included in base install. As in you don't need libstdc++5 in your system as it's commonly replaced by libstdc++6.

---

### Post by phenest on 2009-03-22
> **High_Speed said:**
> Has anyone been able to get the latest lightscribe engine to install under intrepid (8.10) 64 bit?...

Yep. And it works in 9.04 too.

---

### Post by lisati on 2009-03-22
I just went to the lightscribe website and was informed: > The system cannot find the file specified.  

Hmmmmm..... fresh install of Intrepid as dual boot instead of previous Wubi, with all updates installed, and going straight to [www.lightscribe.com](www.lightscribe.com) as well......
Time for a bit of head scratching on my part in case I blinked and missed something. Will come back to this shortly...

Edit: Appears not to be the settings on the new install that are at fault, couldn't access the site from Vista or two other machines connected to the same router, perhaps the website is down or there's a problem with my router's settings.....
Edit 2: Appears not to be the router settings........ Lunch time!

---

### Post by High_Speed on 2009-03-22
Ah!  It finally works.  All I had to do was remove the libstdc++5.  Apparently that version blocks the --force-architecture.  Don't know why...

But it's working now.  ;)

---

### Post by Eagle-Owl on 2009-03-25
Cool, the installation worked after I had removed libstdc++5 and the software runs with no problem. I just need to test it now on a CD. 
I didn't need to apply the error fix, and so far it looks fine. 

Thanks Guys ...

---

### Post by daldude on 2010-06-10
This Program proves how much the Lightscribe owners !@#$* and are greedy. It has no way to just simply type in some Text and add effects like Curve it or make it have a Shadow or look 3-D. You have to have a some kind of JPEG or other picture file format in order to make a label for a Lightscribe Disc. If you simply want to just make a Backup DVD Disc and label it you have to first une a program like GNU paint and then use it's text entering mode to type what ever you want to put on a label and then save it as a JPEG so you can use Lacie to import the image and then write it to the Lightscribe Disc and since it's a image it takes a long time to finish because it has to write the entire surface of the disc and not just the text like if you could just enter text as ASCII Characters.

The Simple Labeing Program is lame too because you can't change the font size or even do simple effects lie curve the text or make it bold.

Because the owners of the Lightscribe technolgy want to make money any time someone uses Lightscribe we will Never see a decent Lightscribe label creating program on Linux or even MAC OS.:mad:

---

### Post by daldude on 2010-12-13
Try this program [SIZE=5]**qlscribe - Qt lisghtScribe**[/SIZE]
 

 

 I think I found this program at [http://qlscribe.sourceforge.net/](http://qlscribe.sourceforge.net/) it  does what I want and allows you to just type in text and choose  the font size and type and even make it circular it also allows you to insert a image but doe not seem to allow you to edit it the image or manipulate it's size or shape but it's a vast improvement over the simple label program and [SIZE=2]the 4L Disk Labeling software plus it has a 64-bit version so there is no need to install it from a terminal.[/SIZE]

---

### Post by benjabean1 on 2011-03-08
In case anyone was looking for an open-source alternative to 4L, I've found it, and it's much better than 4L. It's called Qt+ LightScribe, and can be found here:
sf.net/projects/qlscribe

Scratch that. daldude beat me to it.

---

### Post by Trent T on 2012-05-07
Thanks, GreatGariny, for a clear and easy tutorial!
I was able to install SimpleLabeler on my own, but the LaCie 4L-gui did not work until I fixed the error per your instructions.

I am running Ubuntu 11.10 32-bit, and notice that I am unable to put an icon for LaCie (or Simple Labeler) into Dash;  steps 5 and 6 seem not to work under 11.10. 

If anyone already knows how to create and insert an icon into Dash, let me know (or I will, if I figure it out).  
Thanks again!

---

