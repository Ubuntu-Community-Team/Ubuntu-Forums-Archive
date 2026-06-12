---
title: "new repository for a FEW canon printer drivers"
date: 2006-10-22
forum: Repositories &amp; Backports
---

### Post by slimdog360 on 2006-10-22
EDIT: I just noticed this thread is still going, everyone should note that I started this thread almost a year ago (from when I wrote this edit). This was also before feisty and its included printer drivers which got my ip3000 working was born. Since my printer is working I have stopped checking this thread, not to mention my other disclaimer at the bottom which states that I only found the link, don't know anything about them, don't have anything to do with them and hence can't give any advice. 

[B]If you need advice feel free to post here but don't expect much of a response. So if you do need help you should probably start a new thread or join in on a better one.
[/B]

found this site looking for a driver for my pixma ip3000. It says that the pixus  ip3100 is the same thing but when I use the driver its very slow.

edit:just had a good test of the driver. It works quite well, quality wise, but still very slow with the occasional speed burst. But come to think of it the samething was happening with the bjc7000 driver, which at first was working fine. Maybe its my computer or something wrong with the printer?
Ive also noticed a few other new printers appear in the list besides the ones listed below so maybe give it a shot if you have a pixma/pixus printer.

I think that there should be one big repository where all drivers for all printers are kept. That way when someone installs their OS they can just apt-get install their respective printer. We can all dream.

edit: the link has been moved to here [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/")

the supposed supported printers are:
Canon Pixus iP3100 
Canon Pixus iP4100 
Canon Pixus iP8600 
(probably) Canon Pixma iP1000 
(probably) Canon Pixma iP1500 
Canon BJ S700 (with iP3100 driver, 2006-01-08 ) 
Canon Pixma 3000 (with iP3100 driver, 2006-01-11) 
Canon PIXMA MP750, MP780 (with iP4100 driver, 2006-03-11)


edit again: The reason for me posting this is that I came across it one day and thought wow, drivers for unsupported printers this is great. So I posted it in the hope that others can get their hardware working under linux and this seems as though it is the case for some but not all.

Now I should mention that I dont actually know anything about the drivers, but they do work with my printer (under edgy). So although of course you can post questions, there is next to no chance of me being able to help you printer-driver-wise if they do not work, thats not so say that I wont try though.

---

### Post by terrax on 2006-10-30
How did you install the repos?
When I try to do it in edgy. This error came up: 

That it missed:
pstocanonbj: Dependency: libcupsys2-gnutls10 (>= 1.1.23-1)

---

### Post by slimdog360 on 2006-11-01
update:
yep I tried this myself in edgy and it doesnt seem to work. The drivers for me worked in dapper and mepis though. 

Ive emailed the guy to see if this can be fixed and I'll put the response I get here, assuming that I do get a response. 

There are some other drivers from the same site here
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/")

which cover:
Canon Pixus 550i (or i550) 
Canon Pixus 850i (or i850) 
Canon Pixus 950i (or i950) 
Canon Pixus iP90 (with 550i driver)
Canon Pixus 560i (or i560) 
Canon Pixus 860i (or i860) 
Canon Pixus 990i (or i990)

and some epson drivers:
LP-9800C 
LP-9500C 
LP-9200C 
LP-9000C 
LP-8800C 
LP-8500C 
LP-8300C 
LP-8200C 
LP-8000C 
LP-3000C

---

### Post by terrax on 2006-11-01
Weird.

I actually got it to work, very easy in Edgy.

Just installed the libcupsys2-gnutls10 package, from the debian repos. And it now works flawlessly with my canon pixma mp750..

---

### Post by slimdog360 on 2006-11-02
hmm... mine still isnt working under edgy, I have that package installed and everything.
At least someone got some use out of the drivers.

---

### Post by drobvice on 2006-11-18
I got my mp500 printer working with this!  The driver didn't show up in cups but I tried the web setup and searched for the mp500 ppd file /usr/share/cups/model and it worked like a charm. Probably could click the install driver button in the cups gui as well.

**Edit**  Well, it was working.  Now it just sits there and won't print. :{

---

### Post by tom56 on 2006-11-20
> **slimdog360 said:**
> I think that there should be one big repository where all drivers for all printers are kept

There is, it's called restricted and is available (but not enabled) by default. If the driver you want isn't there file a bug so others can use it (the driver) without having to use unofficial repos.

---

### Post by La muerte del DIos on 2006-11-22
Works perfect on Edgy with Pixma iP1000. Thank you very much.:)

---

### Post by Krwawy on 2006-11-24
My canon pixma ip1000 works too but without color. :( What I must change?

---

### Post by xopher on 2006-11-25
Nice find!

My girlfriend just bought herself a Canon printer, maybe this will get it working on linux for her so she can forget about windoze all together.

Thank you.

---

### Post by slimdog360 on 2006-12-02
if it hasnt already been seen from the change of link in my first post, the guy who runs the site has added a different repository for us edgy eft users. He/she never emailed me back but it seems as though the person has taken notice and fixed it. But unfortunatley for my poor ip3000 it seems as though the ip3100 has been left out of the edgy repository. Oh well I guess the bjc-7000 driver will have to do.

---

### Post by yabbadabbadont on 2006-12-03
I noticed that you have the i990 listed, yet his site doesn't mention it at all.  Is this just a typo on your part, or is it supported as a different model number?  Thanks in advance.

---

### Post by slimdog360 on 2006-12-03
I copied that info off of his old page, so I cant say whether it is still there anymore. Only one way to find out though I suppose.

---

### Post by panas on 2006-12-09
slimdog360 thanks for the info.
Now i don't need xp for printing with my ip6600D.

---

### Post by wersdaluv on 2007-01-07
I have a canon Pixma MP150. What driver can I use?

---

### Post by johnmc on 2007-01-19
awesome, this worked like a charme for me & my i560 :)

Thanks!

---

### Post by blackdalek on 2007-01-21
These Pixus ip3100 drivers are really no good at all for my situation. Not only does it refuse to print from the paper cassette tray, but it will not accept print jobs from Macs running OS X on the LAN. Print jobs just end up in the print queue as "Stopped: job-stopped", and cannot be resumed.

I have not yet tried the commercial Turboprint drivers, but it seems as though they might be the only sensible option to use since no one has been able to squeeze any blood out of Canon to get this thing working in linux.

Partial drivers just isn't going to cut it in my situation.

Forgot to mention - I am trying to get this to work with the Pixma iP3000 printer

---

### Post by slimdog360 on 2007-01-23
> **blackdalek said:**
> These Pixus ip3100 drivers are really no good at all for my situation. Not only does it refuse to print from the paper cassette tray, but it will not accept print jobs from Macs running OS X on the LAN. Print jobs just end up in the print queue as "Stopped: job-stopped", and cannot be resumed.

I have not yet tried the commercial Turboprint drivers, but it seems as though they might be the only sensible option to use since no one has been able to squeeze any blood out of Canon to get this thing working in linux.

Partial drivers just isn't going to cut it in my situation.

Forgot to mention - I am trying to get this to work with the Pixma iP3000 printer

use the canon bjc-7000 driver, make sure you adjust the settings first for it to use the cassette to get it working. Ive personally found that for some odd reason using the kde print manager makes it work better. Perhaps because of the greater choice in settings? I always set the printer to take priority over other things which seems to stop the printer from going slow..

---

### Post by zero-9376 on 2007-01-27
Hi, 
I am currently setting up a computer with dapper for my girlfriends parents and they have a cannon i560. Because they live in a different town its not possible for me to set this up myself but I want to make sure that its going to work otherwise I will have to dual boot which I really dont want to as they will then end up using windows out of habbit.

I am using dapper 6.06.1 as the distro and want to know what is the best way to get the printer to work. I have tried installing the drivers from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) but libc6 and libcupsys are the wrong versions (in supporting edgy did the site manager drop dapper support). If these drivers aren't going to work what ones will. I cant seem to get to the japanese cannon download site mentioned a few places on the web. Do the bjc7000 drivers work well enough for photo printing? 

I need information specific to the i560 and of course Dapper.
Thanks in advance.

---

### Post by slimdog360 on 2007-01-28
I dont have a clue mate, I just found the site a while back and decided to share it with everyone. The bjc-7000 driver is for the canon ip3000, my current printer, so I dont know what driver you should use sorry. You can always email the guy and see if you can get a response.

---

### Post by jolt256 on 2007-01-28
I managed to get my i560 working in Dapper by installing the Debian packages from that site, rather than the Ubuntu ones. Follow the directions for Debian, not Ubuntu, here:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Once I did that, I could get the GNOME test page to print, but nothing else. Something is wrong with the bjtocanonps binary installed by the Debian packages (it segfaults), so grab the sources here:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/pstocanonbj_3.3.orig.tar.gz](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/pstocanonbj_3.3.orig.tar.gz)

You'll need to apt-get libcupsys2-dev and libppd-dev (maybe others too, but try those first). Then, untar the source files and run ./configure && make. You'll then want to grab the freshly-compiled pstocanonbj binary from the src directory, and copy it to /usr/lib/cups/filter, replacing the old pstocanonbj. That got it all working for me. Good luck!

---

### Post by starling on 2007-02-16
Hi
I have a canon i560 and the drivers from here don't print. Any print job sits in the spool 'stopped' and can't be resumed. It doesn't seem to send anything to the printer as the light doesn't flash.
Any ideas?

thanks

---

### Post by slimdog360 on 2007-02-17
you can try this from linux printing [http://openprinting.org/show_printer.cgi?recnum=Canon-i560]("http://openprinting.org/show_printer.cgi?recnum=Canon-i560")

thats about the best I can do Im sorry. Its good to see a few people from newy on these forums (let alone using linux).

---

### Post by slimdog360 on 2007-02-19
okay, for some reason after installing xubuntu the drivers now work flawlessly with my canon ip3000, no slow down, no dodgy colours, no nothing. The driver doesnt support the auto duplexing but all I have to do is print off every second page then turn the pages around and print on the other side. Not much hassle at all. Fantastic.

---

### Post by degsyw on 2007-03-11
thx slimdog works a treat ....... i have a full colour test page anyway! first though i did make sure  i removed all old method with libpng2, libtiff3g and the downloaded rpm's as the install reported some files already in place. the old method was a complete failure on edgy ubuntu fully updated for my canon i950

degsyw

---

### Post by unni on 2007-03-11
Thank you very very much slimdog360. I had been looking for a driver for my Canon Pixma IP1000 for over two months, till I finally gave up. Today, when I accidentally saw this thread, I had no hope. But guess what, it works remarkably fine. I can easily print B/W  documents with my Pixma IP1000. I haven't tried any colour prints as I don't have colour ink.:) But I have three problems:
1. Since I don't use colour ink, how do I specify cups to do only B/W printing. I saw an option with 'RGB' as value in printer driver settings. But I can't change that.:( 
2. Is there any management tool for Canon printers? What I am looking for is a way to send command to clean the printer, like the one available in Windows Canon driver?
3.This is the most important. Since my printer has a lot of wear and tear (possibly due to constant refilling), I can't get good printing unless the print quality is set to highest (In the Windows driver, there are atleast three options - highest, normal & fastest). But with this driver, I think the quality level is equivalent to the 'normal' option in Windows driver. Is there any way to change it? Is it related to the dpi? Mine is currently at 600 dpi. I can't change that value even as root.

---

### Post by slimdog360 on 2007-03-12
I dont really know much about the drivers I just found them one day and decided to share but you can try whacking [http://127.0.0.1:631/](http://127.0.0.1:631/) into firefox and try to configure cups that way.

---

### Post by Gargamella on 2007-03-12
i have a canon pixma ip2000. i will try it

---

### Post by slimdog360 on 2007-04-04
Just to let everyone know, once feisty comes out this will be old news but anyway. Feisty seems to support heaps more canon printers. My canon ip3000 now works perfectly, auto-duplexing and all. This is under feisty.

---

### Post by jitsu on 2007-05-01
I'm running Ubuntu 6.06 and I have a Canon Pixma 3000.

Today I tried to download the trial driver from Turboprint. I saved it to my desktop and tried unsuccessfully to open it.

Got the following message:
Could not open 'turboprint 1.95-2_i386(2).deb'

Package might be corrupted or you are not allowed to open the file.



What do I have to do free trial driver for Pixma 3000.


I'm trying to learn, but maybe I better ask for help.


thanks

---

### Post by zero-9376 on 2007-05-10
Good news for people with cannon multifunctions (well for me it was anyway) this site

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp510_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp510_support.aspx)

provides drivers (albeit in rpm format) for the MP510 printer and scanner, I have only tried the scanner application tonight but it worked perfectly, will try printing soon.
To convert the rpms to debs use alien available in synaptic etc.

alien packagename.rpm --to-deb --scripts (may need sudo)

Then install the generated packages, not sure if it creates a menu item but for the scanner the application is scangearmp again haven't done the printer driver yet.
if scangear doesnt start make sure libpng3 and libtiff4 are installed as well.

Very happy to see cannon providing these drivers, I was in the process of putting vmware together to handle scanning via XP, now no need. 

I would also like to thank teetee for orignially pointing out the site in another topic which refers to MP600
[http://ubuntuforums.org/showthread.php?p=2628646#post2628646](http://ubuntuforums.org/showthread.php?p=2628646#post2628646)

Note that I am using edgy, so cant comment for fiesty.

Seperately to the ubuntu & linux communities and developers (who probably wont read this) thanks for the great work, my computer is now fully functional (windows cant even run my monitor at proper resolution).

---

### Post by zero-9376 on 2007-05-10
attempt 1 at install didnt work, printer is added but nothing happens with testpage...to be continued

---

### Post by Ulysses on 2007-06-09
Morning

Having the same problem. Want to print pictures with my recently purchased Canon Pixma IP3000 and I am getting nowhere with the printing
Using 6.06. It sees the printer, sends the job (i think) and the printer does not print. Only trying it on index cards (testing the photo print) and the manual feed does not want to work

Has anyone gotten anywhere with this? Help would be appreciated. Need to justify my purchases, if you know what I mean!

RAR

---

### Post by slimdog360 on 2007-06-12
try the gutenprint driver

---

### Post by hummingbird59 on 2007-06-13
Hey Ulysses!  I know what you mean ([http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751))!  And to think, I almost bought an HP instead of a canon.....](*,)  If you have any luck, please let us know!

---

### Post by Cappy on 2007-06-15
I have a Canon Pixma MP780 hooked up to a Windows Vista machine. I can log in (Windows Printer (SMB)) on the first step of "Add a Printer" but all I get is "Microsoft Office Document Image Writer".

I'm running AMD64 Feisty, should I extract the i386 packages to usr/lib32/, force install them, or should I compile each of the tarballs?

Edit: I see my printer on "step 2 of 3: Printer Driver" as "Multipass MP780" and I have to click on the very bottom drop down box and I choose "Gutenprint CUPS (Simple)". Doesn't do anything. Probably because it isn't showing it on the first step.

Edit Again: Got it! The printer settings were messed up in Vista, I was trying to configure it in "Networking Settings and Sharing" but it would only let me fix the problem in Vista's Printer configuration on the control panel. Otherwise it would just say "You do not have sufficient permissions!" when I tried to change the my printer's settings.  Vista = retarded.

---

### Post by thedarkside123 on 2007-06-17
Did any get their canon mp510 to work?

---

### Post by Rocketmac on 2007-07-03
cnijfilter-mp510-2.70-1.i386.rpm  --> cnijfilter-mp510_2.70-2_i386.deb
scangearmp-mp510-1.00-1.i386.rpm  -->  scangearmp-mp510_1.00-2_i386.deb

done by `sudo alien --scripts *.rpm`

Just did a `dpkg -i *deb` and it worked.   

I was able to scan with Xsane 0.991.:popcorn:

I'm using Ubuntu Feisty 7.04 with kernel: 2.6.20-16-generic.

I was also able to print as well.  (Installed printer using "System->Administration->Printing").   Driver selected:  "High Quality Gutenprint (CUPS) (expert)".  Yes, duplex does work (you have to select it in the driver before printing.


If anyone needs those debs, I could gmail them to you.


###  EDIT ###
The above is on a Canon Pixma MP500 All-in-One sold in the US.

Rocket

---

### Post by 00t'akk! on 2007-07-08
Hey rocketmac,

could you mail me those debs. 
Would like to try them.
Where do you locate the gutenprint driver?

thx a lot

---

### Post by Rocketmac on 2007-07-24
> **00t'akk! said:**
> Hey rocketmac,

could you mail me those debs. 
Would like to try them.
Where do you locate the gutenprint driver?

thx a lote 


I just downloaded the rpm's from the AU site listed at the top of the thread.

Gutenprint is just the name of the driver available after you install the debs.


:guitar:  
Rock on!

---

### Post by GNUtoo on 2007-09-04
hello,
i have gutsy gibbon(because of the intel wifi drivers of the laptop)
so i have installed the Canon PIXMA MP510 with gutsy gibbon(without the repository) and i tried to print that:
[http://www.gnu.org/graphics/meditate-tiny.jpg](http://www.gnu.org/graphics/meditate-tiny.jpg)
but it gave me that:
[http://img393.imageshack.us/my.php?image=out2xe5.jpg](http://img393.imageshack.us/my.php?image=out2xe5.jpg)

what should i do? try the repository?

---

### Post by BlackShift on 2007-09-19
@GNUtoo
I've got the exact same print, but only after selecting the MP500 model, since the MP510 was not listed (feisty fawn). I've had better results selecting the BJC-8200 and the gutenprint driver, or the S600 with the recomended driver, however YMMV.

---

### Post by nemo1982 on 2007-09-27
I just passed to ubuntu for obvious reasons. But I'm startin to regret it because I can't configure half of the things I have. For example the printer... I'm experiencing the same problems with my canon MP510. Rocketman! Please tell me how you managed because I totally can't make it work!:confused:
Can you please tell me step by step what I have to do to perform a miracle?
thanks a lot...

:guitar:

---

### Post by nemo1982 on 2007-09-27
sorry, i didn't get a word. Can you repeat step by step how to make an mp510 work properly? or do you have an mp500? cause then there's a difference and  a big one too...

thx in advance

:guitar:

---

### Post by exactopposite on 2007-10-01
i was able to get the canon (ip3000) working with no problem in fedora before using the info from this link ([http://tinyurl.com/37lb8f](http://tinyurl.com/37lb8f)) but with ubuntu the colors were off. i have an epson printer that works great with linux, but the canon is a better printer, so it would be great to get it working in ubuntu

---

### Post by oliwally on 2007-11-10
I need help with the MP510 also. I've been able to install the alien-converted packages and my printer is now listed when I go through system_settings - printer - add menu (Kubuntu), but when hitting the test-print button nothing happens.

Has anyone had any luck making this printer work with K/Ubuntu?

---

### Post by oliwally on 2007-12-12
> **nemo1982 said:**
> I just passed to ubuntu for obvious reasons. But I'm startin to regret it because I can't configure half of the things I have. For example the printer... I'm experiencing the same problems with my canon MP510. Rocketman! Please tell me how you managed because I totally can't make it work!:confused:
Can you please tell me step by step what I have to do to perform a miracle?
thanks a lot...

:guitar:

I've had some luck with it. My printer and scanner are now working!!!

Try this:
[http://ubuntuforums.org/showpost.php?p=3938403&postcount=4]("http://ubuntuforums.org/showpost.php?p=3938403&postcount=4")

---

### Post by stadt on 2007-12-23
> **oliwally said:**
> I've had some luck with it. My printer and scanner are now working!!!

Try this:
[http://ubuntuforums.org/showpost.php?p=3938403&postcount=4]("http://ubuntuforums.org/showpost.php?p=3938403&postcount=4")

Many thanks for translating.

A minor correction. Most work was done by 'banty' and me. What 'der Geier' has changed in the wiki was nearly nothing (hadn't noticed any relevant change).

BTW. there are now drivers for the Canon MP 520/610 and Pixma iP3500/4500 too and -surprise, surprise - they are available as *.deb pakages from Canon see:
[http://www.canon-asia.com/index.jsp?fuseaction=support](http://www.canon-asia.com/index.jsp?fuseaction=support)

---

### Post by mrojas73 on 2008-01-06
I have been e-mailing all the manufactures like Logitech and Canon letting them know that I will not purchase their products any more until they start making Linux drivers for their products.

We need to make our voice heard, it is time they start paying attention to us.

---

### Post by criskat777 on 2008-01-29
Thanks for the heads up:) i had this printer on standby since i started full time use of Ubuntu on my main PC. What i really like about this printer is the price of it's ink cartridges $1.75 Black $3.25 Color , simply un real. And yes US Dollars.  I had tried other posts but never got it working before.

---

### Post by stadt on 2008-01-29
Canon has now drivers as deb packages for the MP 140

---

### Post by Rocketmac on 2008-03-09
To install the drivers for the MP500, I just followed the steps at the top of this thread.  The only exception is that I used alien --scripts -k [name_of_rpm].rpm.

This was on a Dell M1210 Laptop running 7.04 at the time (It will still work with 7.10).

I don't have the control panel for ink, which is fine by me as I don't use it (read: trust it).

---

### Post by josh_dye on 2008-04-17
> **Rocketmac said:**
> cnijfilter-mp510-2.70-1.i386.rpm  --> cnijfilter-mp510_2.70-2_i386.deb
scangearmp-mp510-1.00-1.i386.rpm  -->  scangearmp-mp510_1.00-2_i386.deb

done by `sudo alien --scripts *.rpm`

Just did a `dpkg -i *deb` and it worked.   

I was able to scan with Xsane 0.991.:popcorn:

I'm using Ubuntu Feisty 7.04 with kernel: 2.6.20-16-generic.

I was also able to print as well.  (Installed printer using "System->Administration->Printing").   Driver selected:  "High Quality Gutenprint (CUPS) (expert)".  Yes, duplex does work (you have to select it in the driver before printing.


If anyone needs those debs, I could gmail them to you.


###  EDIT ###
The above is on a Canon Pixma MP500 All-in-One sold in the US.

Rocket
The cannon USA site says that the  mp510 will not work with linux.  Will I need to make my printer think it was boutght in australia to use this?

---

### Post by josh_dye on 2008-04-18
I emailed canon about this , and asked them why the USA site says that they don't support linux, and they did respond but they totally evaded the question; I though ssome of you could get a good lagh out of readin their email

> **Canon Support0]	From: 	  [email]CareCenter@cits.canon.com[/email]
	Date: 	April 18, 2008 5:35:32 AM PDT
	Subject: 	Re: Response from Canon - SWSS Web Escalation  (KMM8569435V22071L0KM)
	To: 	  [email]josh.jpenguin@gmail.com[/email]
	Reply-To: 	  [email]CareCenter@cits.canon.com[/email]

Dear Josh Dye:

Thank you for writing to us about your PIXMA MP510.  We value you as a 
Canon customer and appreciate the opportunity to assist you.

Canon USA has not announced support for Linux and Canon consumer Bubble 
jet printers.  Unfortunately, we do not have any information on future 
product or driver development at this time.  We do understand your 
concerns, and some users have reported that they can use their Canon 
printers with Linux.  You can check Linux user groups or sites on the 
Internet, or Linux distributions for any information available 
concerning Canon printers.

We hope this information is helpful to you.  Please feel free to contact
us again if you have any other questions or concerns regarding your 
PIXMA MP510.

Thank you for choosing Canon.

Sincerely,

James
Technical Support Representative

Special Note: Certain issues are very difficult to resolve via email.  
If your question remains unanswered after you have received this email, 
you may call our special toll-free number for email customers with 
unresolved issues and speak to a technician* by dialing 1-866-261-9362, 
Monday - Friday 10:00 a.m. - 10:00 p.m. (excluding holidays).

If you prefer to continue to communicate via email, reply to this 
message and we will respond as quickly as possible.

*Telephone support for products no longer covered under the 
manufacturer's warranty may require a $9.99 fee for support.



Original Message Follows:
-------------------------

SWSS Form Message
Product Type: PIXMA MP510
Product Model: 
mercury: 1450B002AB
category: 
description: 
SWSS-LENGTH: 3
SWSS-ConceptID0: 25873
SWSS-ConceptID1: 28297
SWSS-ConceptID2: 28301
SWSS-ConceptName0: 1450B002AA
SWSS-ConceptName1: What operating systems are compatible with my model?
SWSS-ConceptName2: Compatible operating systems - MP510
SWSS-TypeID0: 2
SWSS-TypeID1: 1
SWSS-TypeID2: 5
SWSS-SearchText: 
Product Serial Number: MP510
Date of Purchase: 11/??/2007
First Name: Josh
Last Name: Dye
Address: 1524 Frederick Street
City: Mount Shasta
State: CA
Zip: 96067
Phone Number: 530-926-5598
Email Address: [email]josh.jpenguin@gmail.com[/email]
EMAIL_ADDRESS_CONFIRM: [email]josh.jpenguin@gmail.com[/email]
q01: USB
q02: OS_X_v10.2_or_later
q03: Not_sure
INQUIRY: So, I am thinking about switching to linux.  So, I went to the 
cannon USA web site to see if there was an "official" linux driver said:**
> http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp510_support.aspx[/url]
So I want to know why you do not offer thiis in the USA.


---

### Post by stadt on 2008-04-20
Maybe you want to have a look on this blog [http://mp610.blogspot.com/](http://mp610.blogspot.com/)

Informations about open-source S.A.N.E scanner drivers and some tweaks (e.g borderless printing) for many Canon Multi-function printers (the printing tweaks can be applied on all Canon Bubble-Jet printers by editing the PPD)

---

### Post by 448191 on 2008-05-21
I'm new to using Linux as a desktop, so please forgive my ignorance.

When I try to convert the rpm using alien, it complains that it's not the right architecture (the rpm is i386, my system is i686).

How to fix?

---

### Post by stadt on 2008-05-22
Sorry 64-bit is not supported by the proprietary drivers.

You may give turboprint ([http://www.turboprint.de](http://www.turboprint.de)) a try

BTW. Linux Support for the Canon IP100 (successor to the IP90 portable printer) has been added by Canon. See [http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)

---

### Post by Nim-X on 2008-05-25
I have a Canon MP520 and it only prints empty pages! any suggestions?

scan and print works fine without the computer

---

### Post by stadt on 2008-05-25
> **Nim-X said:**
> I have a Canon MP520 and it only prints empty pages! any suggestions?

scan and print works fine without the computer

Have a look at this guide (it's for the MP510)
[http://ubuntuforums.org/showpost.php?p=3938403&postcount=4](http://ubuntuforums.org/showpost.php?p=3938403&postcount=4)

---

### Post by stadt on 2008-06-14
Canon supports now the Pixma IP2600 on Linux
See [http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)

---

### Post by Philip Farrugia on 2008-07-09
just purchased an ip3500.
downloaded the .deb package from canon's web site. but guess what? I need amd64 bit drivers.

Can anyone tell me how to install 32 bit debs on a 64 bit OS?

---

### Post by lubeck on 2008-08-15
DRIVERS for the CANON Pixma iP2600 are indeed located at:
[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/) ..... as "stadt" says. Terrific lead, thanks.
[B]
Couple Notes, FYI:[/B]
This install took about 5 minutes... easy for a noob like me.

In addition to the two .deb files (the drivers) at the site above (the drivers appear when you select the Injet, Pixma, iP2680 printer, Downloads), are the VERY USEFUL Linux install instructions (Ubuntu included) listed if you then select "Manuals":

"IJ Printer Driver Ver. 2.90 for Linux (Operation guide [Explanation of the iP2600series operation (html file)]"

With this wonderful documentation the installation went a bit easier... since there is one install step one must take before installing the .debs.

Noteworthy in these instructions, CANON recommends the following command at the Terminal before installing the .debs, to ready the system to "receive" them. I found this necessary and fundamental:

sudo aa-complain cupsd

Final Notes:
The install instructions include a step called "Register the Printer to the Spooler." A sample command is shown, so this is easy to do. However, part of the command needs two things that are peculiar to your computer after you install the .debs.
[printer_name]
[PPD_filename]
[device_URI]
Printer name and the URI may be easily found at System, Administration, Printing ... and your iP2600 PPD can be found using "locate *.ppd" at the command line.

If it helps, mine was located in /usr/share/ppd/canonip2600.ppd, and after the Registration command, in /etc/cups/ppd/canonip2600.ppd

Some applications need to be told the Printer "PPD" to allow them to understand how to talk to the iP2600, so you may want to save this location in a text file--for later recall or copy & paste.
Thanks to those who forged the path and helped me find the drivers.
Best wishes.

---

### Post by welshmike on 2008-08-29
> **lubeck said:**
> DRIVERS for the CANON Pixma iP2600 are indeed located at:
[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/) 

Hmm. Looks like the CANON PIXMA iP100 is the only driver I can find at [http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)

Any idea where I might now find the iP2600 one now?

---

### Post by welshmike on 2008-08-29
Uh??? It didn't yesterday but CANON website now shows driver available for IP2600 at 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)



WTF are CANON up to? Can't be pressure from MicroS..t to make it hard for Linux Ubuntu users can it?

Big deal. The driver does not get the printer to work

---

### Post by Teamgeist on 2008-09-03
> **welshmike said:**
> 

Big deal. The driver does not get the printer to work

Did you let Canon know it didn't work?
There are boxes to click on to let them know how it worked.
If they don't know the package doesn't work for your printer they won't be able to do anything about it.

---

### Post by jmjohn on 2009-06-17
Canon Pixma MP780 didn't work with the drivers listed on the site.  

However, this site [http://openprinting.org](http://openprinting.org) was useful.  MP780 is supported by Gutenprint.  Check it out, your printer may be there!

---

### Post by lefty_lou on 2009-09-01
is there a .deb for the pixma ip1000? can anyone help i'm running 9.04 pleaase help.!!

---

### Post by Philip Farrugia on 2009-11-04
Just checking old posts of mine.

Anyone browsing this might like to know I got my ip3500 working well now after reading somewhere that the MP520 has the same print mechanics so used the drivers for this instead.

---

