---
title: "Nokia 5800 compatibility"
date: 2009-01-24
forum: The Cafe
---

### Post by rootie on 2009-01-24
I've had my eye on the 5800 for a while now. I'm actually thinking of buying it within the week, but I can't help but wonder if there are any *big* issues regarding Nokia - Linux compatibility, along the lines of firmware updates, and the like. I know that the PC suite doesn't work at all, but should anything else make me think twice about this purchase?

Thanks in advance :D

---

### Post by bbldox on 2009-01-27
> **rootie said:**
> I've had my eye on the 5800 for a while now. I'm actually thinking of buying it within the week, but I can't help but wonder if there are any *big* issues regarding Nokia - Linux compatibility, along the lines of firmware updates, and the like. I know that the PC suite doesn't work at all, but should anything else make me think twice about this purchase?

Thanks in advance :D

Well, I didn't found the terrible ones. 
Rhythmbox doesn't work with 5800 (via MTP), Wammu does not, too.

If it sounds no so terrible for you - go on. At least, my bluetooth dongle works well with it.

---

### Post by bbldox on 2009-02-02
Well, changing HAL settings allows to get Nokia 5800 working with Rhythmbox.

---

### Post by rootie on 2009-02-02
Hi bbldox, thanks for the replies :D

Turns out I'm not getting the 5800 after all... I'm now lusting after the N97. How's the experience with the 5800? It doesn't sound like you have any major issues with it, and I hope that's the case :)

---

### Post by t0n1 on 2009-02-05
> **bbldox said:**
> Well, changing HAL settings allows to get Nokia 5800 working with Rhythmbox.

What exactly needs to be changed in order to use the 5800 with Rhythmbox?

---

### Post by meborc on 2009-02-06
firmware updates can be done straight from 5800 (through WLAN) so no need to connect to a pc... usb-cable lets you manage the files as with any usb-device

lucky you, i WANT a 5800 SOOOOOOOOOOO BAD

---

### Post by t0n1 on 2009-02-07
> **meborc said:**
> usb-cable lets you manage the files as with any usb-device

Yes, that I know. But it has its quirks :)
What I want to know, is how it can be used as an MTP device with Rhythmbox.

---

### Post by bbldox on 2009-02-10
Hi
well, I couldn't get it working as MTP device (exactly MTP), but the changes I applied are as following:

cd /usr/share/hal/fdi/information/10freedesktop
backup 10-usb-music-players.fdi
find a comment like <!-- Nokia N82 --> (which ends with </match>)

Add these lines:
<!-- Nokia 5800 -->
          <match key="@storage.originating_device:usb.product_id" int="0x156">
            <merge key="storage.model" type="string">5800</merge>
            <addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
            <append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
            <append key="portable_audio_player.output_formats" type="strlist">audio/aac</append>
            <append key="portable_audio_player.output_formats" type="strlist">audio/x-wav</append>
            <append key="portable_audio_player.audio_folders" type="strlist">Music/</append>
          </match>

If you have your music in "Sound" folder, put it in the last line.

reboot / restart d-bus

According to specs you should be able add both these lines, but I didn't give a try.

The similar trick is usefull if you want to get it working as GPRS/EDGE modem:

edit 10-modem.fdi
find <match key="@info.parent:usb.vendor_id" int="0x421">
and inside it there is:
<match key="@info.parent:usb.product_id" int_outof="0x4f9;0x64;0x2f;0xab;0x418;0x4f0;0x4ce;0x43a;0x44d;0x070;0x3a;0x71;0x72;0xb0;0x01;0x419;0x420;0x425;0x00e;0x432;0x42f;0x445;0x475;0x481;0x486;0x48e;0x4c4;0x4c9;0x4df;0x04e6;0x508;0x078">
add ";0x156" into list of codes.

I tried to change the settings to get it working as MTP device but without any luck.
Probably, you can do it =)

------
best wishes

---

### Post by bbldox on 2009-02-10
> **rootie said:**
> Hi bbldox, thanks for the replies :D

Turns out I'm not getting the 5800 after all... I'm now lusting after the N97. How's the experience with the 5800? It doesn't sound like you have any major issues with it, and I hope that's the case :)

Well, no serious issues yet. 
The only thing I wish to get in there is kind a "synchronization tool" to synchronize my Thunderbird calendar / address book and the phone's calendar / address book.

---

### Post by rootie on 2009-02-10
I can sympathize with the synchronization frustrations. I've been pulling hairs about it too (with a 5310). Doesn't look like a solution's coming anytime soon.

As for buying a new phone--Nokia's announced the [5630]("http://www.engadget.com/2009/02/10/nokias-5630-xpressmusic-is-12-mm-slim-hsupa-fast-and-s60-powe/"), and now I'm gravitating towards the cheaper side of the spectrum. Back to the 5800. =P

---

### Post by t0n1 on 2009-02-11
> **rootie said:**
> I can sympathize with the synchronization frustrations. I've been pulling hairs about it too (with a 5310). Doesn't look like a solution's coming anytime soon.

Google Sync is a nice solution. Not fully functional on the 5800, but a step in the right direction.

---

### Post by rootie on 2009-02-11
Hi t0n1, glad to hear about Google Sync. I can't test it though, I'm out of the country. Has anyone tried Ovi for syncing?

---

### Post by bbldox on 2009-02-11
> **rootie said:**
> Hi t0n1, glad to hear about Google Sync. I can't test it though, I'm out of the country. Has anyone tried Ovi for syncing?

OVI should work with Nokia 5800 when you add the device as N96. Anyway, I couldn't get it working because I didn't get any SMS from them.
When I asked OVI about support, that's what they answered:

> Pertaining to your email, I do apologize for the inconvenience caused; your Nokia 5800 XpressMusic is currently incompatible for use with Ovi. Support for Nokia 5800 XpressMusic will be added once the device has been fully certified for compatibility and accommodating updated features of Ovi services which have been integrated to Ovi.com.

As we are expanding Ovi services in phases, unlisted Nokia SyncML enabled devices will be added accordingly (time frame not confirmed). I assure you, it won’t be long when Nokia 5800 XpressMusic is found listed among those supported Nokia models.

---

### Post by t0n1 on 2009-02-11
> **rootie said:**
> Hi t0n1, glad to hear about Google Sync. I can't test it though, I'm out of the country. Has anyone tried Ovi for syncing?

Didn't even know that Ovi could do that. At least, I don't think it was there when I first got the device a month ago. Thanks for letting me know, definitely going to play around with it some more.
There seems to be no way to make ovi work with google thus far though :(
Which is understandable, everyone is pushing their own services.

---

### Post by rootie on 2009-02-12
hey, glad to be of some help. =P
i wonder if there are any other nokia 5800 users here. a small ubuntu/linux support group would be nice ;)

---

### Post by m3topaz on 2009-02-12
I've got multisync working quite happily with Intrepid and the 5800 - however using Evolution not Thunderbird. Contacts and Calendar are fine with it - worked first time I set it all up.

---

### Post by bbldox on 2009-02-12
Using this: [http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17) guide I was able to copy Addressbook from Nokia 5800 to the Evolution database. It has been copied even with contact's images!
The new challenge is the Calendar, Google Syncing and then back to Thunderbird =)

---

### Post by rootie on 2009-02-17
Took the plunge. I'm now the proud owner of a month-old 5800. :)

I've barely started tinkering with it, but my only comment for now is that the handwriting recognition thingy is kinda lazy (I scribble out a 7-letter word and it "recognizes" it as only 3 letters). Also, camera shutter sounds! :<

edit: oh, so it doesn't support cursive. :p that makes sense.

---

### Post by bbldox on 2009-02-18
> **rootie said:**
>  Also, camera shutter sounds! :<


Hey rootie. You can disable it by turning sound completely off (i.e. changing profile to "Silent" or "Meeting").

---

### Post by rootie on 2009-02-18
> **bbldox said:**
> Hey rootie. You can disable it by turning sound completely off (i.e. changing profile to "Silent" or "Meeting").

Hm, I've tried this but it doesn't work for me... Apparently there are some countries with laws that require cameras to make sounds. Tried cCam but there are some issues with the software certificate being 'expired'. Oh well, I'm not planning to take any upskirt shots soon anyway... ;)

Right now I'm ironing out the data plan details. I can't enjoy the phone while worrying about my bill...

---

### Post by bbldox on 2009-02-19
That's strange.. I've checked the profiles just yet - and yes, while "meeting" and "silent" there's no shutter sound.
Probably you're right, that is because of the product code of your phone.

---

### Post by meborc on 2009-03-01
writing this from 5800. :)

---

### Post by rootie on 2009-03-02
Congratulations, meborc :D Does it live up to your expectations? (It lives up to mine, except with regard to wifi reception. I use 3G instead.)

---

### Post by RaZe42 on 2009-03-02
> **rootie said:**
> Hm, I've tried this but it doesn't work for me... Apparently there are some countries with laws that require cameras to make sounds. Tried cCam but there are some issues with the software certificate being 'expired'. Oh well, I'm not planning to take any upskirt shots soon anyway... ;)

Right now I'm ironing out the data plan details. I can't enjoy the phone while worrying about my bill...

If software certificate is expired, just turn back the clock a year or so.

---

### Post by meborc on 2009-03-03
> **rootie said:**
> Congratulations, meborc :D Does it live up to your expectations? (It lives up to mine, except with regard to wifi reception. I use 3G instead.)

yeah, it's great... the resolution is wery good and videos play nice... 

i find the wifi working great, no problems yet.

only issue is the battery life, when playing with GPS, WIFI and multimedia, it only lasts for 2 days :(

---

### Post by t0n1 on 2009-03-03
Any issues with e-mail when connected via WiFi?
Also, is youtube working for you?

---

### Post by rootie on 2009-03-05
Hey dudes,
The time change does nothing :(
The battery time is admirable imo, even though my 5310 lasted for days with heavy use, it couldn't do half the things this baby can.
I connected to a public wifi spot, and i was able to load up gmail fine. Youtube is ok on 3g. Any specific issues you're facing?
Most annoying thing: inability to mlve cursor when typing into text fields, the multiline kind. Twitter is okay, but if you make a typo in gmail or the forums, you're screwed. (case in point, 'mlve' above.)

---

### Post by bbldox on 2009-03-06
Hey rootie
Backup all the settings / files / contacts / messages etc via PC Suite (NOT via File Manager) and do a hard reset of your phone:
*#7370# (the code is 12345). 
The device will be cleaned to the factory settings.
Now you can re-store the backup and install any application without this annoying "The certificate has expired".

---

### Post by Victor Rossetti on 2009-03-08
I received my new 5800 five days ago, and until now I had only one issue: file transfer from my laptop to the phone via Bluetooth simply doesn't work...the notification message: "Operation not supported by backend" .
Tomorrow I will start configuring OpenSync and start testing with the SyncML and evolution plugins. 

If anyone got the bluetooth file transfer working please ...lend me a hand

bye

Victor Rossetti, M.D.
Caracas, Venezuela

---

### Post by rebegin on 2009-03-08
I have this phone too, gmail, youtube works fine though i have some truble playing music on myspace and some general flash video problems. any idea how i can install it for opera mini 4.2?
i've successfully installed putty, so i can ssh into my pc, but it's quite strange to handle putty on the phone(i could log in, but then i only can see the consol in full screen mode but then i cannot enter anything...). anyone has experience on this? would be great to copy files from-to my phone through wifi...much faster than bluetooth, and bluetooth doesn't work on my jaunty right now :P

---

### Post by RaZe42 on 2009-03-08
> **Victor Rossetti said:**
> I received my new 5800 five days ago, and until now I had only one issue: file transfer from my laptop to the phone via Bluetooth simply doesn't work...the notification message: "Operation not supported by backend" .
Tomorrow I will start configuring OpenSync and start testing with the SyncML and evolution plugins. 

If anyone got the bluetooth file transfer working please ...lend me a hand

bye

Victor Rossetti, M.D.
Caracas, Venezuela

Right-click on the file you want to send, select "Send To", and then you should be able to figure out the rest;)

---

### Post by Victor Rossetti on 2009-03-08
> **RaZe42 said:**
> Right-click on the file you want to send, select "Send To", and then you should be able to figure out the rest;)

yes, I also tried that, but my system insists on compress the file in a .zip and doesn't allow me to uncheck that option... and it fails to transfer too... With my N80 I did transfer files, folders, etc. via bluetooth with no hassles at all. Now I don't know what is broken...I've been checking my system's bluetooth config and everything seems to be OK.


Thanks a lot anyway

Victor

---

### Post by Victor Rossetti on 2009-03-08
> **rebegin said:**
> I have this phone too, gmail, youtube works fine though i have some truble playing music on myspace and some general flash video problems. any idea how i can install it for opera mini 4.2?
i've successfully installed putty, so i can ssh into my pc, but it's quite strange to handle putty on the phone(i could log in, but then i only can see the consol in full screen mode but then i cannot enter anything...). anyone has experience on this? would be great to copy files from-to my phone through wifi...much faster than bluetooth, and bluetooth doesn't work on my jaunty right now :P

Until now i can agree with you ...almost everything works fine. I tried to find Upnp compatibility in the phone to ease the transfer via wifi. But I couldn't...seems that I should take a look at the manual for once.... ;). I also tried putty, but the app is simply not designed for S60 5th. ed. and behaved just like you described. I would like to find a fix to my bluetooth issue. Have you tried to mount your phone via bluetooth (using the bluetooth icon in gnome "Explore files in device.." ) and start a file transfer? -Transfers work from the phone but not TO the phone- Do you have the same issue as me? Because if its an isolated issue then could be my system's bluetooth (then my fault), otherwise I could blame the phone...:D 

Thanks a lot

Victor

---

### Post by rebegin on 2009-03-08
hey Victor Rossetti, 
i've just tried your suggestion and it seems that the transfer between the phone and my laptop is working both ways though it's really slow (pc -> phone: 70kbyte/s, phone -> pc: 50 Kbyte/s but this second one seems to be increasing slowly)
it would be much better to get the transfer work through wlan. is there any chance to make putty or anything else to work as a kind of ssh server on the phone so we could use sshfs to mount it's drive. any further idea?
sorry for my english...

---

### Post by Victor Rossetti on 2009-03-09
> **rebegin said:**
> hey Victor Rossetti, 
i've just tried your suggestion and it seems that the transfer between the phone and my laptop is working both ways though it's really slow (pc -> phone: 70kbyte/s, phone -> pc: 50 Kbyte/s but this second one seems to be increasing slowly)
it would be much better to get the transfer work through wlan. is there any chance to make putty or anything else to work as a kind of ssh server on the phone so we could use sshfs to mount it's drive. any further idea?
sorry for my english...

Hi Rebegin..

as far as i know, there are no SSH servers for symbian at this moment, and my coding capacities are not far than the "Hello World" program. But I think that putty could be adapted to the touch interface in Symbian S60 5th. using the virtual keyboards. That would give us at least a simple SSH and SFTP client. May be someone will come out with a solution soon. In the meantime I'm still looking for the upnp implementation in 5800. 
Thanks for your response...

Victor

---

### Post by meborc on 2009-03-10
for the "moving the cursor when typing" question a page back, i just simply click the text with the stylus at the point i want the cursor to appear... i can also select text and copy/paste...

bluetooth will always be slow... it is said so even in the manual, the fastest way to transfer files is using the usb cable... you could try an ftp addres through the web browser (have not tried miself)

for all of you interested in SSH *LIKE ME* :) i was able to install AND use [MidpSSH]("http://www.xk72.com/midpssh/"), but the text is way too small for my eyes... and the text imput takes time (click on the command line... type... click ok... click ok again... etc)

---

### Post by rebegin on 2009-03-12
i have the solution for the wifi transfer.
two ways:
1. use this program to create supereasily a webpage from where you can download files with the phone(worth to check out this one anyway)
[http://stackp.online.fr/?p=45](http://stackp.online.fr/?p=45)

the problem of this was that the transfer rate was only 130 Kbyte/s max(from the phone to my pc it was 300 kbyte/s). is it because of the phone? is it possible that the speed is locked somehow? i cannot imagine anything else as my wifi network works great, i can watch films from my other pc and usual transfer rate is 3-4 Mbyte/sec...

2. look for SymSMB in a search engine :) - i have not tried this one yet but it sounds good. you can use it with samba.

nr.2 has some problem with signing...any general solution for that? i have tried freesigner so far but did not work :S

---

### Post by rebegin on 2009-03-14
even easier sharing (and folders included), suggested on the mentioned homepage in the previous post:
enter the folder you want to share and type:
python -m SimpleHTTPServer

then navigate your phone's browser to: your-pc's-ip:8000

---

### Post by rootie on 2009-03-19
Random tip regarding music playback and podcast functionality: [http://blogs.s60.com/2007/12/categories_for_music_and_podca](http://blogs.s60.com/2007/12/categories_for_music_and_podca)

I haven't read the user manual so this may already be known to more careful owners. :P

---

### Post by rootie on 2009-03-29
I want to develop an alternative OS for the 5800 xpressmusic. All those little inconveniences in the UI, in the software, etc are getting to me. However I have no practical knowledge for such a feat, and I barely know any modern programming language. I don't know anything about hardware either. Also, as far as I've read, no one's ever mentioned Android running on the 5800, only the N95.

Basically this is the nontechnical version of what I want to achieve:

> Extensibility (basically, make the OS and the original programs open-source)

And actually, when that's been achieved, all the rest will follow:

> separate input preference defaults and settings a.) per program b.) for password input c.) for utilities (alarm clock, calculator)
> ease of setting default programs [i have opera mini installed, but can't set it as default browser]
> browsing of phone memory over USB [is there any way this is possible from a technical standpoint? i notice how S60 takes the memory card offline when it's being accessed over USB.]
> linux [and everything-else] integration
> 'default views' (e.g. for music player -- I want to see the 'now playing' screen when I start it up)
> easy UI/homescreen customization (litestep comes to mind)

and then comes the opening of the API for users to come up with stuff like

> a user-friendly to-do list
> decent handwriting recognition (oh should that have come in the above list?)
> keyboard layout customization (dvorak, anyone?)
> countdown timer (!!!)

And of course all this has to take advantage of all the cool hardware the phone comes with.

So tell me, what's the technical version of the above? That is, how crazy am I?

---

### Post by t0n1 on 2009-04-29
That's quite a move. However, methinks that a phone has to be built from the ground up to use Android, not retrofitted. Not that it is not possible, just a hassle.

Unrelated to that, the latest version of Ubuntu, 9.04, finally brought proper Rhythmbox integration for me. I'm such a happy panda now %)

---

### Post by t0n1 on 2009-05-11
Through trial and error I found an optimal cover art size for the 5800. That is, the cover art image embedded in the mp3 files.
It's 250 x 250, for some reason. This way, the image is the largest when an mp3 file is played using the phone's media player.

---

### Post by TylerMD on 2009-05-11
> **t0n1 said:**
> Through trial and error I found an optimal cover art size for the 5800. That is, the cover art image embedded in the mp3 files.
It's 250 x 250, for some reason. This way, the image is the largest when an mp3 file is played using the phone's media player.

good to know, thanks for sharing

---

### Post by elie00 on 2009-05-26
I've had my 5800 for 3 month now and I'm pretty happy with it, I'm a heavy user so my battery last for a maximum of 2 and a half days but it takes 30 min to charge it so I'm good hehe 

but i like to listen to music and fill the 8GB SD card with my music but i need to install Nokia Music/OVI to do that!

any idea how to do that? I tried copy pasting the mp3 files but the phone didn't recognize them!!

any tips for that??
i've tried installing it with Wine but it didn't work!

---

### Post by rebegin on 2009-05-26
elie00,

you can simply copy your mp3 files to the microsd card, and the phone will search for mp3 files on it. if it doesn't happen than when you start the music player app, click options and rescan collection(or something similar, i have another language on it)...

---

### Post by TylerMD on 2009-05-26
> **elie00 said:**
> but i like to listen to music and fill the 8GB SD card with my music but i need to install Nokia Music/OVI to do that!

any idea how to do that? I tried copy pasting the mp3 files but the phone didn't recognize them!!

any tips for that??
i've tried installing it with Wine but it didn't work!

You don't need Nokia software to add MP3 to the phone. You can do it the following way:

* Connect the phone to your PC in Storage mode and copy the MP3 files to the card. I guess you already did that

* On the phone: Go to your Music Library (Media key -> Music player) and then refresh the library (Options -> Refresh Library).

The phone will then look for new MP3s.

---

### Post by elie00 on 2009-05-27
> **TylerMD said:**
> You don't need Nokia software to add MP3 to the phone. You can do it the following way:

* Connect the phone to your PC in Storage mode and copy the MP3 files to the card. I guess you already did that

* On the phone: Go to your Music Library (Media key -> Music player) and then refresh the library (Options -> Refresh Library).

The phone will then look for new MP3s.
hey thx TylerMD, thx for the tip,

when i copied the MP3 (3 month ago when i got the phone) and didn't know how to listen to them i deleted them, but now my card is "read only" !! allthought it connected it as mass storage device, 
FYI i had copied them from Windows not Ubuntu!! and i don't have windows anymore (thank God in a way)
i tried to change the property of the card but it wasn't successfull
i'll try poking inside the phone to see if it's a phone thing anyways if u have an idea about it i'd appreciate it!
thx

---

### Post by rebegin on 2009-05-27
> **elie00 said:**
> 
... but now my card is "read only" !! allthought it connected it as mass storage device...

try to check it with gparted, or reformat, or maybe could copy the files to card as root but i don't think it is a good way.

hope it helps.

i also have some problems to copy files using symsmb (samba share on the phone, so you can copy files through wifi for example...) when it's connected, krusader shows r?x as attributes...and i cannot copy file into most directoy, but in some of them it works...any idea?

---

### Post by TylerMD on 2009-05-27
> **elie00 said:**
> now my card is "read only" !! allthought it connected it as mass storage device

I don't see any options on the mobile phone to set the card as read only so maybe it is a permissions issue. If the card is automatically mounted at /media/SDCard try the following:

```

sudo chmod 777 /media/SDCard

```

and then try to copy some files. Tell us what happen.

---

### Post by curtis1552 on 2009-07-04
Sharing my experience with my 5800.

Bluetooth did not fully work until i installed another application, gnome-obex-server 0.11.0. This allowed the computer to receive files, which it would not before. 
I also have Bluetooth Applet 1.8 running. 

I have had no issues with rhythmbox putting music on the phone, but it does have some quirks. You cannot use it to make playlists or transfer playlists. You can select all the songs in a playlist and drag them to the phone, or you can cut and paste them into nautilus into a folder of your choice. 

Now, the newest, I decided to try and figure out if there's anything i can do to get premade/working playlists. 

I have not found the playlists yet, but the full song database is located at (mountpoint)/Private/10281e17 on my phone. It is a SQlite database file, and after installing the database browser (from the 9.04 repos) I am able to browse the file a bit. 

I have minimal database experience, so i'm not sure what can be done with it at this point. Please share if there are any ideas

---

### Post by t0n1 on 2009-07-09
> **curtis1552 said:**
>  gnome-obex-server 0.11.0.


Where did you get this package from? Could not find it in the repository.

---

### Post by Post Monkeh on 2009-07-11
quick question. my laptop doesn't have bluetooth, and i'm unable to get my 
nokia phone to connect to the laptop using the usb cable except for file transfer. can the bluetooth connection be used to use the phone's internet connection.

i often have to use my laptop away from a fixed internet connecion and on my old phone (sony ericcson k850i) i was able to just plug it in, select phone mode, then ubuntu immediately connected to the internet.  the nokia just doesn't want to play ball at all.

---

### Post by stwschool on 2009-07-11
A quick google has shown me a possible solution to your problem. [http://www.joiku.com/?action=products&mode=productDetails&product_id=310](http://www.joiku.com/?action=products&mode=productDetails&product_id=310) sets your phone to create a wi-fi hotspot, which your linux box should be able to connect to easily. Software's free for the basic version, which should do a job for you. Let me know how you get on as that's a nice-looking phone.

---

### Post by TylerMD on 2009-07-13
stwschool is right. I tried Joiku Spot with Ubuntu and works fine.

---

### Post by GuruX on 2009-07-13
5800 supports the MTP-transfer protocol. So, to browse files with USB cable, but without using the storage mode.
```

sudo apt-get install mtpfs
mkdir ~/5800 or whatever you'd like to name your folder for mounting the phone
mtpfs ~/5800

```
mtpfs mounts mtp devices in nautilus just like external HDDs.

---

### Post by szadek_ on 2009-07-14
For everyone here with bluetooth problems , its easy to use nokia 5800 .I have one , it works perfectly .

First install blueman , then reboot your computer , and then , turn on bluetooth on the phone , and on blueman just click search and your phone will appear =) .

Easy =) .

---

### Post by Post Monkeh on 2009-07-14
> **GuruX said:**
> 5800 supports the MTP-transfer protocol. So, to browse files with USB cable, but without using the storage mode.
```

sudo apt-get install mtpfs
mkdir ~/5800 or whatever you'd like to name your folder for mounting the phone
mtpfs ~/5800

```
mtpfs mounts mtp devices in nautilus just like external HDDs.

when i connect my phone and try to open the 5800 directory, i get a "transport endpoint is not connected" error.

i think the setup is right, the 5800 directory appears in my "places" menu as if it was an exernally conected drive, but it just doesn't let me open it.
should i select ANY mode when i connect my phone, or just leave the phone alone?

---

### Post by GuruX on 2009-07-17
> **Post Monkeh said:**
> when i connect my phone and try to open the 5800 directory, i get a "transport endpoint is not connected" error.

i think the setup is right, the 5800 directory appears in my "places" menu as if it was an exernally conected drive, but it just doesn't let me open it.
should i select ANY mode when i connect my phone, or just leave the phone alone?

Hmm, no I don't use any special mode. I find my 5800 in places menu and it works fine.

But I have seen quite a lot of that error message in nautilus lately. Especially when I'm browsing my SMBs. I think it might be related to gvfs or nautilus. Not mtpfs.

---

### Post by desperado666 on 2009-07-25
> **m3topaz said:**
> I've got multisync working quite happily with Intrepid and the 5800 - however using Evolution not Thunderbird. Contacts and Calendar are fine with it - worked first time I set it all up.

How ? Want to sync it via bluetooth and multisync. Cant get a connection :(

---

### Post by plb on 2009-07-25
I don't know why nokia don't port OVI suite to Linux..it's QT..we should start a petition lol

---

### Post by curtis1552 on 2009-07-26
> **t0n1 said:**
> Where did you get this package from? Could not find it in the repository.

Oops, I listed the program name/version, not package. 
I believe that it's obexpushd and will allow receiving of files to the computer from another device.

---

### Post by desperado666 on 2009-07-26
> **plb said:**
> I don't know why nokia don't port OVI suite to Linux..it's QT..we should start a petition lol

why not ? Start here [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Bealer on 2009-08-21
Been using Rhythmbox to put music onto my 5800.

It works fine for MP3's. However, FLAC's don't get transcoded, and OGG files get changed to M4A's.

Bit annoying, need to figure out a way to tell Rhythmbox to transcode my OGG and FLAC music to MP3.

---

### Post by kija on 2009-11-01
Does anyone know a way to control ubuntu with 5800 using bluetooth.. like changing songs in rhythmbox/banshee or changing slides.. thats the only thing im missing from w810.

---

### Post by simplyw00x on 2009-11-27
> Does anyone know a way to control ubuntu with 5800 using bluetooth.. like changing songs in rhythmbox/banshee or changing slides.. thats the only thing im missing from w810.
You can use [recmuco]("http://code.google.com/p/remuco/") to control all forms of media player, and more general control can be had with [anyremote]("http://anyremote.sourceforge.net/dload.html") &#8212; the former is Symbian, the latter a Java Midlet.

Touch wood, but I'm currently having a good experience syncing an N97 mini with evolution using opensync, and the general gist of [these instructions/]("http://www.blogtecnologico.it/2007/12/pc-suite-no-grazie-sincronizzare-il-tuo-cellulare-nokia-con-linux/") (I don't speak Italian, but it seems to make a lot of sense) &#8212; for reference, the bluetooth channel was "7" for me (not "10" as they suggest).

No luck getting MTP working yet, and NetworkManager dies horribly when trying to use it as a modem, but otherwise pretty happy!

---

### Post by simplyw00x on 2009-11-27
(double post — thanks, Virgin Media)

---

### Post by Post Monkeh on 2009-12-23
> **simplyw00x said:**
> You can use [recmuco]("http://code.google.com/p/remuco/") to control all forms of media player, and more general control can be had with [anyremote]("http://anyremote.sourceforge.net/dload.html") — the former is Symbian, the latter a Java Midlet.

Touch wood, but I'm currently having a good experience syncing an N97 mini with evolution using opensync, and the general gist of [these instructions/]("http://www.blogtecnologico.it/2007/12/pc-suite-no-grazie-sincronizzare-il-tuo-cellulare-nokia-con-linux/") (I don't speak Italian, but it seems to make a lot of sense) — for reference, the bluetooth channel was "7" for me (not "10" as they suggest).

No luck getting MTP working yet, and NetworkManager dies horribly when trying to use it as a modem, but otherwise pretty happy!

is there an easy way to get an ubuntu box to run a program via a mobile phone?

i've been playing about and got remuco up and running with totem (i did try vlc but couldn't manage to figure out how to switch my videos to fullscreen from the phone) , but it's only useful if i actually have totem running.
eventually what i plan to have is my pc hooked up to the tv in my living room, though it would be in the study. this bit isn't a problem, but if the pc is on, but totem isn't running, then you can't use remuco .
i've been able to use putty to ssh into the pc, but while i found out how to make totem run in the current login using [export DISPLAY=:0]("http://www.linuxquestions.org/questions/linux-networking-3/vlc-remote-access-with-ssh-and-command-line-676844/"), it doesn't continue to run when i exit putty, the totem windows closes too.

i know i could just have totem always running just in case i fancy watching a film, but it would be a bit of a waste of resources

---

### Post by josno on 2009-12-23
> **Post Monkeh said:**
> i've been able to use putty to ssh into the pc, but while i found out how to make totem run in the current login using [export DISPLAY=:0]("http://www.linuxquestions.org/questions/linux-networking-3/vlc-remote-access-with-ssh-and-command-line-676844/"), it doesn't continue to run when i exit putty, the totem windows closes too.
Can't you just get round this by running Totem in the background by appending & to the end of the command e.g.
```
$ totem -arg1 -arg2 **&**
```

---

### Post by Post Monkeh on 2009-12-23
> **josno said:**
> Can't you just get round this by running Totem in the background by appending & to the end of the command e.g.
```
$ totem -arg1 -arg2 **&**
```

nice idea, but it still closes when i exit the ssh session. i think the "&" just allows you to regain control of the terminal window. the running application is still tied to the terminal session

---

### Post by Post Monkeh on 2009-12-23
your suggestion did give me a kick towards a workaround though.
if i use gnome-open to open a file instead of totem, then totem stays open when i leave the ssh session.

now i just need to find how to make putty send the commands automatically when i log in and i'll be sorted.

---

### Post by debsankha on 2010-01-07
@Bealer:
Did Rhythmbox recognize your Nokia 5800 automatically? In my laptom running Karmic it doesn't . I've already  tried bbldox's suggestion without any result. Please help!

---

### Post by Bealer on 2010-01-20
Just tried it and no, it's not working any more!

I was using it with 9.04 before, now I'm on 9.10. Guess it not working and what people have mentioned, does tie in with in the HAL changes and deprecation being made in Ubuntu.

Rhythmbox picks it up as an "Unknown Device" in MTP mode. I'm having to use it in Mass Storage mode to get files onto it at the moment until I can figure out a fix.

---

### Post by bigbrovar on 2010-01-20
> **rootie said:**
> I've had my eye on the 5800 for a while now. I'm actually thinking of buying it within the week, but I can't help but wonder if there are any *big* issues regarding Nokia - Linux compatibility, along the lines of firmware updates, and the like. I know that the PC suite doesn't work at all, but should anything else make me think twice about this purchase?

Thanks in advance :D

**firmware updates**
There is currently no way to update your Nokia Symbian based device from Linux, this is because the neither the PC Suit or the Ovi suit which is needed for the update has a Linux version. However I have been able to get both my E72 and E71 (former phone) work with windows xp on virtual-box, using the virtual usb. It is very easy and works like a charm. Beside many new Nokia phones using what is called Over The Air updates (OTA) which basically allows you to install FW updates directly from your device. You have an application that you can use to search for updates and if any is available it downloads it and installs it on your phone without the need for a PC.

**Contact Syncing**
I just use the OVI sync suite which allows me to sync my connects, bookmarks,notes, and SMS? to the ovi.com directly from my phone using the wifi/ or data connections. and I can always restore the contacts to another Nokia phone or same phone in case I flash the phone. It works very well and I was able to use it to backup my E71 ---> E72 with no issues what so ever. 
 
**Concerning Syncing of Music**
I wrote a tut on how I got my **[Nokia E71 to sync well with Rhythmbox, ]("http://bigbrovar.aoizora.org/index.php/2009/09/14/transcode-and-sync-music-to-your-portable-music-player-in-linux/")**
all you need is a phone that has mass storage support ( meaning it can be seen as a mass storage device when connected to a PC) AFAIK almost very recent (since 2008) Nokia phone support is usb-storage compliant. which should include the Nokia 5800.
The good thing about the fix is that even if you have music in ogg format it will encode them to mp3 and sync them on the fly. I use it and it works like a charm all the time.

**Tethering**  Most when using the usb cable, your nokia is detected and auto configured by network manager and you are good to use your phones internet to sync with Ubuntu right Out of the box. If you dont use network manager then wvdial always works fine with every Nokia i have tried it with. Also if you use a bluetooth manager like **[blueman]("http://bigbrovar.aoizora.org/index.php/2009/02/14/blueman-an-awesome-bluetooth-manager-for-ubuntu/")** you can easily tether using the bluetooth of your phone. 

yeah so thats it.. hope this helps you in making your choice :)

---

### Post by Joe Question on 2010-02-23
> **bbldox said:**
> Hey rootie. You can disable it by turning sound completely off (i.e. changing profile to "Silent" or "Meeting").

To make your camera silent you can personalize any profile you are using.

e.g. menu-settings-personal-profiles-general-personalise-warning tones-off

;)

---

### Post by rafadev on 2010-02-23
I've had a really weird problem for a long time, with two different phones... I'm now using the latest firmware version and it seems to have got better but its still happening.

I usually connect the 5800 as mass storage, then copy audio files to sounds/. Sometimes, though, in the middle of file transfer I get an error, transfer interrupts or stalls and when I disconnect the cellphone the filesystem starts to corrupt... Some files will still be there but corrupt. It starts working worse and worse until it's unusable and I have to format.

Anyone had some similar issue? I've read this one that gave me a hint, apparently the cell's USB chip sucks
[https://launchpad.net/bugs/324315](https://launchpad.net/bugs/324315)

Thanks!

---

### Post by the hoplite on 2010-03-19
I'm using the Nokia 5800 with Banshee, only needed to install mtpfs first, now it runs great, recognised immediately and transferring cover art flawlessly. The only problem I have is that there's no way to manage 5800's playlists directly from Banshee. It seems to work but once disconnected the playlists don't appear on the phone. Anyone has the same problem?

---

### Post by smartinjose on 2010-03-19
It is not possible to update Nokia 5800 firmware on Linux as we don't have Linux versions of Ovi suite and PC suite. You can use cCam application if you want to block Shutter sound in Nokia phones (official site [http://pachome1.pacific.net.sg/~welic/cCam.html](http://pachome1.pacific.net.sg/~welic/cCam.html)). But i don't know if it will work with Nokia 5800 as its an S60 V5 phone.

---

### Post by megamaced on 2010-03-23
The nokia 5800 doesn't show up in rhythmbox, doesn't matter if i choose mass storage mode or pc suite mode. However it shows up in Banshee (using mass storage mode (i haven't tried pc suite mode with banshee))

i am using ubuntu lucid beta (fully updated) but i also have this issue in karmic.. how can i solve it?

---

### Post by averybigfish on 2010-04-08
Hi

I'm sorry, but I can't seem to find the information I need from this thread, although my question has probably (to a degree) been answered: could someone possibly post a comprehensive tutorial on how to get rhythmbox to see and be able to copy music to a usb-connected nokia 5800 on ubuntu 9.10? Copying mp3 files directly is a cumbersome method... it would be far better to use rhythmbox to do it. It would also be nice if rhythmbox would do album art...

Thank you in advance!

---

### Post by the hoplite on 2010-04-08
I don't think there's a way to get 5800 working with rhytmbox, anyway banshee does a great job, playlists apart..

---

### Post by averybigfish on 2010-04-08
Ok, thanks. I hope Banshee doesn't mess up my Rhythmbox folder structure... It probably won't. Enjoy your phones, as I will!

---

### Post by imopen on 2010-04-20
> **the hoplite said:**
> I'm using the Nokia 5800 with Banshee, only needed to install mtpfs first, now it runs great, recognised immediately and transferring cover art flawlessly. The only problem I have is that there's no way to manage 5800's playlists directly from Banshee. It seems to work but once disconnected the playlists don't appear on the phone. Anyone has the same problem?

I'm using a nokia 5800 with Banshee but I am not able to trasnfer cover art, they are in Banshee but once transfered music on 5800 I don't see them on Music Player of the phone.

How do you transfer them?

Thanks :)

---

### Post by the hoplite on 2010-04-20
That's strange, I haven't had any problems with cover art. Are the jpegs those downloaded by Banshee or are they set by you? If the latter maybe the format's not right.
I would also try to change the theme on the 5800, just in case.

---

### Post by imopen on 2010-04-20
> **the hoplite said:**
> That's strange, I haven't had any problems with cover art. Are the jpegs those downloaded by Banshee or are they set by you? If the latter maybe the format's not right.
I would also try to change the theme on the 5800, just in case.

sorry, I don't understand.

aren't the cover embedded in the mp3 file?

I told Banshee to download the covers, I have all the library with the right covers. 

But after have transferring the mp3 files on the nokia I don't see the cover on music player. Should I transfer the covers in other way? :confused:

---

### Post by the hoplite on 2010-04-21
No, the cover file should be just a jpeg which you can add manually to the album folder. When automatically downloaded Banshee should store it soewhere in his .conf file I think. Maybe the problem is on the phone's end, try changing the theme or the default player.

---

### Post by Tom Mann on 2010-04-21
> **imopen said:**
> I'm using a nokia 5800 with Banshee but I am not able to trasnfer cover art, they are in Banshee but once transfered music on 5800 I don't see them on Music Player of the phone.

How do you transfer them?

Thanks :)

The 5800 retrieves it's images from the tag of the music file, so you need a method to embed the images into the music file.

And for people failing with MTP, use disk mode :KS

---

### Post by imopen on 2010-04-21
> **Tom Mann said:**
> The 5800 retrieves it's images from the tag of the music file, so you need a method to embed the images into the music file.

And for people failing with MTP, use disk mode :KS

yes, I found the solution.

I downloaded Album Cover Art Downloader from [http://www.unrealvoodoo.org/hiteck/projects/albumart/](http://www.unrealvoodoo.org/hiteck/projects/albumart/)

Given a directory it retrieves all cover art and embeds them into the files in a tag of your choise, chosing "front cover" tag it's visible from Nokia 5800 music player :guitar:

Hope it helps others ;)

---

### Post by desperado666 on 2010-08-20
If Rhythmbox doesnt discover your Nokia 5800 at all create a file named 

.is_audio_player

in your nokia 5800 root folder. If that doesnt help then edit this file and paste that 
audio_folders=Music/
folder_depth=2
output_formats=audio/mpeg

in save and connect your 5800 again. Now it should work.

---

### Post by perseas on 2010-09-14
Actually kid3( in the repositories) does an excellent job on embedding cover art in 5800. it also offers the choice to automatically search Google images for album art. as mentioned above 5800 recognizes cover only in front cover mode. one has only got to tweak "edit" in kid3. also to my knowledge, 5800 recognizes genre only if its text and not unicode. kid3 allows to tweak that also. quite a program if i might say.

---

### Post by sommotommo on 2010-09-18
Hi

there are some **problems** with **ogg**:


**[SIZE="5"]1[/SIZE]**     You can play **ogg** using ***Folderplay*** but isn't more at:

    **_[SourceforgeFolderplay]("http://sourceforge.net/projects/folderplay/")_**

    you find it on the web for instance here:

    [B][U][NokiaseriesFolderplay]("http://www.nokiaseries.net/2322/folder-play-1-00-s60v5.html")
[/U][/B]
    but the certificate is expired, probably you could use this:

    [B][U][ODPA]("http://cer.opda.cn/en/index.php?module=index&amp;action=login")
[/U][/B]
    Have installed ***Folderplay*** on my son's **5800** (more than one year ago) and works ***fine***.



**[SIZE="5"]2[/SIZE]**     It will come too:

    **_[SymbianOggplay]("http://symbianoggplay.sourceforge.net/")_**

I use it on my **5320 Xpm**(*Symbian v.3*) and it works ***fine***.


**[SIZE="5"]3[/SIZE]**     Following isn't mature:

[B][U][VLC for Symbian]("http://mahaserver.github.com/MHSVLC/")
[/U][/B]

Hope it will arrive asap.


Moreover :

**[SIZE="5"]4[/SIZE]**     As far **sobstitute** of **Nokia PC** Suite the following is not jet mature also:

[B][U][Nokuntu]("http://sourceforge.net/projects/nokuntu/")
[/U][/B]

Hope it will arrive asap.
#####################################################


Is somebody knowing other **ogg player** or a **plugin** for default Nokia player?


Thanks for attention

---

### Post by Pocio on 2010-11-13
Hi all!!
Using the .is_music_player trick I can sync my music from rhythmbox to the Nokia 5800 both connecting the phone as "nokia pc suite" or as "storage device".

However, I can not see album artwork on the telephone...I try all the suggestments above, including the use of Album Art Cover Downloader...but nothing.

Can someone help me?

Thank you so much!

---

### Post by Tur Third on 2010-11-30
I have a nokia musicxpress 5530, In order to get the ablum images on the phone you have to embed them in the individual MP3 files themselves.

The only way that I have found to do this is to use windows software :(. I use 'Media Monkey'. I would be interested if anyone has found a way of doing this in Linux.

---

### Post by zob on 2010-11-30
I'm quite sure that EasyTAG does that too (rather, I know it does). Look for the pictures tab in the ID3 area.

---

### Post by Pocio on 2010-11-30
thank you Tur Third!

@zob: easy tag is the app that I usually use to set album art for my songs, btw when I transfer them into the phone the songs does not have the album art...The pictures are automatically transfer in the picture folder and I have to set them manually

---

### Post by zob on 2010-11-30
But can't you embed them the same way media monkey does. On my system it seems to work like that. I have to add though, that I haven't come around to transferring mp3-files to my newly aquired second hand nokia 5800. But all others players I've tried on ubuntu seem to read the embedded picture from the mp3-file not from a folder.jpg-file. But I might be unaware of something here.

---

### Post by Pocio on 2010-11-30
> **zob said:**
> But can't you embed them the same way media monkey does. On my system it seems to work like that. I have to add though, that I haven't come around to transferring mp3-files to my newly aquired second hand nokia 5800. But all others players I've tried on ubuntu seem to read the embedded picture from the mp3-file not from a folder.jpg-file. But I might be unaware of something here.

easytag has always works for me but, I repeat, as I said before, NOT with nokia 5800. Try yourself.

---

### Post by josno on 2010-11-30
> **Tur Third said:**
> I have a nokia musicxpress 5530, In order to get the ablum images on the phone you have to embed them in the individual MP3 files themselves.

The only way that I have found to do this is to use windows software :(. I use 'Media Monkey'. I would be interested if anyone has found a way of doing this in Linux.

Try [MusicBrainz Picard](http://musicbrainz.org/doc/PicardDownload). It fixes the tags on your MP3s by looking them up in the MusicBrainz database and downloads album art, embedding them in the file (iirc).

---

### Post by Tur Third on 2010-12-08
Thanks josno.:)

Musicbrainz Picard does seem to embed the artwork in the files ok. Not transferred to phone yet, but can't see a problem

I am struggling a bit with it. It is tricky if it does not recognise all the tracks, also am not sure if I can add my own choice of artwork yet. However will give it a go.

---

