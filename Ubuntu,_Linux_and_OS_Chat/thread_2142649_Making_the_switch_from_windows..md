---
title: "Making the switch from windows."
date: 2013-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by smOBudda on 2013-05-06
Good morning,

I decided this morning that I wanted to switch my laptop over from Windows 7 to Ubuntu. The biggest thing that has been holding me back is the fact I play PC games on my laptop as it is and noticed that 75% of the game titles and programs I use are not supported by Linux. I recently started an IT internship and find myself using Linux on the daily so I just wanted to upgrade my daily driver to run the platform I work with the most. With that said  my question being is there any way that I can get those programs I use most on my Windows platform to run on Ubuntu? Those programs being Photoshop, Ventrilo, and a handful of PC games that I play, Starcraft 2, Neverwinter... I would love to just make a full switch to Ubuntu but I'm not willing to do that unless I know for sure I'm able to use the programs I use most. Otherwise I may have to look into getting another laptop. Thanks for the advice ahead of time.

---

### Post by pfeiffep on 2013-05-06
Going out on a limb here without knowing more specifics about your machine. I don't think a 'cold turkey' solution is best for you!

I suggest a dual boot - ie install Ubuntu Along Side of Win 7. This will provide you the flexibility of fully testing all the games and software you require.

If your PC has the capability to boot USB - than installing Ubuntu to a USB hard drive is an option which will provide you quite a bit of flexibility

---

### Post by Cheesemill on 2013-05-06
It's possible to run *some* Windows applications on Linux using Wine. You can check if your applications will work or not by checking the [Wine application database]("http://appdb.winehq.org/"). Anything with a gold or platinum rating should be fine, if your applications have any other rating then don't bother as they won't work.

For applications that don't work in Wine you could also consider setting up a Windows VM. This has the advantage over Wine in that all of your applications will run, but you do need a Windows license to install your VM. Also 3D support in a VM is poor, you can't really use a VM for gaming.

I believe that Neverwinter has a native Linux client available. Also there are more and more games being released natively for Linux now that the Steam platform is available.

---

### Post by kaldor on 2013-05-06
This might not be helpful depending on who you use Ventrilo with, but I've found that Mumble (check Ubuntu Software Centre or their website) is by far the best VoIP client for gaming. Very little delay, crisp sound, and cross-platform. Ventrilo's website has shown the Linux client as "in development" for as long as I can remember.

Neverwinter Nights does have a Linux port available. However, I believe the install process is a bit messy. Starcraft II apparently works flawlessly under WINE.

---

### Post by smOBudda on 2013-05-06
Thanks for the information I did a little more digging and I think that I'm going to install as soon as I get home :]

---

### Post by gordintoronto on 2013-05-06
Dual Boot!

Use Windows to free up some space on your hard drive, install Ubuntu into that space. If you were to mention the brand and model of your laptop, you might get some specific pointers.

---

### Post by thiebaude on 2013-05-06
I would also say Dual-Boot.

---

### Post by lovebluesky2009 on 2013-05-06
you can both have windows and linux installed in your laptop

---

### Post by mastablasta on 2013-05-07
photoshop - use windows. Linux has opensource alternative that is very powerful called GIMP (has windows version as well). it comes close to Photoshop (especially with plugins installed), but is maybe not as powerful or easy.

some older versions of Photoshop work well in Wine though.

if what you mostly use are windows programmes and you are not ready to explore the alternatives then stay with Windows. you also won't be able to use Mac. since not all windows porgrammes have Mac version.

i used (and am using) mostly opensource programmes on windows. firefox for web browsing, thunderbird for email (been with them since they started), libre office for documents (though i also have MS office installed but that is about to change), IRC and IM clients, GIMP, Inkscape, wget, notepad++, bluefish, various system tools and many many more.

and the only thing keeping me there are games (and online banking). for everything else linux is just fine. so we use it on two mashcines and when i have time 3rd one will move to linux as well (in dual boot form). the main windows maschine will probably also get a dual boot.

---

### Post by rewyllys on 2013-05-07
[QUOTE=mastablasta;12637011] . . . . and the only thing keeping me there are games (and online banking). . . .

Why do you need Windows for online banking?  For several years I've done that with Linux alone.

---

### Post by BlinkinCat on 2013-05-07
> **rewyllys said:**
> Why do you need Windows for online banking?  For several years I've done that with Linux alone.

Me too - no problems whatsoever - :)

---

### Post by mastablasta on 2013-05-07
> **rewyllys said:**
> Why do you need Windows for online banking? For several years I've done that with Linux alone.


come live here and try to repeat that sentence :-)


online banking works for normal conumers. digital certificate+firefox, Chrome or Opera.

but for companies a special USB stick with chip inside is needed and they only make windows drivers for that chip. some banks work with special card readers. usally they too need windows to run.

there is a bank that supports all OS. there are two issues with them though - 1. they do not have an office in my town. 2. would have to pay extra comission when getting money on ATM sicne they have only few ATMs. 3. their solution revolves arround using Oracle Java which is a very safe platform i believe....

---

### Post by Sprinkman on 2013-05-07
I need to look into dual boot.  Is there any way that I can toggle back and forth between windows 7 and Ubuntu?  I have Ubuntu installed on a second HD and sometimes I need to go to Win7 to do business things through Web. I play CS and need to run Source.  I'm a little worried about my graphics not running clean too.  I don't want to have to shut down windows to start Ubuntu. What do I need to do?

---

### Post by thiebaude on 2013-05-07
You will have to log out and then choose which OS at startup.

---

### Post by SeijiSensei on 2013-05-07
Unless your computer is starved for memory, I suggest you try installing [VirtualBox]("http://www.virtualbox.org/") on your Windows machine, then install Ubuntu into a "virtual machine."  This avoids the need for dual-booting.  In fact, many computers these days come with all four primary hard drive partitions in use which makes formatting a machine for dual-boot a daunting task.

Make sure you install the "extensions pack" as well.

With a VM, you can switch between operating systems just by a mouse click or Alt-Tab.

---

### Post by cindrella on 2013-05-08
we can install both operating system in our system is it posssible or not? incase is it possible howcan we install

---

### Post by Erik1984 on 2013-05-08
> **cindrella said:**
> we can install both operating system in our system is it posssible or not? incase is it possible howcan we install

Perfectly possible (a little trickier maybe if you have a machine pre-installed with Windows8). But I suggest you start a thread in the Installation subforum if you have a technical question about dual booting Windows and Ubuntu.

---

### Post by Sprinkman on 2013-05-08
> **SeijiSensei said:**
> Unless your computer is starved for memory, I suggest you try installing [VirtualBox]("http://www.virtualbox.org/") on your Windows machine, then install Ubuntu into a "virtual machine."  This avoids the need for dual-booting.  In fact, many computers these days come with all four primary hard drive partitions in use which makes formatting a machine for dual-boot a daunting task.

Make sure you install the "extensions pack" as well.

With a VM, you can switch between operating systems just by a mouse click or Alt-Tab.

I am currentlt running 8gigs, 6 core and 2 hard drives = 1T and 500MB. I have ubuntu installed on the 500MB drive.

---

### Post by rewyllys on 2013-05-09
> **mastablasta said:**
> come live here and try to repeat that sentence :-) . . . . but for companies a special USB stick with chip inside is needed and they only make windows drivers for that chip. . . . 
Too bad about your banking situation.  You have my sympathy.

I understand only too well, because I keep Windows XP running in VirtualBox on my desktop, almost solely because there is no Linux personal computer software for doing US income-tax returns (and because I refuse to prepare my return "in the cloud").:(

P.S.  OTOH, if my impression that you live in Colorado is correct, then I'd gladly trade locales with you, especially in summertime.

---

### Post by craig10x on 2013-05-09
@rewylls: actually the online versions of the tax programs (like Tax Act which is the one i use and absolutely love) are VERY SECURE and encypted also...read the information on their link regarding security:
[http://www.taxact.com/security-center.asp](http://www.taxact.com/security-center.asp)

So, you shouldn't be so afraid about using it...and it would give you the opportunity to finally free yourself of that "windows noose" :)
Been using them (first Turbo Tax and in recent years switched to Tax Act) for years and never been compromised in any way...

---

### Post by Sam Mills on 2013-05-09
> **rewyllys said:**
> I keep Windows XP running in VirtualBox on my desktop, almost solely because there is no Linux personal computer software for doing US income-tax returns (and because I refuse to prepare my return "in the cloud").:(


In effect, there really is no difference whether you use "the cloud" or do it on your computer first. Either way, the information gets sent online and they wind up with all of your info. It's 6 of one way, or a half dozen another way. Doing it in a web browser eliminates the need to download any programs. And craig is right, it is *very* secure nowadays.

---

### Post by mastablasta on 2013-05-10
> **rewyllys said:**
> Too bad about your banking situation. You have my sympathy.

I understand only too well, because I keep Windows XP running in VirtualBox on my desktop, almost solely because there is no Linux personal computer software for doing US income-tax returns (and because I refuse to prepare my return "in the cloud").:(

P.S. OTOH, if my impression that you live in Colorado is correct, then I'd gladly trade locales with you, especially in summertime.

Well the tax report is handled by government here. we only need to report any extra income. we can do it via papers or online. and the online is signed with certificate and works well in Firefox. similar for businesses. thoguh for some reason my accountant can get it uploaded only in IE. and even then it didn't work for my account. so i did it myself later in Firefox. the bonus of giving in tax online for businesses is a much lower tax fee. while for normal people if they do it online it is free of charge. while in paper it's a small feel. maybe 1 EUR or something like that.

I am in EU. we might be the next country to go under (though i still hope this won't happen) so it's not a good time to move here. although appart from economy situation the place is nice to live at all times of year. small enough you can ski on mountain slopes and enjoy a coctail on the beach within a few hours appart. aslo everyone from my customers that comes here the firts time says "it's so green here, the air is so fresh and everything is so clean". it's funny, cause everyone says it. maybe they expect gray industrial soviet like towns... i guess then it is probably true.
anyway nice place to live only economy situation is not good at the moment. and a lot bigger problems than business bank acocunts not supporting linux (consumer accounts work well).

---

### Post by mreq on 2013-05-10
+1 for running Ubuntu in Virtualbox. If you don't need to switch often, go with dual boot. I dumped gaming for pure Ubuntu ;) If you'd be willing to dump gaming as well, internet banking & Photoshop could be done in Virtualbox running Windows...

---

### Post by rewyllys on 2013-05-10
> **mastablasta said:**
> . . . . the place is nice to live at all times of year. small enough you can ski on mountain slopes and enjoy a coctail on the beach within a few hours appart. aslo everyone from my customers that comes here the firts time says "it's so green here, the air is so fresh and everything is so clean". it's funny, cause everyone says it. maybe they expect gray industrial soviet like towns. . . . 
Because your comment arouses an especially nice memory of mine, I can't resist going off topic to hazard a guess that you live in the Piedmont, perhaps in Turin.

The memory I mentioned is of 1965 January 1.  My family, with 4 then-young children, celebrated the New Year by going up into the mountains northeast of Los Angeles, where the children played in the snow, and then down to the beach in Santa Monica, where we all swam in the surf.  It was a lovely day!:)

---

### Post by aykoola on 2013-05-11
Or maybe Slovenia?

---

### Post by mastablasta on 2013-05-12
> **aykoola said:**
> Or maybe Slovenia?

That's the one.

---

### Post by aykoola on 2013-05-12
V tem primeru - pozdravljen! :)

---

### Post by entangled on 2013-05-13
Another +1 to run linux in virtualbox.

I've tried dual-boot on my iMac using both grub and efi. It mostly works but I have several issues:
1. no resume after suspend - means no suspend, so running at full power continuously. A KMS (kernel) issue on iMac I think.
2. Uses 15w more than OSX, i.e. 20% higher power drain.
3. My video card (AMD Radeon 4670) is no longer supported by AMD, and open-source ati driver fails - using last-ditch 'fbdev' driver.

In virtualbox I have several advantages:
1. nearly the same video performance, 
2. no driver problems
3. ability to exactly freeze what I'm doing and return to it later
4. ability to cut and paste with OSX
5. included in OSX backups.  

Linux is great until you get to the desktop. In my experience, linux' achilles heel is buggy and deficient video drivers. There are many cards with so many quirks that only the manufacturer is likely to program them well, and most manufacturers seem to ignore linux.

---

