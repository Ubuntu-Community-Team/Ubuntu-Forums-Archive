---
title: "How to make the totally unsupported Lexmark X2500 Work"
date: 2009-08-18
forum: Tutorials
---

### Post by zerhacke on 2009-08-18
1. On the Lexmark website under Drivers & Downloads find the X2600 all-in-one printer and click on Unix/Linux. For the Eee PC or other Debian-based distros choose the first option Debian 4 and download the following driver file (approx 30MB) to your home folder:
lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip

2. Don't connect the printer yet. Right-click on the downloaded file and choose "Extract All...". then click OK to unzip it in your home folder.

3.You will now also have the same file but unzipped so it ends in sh. If you can't get the installer to run by clicking the icon, open a terminal and try the following:
chmod 744 lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

4. Now follow the instructions on screen. When you get to the point where it asks you to connect the printer, do so. However, you will find it won't be recognised (because it's not a 2600 series or Z2300 series printer). Exit by clicking the close button on the window and then clicking "Yes".

5. Now edit three text files to change the product i/d (PID) from 011d (or 0x011d), which is the PID for the X2600 series, to 010b (or 0x010b) which is the PID for the Lexmark X2550. The following commands in a terminal will open each of the relevant files in a text editor:
sudo kwrite /usr/lexinkjet/lxk08/etc/lxdn.conf
sudo kwrite /usr/lexinkjet/lxk08/etc/99-lexmark-2600-series.rules
sudo kwrite /usr/lexinkjet/lxk08/etc/Lexmarklxdn.conf
In each case change 011d wherever it appears to 010b (or 011D to 010B if it was in capitals), save and exit.

6. Now add the printer using the CUPS interface.
In the first box on the name/ description page there must not be any spaces so, for instance, just type lexmarkX2550 as one word. On the next page, in the Device dropdown list, select: "Lexmark USB Backend #1 (Lexmark X2500 series)" For Model/Driver select "Lexmark 2600 series, 1.0 (en)".
(On the Eee PC, you can also add the printer via the Printers icon on the Settings tab. However, I found doing it this way did not set the A4 paper size properly so that multiple-page printing did not work correctly.I then had to change the paper size in CUPS so it seems best to add the printer via CUPS in the first place.)

7. Finally click on "Print Test Page" and keep your fingers crossed... The scanner should work as well, although only from the computer not from the scanner button on the printer. There is also a Lexmark inkjet program to monitor ink levels and align the cartridges (type lexijtools in a terminal). However I could not get this to work - probably it doesn't recognise the different cartridges in the X2550. I'm hoping it doesn't matter on the X2500 series as an alignment sheet can be printed by holding the scan button for 3 seconds, then place it on the scanner glass and press the button again.

(with thanks from OpenPrinting Forum)

---

### Post by letocharm on 2009-09-14
You sir are amazing. This deservers a bump as it probably works for many printers not just the X2500 - one needs only go

dmesg | grep lp

and look at their printer's PID. So instead of 010B, it might be 011A, for example.

---

### Post by Joshh100 on 2009-09-22
I'd like to bump this up once more, I found the same solution on the aforementioned website and it works like a charm! I've been trying forever to get my damn Lexmark X2500 working with Ubuntu and with this solution I finally got it to work! works great!

---

### Post by 2007mordor on 2009-11-11
I was trying to install the script but, there is an error that says the CUPS is not the last version, it needs the 1.2 version or above, but i already have installed 1.4.1 CUPS version. Any idea?
Thanks in advance.
Mordor

---

### Post by Shifty0509 on 2009-11-16
You are amazing!! Thanks a million.

---

### Post by ktsteel on 2009-11-22
Hey guy I can get all the way to the screen that says need to enter admin password but it wont accept mine, and I know it is correct, any thoughts?

---

### Post by nathan726 on 2009-11-30
> **2007mordor said:**
> I was trying to install the script but, there is an error that says the CUPS is not the last version, it needs the 1.2 version or above, but i already have installed 1.4.1 CUPS version. Any idea?


[http://ubuntuforums.org/showthread.php?t=1223710](http://ubuntuforums.org/showthread.php?t=1223710)

---

### Post by ru0n on 2009-12-05
Thanks a lot. Worked like a charm... If only Lexmark would support Linux better.

---

### Post by nickblooruk on 2009-12-27
Hi All,

I am trying to install an X2580 and was hoping that these instructions would work. Unfortunately the print job is failing with the following error
stopped 
*"A wrong printer is detected. Any printjobs are canceled."*
I am using version 1.4.1 of CUPS.
Has anybody else had similar problems? Has anybody found a solution?

Thanks in advance

Nick Bloor.

---

### Post by nickblooruk on 2009-12-27
My BAD!!!

Sorry all,
School boy error!!

Thanks to Letocharm I have fixed the problem.
After typing the "dmesg | grep lp" command I discovered that I was using the wrong PID
Instead of using  of 010B, I was using 011B

Nick Bloor

---

### Post by mbv93 on 2010-02-01
Amaaaaazing!!! it worked perfectly I had tried to install this printer for ages and searched all over the web for a solution with no luck. until I found this! thank you so much!

---

### Post by billcecil on 2010-02-22
> **ktsteel said:**
> Hey guy I can get all the way to the screen that says need to enter admin password but it wont accept mine, and I know it is correct, any thoughts?

I have the same problem. What can I do?

---

### Post by joedulin on 2010-02-22
Hey ktsteel and billcecil, I was having that same problem and it's a very simple fix. The trouble is that it's looking for the 'root' password, and I'm guessing you're using an OS that uses sudo instead of root, right? Yeah, so you don't have a root password, you have a sudo password. Anyway, to get around that just execute the script with sudo, e.g. sudo ./lexmark_script_whateveritis

Also thanks for this little tip altogether. I haven't got it running yet (having troubles with the cups 1.2 thing, but I'm sure nathan726's link will do the trick for me, thanks to you too), but I will. I've been looking for this for over a year now...

UPDATE: Well, I got it working just fine if the printer is plugged directly into my Ubuntu box. Trouble is, I usually have it connected to a laptop that serves as a print server. Honestly, I'm thinking my troubles lie in the fact that the "server" is Windows XP, due to the fact that before today I couldn't use the printer with anything but Windows. I have the printer connected to my Ubuntu box through CUPS, and setup as a Samba printer. I'm using the exact same driver as I did when connected directly using USB. When printing over the network, my Ubuntu box gives me an error.

The error states:"There was a problem processing document 'test page', but in the Printer Properties window next to Printer State: it says, only for a moment, that the printer cannot communicate with the computer. 

If anyone can help me out with this, that would be awesome. Otherwise, I'll take what I can and simply connect this computer directly to the printer (it's a laptop anyway) when I need to print, which is rarely. Thanks again guys.

---

### Post by billcecil on 2010-02-23
Thanks Joedulin, but I tried the sudo thing and still had no luck. I get through the setup until it asks for root password.

---

### Post by billcecil on 2010-02-23
I did it! I had to change the sudo password. Thanks for the help. I might get this stuff down some day.

---

### Post by harrison bergeron on 2010-02-23
thank you this worked really well for me! you sir, are a hero.

---

### Post by Karmic Alice on 2010-05-14
Hello and thank you! 

**But THERE IS ANY way of making the scanner of this all-in-one work too? **Is very important. Maybe even more than the printing. 

Any suggestions?

---

### Post by Karmic Alice on 2010-05-14
Bump

---

### Post by mbv93 on 2010-05-26
Hi, thanks this worked perfectly for me! everything worked including the scanner but I recently upgraded ubuntu to 10.04 Lucid Lynx and Xsane just doesn't detect the scanner now. What can I do?

---

### Post by Gold_Eyes on 2010-06-12
> **mbv93 said:**
> Hi, thanks this worked perfectly for me! everything worked including the scanner but I recently upgraded ubuntu to 10.04 Lucid Lynx and Xsane just doesn't detect the scanner now. What can I do?

i don't Understand what should i do in here:
> 6. Now add the printer using the CUPS interface.
In the first box on the name/ description page there must not be any  spaces so, for instance, just type lexmarkX2550 as one word. On the next  page, in the Device dropdown list, select: "Lexmark USB Backend #1  (Lexmark X2500 series)" For Model/Driver select "Lexmark 2600 series,  1.0 (en)".
(On the Eee PC, you can also add the printer via the Printers icon on  the Settings tab. However, I found doing it this way did not set the A4  paper size properly so that multiple-page printing did not work  correctly.I then had to change the paper size in CUPS so it seems best  to add the printer via CUPS in the first place.)Can you please provide me some informations about what should i do exactly in here .
I can't find this =>> "name/ description" , where should i look for it becouse on [http://localhost:631/](http://localhost:631/) i cannot see it.
Thank you all .
This i my CUPS 1.4.3 main page[ http://img816.imageshack.us/img816/261/cups143.png]("http://img816.imageshack.us/img816/261/cups143.png")

---

### Post by muasg on 2010-08-14
> **billcecil said:**
> I have the same problem. What can I do?
Hi,

I'm a new Ubuntu 10.04 user and I'm trying to install this stupid Lexmark driver.  I ran into the same problem where it asks you to enter the root password and naturally I enter my user/administrator password and it says it's not correct.  I guess what I'm asking is if someone can spell out exactly what I'm supposed to type to get through the root password thing so I can continue installing the driver for my x2580.  Please...very specific instructions are highly sought after.

THanks,

---

### Post by aquascrotum on 2010-08-15
I've managed everything up until going into the CUPS interface...how do I go about this?  I have Cups installed in synaptic, is there any other package I need and then how do I run it?

---

### Post by aquascrotum on 2010-08-15
> **aquascrotum said:**
> I've managed everything up until going into the CUPS interface...how do I go about this?  I have Cups installed in synaptic, is there any other package I need and then how do I run it?

I'll answer my own question...[http://localhost:631/](http://localhost:631/)

---

### Post by Erasmuz on 2010-08-26
muasg

For some reason when I ran the file the lexmark installer it did not recognize my password as correct either.

If you go to a command line and run the app from there with sudo it should work fine.  It won't ask for the root password during the install process. 

(assuming the installer is extracted to your home dir.)
```

sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

```


To get to the cups interface point your browser at:
```

http://localhost:631

```

Click the Administrator tab, and add the printer. 

Hope that helps, and thanks for the great post!  This helped a lot!

---

### Post by newfuturevintage on 2010-09-17
For those of you that have had a chance to use the x2500 in ubuntu, can you please report back if this printer is as much of an infuriating beast (ink hog / print test sheet / "your filled ink cartridge is empty, please order more from Lexmark") in ubuntu as it is in XP?

Thanks

---

### Post by somerefriedbeans on 2010-09-28
It seems to work fine for me. Doesn't hog that much ink...

---

### Post by firehawk_1989 on 2010-10-18
that was awesome, I have been wanting to get my x2500 to work in Linux forever and nothing ever worked, this worked flawlessly!

---

### Post by wotsken on 2010-11-06
i am hoping you all can help me i am very veryyyy new to this and not good at command line i have done some years ago but well stupid as ?!@##$ but i will not use windows anything any more and i am trying to learn i am in the works of converting everything i have to ubuntu this printer the lexmark X2500 is one of 3 things left and i can say good by to the windows world forever but i need this for my business is anyone willing to walk me threw it like i am a idiot because well i am when it comes to this i am going to get as far as i can i have to get out of the windows world

---

### Post by benbeel on 2010-12-22
> **muasg said:**
> Hi,

I'm a new Ubuntu 10.04 user and I'm trying to install this stupid Lexmark driver.  I ran into the same problem where it asks you to enter the root password and naturally I enter my user/administrator password and it says it's not correct.  I guess what I'm asking is if someone can spell out exactly what I'm supposed to type to get through the root password thing so I can continue installing the driver for my x2580.  Please...very specific instructions are highly sought after.

THanks,
Specific instructions on installation on Ubuntu 9.10+ (including 64bit machines): 
Download the debian drivers from the lexmark website [here]("http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_X2600&focusedTab=DOWNLOADS#1"), click on the dowloaded .zip file and extract it. Then open a terminal and enter the following:
```

cd **directory where you extracted your installer file**
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark
cd lexmark/
tar xvf instarchive_all --lzma
lexmark-inkjet-08-driver-1.0-1.i386.deb
sudo dpkg -i --force-all lexmark-inkjet-08-driver-1.0-1.i386.deb
```

Your driver will then be installed. Following the directions at the beginning of this post has NOT yielded good results for me however, and am unable to print or scan in ubuntu 10.10 using the x2500.

---

### Post by aquascrotum on 2011-10-16
I had this working in Karmic, have installed Oneiric and am now in a mess.

I can do everything up to:

> 6. Now add the printer using the CUPS interface.
In the first box on the name/ description page there must not be any spaces so, for instance, just type lexmarkX2550 as one word. On the next page, in the Device dropdown list, select: "Lexmark USB Backend #1 (Lexmark X2500 series)" For Model/Driver select "Lexmark 2600 series, 1.0 (en)".
(On the Eee PC, you can also add the printer via the Printers icon on the Settings tab. However, I found doing it this way did not set the A4 paper size properly so that multiple-page printing did not work correctly.I then had to change the paper size in CUPS so it seems best to add the printer via CUPS in the first place.)

When I go into the CUPS interface (CUPS 1.5?) to add a printer I dont get the option to add a new custom printer, only to add printers from a defined list.  One of them is a Lexmark 2500 series, however if I select that I can't select "Lexmark USB Backend #1 (Lexmark X2500 series)" anywhere.

Can anyone shed any light!?

---

### Post by uh60-army-mac on 2011-10-23
> **aquascrotum said:**
> I had this working in Karmic, have installed Oneiric and am now in a mess.

I can do everything up to:



When I go into the CUPS interface (CUPS 1.5?) to add a printer I dont get the option to add a new custom printer, only to add printers from a defined list.  One of them is a Lexmark 2500 series, however if I select that I can't select "Lexmark USB Backend #1 (Lexmark X2500 series)" anywhere.

Can anyone shed any light!?

I also have this same problem any help would be great.:confused:

---

### Post by aquascrotum on 2011-12-28
Bit of a bump to the top - has anyone any new workaround around the new CuPS issue?

---

### Post by nyjkkyjn on 2012-01-07
I think this bug is related to the problem..
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/908864](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/908864)

---

### Post by aquascrotum on 2012-02-16
Bump...I gave up and bought an Epson, still don't like having my printer turned into a brick though - any update on this bug?

---

### Post by tuxwarrior10k on 2012-07-18
Hmm... I checked the support page for Lexmark. The driver download page for the 2600 gives me no option to select a distro after selecting Linux/Unix from the dropdown. Am I just missing something incredibly obvious?

---

### Post by BrandonTX on 2012-08-05
I've just started learning ubuntu. its going we'll. I'm sure I can alter the x2600 driver to work with my x2500... 
but I'm having the same issue the previous post describes: the Lexmark x2600 driver download page doesn't have a linux driver available.

I know its an ancient printer, but it works great for me. I love to implement the solution provided in this thread. 

Can anybody help me find this x2600 driver?

thx

---

### Post by erikao on 2012-08-10
I found the x2600 link just by filtering for that (not also OS) [http://support.lexmark.com/index?page=content&docLocale=en_US&id=DR860](http://support.lexmark.com/index?page=content&docLocale=en_US&id=DR860)

But, unfortunately, when I tried to follow the installation instructions, the installer starts and then fails. It closes immediately and I couldn't copy and paste the error text, so I'm not sure what happened.

Current status for me is that I can't even get through the Lexmark installation. I'm on 12.04.

---

### Post by mjm1231 on 2012-08-22
There are a couple threads on the forums about this (not always easy to find) but the short answer is the installer must be run as root. Unfortunately, the easiest way to do this is from a command line.

Open up a terminal. Navigate to the folder where your extracted download is (cd Downloads, or wherever your lexmark-inkjet-1.0-1.i386.deb.sh is located). Type 'sudo su' (no quotes) and enter your password. Then type ./lexmark-inkjet-1.0-1.i386.deb.sh.

This will allow the installer to run. Unfortunately, there is a new bug that has always existed in the driver that now affects newer versions of Ubuntu (it was working fine in 10.04, at least). So the installer still fails for me. I have contacted Lexmark support about this issue, and will be starting a new thread about it as well. Hopefully it can be resolved. It is a nice light duty printer, and as long as I can get ink for it I would like to keep using it.

---

