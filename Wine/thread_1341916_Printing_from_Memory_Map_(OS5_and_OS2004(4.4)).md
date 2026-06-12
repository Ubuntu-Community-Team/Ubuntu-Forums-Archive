---
title: "Printing from Memory Map (OS5 and OS2004(4.4))"
date: 2009-11-30
forum: Wine
---

### Post by TimGS on 2009-11-30
Has anyone here successfully printed from Memory Map on Wine?

I am running Ubuntu 9.10. WineHQ reports problems with printing from ver 4.4 but there is no mention of such issues with 5.0.

(Memory Map is mapping software available in the UK)

-- Tim.

---

### Post by mark_uk on 2009-12-06
Hello, Sorry I dont know how to answer your question regarding printing, however how did you get Memory Map working in the first place using Wine? I have tried and failed on this quite a few times.

---

### Post by PeggySue on 2009-12-07
Hi,

I also have a printing problem.

Memory Map didn't work successfully under wine until now!
I am running Ubuntu 9.10 (Karmic) on a Dell, x86 processor.  I installed wine 1.2 using the synaptic package manager.
I installed Memory Map by inserting the CD, navigating to the setup.exe in the Set Up folder and double clicked it; following the instructions for a windows like install.
Clicking the icon on the desktop launches a stable Memory Map.  No flickering as you move the cursor!  (Much improved from previous versions of Wine.)  So I loaded the maps and tried to load my .mmo file with my stored data.  I didn't try printing at this stage.  (Pity)
Here I was told the version of the stored data was newer than the version of the Memory Map software.  I followed the links to get the latest version "EU" version and installed that.  It's looks very fancy but has the same features as the old version.

When I selected Map | Print I was told that on line licence verification was required.  I clicked OK and Memory Map just hung.  I had to force quit after 10 mins.  On a restart I go to Map | Print and nothing happens.  Everything else seems to work fine though.

I will raise a support request with Memory Map but don't expect any help from them.  Their supprt in the past has been as good/bad as their software writting skills!

---

### Post by PeggySue on 2009-12-07
An update:

My installation from the CD was still on my computer so I tested that out.
CD Installation:  Version 5.0.2 Build 627  Licence Valid

Prints OK.  Prints to scale with map co-ordinates.

GPS Garmin III only works on the RS232 serial port; not on the USB to serial adapter.  Routes uploaded successfully.  Tracks downloaded successfully.

The 3D World manipulation and 3D flythrough are extremely slow, probably unusable.

Data saved as Memory Map format (.mmo) from a more recent version can't be imported.  However, tracks and routes saved as .csv can be imported.  Flags etc. are not in the .csv file.

The Memory Map latest version 5.4.2 Build 1089 requires online re-verification of the licence before it will let you print or talk to the GPS.  This verifiaction process hangs Memory Map.

Tim:
Does your version print a black page or nothing at all?

---

### Post by TimGS on 2009-12-07
Hi,

When I print I get a dark grey page with some diagonal thin coloured lines (I forget the colours!).

The same happens if I output the 'print' as a postscript file.

-- Tim.

---

### Post by PeggySue on 2009-12-07
Yes I had a dark page when using Ubuntu 8.04 and the version of wine that went with it.

I would think it is the changes in Wine to 1.2 that make the difference.  If you have a way of trying Wine 1.2 without messing up your current installations, it would be worth a go.

I have had no response from Memory Map.  I will post any usefull information I get from them.

Lets hope for some weather to get on the moors this weekend!

---

### Post by TimGS on 2009-12-15
Fantastic!

Downloading the latest wine from [http://packages.ubuntu.com/karmic/amd64/wine1.2/download](http://packages.ubuntu.com/karmic/amd64/wine1.2/download) does indeed solve the printing problem.

Thanks,
Tim.

---

### Post by PeggySue on 2009-12-16
Glad the printing works.

Further to post #3: The only help I got from Memory Map was to check that the firewall wasn't blocking internet access and a link to download version 5.1.3

[http://www.memory-map.co.uk/downloads/mmv5/mmv5_os_513.exe]("http://www.memory-map.co.uk/downloads/mmv5/mmv5_os_513.exe") 

I did download v 5.1.3 and was able to import my .mmo file and didn't need to connect to the internet to activate printing or GPS.  (My .mmo file didn't contain the marks; just routes, traks and way points.  This might have been my fault but I did do an export all.)

Do you have a graphics cxard with the restricted driver enabled?  If so does your 3D flythrough work?

---

### Post by TimGS on 2009-12-17
> Do you have a graphics cxard with the restricted driver enabled? If so does your 3D flythrough work?

I think yes to the first (nvidia)- don't know about the second. Will check after Christmas - away from home at the moment.

-- Tim.

---

### Post by AlenShaw on 2009-12-18
Have you tried Quo GB Digital Mapping Software, it's a free download?
Available at [www.mapyx.com](www.mapyx.com) :)

---

### Post by mark_uk on 2009-12-26
Just to confirm I upgraded Wine to wine1.2_1.1.31 and Memory Map now installs and prints with no issues. 

I am having issues with the 3D fly through but I'm guessing thats more todo with my low spec laptop, not sure.

---

### Post by TimGS on 2010-01-01
> **TimGS said:**
> I think yes to the first (nvidia)- don't know about the second. Will check after Christmas - away from home at the moment.

-- Tim.

After checking, I do have the nvidia restricted drivers. 3D fly through is temperamental. Reasonably smooth (but not perfect) but does occasionally freeze en-route with no further response.

The best '3D fly through' is to go there yourself!

-- Tim.

---

