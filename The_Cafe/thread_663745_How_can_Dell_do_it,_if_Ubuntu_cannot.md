---
title: "How can Dell do it, if Ubuntu cannot?"
date: 2008-01-10
forum: The Cafe
---

### Post by brucewagner on 2008-01-10
Dell includes the DVD playback stuff now... in their pre-installed image of Ubuntu.   Did you know that?  (see [http://www.markshuttleworth.com/archives/133](http://www.markshuttleworth.com/archives/133) )

Can someone please explain to me HOW Dell can get away with selling a pre-installed image of Ubuntu complete with the DVD playback code, within the USA, and Ubuntu (Canonical) can not provide it in the standard Ubuntu download (even if they have to have a separate splash-screen “agreement”/”acknowledgment”)…?

How can Dell do it legally, if Ubuntu itself cannot do it legally — within the US?

Why doesn't Ubuntu simply include -- at least a slick little utility for installing all that proprietary stuff that every user needs -- like the one called QuickStart (see [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) )

---

### Post by maybeway36 on 2008-01-10
1. DVD-playing software requres a license to use in the US. This usually comes with a computer purchase.
2. Dell pays for a license to ditribute the DVD-playing software LinDVD.
3. Ubuntu is free of charge.

Also (beware, legalese):
4. The way better libdvdcss2 DVD-playing software is under the GPL, which says you can't buy a license for it unless you buy a license for all users of the software, including people **not** going through your company. However, it can't be distributed in the US witout a license. Hence, Dell must use LinDVD.

---

### Post by brucewagner on 2008-01-10
> **maybeway36 said:**
> The way better libdvdcss2 DVD-playing software is under the GPL, which says you can't buy a license for it unless you buy a license for all users of the software, including people **not** going through your company. However, it can't be distributed in the US witout a license. Hence, Dell must use LinDVD.

This part is very confusing.  It sounds to me like it's a legal catch-22...?

So...  What about this....

Why doesn't the Ubuntu standard download at least include an install script which would automatically install libdvdcss2 (along with all the other appropriate stuff, which is not there -- and needs to be there -- like flashplayer, dixv codecs, java aplet code, etc, etc)... only AFTER the splash-screen warning where you state that you are NOT in the usa....?

Wouldn't that be legal?

---

### Post by mrgnash on 2008-01-10
Who cares? It takes like 2 minutes to get all that stuff up and running after a fresh install. And if that's too much trouble you can always install Linux Mint instead.

---

### Post by BDNiner on 2008-01-10
Legally i don't think they can provide a script, since providing a way for someone to break the law is also against the law. But since they sell you the computer the price of the license is also included in the price of the computer. That is why there is not too much of a price difference between an ubuntu Dell and a windows Dell.

---

### Post by KiwiNZ on 2008-01-10
> **brucewagner said:**
> Dell includes the DVD playback stuff now... in their pre-installed image of Ubuntu.   Did you know that?  (see [http://www.markshuttleworth.com/archives/133](http://www.markshuttleworth.com/archives/133) )

Can someone please explain to me HOW Dell can get away with selling a pre-installed image of Ubuntu complete with the DVD playback code, within the USA, and Ubuntu (Canonical) can not provide it in the standard Ubuntu download (even if they have to have a separate splash-screen “agreement”/”acknowledgment”)…?

How can Dell do it legally, if Ubuntu itself cannot do it legally — within the US?

Why doesn't Ubuntu simply include -- at least a slick little utility for installing all that proprietary stuff that every user needs -- like the one called QuickStart (see [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) )

Post #2 gave the right answer.

If you need to add DVD playback ( not all users require it) its dead easy to add post install.

---

### Post by GavinZac on 2008-01-10
people still watch DVDs?

---

### Post by iPower on 2008-01-10
> **GavinZac said:**
> people still watch DVDs?

i rent dvds for a few cents per dvd

---

### Post by brucewagner on 2008-01-10
> **KiwiNZ said:**
> Post #2 gave the right answer.

If you need to add DVD playback ( not all users require it) its dead easy to add post install.

> **mrgnash said:**
> Who cares? It takes like 2 minutes to get all that stuff up and running after a fresh install. And if that's too much trouble you can always install Linux Mint instead.

You guys...  I'm a brand new day one user.   And I don't know how to do it. (seriously)

Besides....  I think there are a LOT of us "brand new day one" users out there.

Part of the whole concept of Ubuntu is to make it simple and easy for anyone... no?

There has to be a way to automate the installation of that stuff... and still conform to the legalities. 

If apt-get can install it...  Then apt-get is "a script providing a way for someone to break the law".

It can get to the point of being ridiculous.   And remember, it's NOT always against the law --- in the country the user may be living in.

---

### Post by GavinZac on 2008-01-10
Simple, easy, and **free**. Anyway, isn't there already the codec wizard which is like a dumbed down version of synaptic?

---

### Post by perce on 2008-01-10
Forgive me if this is off topic: does Windows come with DVD support out of the box? Last time I used it, it was Win98 in 2001, and I had to install a 3rd party software.

---

### Post by GavinZac on 2008-01-10
> **perce said:**
> Forgive me if this is off topic: does Windows come with DVD support out of the box? Last time I used it, it was Win98 in 2001, and I had to install a 3rd party software.

In XP I had to use the driver/codec/player cd I got with the drive.

---

### Post by perce on 2008-01-10
> **GavinZac said:**
> In XP I had to use the driver/codec/player cd I got with the drive.

So, if you have to install extra software in Windows, and you have to install extra software in Linux, why so much fuzz about Linux not playing DVD's out of the box?

---

### Post by saulgoode on 2008-01-10
> **brucewagner said:**
> There has to be a way to automate the installation of that stuff... and still conform to the legalities. 

If apt-get can install it...  Then apt-get is "a script providing a way for someone to break the law".

It can get to the point of being ridiculous.   And remember, it's NOT always against the law --- in the country the user may be living in.

It is not just (or sometimes *even*) a matter of "conforming to the legalities". Ubuntu has firmly expressed a philosophy of promoting Free Software. People volunteer to contribute to Ubuntu because of this philosophy and with the agreement to support this philosophy.

Changing the philosophy of Ubuntu so that it might now promote proprietary solutions would not only be a slap in the face to those who have contributed under the previous agreement, it would lead to withdrawal of their further contribution and reduce the hope of attracting other Free thinkers (not to mention that receiving donations of money and services under false pretenses falls under the category of "fraud", which is a crime).

---

### Post by justsomedude on 2008-01-10
> **perce said:**
> Forgive me if this is off topic: does Windows come with DVD support out of the box? Last time I used it, it was Win98 in 2001, and I had to install a 3rd party software.

I bought a new Laptop 4 month ago, that came with Vista Home Basic pre-installed. Vista Home Basic does not play DVDs out of the box, however the OEM included some third party software (WinDVD or something, can't remember) that had to be installed...

---

### Post by Methuselah on 2008-01-10
> 
So, if you have to install extra software in Windows, and you have to install extra software in Linux, why so much fuzz about Linux not playing DVD's out of the box?


I also wonder about this too when people complain about flash not being there. Even on windows you have to go out it the web and download adobe's program.

Last time I checked microsoft was not helping to proliferate flash and they certinaly won't be doing so in the future with their own competing silverlight in the works.

---

### Post by forrestcupp on 2008-01-10
> **brucewagner said:**
> 
There has to be a way to automate the installation of that stuff... and still conform to the legalities. 

If apt-get can install it...  Then apt-get is "a script providing a way for someone to break the law".

you have the wrong idea of what apt-get is.  What you said is like saying that Microsoft is liable for piracy because pirated software uses Windows installer.

If you want *everything* to just work without any effort at all, then Ubuntu or any Linux is not for you.  You need a Mac.  But there are plenty of resources available that will teach you how to set up your computer the way you need it.

And like others said, Linux Mint is a variant of Ubuntu that automatically installs with all of this support.  And I think they have a version without all of that for people who live in the US, so it's up to the user to decide if they want to break the law or not.  But I'd say Ubuntu is doing a good job at playing it safe.  In case of a legal battle, Ubuntu will not be shut down over something like that.

> **perce said:**
> Forgive me if this is off topic: does Windows come with DVD support out of the box? Last time I used it, it was Win98 in 2001, and I had to install a 3rd party software.
XP Media Center Edition and everything Vista Home Premium and above supports DVD playback OOTB.  But I agree with your point.

---

### Post by maybeway36 on 2008-01-10
If you were wondering about the GPL / libdvdcss2 thing I rambled about, it was my interpertation of this:
> you must either
(1) cause the Corresponding Source to be so available, or
(2) arrange to deprive yourself of the benefit of the patent license for this particular work, or
(3) arrange, in a manner consistent with the requirements of this License, to extend the patent license to downstream recipients.
Maybe I was wrong ,though. Licensing is confusing...

---

### Post by GavinZac on 2008-01-10
> **forrestcupp said:**
> XP Media Center Edition and everything Vista Home Premium and above supports DVD playback OOTB.  But I agree with your point.
They come with DVD playback pre-installed for their Media Players (in this case, media center). The same as Dell's pre-installation of DVD in their's, you are paying for it.

---

### Post by macogw on 2008-01-10
> **maybeway36 said:**
> 
Also (beware, legalese):
4. The way better libdvdcss2 DVD-playing software is under the GPL, which says you can't buy a license for it unless you buy a license for all users of the software, including people **not** going through your company. However, it can't be distributed in the US witout a license. Hence, Dell must use LinDVD.
HUH???  Why would you need to *buy* a license to distribute GPL'd software?  One major point of the GPL is allowing redistribution.

---

### Post by macogw on 2008-01-10
> **forrestcupp said:**
> 
If you want *everything* to just work without any effort at all, then Ubuntu or any Linux is not for you.  You need a Mac.

Funny you say that...I couldn't stand using a Mac until I installed Fink (apt), Virtue Desktops (as close as they get to mimicking Compiz's functionality), and Quicksilver (alt+f2 runbox).

---

### Post by perce on 2008-01-10
> **macogw said:**
> HUH???  Why would you need to *buy* a license to distribute GPL'd software?  One major point of the GPL is allowing redistribution.

Because the algorithm it implements is patented, so in countries which enforce software patents you have to license the patent I guess.

---

### Post by macogw on 2008-01-10
> **perce said:**
> Because the algorithm it implements is patented, so in countries which enforce software patents you have to license the patent I guess.

I thought libdvdcss2 didn't use the actual CSS algorithm and instead brute-forces it.  That's what Wikipedia says, anyway.  The trouble with the US, specifically (and not other countries where they enforce software patents) is that there's the DMCA which basically says it's illegal to break encryption.

---

### Post by jrusso2 on 2008-01-10
> **perce said:**
> Forgive me if this is off topic: does Windows come with DVD support out of the box? Last time I used it, it was Win98 in 2001, and I had to install a 3rd party software.

Vista does.

---

### Post by jrusso2 on 2008-01-10
What Ubuntu could do is buy a license like Dell did and charge those that wanted it to cover the cost.

---

### Post by BLTicklemonster on 2008-01-10
> **maybeway36 said:**
> 1. DVD-playing software requres a license to use in the US. This usually comes with a computer purchase.


But I bought my computer, shouldn't I be licensed to use dvd playback regardless of the operating system?

---

### Post by perce on 2008-01-10
> **macogw said:**
> I thought libdvdcss2 didn't use the actual CSS algorithm and instead brute-forces it.  That's what Wikipedia says, anyway. 

You're right, patents are a problem with other codecs, like MP3.

> **jrusso2 said:**
> What Ubuntu could do is buy a license like Dell did and charge those that wanted it to cover the cost.

Not a good move in my opinion. First, we should oppose rather that 
endorse policies which tend to deprive users of their freedom. 

Second, who would by that license? I wouldn't. We are not even sure if the libdvdcss actually brake DCMA; I was reading a discussion about the issue on the Debian legal mailing list a few years ago, but it was too technical and I didn't get the point. Also, with thousands of kids downloading hundreds of copyrighted movies on Windows, I don't see who would go after a few Linux users watching legally purchased DVD's.
  
Third, it will probably brake the GPL: if you distribute GPL software, you must pass the right to distribute too. If you can't pass that right because the user would need to buy an extra licence from someone else, you can't distribute the software.

---

### Post by saulgoode on 2008-01-10
> **jrusso2 said:**
> What Ubuntu could do is buy a license like Dell did and charge those that wanted it to cover the cost.

The problem with this is that the only licensed source of Ubuntu would be Ubuntu. You, the user, could no longer use multiple copies, nor could you give a copy to your friends. User groups would no longer to be able to hand out free copies and even bittorrents or mirror downloads would be forbidden. In short, Ubuntu would no longer be Free.

---

### Post by jrusso2 on 2008-01-11
> **saulgoode said:**
> The problem with this is that the only licensed source of Ubuntu would be Ubuntu. You, the user, could no longer use multiple copies, nor could you give a copy to your friends. User groups would no longer to be able to hand out free copies and even bittorrents or mirror downloads would be forbidden. In short, Ubuntu would no longer be Free.

You would buy it as a download.  It would not be on the cd.  I am not the one in here every day complaning that codecs and dvd are illegal but a lot of others are.

This would provide a legal way for those who are trouble by it.

I just use libdvdcss2

---

### Post by jrusso2 on 2008-01-11
> **perce said:**
> You're right, patents are a problem with other codecs, like MP3.



Not a good move in my opinion. First, we should oppose rather that 
endorse policies which tend to deprive users of their freedom. 
 .

Are you not depriving Linux users of watching DVD's by that approach?

This is really what keeps Linux from being a major player on desktop,
Its this all software must be free holy approach.

All software is never going to be free. Its a billion dollar business.

The sooner Linux realizes this and works with both commercial and Free Software the sooner Linux will be usable and popular by regular users.

---

### Post by perce on 2008-01-11
> **jrusso2 said:**
> Are you not depriving Linux users of watching DVD's by that approach?


I'm not, those claiming that libdvdcss are illegal do.

>  
This is really what keeps Linux from being a major player on desktop,
Its this all software must be free holy approach.


What keeps Linux from being a major player on desktop is the lack of support from manifacturers: 90% of users don't install operating systems

> 
All software is never going to be free. Its a billion dollar business.


I don't want all software to be free. I don't have any problem with Acrobat reader not being free for example, I don't see it as a threat to my rights. On the contrary, DRM like technologies are a threat to my fair use rights.

> 
The sooner Linux realizes this and works with both commercial and Free Software the sooner Linux will be usable and popular by regular users.

It's not an OS that works with software, but software which work with the OS. This said, commercial software works with Linux, it's just that not much of it is developed.

---

### Post by brucewagner on 2008-01-13
> **GavinZac said:**
> Simple, easy, and **free**. Anyway, isn't there already the codec wizard which is like a dumbed down version of synaptic?

Where?

---

### Post by macogw on 2008-01-13
> **brucewagner said:**
> Where?

Try to play a file and it'll open an Add/Remove window already limited to whatever files you need to run the file.  I just saw it the other day when I tried to play a midi file.

---

### Post by brucewagner on 2008-01-15
> **macogw said:**
> Try to play a file and it'll open an Add/Remove window already limited to whatever files you need to run the file.  I just saw it the other day when I tried to play a midi file.

Yes, I know.

Unfortunately, it does not work.

Apparently, it does not install the correct code.

No matter which option you select, it does not work.

I have reinstalled Ubuntu 4 times, and tried each one.  They do not work.

---

### Post by bufsabre666 on 2008-01-15
install ubuntu restriced extras under the other tab

thats where the codecs you need lie

---

### Post by brucewagner on 2008-01-15
> **bufsabre666 said:**
> install ubuntu restriced extras under the other tab

thats where the codecs you need lie

"Under the Other tab"  ?

What are you talking about?

---

### Post by tom66 on 2008-01-15
Apparently, according to Wikipedia, libdvdcss does not break the DMCA:

> libdvdcss is not to be confused with DeCSS. While DeCSS uses a cracked DVD player key to perform authentication, libdvdcss uses a generated list of possible player keys. If none of them work (for instance, when the DVD drive enforces region coding) a brute force algorithm is tried so the region code of a DVD is ignored. Unlike DeCSS, libdvdcss has never been fought over in a courtroom, in part because Section 1201(f) of the Digital Millennium Copyright Act authorizes such circumvention for purposes of software interoperability.

---

### Post by bufsabre666 on 2008-01-15
> **brucewagner said:**
> "Under the Other tab"  ?

What are you talking about?

theres a tab labeled other or misc or something ((im on windows at school i cant exactly check it)) just do a search in the add/remove programs for ubuntu restricted

---

### Post by mali2297 on 2008-01-15
> **brucewagner said:**
> "Under the Other tab"  ?

What are you talking about?

See this [doc]("https://help.ubuntu.com/community/RestrictedFormats").
> 
* Go to Applications &#8594; Add/Remove...
* Set Show: to All available applications
* Search for ubuntu-restricted-extras and install it. 


---

### Post by PriceChild on 2008-01-15
> **brucewagner said:**
> I have reinstalled Ubuntu 4 times, and tried each one.  They do not work.They **DO work**. They just **don't seem to work for you**.

Big difference.

Please file bugs on file-formats not correctly detected etc. on launchpad

---

### Post by sr20ve on 2008-01-15
Dell has more money than Canonical.

---

### Post by bufsabre666 on 2008-01-15
> **sr20ve said:**
> Dell has more money than Canonical.

regardless of that, canonical can afford it, its just that would violate the meaning of OSS

---

### Post by kellemes on 2008-01-15
I really don' t see why people can have a hard time installing non-free stuff.. I understand people don't known initially but it's all in the standard documentation.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by igknighted on 2008-01-15
> **brucewagner said:**
> You guys...  I'm a brand new day one user.   And I don't know how to do it. (seriously)

Besides....  I think there are a LOT of us "brand new day one" users out there.

Part of the whole concept of Ubuntu is to make it simple and easy for anyone... no?

There has to be a way to automate the installation of that stuff... and still conform to the legalities. 

If apt-get can install it...  Then apt-get is "a script providing a way for someone to break the law".

It can get to the point of being ridiculous.   And remember, it's NOT always against the law --- in the country the user may be living in.

Put that same movie in a stock windows PC and click play... oh wait, it doesn't work there either.  You still need to search online to find a codec.  An OEM like Dell often includes this, but stock windows does not.

The problem is not with Ubuntu.  It is easier to get and add this functionality to Ubuntu than it is to windows.  The problem lies with Users who are used to an OEM setting up their computer having to deal with all these little things that they don't usually see.  When OEMs sell linux PCs with the same level of thought put into them as windows PCs (like Dell including DVD playback), you will see this being less of a problem.  But until then we should simply make the information available on how to do it, for various legal and philosophical reasons that have been discussed here ad nauseam.

---

### Post by bufsabre666 on 2008-01-15
honestly getting the codecs is easy in ubuntu

its easy in windows too

ever hear of free-codecs.com?

or just codecs.com same site but you just need to get a simple codec pack.... just like ubuntu, theres no reason to include it especially when its technically illegal when getting it is so easy

---

