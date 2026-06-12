---
title: "Windows 7's &quot;device stage&quot;"
date: 2009-05-31
forum: The Cafe
---

### Post by Polygon on 2009-05-31
[http://www.betanews.com/article/Top-10-Windows-7-Features-2-Device-Stage/1243631168](http://www.betanews.com/article/Top-10-Windows-7-Features-2-Device-Stage/1243631168)

I just thought that concept behind this is really neat. You plug in the device, it actually shows you a picture OF the device, installs the correct drivers, and gives you a customized list of what the device can do, and any other pertinent information, such as battery level, % free space, etc.

and since the article says that most of that information is just stored in a XML file somewhere in the device, with documentation on it here: [http://msdn.microsoft.com/en-us/library/dd445716.aspx](http://msdn.microsoft.com/en-us/library/dd445716.aspx) , it is possible that gnome/kde could parse that and tailor some of it to respective linux programs. Schweet.

---

### Post by Xbehave on 2009-05-31
seams like the "recently added hardware" button in kde4 (or storage media applet in kde3)
If they parse the XML file and add shortcuts to the relevant programs this will be great for peripherals :D

---

### Post by fatality_uk on 2009-05-31
"Lets connect a portable media player that **supports** device stage"
So you device has to be compatible I am guessing. Anyone for a ZUNE?

---

### Post by Polygon on 2009-05-31
No, it can be any device. Even an ipod. All you have to do is create an XML document and some images and store it somehow in the device  that let windows 7 know how to handle your device. You don't have to have it 'approved' by microsoft.

---

### Post by t0p on 2009-05-31
> **Polygon said:**
> No, it can be any device. Even an ipod. All you have to do is create an XML document and some images and store it somehow in the device  that let windows 7 know how to handle your device. You don't have to have it 'approved' by microsoft.

So you want to put some pics of your ipod onto your Windows 7 so when you connect your ipod to your computer Windows 7 can show you what your ipod looks like?  Even though you damn well *know* what your ipod looks like as it's there in front of you, on the table next to the computer?  Sounds great, I want one.  How long do I have to wait for this brilliant innovation?

---

### Post by steeleyuk on 2009-05-31
Its not how long, its how much. ;)

---

### Post by Delever on 2009-05-31
Worked with my HP printer just fine. They are probably working with companies to provide as many drivers as possible, because I had to request to download driver list to find my printer in it. 

Drivers are basically for vista, just small fixes or none at all required to work.

People ARE going to love windows 7, you can scream, frown or pull your hair out... Real tragedy :P

---

### Post by HappyFeet on 2009-05-31
> **t0p said:**
> So you want to put some pics of your ipod onto your Windows 7 so when you connect your ipod to your computer Windows 7 can show you what your ipod looks like?  Even though you damn well *know* what your ipod looks like as it's there in front of you, on the table next to the computer?  Sounds great, I want one.  How long do I have to wait for this brilliant innovation?

Good one. I think I'll install win7 right now because of this life changing innovation. I guess some people need a pic of the device they are plugging in. :rolleyes:

---

### Post by Delever on 2009-05-31
> **HappyFeet said:**
> Good one. I think I'll install win7 right now because of this life changing innovation. I guess some people need a pic of the device they are plugging in. :rolleyes:

Let's see. Imagine typical office, with 20-50 employees and several printers in another room. Consider how well they remember printer model names vs how well they remember how they look.

---

### Post by Polygon on 2009-05-31
This is a good step of making computers easier to use, even without the pictures you guys like to complain about, having a window open with all the possible actions for X device is really useful.

Example, instead of having to open itunes for your ipod, you plug it in, and it opens a window with sync, repair, randomize (for small players where the library is too big for the storage space).

Other devices can have options for syncing, scanning, searching for updates for drivers, adding media to a phone or a mp3 player.

Question is, would you guys be bashing this if this was a gnome/kde innovation instead of a windows one?

---

### Post by HappyFeet on 2009-05-31
> **Delever said:**
> Let's see. Imagine typical office, with 20-50 employees and several printers in another room. Consider how well they remember printer model names vs how well they remember how they look.

Yeah whatever. It's amazing how people got by all these years with not being able to see the printer they need, but all of a sudden it's important? Give me a break.

---

### Post by Polygon on 2009-05-31
one application for it, can you tell which one of the drives is the SD slot?

[[IMG]http://img268.imageshack.us/img268/6492/examplej.th.png[/IMG]](http://img268.imageshack.us/my.php?image=examplej.png)

If it had a picture of....an SD card there, i could tell very easily which drive i have to click to get to my sd card on my multimedia card reader. Instead of having to click 4 different drives and get 'there is no media in this drive!' to figure it out =P

ubuntu is a bit better at this, as it will automatically mount it, but it still has a very generic 'memory card' picture, with the name "disk' or "2 GB Disk" or something. having an xml file on a disk telling the OS what it is would be very useful, even for linux.

and for people who are NOT geeks, you know, those pesky people that make up like 90% of the market, it would help them to see a picture of...whatever device they plugged in rather then just seeing a generic icon which they might not associate with the device they just plugged in. Sure, you and I might see that the 250 gb drive on our desktop  is actually an ipod, but other people might not.

---

### Post by Screwdriver0815 on 2009-05-31
isnt it basically the same as all the OS have since 8 years or so?

when I plug in a USB stick for example (because I don't have a mp3 player) then a small window pops up and I can choose what I want to do:

- download photos
- open the stick with the filebrowser
- ??

the same with a digital camera:

- download photos with Digikam
- browse files with Dolphin

this is possible in Windows Xp, in Linux and I think in Mac too. 

And in the filebrowser and on the desktop there always appears a photo or at least an icon of the device. At least in Linux... ;)

So whats new about all this? The photos of the device? Honestly and this is no "windows is stupid" I don't ge the point of this. When this was installed as default in Linux I would uninstall it I think.

---

### Post by MaxIBoy on 2009-05-31
> What Microsoft is hoping manufacturers will embrace is a concept called  the [Device Stage *metadata package*]("http://msdn.microsoft.com/en-us/library/dd445716.aspx"). It's an  XML-based file that represents all the visual elements that the user  sees when he plugs in a device (or when Bluetooth captures it), and all  the software components related to the functions that device performs,  in an explicit database. Conceivably, that software can be installed  automatically through the Internet as the device is plugged in (or comes  in range), since the metadata package will contain instructions for how  Win7 retrieves it, and how it should be registered locally.Sounds like a great idea! The drivers for my Bluetooth device are at [www.antivirus2009.com](www.antivirus2009.com), now let me casually stroll past your computer and let's do this!

---

### Post by Namtabmai on 2009-05-31
> **Delever said:**
> Let's see. Imagine typical office, with 20-50 employees and several printers in another room. Consider how well they remember printer model names vs how well they remember how they look.

What sort of people work in your office? In mine it would have to say "The printer over by Steve" and should a picture of Steve for this to be any use to them. One beige box is just like any other beige box to them.

---

### Post by Giant Speck on 2009-05-31
> **Namtabmai said:**
> What sort of people work in your office? In mine it would have to say "The printer over by Steve" and should a picture of Steve for this to be any use to them. 
 
That would actually be funny to see.

---

### Post by Namtabmai on 2009-05-31
> **Giant Speck said:**
> That would actually be funny to see.

Thinking about it, it would be kind of cool in a creepy way. Just need to hook a web cam next to every printer and hook a frame grabber into this Windows 7 XML driver thing.

---

### Post by monsterstack on 2009-05-31
In an office where people do things right, they will avoid identifying printers by fancy device numbers anyway. The last place I worked at identified the printers by where they were, with the device numbers themselves in brackets. Much better than the "print and pray" other places seem to operate.

---

### Post by Skripka on 2009-05-31
> **Polygon said:**
> one application for it, can you tell which one of the drives is the SD slot?

[[IMG]http://img268.imageshack.us/img268/6492/examplej.th.png[/IMG]](http://img268.imageshack.us/my.php?image=examplej.png)

If it had a picture of....an SD card there, i could tell very easily which drive i have to click to get to my sd card on my multimedia card reader. Instead of having to click 4 different drives and get 'there is no media in this drive!' to figure it out =P

ubuntu is a bit better at this, as it will automatically mount it, but it still has a very generic 'memory card' picture, with the name "disk' or "2 GB Disk" or something. having an xml file on a disk telling the OS what it is would be very useful, even for linux.

and for people who are NOT geeks, you know, those pesky people that make up like 90% of the market, it would help them to see a picture of...whatever device they plugged in rather then just seeing a generic icon which they might not associate with the device they just plugged in. Sure, you and I might see that the 250 gb drive on our desktop  is actually an ipod, but other people might not.


Your argument here proves why the Windows convention for identifying drives is idiotic.  Your argument however does NOT prove why another "feature" is an improvement on the matter.

I do think this "feature" is pure marketing, and really provides no real improvement on what already is.

---

### Post by Giant Speck on 2009-05-31
Device Stage just seems to me like a more user-friendly version of Device Manager with a few added capabilities.

---

### Post by geoken on 2009-05-31
> **Namtabmai said:**
> What sort of people work in your office? In mine it would have to say "The printer over by Steve" and should a picture of Steve for this to be any use to them. One beige box is just like any other beige box to them.

Where I work there is no such thing as 'printer by steve'. The printers are in common areas (about 5 or 6 in an area). Employees commonly refer to them by the way they look (ie. the smaller laser or the black impact)

---

### Post by geoken on 2009-05-31
> **HappyFeet said:**
> Yeah whatever. It's amazing how people got by all these years with not being able to see the printer they need, but all of a sudden it's important? Give me a break.

By your logic, computers themselves are un-important since people have gotten by for years without needing them.

---

### Post by Jimleko211 on 2009-05-31
I think this is a good improvement, but the only people who would need it are the non-geeks.  You know, the people who can't go in and edit a .xml file if their hardware isn't supported by device stage.  And it's not like every single device is going to be supported by it, especially hardware made a few years ago.

---

### Post by burvowski on 2009-05-31
> **Polygon said:**
> one application for it, can you tell which one of the drives is the SD slot?

[[IMG]http://img268.imageshack.us/img268/6492/examplej.th.png[/IMG]]("http://img268.imageshack.us/my.php?image=examplej.png")

If it had a picture of....an SD card there, i could tell very easily which drive i have to click to get to my sd card on my multimedia card reader. Instead of having to click 4 different drives and get 'there is no media in this drive!' to figure it out =P

Can't you just set a custom icon for that SD card that Windows would remember everytime you plugged it in? That's how it worked on my mac. Haven't tried it with Ubuntu yet as I just started using it. Hmm, now that I think about it, hasn't OS X been able to do something similar to this for years with the ds_store hidden metadata file?

---

### Post by gashcr on 2009-05-31
> **burvowski said:**
> Can't you just set a custom icon for that SD card that Windows would remember everytime you plugged it in? That's how it worked on my mac. Haven't tried it with Ubuntu yet as I just started using it. Hmm, now that I think about it, hasn't OS X been able to do something similar to this for years with the ds_store hidden metadata file?

yup.

I think you can do the icon think in gnome (can't speak for KDE, never tried that there), it even "remembers" where to put the icon in the desktop and the size :P

---

### Post by t0p on 2009-05-31
> **Polygon said:**
> This is a good step of making computers easier to use, even without the pictures you guys like to complain about, having a window open with all the possible actions for X device is really useful.

Example, instead of having to open itunes for your ipod, you plug it in, and it opens a window with sync, repair, randomize (for small players where the library is too big for the storage space).

Other devices can have options for syncing, scanning, searching for updates for drivers, adding media to a phone or a mp3 player.

Question is, would you guys be bashing this if this was a gnome/kde innovation instead of a windows one?

But this *is* a gnome innovation.  I plug in my phone, ubuntu asks if I want to mess with the pics or tunes.  I plug in my camera, up pops f-spot.

Only thing it doesn't do is show me a pic of my device.  I'm gutted about that.  How am I meant to go on living now?  :(

---

### Post by Polygon on 2009-06-01
I jsut see this as an improvement over the 'what do you want to do?" screen with windows that just gives you an autogenerated list on whats actually on the device (as in if it has mp3's, it will put windows media player on the list).

this way, the listed actions are much more relevant rather then having the OS guess what the device can do, the OS can just fetch a file that is on the device that tells it EXACTLY what it can do. I dunno, i thought it was pretty neat.

---

### Post by tbroderick on 2009-06-01
> **t0p said:**
> But this *is* a gnome innovation.  I plug in my phone, ubuntu asks if I want to mess with the pics or tunes.  I plug in my camera, up pops f-spot.

Only thing it doesn't do is show me a pic of my device.  I'm gutted about that.  How am I meant to go on living now?  :(

To be fair to Windows, it's a little more then the usual auto run type feature. Using the Sansa Clip as an example, it has the typical browse, sync, and manage functions. But it also includes a display of free space and battery charge, shortcut for the device's user manual, shortcut to online accessories shop, and shortcut to download latest firmware. A few little things that may be useful to some.

---

### Post by zekopeko on 2009-06-01
i'm just amazed how people like to bash MS with no valid argument.

what MS just gave the FOSS community is an easy way for managing devices.

to all the "M$ sux" kids in this thread: Get of your high horse.

to the OP: nice find with the XML part. didn't know it was an open specification.

---

### Post by Giant Speck on 2009-06-01
> **zekopeko said:**
> what MS just gave the FOSS community is an easy way for managing devices.

Um, what?  Microsoft didn't give the FOSS community anything other than an idea.  The Device Stage itself is still proprietary.

---

### Post by Swarms on 2009-06-01
Yeah Ubuntu should definitely support it, if it improves the user experience, why not?

---

### Post by Sublime Porte on 2009-06-01
Doesn't udev already do this? Aside from the nice little images? Which wouldn't be too hard to do anyway. I'm sure it wouldn't be that hard to start an online database which matches hardware ID strings with pictures/feature lists of the product. Certainly more reliable than expecting vendors (or even users??) to create xml files and store them on the device somewhere.

---

### Post by geoken on 2009-06-01
> **Sublime Porte said:**
> Doesn't udev already do this? Aside from the nice little images? Which wouldn't be too hard to do anyway. I'm sure it wouldn't be that hard to start an online database which matches hardware ID strings with pictures/feature lists of the product. Certainly more reliable than expecting vendors (or even users??) to create xml files and store them on the device somewhere.

I think it's a lot more reliable to have manufacturers maintain an XML file like this than it would be to have some online, user maintained database.

---

### Post by michaeldt on 2009-06-01
First question we need to ask is, did MS apply for a patent for this sort of thing, if not then it's a great idea.

Effectively what MS is doing is asking hardware manufacturers to do all the leg work. They add the XML file to the device, point the OS to the drivers (windows only ofc), tell it how to interface with the device etc. 

It's MS's way of no longer having to write code to probe a device to see what it is and how it functions, which is pretty much what plug-and-play is in a way. 

Is it an innovation, not really. Will it make it look as if Windows is really clever, yes. Does it mean windows is, no. It's a good idea, if only because it's making hardware vendors provide the information in a way which can "hopefully" be easily detected by any OS.

What this comes down to is whether MS have a patent on this and whether the information in the XML file will be at all useful to another OS. But knowing the FOSS community, it won't take long to get this integrated into Linux desktops.

---

### Post by Polygon on 2009-06-01
> **Giant Speck said:**
> Um, what?  Microsoft didn't give the FOSS community anything other than an idea.  The Device Stage itself is still proprietary.

well by them asking manufactuers to 'comply' with device stage, that means that lots of devices will start having xml files embedded in them somewhere, which gnome/kde/xfce can  retrieve somehow, and there is a spec page here: [http://msdn.microsoft.com/en-us/library/dd445716.aspx](http://msdn.microsoft.com/en-us/library/dd445716.aspx) that they can use to use the information in the file in their own way.

and yeah, udev does have those weird hardware strings like 052f:2310 or something, and those do identify the device, but not much else i don't think.

---

### Post by Wiebelhaus on 2009-06-01
> **t0p said:**
> so you want to put some pics of your ipod onto your windows 7 so when you connect your ipod to your computer windows 7 can show you what your ipod looks like?  Even though you damn well *know* what your ipod looks like as it's there in front of you, on the table next to the computer?  Sounds great, i want one.  How long do i have to wait for this brilliant innovation?

+1

---

### Post by Giant Speck on 2009-06-01
> **Polygon said:**
> well by them asking manufactuers to 'comply' with device stage, that means that lots of devices will start having xml files embedded in them somewhere, which gnome/kde/xfce can  retrieve somehow, and there is a spec page here: [http://msdn.microsoft.com/en-us/library/dd445716.aspx](http://msdn.microsoft.com/en-us/library/dd445716.aspx) that they can use to use the information in the file in their own way.

I guess that makes sense, but the benefit to FOSS is indirect and certainly not deliberate.  That doesn't mean we can't enjoy the benefit, though.  :)

---

### Post by Sublime Porte on 2009-06-01
> I think it's a lot more reliable to have manufacturers maintain an XML file like this than it would be to have some online, user maintained database

Encyclopaedia producers used to think like that too...

---

### Post by geoken on 2009-06-01
> **Wiebelhaus said:**
> +1

Did you even read the thread or do you simply support his comment because it contained the requisite amount of anti-Microsoft jargon?

---

### Post by geoken on 2009-06-01
> **Sublime Porte said:**
> Encyclopaedia producers used to think like that too...

Your analogy doesn't relate.

I'm comparing manufacturer maintains data vs. community maintains data. Your comparing third party maintains data vs community maintains data.

---

