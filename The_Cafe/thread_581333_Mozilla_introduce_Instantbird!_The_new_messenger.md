---
title: "Mozilla introduce Instantbird! The new messenger"
date: 2007-10-19
forum: The Cafe
---

### Post by Kosimo on 2007-10-19
The fresh new messenger from the Mozilla foundation is out. A very early bugged 0.1 version. But just there:

Here's the link:
[URL="http://www.instantbird.org/"]
http://www.instantbird.org/[/URL]
If some body can make it work, just let us know.

---

### Post by Frak on 2007-10-19
If I can figure out the dependencies and successfully compile it, I'll create a debian package for it.

EDIT
Nevermind, they did the first two parts already, I'll just create the package.

---

### Post by bruce89 on 2007-10-19
Yay, now IM can take up 1GB of memory.

---

### Post by Frak on 2007-10-19
> **bruce89 said:**
> Yay, now IM can take up 1GB of memory.
lol, think the answer to cross platforming was XUL, except the fact that it is VERY resource intensive.

---

### Post by urukrama on 2007-10-19
What a bad name for a program!

---

### Post by Tom Mann on 2007-10-19
XUL has bloated quite - it should be called Chicken Tonight :)

---

### Post by bruce89 on 2007-10-19
In other news, Debian release Slowfish.

*In fact, I found Debian Testing to be very fast to boot.*

---

### Post by shad0w_walker on 2007-10-19
Regardless of the resource usage of the client, i love the look of the timeline, especially the after version 1.0 section

Video/Voice

The one biggest weak spot of Linux IM clients. I know there are clients that do it but I'm not aware of one that does all the major protocols with both video/voice support.

---

### Post by Stex on 2007-10-19
So what is it exactly? A jabber client? Seems a bit unnecessary really, should have made it closer integrated like chatzilla. But at least it's something that is actually planning for voice & video.

---

### Post by RAV TUX on 2007-10-19
> **Kosimo said:**
> The fresh new messenger from the Mozilla foundation is out. A very early bugged 0.1 version. But just there:

Here's the link:
[URL="http://www.instantbird.org/"]
http://www.instantbird.org/[/URL]
If some body can make it work, just let us know.Cool I'll have to give this one a try and see how it measures up to Kopete.

---

### Post by mikeypizano on 2007-10-19
I think I will stick to Pidgin... Looks interesting though.

---

### Post by fqueze on 2007-10-19
> **Frak said:**
> If I can figure out the dependencies and successfully compile it, I'll create a debian package for it.

EDIT
Nevermind, they did the first two parts already, I'll just create the package.

If you create a working .deb package, please keep us informed.
If you have trouble building instantbird on Ubuntu, I can assist you.

---

### Post by Kosimo on 2007-10-19
Hey, I would really appreciate if someone can build a working .deb for gutsy.  
Thank you in advance!

---

### Post by craig1709 on 2007-10-19
Is this really from Mozilla, or are they just using XULRunner? I don't want to get the wrong idea....

---

### Post by Kosimo on 2007-10-19
It works out of the box downloading the code and executing the .sh file

---

### Post by FredB on 2007-10-19
It is not a mozilla project. Just a xulrunner based one, like songbird.

---

### Post by corney91 on 2007-10-19
Thought I'd give it a go, but the script thing stops at:
```
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -r NSS_3_12_ALPHA_2 mozilla/dbm mozilla/security/nss mozilla/security/coreconf mozilla/security/dbm
Unknown host cvs-mirror.mozilla.org.

cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -A -l mozilla/ mozilla/db mozilla/js mozilla/js/jsd mozilla/js/src
Unknown host cvs-mirror.mozilla.org.
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -A mozilla/README mozilla/accessible mozilla/build mozilla/caps mozilla/chrome mozilla/config mozilla/content mozilla/db/mdb mozilla/db/mork mozilla/db/morkreader mozilla/db/sqlite3 mozilla/docshell mozilla/dom mozilla/editor mozilla/embedding mozilla/extensions mozilla/gfx mozilla/intl mozilla/ipc/ipcd mozilla/jpeg mozilla/js/jsd/idl mozilla/js/src/fdlibm mozilla/js/src/liveconnect mozilla/js/src/xpconnect mozilla/layout mozilla/modules/lcms mozilla/modules/libbz2 mozilla/modules/libimg mozilla/modules/libjar mozilla/modules/libmar mozilla/modules/libpr0n mozilla/modules/libpref mozilla/modules/libreg mozilla/modules/libutil mozilla/modules/oji mozilla/modules/plugin mozilla/modules/staticmod mozilla/modules/zlib mozilla/netwerk mozilla/other-licenses/atk-1.0 mozilla/other-licenses/ia2 mozilla/parser mozilla/plugin/oji mozilla/probes mozilla/profile mozilla/rdf mozilla/security/manager mozilla/storage mozilla/sun-java mozilla/testing/mochitest mozilla/toolkit mozilla/tools/elf-dynstr-gc mozilla/tools/test-harness mozilla/uriloader mozilla/view mozilla/webshell mozilla/widget mozilla/xpcom mozilla/xpfe mozilla/xpinstall mozilla/xulrunner
Unknown host cvs-mirror.mozilla.org.
checkout finish: Fri Oct 19 17:34:15 BST 2007
make[1]: Leaving directory `/home/dan'
can't find file to patch at input line 8
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: netwerk/base/public/nsPISocketTransportService.idl
|===================================================================
|RCS file: /cvsroot/mozilla/netwerk/base/public/nsPISocketTransportService.idl,v
|retrieving revision 1.1
|diff -u -r1.1 nsPISocketTransportService.idl
|--- netwerk/base/public/nsPISocketTransportService.idl 14 Apr 2005 23:18:34 -0000      1.1
|+++ netwerk/base/public/nsPISocketTransportService.idl 16 Sep 2007 16:02:54 -0000
--------------------------
File to patch:
```

Anyone know why?

---

### Post by Frak on 2007-10-19
> **corney91 said:**
> Thought I'd give it a go, but the script thing stops at:
```
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -r NSS_3_12_ALPHA_2 mozilla/dbm mozilla/security/nss mozilla/security/coreconf mozilla/security/dbm
Unknown host cvs-mirror.mozilla.org.

cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -A -l mozilla/ mozilla/db mozilla/js mozilla/js/jsd mozilla/js/src
Unknown host cvs-mirror.mozilla.org.
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -A mozilla/README mozilla/accessible mozilla/build mozilla/caps mozilla/chrome mozilla/config mozilla/content mozilla/db/mdb mozilla/db/mork mozilla/db/morkreader mozilla/db/sqlite3 mozilla/docshell mozilla/dom mozilla/editor mozilla/embedding mozilla/extensions mozilla/gfx mozilla/intl mozilla/ipc/ipcd mozilla/jpeg mozilla/js/jsd/idl mozilla/js/src/fdlibm mozilla/js/src/liveconnect mozilla/js/src/xpconnect mozilla/layout mozilla/modules/lcms mozilla/modules/libbz2 mozilla/modules/libimg mozilla/modules/libjar mozilla/modules/libmar mozilla/modules/libpr0n mozilla/modules/libpref mozilla/modules/libreg mozilla/modules/libutil mozilla/modules/oji mozilla/modules/plugin mozilla/modules/staticmod mozilla/modules/zlib mozilla/netwerk mozilla/other-licenses/atk-1.0 mozilla/other-licenses/ia2 mozilla/parser mozilla/plugin/oji mozilla/probes mozilla/profile mozilla/rdf mozilla/security/manager mozilla/storage mozilla/sun-java mozilla/testing/mochitest mozilla/toolkit mozilla/tools/elf-dynstr-gc mozilla/tools/test-harness mozilla/uriloader mozilla/view mozilla/webshell mozilla/widget mozilla/xpcom mozilla/xpfe mozilla/xpinstall mozilla/xulrunner
Unknown host cvs-mirror.mozilla.org.
checkout finish: Fri Oct 19 17:34:15 BST 2007
make[1]: Leaving directory `/home/dan'
can't find file to patch at input line 8
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: netwerk/base/public/nsPISocketTransportService.idl
|===================================================================
|RCS file: /cvsroot/mozilla/netwerk/base/public/nsPISocketTransportService.idl,v
|retrieving revision 1.1
|diff -u -r1.1 nsPISocketTransportService.idl
|--- netwerk/base/public/nsPISocketTransportService.idl 14 Apr 2005 23:18:34 -0000      1.1
|+++ netwerk/base/public/nsPISocketTransportService.idl 16 Sep 2007 16:02:54 -0000
--------------------------
File to patch:
```

Anyone know why?
It looks as if its looking for mozilla-core-source (or something) but can't find it.

---

### Post by fqueze on 2007-10-19
> **corney91 said:**
> Thought I'd give it a go, but the script thing stops at:
```
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot -q -z 3 co -P -r NSS_3_12_ALPHA_2 mozilla/dbm mozilla/security/nss mozilla/security/coreconf mozilla/security/dbm
Unknown host cvs-mirror.mozilla.org.

```

Anyone know why?

Your DNS resolution is broken.

---

### Post by mohnkern on 2007-10-19
Well, I downloaded it, and it ran out the box (despite being a resource hog), this is good.

But the minute I added a second IM account, it crashed, and when I restarted it, it crashed.  Removing ~/.instantbird resolve the issue, except I had to put in an account again.

Interesting idea, if they can resolve the resource issue, and the crashing issue, it'll be a good competitor for Pidgin.

I agree, audio and video are some things I miss, and  Skype is a bad alternative.

---

### Post by fqueze on 2007-10-19
> **mohnkern said:**
> 
But the minute I added a second IM account, it crashed, and when I restarted it, it crashed.  Removing ~/.instantbird resolve the issue, except I had to put in an account again.


On which protocols were the accounts? Do you have specific steps to reproduce the crash?

---

### Post by corney91 on 2007-10-19
Ah, a quick off and on of my router fixed it. My wireless has been acting up lately:(

---

### Post by Kosimo on 2007-10-19
Looking forward to the 0.2 so... :(

---

### Post by IYY on 2007-10-19
Seems like it uses Pidgin's libpurple library, so they won't be reinventing the wheel when it comes to backend. You could say that this is just a new frontend for pidgin.

There is the major advantage I can immediately think of: It might be possible to not only skin this program, but to easily **rearrange** the UI components. There are many Windows users who are very frustrated with the differences in layout between Pidgin and MSN (in fact, there is now a project called **emesene** set to fix just that). In this client, it would probably be possible to make skins that will make it look like MSN, Yahoo, AIM, Google Talk, or whatever.

Writing plugins might also be easier than with Pidgin, so we might see video and audio chat implemented at some point.

By the way, you don't have to compile this program. Just download and run the executable. It seems to be quite incomplete at this point though.

---

### Post by fuscia on 2007-10-19
the name's hilarious.

---

### Post by dart1007 on 2007-10-19
> **Tom Mann said:**
> XUL has bloated quite - it should be called Chicken Tonight :)

:lolflag::lolflag::lolflag::lolflag:

---

### Post by Polygon on 2007-10-19
interesting... i wish they would post screenshots on the homepage though.

---

### Post by Wiebelhaus on 2007-10-19
omg , I just had a mozilla fangasm.

---

### Post by bruce89 on 2007-10-19
I'm waiting for Empathy.

---

### Post by High Roller on 2007-10-20
> **bruce89 said:**
> I'm waiting for Empathy.

Telepathy just seems to be the way to go.  I can't wait for it to grow.  Mercury IM/Java eats the heck out of system resources.

---

### Post by Gargamella on 2007-10-20
I hope they will develope well msn network protocol (as amsn did) otherwise it is just an unuseful copy of pidgin (based on libpurple instead)

---

### Post by Kundalinux on 2007-11-14
What is this? There's at least 8 IMing programs out there for Linux, and none of them suits our needs. How many unhappy users are out there desperate for a good program? All we do is hope and expect that some of these programs develope well in the right direction. I think it's very frustrating! Having a community and having free software is great. But this is not working guys. Obviously we have a huge problem here.

---

### Post by Frak on 2007-11-14
> **Kundalinux said:**
> What is this? There's at least 8 IMing programs out there for Linux, and none of them suits our needs. How many unhappy users are out there desperate for a good program? All we do is hope and expect that some of these programs develope well in the right direction. I think it's very frustrating! Having a community and having free software is great. But this is not working guys. Obviously we have a huge problem here.
Pidgin is doing alot of users fine. Also, you just reminded me to package this ;)

---

### Post by Kundalinux on 2007-11-14
> **Frak said:**
> Pidgin is doing alot of users fine. Also, you just reminded me to package this ;)

Thanks Frak. I use Pidgin myself cause I find it to be the best choice. But I am far from being satisfied. It lacks some key features and gives me problems when I manage groups and contacts.

---

### Post by the yawner on 2007-11-14
I hope the name's just a development monicker. Ugh..

---

### Post by EmilyRose on 2007-11-20
I have to say, I am very fustrated with Ubuntu IM clients right now.. I bought a System 76 laptop, assuming (very wrongly, obviously), that I'd be able to video-chat with my family via pidgin or whatever (afterall, they video chat between iChat and AIM in windows, so why not linux, right??)... and its a total no-go. Pidgin is OK, and if it suported video I'd have zero problems... but without video, I'm left wondering what I was thinking not going for the Mac

---

### Post by screaminj3sus on 2007-11-20
> **EmilyRose said:**
> I have to say, I am very fustrated with Ubuntu IM clients right now.. I bought a System 76 laptop, assuming (very wrongly, obviously), that I'd be able to video-chat with my family via pidgin or whatever (afterall, they video chat between iChat and AIM in windows, so why not linux, right??)... and its a total no-go. Pidgin is OK, and if it suported video I'd have zero problems... but without video, I'm left wondering what I was thinking not going for the Mac

I really love pidgin, I use it on widnows too, but you are correct, it sorely lacks in the video/voice chat features (Which I don't use, but I can see how this frustrates people because there aren't really any good solutions for this in linux)

I have heard that Adium on Mac OSX is getting video/voice, and since that is based on pidgin and use pidgin's core could that mean someday it could be coming to pidgin?

---

### Post by epimer on 2007-11-21
> **EmilyRose said:**
> I have to say, I am very fustrated with Ubuntu IM clients right now.. I bought a System 76 laptop, assuming (very wrongly, obviously), that I'd be able to video-chat with my family via pidgin or whatever (afterall, they video chat between iChat and AIM in windows, so why not linux, right??)... and its a total no-go. Pidgin is OK, and if it suported video I'd have zero problems... but without video, I'm left wondering what I was thinking not going for the Mac

Kopete supports video chat (albeit a KDE program rather than a Gnome one), and the latest Skype beta also supports video stuff. Not the ideal solution, I know - I'd like to see video support in pidgin, too - but better than nothing.

---

### Post by EmilyRose on 2007-11-21
Kopete doesn't support video via AIM - only Yahoo and MSN. While better than Pidgens total lack of support, it still won't let me chat with my family who use iChat/AIM. Teaching/convincing them to download MSN or Yahoo!  is not the ideal.

---

### Post by bailout on 2007-11-21
> **EmilyRose said:**
> Kopete doesn't support video via AIM - only Yahoo and MSN. While better than Pidgens total lack of support, it still won't let me chat with my family who use iChat/AIM. Teaching/convincing them to download MSN or Yahoo!  is not the ideal.

Have you tried wengophone? I know it does AIM and video but not sure if it does video on AIM.

---

### Post by Sammi on 2007-11-21
The new Skype beta client for Linux has Video chat support: [http://www.skype.com/download/skype/linux/beta/](http://www.skype.com/download/skype/linux/beta/) :KS

---

### Post by EmilyRose on 2007-11-21
I have tried it... looking at their website, they don't even mention the possibility of AIM vidoe chat:( I just dont' get it... why is AIM video chat SO hard??

---

### Post by Frak on 2007-11-21
> **EmilyRose said:**
> I have tried it... looking at their website, they don't even mention the possibility of AIM vidoe chat:( I just dont' get it... why is AIM video chat SO hard??
It's a closed service, so developers can only **guess** on how it works.

---

### Post by init1 on 2007-11-21
> **bruce89 said:**
> In other news, Debian release Slowfish.

*In fact, I found Debian Testing to be very fast to boot.*
Yes, but testing is still a bit buggy. I might actually switch back to etch for now.

---

### Post by airtonix on 2008-01-02
LAWL....its just a xulrunnner frontend for libpurple....GAIM.


OMG so funny.

---

### Post by Kernel Sanders on 2008-01-02
From what I can tell, this isn't a mozilla project? :confused:

---

### Post by And1945 on 2010-02-18
Can I lure someone on 9.10 32bit to make a .deb file? :)

Otherwise,
I will await the Mozilla team to make it in future builds. Definately something i am looking forward to.

---

### Post by Nevon on 2010-02-18
This project seems kinda dead. The last version was released in March 2009, from what I can tell. 

Still, if it's just libpurple with a XUL frontend; it seems kind of pointless.

---

### Post by Ric_NYC on 2010-02-18
> **Nevon said:**
> This project **seems kinda dead**. The last version was released in March 2009, from what I can tell. 

Still, if it's just libpurple with a XUL frontend; it seems kind of pointless.


...just like this thread.

---

### Post by Sef on 2010-02-18
> Quote:
 	 	 		 			 				 					Originally Posted by **Nevon** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8845503#post8845503") 				
 				[I]This project **seems kinda dead**.  The last version was released in March 2009, from what I can tell. 

Still, if it's just libpurple with a XUL frontend; it seems kind of  pointless.[/I]
 			 		 	 	 

...just like this thread.


Locked for necromancing.

---

