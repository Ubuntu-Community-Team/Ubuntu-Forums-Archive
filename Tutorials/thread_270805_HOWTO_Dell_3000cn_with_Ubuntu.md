---
title: "HOWTO: Dell 3000cn with Ubuntu"
date: 2006-10-03
forum: Tutorials
---

### Post by kewldude606 on 2006-10-03
[SIZE="4"]THIS IS FOR PRINTING OVER A NETWORK CONNECTION.  NOT TESTED FOR PRINTING VIA USB OR PARALLEL.[/SIZE]
[Size="3"]Works even better with Gutsy![/size] See [http://ubuntuforums.org/showpost.php?p=4174927&postcount=15](http://ubuntuforums.org/showpost.php?p=4174927&postcount=15)

**Preface:**
I bought a Dell 3000cn Network Printer before realizing the awesomeness of Ubuntu and linux in general.  Now, that I have Ubuntu, I can't just go out and buy another $300 printer.  So I searched the web and came up with [url=http://www.mit.edu/~jik/3000cn/]this page[url], which didn't work for me.

**Step One: Change some printer configurations**
[LIST=1]
[*]On the printer, press the Menu button.
[*]Scroll to Configuration --> PCL.
[*]Most of these should be set correctly except for Color.  Change this option from Black to Color.
[*]Also check Paper Size and set it to the correct value (varies).
[/LIST]

**Step Two: Making the Physical Connection**
This is out of the scope of the guide, but might save you troubles if your printer doesn't work.
[LIST=1]
[*]Get the IP address of your printer.  If you know it by heart, go on, otherwise, go to Menu-->Configure-->Network-->TCP (or TCP/IP, varies)-->IPAddress.
[*]On your computer, go to Applications-->Accessories-->Terminal and run the command: [FONT="Fixedsys"]ping <ipaddress>[/FONT].
[*]If you get data back that says something like [FONT="Fixedsys"]64 bytes from 192.168.2.101: icmp_seq=2 ttl=254 time=4.27 ms[/FONT], go to Step 3.
[*]If you didn't get data like that, make sure everything is plugged in, then use Google, and finally post on the forums (even in this thread).

**Step Three: Setting Up Ubuntu**
[LIST=1]
[*]Add a new printer.  Go to System-->Administration-->Printing and double click on "New Printer".
[*]Select network printer near the top.
[*]Change CUPS to HP JetDirect.
[*]In the Host text box, enter in the IP Address that you got from Step 2.
[*]In the Port text box, enter 9100 (should be pre-filled)
[*]Click Forward and enter the following information: Manufacturer-->HP, Model-->Color LaserJet Series PCL 6 CUPS, Driver-->Standard
[*]Click Forward and enter in the appropriate information.  It really doesn't matter what you put here.
[*]Wait a bit and your new printer should appear in the Printers window that you opened in number 1 of this step.  Right click on it and select properties.  Set the properties according to the following images:
[*][img]http://img50.imageshack.us/img50/3590/screenshot3000cnproperties4ik1.png[/img]
[*][img]http://img127.imageshack.us/my.php?image=screenshot3000cnproperties3zm7.png[/img]
[*][img]http://img127.imageshack.us/img127/6704/screenshot3000cnproperties3zm7.png[/img]
[*][img]http://img134.imageshack.us/img134/2388/screenshot3000cnproperties2jq4.png[/img]
[*][img]http://img50.imageshack.us/img50/7106/screenshot3000cnproperties1ci9.png[/img]
[*][img]http://img134.imageshack.us/img134/2397/screenshot3000cnpropertiesqg0.png[/img]
[/list]

**Step Four**
There is no step 4.  But you might want to test your printer by clicking the Print Test Page button in the Properties Window.

---

### Post by sostenible on 2006-10-28
Hi, I don't have in my Ubuntu 6.10 anything such as Color LaserJet Series PCL 6 CUPS.

Can you tell me an alternative model to select?

Many thanks.

---

### Post by kewldude606 on 2006-10-28
Try sudo aptitude install hplip hpijs and see if it shows up.

---

### Post by Jæd on 2006-12-15
I have both of those but still can't see the driver... Any other hints...? :D

---

### Post by jhaitas on 2007-02-02
Hey kewldude606....

I hope you or an administrator could address why "Manufacturer-->HP, Model-->Color LaserJet Series PCL 6 CUPS, Driver-->Standard" is not available in the standard install of edgy... even following your suggestion to: ```
sudo aptitude install hplip hpijs
``` does not make this option available...

is it possible you upgraded to edgy from a previous version of ubuntu? or perhaps you somehow you installed this driver from another source and failed to mention it?

PLEASE HELP

THIS PRINTER IS DRIVING ME CRAZY

---

### Post by keith11 on 2007-02-02
To Jhaitas and Jaed:

I have a Dell 1700n as the network printer and I selected Laserjet series PCL 4/5 and it worked. So you may want to try that. Hope it works for both of you.

---

### Post by jhaitas on 2007-02-02
no keith that did not work....

thank you for the thought though....

We need to figure out where the ```
Manufacturer-->HP, Model-->Color LaserJet Series PCL 6 CUPS, Driver-->Standard
```
drivers came from... they are not a part of the Edgy distribution. If anyone has any ideas about this it would be greatly appreciated.

---

### Post by BenHines on 2007-02-13
Hi,

I have a Dell 3000cn and am using Dapper.  I tried the solution for printing here, but when I print a test page, it is all sqashed into the upper-left quarter of the page.  Text is also squashed.  Has anyone else had this problem.  Has anyone solved this problem?  

BTW...why aren't there any (or many) linux drivers for Dell printers?

---

### Post by jhaitas on 2007-02-13
dell ******* sucks... their printers are a nightmare and their tech support doesn't care... save your sanity and forget it... i've had no luck... if you figure it out PLEASE let me know.... i assure you i've tried every guide available on the net and tried contacting their authors... i wouldn't believe anyone who says they've got it working unless they can help you get yours working... no one has been able to help me and i do know what i'm doing...

**** DELL

---

### Post by sovietfunk on 2007-02-19
In KDE's printer setup, this driver is listed under "ESP" as manufacturer, instead of under HP. 
I don't have the same printer as listed above, but it did let me finally print something from a Xerox WorkCentre 7132 multifunction printer/copier/fax, while I'm waiting for a serviceman to upgrade it with a PostScript module.

---

### Post by kevin niebuhr on 2007-02-19
Your post fixed my printing problems with my Epson R220, could not get it to work until I read you post.
Thanks,
Kevin

---

### Post by neonigma on 2008-01-03
Well, sorry for my English (I'm spanish), and forgive the delay in replying.

I'm using Kubuntu and we have in our job a DELL 3000cn. I was fighting with Kubuntu about way for printing my notes in color.

I follow your first post, but I hadn't anything such as Color LaserJet Series PCL 6 CUPS in the KDE -> System Preferences -> Printers menu.

Nevertheless, this special printer APPEARED when I connected to CUPS via Web => [http://localhost:631](http://localhost:631)

Simply add a new printer and specify a name for it, select AppSocket/HPJetDirect like Connection, give the URI: socket://xxx.xxx.xxx.xxx:9100 in example (changing the "x" by printer IP) and select HP as manufacturer in the next stage. Click next and HP Color Laserjet Series PCL 6 CUPS appears. In my example is the last printer from the HP Color Laserjet models.

I don't know why this model appears in CUPS web mode but it can't finding in the KDE printer menu.

Greetings.

---

### Post by jhaitas on 2008-01-03
are you saying you got this piece of **** printer to successfully print color documents that are correctly aligned???

i am skeptical... Dell has been tremendously unhelpful... the employees seem to have nothing but contempt for Linux... 

i am thoroughly disappointed in Dell and will not purchase from them unless there is a truly compelling reason to do so...

Dell follows Microsoft's shitty business practices it seems – they care more about money than satisfied customers

---

### Post by neonigma on 2008-01-08
I agree with you: Dell seems a typical "only works in Microsoft Windows" bla bla bla.

It's very strange. I was printed only a color document (with ONLY one page) and works fine. You have to configure it for printing in 600 dpi, in another way doesn't work for me.

But when I try to printing a medium-size doc (about 20 pages), printer doesn't work. I was trying this about jan 3, so when my boss going to have breakfast (I'm a work-study in an University), I'll try again.

Greetings!

---

### Post by kewldude606 on 2008-01-20
Hi all,

I just wanted to update this thread with information for Gutsy.  The steps are all pretty much the same, just the dialog boxes are a little bit different.

To get it working in Gutsy, once you have finished following the steps above, go to Control Center-->Printing (its in the Hardware category)-->Select the printer under the Local Printers menu-->Go to the printer options tab-->Change the output resolution to 600DPI.

Now, I have trouble printing large documents even from Windows to this printer (it runs out of RAM occasionally), so I would send things a few pages at a time.  Besides that, the printer works a lot better under Gutsy than it did in Feisty for me at least.

Also, this is from a clean install of Gutsy.

Enjoy!

---

### Post by StevenBirnam on 2008-04-03
Don't know why you are complaining about Dell - the key piece in the puzzle when configuring the 30000cn is to make sure you have - and it was mentioned several times before - configured the printer for 600dpi (300dpi, which seems to be the default, produces a small test page, with the printed area restricted to the upper lefthand corner of the page - while setting it to 600dpi gives the perfect result for printing the test page.

The HP driver works fine, but it would be nice if someone, preferably Dell, posted a driver for the printer.

StevenB

---

### Post by StevenBirnam on 2008-04-03
BTW: If you complain about Dell's allegiance to MS, then what about their supplying Google with the Google GSA (Google Search Appliance)?
Dell isn't all that bad - it's just that they are new to the Linux market, and started off on the wrong foot with Redhat. Hopefully, demand from the Ubuntu community will change that.

StevenB

---

### Post by neonigma on 2008-04-21
You have reason, maybe Dell it's a newbie in this world of free software.

I hope Dell compile its drivers for a better Ubuntu compliance in the future.

Greetings!

---

### Post by rhdinah on 2008-06-30
Yeah, don't be too hard on Dell as they've announced their support in the future for Linux. To expect a lot of support on older drivers might be a bit much, but to put an older driver in the public domain is not. Honestly, the people at Ubuntu or Debian should get in bed with Dell a bit to convince them that in no way does porting drivers with open source have a impact on their business other than possibly increasing it.

I have this printer too ... and under Linux ... unacceptable performance ... so a tiny Windows partition somewhere with the supported driver there ... when I need total compliance ... is not too much to expect ... I guess ... sigh ...

---

### Post by melanarchy on 2008-08-05
If the printer is printing just into the left corner, just change the res to 600dpi.

---

### Post by keptang on 2010-05-14
Thanks for the guide, works perfect in Lucid as well :)

---

### Post by neonigma on 2010-05-14
Cool! ^__^

---

### Post by Nicholas Goodwin on 2010-06-07
The Dell 3100cn driver works fine for me with 10.04

---

### Post by AlbertP on 2011-09-02
There will be an option Dell 3000cn in the next Foomatic version (I hope that 3.0.8 it comes out before the Oneiric release, so that Oneiric will include this). For the time being you can use the drivers for Dell 3100cn or Generic PCL 6 / PCL XL which are included with Natty.

For Lucid/Maverick users, it's recommended to update foomatic-filters to 4.0.7. The .deb file for Natty ([http://packages.ubuntu.com/natty/foomatic-filters](http://packages.ubuntu.com/natty/foomatic-filters)) works fine on Maverick, I haven't tried it on Lucid.

---

