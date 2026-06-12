---
title: "install problem with wow lich king"
date: 2008-12-24
forum: Wine
---

### Post by Dontechjuan on 2008-12-24
i just got world of warcraft: wrath of the lich king and i can not figure out how to install it. Every time i try this message pops up "No installer data can be found." WTF do i have to do to get it to work? I've tried the wineHQ site and it didn't have any info on this problem.

---

### Post by Dontechjuan on 2008-12-25
ok i found a comment on a site that sort of helps me. The guy who posted the comment said that he was having a problem exactly like the one i am having. he said this........ "If you insert the DVD and try 'wine Installer.exe' it will fail, claiming it cannot find the data. You *must* mount the DVD with the 'unhide' option, and the Installer Tome files will then become accessable. There may be more strangeness with file permissions as well. Also, doing this will let you copy the files off the DVD onto your hard drive." OK so what is this "unhide option" and how do I go about doing what he said?

---

### Post by Dontechjuan on 2008-12-25
Ok WTH I know someone on here knows what an "unhide option" is and what I need to do to get lich king installed. So why is it this post has been on here for over 24 hours and no one gives a sh!t? Maybe I should go back to the cursed windows OS. At least when I need help with windows the guy from India will attempt to help (fail miserably, but he will at least TRY). So someone, anyone please post something constructive so that I at least know that somebody is listening and trying to be helpful.

---

### Post by hibajugala on 2008-12-25
stop talking to yourself ;)

---

### Post by EnderEcho on 2008-12-25
The unhide option can be done by pressing ctrl+h

The lack of responses may be due to what it seems to be a lack of research. Googling has been an amazing tool for me and getting applications to work. You can literally type the question you have into google and something of relevance will pop up. 9 out of 10 times there will be something from the ubuntu forums that shows up.

Good luck.

---

### Post by Dontechjuan on 2008-12-25
thank you ill try that. You have restored at least some of my hope for these forums.

---

### Post by Dontechjuan on 2008-12-25
unfortunately ctrl+h didnt do anything helpful.:confused: thx for the try though. I also tried downloading the lich king from the wow website and it downloaded an installer and i opened it. it went to a menu and i clicked install. it went to the End user agreement and hung up. so i tried to close the window and i had to force quit it becuase it wouldnt respond. Now i connot even get the installer to open any more. i tried restarting my computer i redownloaded the installer and it still wont open again. so im back to square one. i messaged blizzard support and told them as much as i could with the 1000 character limit on the email and am now waiting for a reply that i dont expect to get till at least tomarrow since their office hours are 8am to 8pm pacific time. But i dont really expect them to have an answer either since linux is still not considered a "mainstream" OS. So I doubt they have any techs that know enough about ubuntu to help me. So plz there must be someone that has installed lich king on ubuntu and if you know somwone who has please get them to come to these forums and reply to this post. thank you.

---

### Post by OrbJinzo on 2008-12-25
sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/ 

Make sure you have unmounted the drive first with umount. then run this it should get ya going.

---

### Post by oni5115 on 2008-12-25
I actually had this problem I think with either BC or the original WoW CE DvD.  Regardless, it's format is a little odd and as mentioned earlier you need to use the unhide option.

You can either umount and remount using -o unhide, or do what I did and modify your /etc/fstab file to have the unhide option.

With wotlk, I also found I had to copy the entire DvD contents to my hard drive, then give myself the correct file permissions (rest the user/group) and then I could run the installer correctly.  What a pain, but it worked.

I used PCManFM to change the user/group, I'm pretty sure nautilus can do it as well - but you will likely have to load nautilus using sudo nautilus from the command line.  Then right click the folder, properties, etc.

I'd give you the command line to do it, but I don't really know what it is off hand.  Something like chmod -R username:username foldername - but that is just going from memory from what I read earlier this afternoon.  As mentioned above, I just did it from the GUI myself.

Alternatively, you can just download it from blizzard and it'd probably be less of a hassle.

---

### Post by Dontechjuan on 2008-12-28
I tried entering 

"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/"

 as its shown and i get this message "Mount: special device dev/cdrom does not exist" i checked the file and sure enough its not there, its in the media file with cdrom0 so i typed it in like this

"sudo mount -o ro,unhide,uid=1000,gid=1000 /media/cdrom /media/cdrom0/"

and it says this "mount: /media/cdrom0 is not a block device" I wonder if it matters that in the media folder with cdrom file and cdrom0 file is the file with the name "lich king" so i placed the name in the terminal command like

"sudo mount -o ro,unhide,uid=1000,gid=1000 /media/cdrom /media/"lich king"/"

I got this message "mount: mount point /media/lich king does not exist" yet i open the media file and there is a file named "lich king" so i have no idea what I'm doing wrong. So plz help me and remember that im terminal illiterate so plz lead me through step by step with "copy paste" terminal commands. thank you.

---

### Post by Dontechjuan on 2008-12-28
ok new problem i found the file i needed instead of 

"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/"

its supposed to be

"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom1 /media/cdrom0/"

but now i get

"no medium found"

so now what?

---

### Post by Dontechjuan on 2008-12-28
I got the tome files shown using the unhide option and the installer finally runs. I click install and it goes to the select language screen. ok select english and click ok and it goes to the End User agreement and it loads the window boarder and the agrre disagree buttons but the text is gone and it freezes up and I have to force quit it. Does anyone know how to fix this?

---

### Post by OrbJinzo on 2008-12-29
download the installer from blizzard?

---

### Post by Dontechjuan on 2008-12-29
tried that. it started to install once and got stuck at the End User Agreement as well and then would not open again even after deleting the downloaded installer and redownloading it.

---

### Post by OrbJinzo on 2008-12-30
Im curious which verison of wine are you running. When I got my DVD for wotlk wine was at 1.1.4 and it installed flawlessly once ran the unhide stuff. It might be an off chance this could be a regression *shrug*

---

### Post by Dontechjuan on 2008-12-30
it says wine 1.0 im not sure if the the newest version or an older one. If it is an older one how can i update it without losing all of the games and saved files that I have already installed on wine?

---

### Post by Dontechjuan on 2008-12-30
well i found the wine HQ and was able to get my update manager to download and install the newest wine version. But I still can not get lich king installed. it still bugs out at the "End User Agreement".

---

### Post by Dontechjuan on 2009-01-01
SUCCESS!! I finally figured it out. For those of you who are curious in how I got it working or anyone who has the same problem in the future I will go through the steps on how I got "Lich King" working.

1.Mounting the cd-rom drive with the "unhide" option. 

As stated above you must open the terminal and enter this line...
"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/"
However this did not work for me, because I do not have "/dev/cdrom". During one of the ubuntu updates it changed the folder name from cdrom to cdrom1 so i had to enter this line....
"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom1 /media/cdrom0/"
But it did not work either with or without the cd, i did get it working by opening the cd tray placing the cd in the tray entering the line on the terminal and when i did it pulled the tray in and it worked.

2.Copy the entire contents of the cd to a folder on your drive. 

I would suggest making a new folder on your desktop to copy the cd to. Do not copy it to the WoW folder.

3.Try running the "installer.exe" file.
If it works then great. If it freezes on the "End User Agreement" like it was doing on me then proceed to step 4.

4.Getting past the "End User Agreement"

As most of you know some games require you to go to the "configure wine" and add .dll files in the libraries tab. If you don't know where that is just click on "Applications" on the top left of your desktop on the toolbar, go down to "Wine", then "Configure Wine" and click on the "Libraries" tab. In this tab you can add .dll files and change their status to a couple of different options like, native, builtin, disable, ect. The problem that I was having was that a game I installed earlier required that I add the "mshtml.dll" and set it to "native". Having this .dll file added to the list was keeping the program from getting the data from online sources. I didn't know it when I was playing the original WoW and "The Burning Crusade" that when I started the game and the news page comes up that because of the mshtml.dll file it was not able to access the data for the news page. The same thing was happening to the "End User Agreement". So just write down on a piece of paper mshtml.dll(native), so that when you go to play the other game that requires it you'll be able to remember what to add to play the other game. And then remove the mshtml.dll from the list. Now open the "installer.exe" and it should work. If it does not then you may have another .dll file causing problems, so again start writing down all the .dll files you have added to your list and start removing them one by one and after each one try the installer. One should eventually work.

---

### Post by OrbJinzo on 2009-01-01
Hrm i would never thought it was that mshtml.dll problem. I find it strange though since i have never had any problems installing Wotlk

---

### Post by techtree on 2009-01-23
> **OrbJinzo said:**
> sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/ 

Make sure you have unmounted the drive first with umount. then run this it should get ya going.

Hot snot!!  That did the trick for me!

Thank you!  :D :popcorn: :KS

-techtree

---

### Post by machineghost on 2009-01-26
> Hot snot!! That did the trick for me!
Ditto ... except for the snot part.

Also, for n00bs like myself who read this:
> Make sure you have unmounted the drive first with umount
and cringed because they're not super-familiar with mounting/unmounting stuff at the command line, all it takes is:
```
sudo umount /dev/cdrom
```

---

### Post by DSK on 2009-02-09
Got Lich King to install.  Added Wine repos and upgraded to 1.1.14.   Also updated the nvidia drives to 180.11 from intrepid backports.  Also had to do the unmount of the dvd and remount to copy contents to the HDD.  Also as a side note after the wine update and running the installer Wine asked to enable the gecko engine and after that all went well.

Thanks everyone for the tips and info in this topic.

---

### Post by Sam_wyze on 2009-03-12
I'm having the same problems as donjuan.  
i've tried:
sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/
and 
sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom1 /media/cdrom0/

but i'm told that 
mount: special device dev/cdrom does not exist
and
mount: special device dev/cdrom1 does not exist

what am I doing wrong?

---

### Post by Sam_wyze on 2009-03-15
ok, nevermind.  after pulling my head outta my ***, i realized what was wrong.  thanks for the help

---

### Post by Impregnator on 2009-05-13
> **OrbJinzo said:**
> sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/ 

Make sure you have unmounted the drive first with umount. then run this it should get ya going.

I registered for this forum simply to say Thank You to Orb for the simple and perfect instructions. I've tried almost everything else on these forums. His is what works. Just make sure you type the right CDROM number!

Thanks again!

---

