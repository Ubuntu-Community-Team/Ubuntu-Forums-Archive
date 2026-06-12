---
title: "I have only 2 gripes about Ubuntu everything else is terrific"
date: 2008-05-12
forum: Testimonials &amp; Experiences
---

### Post by Bigtime_Scrub on 2008-05-12
I wanted to say Im a long time windows user. I got my last blue screen of death and Im sick of microsoft. I have thought about seriously switching to Mac but before I did I wanted to give Linux a fair shot. 

So far, Ive been told everything I can do in Windows I can do in Linux and Ive found that out to be false. 

I have still been unable to mount/unmount my Ipod classic with amaroK, gtkpod, or Floola. None of them work and no one seems to know how to make it work. I can play music off of it, but I cant put anything on it. Ive read every how to Ive been able to get my hands on and it was all to no avail. 

I cant copy DVDs. I cant make back ups of my DVDs and there is no alternative to DVD Shrink. Ive tried using k9copy, but it either copies it too big, or it fails to compress and just copies small sections of the DVD and saves it all as an ISO. This program is useless to me. 

The good part is I havent gotten a single BSOD, virus, worm, trojan, or spyware and trust me Ive tried to on purpose.

Linux is very secure compared to windows. 

Its extremly stable.

Its easy to install programs from the repositories.

and last but not least the support community here is the best I have ever seen. Kudos on that.

Im afraid though, that the things I cant do outweigh the positives because its really all I use a computer for.

---

### Post by wadelewis4 on 2008-05-12
For your iPod, Try This: [http://www.getdeb.net/app/Banshee]("http://www.getdeb.net/app/Banshee")

And I am fairly certain you can install DVDshrink with Wine and it'll work fine.

---

### Post by SgtDude on 2008-05-12
I've tried using DVDshrink with wine before.  From a software functionality point it worked ok (it was able to shrink ISO images or DVD Folders), but it had trouble accessing encrypted DVDs.  I'm not saying it won't work, as I haven't tried this in over a year, but that and my wife's obsession with M$ Powerpoint keeps Window$ installed on one machine in my house.

---

### Post by Bigtime_Scrub on 2008-05-12
> **wadelewis4 said:**
> For your iPod, Try This: [http://www.getdeb.net/app/Banshee]("http://www.getdeb.net/app/Banshee")

And I am fairly certain you can install DVDshrink with Wine and it'll work fine.

DVD Shrink worked perfectly with wine thank you. It was actually faster from start to finish in Wine then it was with Vista. Very nice.

As far as the Ipod goes, banshee didnt work. I also tried YumiPod and Songbird. They didnt work either.

Why is it so hard to just put some music on an ipod :(

---

### Post by karellen on 2008-05-13
> **Bigtime_Scrub said:**
> DVD Shrink worked perfectly with wine thank you. It was actually faster from start to finish in Wine then it was with Vista. Very nice.

As far as the Ipod goes, banshee didnt work. I also tried YumiPod and Songbird. They didnt work either.

Why is it so hard to just put some music on an ipod :(

because ipods are locked by apple. I'd never buy one, there are plenty other good mp3/mp4 players

---

### Post by jolx on 2008-05-13
instead of DVDshrink, theres also acidrip, dvd:rip, dvd95 and thoggen

---

### Post by Crick on 2008-05-13
DVDDecryptor.exe works perfectly well with WINE.

And as far as IPods are concerned, I don't know much about them. If I was to get a portable media player, it would probably be a Cowon. They have excellent [compatibility]("http://en.wikipedia.org/wiki/Comparison_of_portable_media_players"), especially with OGG, FLAC, APE etc. Apparently the sound quality is also really good according to reviews I have read. I'd get the D2.

---

### Post by Bigtime_Scrub on 2008-05-14
O btw, I found a great Debian application that works in Ubuntu. Im really into media, and its the main thing Im productive with as far as my computer goes. It can download youtube viedos, create ISO images out of TS_ folder or really any video file, it does MD5 sums, decrypt/encrypt, compression,convert MacOs images,  convert Flac to avi and vise versa. Its what I really needed. Its awesome.

The program is called AcetoneISO2. 

Its fantastic.

---

### Post by tashmooclam on 2008-05-14
If iPods don't like the players, why not run iTunes in Wine? Just an idea.

---

### Post by Bigtime_Scrub on 2008-05-14
> **tashmooclam said:**
> If iPods don't like the players, why not run iTunes in Wine? Just an idea.

Im told not to even try because it doesnt work and stuff will crash.

---

### Post by pbeesley on 2008-05-14
> **Bigtime_Scrub said:**
> 
I cant copy DVDs. I cant make back ups of my DVDs and there is no alternative to DVD Shrink. Ive tried using k9copy, but it either copies it too big, or it fails to compress and just copies small sections of the DVD and saves it all as an ISO. This program is useless to me. 


OK well I was having the same problem. To fix it I found that as long as I could get a DVD to play (there's a guide on this somewhere but I don't know where I'll have a look) then I could copy them. I used ACIDRIP

Hope this helps

---

### Post by 3rdalbum on 2008-05-14
There are a couple of DVDs that will trip up K9Copy, but then there are a couple of DVDs that will trip up DVDshrink. Give K9 another chance, as 98% of my discs work. I have a friend who, like you, mostly does DVD shrinking on her computer; and she is happy with K9Copy.

---

### Post by Zer0Nin3r on 2008-05-14
> **3rdalbum said:**
> There are a couple of DVDs that will trip up K9Copy, but then there are a couple of DVDs that will trip up DVDshrink.

I think DVD Shrink has the best interface and give me the best quality shrink for a DVD.  I haven't tried it with the recent wine, as I've always ran into problems.

K9Copy will get the job done, but I am not too terribly impressed with the quality of my copies, but I'm almost done archiving my library so I will be done for a while.

However, it is true, some of the newer titles will "trip" up both K9Copy and DVD Shrink.


> Originally Posted by Bigtime_Scrub
I cant copy DVDs. I cant make back ups of my DVDs and there is no alternative to DVD Shrink. Ive tried using k9copy, but it either copies it too big, or it fails to compress and just copies small sections of the DVD and saves it all as an ISO. This program is useless to me. 


As for Bigtime_Scrub make sure you have all the necessary libraries installed.  That includes [libdvdcss]("http://www.google.com/search?q=libdvdcss&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

Also to encode to AVI, under the tab at the bottom of your window tabled 'MPEG-4 Encoding Options' I go with XVID and encode the audio to mp3(lame) with a bitrate of 192. Again, make sure you have all the libraries and codecs that you need installed.  I'm sure you have this done already.

Cheers!

---

### Post by Bigtime_Scrub on 2008-05-14
I finally got K9 Copy to work, I guess It was just 1 DVD for whatever reason, didnt want to be copied. 

I have evevn found games that work with wine! For people who dont know I play 3 older games that work. AOE: II, Crusader, and Warlords IV: Heros Of Etheria.

The only thing I still use Windows for is my IPod, hopefully, that will change someday.

---

### Post by Vegetarianrage on 2008-05-14
For you ipod troubles, can you explain a little more what is actually happening? I use an ipod classic 4th gen (grayscale) and i had no problems at all right out of the box. Can you not mount the file system at all? Or are you just having issues with your players not recognizing it. I'm still using rhythmbox until I can find something worth replacing it with and it recognizes and loads my ipod without worry.

I suggest trying something like Rockbox if you want compatability with more filetypes etc. I'm really enjoying it and you can dual boot your ipod if for some reason you want to keep iTunes. You don't need to, however, because you can just copy your media files to anywhere on the ipod you choose and rockbox will find it on its own.

---

### Post by Bigtime_Scrub on 2008-05-14
> **Vegetarianrage said:**
> For you ipod troubles, can you explain a little more what is actually happening? I use an ipod classic 4th gen (grayscale) and i had no problems at all right out of the box. Can you not mount the file system at all? Or are you just having issues with your players not recognizing it. I'm still using rhythmbox until I can find something worth replacing it with and it recognizes and loads my ipod without worry.

I suggest trying something like Rockbox if you want compatability with more filetypes etc. I'm really enjoying it and you can dual boot your ipod if for some reason you want to keep iTunes. You don't need to, however, because you can just copy your media files to anywhere on the ipod you choose and rockbox will find it on its own.

I cant transfer songs to it. The IPod is mounted correctly. It shows on my desktop as an icon. Ive followed the step by step guides and it seems to work ok but everytime I check the IPod the songs are never there. They simply dont transfer. Ive already given up trying to make it work. Ive chaulked it up to being something that just cannot be done, its ok it isnt the end of the world or anything. Everything else Ubuntu does flawlessly.

---

### Post by MNICY on 2008-05-14
for your Ipod, you can  always install windows (or  OSA) intro Virtual box  (or duel-boot) and only  load into Windows to change your Ipod. Virtualbox ever has a "save state"  option so It does not take much time :)seems silly to ditch Linux just  because you can't change your Ipod...  Anyway, wish you luck, whatever you do.

---

### Post by Bigtime_Scrub on 2008-05-14
> **MNICY said:**
> for your Ipod, you can  always install windows (or  OSA) intro Virtual box  (or duel-boot) and only  load into Windows to change your Ipod. Virtualbox ever has a "save state"  option so It does not take much time :)seems silly to ditch Linux just  because you can't change your Ipod...  Anyway, wish you luck, whatever you do.

Im not ditching Linux because of the IPod. I am saying Im only keeping Vista on 1 machine because of it. I use my desktop loaded with Ubuntu 8.04 90% of the time now. I'd like to put Fedora Core 9 on my laptop to see how it works but wihout IPod support I cant do that. Its really the only thing keeping me from being 100% linux at this point.

---

### Post by MNICY on 2008-05-14
Ah, i see :)
That sounds like a great solution.
To bad it cant be made to work with wine..
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11372&iTestingId=24039](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11372&iTestingId=24039)
.. or apple doesn't just make a Linux version..

---

### Post by abhiroopb on 2008-05-15
Which iPod do you have? Took me forever but I got mine to work (ipod classic 80gb).

Let me know which one it is and I can promise you we'll figure out a way to make it work!

---

### Post by Bigtime_Scrub on 2008-05-15
> **abhiroopb said:**
> Which iPod do you have? Took me forever but I got mine to work (ipod classic 80gb).

Let me know which one it is and I can promise you we'll figure out a way to make it work!

Ironically enough I have an 80GB classic lol.

---

### Post by Nampla on 2008-05-15
as far as the dvd copying.  I have actually had fantastic luck with graveman. It's in the add-remove programs.  I have iso. of win XP,2000,Nt,vista and about 20 win programs that i use with vmware.  THese are all on my hard drive and trasfer easily to dvd's if needed.  
as far as Ipod my niece uses gtkpod and hippo ipod applications and she is happy with them.  THey are also on you add-remove programs under the applications menu. Just make sure you "show" "all availabla applications" and search for ipod.

---

### Post by abhiroopb on 2008-05-15
Alrighty, here's what I suggest you do.
[B]
NB: Going to start RIGHT at the begining, so I am assuming that you have ALL your music somewhere on your computer and the iPod is blank.[/B]
[COLOR="SeaGreen"][B]
1. Cleaning out you're iPod[/B][/COLOR]

1. Connect the iPod.
2. It should (as you say) appear in nautilus.
3. Browse to the iPod folder.
4. You should see the following folders: Calendars, Contacts, iPod_Control, Notes, Recordings.
6. Delete everything (NB: This erases you're iPod to factory settings.
7. Eject you're iPod.
8. Wait a bit and the apple logo should appear on the iPod
9. Select you're desired language.

[B][COLOR="SeaGreen"]
2. Amarok and Libgpod:[/COLOR][/B]

From: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=658523](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=658523)
(I have condensed it with the useful bits you need)

Apple have recently released a new look for their ipods, but with the new interface comes more firmware encryption to stop 3rd party media players (including Amarok, Rhythmbox and gtkpod) syncing music to the ipods.

Since there is no itunes for linux it was up to the guys at [http://ipodminusitunes.blogspot.com](http://ipodminusitunes.blogspot.com) to crack it.

This should work for any new nanos and ipod classics. Please be aware that this is rather experimental so please make sure that you have all of the music on you ipod backed up before attempting it. The programs instanlled by this tutorial are from the hardy repository so don't be supprised if they break stuff.


Here's how to get it working (type this into terminal one line at a time, use the same terminal session for all):

First to install the latest libgpod
```

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common

```

Then installing amarok (NB: if you already had amarok this will overwrite everything!)
```

aptitude install amarok

```

Removing the old libgpod
```

aptitude remove libgpod2

```
(this may prompt you to remove the ubuntu-desktop package, don't worry - it's only a meta-package)

then check if it works. if it does run

```

rm /etc/apt/sources.list
mv /etc/apt/sources.list.tmp /etc/apt/sources.list
apt-get update

```
[B][COLOR="SeaGreen"]
3. Setting up Amarok[/COLOR][/B]

1. Here I assume you know how to use amarok (i.e. adding music, doing your own customisations, etc).
2. After you have done all that connect up your iPod.
3. Go to devices and your iPod SHOULD appear here (you may have to click connect) - you will be asked to "Initialize your iPod", say OK"
4. Set your iPod model by going to iPod (just below main toolbar on top)>Set iPod Model>Classic>80GB (black or silver).
5. Next go to collection and right click on whatever songs you want to transfer and select transfer to media device.
6. Next go back to device tab and select transfer (from the top).
7. Hopefully everything should transfer.
[COLOR="SeaGreen"][B]
4. Properly Disconnecting[/B][/COLOR]

1. Click on the gears next to where it says iPod, this should open up a dialog for mounting and post-disconnect commands.
2. Leave the mount command blank and put the following in the disconnect box:

```

rm /media/iPod/iPod_Control/iTunes/iTunesLock;rm "/media/iPod/iPod_Control/iTunes/Play Counts";eject -t -d %d

```

where it says "rm /media/iPod/iPod Control" change "/media/iPod" to wherever your iPod is mounted (this can be found by going to nautilus browsing the iPod and looking at the address bar).

3. Click OK
4. WAIT for everything to complete (including on the bottom statusbar of Amarok which should say Flushing iPod Cache).
5. When everything seems to have stopped click on iPod>Update Artwork (this may take a while depending on the number of songs, but after it is done you will see Artwork updated on the bottom).
6. Click disconnect, it should say device successfully disconnected.
7. Now right-click on the iPod icon (either in nautilus or on the desktop, and select eject).

THATS IT!

Let me know if you have any problems.

---

### Post by stchman on 2008-05-15
> **Bigtime_Scrub said:**
> I wanted to say Im a long time windows user. I got my last blue screen of death and Im sick of microsoft. I have thought about seriously switching to Mac but before I did I wanted to give Linux a fair shot. 

So far, Ive been told everything I can do in Windows I can do in Linux and Ive found that out to be false. 

I have still been unable to mount/unmount my Ipod classic with amaroK, gtkpod, or Floola. None of them work and no one seems to know how to make it work. I can play music off of it, but I cant put anything on it. Ive read every how to Ive been able to get my hands on and it was all to no avail. 

I cant copy DVDs. I cant make back ups of my DVDs and there is no alternative to DVD Shrink. Ive tried using k9copy, but it either copies it too big, or it fails to compress and just copies small sections of the DVD and saves it all as an ISO. This program is useless to me. 

The good part is I havent gotten a single BSOD, virus, worm, trojan, or spyware and trust me Ive tried to on purpose.

Linux is very secure compared to windows. 

Its extremly stable.

Its easy to install programs from the repositories.

and last but not least the support community here is the best I have ever seen. Kudos on that.

Im afraid though, that the things I cant do outweigh the positives because its really all I use a computer for.

I have used K9Copy numerous times (archive my own purchased DVDs) and it successfully creates a 4.3G .iso from a dual layer DVD.

I am not a big iPod fan, but Rhythmbox supports most iPods OOB.  There are lots of portable music players out there as capable as the iPod for less cash.  From what I have read Apple has a new firmware that renders the newer iPod nearly useless to Linux.

I have been happily on Ubuntu now for over a year and have not looked back.  I keep XP around for gaming and use Linux for everything else.

---

### Post by Thanh-BKK on 2008-05-16
Hi :)

As for copying DVD's, if you want to copy them 1:1, have you tried k3b? It does it nicely (even "on the fly") for me on Ubuntu Hardy. 

I have gotten that tip here because i, too, had problems with that before. k3b is perfect (it's a KDE app so if you have no other KDE things it'll install a bunch of libraries along with itself). Get it via Synaptic.

Best regards.....

Thanh

---

### Post by xt0rt on 2008-05-16
> **SgtDude said:**
> I've tried using DVDshrink with wine before.  From a software functionality point it worked ok (it was able to shrink ISO images or DVD Folders), but it had trouble accessing encrypted DVDs.  I'm not saying it won't work, as I haven't tried this in over a year, but that and my wife's obsession with M$ Powerpoint keeps Window$ installed on one machine in my house.

Openoffice.org Presentation is still nothing compared to Powerpoint.

Powerpoint is the only reason I have WINE installed ;O

---

### Post by abhiroopb on 2008-05-16
Just curious, what would you say is lacking?

---

### Post by Bigtime_Scrub on 2008-05-16
> **abhiroopb said:**
> Alrighty, here's what I suggest you do.
[B]
NB: Going to start RIGHT at the begining, so I am assuming that you have ALL your music somewhere on your computer and the iPod is blank.[/B]
[COLOR="SeaGreen"][B]
1. Cleaning out you're iPod[/B][/COLOR]

1. Connect the iPod.
2. It should (as you say) appear in nautilus.
3. Browse to the iPod folder.
4. You should see the following folders: Calendars, Contacts, iPod_Control, Notes, Recordings.
6. Delete everything (NB: This erases you're iPod to factory settings.
7. Eject you're iPod.
8. Wait a bit and the apple logo should appear on the iPod
9. Select you're desired language.

[B][COLOR="SeaGreen"]
2. Amarok and Libgpod:[/COLOR][/B]

From: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=658523](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=658523)
(I have condensed it with the useful bits you need)

Apple have recently released a new look for their ipods, but with the new interface comes more firmware encryption to stop 3rd party media players (including Amarok, Rhythmbox and gtkpod) syncing music to the ipods.

Since there is no itunes for linux it was up to the guys at [http://ipodminusitunes.blogspot.com](http://ipodminusitunes.blogspot.com) to crack it.

This should work for any new nanos and ipod classics. Please be aware that this is rather experimental so please make sure that you have all of the music on you ipod backed up before attempting it. The programs instanlled by this tutorial are from the hardy repository so don't be supprised if they break stuff.


Here's how to get it working (type this into terminal one line at a time, use the same terminal session for all):

First to install the latest libgpod
```

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common

```

Then installing amarok (NB: if you already had amarok this will overwrite everything!)
```

aptitude install amarok

```

Removing the old libgpod
```

aptitude remove libgpod2

```
(this may prompt you to remove the ubuntu-desktop package, don't worry - it's only a meta-package)

then check if it works. if it does run

```

rm /etc/apt/sources.list
mv /etc/apt/sources.list.tmp /etc/apt/sources.list
apt-get update

```
[B][COLOR="SeaGreen"]
3. Setting up Amarok[/COLOR][/B]

1. Here I assume you know how to use amarok (i.e. adding music, doing your own customisations, etc).
2. After you have done all that connect up your iPod.
3. Go to devices and your iPod SHOULD appear here (you may have to click connect) - you will be asked to "Initialize your iPod", say OK"
4. Set your iPod model by going to iPod (just below main toolbar on top)>Set iPod Model>Classic>80GB (black or silver).
5. Next go to collection and right click on whatever songs you want to transfer and select transfer to media device.
6. Next go back to device tab and select transfer (from the top).
7. Hopefully everything should transfer.
[COLOR="SeaGreen"][B]
4. Properly Disconnecting[/B][/COLOR]

1. Click on the gears next to where it says iPod, this should open up a dialog for mounting and post-disconnect commands.
2. Leave the mount command blank and put the following in the disconnect box:

```

rm /media/iPod/iPod_Control/iTunes/iTunesLock;rm "/media/iPod/iPod_Control/iTunes/Play Counts";eject -t -d %d

```

where it says "rm /media/iPod/iPod Control" change "/media/iPod" to wherever your iPod is mounted (this can be found by going to nautilus browsing the iPod and looking at the address bar).

3. Click OK
4. WAIT for everything to complete (including on the bottom statusbar of Amarok which should say Flushing iPod Cache).
5. When everything seems to have stopped click on iPod>Update Artwork (this may take a while depending on the number of songs, but after it is done you will see Artwork updated on the bottom).
6. Click disconnect, it should say device successfully disconnected.
7. Now right-click on the iPod icon (either in nautilus or on the desktop, and select eject).

THATS IT!

Let me know if you have any problems.

It still doesnt let me transfer. When I go to the transfer button in amarok, its greyed out and it doesnt even give me the option to transfer. The IPod connects and it can disconnect, but transfer is a no go.

---

### Post by abhiroopb on 2008-05-16
OK firstly have you done everything?

The most important thing is did Amarok ask at any point (after you connected the iPod), whether you wanted to Initialize it or not?

Also can do you actually have songs in the transfer queue? That is in the Devices tab is the pane split into a top half (where the songs in your iPod should show up as they transfer) and the bottom half (where the songs you want to transfer are located).

---

### Post by Bigtime_Scrub on 2008-05-16
> **abhiroopb said:**
> OK firstly have you done everything?

The most important thing is did Amarok ask at any point (after you connected the iPod), whether you wanted to Initialize it or not?

Also can do you actually have songs in the transfer queue? That is in the Devices tab is the pane split into a top half (where the songs in your iPod should show up as they transfer) and the bottom half (where the songs you want to transfer are located).

Yes I did all that.

yes I initialized.

At first, the transfer icon was available. It started but there was an error that one track couldnt be transfered. On the bottom left it was moved to the queue. Since that happened I havent been able to use the transfer icon.

---

### Post by abhiroopb on 2008-05-16
What did the error say? If you can vaguely remember.

Otherwise I'd suggest trying erasing your iPod again (step 1) and reconnecting it to amarok. It shouldn't take too long, and this time you can try with a different song.

---

### Post by Bigtime_Scrub on 2008-05-16
> **abhiroopb said:**
> What did the error say? If you can vaguely remember.

Otherwise I'd suggest trying erasing your iPod again (step 1) and reconnecting it to amarok. It shouldn't take too long, and this time you can try with a different song.

It wasnt a song that I put on that caused the error. It was a song amaroK put on there. It was some kind of "Welcome to AmaroK" track.

---

### Post by abhiroopb on 2008-05-16
A welcome to amarok song? Seriously? In my year of using Amarok I haven't ever seen a welcome song!! :P...anyway. Like I said, reset everything (and perhaps make sure that the welcome song is erased).

---

### Post by Bigtime_Scrub on 2008-05-16
Media Device: Copying file:///home/kong/Desktop/Metallica/Metallica - 1983 - Kill 'em All/[MP3] - 05-(Anethesia) - Pulling Teeth.mp3 to file:///media/ipod/Metallica/Kill_'em_All/(Anethesia)_-_Pulling_Teeth.mp3 failed



I finally got the transfer button working after I reinstalled amarok.

This is what I got when clicked transfer.

---

### Post by abhiroopb on 2008-05-16
Couple of things:

1. Make sure the file is properly located (i.e. its actually on the desktop),

2. This is more likely and it is most probably what the problem is....its transferring to /media/ipod/Metallica...etc...the song shouldn't be transfering like this. As in the file structure of the iPod is slightly different.

Go to your iPod folder, and into the iPod_Control folder, and list what folders there are in there. Then list what files you have in the iTunes folder. We have to make sure you're file structure for the iPod is ok. and the iTunes database has been created.

Also try with a different file.

---

### Post by Bigtime_Scrub on 2008-05-16
I really appreciate you trying to help with this, but it just doesnt work for whatever reason. Im still new to Linux, Im a fast learner but I think I just dont have the technical know how to do this. Im getting extremely FRUSTRATED.

Thanks anyway though, seriously.

---

### Post by abhiroopb on 2008-05-16
No worries.

Just like to point out that contrary to popular belief I personally DO NOT think Ubuntu is a point and click affair. Thats not to say I don't absoloutely love it!

I recently dual-booted windows and (being a new install), it ran smoothly, ran all my games, did everything I really needed it to. But honestly I still love running ubuntu and tinkering with it (as almost EVERYTHING is configurable).

I've used ubuntu for about a year and a half and I had my iPod since about October, yet I only FULLY got it working with amarok about yesterday.

I don't listen to my iPod ALL the time but it was a pain not having it working, and the fix I found FINALLY fixed it. I haven't used itunes so I can't attest to how good/bad it is, however, amarok does what I need it for, and most importantly it recognises and works with my iPod. I'm not saying it didn't take a lot of work (in fact I had to repeat step 1 about 20-30 times! Whenever it would cause a problem). But it was so satisfying now that its all working really well.

You need to put a lot of effort to make ubuntu works as you need to it, and honestly I don't believe the people who say they plugged it and "it just worked" thats certainly what would've happened on a mac, but not here. There isn't a single device that I haven't had to configure, tweak, and read up on. But thats what the forums are for after all!

Anyway done with my preaching, glad I could've helped. I'm happy to continue if you'd still like to keep trying :)

---

### Post by Bigtime_Scrub on 2008-05-16
The thing I dont understand is that when I uninstall amarok, when I reinstall it and open for the first time it keeps my old playlist and old settings like it had never been removed. I opened a terminal and did:

sudo apt-get remove amarok

Then I did:

sudo apt-get install amarok



BTW iTunes is very easy to use on a Mac. You just plug it in, drag and drop your music/video/whatever and sync. 

The windows way needs just a little bit of tweaking, but then it runs the same way. I understand Linux is not Mac or Windows. Im not even trying to compare them. They are each good for their own things. I wouldnt expect Windows to be a good server or a Mac to play video games. Can these things be done? Of course, but it doesnt mean its easy because its not designed for it. In the same way, if it takes that much effort to get an IPod working, its not supposed to be. 

I think a lot of the problems I am having is that running things with Ubuntu and Linux in general is not intuitive. Im trying to keep a very open mind and Im determined to give Linux a fair shot, which is why I am using Ubuntu full time now for everything. Ive learned how to do a lot of things with the terminal and Ive customized my themes, desktop, etc. In fact the only thing I havent done is get the IPod working and duel booting (which I would never do anyway, I dont see the use for it.)


Ive started using Ubuntu May 1. Ive learned a great deal and can do almost anything, so I can say without a doubt Ubuntu is not a difficult to use OS. But, like I said earlier it is not intuitive and fixing problems and getting things to work is easy if you know where to find documentation about the problem. The thing is though, you have to shift through pages and  pages of google and no one has time or energy for that. There needs to be standardized programs that just work. Id rather have an application with fewer features and not very customizable that just works then to have 10 different applications with loads of features that takes days to work properly. I tried Fedora Red Hat before a few years ago, and what I just said was the reason I hated it and never used it again.

---

### Post by abhiroopb on 2008-05-16
Thats because your settings aren't being properly deleted. In fact this might be a good idea.

Do this:

sudo apt-get remove amarok --purge
cd /home/<user>/.kde/share/apps
rm -rf amarok

This should clean out the amarok settings

then re-install.

---

### Post by Bigtime_Scrub on 2008-05-16
Weird, it wasnt showing any music on the Ipod's menu, but it does show that memory is being used by something somewhere. When I checked in the folder the ipod icon lets you see when you open it from the desktop, all the music was in a folder in there.

---

### Post by abhiroopb on 2008-05-17
See this is at the crux of the "iPod Problem". Basically apple did something funny to the iTunes database file. So now if you transfer songs it doesn't show the music on your iPod but the memory shows as "other". If this happens you'll have to reset your iPod (i.e. delete everything) and re-initialize it using amarok. The problem should be fixed since you installed libgpod3. Also check your amarok version, it should be 1.4.9. Finally make sure the disconnect command I gave you is disconnecting it properly.

If not I suggest you clean out EVERYTHING and start again, its likely that you messed up somewhere. Also make sure that you set you're iPod model correctly. THIS IS V V important.

Honestly you have the same iPod as me, if I can get it working (albeit painfully) I'mm sure so can you!

---

### Post by Bigtime_Scrub on 2008-05-30
I got it to work finally after a whole month of trying. Someone was kind enough to see what I was doing. As it turns out I was using the wrong mount point and trying to use that in Amarok. No wonder it was telling me it couldn't transfer. 

Thank you to everyone who has helped me to get this to work. I really appreciate it. 

So in the end, I guess I don't have any gripes. I understood when I switched there would be a learning curve at first. I don't have any problem with that because I think Linux is more stable, cheaper, more powerful, and freer than what I was using. I didn't learn Windows over night so I shouldn't expect to learn Linux over night either. 

If you guys could really understand how little I knew about Linux from just a month ago and compare it to now yall would be shocked. I can install anything with ease, compile like a champ, customize everything, and I use only free and open source software. Today, I can truly do what I did before and not miss out on anything. I even play games on Linux when I feel like it. It's awesome! I should have made the switch sooner.

---

