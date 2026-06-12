---
title: "Rockbox on YOUR sansa fuze :o"
date: 2009-06-08
forum: The Cafe
---

### Post by dragos240 on 2009-06-08
A few days ago I posted about my sansa fuze finally getting rockbox on it, and I noticed a few people wanting to install it. I have just zipped all of the things you need in an archive, but I am going to give you a warning.

**[COLOR=Red]DOING THIS WILL VOID YOUR WARRANTY AND HAS A POSSIBILITY TO PERMANENTLY BRICKING YOUR SANSA FUZE.[/COLOR]**

Just to let you know, if you don't care, then be my guest and follow these instructions:

1. Download the [archive]("http://www.megaupload.com/?d=HRI9IF7I") to a folder.

2. Plug in your sansa fuze and make sure the usb mode is MSC.

3. Extract the contents of the archive to the root directory of your fuze.

4. Unplug your fuze, and shut it off.

5. Boot it back up and rockbox should be there.

EDIT: New link from coldbird, (Link removed, it is broken at the current time)
This is updated to the latest build of rockbox, the other link is outdated. Thank you!

EDIT2: Coldbird has removed the index.php because it was building up on their server, this link is just a list of the latest versions that coldbird has compiled. It's manual now. [Here is the link.]("http://coldbird.celes-network.de/rockboxfuze/")
Also the newest archives from this site are in rar format, you will need to install this manually as well:
Arch pacman -S rar unrar
Ubuntu/Debian apt-get install rar unrar
Fedora yum install rar unrar

EDIT3: Rockbox is now officially supporting the fuze! No need for this topic anymore!

---

### Post by NFblaze on 2009-06-08
It hasnt been offically released?

---

### Post by dragos240 on 2009-06-08
> **NFblaze said:**
> It hasnt been offically released?

No it has not. Rockbox has not been officially released yet. I compiled the source.

---

### Post by clonne4crw on 2009-06-09
Has anyone ELSE sucessfully tried this yet? I don't wanna brick my fuze. It's not that I don't trust you, I just want to see that other people have done it, too. I've been waiting fot this for ages!

----edit:
What firmware version are you using?

---

### Post by days_of_ruin on 2009-06-09
> **dragos240 said:**
> A few days ago I posted about my sansa fuze finally getting rockbox on it, and I noticed a few people wanting to install it. I have just zipped all of the things you need in an archive, but I am going to give you a warning.

**[COLOR=Red]DOING THIS WILL VOID YOUR WARRANTY AND HAS A POSSIBILITY TO PERMENENTLY BRICKING YOUR SANSA FUZE.[/COLOR]**

Just to let you know, if you don't care, then be my guest and follow these instructions:

1. Download the [archive]("http://www.megaupload.com/?d=HRI9IF7I") to a folder.

2. Plug in your sansa fuze and make sure the usb mode is MSC.

3. Extract the contents of the archive to the root directory of your fuze.

4. Unplug your fuze, and shut it off.

5. Boot it back up and rockbox should be there.

pics or it didn't happen:p

---

### Post by PatrickMoore on 2009-06-09
Im going to since i have a backup mp3 player

---

### Post by dragos240 on 2009-06-09
> **days_of_ruin said:**
> pics or it didn't happen:p

You have a point, and I have a camera. Let me take some, and I'll be back ;)

---

### Post by PatrickMoore on 2009-06-09
i tried and still have the same sansa firmware so am i missing something? is there files that need to be pitched?

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> i tried and still have the same sansa firmware so am i missing something? is there files that need to be pitched?

Did you extract ALL the contents to your fuze, and did you make sure the usb mode was MSC? Try it again, and also I would like a screenshot of your sansa fuze root directory with hidden items enabled before you plug it in. Oh and by the way. I GOT PICTURES! Excuse the quality of them though.
[http://dragos240.freewebhostx.com/P1010090.JPG](http://dragos240.freewebhostx.com/P1010090.JPG)
[http://dragos240.freewebhostx.com/P1010091.JPG](http://dragos240.freewebhostx.com/P1010091.JPG)
[http://dragos240.freewebhostx.com/P1010092.JPG](http://dragos240.freewebhostx.com/P1010092.JPG)
[http://dragos240.freewebhostx.com/P1010093.JPG](http://dragos240.freewebhostx.com/P1010093.JPG)
[http://dragos240.freewebhostx.com/P1010094.JPG](http://dragos240.freewebhostx.com/P1010094.JPG)
[http://dragos240.freewebhostx.com/P1010095.JPG](http://dragos240.freewebhostx.com/P1010095.JPG)
[http://dragos240.freewebhostx.com/P1010096.JPG](http://dragos240.freewebhostx.com/P1010096.JPG)
[http://dragos240.freewebhostx.com/P1010097.JPG](http://dragos240.freewebhostx.com/P1010097.JPG)
[http://dragos240.freewebhostx.com/P1010098.JPG](http://dragos240.freewebhostx.com/P1010098.JPG)

---

### Post by PatrickMoore on 2009-06-09
heres my screenshot im going to have another go

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> heres my screenshot im going to have another go

Nice theme, did you press ctrl H? Just curious, and is it in MSC mode? These points are critical.

---

### Post by PatrickMoore on 2009-06-09
thank you i think its elegant. i did not hit ctrl+ h my fuze is set to msc though

i did however include hidden files.

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> thank you i think its elegant. i did not hit ctrl+ h my fuze is set to msc though

i did however include hidden files.

Would you give another screenshot with ctrl H? It would help.

---

### Post by PatrickMoore on 2009-06-09
this is including ctrl + h i just formatted thinking that if i remove media then it may be easier

---

### Post by days_of_ruin on 2009-06-09
So you're Mr Blurrycam.:lolflag:

Can you run doom on it?

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> this is including ctrl + h i just formatted thinking that if i remove media then it may be easier
Thank you  for helping us help you help us all! Now it seems that .rockbox and the bootloader did not get put in, this really does help. Now try extracting everything from the archive into a folder, then into the main fuze directory, make sure to have ctrl + H on so you can view .rockbox and copy it. Try this method and shut down your fuze, and boot it back up afterwards.

---

### Post by days_of_ruin on 2009-06-09
Where exactly did you get this archive anyway? I'd appreciate a link.

---

### Post by dragos240 on 2009-06-09
> **days_of_ruin said:**
> So you're Mr Blurrycam.:lolflag:

Can you run doom on it?

Yeah rockdoom, it doesn't seem so, I guess that plugin doesn't work yet, it didn't work for me :(

---

### Post by dragos240 on 2009-06-09
> **days_of_ruin said:**
> Where exactly did you get this archive anyway? I'd appreciate a link.

Oh I compiled the rockbox source myself that I downloaded via subversion. And I put all the files into an archive.

---

### Post by PatrickMoore on 2009-06-09
still nothing. i extracted to my desktop and then cut and pasted into the root folder

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> still nothing. i extracted to my desktop and then cut and pasted into the root folder
Really? Hmm.... Try just extracting the bootloader, and after it updates THEN try copying .rockbox.

---

### Post by PatrickMoore on 2009-06-09
that again didnt work i have to be missing something

---

### Post by dragos240 on 2009-06-09
Hmm.... I wish I knew what was wrong... OH! When opening your fuze root folder you will see the directory name. What does it say? Trust me, this will help me find the problem.

---

### Post by PatrickMoore on 2009-06-09
that may be the issue im just openong up the fuze how are you accessing the root folder?

---

### Post by days_of_ruin on 2009-06-09
For doom did you try putting the .wad in there?

EDIT: btw I am running it rockbox now. Thanks for posting.

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> that may be the issue im just openong up the fuze how are you accessing the root folder?

The same way (I think), but could you just tell me what it says right of the Location: bar? Oh and are you talking about the actual root folder located at / rather than /media/diskx?

---

### Post by PatrickMoore on 2009-06-09
the root folder on the device.i wonder if i enter nautilus as root to do it if that will work

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> the root folder on the device.i wonder if i enter nautilus as root to do it if that will work

Well.... I don't see the harm of it, but I didn't have to.

Also would you please post what your location bar says? Please?

---

### Post by PatrickMoore on 2009-06-09
/media/3.9GB media root privledges changed nothing

---

### Post by dragos240 on 2009-06-09
> **PatrickMoore said:**
> /media/3.9GB media root privledges changed nothing

Well it's definitely in MSC, that was my main suspicion.

Extract the contents of the archive to a folder in your home folder named "a".

After this is done, open up a terminal and type the following command:

```

cp a/fuzea.bin /media/3.9GB\ media && cp -r a/.rockbox/ /media/3.9GB\ media

```

---

### Post by PatrickMoore on 2009-06-09
```
cp: cannot overwrite non-directory `/media/3.9GB media' with directory `a/.rockbox/'

```

im getting this error

---

### Post by regeya on 2009-06-10
> **dragos240 said:**
> 5. Boot it back up and rockbox should be there.

It was indeed.  It works much better than I'd been expecting!

Thank you for posting this. :D  I'd tried building it myself, and though I consider myself to be fairly computer-savvy, I didn't manage to do it (I get a "no .rockbox directory" error) and I even tried a Rockbox dev's "fixed" build, no dice.

---

### Post by V!&gt;&lt;0N on 2009-06-10
why....why...why did you use mega upload......... 
Thanks though.  Ill try it once i can download:D

---

### Post by clonne4crw on 2009-06-10
Another question: Is there a way to revert back to the original Sansa firmware after this? Or switch between it and Rockbox? I'm still a little sketchy about trying this on my own.

---

### Post by days_of_ruin on 2009-06-10
> **clonne4crw said:**
> Another question: Is there a way to revert back to the original Sansa firmware after this? Or switch between it and Rockbox? I'm still a little sketchy about trying this on my own.

[http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=23276]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=23276")

Just follow the instructions.

EDIT: Try using an older firmware in case it can't load you microSD card.

---

### Post by V!&gt;&lt;0N on 2009-06-10
This worked for me! Finally, I've been waiting for so long.  Thanks very much! However, I do have one problem... Now my Fuze does not show up in Ubuntu.  Is there a special way that I should be connecting it?

---

### Post by Jackelope on 2009-06-10
OK, not that I don't believe you all, but since when can you install Rockbox without loadinng a shiny new bootloader? You really just copy the files and reset? Can someone confirm that you don't need the custom rockbox bootloader to make this work? Thanks.

---

### Post by dragos240 on 2009-06-10
> **V!><0N said:**
> This worked for me! Finally, I've been waiting for so long.  Thanks very much! However, I do have one problem... Now my Fuze does not show up in Ubuntu.  Is there a special way that I should be connecting it?

Yes, the USB doesn't work yet. Shut down your rockbox by holding your power switch up until it powers off and then connect it.

---

### Post by dragos240 on 2009-06-10
> **Jackelope said:**
> OK, not that I don't believe you all, but since when can you install Rockbox without loadinng a shiny new bootloader? You really just copy the files and reset? Can someone confirm that you don't need the custom rockbox bootloader to make this work? Thanks.

Yes, the reason being that this bootloader directs the fuze's hardware to read the rockbox files on bootup, compared to sansa's bootloader which only reads it's firmware. Take the windows bootloader, it automatically boots into windows xp without showing you your options, so you need grub.

---

### Post by dragos240 on 2009-06-10
> **PatrickMoore said:**
> ```
cp: cannot overwrite non-directory `/media/3.9GB media' with directory `a/.rockbox/'

```im getting this error

Hmm..... I suggest going plugging into your fuze and using gparted to change the label to nothing, this will automatically make it /media/disk. And it will be much easier.

---

### Post by Goombie on 2009-06-11
> **dragos240 said:**
> Yes, the USB doesn't work yet. Shut down your rockbox by holding your power switch up until it powers off and then connect it.
When I do this, I connect using the Sansa firmware instead of Rockbox. Is that supposed to happen?

Otherwise, everything works fine so far. Is there a way to change the font size for the menus, though? I can't read them very well. >.<

---

### Post by Ebuntor on 2009-06-11
That worked great! I'm so glad my Fuze has so much more options now, and games too. :D
Thank you dragos.

---

### Post by Ebuntor on 2009-06-11
Oh crap, seems FAT is corrupted somehow. I can't mount it in Ubuntu. I had this problem before and I fixed it by formatting it in OSX, is there a way to make it show up in Linux, because it isn't listed in GParted.

---

### Post by woonghee on 2009-06-11
Everything looks fine but I can't find recording menu.

---

### Post by GeneralTrue on 2009-06-11
I can truly confirm that this works=) is there a way to get custom themes?

---

### Post by days_of_ruin on 2009-06-11
The normal fuze firmware can't load my microSD card now. Must have corrupted it;_;

---

### Post by dragos240 on 2009-06-11
> **Goombie said:**
> When I do this, I connect using the Sansa firmware instead of Rockbox. Is that supposed to happen?

Otherwise, everything works fine so far. Is there a way to change the font size for the menus, though? I can't read them very well. >.<

Yep, that's normal. That's supposed to happen.

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> Oh crap, seems FAT is corrupted somehow. I can't mount it in Ubuntu. I had this problem before and I fixed it by formatting it in OSX, is there a way to make it show up in Linux, because it isn't listed in GParted.

Nope, nothing of the sort. the USB doesn't work on the firmware yet, don't panic. Just shut down the sansa, and plug it in, it will charge and connect using the original firmware.

---

### Post by dragos240 on 2009-06-11
> **woonghee said:**
> Everything looks fine but I can't find recording menu.

Voice and recording do not yet work on the fuze.

---

### Post by dragos240 on 2009-06-11
> **GeneralTrue said:**
> I can truly confirm that this works=) is there a way to get custom themes?

Yes they are general themes for rockbox, search "rockbox themes"

---

### Post by dragos240 on 2009-06-11
> **days_of_ruin said:**
> The normal fuze firmware can't load my microSD card now. Must have corrupted it;_;

Now can you boot into rockbox? If you can then go into files, and then ##PORT## you should be able to access your files from there.

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> Nope, nothing of the sort. the USB doesn't work on the firmware yet, don't panic. Just shut down the sansa, and plug it in, it will charge and connect using the original firmware.

Oh no the Rockbox firmware installed just fine, it just is that when I connect it I get an error message saying "FAT is corrupted. Please Connect device to a PC and recover FAT" 
Also it no longer shows up in Ubuntu, I can't mount it nor can I format it with GParted. 
It isn't listed in /dev/ either.

EDIT: I'll just ask a friend of mine who has a Mac to format it for me, for some reason OSX can still mount it. I just don't know how to do that in Linux if the device isn't listed.

---

### Post by days_of_ruin on 2009-06-11
> **dragos240 said:**
> Now can you boot into rockbox? If you can then go into files, and then ##PORT## you should be able to access your files from there.

In Port there in a bunch of wierdly named files and I can't do anything with them.

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> Oh no the Rockbox firmware installed just fine, it just is that when I connect it I get an error message saying "FAT is corrupted. Please Connect device to a PC and recover FAT" 
Also it no longer shows up in Ubuntu, I can't mount it nor can I format it with GParted. 
It isn't listed in /dev/ either.

EDIT: I'll just ask a friend of mine who has a Mac to format it for me, for some reason OSX can still mount it. I just don't know how to do that in Linux if the device isn't listed.

Hmm.... Thats odd. What are you using to connect, rockbox, or the original firmware? It would be appreciated. If it doesn't work, then I suggest finding the original firmware (which I can send you) and putting it in the sansa root directory. That may fix it.

---

### Post by dragos240 on 2009-06-11
> **days_of_ruin said:**
> In Port there in a bunch of wierdly named files and I can't do anything with them.

Such as?

---

### Post by days_of_ruin on 2009-06-11
EDIT: nvr mind

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> Hmm.... Thats odd. What are you using to connect, rockbox, or the original firmware? It would be appreciated. If it doesn't work, then I suggest finding the original firmware (which I can send you) and putting it in the sansa root directory. That may fix it.

Well I guess I am using the original firmware, at least that's what shows up when I connect it, once I disconnect the device Rockbox starts up. 

The problem is I can't mount the device, I just no longer shows up as a mountable device, it isn't listed anywhere. Because I can't mount it I can't put the old firmware on it either.

---

### Post by days_of_ruin on 2009-06-11
> **dragos240 said:**
> Such as?

oops I forgot I didn't have my microSD card in.

Ok I can access the files now but they are not in PORT, they are in something like "<microsd>".

Btw I want to be able to access the microsd card in the old firmware.

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> Well I guess I am using the original firmware, at least that's what shows up when I connect it, once I disconnect the device Rockbox starts up. 

The problem is I can't mount the device, I just no longer shows up as a mountable device, it isn't listed anywhere. Because I can't mount it I can't put the old firmware on it either.

Try this:
Shut down your sansa by holding the power switch up until it shuts down, much like you would to to a computer in the situation you needed a hard powerdown. And then plug it in.

---

### Post by dragos240 on 2009-06-11
> **days_of_ruin said:**
> oops I forgot I didn't have my microSD card in.

Ok I can access the files now but they are not in PORT, they are in something like "<microsd>".

Btw I want to be able to access the microsd card in the old firmware.

Okay, go into your old firmware (by of course shutting it down, and plugging it in, now put in your SD card.) It should work.

---

### Post by days_of_ruin on 2009-06-11
> **dragos240 said:**
> Okay, go into your old firmware (by of course shutting it down, and plugging it in, now put in your SD card. It should work.

Trying that again. Hopefully it will work this time.

---

### Post by dragos240 on 2009-06-11
> **days_of_ruin said:**
> Trying that again. Hopefully it will work this time.

I just noticed something! I forgot the other bracket XD

---

### Post by days_of_ruin on 2009-06-11
"Refreshing your media" always freezed 3/4 of the way thru.

---

### Post by dragos240 on 2009-06-11
> **days_of_ruin said:**
> "Refreshing your media" always **froze** 3/4 of the way **through**.

Odd..... I'll look up a firmware for you, okay?
[http://mp3support.sandisk.com/firmware/fuze/fuze01.01.11a.zip](http://mp3support.sandisk.com/firmware/fuze/fuze01.01.11a.zip)

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> Try this:
Shut down your sansa by holding the power switch up until it shuts down, much like you would to to a computer in the situation you needed a hard powerdown. And then plug it in.

That's the first thing I did, when I do that the old firmware shows up and shows the error about the FAT filesystem being corrupted. The only way to fix FAT is by formatting the whole device but for some reason Linux refuses to recognize usb devices with corrupted filesystems.

This is no big deal, it just happens sometimes when installing new firmware, I had this exact some problem before, all I need to do is format it using OSX, no idea why but OSX does mount corrupted FAT filesystems. It's just really annoying I don't know how to force Ubuntu to detect the device once it is connected.

---

### Post by days_of_ruin on 2009-06-11
> **dragos240 said:**
> Odd..... I'll look up a firmware for you, okay?
[http://mp3support.sandisk.com/firmware/fuze/fuze01.01.11a.zip](http://mp3support.sandisk.com/firmware/fuze/fuze01.01.11a.zip)

Dude thru is just shorthand.
I got it mounted on my computer so I am going to try and reformat it.
AFAIK FAT 32 would be the correct format?

EDIT: I'll try that firmware first.

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> That's the first thing I did, when I do that the old firmware shows up and shows the error about the FAT filesystem being corrupted. The only way to fix FAT is by formatting the whole device but for some reason Linux refuses to recognize usb devices with corrupted filesystems.

This is no big deal, it just happens sometimes when installing new firmware, I had this exact some problem before, all I need to do is format it using OSX, no idea why but OSX does mount corrupted FAT filesystems. It's just really annoying I don't know how to force Ubuntu to detect the device once it is connected.

I've mounted a few corrupted filesystems in my day and it works fine, must be something with your computer...

---

### Post by dragos240 on 2009-06-11
> **days_of_ruin said:**
> Dude thru is just shorthand.
I got it mounted on my computer so I am going to try and reformat it.
AFAIK FAT 32 would be the correct format?

err..... please don't. Just copy the firmware to your fuze. And you should be fine.
Also I know through is shorthand, but freezes isn't.

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> I've mounted a few corrupted filesystems in my day and it works fine, must be something with your computer...

Oh no, same story with every computer I've got, Linux and Windows. Besides a usb device with a corrupted filesystem is a bit different than a HDD for example.

If you know how to mount a corrupted usb device I would be very glad to hear it, would save me a lot of time. :)

---

### Post by days_of_ruin on 2009-06-11
> **dragos240 said:**
> err..... please don't. Just copy the firmware to your fuze. And you should be fine.
Also I know through is shorthand, but freezes isn't.

Yeah I realized that. Altho I think it is better grammar to put freezes instead of freezed/froze.

/off-topic

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> Oh no, same story with every computer I've got, Linux and Windows. Besides a usb device with a corrupted filesystem is a bit different than a HDD for example.

If you know how to mount a corrupted usb device I would be very glad to hear it, would save me a lot of time. :)

Err..... plug a device in.... and wait for nautilus to recognize it and it will give you an error, also it would help to know the /dev/ id that your sansa got. If so, you can force mount it.

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> Err..... plug a device in.... and wait for nautilus to recognize it and it will give you an error, also it would help to know the /dev/ id that your sansa got. If so, you can force mount it.

That's the problem, no error, and it isn't listed in /dev/ either (as far as I can tell). Just my HDD and nothing else.

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> That's the problem, no error, and it isn't listed in /dev/ either (as far as I can tell). Just my HDD and nothing else.

I meant if you had it before.

---

### Post by days_of_ruin on 2009-06-11
That old firmware worked, thanks;)

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> I meant if you had it before.

Oh I see, sorry. :) yeah I did have it before /dev/sdb

---

### Post by dragos240 on 2009-06-11
Find a guide on how to force a mount on linux, it should help. I'm too lazy right now.

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> Find a guide on how to force a mount on linux, it should help. I'm too lazy right now.

Woudn't force mounting only work if was listed in /dev/? which is not the case here.

---

### Post by dragos240 on 2009-06-11
> **Ebuntor said:**
> Woudn't force mounting only work if was listed in /dev/? which is not the case here.

So sdb isn't listed? Not even sdb1? It should still be in /dev

---

### Post by Ebuntor on 2009-06-11
> **dragos240 said:**
> So sdb isn't listed? Not even sdb1? It should still be in /dev

No, like I said a few posts back it isn't listed, that's the weird thing about it. Yeah of course if it was in /dev I could mount it, no problem. Strange thing is that if I star Virtualbox it is still listed and my virtual Windows install can detect it (it can't format it either unfortunately) 

But don't worry about it, like I said I had this problem before, I'll just find a Mac and format it in OSX like I did the last time.

---

### Post by Yes on 2009-06-11
So how many people have gotten it to work and how many people have bricked theirs?  I'd really really love to try this out but I'm scared of bricking it.

---

### Post by days_of_ruin on 2009-06-11
Reformated the micro sd card. Now it works with the latest firmware. :D

---

### Post by PatrickMoore on 2009-06-11
ok so after nearly bricking my player and recovering it, i found out some information.
  BEFORE YOU ATTEMPT TO INSTALL ROCKBOX
 check your firmware on your fuze.

if it starts with a 2 its the second release of the player and has different hardware specifications. 
  it may not work with yours.

trust me i went through a huge headache with mine which is of no fault of anyone but me but this is incompatable if its a version 2 fuze.

---

### Post by RPG Master on 2009-06-11
OK I did it, now how do I add music? When I go to the music folder its empty... when I have 6 gigs of music on there. 
And will using Rockbox drain my battery quicker?

---

### Post by Yes on 2009-06-11
> **PatrickMoore said:**
> ok so after nearly bricking my player and recovering it, i found out some information.
  BEFORE YOU ATTEMPT TO INSTALL ROCKBOX
 check your firmware on your fuze.

if it starts with a 2 its the second release of the player and has different hardware specifications. 
  it may not work with yours.

trust me i went through a huge headache with mine which is of no fault of anyone but me but this is incompatable if its a version 2 fuze.

And to determine if your Fuze is v1 or v2, from the main menu go to Settings -> System Settings -> Info.

I just installed it and it works great.  I love this interface way more than the standard Fuze one.

Thanks : D

e: Can't get Doom to work though.  It says it can't find the WAD file but I put the doom1.wad file in .rockbox/doom/. Oh well, I suppose that'll be fixed eventually.

And also after it boots the standard firmware for USB transfer, it freezes halfway through the refreshing media screen when you unplug it.  Just to a soft reset (hold the power button up for about 15 seconds) and it turns off, when you turn it back on it boots Rockbox like normal.

---

### Post by PatrickMoore on 2009-06-11
> **Yes said:**
> And to determine if your Fuze is v1 or v2, from the main menu go to Settings -> System Settings -> Info.

I just installed it and it works great.  I love this interface way more than the standard Fuze one.

Thanks : D

did you install on a version 2 fuze?
because if you did please help me out

---

### Post by days_of_ruin on 2009-06-11
> **RPG Master said:**
> OK I did it, now how do I add music? When I go to the music folder its empty... when I have 6 gigs of music on there. 
And will using Rockbox drain my battery quicker?

I don't remember exactly but there is somewhere you go and it asks if you
want to create a database.

---

### Post by cooltomcat on 2009-06-12
Many thanks to dragos 240 for this howto!
This works fine on my fuze 8GB with external 2GB card.

---

### Post by Yes on 2009-06-12
> **days_of_ruin said:**
> I don't remember exactly but there is somewhere you go and it asks if you
want to create a database.

Just go from the mainmenu to Database and it'll ask you if you want to create one if it doesn't already exist.

@PatrickMoore - sorry, mine's a v1 Fuze.

---

### Post by GeneralTrue on 2009-06-12
all the gbc games in rockboy are very very very very slow what can i do? or is it cause this is no offical release

---

### Post by clonne4crw on 2009-06-12
Ok. I just installed Rockbox on my Rev 1 Fuze. It only does audio, but it is VERY good at it. I am now addicted to Tetris.

The question about the Music folder being empty. This happened to me, I have to first browse into the /##MUSIC##/ folder to see anything on it.

Secondly, Rockbox ONLY does audio, not video, so I figured out that by HOLDING DOWN [<<] (the reverse key) on bootup (before the Rockbox logo appears), it will boot the Sansa firmware.

Have fun!

---

### Post by Yes on 2009-06-12
I got Doom to work!  I had missed one of the .wad files on the Wiki page (rockdoom.wad), I just copied that over and it works great.  Except I don't think the Fuze has enough buttons, cause I can't figure out how to jump.

Oh and Pacman is a pain cause all the buttons are rotated 90 degrees from what you think they should do.

---

### Post by ktp on 2009-06-12
> **PatrickMoore said:**
> did you install on a version 2 fuze?
because if you did please help me out

Looking here might help...but seems like not many people have tried v2.

[http://www.rockbox.org/twiki/bin/view/Main/SansaAMS](http://www.rockbox.org/twiki/bin/view/Main/SansaAMS)

---

### Post by dragos240 on 2009-06-12
> **clonne4crw said:**
> Ok. I just installed Rockbox on my Rev 1 Fuze. It only does audio, but it is VERY good at it. I am now addicted to Tetris.

The question about the Music folder being empty. This happened to me, I have to first browse into the /##MUSIC##/ folder to see anything on it.

Secondly, Rockbox ONLY does audio, not video, so I figured out that by HOLDING DOWN [<<] (the reverse key) on bootup (before the Rockbox logo appears), it will boot the Sansa firmware.

Have fun!

Let me explain this. The ##MUSIC## folder is the folder that is shown when MTP mode is activated, it's where all your music goes.

---

### Post by dragos240 on 2009-06-12
And the v2 has a COMPLETELY different hardware set, and it WILL NOT work with this, do not try. YOU WILL FAIL AND MOST LIKELY GET YOUR FUZE V2 BRICKED!!!!!!! Just thought I would state that.

---

### Post by Yes on 2009-06-12
Dragos how did you compile Rockbox?  I keep getting the error '/usr/bin/arm-elf-ld: this linker was not configured to use sysroots' when I run make.

e: Maybe it's got something to do with the export line in my .bashrc?  I think that's supposed to make it use a different version of arm-elf-gcc in /usr/local instead of /usr/bin but I'm not sure.  The line is 'export PATH=$PATH:/usr/local/arm-elf/bin'.  Is that right?

---

### Post by Vostrocity on 2009-06-12
Wow I'm surprised this many people have Sansas.

---

### Post by NFblaze on 2009-06-12
> **Vostrocity said:**
> Wow I'm surprised this many people have Sansas.

Well, I think it's because its carried in alot of the major stores which gives it exposure. Also, I bought mine in Kuwait, and I've seen it in a couple of other countries. 

When I was working at a popular retail shop, when the parents came in and inquired about ipods, and then promptly fainted after they saw the price, once we revived them we showed them the Sandisk products, which pretty muched packed more features in it and was alot cheaper.

Also, this is a Linux forum. Sansa Fuze supports Ogg and FLAC and is Linux friendly because of selectable USB modes and drag and drop support. 

Did I mention it packs alot more than an ipod and is cheaper.

---

### Post by Vostrocity on 2009-06-12
Yea I guess the main reason is that this is a Linux forum. But in the real world, I probably see 1 Sansa for every 100 iPods. Anyhow it's still the best-selling non-iPod player. I actually have both a Sansa e200 and a 2nd gen Nano, and I like the Sansa with Rockbox better.

---

### Post by PatrickMoore on 2009-06-13
> **dragos240 said:**
> And the v2 has a COMPLETELY different hardware set, and it WILL NOT work with this, do not try. YOU WILL FAIL AND MOST LIKELY GET YOUR FUZE V2 BRICKED!!!!!!! Just thought I would state that.

there is a solution if you are overly ambitious and a bit reckless like me

format via gparted if you get a fat error or it locks up.

seriously worked for me and recovered the original fuze firmware too

---

### Post by DoctorMO on 2009-06-13
I wonder if this works without an SD Card, if not that should be in the instructions.

I just tried this with my Sana Fuze and it wouldn't even mount, MTP mode works fine, but MSC fails to even register with linux at all.

---

### Post by GeneralTrue on 2009-06-13
> **DoctorMO said:**
> I wonder if this works without an SD Card, if not that should be in the instructions.

I just tried this with my Sana Fuze and it wouldn't even mount, MTP mode works fine, but MSC fails to even register with linux at all.

i`m not using a sd card and its working



ALSO   ANYONE THAT INSTALLED ROCKBOX ON THEIR FUZE  IS THE ROCKBOY ALSO SLOW FOR YOU? LIKE UNPLAYABLE?

---

### Post by Yes on 2009-06-13
> **GeneralTrue said:**
> i`m not using a sd card and its working



ALSO   ANYONE THAT INSTALLED ROCKBOX ON THEIR FUZE  IS THE ROCKBOY ALSO SLOW FOR YOU? LIKE UNPLAYABLE?

It's not slow for me, but how are you using all the buttons?  You need up, down, left, right, A, B, start, and select.  The Fuze is missing two.  Or can you do combinations, like up and down for B?

---

### Post by Changturkey on 2009-06-13
This only works with V1 players right? Because there's a V2 of the Fuze and Clip.

---

### Post by dragos240 on 2009-06-13
> **Changturkey said:**
> This only works with V1 players right? Because there's a V2 of the Fuze and Clip.

Yep only with v1.

---

### Post by hyperdude111 on 2009-06-13
I bought a V1 player today and want to do this.

1. Is this possible to undo if something goes wrong.
2. Does this replace the actual firmware?
3. If I prefer fuze firmware can i switch back? 

Tanks

Don't worry, after research I found out all the info I need.

---

### Post by GeneralTrue on 2009-06-13
> **Yes said:**
> It's not slow for me, but how are you using all the buttons?  You need up, down, left, right, A, B, start, and select.  The Fuze is missing two.  Or can you do combinations, like up and down for B?

Well i tried to set all buttons but as you just said.we just dont have enough buttons    but i could not test it in game as its too slow . how did you get it fast like   what do you do? which games do you play?


and anyone who wants too share their experience with rockbox on the fuze and figure out solutions for problems please add me [email]xgeneraltruex@hotmail.com[/email]

---

### Post by Yes on 2009-06-13
> **GeneralTrue said:**
> Well i tried to set all buttons but as you just said.we just dont have enough buttons    but i could not test it in game as its too slow . how did you get it fast like   what do you do? which games do you play?


and anyone who wants too share their experience with rockbox on the fuze and figure out solutions for problems please add me [email]xgeneraltruex@hotmail.com[/email]

I just found some random ROMs online to try it out.  I think it was Street Racer or something.

I found a patch (after making my own lol) that fixes the button for Pacbox, I can't stop playing that game now.

---

### Post by GeneralTrue on 2009-06-14
> **Yes said:**
> I just found some random ROMs online to try it out.  I think it was Street Racer or something.

I found a patch (after making my own lol) that fixes the button for Pacbox, I can't stop playing that game now.

What do you mean with fixing the buttons? and where can i get that patch?

---

### Post by Yes on 2009-06-14
With the current source, the screen tilts 90 degrees but the buttons don't, so when you hold it so the screen is right way up the buttons are all screwed up (left doesnt go left, up doesnt go up, its all very confusing).  The patch fixing that is here: [=4&sev[0]=&pri[0]=&due[0]=&reported[0]=&cat[0]=&status[0]=open&percent[0]=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto="]here]("http://www.rockbox.org/tracker/task/10235?string=pacbox&project=1&search_name=&type[0).  You'll have to recompile Rockbox though, but that is really quite simple.

If you do compile it again, the devs recommend using a version prior to 21227, as versions after that have had random file corruption and other nasty stuff.  Just grab the 21212 source from here [http://www.rockbox.org/dl.cgi?bin=source](http://www.rockbox.org/dl.cgi?bin=source)

---

### Post by dragos240 on 2009-06-14
> **hyperdude111 said:**
> I bought a V1 player today and want to do this.

1. Is this possible to undo if something goes wrong.
2. Does this replace the actual firmware?
3. If I prefer fuze firmware can i switch back? 

Tanks

Don't worry, after research I found out all the info I need.

1. Most likely.
2. No it does not.
3, Yes of course, just turn off the rockbox, and plug it in to your charger, and load the original sansa firmware.

---

### Post by GeneralTrue on 2009-06-14
> **dragos240 said:**
> 1. Most likely.
2. No it does not.
3, Yes of course, just turn off the rockbox, and plug it in to your charger, and load the original sansa firmware.



1.Can you load the rockboy and spectrum games normaly?
2.If yes what about the controls? there are not enough buttons
3.Will the official release of rockbox for the sansa fuze be better and fix the bugs that are in it right now?

thanks in advance for reading.:popcorn:

---

### Post by Yes on 2009-06-14
> **GeneralTrue said:**
> 1.Can you load the rockboy and spectrum games normaly?
2.If yes what about the controls? there are not enough buttons
3.Will the official release of rockbox for the sansa fuze be better and fix the bugs that are in it right now?

thanks in advance for reading.:popcorn:

1. Yes for rockboy.  I dunno about spectrum games, I suppose I'll try that tonight and let you know how it goes.
2. Yeah, I don't see how you can play Gameboy games on a Fuze.  But according to the Wiki you only need five buttons for the Spectrum, so that should definitely be doable.
3.  Of course!  That'll be a little while though.  Right now they're still running into some major problems (i.e. random file system corruption on some of the more recent daily builds) but as they work those out they'll move on to address the bugs and add some more features.

---

### Post by dragos240 on 2009-06-14
Wow 113 posts? Thats a heck of a lot of people that want rockbox in their fuze!

---

### Post by GeneralTrue on 2009-06-14
> **Yes said:**
> 1. Yes for rockboy.  I dunno about spectrum games, I suppose I'll try that tonight and let you know how it goes.
2. Yeah, I don't see how you can play Gameboy games on a Fuze.  But according to the Wiki you only need five buttons for the Spectrum, so that should definitely be doable.
3.  Of course!  That'll be a little while though.  Right now they're still running into some major problems (i.e. random file system corruption on some of the more recent daily builds) but as they work those out they'll move on to address the bugs and add some more features.


Oke thanks lemme know about the spectrum cause i can only load 1 spectrum game until now  but i heard i need SNA files but i cannot get them at WORLD OF SPECTRUM

---

### Post by hyperdude111 on 2009-06-14
Oh yeh i found out that this is a dualboot. So if you want to boot sansa firmware then press "|<<" or "left" key during boot and it will boot sansa.

---

### Post by Yes on 2009-06-14
> **GeneralTrue said:**
> Oke thanks lemme know about the spectrum cause i can only load 1 spectrum game until now  but i heard i need SNA files but i cannot get them at WORLD OF SPECTRUM

I've tried the .tap file for RainbowIsland and that didn't work, it froze after loading to 99%.  The .tzx file loaded to 100% but then seemed to freeze.

As I understand it, .sna files are like saved games.  If you want to load a preexisting game you can use an .sna file, but you don't need them.

Waaaaaaiiiiit the .tzx file just loaded.  Kinda.  I'm at the starting screen now but it says it's 99% loaded. It drew the screen really slowly though, I'm thinking it might run too slowly to actually play anything.

I'm gonna fiddle around and see if I can get it to do anything.

e: Can anyone suggest me some decent ZX Spectrum games I could try?

---

### Post by cubeist on 2009-06-14
Thank You Dragos240.

Worked perfectly on my v1...took less than 3minutes including the d/l!

After unpluging it I got a message on my fuze saying "Firmware upgrade in progress"

So I didn't turn it off, just waited for the 'upgrade' to finish, then it automatically rebooted itself into Rockbox...very cool!

Radio works too!

Edit - 
RB won't boot if I have the external microSD card in the slot... it just goes to the rockbox loading screen and freezes.  But if I boot without the microSD in, it boots fine, and then I can insert the card and the contents are accessible in the database.

---

### Post by Yes on 2009-06-14
Gah it turns out that number was the speed.  Ooops.

Now I've got to figure out how to map the keys...

e: It appears that once you start the game, you can just use up for up, left for left, etc. and select for shoot/jump.  The problem is a lot of games expect you to press "Space" or "Enter" to start the actual game, and I can't figure out how to get past this.  If anyone finds something, please let me know.

e2: There's a virtual keyboard that you can use to press Enter.  For some reason space doesn't work, which is really a pain cause that seems to be all I need to start the game...

e3: I selected a random blank spot on the virtual keyboard and was able to start the game.  Once I started the game though, none of the controls seemed to work.  Perhaps it's just buggy.

e4: Yeah, this game seems very buggy.  Sometimes I can go into the virtual keyboard and press q to jump (it's a moon buggy kinda game), but other times it doesn't work.  And mapping the up button to q never works.  I'm gonna try a different game.

---

### Post by dragos240 on 2009-06-14
> **hyperdude111 said:**
> Oh yeh i found out that this is a dualboot. So if you want to boot sansa firmware then press "|<<" or "left" key during boot and it will boot sansa.

Cool! I didn't even know that!

---

### Post by GeneralTrue on 2009-06-14
> **Yes said:**
> Gah it turns out that number was the speed.  Ooops.

Now I've got to figure out how to map the keys...

e: It appears that once you start the game, you can just use up for up, left for left, etc. and select for shoot/jump.  The problem is a lot of games expect you to press "Space" or "Enter" to start the actual game, and I can't figure out how to get past this.  If anyone finds something, please let me know.

e2: There's a virtual keyboard that you can use to press Enter.  For some reason space doesn't work, which is really a pain cause that seems to be all I need to start the game...

e3: I selected a random blank spot on the virtual keyboard and was able to start the game.  Once I started the game though, none of the controls seemed to work.  Perhaps it's just buggy.

e4: Yeah, this game seems very buggy.  Sometimes I can go into the virtual keyboard and press q to jump (it's a moon buggy kinda game), but other times it doesn't work.  And mapping the up button to q never works.  I'm gonna try a different game.


yeah ive played around with the spectrum allot but it just doesnt seem to work   btw try out DIGGER thats the only one that works for me  completly      all the others just wont start

---

### Post by Yes on 2009-06-14
Well most of mine will start, I just can't get the buttons to do anything.

I'm just gonna give up for now and try again later.  I'm assuming they'll address that later on.

---

### Post by dragos240 on 2009-06-14
> **Yes said:**
> Well most of mine will start, I just can't get the buttons to do anything.

I'm just gonna give up for now and try again later.  I'm assuming they'll address that later on.

Your buttons don't work? Elaborate. Do you have a v2?

---

### Post by GeneralTrue on 2009-06-15
> **dragos240 said:**
> Your buttons don't work? Elaborate. Do you have a v2?


He ment the buttons in the spectrum games.i have the same problem and have a v1 so he probaly does too.   what about you dragos does it work for you?

---

### Post by dragos240 on 2009-06-15
> **GeneralTrue said:**
> He ment the buttons in the spectrum games.i have the same problem and have a v1 so he probaly does too.   what about you dragos does it work for you?

They work fine for me :/

---

### Post by Yes on 2009-06-15
You can play ZX Spectrum games and the buttons and everything works fine?  What Rockbox version are you using?  Could you link me to the .txz files you're using?

---

### Post by GeneralTrue on 2009-06-15
> **dragos240 said:**
> They work fine for me :/


yeah which spectrum games are you using from which web

---

### Post by dragos240 on 2009-06-15
> **GeneralTrue said:**
> yeah which spectrum games are you using from which web

I thought you meant the normal games. No I don't think I have any on mine, aside from that, the version I gave you guys isn't stable, so some things may not work. Sorry for the misunderstanding.

---

### Post by GeneralTrue on 2009-06-15
> **dragos240 said:**
> I thought you meant the normal games. No I don't think I have any on mine, aside from that, the version I gave you guys isn't stable, so some things may not work. Sorry for the misunderstanding.


Ow thanks for informing us  so we can still look forward too the official release of rockbox for the sansa fuze;p

---

### Post by Yes on 2009-06-15
Yeah if the version dragos packaged was 21228 or later you really shouldn't be using it, there's been some really nasty problems.  And they're random, so just because everyting seems fine doesn't mean you won't turn it on next time to find it's corrupted your file system and you've lost all your music.

I've got to run out, but I'll post the .zip for the version I'm using (21212 or something), that should be safe to use.

---

### Post by dragos240 on 2009-06-15
Hmm.... It hasn't had any issues so far except for no USB

---

### Post by GeneralTrue on 2009-06-15
o but if it corrupts does that mean i cant use my fuze at all anymore or that i will just lose my music? cause i got my music backed up.    but i would  love for you too post your version yes.

---

### Post by dragos240 on 2009-06-15
> **GeneralTrue said:**
> o but if it corrupts does that mean i cant use my fuze at all anymore or that i will just lose my music? cause i got my music backed up.    but i would  love for you too post your version yes.

It all depends, but it has a high chance of bricking if installed incorrectly, and as of now, there is no way of unbricking a fuze yet.

---

### Post by GeneralTrue on 2009-06-15
> **dragos240 said:**
> It all depends, but it has a high chance of bricking if installed incorrectly, and as of now, there is no way of unbricking a fuze yet.

whats the wrong way of having it installed if you know? i dont want to get rid of my rockbox anymore now i have it cause its so wonderfull

---

### Post by dragos240 on 2009-06-15
> **GeneralTrue said:**
> whats the wrong way of having it installed if you know? i dont want to get rid of my rockbox anymore now i have it cause its so wonderfull

Well, if it works, you don't have to worry, it occurs WHEN installing it. You should be fine.

---

### Post by Yes on 2009-06-15
I don't think that's right.  I'm not sure if they're serious enough to brick it, but they said that you should be using build 21227 or earlier.  They said that they're completely random issues, so even if it seems to be working fine you could randomly have problems.

I'm not sure on that though.  You may be ok if it installed fine.  Anyway, here's build 21197, which should be perfectly fine (barring any normal pre-release issues): [http://www.megaupload.com/?d=3HV4LBKJ](http://www.megaupload.com/?d=3HV4LBKJ)

Also, does anyone know of any good themes for the Fuze?

e: That .zip also has the patched Pacbox.

---

### Post by GeneralTrue on 2009-06-15
> **Yes said:**
> I don't think that's right.  I'm not sure if they're serious enough to brick it, but they said that you should be using build 21227 or earlier.  They said that they're completely random issues, so even if it seems to be working fine you could randomly have problems.

I'm not sure on that though.  You may be ok if it installed fine.  Anyway, here's build 21197, which should be perfectly fine (barring any normal pre-release issues): [http://www.megaupload.com/?d=3HV4LBKJ](http://www.megaupload.com/?d=3HV4LBKJ)

Also, does anyone know of any good themes for the Fuze?

e: That .zip also has the patched Pacbox.


i know that you can use all the [iriver H3xx]("http://themes.rockbox.org/index.php?target=h300")  and [iPod Color/Photo]("http://themes.rockbox.org/index.php?target=ipodcolor")   themes cause they are the same screen size  i do that too.  i`m gonna try out that build now thank you kindly   edit also the roms are still slow for me  should i just throw away the old rockbox folder and replace it with yours?

---

### Post by dragos240 on 2009-06-15
> **Yes said:**
> I don't think that's right.  I'm not sure if they're serious enough to brick it, but they said that you should be using build 21227 or earlier.  They said that they're completely random issues, so even if it seems to be working fine you could randomly have problems.

I'm not sure on that though.  You may be ok if it installed fine.  Anyway, here's build 21197, which should be perfectly fine (barring any normal pre-release issues): [http://www.megaupload.com/?d=3HV4LBKJ](http://www.megaupload.com/?d=3HV4LBKJ)

Also, does anyone know of any good themes for the Fuze?

e: That .zip also has the patched Pacbox.

Well the official page says that it can and will if installed incorrectly, see the link:
[http://www.rockbox.org/twiki/bin/view/Main/SansaAMS](http://www.rockbox.org/twiki/bin/view/Main/SansaAMS)

> 
**Unbricking **

 It's possible to [COLOR=#ff0000]brick[/COLOR] an AMS Sansa by running faulty code.  E200v2's can be put in a recovery mode by shorting a couple of pins on the PCB, see the [SansaE200v2]("http://www.rockbox.org/twiki/bin/view/Main/SansaE200v2") page for details, or see [http://www.anythingbutipod.com/forum/showpost.php?p=281975&postcount=3](http://www.anythingbutipod.com/forum/showpost.php?p=281975&postcount=3) 
 Other AMS Sansas can also get into this mode, but [COLOR=#ff0000]can not be unbricked[/COLOR] this way (they present an USB disk of size 0 that cannot be written). 



---

### Post by xuCGC002 on 2009-06-15
Quick question- does rockbox support the FM radio? I know I can just switch back to the normal fuze firmware, but just asking.

---

### Post by dragos240 on 2009-06-15
> **xuCGC002 said:**
> Quick question- does rockbox support the FM radio? I know I can just switch back to the normal fuze firmware, but just asking.

Yes, but it counts by fives, so not really >.<

---

### Post by Yes on 2009-06-15
Problems caused by installing it incorrectly and the random problems from using one of the recent builds are different.  I don't know if the random problems can brick it, all I'm saying is when the devs tell you you shouldn't be using a certian version, you probably shouldn't use it.

My FM radio works fine.  It counts by .05 if you don't have any presets, but I don't know why you would need to count by anything less than that.

Thanks GeneralTune, those themes work great : D

---

### Post by dragos240 on 2009-06-15
> **Yes said:**
> Problems caused by installing it incorrectly and the random problems from using one of the recent builds are different.  I don't know if the random problems can brick it, all I'm saying is when the devs tell you you shouldn't be using a certian version, you probably shouldn't use it.

My FM radio works fine.  It counts by .05 if you don't have any presets, but I don't know why you would need to count by anything less than that.

Thanks GeneralTune, those themes work great : D

Then how can I get to 90.9 wbur?

---

### Post by cubeist on 2009-06-15
> **dragos240 said:**
> Then how can I get to 90.9 wbur?

Mine counts by .05 as well... so 90.9 would be between 90.85 and 90.95 :mrgreen:

---

### Post by Yes on 2009-06-15
> **dragos240 said:**
> Then how can I get to 90.9 wbur?

Make sure you don't have it autoscan, or else it might miss some stations and since it only tunes to the presets you won't be able to get to anything it missed.

Just curious, anyone know where you can get more fonts?

---

### Post by GeneralTrue on 2009-06-16
> **Yes said:**
> Make sure you don't have it autoscan, or else it might miss some stations and since it only tunes to the presets you won't be able to get to anything it missed.

Just curious, anyone know where you can get more fonts?


The way i got more fonts is by downloading the orginal rockbox installer and i just installed all the fonts with that progam

---

### Post by clonne4crw on 2009-06-16
> **dragos240 said:**
> Let me explain this. The ##MUSIC## folder is the folder that is shown when MTP mode is activated, it's where all your music goes.
Ahh. Makes sense to me. Was wondering why that was.

---

### Post by clonne4crw on 2009-06-16
> **Vostrocity said:**
> Wow I'm surprised this many people have Sansas.

Because they're more awesome than some stupid, overpriced iPod. Over the past few years, I've been able to convince at least 4 other friends to go with the Fuze instead of the Nano.

---

### Post by clonne4crw on 2009-06-16
> **hyperdude111 said:**
> I bought a V1 player today and want to do this.

1. Is this possible to undo if something goes wrong.
2. Does this replace the actual firmware?
3. If I prefer fuze firmware can i switch back? 

Tanks

Don't worry, after research I found out all the info I need.

1) yes, it is. Just install the Fuze firmware like it's an upgrade.
2) No, it sits on top of the Fuze fw.
3)Yes, just hold down the REV (<<) button on bootup.

---

### Post by Schaep on 2009-06-16
Hi all
I want to install rockbox on my fuze as well, but i've got a few questions first. You have a zip file at the original post, and a much smaller .rar file on the previous page. Which one should I use? Is the one from the previous page not yet prepared, like the one at the original post, where you can just copy the folder to the root( right?) ?

---

### Post by GeneralTrue on 2009-06-16
> **Schaep said:**
> Hi all
I want to install rockbox on my fuze as well, but i've got a few questions first. You have a zip file at the original post, and a much smaller .rar file on the previous page. Which one should I use? Is the one from the previous page not yet prepared, like the one at the original post, where you can just copy the folder to the root( right?) ?

use the one a page back which yes has posted.

---

### Post by Schaep on 2009-06-17
And I can just extract the folder to the root of my fuze, without any other preps?

---

### Post by GeneralTrue on 2009-06-17
> **Schaep said:**
> And I can just extract the folder to the root of my fuze, without any other preps?

yeah just extract it and let it do the firmware update. if you get a error when you start your fuze up just put old sansa firmware over it too restore it.

---

### Post by Schaep on 2009-06-17
So, I extracted the folder to my Fuze (and it's in MSC), but I don't get rockbox when I reboot. What did I do wrong?

---

### Post by GeneralTrue on 2009-06-17
> **Schaep said:**
> So, I extracted the folder to my Fuze (and it's in MSC), but I don't get rockbox when I reboot. What did I do wrong?


I`m sorry    on the first page download that file too BUT DONT USE THE ROCKBOX FOLDER ON THAT ONE  use the other file thats in it and put it on your fuze and use the rockbox folder on the 14th page.that way it will do a firmware update.

---

### Post by Schaep on 2009-06-17
Yes.
Edit: Just read your edit. Will try that.
And it worked. Thanks a mil.

---

### Post by GeneralTrue on 2009-06-17
> **Schaep said:**
> Yes.
Edit: Just read your edit. Will try that.
And it worked. Thanks a mil.

Your welcome enjoy =DD  make sure you used the rockbox folder off the link on page 14 and the firmware updater on the first page or else you could run into problems

---

### Post by OMIGHTY1 on 2009-06-21
When I didn't put the .rockbox folder on, it actually showed a screen saying Rockbox, and said it could find some file. When I tried the .rockbox file (from page 14), it just says "refreshing media". What am I doing wrong?

---

### Post by dragos240 on 2009-06-21
> **OMIGHTY1 said:**
> When I didn't put the .rockbox folder on, it actually showed a screen saying Rockbox, and said it could find some file. When I tried the .rockbox file (from page 14), it just says "refreshing media". What am I doing wrong?


Good news:
You installed the bootloader,

Bad news:
the .rockbox directory isn't there.

More good news:
It's fixable, and easily too. On bootup, hold the left button "<<|" or something, i will boot up into the original firmware, now set it to MSC and try extracting the archive again.

---

### Post by Yes on 2009-06-21
> **OMIGHTY1 said:**
> When I didn't put the .rockbox folder on, it actually showed a screen saying Rockbox, and said it could find some file. When I tried the .rockbox file (from page 14), it just says "refreshing media". What am I doing wrong?

Is it the normal "Refreshing media" that the Fuze shows after you put something on it?  Try just pushing the power button up for 10 seconds or so until it turns off and then turn it back on and Rockbox should boot normally.

---

### Post by OMIGHTY1 on 2009-06-21
> **dragos240 said:**
> Good news:
You installed the bootloader,

Bad news:
the .rockbox directory isn't there.

More good news:
It's fixable, and easily too. On bootup, hold the left button "<<|" or something, i will boot up into the original firmware, now set it to MSC and try extracting the archive again.

Well, it now goes to the screen with the Rockbox logo on it, and has text on the top that says:
"Loading firmware
File not found"
What do I have to do now?

[Edit]: Oh, and I do have it in the MSC mode.

---

### Post by dragos240 on 2009-06-21
> **OMIGHTY1 said:**
> Well, it now goes to the screen with the Rockbox logo on it, and has text on the top that says:
"Loading firmware
File not found"
What do I have to do now?
Hmm......

Do you know if it's a v1 or v2 before we go any further? If you don't boot into the oiginal firmware and go into system information, if it says 2.??.? it's v2, and I can't help you, if it's 1.??.? then I can help you.

---

### Post by OMIGHTY1 on 2009-06-21
> **dragos240 said:**
> Hmm......

Do you know if it's a v1 or v2 before we go any further? If you don't boot into the oiginal firmware and go into system information, if it says 2.??.? it's v2, and I can't help you, if it's 1.??.? then I can help you.

I have V01.02.26A

---

### Post by dragos240 on 2009-06-21
> **OMIGHTY1 said:**
> I have V01.02.26A

Okay. You can run this and I can help you. Now, just give me a screenshot of that directory with hidden items enabled, with a graphical file manager like nautilus or dolhpin.

---

### Post by OMIGHTY1 on 2009-06-21
Ermm... I'm currently in Windoze XP.

---

### Post by dragos240 on 2009-06-21
> **OMIGHTY1 said:**
> Ermm... I'm currently in Windoze XP.


Well thats your problem..... go to a linux machine.

---

### Post by OMIGHTY1 on 2009-06-21
lol, another problem that XP creates! I'll boot to Ubuntu when I get home. Dang, I've gotta remember to reinstall that...:lolflag:

---

### Post by GeneralTrue on 2009-06-22
> **OMIGHTY1 said:**
> lol, another problem that XP creates! I'll boot to Ubuntu when I get home. Dang, I've gotta remember to reinstall that...:lolflag:

You can also make a screenshot of the folder with windows xp..... just press the print screen button then go too paint and hold the CTRL button and then press V

---

### Post by OMIGHTY1 on 2009-06-23
> **GeneralTrue said:**
> You can also make a screenshot of the folder with windows xp..... just press the print screen button then go too paint and hold the CTRL button and then press V

Heh, XP even makes screenshots harder!

---

### Post by OMIGHTY1 on 2009-06-23
> **dragos240 said:**
> Well thats your problem..... go to a linux machine.

Will Mac work, since it's Unix?

---

### Post by OMIGHTY1 on 2009-06-23
It worked on the Mac! :lolflag:

---

### Post by GeneralTrue on 2009-06-24
> **OMIGHTY1 said:**
> It worked on the Mac! :lolflag:


Aint you happy now    NOW POST THE SCREEN=D:popcorn:

---

### Post by miggols99 on 2009-06-24
Is this going to support USB? When I plug it in when it is in Rockbox, it freezes. I can still copy files when I turn it off and plug it in though...

---

### Post by GeneralTrue on 2009-06-24
> **miggols99 said:**
> Is this going to support USB? When I plug it in when it is in Rockbox, it freezes. I can still copy files when I turn it off and plug it in though...


Just turn your fuze off totaly and plug it into usb.

---

### Post by dragos240 on 2009-06-24
> **GeneralTrue said:**
> Just turn your fuze off totaly and plug it into usb.

OR turn it off completely and  hold the left button on boot.

---

### Post by GeneralTrue on 2009-06-25
> **dragos240 said:**
> OR turn it off completely and  hold the left button on boot.


Yeah that will get you into the orginal firmware but its not needed if you just want to put some stuff on your sansa fuze.

---

### Post by Gryphen on 2009-06-25
Can't you just format a v2 and install an older firmware and then install Rockbox?

---

### Post by dragos240 on 2009-06-25
> **Gryphen said:**
> Can't you just format a v2 and install an older firmware and then install Rockbox?

It's not the firmware, it's the hardware, it's completely different than a v1's hardware, therefore it won't work.

---

### Post by Gryphen on 2009-06-25
> **dragos240 said:**
> It's not the firmware, it's the hardware, it's completely different than a v1's hardware, therefore it won't work.
Will there be a version of rockbox for the v2

---

### Post by Yes on 2009-06-25
> **Gryphen said:**
> Will there be a version of rockbox for the v2

They're working on it, they'll have it eventually.

---

### Post by Gryphen on 2009-06-25
Is the V2 hardware better?
Will there be video support?
And how long will it take for them to release it?

---

### Post by dragos240 on 2009-06-26
> **Gryphen said:**
> Is the V2 hardware better?
Will there be video support?
And how long will it take for them to release it?

Until a stable one? Probably half of a year or something, and even by then there will be bugs.

---

### Post by GeneralTrue on 2009-06-28
> **Gryphen said:**
> Is the V2 hardware better?
Will there be video support?
And how long will it take for them to release it?


There is mpeg video support only.

---

### Post by curu on 2009-06-29
Hi, thanks for the archives, it worked for me. DO you run it with a SD card plugged ? I can't, Rockbox seems to block at the logo start. Maybe a more recent build could fix it ?

Regards

---

### Post by GeneralTrue on 2009-06-29
> **curu said:**
> Hi, thanks for the archives, it worked for me. DO you run it with a SD card plugged ? I can't, Rockbox seems to block at the logo start. Maybe a more recent build could fix it ?

Regards


Is the rockbox folder on the like uhmm 15th page or something and then use the other file that will update your firmware on page 1. then let it update and reboot.and no you do not need the sd card.

---

### Post by curu on 2009-06-29
Hum yes I used the fuzea.bin from the file on the first page and the rockbox folder from the 14th page file. It works nicely, if I have removed the 8 Go micro SD card. My problem is with this SD card Rockbox don't run properly and blocks at the start.

---

### Post by curu on 2009-06-29
Well I tried some manips and it seems it works and recognizes the SD card when I hotplug it when rockbax has started. With it already plugged Rockbox blocks.

---

### Post by dragos240 on 2009-06-29
> **curu said:**
> Well I tried some manips and it seems it works and recognizes the SD card when I hotplug it when rockbax has started. With it already plugged Rockbox blocks.

Your english is abeit broken, although I think I can make it out. The usb connection is broken on the rockbox, turn your rockbox off and plug the usb cord into your fuze, it will recognize it.

---

### Post by GeneralTrue on 2009-06-30
> **dragos240 said:**
> Your english is abeit broken, although I think I can make it out. The usb connection is broken on the rockbox, turn your rockbox off and plug the usb cord into your fuze, it will recognize it.


The sd card never ever seemed too work for me not even with the orginal fuze software

---

### Post by curu on 2009-06-30
Well I think my english is more broken than you thought. I have no problems to recognize the SD card when I plug the Fuze on the pc. My problem is with the Fuze itself when the SD card is inserted within. In this case Rockbox freezes at the start, when the logo is displayed.

The workaround I found to use the SD card on the player is to boot Rockbox without having the SD inserted and then insert the SD when the boot ends to the general menu. This way the SD card is recognized by the player although sometimes it also freezes on this step.

---

### Post by Coldbird on 2009-07-03
I developed a easy way for Sansa Fuze users to stay up 2 date with the Rockbox SVN...

[http://coldbird.celes-network.de/rockboxfuze/index.php](http://coldbird.celes-network.de/rockboxfuze/index.php)

I doubt it needs a explanation. Have fun guys.):P

---

### Post by dragos240 on 2009-07-03
Good job. I would be too lazy to do that. Thanks coldbird!

---

### Post by dragos240 on 2009-07-03
EDIT, coldbird, your link has been added to the first page.

---

### Post by Coldbird on 2009-07-03
I feel honored.:popcorn:
The page should be easy to use - when a new SVN version is out... just load the rebuild page on it and a whole new version will get compiled and packaged.

The script automatically compiles the bootloader and applies it to the latest official sansa software and packs the newly compiled rockbox firmware + bootloader installer + readme + latest official sansa firmware for uninstalling into a rar file.

But I suppose you know that already.

---

### Post by doorknob60 on 2009-07-03
Sweet, it works on Fuzes now? I use RB on my Sansa e260 (pre-Fuze) and I love it. Maybe I'll buy a Fuze now if something happens to my current one.

EDIT: Whoa, I just updated to the latest Rockbox with USB support for e200, and now when it's plugged in when I press the buttons on it it CONTROLS EXAILE! HOW? That's pretty sweet I gotta say, since normally my keyboard media buttons don't even work without extra configuration :-P

---

### Post by dragos240 on 2009-07-04
> **Coldbird said:**
> I feel honored.:popcorn:
The page should be easy to use - when a new SVN version is out... just load the rebuild page on it and a whole new version will get compiled and packaged.

The script automatically compiles the bootloader and applies it to the latest official sansa software and packs the newly compiled rockbox firmware + bootloader installer + readme + latest official sansa firmware for uninstalling into a rar file.

But I suppose you know that already.

No problem coldbird, it's very helpful that you provided that link, and this small project needs that. Thank you.

---

### Post by Coldbird on 2009-07-04
> **doorknob60 said:**
> Sweet, it works on Fuzes now? I use RB on my Sansa e260 (pre-Fuze) and I love it. Maybe I'll buy a Fuze now if something happens to my current one.
Be careful which one you buy... the model #2 Sansa Fuze aren't supported.

Which Sansa Fuze it is you can check by it's firmware version on the Information screen of your Sansa.

If the firmware version starts with 01 - you're fine. If it's 02 thought you're screwed.;)

Edit: Known problem. If two guys rebuild the source at the same time... it ruins both builds... and still ticks the 1-hour-timer. This can lead to unavailability of Rockbox for Fuze for 1 hour in the worst case scenario...

So it would be a good idea to mirror the created builds somewhere. Just in case two idiots manage to rebuild the file at the same time. >_>

PS. If you see the currently available version to be fuze01.02.26.rockbox..rar - ITS BROKEN. This file is output, every time the above happens. I will redo the script sometime soon to prevent that. Till then that means... trigger a rebuild to fix the issue. If a rebuild is currently not possible. You gotta wait.

---

### Post by 2stepsteve on 2009-07-05
Hi

 How stable is this current version of Rockbox? Has the currupting of the file system been addressed?

Is there anyway to completely remove Rockbox once installed?
Thanks

---

### Post by Yes on 2009-07-05
It's definetly got issues, but for the most part it seems pretty stable.  The biggest problem I have is when I try to play all my songs on shuffle it seems to run out of memory after a few songs and crash.  

I dunno if the file system corruption has been addressed, you can read through [this](http://forums.rockbox.org/index.php?topic=14064.1050) thread to see what people are saying about that.

Just reinstall the original firmware to completly remove Rockbox.

---

### Post by dragos240 on 2009-07-05
> **2stepsteve said:**
> Hi

 How stable is this current version of Rockbox? Has the currupting of the file system been addressed?

Is there anyway to completely remove Rockbox once installed?
Thanks

Yes, remove the .rockbox and install the original firmware.

---

### Post by Coldbird on 2009-07-06
> **2stepsteve said:**
> How stable is this current version of Rockbox? Has the currupting of the file system been addressed?
I at the very least had no corruption on my uSD card or main memory till now. So I suppose it is.

I'm also using the database feature, which was said to trigger the corruption - and still I'm fine.

> **2stepsteve said:**
> Is there anyway to completely remove Rockbox once installed?
My online compile script from the very first page of this thread automatically packs you a rar file containing the following files...

.rockbox (folder with rockbox firmware svn build)
fuzeA.bin (latest sansa fuze fw + rockbox fw bootloader installer)
fuzeA.bak (original latest sansa fuze fw)
readme.txt (just some warnings and basic instructions)

The readme explains both how to install rockbox and how to remove it again with just the contents of the rar file.

Keep in mind thought that no matter what you do... by installing Rockbox - even if you remove it lateron - you break DRM support.

:popcorn:

**EDIT**: Guys - due to a damn SSH mistake of mine... (cd-ing into the wrong folder + rm while I was not quite there mentally) - I lost the script.

Give me a few minutes to rebuild it. I've got a backup around here somewhere. I'll use this downtime for maintenance and improvement of the script while I'm at it.

So I'm sorry that the script won't be available for 30 minutes up to 1 hour.

I will report back when it's back up.

---

### Post by 2stepsteve on 2009-07-06
Thanks for that dragos240 and Coldbird :)

I installed rockbox last night and had a good play with it for 4 hours, worked without any problems. 

Today things are acting up slightly I had a couple of 'Data abort at 3001E5F8' errors when selecting an MP3 from the main memory. This gets a mention on the Rockbox forums.

---

### Post by Coldbird on 2009-07-06
I did notice a bug myself, a few flac files of mine refuse to play and simply "nuke" the player.

It doesn't turn off... just blackscreens and nothing happens anymore.

I have to manually turn it off when that happens and reboot. It's always the same flac files that **** up though... Amaranth from Nightwish for example...

I think I will start a bit of debugging myself with those songs and see if I can write a bugfix.

Edit: Oh just noticed - yeah no problem. Glad to be of help.

**EDIT! IMPORTANT!**: Script recoded from scratch, back up and working. Also has a multi-rebuild lock in it now. No more broken builds when multiple people try to compile at once.

---

### Post by 2stepsteve on 2009-07-06
Looks like the guys at rockbox are now happy enough with things to start offically giving out test builds.

[http://forums.rockbox.org/index.php?topic=22137.msg152789#msg152789](http://forums.rockbox.org/index.php?topic=22137.msg152789#msg152789)

---

### Post by Chronon on 2009-07-06
Any folks who wish to help get Rockbox officially supported on the Fuze (and e2x0 v2)should consider installing a test build and reporting issues on the Rockbox forums.  

[http://forums.rockbox.org/index.php?topic=22137.0](http://forums.rockbox.org/index.php?topic=22137.0)

---

### Post by Coldbird on 2009-07-06
I know they started it. In fact I've got a feeling I was the trigger for them to do that... the administrators got back to me about my live-svn-builds. ^^'

---

### Post by dragos240 on 2009-07-06
Wow...... 21 pages of this....

---

### Post by 2stepsteve on 2009-07-06
> **Coldbird said:**
> I know they started it. In fact I've got a feeling I was the trigger for them to do that... the administrators got back to me about my live-svn-builds. ^^'

I am still using your service Coldbird, it is much more convenient having all the files ready for download in one rar file instead of fiddling around with downloading other files and running an exe.

I think you deserve a lot of credit for providing something which works and which made the guys at rockbox notice that they need to change and move in to precomplied binaries for the fuze. I hope that email you got gave you some praise!

Thanks again :)

---

### Post by Coldbird on 2009-07-06
Not exactly praise. More like demand and trying to make me feel guilty.
Not all admins though! One admin was in fact quite supportive and understanding. I'm not mentioning names though.

About the fullpack. I fear this will change a tiny bit though. At the request of the Rockbox Administrators I was asked to remove the retail firmwares and the precompiled installers from my package.

As to avoid trouble with the Rockbox Forum Administration I will indeed rewrite my scripts a tiny bit to follow their request.

Don't worry about it though. The Package will remain just as simple to use as always. I will find a way.

**EDIT**: I'm not much of a advertiser but still I will try to misuse that post a tiny bit.
If you guys ever need me, contact me via Jabber. I host my own Jabber Server, together with many other services (as you might have noticed *laugh*) on celes-network.de.

JID: [email]coldbird@celes-network.de[/email]

For Linux Users this really should be the PROPER alternative to MSN, etc... as its the only TRUELY free network. You can just use Pidgin or Spark for connecting. On Pidgin the Account Type is XMMP btw. ^^

---

### Post by Chronon on 2009-07-06
AFAIK, the main problem that certain members of the forum staff have is with advertising copyright infringement on the forums.  If you fix this, then I think there's no further problem.  

People are, of course, free to use whatever build they like.  However, it would help the target to gain official support if you tried out the official test build and reported any bugs to the project.

---

### Post by Coldbird on 2009-07-07
Chronon - the official build is pretty obsolete seriously. Every bugreport is just AS valid - as long as you mention what Rockbox Version you used to trigger it, the administrators and developers can - afterall - rebuild exactly that version using their SVN repository.

So if you used one of my builds for example and reported a bug you found - it would be just as valid and accepted as the "official" build.

The only problem the admins have with my build is that I'm providing fuzeA.bin and fuzeA.bak.

---

### Post by Chronon on 2009-07-07
If the Rockbox devs want to test against a specific revision -- such as the case when they offer a particular test build -- then I think providing bug reports against this particular revision is better than providing them against a different SVN revision.  The surest way to know you're testing against the version they want data about is to use their test build.

Obviously, people can do what they like.  They can choose for themselves whether or not they wish to contribute feedback to the project and whether they wish to use your builds or the project's builds. If anyone does decide to provide feedback, it's worth installing the official build so you can be sure that your observations apply to the particular revision of interest.

Anyway, I don't have any further agenda in this thread.  I pointed out the existence of the official test builds and why, from a methodological standpoint, they may be preferred.

Edit: removed unnecessary bits about copyright issues.

---

### Post by GeneralTrue on 2009-07-08
Finaly i was waiting for a stable release sort of.. now my gbc games run smoothly

---

### Post by curu on 2009-07-09
With your Fuze ? i tried some games as Pokemon and Zelda with the 14th page archive build and It runned pretty slowly.

---

### Post by GeneralTrue on 2009-07-09
> **curu said:**
> With your Fuze ? i tried some games as Pokemon and Zelda with the 14th page archive build and It runned pretty slowly.

use the link from icebird on the first page thats the most recent build and will make it work great

---

### Post by dragos240 on 2009-07-09
> **GeneralTrue said:**
> use the link from icebird on the first page thats the most recent build and will make it work great

coldbird?

---

### Post by GeneralTrue on 2009-07-10
> **dragos240 said:**
> coldbird?
 

Yea theres a link on the very first page just use this link for the latest rockbox build

[[COLOR=#444444]http://coldbird.celes-network.de/rockboxfuze/index.php[/COLOR]]("http://coldbird.celes-network.de/rockboxfuze/index.php")


Thats the up to date version always so keep checking back too see if its edited.although when the offical rockbox for the sansa fuze is released just use that one.

---

### Post by anishbenji on 2009-07-10
Once the firmware has been patched to include the rockbox bootloader, I presume, I can keep rockbox up to date by downloading new builds and copying the .rockbox folder on to the fuze? Is there any need or advantage to re-flashing the firmware for new builds (I know there is the chance of bricking your fuze during firmware updates....)?
How much chance is there of bricking it just running the rockbox firmware? From what I understand, reading the this and the Sansa Fuze forums, is that once you install the bootloader safely, you should be fine. Is there any evidence against this?
Thanks for your help,
Anish

---

### Post by dragos240 on 2009-07-10
> **GeneralTrue said:**
> Yea theres a link on the very first page just use this link for the latest rockbox build

[[COLOR=#444444]http://coldbird.celes-network.de/rockboxfuze/index.php[/COLOR]]("http://coldbird.celes-network.de/rockboxfuze/index.php")


Thats the up to date version always so keep checking back too see if its edited.although when the offical rockbox for the sansa fuze is released just use that one.

You said icebird, it was coldbird.

---

### Post by GeneralTrue on 2009-07-11
> **dragos240 said:**
> You said icebird, it was coldbird.


Ooo lol sorry

---

### Post by GeneralTrue on 2009-07-14
Just a question here.whats everyones favorite gbc game on the sansa fuze?

---

### Post by clonne4crw on 2009-07-14
Lol. They all run terrible on the little 248MHz CPU.

---

### Post by clonne4crw on 2009-07-14
> **anishbenji said:**
> Once the firmware has been patched to include the rockbox bootloader, I presume, I can keep rockbox up to date by downloading new builds and copying the .rockbox folder on to the fuze? Is there any need or advantage to re-flashing the firmware for new builds (I know there is the chance of bricking your fuze during firmware updates....)?
How much chance is there of bricking it just running the rockbox firmware? From what I understand, reading the this and the Sansa Fuze forums, is that once you install the bootloader safely, you should be fine. Is there any evidence against this?
Thanks for your help,
Anish

You will not need to reflash with FUZEA.bin again after the first time. All that does is (re)install the BootLoader. You're right, just copy over the new .rockbox folder to upgrade. 

I would say there is a little-to-no chance of bricking the Fuze, as it installs just like any other FW update. Just make sure yours is the V1 and not the V2.

---

### Post by GeneralTrue on 2009-07-15
> **clonne4crw said:**
> You will not need to reflash with FUZEA.bin again after the first time. All that does is (re)install the BootLoader. You're right, just copy over the new .rockbox folder to upgrade. 
 
I would say there is a little-to-no chance of bricking the Fuze, as it installs just like any other FW update. Just make sure yours is the V1 and not the V2.
 

i think theres no chance at all too brick your sansa fuze that way.the only way i think is that when you try too experiment with it.like trying too configure things which you have no knowledge of or if you go in debug mode.i dont even dair too go in debug mode.

---

### Post by dragos240 on 2009-07-15
> **GeneralTrue said:**
> i think theres no chance at all too brick your sansa fuze that way.the only way i think is that when you try too experiment with it.like trying too configure things which you have no knowledge of or if you go in debug mode.i dont even dair too go in debug mode.

Spelling and grammar 101.

---

### Post by dragos240 on 2009-07-15
Coldbird's link is broken fellas! We'll wait for them to get it back up.

---

### Post by dragos240 on 2009-07-15
Hi everyone! I just checked out and compiled the absolute latest build of rockbox, with a ton more plugins, and a few bugfixes.
Download it [here]("http://uppit.com/v/6342FP6G").

---

### Post by GeneralTrue on 2009-07-16
> **dragos240 said:**
> Spelling and grammar 101.

I`m sorry but english is not my first langauge.

---

### Post by dragos240 on 2009-07-16
It's okay.

---

### Post by Coldbird on 2009-07-20
My link is still valid... just remove the index.php...
[http://coldbird.celes-network.de/rockboxfuze/](http://coldbird.celes-network.de/rockboxfuze/)

I just deactivated the user-webscript because for some reason the processes created by the apache2 server never end... and they pile up in my servers ram - making it unstable.

So I'm building a new build every now and then and link it there.

---

### Post by dragos240 on 2009-07-20
Thanks cold bird, I updated the link, I'm also going to mention that not everyone has winrar.

---

### Post by PatrickMoore on 2009-07-21
has anyone got this working on a v2 fuze yet? i really want to upgrade

---

### Post by dragos240 on 2009-07-21
Sorry, the development has not even started. Either get a fuze v1, or wait for people to start working on fuze v2, also, I will try compiling the latest version with the sansa v2 firmware, and see if it works. But no promises.

---

### Post by dragos240 on 2009-07-21
I'm sorry PatrickMoore, I tried to bind the sansa v2 firmware with the rockbox bootloader, but it's not working, they have not even started developing it yet, it returns an error that states:
"./mkamsboot fuzpA.bin bootloader-fuze.sansa output.bin
mkamsboot Version r21996-090722
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[ERR]  Unknown firmware model (v2) - model id 0x70
[ERR]  Could not load fuzpA.bin"

Even the absolute latest rockbox that I downloaded less than 10 minutes ago is not compatible with the v2 yet. So, please wait, or buy a v1.

---

### Post by PatrickMoore on 2009-07-21
> **dragos240 said:**
> I'm sorry PatrickMoore, I tried to bind the sansa v2 firmware with the rockbox bootloader, but it's not working, they have not even started developing it yet, it returns an error that states:
"./mkamsboot fuzpA.bin bootloader-fuze.sansa output.bin
mkamsboot Version r21996-090722
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[ERR]  Unknown firmware model (v2) - model id 0x70
[ERR]  Could not load fuzpA.bin"

Even the absolute latest rockbox that I downloaded less than 10 minutes ago is not compatible with the v2 yet. So, please wait, or buy a v1.

Dragos, I appreciate the effort you have done great things for the fuze community I'll probably wait and see, or perhaps create a homework assignment to find a working build for the v2. I could've swore ive seen one after searching the darkest depths of the abi forums. if i find anything i will indeed post it immediately

---

### Post by Coldbird on 2009-07-22
I will be compiling a new build every 1-2 days, check my link on the first post.

Sansa Fuze V1 only.

---

### Post by adagio89 on 2009-08-01
Dragos, i want to thank you!:):P Im without any programing skills but this thread let me easy install rockbox on fuze.I have been using rockbox on fuze for a week now, no major problems, only a few crashes. Im very very happy kid now!! :mrgreen: Sound quality is just amazing! Doom wad,themes from rockbox.org works too !:)

---

### Post by computerkid2000 on 2009-08-10
i posted somthing on youtube bout rockbox on a [sansa clip]("http://www.youtube.com/watch?v=5PhVD5nyrWo")!

---

### Post by dragos240 on 2009-08-10
Yes the only issue about the clip model so far is that the external storage is not working, and the USB connection, and the recording. But everything else is okay so far. Also I read that the clip has occasional playback crashes.

Source: [http://www.rockbox.org/twiki/bin/view/Main/SansaAMS#Port_Status](http://www.rockbox.org/twiki/bin/view/Main/SansaAMS#Port_Status)

---

### Post by sideaway on 2009-08-11
Rockbox + Gigabeat F60 = win.

---

### Post by clonne4crw on 2009-08-12
> **sideaway said:**
> Rockbox + Gigabeat F60 = win.

Anything + Rockbox = Epic Win

---

### Post by computerkid2000 on 2009-08-12
well i just got my new from best buy fuze but it is v2 so i cant install rockbox!:(
but we all have to wait untill portage to this player!:)

---

### Post by dragos240 on 2009-08-12
Well, it is being ported, but all it can do right now is turn on.

---

### Post by miggols99 on 2009-08-12
I see that people have got themes different from the yellow and black default. Where do you get these? I don't know which ones are compatible from the ones on the Rockbox website...

---

### Post by dragos240 on 2009-08-12
You can make them. :)

---

### Post by Chronon on 2009-08-12
Go to [http://themes.rockbox.org](http://themes.rockbox.org) and download them.  I believe someone on the forums mentioned that the fuze has the same screen size and orientation as the 4g Color iPod (also same as the iriver H3xx but both links take you to the same set of themes). 

There's also a page in the Rockbox wiki containing the tag syntax if you would like to create your own.  Its name is CustomWPS. 

If you choose to create your own theme please consider licensing it under a CC-BY-SA license and sharing with the community by uploading it at the themes.rockbox.org site.

---

### Post by KevinEvans on 2009-08-13
Is there an updated version yet? I cba to go through all the posts -.-

---

### Post by dragos240 on 2009-08-13
> **KevinEvans said:**
> Is there an updated version yet? I cba to go through all the posts -.-

Come again? I can post the newest version within an hour.....

---

### Post by KevinEvans on 2009-08-13
Is there an updated version, other than the one on the first post?

Edit: If you can post the last updated version, that'd be great! :D

---

### Post by dragos240 on 2009-08-14
Okay, I will do that. But first I am setting up my compiler, as I am on my fedora computer. It's still making the compiler. Rockbox is funny like that, it needs a special compiler for mp3 players. So I need to let it finish making, then I need to set the PATH. after that of course, I will make the latest rockbox from the latest svn build (today).

---

### Post by dragos240 on 2009-08-14
Okay, I have successfully made the latest rockbox for the sansa fuze! This is the absolute newest version as of now. It was updated 5 hours ago.
[Here is the link.]("http://uppit.com/v/H221G89W") Make sure you can open .zip files.

---

### Post by Chronon on 2009-08-17
> **dragos240 said:**
> Okay, I will do that. But first I am setting up my compiler, as I am on my fedora computer. It's still making the compiler. Rockbox is funny like that, it needs a special compiler for mp3 players. So I need to let it finish making, then I need to set the PATH. after that of course, I will make the latest rockbox from the latest svn build (today).
A compiler builds the source code into machine language.  Different architectures speak different machine language so you need a different compiler for each architecture.  To build Rockbox requires cross-compilers to convert the ELF binaries used in Linux into the ARM, SH, etc. language spoken by a particular portable player.

Just to remind folks, there are builds available at the Rockbox forums for both Fuze and v2 e2x0.

---

### Post by dragos240 on 2009-08-17
> **Chronon said:**
> A compiler builds the source code into machine language.  Different architectures speak different machine language so you need a different compiler for each architecture.  To build Rockbox requires cross-compilers to convert the ELF binaries used in Linux into the ARM, SH, etc. language spoken by a particular portable player.

Just to remind folks, there are builds available at the Rockbox forums for both Fuze and v2 e2x0.

For v2 also? It isn't even in svn yet.

---

### Post by Chronon on 2009-08-17
Are you thinking of v2 Fuze?  Much of the code for the v1 Fuze also is shared by the v2 e200s and Clip (v1).  There are test builds currently for both Fuze (v1) and v2 e200 series.

---

### Post by dragos240 on 2009-08-17
Interesting...... I will check that out.

---

### Post by Chronon on 2009-08-17
Here's a link for those interested: [Sansa e200v2 and Sansa Fuze: Test builds](http://forums.rockbox.org/index.php?topic=22137.0)

---

### Post by #11u-max on 2009-08-17
i wish it was ported over to the zen vision:M!!!

---

### Post by GeneralTrue on 2009-09-22
Its finaly released by rockbox.so no need for crazy work arounds anymore.BUT THANK YOU VERY MUCH THOUGH i realy enjoyed rockbox and still will.

---

### Post by dragos240 on 2009-09-22
It has, has it? Nice!

Well then. This topic can now be closed, I need support the fuze no more.

---

### Post by frrobert on 2009-09-22
Please excuse the dumb question.

What are the advantages of Rockbox on the fuze?

I just got my Fuze last week and Ubuntu sees it and it plays oggs out of the box.  So I was curious what added features come with Rockbox over the standard firmware?

---

### Post by dragos240 on 2009-09-22
Games, video on your fuze without windows software, 3D effects, paint, binary clock, a text editor, and much more. Oh, and it's theme-able!

---

### Post by Chronon on 2009-09-23
After some recent restructuring, SVN builds for Fuze, e2x0 v2, Cowon D2, M:Robe MR-500, Toshiba Gigabeat S, and Samsung YH-925 builds are now available.  

> **Unstable ports**

Rockbox runs on these players, but is incomplete, less usable or has problems that limit it to advanced users:

    * Cowon: D2
    * Olympus: M:Robe 500
    * Samsung: YH-925
    * SanDisk: Sansa e200 v2 (AMS) and Sansa Fuze V1 

Main Page: [http://www.rockbox.org/](http://www.rockbox.org/)
Forums: [http://forums.rockbox.org/](http://forums.rockbox.org/)
Downloads: [http://build.rockbox.org/](http://build.rockbox.org/)
Key Features: [http://www.rockbox.org/wiki/WhyRockbox](http://www.rockbox.org/wiki/WhyRockbox)

---

### Post by OLFP on 2009-09-23
I'd like to try this, but I have some questions.

1) According to [**this**]("http://www.rockbox.org/wiki/SansaAMS"), USB is not supported. What exactly does that mean? If I can't copy files to the player's storage, it's pointless to try this.

2) Which build do I need? My 4GB Fuze uses firmware 02.02.26A. Rockbox leaves me in the dark with: > The v1 hardware uses firmware named 01.xx.xx, while the v2 hardware uses firmware beginning with 03. This version number can be retrieved under Settings->Info. All other indicators, such as markings on the casing or packaging, are unreliable due to SanDisk's practice of reusing these things without consideration for the hardware inside.

Thanks

---

### Post by dragos240 on 2009-09-23
> **OLFP said:**
> I'd like to try this, but I have some questions.

1) According to [**this**]("http://www.rockbox.org/wiki/SansaAMS"), USB is not supported. What exactly does that mean? If I can't copy files to the player's storage, it's pointless to try this.

2) Which build do I need? My 4GB Fuze uses firmware 02.02.26A. Rockbox leaves me in the dark with: 

Thanks

Easy, just like you can dual boot windows and Linux. By default you dual boot the original sansa fuze firmware with rockbox. Holding left while flipping the on switch will boot you up to the original firmware. Also, upon plugging the device in, the original firmware will be booted. It's just not part of rockbox yet.

---

### Post by Chronon on 2009-09-23
If you have Rockbox questions you'll get better advice/info over at the Rockbox forums.

@OLFP: The text you quoted was originally in reference to the e200 and c200.  I did a little checking and it appears that for the Fuze, the second hardware revision uses firmware numbers starting with 2.
> 
Revision 1 = 1.XX.XX (example: 1.01.15)
Revision 2 = 2.XX.XX (example: 2.01.16)

From here: [http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=9473](http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=9473)

Rockbox is being ported to the Revision 1 players.  As far as I know, nobody is working on Revision 2 yet (different hardware).

---

### Post by dragos240 on 2009-09-23
> **Chronon said:**
> If you have Rockbox questions you'll get better advice/info over at the Rockbox forums.

+1

Also, this topic does not have any use anymore. Can someone close this topic?

---

### Post by computerkid2000 on 2009-09-26
well teh admins havent closed so it is still open

---

### Post by clonne4crw on 2009-09-26
Wow. Almost 30 pages now. I remember when it was started earlier this summer.

---

### Post by dragos240 on 2009-09-26
Yep. It should be dead now though, :p

The fuze is now officially supported.

---

### Post by clonne4crw on 2009-09-26
Hey you're right! Awesome. I don't think this would've happened without you. I will still continue to compile my own custom builds, because it's the only real way to add main menu items.

---

### Post by dragos240 on 2009-09-27
> **clonne4crw said:**
> Hey you're right! Awesome. I don't think this would've happened without you. I will still continue to compile my own custom builds, because it's the only real way to add main menu items.

The rockbox team has been working on this for a while. It was bound to be released anyway, and yes, compiling builds from source is the only way for me too. :p

---

### Post by GeneralTrue on 2009-09-27
When i try to install it with the orginal rockbox installer,it says i need some kind of orginal firmware bin file.where do i get it? nevermind it is the fuzeA.bak file,i should look better before i ask  sorry=p

---

### Post by dragos240 on 2009-09-27
:p

---

### Post by skralljt on 2009-12-02
Thoughts on sansa fuze firmware I used a few weeks ago:
expect the new firmware to drain battery power really fast.  My fuze used to last on battery about 150% of the time it lasts on the rockbox firmware.
Don't expect the fuze to mount properly on your computer.  I haven't been able to mount mine more than twice since rb'ing (though it does charge when connected by usb, and the original firmware boots up saying that it is connected).
Don't expect to be able to USE the original firmware.  When I try to boot the player to the original firmware to double check what usb mode it is set to so that I can mount it on my computer in msc mode, it has the dreaded long "refreshing database" dialog.  The progress meter freezes about 10% of the way through.  
It is a good thing that I put a lot of great songs on it before I rockboxed it, I fear that I may never be able to mount it again!  (I've tried under winxp as well as ubuntu and slitaz).  

The good news is that I can listen to my beloved ogg vorbis files, musepack files, etc etc.  And also have a database including id3 2.4 data, which the orig firmware ignored.  It could only read 2.3.

---

### Post by dragos240 on 2009-12-02
#1. This topic is over. The rockbox officially supports the fuze now.
#2. Sansa's firmware supports ogg too!
#3. Did you update the original firmware to it's latest version? That's necessary.

Please don't post here, as it is now supported.

---

### Post by kyle99 on 2009-12-02
Rockbox is amazing, don't hesitate, just put it on right now :)

---

### Post by NFblaze on 2009-12-03
What about the battery life did it really decrease?

Also, two good news in one day. Opera Mini 5 Beta 2 and Rockbox...sweeeet.

---

### Post by skralljt on 2009-12-03
I am not asking for support here, I am merely discussing the topic's title within a cautionary tale.  Those thinking about this upgrade should have all the answers.  Plenty of software is discussed here that is supported elsewhere, amiright?  
Thanks for the firmware tip, I am p sure I did but it is something to check if I am ever able to mount it again since it is stuck in mtp mode and I have no way to change it back.



> **dragos240 said:**
> #1. This topic is over. The rockbox officially supports the fuze now.
#2. Sansa's firmware supports ogg too!
#3. Did you update the original firmware to it's latest version? That's necessary.

Please don't post here, as it is now supported.

---

### Post by dragos240 on 2009-12-04
> **skralljt said:**
> I am not asking for support here, I am merely discussing the topic's title within a cautionary tale.  Those thinking about this upgrade should have all the answers.  Plenty of software is discussed here that is supported elsewhere, amiright?  
Thanks for the firmware tip, I am p sure I did but it is something to check if I am ever able to mount it again since it is stuck in mtp mode and I have no way to change it back.

The newest firmware I provided automatically reboots the fuze into the original firmware when a usb is plugged in. I'm not sure if the firmware at the front page is the same. If all else fails. Find a way to mount it onto your linuxbox, and I'll give you a dd image of my drive. It should work.

---

### Post by zap.iso on 2010-01-14
has anyone heard anything about rockbox for the V2 fuze?

---

### Post by dragos240 on 2010-01-14
> **zap.iso said:**
> has anyone heard anything about rockbox for the V2 fuze?

No. Sorry. It's not stable yet.

---

