---
title: "How to get the Lexmark X1270 fully working under linux"
date: 2008-09-29
forum: Tutorials
---

### Post by s0l1dsnak3123 on 2008-09-29
Hey there :)

Here is how I got my Lexmark X1270 working fully under linux  (printer **AND** scanner).

_Prerequisites:_
[list=1]
[*] Download and install libstdc++5 from here: [http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb]("http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb")
[/list]

_Printer:_
[LIST=1]
[*]Unplug your Lexmark X1270 If it has been plugged in before, and make sure there is no record of it in System > Administration > Printing.

[*]Download and install these two files:
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb")
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb")
[*]Plug the printer back in, hardy should detect it has been inserted and give some info about using a "plaintext driver" or something. Click on the button in that notification balloon, it should search for drivers. Choose Lexmark in the list, then z600. Once you have completed the wizard, select the printer as the default, and print a test page, it should work!
[/LIST]
_Scanner_

[COLOR="Red"]If you are running Lucid, the scanner should work out of the box. Otherwise, follow the steps below:[/COLOR]

[LIST=1]
[*]Download this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/dll.conf](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/dll.conf), and this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/lexmark.conf](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/lexmark.conf), and copy (as root) to "/etc/sane.d/"
[*]Download this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/home-User-.sane-Xsane/Lexmark:X1200_USB1.1.drc](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/home-User-.sane-Xsane/Lexmark:X1200_USB1.1.drc), and copy to "/home/$USER/.sane/Xsane/". If "/home/$USER/.sane/Xsane/" doesn't exist, try opening xsane. It might actually scan at this point, but finish the tutorial anyway, because it improves picture quality.
[*]Download these:
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.la](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.la)
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1(%20link%20to-%3e%20libsane-lexmark.so.1.0.19%20)](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1(%20link%20to-%3e%20libsane-lexmark.so.1.0.19%20))
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1.0.19](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1.0.19)
and copy (as root) to "/usr/lib/sane/"
[*]Open up xsane and click scan! xsane does crash sometimes, but if this happens, simply reconnect the printer, and restart xsane.
[/LIST]

(Taken from [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/), but adapted to be more user friendly.)

---

### Post by hawkhock on 2008-12-01
[COLOR="Red"]Scanner
  [COLOR="Red"] 1. Download this: [http://www.indexdata.com.br/Linux/Dr...ane.d/dll.conf](http://www.indexdata.com.br/Linux/Dr...ane.d/dll.conf), and this: [http://www.indexdata.com.br/Linux/Dr...d/lexmark.conf](http://www.indexdata.com.br/Linux/Dr...d/lexmark.conf), and copy (as root) to "/etc/sane.d/"[/COLOR]
   2. Download this: [http://www.indexdata.com.br/Linux/Dr...200_USB1.1.drc](http://www.indexdata.com.br/Linux/Dr...200_USB1.1.drc), and copy to "/home/$USER/.sane/Xsane/". If "/home/$USER/.sane/Xsane/" doesn't exist, try opening xsane. It might actually scan at this point, but finish the tutorial anyway, because it improves picture quality.
   3. Download these:
      [http://www.indexdata.com.br/Linux/Dr...ane-lexmark.la](http://www.indexdata.com.br/Linux/Dr...ane-lexmark.la)
      [http://www.indexdata.com.br/Linux/Dr....so.1.0.19%20](http://www.indexdata.com.br/Linux/Dr....so.1.0.19%20))
      [http://www.indexdata.com.br/Linux/Dr...mark.so.1.0.19](http://www.indexdata.com.br/Linux/Dr...mark.so.1.0.19)
      and copy (as root) to "/usr/lib/sane/"[/COLOR]
   
Am newbie running Wubi Ubuntu 8.10
Can you give me specific directions how to [COLOR="Red"]"copy (as root) to "/etc/sane.d/"[/COLOR]?

Would same directions apply to [COLOR="Red"]"copy (as root) to "user/lib/sane/"[/COLOR]

Thanks in advance
Georgi in UT

---

### Post by s0l1dsnak3123 on 2008-12-02
Hi there. To copy something as root go to Applications -> Accessories -> Terminal, then type 
```
sudo cp <file you want to copy> <destination>
```

Obviously, <file you want to copy> and <destination> would be changed to the respective file name and path.

I hope I've made it clear for you :)

John.

---

### Post by hawkhock on 2008-12-02
Thanks John - I learned computers with wysiwyg so command line is a foreign language which I'll have to learn.  Thanks for your prompt response.
G in UT

---

### Post by s0l1dsnak3123 on 2008-12-03
Not a problem ):P

---

### Post by hawkhock on 2008-12-15
[QUOTE=s0l1dsnak3123;5877836]Hey there :)

Here is how I got my Lexmark X1270 working fully under linux  (printer **AND** scanner).

_Printer:_
[LIST=1]
[*]Unplug your Lexmark X1270 If it has been plugged in before, and make sure there is no record of it in System > Administration > Printing.

[*]Download and install these two files:
[http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb]("http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb")
[http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb]("http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb")
[*]Plug the printer back in, hardy should detect it has been inserted and give some info about using a "plaintext driver" or something. Click on the button in that notification balloon, it should search for drivers. Choose Lexmark in the list, then z600. Once you have completed the wizard, select the printer as the default, and print a test page, it should work!

[LIST=1]
[*]I disconnected my printer, made sure it was not listed.
[*]Your link to leighm.dgtimoon.com yields a 404 message but I did find the files at indexdata.com, downloaded and installed them.
[*]Reconnected my printer.
[*]I did not get any wizard to select the Z600 driver.  Checked printer properties and only item to change was a URI - not sure what this is.
[*]I also can't find where the drivers are installed in the file system.
[/LIST]

If you can help, it would be much appreciated.

---

### Post by s0l1dsnak3123 on 2008-12-15
Hi there, I wrote this tutorial when I was using Hardy at the time - it is quite possible that this tutorial no longer works/applies to intrepid. The computer I wrote this tutorial for is still running Hardy also, so I cannot tell you if this tutorial even works at all.

However, you may be able to setup the printer manually:
[LIST=1]
[*]Go to System > Administration > Printing
[*]Click on Server > Printer > New
[*]At this point I am unsure what will happen in Intrepid's case - it may detect the driver and auto install, it may require you to take extra steps.
[/LIST]

If you cannot fix this in intrepid, I will try and install the driver under my main computer, which is running intrepid.

Thanks :popcorn:

p.s I updated the links to (what I think) is the correct version you mentioned at indexdata.

---

### Post by hawkhock on 2008-12-15
Golly - you're quick -- mea culpa, mea cupla for I have erred.  
1) I thought my printer was disconnected - it wasn't.  
2  I finally found the setting to change from generic printer, installed the correct driver and voila - the printer works!!!

Now to work on the scanner -- sorry for bothering you but thanks again for the prompt reply!

---

### Post by s0l1dsnak3123 on 2008-12-15
Not a problem - we all make mistakes like those :lolflag:

I have a email widget on my desktop that tells me when I get an email ;)

You weren't bothering me - I am happy to help ):P

---

### Post by hawkhock on 2008-12-15
> **s0l1dsnak3123 said:**
> Not a problem - we all make mistakes like those :lolflag:

I have a email widget on my desktop that tells me when I get an email ;)

You weren't bothering me - I am happy to help ):P

I'll have to get that email widget.  Next problem.  For some reason, I am unable to use terminal but I'll learn how to do that separately. 

On a whim, I decided to try scanning using XSane, without installing the second half of your tutorial.  IT WORKS! - document scanned beautifully BUT -- how to I print what is scanned?  Could not find any print buttons or instructions in XSane.  Do I have to save it as a document and then print it? I'm aware that the Lexmark device buttons don't work in Ubuntu.
Hope this is the last one!

---

### Post by s0l1dsnak3123 on 2008-12-15
Hi there - that's an easy question :D

[LIST=1]
[*]click on the save icon at the top-left (a floppy disk if I remember it correctly) and choose a destination.
[*]Open the file up in The Gimp.
[*]File > Print :D
[/LIST]

That should do it from memory ;)

---

### Post by hawkhock on 2008-12-15
Much thanks -- am good to go -- God bless!
Georgi

---

### Post by ColeenM on 2009-03-01
Thanks, after a lot of other suggestions didn't work, I found your info and in 5 minutes had my Lexmark x1270 printing!
> **s0l1dsnak3123 said:**
> Hey there :)

Here is how I got my Lexmark X1270 working fully under linux  (printer **AND** scanner).

_Printer:_
[LIST=1]
[*]Unplug your Lexmark X1270 If it has been plugged in before, and make sure there is no record of it in System > Administration > Printing.

[*]Download and install these two files:
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb")
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb")
[*]Plug the printer back in, hardy should detect it has been inserted and give some info about using a "plaintext driver" or something. Click on the button in that notification balloon, it should search for drivers. Choose Lexmark in the list, then z600. Once you have completed the wizard, select the printer as the default, and print a test page, it should work!
[/LIST]
_Scanner_
[LIST=1]
[*]Download this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/dll.conf](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/dll.conf), and this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/lexmark.conf](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/lexmark.conf), and copy (as root) to "/etc/sane.d/"
[*]Download this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/home-User-.sane-Xsane/Lexmark:X1200_USB1.1.drc](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/home-User-.sane-Xsane/Lexmark:X1200_USB1.1.drc), and copy to "/home/$USER/.sane/Xsane/". If "/home/$USER/.sane/Xsane/" doesn't exist, try opening xsane. It might actually scan at this point, but finish the tutorial anyway, because it improves picture quality.
[*]Download these:
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.la](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.la)
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1(%20link%20to-%3e%20libsane-lexmark.so.1.0.19%20)](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1(%20link%20to-%3e%20libsane-lexmark.so.1.0.19%20))
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1.0.19](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1.0.19)
and copy (as root) to "/usr/lib/sane/"
[*]Open up xsane and click scan! xsane does crash sometimes, but if this happens, simply reconnect the printer, and restart xsane.
[/LIST]

(Taken from [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/), but adapted to be more user friendly.)

---

### Post by s0l1dsnak3123 on 2009-03-01
You are very welcome :)

---

### Post by hawkhock on 2009-03-06
> **s0l1dsnak3123 said:**
> Hey there :)

Here is how I got my Lexmark X1270 working fully under linux  (printer **AND** scanner).

_Printer:_
[LIST=1]
[*]Unplug your Lexmark X1270 If it has been plugged in before, and make sure there is no record of it in System > Administration > Printing.

[*]Download and install these two files:
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb")
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb")
[*]Plug the printer back in, hardy should detect it has been inserted and give some info about using a "plaintext driver" or something. Click on the button in that notification balloon, it should search for drivers. Choose Lexmark in the list, then z600. Once you have completed the wizard, select the printer as the default, and print a test page, it should work!
[/LIST]
_Scanner_
[LIST=1]
[*]Download this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/dll.conf](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/dll.conf), and this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/lexmark.conf](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/etc-sane.d/lexmark.conf), and copy (as root) to "/etc/sane.d/"
[*]Download this: [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/home-User-.sane-Xsane/Lexmark:X1200_USB1.1.drc](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/home-User-.sane-Xsane/Lexmark:X1200_USB1.1.drc), and copy to "/home/$USER/.sane/Xsane/". If "/home/$USER/.sane/Xsane/" doesn't exist, try opening xsane. It might actually scan at this point, but finish the tutorial anyway, because it improves picture quality.
[*]Download these:
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.la](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.la)
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1(%20link%20to-%3e%20libsane-lexmark.so.1.0.19%20)](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1(%20link%20to-%3e%20libsane-lexmark.so.1.0.19%20))
[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1.0.19](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/usr-lib-sane/libsane-lexmark.so.1.0.19)
and copy (as root) to "/usr/lib/sane/"
[*]Open up xsane and click scan! xsane does crash sometimes, but if this happens, simply reconnect the printer, and restart xsane.
[/LIST]

(Taken from [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/), but adapted to be more user friendly.)

After installing my printer when I first started with Ubuntu, I never got around to the scanner instructions and would like to try them now.  Since then I've downgraded from Intrepid to Hardy. I downloaded the scanner files noted above and they open in gedit.  

Do I copy and paste the entire dll.conf gedit file to /etc/sane.d/? 
Same for other files that open in gedit but to proper locations?
Should printer be unplugged while working on the scanner files?

Thanks in advance for your help.

---

### Post by s0l1dsnak3123 on 2009-03-06
> **hawkhock said:**
> After installing my printer when I first started with Ubuntu, I never got around to the scanner instructions and would like to try them now.  Since then I've downgraded from Intrepid to Hardy. I downloaded the scanner files noted above and they open in gedit.  

Do I copy and paste the entire dll.conf gedit file to /etc/sane.d/? 
Same for other files that open in gedit but to proper locations?
Should printer be unplugged while working on the scanner files?

Thanks in advance for your help.

The **files** need to be pasted in the directory, not the text inside them.

I hope that clears things up for you :)

---

### Post by hawkhock on 2009-03-06
> **s0l1dsnak3123 said:**
> The **files** need to be pasted in the directory, not the text inside them.

I hope that clears things up for you :)

Know this may sound dense - I downloaded the files into a folder.  Do I just copy the file name, i.e. dll.conf, as listed?  Or should I have downloaded the files to some other place, like my desktop?

My scanner works without the added files. Am being overly cautious for a reason. I just got done with a full reinstall because I royally screwed up my system with an attempt to install a .deb file that I later learned was not compatible with Hardy.  Not anxious to do this again anytime soon.

Georgi

---

### Post by s0l1dsnak3123 on 2009-03-07
> **hawkhock said:**
> Know this may sound dense - I downloaded the files into a folder.  Do I just copy the file name, i.e. dll.conf, as listed?  Or should I have downloaded the files to some other place, like my desktop?

My scanner works without the added files. Am being overly cautious for a reason. I just got done with a full reinstall because I royally screwed up my system with an attempt to install a .deb file that I later learned was not compatible with Hardy.  Not anxious to do this again anytime soon.

Georgi

Not a problem, I can totally identify with that :)
Make sure that in the folder you copy to, they have the same filenames as listed.
Think most people (if not all) can identify with being overly cautious, and taking things slowly is always best if you don't want to screw things up :P

---

### Post by hawkhock on 2009-03-07
Thanks for your help. Before I tried anything, I checked and the files were already in place. Not sure why I didn't think of that in the first place.  However, I've uninstalled/reinstalled my Lexmark many times and your instructions work beautifully each time.  Many thanks.

---

### Post by s0l1dsnak3123 on 2009-03-07
> **hawkhock said:**
> Thanks for your help. Before I tried anything, I checked and the files were already in place. Not sure why I didn't think of that in the first place.  However, I've uninstalled/reinstalled my Lexmark many times and your instructions work beautifully each time.  Many thanks.

You are more than welcome :)

---

### Post by kaddsubunto on 2009-03-08
Hi all
I have just installed unbutu 8.10.
I have a lexmark 1270 printer.  my first try with linux was with mandriva 2009.  I spent 15hrs trying to get this printer to work following various forum instructions with out any luck.  I installed ubunto 8.1 and as soon as the desktop came up, it wanted to install updates.  I cancelled this and came to this forum and installed the two .deb files.  When I clicked to download them, I did not save them, but used "open" and when that was finished, I went to the printer setup area.  I selected to install new printer and selected the default lexmark 1200, and then had it look for driver.  Then selected lexmark and the z600 option was there. Selected it and tried a test page and a page from the web.  Worked perfectly (a bit slow but what the hell).  I spent 15 hrs trying to get it to work on mandriva 2009 with no luck. 
thanks

---

### Post by s0l1dsnak3123 on 2009-03-08
> **kaddsubunto said:**
> Hi all
I have just installed unbutu 8.10.
I have a lexmark 1270 printer.  my first try with linux was with mandriva 2009.  I spent 15hrs trying to get this printer to work following various forum instructions with out any luck.  I installed ubunto 8.1 and as soon as the desktop came up, it wanted to install updates.  I cancelled this and came to this forum and installed the two .deb files.  When I clicked to download them, I did not save them, but used "open" and when that was finished, I went to the printer setup area.  I selected to install new printer and selected the default lexmark 1200, and then had it look for driver.  Then selected lexmark and the z600 option was there. Selected it and tried a test page and a page from the web.  Worked perfectly (a bit slow but what the hell).  I spent 15 hrs trying to get it to work on mandriva 2009 with no luck. 
thanks

That's great news, your very welcome :)

---

### Post by switch10 on 2009-05-16
Does anyone know if I can force these drivers to work on my 64 bit ubuntu 8.10?  I couldn't find any 64 bit drivers.

---

### Post by alket on 2010-03-25
Thank you. This worked perfectly in Lucid Beta 1.
You need to have libstdc++5
> [http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)


---

### Post by s0l1dsnak3123 on 2010-03-25
> **babaroga said:**
> Thank you. This worked perfectly in Lucid Beta 1.
You need to have libstdc++5

No problem, it's awesome that it still works in Lucid. I'll add that link to the first post.

---

### Post by alket on 2010-03-25
> **s0l1dsnak3123 said:**
> No problem, it's awesome that it still works in Lucid. I'll add that link to the first post.

Thank you again for awesome packages. By the way Scanning with x1270 works out of box in lucid even without those packages.

---

### Post by s0l1dsnak3123 on 2010-03-25
> **babaroga said:**
> Thank you again for awesome packages. By the way Scanning with x1270 works out of box in lucid even without those packages.

I didn't actually make these packages, I only found them - but you're welcome :) I'll add a notice to the front-page about the scanning :)

---

### Post by randywilharm on 2010-04-25
Its a winner!

I have 8.04 Ubuntu + that Lexmark I have would have gone
straight to the dumpster if I had'nt tried the remedy
you posted.

I got the scanner working fine, but I won't bother
with the printer as they're too unreliable.

Many thanks!

---

### Post by poetofzwan on 2010-06-20
Thank you very much s0l1dsnak3123!

My printer now works perfectly in Ubuntu 10.04 Lucid!

---

### Post by guidos on 2010-07-31
Great how-to.  Using the printer installation part only, I also got my X1240 to work under Lucid. Many thanks! :popcorn:

---

### Post by $hellier on 2010-08-21
Ur awesome.. I have been looking for a week for instructions and tried almost everything. Ran into this as a last resort and it works.  Thank you.:D

---

### Post by p3t3rs on 2012-02-17
This is not working on Ubuntu 11.10... When i press PRINT, Lexmark x1270 doesn't even turn on...
Can anyone help me solve this problem??

---

