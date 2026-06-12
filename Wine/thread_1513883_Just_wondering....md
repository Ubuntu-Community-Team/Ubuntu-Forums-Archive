---
title: "Just wondering..."
date: 2010-06-20
forum: Wine
---

### Post by Zerocool Djx on 2010-06-20
Since many of us use dual boot,.. is there any programs like wine that can just use the win files we already have in windows partitions to run under Ubuntu? I mean, I know what wine is traditionally trying to do. But,.. if we already have a dual boot could I not take advantage of files I already have Vs fighting installing with wine?

---

### Post by mickie.kext on 2010-06-20
Wine can do it. Just find .exe file, right click, and select run with Wine.

---

### Post by Zerocool Djx on 2010-06-20
in the windows partition itself? I just read here:

*BTW - Wine shouldn't have affected your existing Windows install at all,  unless you made the colossal mistake of trying to use it to run  applications that are installed on your Windows partition, instead of  installing them in Linux with Wine as you are supposed to do.*

On another forum,.. is there any truth to this?

Also,.. what version of windows is wine trying to imitate? I got XP on my system on a dual boot and if I have to do an over kill and make a third partition to link wine to a 3rd partition of windows to make it work and not affect my real version of windows I will do that until I know it works correctly. Then I'll just use 2 partitions after I get it running.. I mean.. If I have the actual files to make a program work already,.. why wine just don't link to it makes me think...

---

### Post by ronnielsen1 on 2010-06-20
> Also,.. what version of windows is wine trying to imitate?

There's 14 different versions that you can choose in winecfg

---

### Post by Zerocool Djx on 2010-06-20
> **ronnielsen1 said:**
> There's 14 different versions that you can choose in winecfg

Good to know,.. What is it set by default?

---

### Post by ronnielsen1 on 2010-06-20
I believe it's xp

---

### Post by Zerocool Djx on 2010-06-20
Groovy,.. so any truth to wine messing up my windows partition is I open exe files in the windows partition  with wine?

---

### Post by hikaricore on 2010-06-20
> **Zerocool Djx said:**
> Groovy,.. so any truth to wine messing up my windows partition is I open exe files in the windows partition  with wine?

Depending on what you tried to run and how you did it yea there's plenty of truth to it.

---

### Post by Zerocool Djx on 2010-06-20
> **mickie.kext said:**
> Wine can do it. Just find .exe file, right click, and select run with Wine.


-1 point for you then!

---

### Post by Zerocool Djx on 2010-06-20
ok,.. so does it still run tho? Like does it damage the files? Cause if I can make a third partition of windows for wine and it works consistently, I'll do it... Anything to make it work. If it just changes address for files perminantly who cares then.. I'll just load it in the 3rd partition.

---

### Post by ronnielsen1 on 2010-06-20
> Cause if I can make a third partition of windows for wine and it works  consistently, I'll do it... 

You don't need to do this. They were just saying it was possible. Best way is to google the app in question and see if someone has had luck running it.

When I googled [COLOR=DarkRed]**winehq ms office 2007**[/COLOR] one of the results got me to this page.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

If you scroll down it will tell you certain overrides you may need to do in winecfg like

> [SIZE=2]Once installed, the following tweaks may be needed:                                                                                                       
[/SIZE]
   
[LIST]
[*][SIZE=2]**riched20:** Set riched20 to  'native' in winecfg. DO NOT INSTALL IT YOURSELF. Office 2007 comes with  its own version of riched20. Without using it, Powerpoint will not  launch, and some dialog boxes will not display properly. Do not set this  override globally unless Office is installed in a separate wineprefix.                                             
[/SIZE]
[*][SIZE=2]**Windows Scripting Host (jscript):**     Needed for the thesaurus; install it with winetricks wsh56js. [/SIZE]
[*][SIZE=2]**wingdings.ttf: **Most of the  default bullet characters are from this font; if it is not installed on  your system, Wine will substitute characters from a font that is  installed on your system.                                                                                 
[/SIZE]
[*][SIZE=2]**symbol.ttf: **For versions of Wine  prior to 1.1.16, this font must be installed for equations to display  properly[/SIZE]
[*][SIZE=2]**usp10:** Set usp10 to  'native,builtin' in winecfg for the equation toolbar in Word. There is  no need to install it; simply set the override. Do not set this override  globally unless Office is installed in a separate wineprefix.                                             [/SIZE]
[/LIST]


Easy after you figure it out


>  					Originally Posted by **Zerocool Djx** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9486477#post9486477") 				
 				*Groovy,.. so any truth to wine  messing up my windows partition is I open exe files in the windows  partition  with wine?*
 			 		 	 	 Depending on what you tried to run and how you did it yea there's  plenty of truth to it. 	

I'm not so sure I agree with that. The paths would be different. You could hose wine and have to reinstall wine but if I'm linking to an existing windows installation, the path would most likely be something like[COLOR=RoyalBlue] [COLOR=Blue]/media/6b466854-7496-464b-83d5-1e5456ad6028[/COLOR][/COLOR] or [COLOR=Blue]/media/sda1[/COLOR]. I don't think many viruses would implant themselves in /media

> A virus named after SCO that was designed to DoS attack SCO should  definitely be Linux compatible, right?  The SCO virus (at least  according to ClamAV) is actually just a variant on the MyDoom worm, but  unlike MyDoom I was able to unzip this on Linux.    
  Not only does it run, but it actually dumped its payload at  ~/.wine/fake_windows/Windows/System/shimgapi.dll!  Unfortunately, that's  all it did before it terminated.  I mean, if it had kept on running, I *might*  have been sufficiently tempted to set my system clock to February 3,  2004, in order to get in on the DoS fun!  It must require Windows to  bone-headedly execute its payload.  I'll give it 3/5 penguins for  actually doing something.  Plus, whoever modified MyDoom like this  actually seemed to put some thought into making it more  Linux-compatible.  That's what I call progress.




[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

I think any viruses or malware would go to /home/user/.wine

---

### Post by ajgreeny on 2010-06-20
In the days when I had Windows XP Home SP2 on my computer, i did run a few applications direct from the windows partition and not install them in Ubuntu.  The two I can specifically remember were **Mailwasher Free**, and **IrfanView**.  Doing that did not affect the windows partition in any way I could see, and both apps continued to work as expected in the windows OS, and were not harmed in any way.

There were a lot of apps that I tried to run that way, but most would not do so at all and just refused to do anything at all.

I hasten to add that I did this just as an experiment, rather than as the best way to use the applications, and to be honest, I quickly realised that I did not need Windows at all, so I deleted that partition and now always use native linux applications for everything;  Windows is now history for me and I do not miss anything about it!

---

### Post by ucal on 2010-06-20
I don't think WINE is designed to do that.  It might be easier to set up a virtual box on your windows partition so it runs it like windows ran when it left off, just in Ubuntu.  Though I don't know if that's possible.

---

### Post by Zerocool Djx on 2010-06-20
> **ucal said:**
> I don't think WINE is designed to do that.  It might be easier to set up a virtual box on your windows partition so it runs it like windows ran when it left off, just in Ubuntu.  Though I don't know if that's possible.

 can't internet connectivity issues. not to mention it lags..

---

### Post by The Real Dave on 2010-06-21
Sorry mate, I posted this in your last thread. Here it is here again :)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For me, DreamWeaver 8 works perfectly in Wine (1.2-rc4). According to their [site]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14343"), quite a few people have had success with CS4 in Wine also.

I suggest that you get the latest version of Wine from their site, and try to install DreamWeaver. Don't assume that something won't work without trying it. Hell, I got most of Office 2007 to work by default.

[[img]http://linuxexpresso.files.wordpress.com/2010/06/dreamweaver8.png?w=200h=200[/img]]("http://linuxexpresso.files.wordpress.com/2010/06/dreamweaver8.png")

[[img]http://linuxexpresso.files.wordpress.com/2010/02/office_2007_28-feb-2010.png?w=200h=200[/img]]("http://linuxexpresso.files.wordpress.com/2010/02/office_2007_28-feb-2010.png")

---

### Post by Zerocool Djx on 2010-06-21
I think I finally understand the need for the reoccurring discussions thread.

---

