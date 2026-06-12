---
title: "Dell optiplex gx240 running slow on Ubuntu Server 9.10"
date: 2012-06-15
forum: Server Platforms
---

### Post by narked165 on 2012-06-15
I am having issues with an old Optiplex I inherited.  It sat in my store room for a year before I opened it up.  First I had Kbuntu 10 running on it then I stripped it down and installed the most recent server with Unity.  It ran a little slow on 512 GiB of RAM then it crashed.  I was getting memory read/write errors so I upgraded to 1 GiB (512 X 2) pc133 SDRAM but now it runs so slow that it took 6 hours to install Ubuntu Server 9.10.  In command line it takes two to three minutes just to sudo apt-get a package.  I socket checked the processor and north bridge. I have air cleaned the entire case including the AGP slot for the video card and chips.  I have even cleaned and checked the PATA cables with a spare set.  I am pretty sure that the problem lies with the ATI -- AGP card; or rather the drivers.  It took all day just to get this far.  The first installation (on a scsi 0) is listed but if it takes half an hour to load to the server command line, I shutter to think how long it will take to load into Unity.  I am not as familiar with Ubuntu as I am with SUSE, I was hoping that someone might have a starting place.  I am going to fiddle with xorg and the ATI drivers tomorrow and perhaps try to reconfigure the xserver but that does not explain why I am having issues with slow response.  To get an idea, I did a ls -a for the heck of it and the response took 45 seconds.  There is no reason why I should be able to run Hardy Heron with KDE for six months on 512 then Unity for a day and not be able to get instant results from bash on a gig of RAM.  I am totally stumped. Please help.[/FONT]

---

### Post by spynappels on 2012-06-15
Ok, there are a few clarifications we need first:

Are you running Server Edition? This does not come with any Desktop Environment, so no Unity, no KDE, LXDE etc.

Which release are you actually running? 9.10 went End of Life over a year ago and never had Unity as an option.


If you are trying to run a server, which would normally run headless (no GUI), graphics card driver should not be an issue as you can use the on-board video, as there is only a text console anyway. Perhaps if this is the case, removing the graphics card might be the simplest solution.

If you are looking for a Desktop Environment and are having problems with the graphics card, perhaps the Hardware & Laptops subforum ([http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)) or the Desktop Environment subforum ([http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)) might be a place to get help more quickly.

---

### Post by narked165 on 2012-06-15
Thanks for the quick reply.  I was first running Ubuntu Server 12 and I installed the Ubuntu (Unity) desktop.  I had not used Ubuntu in a while and I used the gui to make things easier.  It worked fine then my system went down.

The system came back up and I did some trouble shooting.  I narrowed the problems down to a faulty 256 RAM chip.  I ordered two new 512's and tried to reboot into the (first) Server install. I let that go for two hours. It either hung or was going to require more than two hours to boot.  Next I tried SUSE Server then SUSE 12.1 desktop.  The install scroll speed was one line every five seconds.  I did better with MS XP and got all the way to the partitioner before manually aborting.  I decided to backtrack to Ubuntu server 9.10 (Whichever the last update version was) It took almost six hours to complete the install.  It boots into bash but the lag is terrible.  Like I said, simple commands like lspci or cd take 30 to 45 seconds to return.  Whatever the problem is, it is system wide.  I thought that there might be an issue with the ATI open source driver.  There is no reason for bash to lag that bad.  AS far as I know, the ATI-AGP card came preinstalled by Dell.  The mobo has no embedded video card.  The rest of the hardware seems to work fine.

---

### Post by mbeach on 2012-06-15
just a shot in the dark and may not be your issue at all, but take a look at the capacitors on the board. I've had some odd behaviour from some older 240's, ranging from slowness, to complete failure, remedied by replacing some bad caps. You'd be able to see them bulging on the top likely.

---

