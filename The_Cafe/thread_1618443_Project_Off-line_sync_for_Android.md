---
title: "Project: Off-line sync for Android"
date: 2010-11-10
forum: The Cafe
---

### Post by arkroan on 2010-11-10
As **aysiu** said, if the government and the big corporations want the information, they will get it. I try to keep a small footprint on the Internet and on the information I disclose to the public just because I HATE TARGETED ADVERTISEMENT.. And I believe Marketing People should die a painfull death.. (just like Hicks said).

Now, since I got that out of me , I would like to bring the discussion back to the original form: 
Ubuntu sync with Android!

I have decided to go ahead and try to create a sync application between my HTC Hero and Evolution in Ubuntu. 
**ColdFusionEESG** if you want to give a hand it will be most appreciated. We need of course the help of a Linux-able person. And by able I mean someone that can develop drivers for usb devices. I am guessing that kernel compilation skills might be needed. - Any Linux specialists out there that share our cause???
 
I am gonna try and sneak a peek to the packets exchanged betweeen the Hero and the HTC Sync at first. Then if I manage to decipher any usable information I am going to try and replicate the communication in a Linux terminal.

Lets see what happens.

---

### Post by aysiu on 2010-11-10
This is splintered off [a thread that had devolved into general discussion about Google and privacy.](http://ubuntuforums.org/showthread.php?t=1383820)

There were definitely some people interested in the practical aspects of setting up an offline sync for Android, so that's what this thread is for--to discuss how to do that and perhaps coordinate efforts.

---

### Post by markp1989 on 2010-11-10
Would love to see this happen, i normally sync my android over the "air" but if im in a situation with no internet i would love to be able to sync offline. 

I dont have the skills to help as a dev, but im willing to help test.

---

### Post by arkroan on 2010-11-12
Update:

Ok, I have now started researching the requirements of writing a program that could sync an Android phone and Evolution mail client.

From my trivial experience of how Linux works I understand that, at least for now, I will write a usb driver for use in userspace.
This means that I will use the *libusb* API to develop my driver.

I have already started reading the USB 2.0 specification ( no previous experience with USB whatsoever) and digging into how Linux handles device drivers. - Thank God (the Linux community) for the **Linux Device Drivers** publication in [http://lwn.net/Kernel/LDD3/]("http://lwn.net/Kernel/LDD3/").

So for now.. Just a steep learning curve..

Next task would be to sneak a pick to the data exchanged between the Windoze HTC Sync and the HTC Hero phone. 

If any of the Linux enthusiasts have anything to suggest that will make this task easier please feel free to post it here.

As always, advice from *Linux Elders* is highly appreciated

Regards.

---

### Post by aysiu on 2010-11-12
Forgive my ignorance, as I'm not a developer or programmer of any kind, but wouldn't it just be a program that just looks at your contacts and then syncs them?

I would think (again, I'm not a programmer, so please correct me if I'm wrong) you'd have two programs--one an Android app and one a regular Linux/Windows/Mac program for your computer. The Android app would take your contacts and sync them to a file on your SD Card, and then the other on the computer would, once your SD Card was mounted, sync the contacts from the SD Card to the computer.

I'm not sure how a USB driver would help in that scenario.

---

### Post by ColdFusionEESG on 2010-11-12
> **aysiu said:**
> Forgive my ignorance, as I'm not a developer or programmer of any kind, but wouldn't it just be a program that just looks at your contacts and then syncs them?

I would think (again, I'm not a programmer, so please correct me if I'm wrong) you'd have two programs--one an Android app and one a regular Linux/Windows/Mac program for your computer. The Android app would take your contacts and sync them to a file on your SD Card, and then the other on the computer would, once your SD Card was mounted, sync the contacts from the SD Card to the computer.

I'm not sure how a USB driver would help in that scenario.

Although that route would be possible, I would expect most people would prefer not to have to take out their SD card and mount it on their PC/laptop in order to perform the sync.

Instead, they would more likely prefer the method that has been traditionally used....connect the device to the PC via USB and sync.

To do so of course requires a USB driver ;-)

Cheers

---

### Post by aysiu on 2010-11-12
> **ColdFusionEESG said:**
> Although that route would be possible, I would expect most people would prefer not to have to take out their SD card and mount it on their PC/laptop in order to perform the sync.

Instead, they would more likely prefer the method that has been traditionally used....connect the device to the PC via USB and sync.

To do so of course requires a USB driver ;-)

Cheers Do you own an Android phone?

To mount the SD Card, you don't physically remove it from the phone. You actually plug the phone in via USB to your computer, and then your phone will ask if you want to mount the SD Card to your computer. That's what I'm talking about.

---

### Post by arkroan on 2010-11-12
That method you are describing **aysiu** is exactly the same as removing the card from the phone and plug-in it to your card reader in your PC.

The aim here is NOT to save the contacts on the SD-Card and retrieve them from that card. But to "talk" directly to the phone and "convince" it to hand over the contacts directly to the pc.

The contacts reside usually in the internal phone memory (or SIM) so by having a driver able to "talk" to the phone, you are able to instruct it what to do. That is of course, to instruct it to send all the contacts from the internal phone memory.

Hope this helps your understanding a bit more :)

---

### Post by ColdFusionEESG on 2010-11-12
> **aysiu said:**
> Do you own an Android phone?

To mount the SD Card, you don't physically remove it from the phone. You actually plug the phone in via USB to your computer, and then your phone will ask if you want to mount the SD Card to your computer. That's what I'm talking about.

No I don't....I thought that was pretty obvious at this point ;-)

So back to your original idea....

It could very well work, but as a programmer it seems to me to be an extra step (copying to one location on the phone only to be read by the PC).

That said, I build web-based business applications and not phone syncing apps....so I guess we'll see how this thread unfolds...

Cheers

---

### Post by aysiu on 2010-11-12
> **arkroan said:**
> That method you are describing **aysiu** is exactly the same as removing the card from the phone and plug-in it to your card reader in your PC.

The aim here is NOT to save the contacts on the SD-Card and retrieve them from that card. But to "talk" directly to the phone and "convince" it to hand over the contacts directly to the pc.

The contacts reside usually in the internal phone memory (or SIM) so by having a driver able to "talk" to the phone, you are able to instruct it what to do. That is of course, to instruct it to send all the contacts from the internal phone memory.

Hope this helps your understanding a bit more :)
From a programming perspective it's exactly the same, but from the end-user perspective, it's not. The end-user just plugs in the USB cable either way.

I was addressing this concern: > I would expect most people would prefer not to have to take out their SD card and mount it on their PC/laptop in order to perform the sync. Most people would not be taking out the SD card. That was my point.

It's not efficient (again, from the programmer perspective, not the end user one) to have to copy to one location only to copy to another location, but it certainly is easier than having to figure out how to interact directly via USB.

---

### Post by arkroan on 2010-11-12
> **aysiu said:**
> 
It's not efficient ... to have to copy to one location only to copy to another location, but it certainly is easier than having to figure out how to interact directly via USB.

Well, that is why this is a good challenge!!
Many things are not easy to figure out at first, but once you figure them out you can be efficient AND knowledgeable!
Windows are made to make things easier, many people choose Linux because is more efficient.

- Plus if nobody tried to figure out how to interact directly via USB in a windows environment, you would still have to copy from one location to another and then again.. 

It is all about efficiency ( for the developer ) and ease of use (for the end user).

---

### Post by ColdFusionEESG on 2010-11-12
> **aysiu said:**
> 
It's not efficient (again, from the programmer perspective, not the end user one) to have to copy to one location only to copy to another location, but it certainly is easier than having to figure out how to interact directly via USB.

Easier does NOT equal better....if you start an app in a sloppy manner you will pay for it later ;-)

---

### Post by Paqman on 2010-11-12
> **ColdFusionEESG said:**
> Easier does NOT equal better....if you start an app in a sloppy manner you will pay for it later ;-)

It's not sloppy if it's properly planned. It seems like it might be hugely simpler to grab a file off the SD card, so why not release a first version that does it this way, and in the meantime work on the more complicated concept for a subsequent release? That would give you space to work on things like a good interface right from the start, and would mean people have something to use sooner rather than later.

Just a thought.

---

### Post by ColdFusionEESG on 2010-11-12
> **Paqman said:**
> It's not sloppy if it's properly planned. It seems like it might be hugely simpler to grab a file off the SD card, so why not release a first version that does it this way, and in the meantime work on the more complicated concept for a subsequent release? That would give you space to work on things like a good interface right from the start, and would mean people have something to use sooner rather than later.

Just a thought.

....and a perfectly valid thought at that....just not how I develop....I do my best to do it as "right" as possible the first time...but hey...I'm not steering this ship ;-)

---

### Post by arkroan on 2010-11-14
UPDATE:

After hours of reading the USB 2.0 specification and libusb developer's guide I have managed to retrieve the Manufacturer name of my HTC Hero using libusb and some basic C code.

....And then I found an online tutorial that demonstrated how to use libUSB to get ALL the information I needed (Vendor-Id , Product-Id ,Endpoint addresses etc) for all attached usb devices :) .

If anybody is interested on how it is done, you may find it here: 
[http://www.linuxquestions.org/linux/answers/Programming/Developing_Linux_Device_Drivers_using_Libusb_API](Developing Linux Device Drivers using Libusb API")

Here is a sample of the information gathered:
```

bus/device idVendor/idProduct
002/006 0BB4/0C99
Manufacturer : HTC
Product : Android Phone
Serial Number: MB039L9xxxxx
 wTotalLength: 55
 bNumInterfaces: 2
 bConfigurationValue: 1
 iConfiguration: 0
 bmAttributes: 80h
 MaxPower: 250
 bInterfaceNumber: 0
 bAlternateSetting: 0
 bNumEndpoints: 2
 bInterfaceClass: 8
 bInterfaceSubClass: 6
 bInterfaceProtocol: 80
 iInterface: 4
 bEndpointAddress: 01h
 bmAttributes: 02h
 wMaxPacketSize: 512
 bInterval: 0
 bRefresh: 0
 bSynchAddress: 0
 bEndpointAddress: 81h
 bmAttributes: 02h
 wMaxPacketSize: 512
 bInterval: 0
 bRefresh: 0
 bSynchAddress: 0
 bInterfaceNumber: 1
 bAlternateSetting: 0
 bNumEndpoints: 2
 bInterfaceClass: 255
 bInterfaceSubClass: 66
 bInterfaceProtocol: 1
 iInterface: 5
 bEndpointAddress: 02h
 bmAttributes: 02h
 wMaxPacketSize: 512
 bInterval: 0
 bRefresh: 0
 bSynchAddress: 0
 bEndpointAddress: 82h
 bmAttributes: 02h
 wMaxPacketSize: 512
 bInterval: 0
 bRefresh: 0
 bSynchAddress: 0
```


The most important bits of this report are:
The bus and device usb address with the vendor id (HTC=0BB4) and the usb device id(Sync Function=0C99)
```
002/006 0BB4/0C99
```

The number of usb interfaces available:
```
bNumInterfaces: 2
```

And their corresponding settings.
```

 bInterfaceNumber: 0
 bAlternateSetting: 0
 bNumEndpoints: 2
 bInterfaceClass: 8
 bInterfaceSubClass: 6
 bInterfaceProtocol: 80
 iInterface: 4
 bEndpointAddress: 01h
 bmAttributes: 02h
 wMaxPacketSize: 512
 bInterval: 0
 bRefresh: 0
 bSynchAddress: 0
 bEndpointAddress: 81h
 bmAttributes: 02h
 wMaxPacketSize: 512
 bInterval: 0
 bRefresh: 0
 bSynchAddress: 0
```

The next step now is to get samples of the usb data exchanged between the Windows PC and the HTC phone in order to determine what packet or instruction from HTC Sync initiates the synchronisation.
- a bit of reverse engineering -

This will have to wait until next weekend though..

Regards,

---

### Post by talent03 on 2010-11-15
I like this. I am eager to see where you will be able to get with this. Good luck.

---

### Post by ColdFusionEESG on 2010-11-15
> **arkroan said:**
> UPDATE:

After hours of reading the USB 2.0 specification and libusb developer's guide I have managed to retrieve the Manufacturer name of my HTC Hero using libusb and some basic C code.

....And then I found an online tutorial that demonstrated how to use libUSB to get ALL the information I needed (Vendor-Id , Product-Id ,Endpoint addresses etc) for all attached usb devices :) .

If anybody is interested on how it is done, you may find it here: 
[http://www.linuxquestions.org/linux/answers/Programming/Developing_Linux_Device_Drivers_using_Libusb_API](Developing Linux Device Drivers using Libusb API")

[snipped]

The next step now is to get samples of the usb data exchanged between the Windows PC and the HTC phone in order to determine what packet or instruction from HTC Sync initiates the synchronisation.
- a bit of reverse engineering -

This will have to wait until next weekend though..

Regards,

Great work!....1st piece down....a connection and some device details...keep up the good work arkroan!

---

### Post by arkroan on 2010-11-17
> **ColdFusionEESG said:**
> Great work!....1st piece down....a connection and some device details...keep up the good work arkroan!

Thanks ColdFusion, but I found most of the stuff out there online.. I can't really say I worked hard for it..:P

But I am learning... And I am really happy that the community provides...

I can't wait for the weekend really!!! Maybe I get the chance to provide something back as well.

---

### Post by ColdFusionEESG on 2010-11-18
> **arkroan said:**
> Thanks ColdFusion, but I found most of the stuff out there online.. I can't really say I worked hard for it..:P

But I am learning... And I am really happy that the community provides...

I can't wait for the weekend really!!! Maybe I get the chance to provide something back as well.

Online or not....you figured it out.  I always search first when I'm doing something new (to me).  There is no point in re-inventing the wheel....but hey....maybe you can improve it ;-)

FYI....I did a little searching on the Andriod Market and found quite a few apps that claim to allow for direct connection syncing without the cloud.  A lot seem like someone's first painful attempt, but good to see others are trying.  Most I saw were Windows or Mac of course ;-)

When I get a chance I'll dig deeper to get a better feel for exactly what these do.  I say that because some involve importing or exporting via CSV file, but that is NOT synchronization....even  though the app name had  "sync" in it.

Cheers

---

### Post by aysiu on 2010-11-18
Can I ask what exactly you would be syncing *to*? Would this be to a Thunderbird address book? Or something in Evolution?

---

### Post by ColdFusionEESG on 2010-11-18
> **aysiu said:**
> Can I ask what exactly you would be syncing *to*? Would this be to a Thunderbird address book? Or something in Evolution?

For me I'm looking for an Evolution solution....can't speak for others.


....and no the Ubuntu One cloud solution does not solve that for me (in case you've seen that already) ;-)

Cheers

---

### Post by arkroan on 2010-11-21
> **aysiu said:**
> Can I ask what exactly you would be syncing *to*? Would this be to a Thunderbird address book? Or something in Evolution?

I will aim for syncing with the Evolution address book since it is the standard mail client for Ubuntu.

---

### Post by glendavee on 2010-12-02
This would be a very useful app. How's progress?

---

### Post by arkroan on 2010-12-02
> **glendavee said:**
> This would be a very useful app. How's progress?

Well progress is slow.. I can only work on this on Saturdays since I have a full time job. 
I am a bit frustrated with the way Android sync works and my lack of knowledge in.. everything really... :)

At the moment I am still trying to retrieve contacts from the phone by usb cable connection.

The plan is to retrieve all contacts from the phone at first and then convert this to a sync procedure (retrieve only updated contacts).

---

### Post by stanley78 on 2010-12-14
maybe a part of work has already done...

[http://www.appbrain.com/app/com.fjsoft.myphoneexplorer.client](http://www.appbrain.com/app/com.fjsoft.myphoneexplorer.client)

that's the best sw for offline syncing and backing up phone data ever.

---

### Post by ColdFusionEESG on 2010-12-14
> **stanley78 said:**
> maybe a part of work has already done...

[http://www.appbrain.com/app/com.fjsoft.myphoneexplorer.client](http://www.appbrain.com/app/com.fjsoft.myphoneexplorer.client)

that's the best sw for offline syncing and backing up phone data ever.

Maybe, but it sure looks like a Windows only app (the desktop portion anyways).  I can't find any system requirements at the link provided to prove that though.  It does list mail clients that generally Windows only (with the exception of Thunderbird which works fine on Windows and Linux).

Thanks for the link though.....just shows us that there are others that don't want to get rained on by the cloud ;-)

Cheers

---

### Post by Jared Norris on 2010-12-14
This is a deal breaker for me as well. I cannot purchase an Android phone until the option exists NOT to sync it with the cloud and to sync it locally. I don't think it's fair for me to abuse all my contacts by putting their names, addresses, phone numbers, birthdays, and all my calendar events online for someone else to look after the privacy of. If it were just mine then it would be acceptable for me to take the decision but when it involves the people around me it's just not up to me to take that decision for them. I understand it's a great option to have there and for most people it might be wanted but I think it should at least be an option not a lock in.

I am in the market for a new phone right now and so far my hours of googling have turned up a whole lot of not much. 

The whole reason I switched to open source was to give me back control and give me decisions like these back for me to take.

---

### Post by ColdFusionEESG on 2010-12-14
> **head_victim said:**
> This is a deal breaker for me as well. I cannot purchase an Android phone until the option exists NOT to sync it with the cloud and to sync it locally. I don't think it's fair for me to abuse all my contacts by putting their names, addresses, phone numbers, birthdays, and all my calendar events online for someone else to look after the privacy of. If it were just mine then it would be acceptable for me to take the decision but when it involves the people around me it's just not up to me to take that decision for them. I understand it's a great option to have there and for most people it might be wanted but I think it should at least be an option not a lock in.

I am in the market for a new phone right now and so far my hours of googling have turned up a whole lot of not much. 

The whole reason I switched to open source was to give me back control and give me decisions like these back for me to take.

I couldn't agree more mate!

I think you hit the nail on the head.....it sure would be nice to have the OPTION to do what you want with your data instead of being forced to use the cloud.

What's driving me nuts is that there seem to be local syncing options for Windows, but not for Linux (which Android is....Linux)!! grrrrrr ;-)

Cheers

---

### Post by theDaveTheRave on 2011-03-03
Hi all,

I don't know how this project is panning out but...

I have 2 thoughts.

First, can you not export the contacts / calendar info in an XML format of some kind then simply link this into the linux desktop - maybe use a kind of CVS repo for the changes to sync together??

Secondly, I believe that a solution may already exist. It is called SyncML. I don't currently have an android phone, but once I get one if I have time (which means if I still don't have a job) I will work out how to get syncML onto my laptop, and then link this into the mobile via my wifi router.
[INDENT]
Quick bit of info on SyncML. From what I have read you need to have Tomcat, which means apache, Java, and Funambol (the syncML server) - which also needs a database (here is a [howto]("https://wiki.ubuntu.com/marckaplan/funambol") which hasn't been updated in a hile) which isn't exactly a 'quick job' or a small footprint for a simple synching mechanism.
Also I don't know what the footprint would be like. There may be other more lightweight syncML servers, I just mention funambol as it already has a [client]("https://www.forge.funambol.org/download/#phone") for android, and it seems to be able to sync most file / media types.

So from my side it would seem fairly 'easy' to implement in terms of all the required serviced being readily available, the issue will be to create a package of some form that will be small and lightweight, and easily installed by my wife ;)

I don't know what the footprint of all the above stuff would be on a system?[/INDENT]

The third option would be to use a method to control the Android phone directly from your pc, there seems to be [VNC server]("http://code.google.com/p/android-vnc/") for the platform, but I wouldn't know how that will work out.

David

---

### Post by Arathorn on 2011-03-03
The HTC Sync program for PC sucks, but for backups I just found this one: [https://market.android.com/details?id=com.BackupEverything](https://market.android.com/details?id=com.BackupEverything)
I haven't tried it yet, but it looks like it backups everything I want, and on the sd.

---

### Post by cataclysmic on 2011-04-09
Hey everyone

I was searching for the exact same thing.
I don't have that big of a problem especially as I have a google-account but Google doesn't have to know everything.

I found this project: [http://www.androidzoom.com/android_applications/tools/ical-importexport_ljev.html](http://www.androidzoom.com/android_applications/tools/ical-importexport_ljev.html)
It's an app that let's you import the ical format to your calendar.
I haven't tested it yet but it looks promising.
Thunderbird Lightning is able to export to the iCal format.
It is NOT direct syncing of the calendars but it might work as a bridging solution.

---

### Post by Johnsie on 2011-04-09
I'm an Android developer and might be able to offer a few tips for this. I have written apps that use an httpClient to check if various system at work are functioning correctly. It plays he star trek red alert sound if something is wrong lol. I've also written some things that record gps coordinates and pin that on a Google map (for a vehicle fleet tracking system).

Anyway, back to the topic... If this this going to be an offline thing then I'm not sure messing around with drivers etc would be the best option.

My solution is dirty, but it works as follows:

Android app reads the list of contacts/emails and saves them to a csv file or an sqlite db on the the phones internal memory.

Linux app finds the file when the phone is plugged in and imports it into Evolution.

No messing around with drivers would be required with this solution and it should work with all versions of Android.

---

### Post by natuk on 2011-06-14
This one is not offline sync but it goes around the google problem:

[http://www.androidzoom.com/android_applications/productivity/icssync_yegk.html](http://www.androidzoom.com/android_applications/productivity/icssync_yegk.html)

---

### Post by wi0 on 2011-07-11
I, too, am looking for a solution to sync Thunderbird calendar (lightning) with some calendar app on the android without the cloud. This [link]("http://paedi.biche.ch/setupOgi.html") contains an extremely convoluted solution, but maybe it can give some ideas to those who know more about how this whole thing works.

---

### Post by angus73 on 2012-02-27
Hello, are there any news about this project? Having my Android phone offline-synced with Evolution would be very useful for me too. I'm not a Linux programmer, but I would be glad to help the dev's with some testing and some ideas from a "user" point of view

Thank you
Angus73

---

### Post by ColdFusionEESG on 2012-02-27
> **angus73 said:**
> Hello, are there any news about this project? Having my Android phone offline-synced with Evolution would be very useful for me too. I'm not a Linux programmer, but I would be glad to help the dev's with some testing and some ideas from a "user" point of view

Thank you
Angus73

I'm pretty sure it's dead, but I did find a simple enough way to get Evolution contacts into Andriod using the app "ICS Importer".  So it's a one-way method (Evolution to phone).  I haven't had time to look for a tool that could perhaps merge the output from ICS Importer (i.e. export from Evolution and from phone....merge data...replace data on phone and in Evolution).  A bit clunky for sure, but good enough for my infrequent syncing needs

Cheers

---

### Post by angus73 on 2012-03-06
Thank you ColdFusionEESG, I will give a try and may post here if I find something useful.

Cheers,
Angus

---

### Post by grewolf on 2012-06-08
I too am intrested in an app that alows for offline syncing.  Didn't they have jpilot for palm.  I am not a developer but would looking at that ubuntu application provide cues on how to complete the same thing for android?

---

