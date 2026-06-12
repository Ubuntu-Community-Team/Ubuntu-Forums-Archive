---
title: "something besides skype?"
date: 2006-10-20
forum: The Cafe
---

### Post by akurashy on 2006-10-20
So i feeling like looking for another option.. and preferrably with voicemail too. 

since skype charges, though even if is not expensive, is not something that i'm going to use daily.. if you know what i mean. in other words it would be a waste for me.

if there is any good one please name them :) (i only be choosing one of course i don't like using multiple things)

thanks!

---

### Post by Fass on 2006-10-20
There's [Gizmo](http://www.gizmoproject.com/), for one.

---

### Post by wieman01 on 2006-10-20
I don't quite get the point... SKYPE is free if you are making SKYPE to SKYPE phone calls because it goes solely through the Internet.

If you need to call somebody who happens to have a "fixed" telephone line only, then there are charges no matter what tool you use. That's because the traditional telecom companies take a cut & charge you.

So you pay one way or the other if you make calls through a telephone line.

---

### Post by moeFinley on 2006-10-20
Isn't it just about what your family and friends have installed?

But anyway Ubuntu comes with Ekiga which does every thing Skype does and video too.  Not sure about voicemail though.  Being open source its designed to be as flexible as possible can connect to a ton of other apps most notably MSN Messenger and Netmeeting.

[http://en.wikipedia.org/wiki/Ekiga]("http://en.wikipedia.org/wiki/Ekiga")

Another option is Wengo which is very similar but is a more comercial rather than community led project.

[http://www.openwengo.com]("http://www.openwengo.com")

Hope this helps

---

### Post by moeFinley on 2006-10-20
Wow, good tip Fass!  Gizmo let you call the landlines of your contacts for free!!  I'm going to persude everyone I know to install that! :)

---

### Post by wieman01 on 2006-10-20
> **moeFinley said:**
> Wow, good tip Fass!  Gizmo let you call the landlines of your contacts for free!!  I'm going to persude everyone I know to install that! :)
Read the side note... I don't think it's as simple as that. There is a catch.

---

### Post by akurashy on 2006-10-20
> **wieman01 said:**
> I don't quite get the point... SKYPE is free if you are making SKYPE to SKYPE phone calls because it goes solely through the Internet.

If you need to call somebody who happens to have a "fixed" telephone line only, then there are charges no matter what tool you use. That's because the traditional telecom companies take a cut & charge you.

So you pay one way or the other if you make calls through a telephone line.


What i want is also voicemail, skype charges voicemail which is the reason i'm looking for another. 

just to note, i don't hate skype or anything just if anyone wondering, just looking for a voicemail feature, since our timezones are differents i think you understand.

I probably go with gizmo if everything goes smooth, thanks!

---

### Post by wieman01 on 2006-10-20
> **akurashy said:**
> just to note, i don't hate skype or anything just if anyone wondering, just looking for a voicemail feature, since our timezones are differents i think you understand.
That's alright & understood. Personally - if I may say that - I don't like SKYPE at all. The Windows version is totally fine, however, their Linux support is lousy. But that's another story.

---

### Post by akurashy on 2006-10-20
well their new beta supports ALSA and the interface got way better.. dunno if you have check it out, which is way i'm liking it... after their changes and new support it's a relief for linux users imho

---

### Post by moeFinley on 2006-10-21
Just tried Gizmo, very buggy!  It wouldn't even start on mine.  Complained about no audio output device present.  The forums seems to be full of Linux support complaints.  Is it true the Linux app is only an Alpha?

Anyways I think I'm going to stick with Skype until Gizmo get there software sorted.

---

### Post by .t. on 2006-10-21
Don't use Skype. It's one of the evilest pieces of work on the planet. It's closed source and uses proprietary protocols. The least they could do would be to have it support SIP.

---

### Post by wieman01 on 2006-10-21
> **.t. said:**
> Don't use Skype. It's one of the evilest pieces of work on the planet. It's closed source and uses proprietary protocols. The least they could do would be to have it support SIP.
The most annoying thing is that they software is full of bugs. Bad programming... At least the Linux version.

---

### Post by banjobacon on 2006-10-21
> **moeFinley said:**
> Just tried Gizmo, very buggy!  It wouldn't even start on mine.  Complained about no audio output device present.  The forums seems to be full of Linux support complaints.  Is it true the Linux app is only an Alpha?

Anyways I think I'm going to stick with Skype until Gizmo get there software sorted.
Gizmo uses the SIP protocol, so you can access your Gizmo account with another SIP client, like Ekiga. This way you can take advantage of free voice mail without dealing with Gizmo's bugginess. 

Not that Ekiga is that great, but it might be good enough for what you need.

---

### Post by Mathiasdm on 2006-10-22
> **.t. said:**
> Don't use Skype. It's one of the evilest pieces of work on the planet. It's closed source and uses proprietary protocols. The least they could do would be to have it support SIP.
Nothing wrong with it being closed source, in my opinion;) 
The protocols are another thing.

I'm not using Skype, because of those protocols. Go SIP!

---

### Post by patrick295767 on 2006-11-19
I tried below: 

ekiga : has alsa support but if you get segmentation fault, your voip are not working !!!!!

gizmo : has problem of startup, you cannot even pass teh configuration settings

x-lite : it works but has only /dev/dsp support, no alsa: so, it sucks 

kphone : i dont know how to set up the alsa input / outpout
i wanna use my usb mic
so, not great for configuring.
and how to use the [email]user@ekiga.net[/email] account already made
 
 
 
soo, still, to get better

---

### Post by patrick295767 on 2006-11-19
wengo 
looks very close to LinuxSkype but in much less buggy
it is nice and not taht ugly
sthg nice is that it is supporting ALSA !! waho
you make an account and you get 1 euros for free that u can use to try to call lands.
i dont know about sip ? i doestnt look like there is a sip number on it.
it looks to be working and not buggy at all

---

### Post by patrick295767 on 2006-11-19
to use the gizmo account from ekigaa software:
config
Assuming 1747645xxxx is your SIP number. You can get your SIP number when viewing/editing your Gizmo user profile.

Run Ekiga and go to Edit -> Accounts -> Add. And add these entry:

    Account Name: gizmo
    Registrar: proxy01.sipphone.com
    User: 1747645xxxx
    Password: **********

    Authentication Login: 1747645xxxx
    Realm/Domain: proxy01.sipphone.com
    Registration Timeout: 3600

thank u buffalo soldier

---

### Post by Patrick K. on 2006-11-19
> **wieman01 said:**
> That's alright & understood. Personally - if I may say that - I don't like SKYPE at all. The Windows version is totally fine, however, their Linux support is lousy. But that's another story.

I've used skype for a long time and I have no complaints about the Linux version. In fact I even have skype out and skype in credits. However when they expire I'm switching to Gizmo so I can have call waiting music. I like the feature where I can put them on hold and make them listen to crappy poor quality elevator music. Bowhahahahaha

---

### Post by patrick295767 on 2006-11-19
> **Patrick K. said:**
> I've used skype for a long time and I have no complaints about the Linux version. In fact I even have skype out and skype in credits. However when they expire I'm switching to Gizmo so I can have call waiting music. I like the feature where I can put them on hold and make them listen to crappy poor quality elevator music. Bowhahahahaha

:-)
and you are using /dev/dsp or alsa ? usb mic ?

Thx

---

### Post by Sef on 2006-11-19
Here's what [Wengo's]("http://www.openwengo.org/") site says about Wengo:

> Freedom to Call, Freedom to Code
OpenWengo screenshot

Wengo is a VoIP provider from France. Our goal is to make standards-based SIP telephony available to all. That means you!

This website serves as a hub to our Open Source projects. Currently our main offering is WengoPhone, a GPL-licensed multi-platform softphone. Download it (or get the source and build it yourself) and use Wengo service or another SIP provider of your choice to make calls to any phone in the world. OpenWengo is an active community of developers, join us and become part of the Voice revolution! 

---

### Post by Patrick K. on 2006-11-19
> **patrick295767 said:**
> to use the gizmo account from ekigaa software:
config
Assuming 1747645xxxx is your SIP number. You can get your SIP number when viewing/editing your Gizmo user profile.

Run Ekiga and go to Edit -> Accounts -> Add. And add these entry:

    Account Name: gizmo
    Registrar: proxy01.sipphone.com
    User: 1747645xxxx
    Password: **********

    Authentication Login: 1747645xxxx
    Realm/Domain: proxy01.sipphone.com
    Registration Timeout: 3600

thank u buffalo soldier


What the heck? I tried that and it fails.

---

### Post by Patrick K. on 2006-11-19
> **patrick295767 said:**
> :-)
and you are using /dev/dsp or alsa ? usb mic ?

Thx


Man I got USB everything at this point. My sound is an external usb.

I got a total of 20 USB ports, 18 of them are being used.

Only thing on my computer that isn't USB is the friggin Video card. (AGP)

---

### Post by adam.tropics on 2006-11-19
> **Patrick K. said:**
> Man I got USB everything at this point. My sound is an external usb.

I got a total of 20 USB ports, 18 of them are being used.

Only thing on my computer that isn't USB is the friggin Video card. (AGP)


Why!?

---

### Post by Patrick K. on 2006-11-19
> **adam.tropics said:**
> Why!?

Simple. USB is better. :P

Well for one, I have a custom board from Biostar.com.tw

It has only one PCI slot and one AGP slot. The PCI slot has a mass USB hub internal card on it. With a total of 10 USB ports on it and 10 more on the board it's self.

5 of the USB ports on the card stick out the back and 5 more inside off the card. The 5 inside are dedicated to USB 4gig drives that hold Installations of Ubuntu 6.10, Fedora Core 6, FreeBSD, Windows XP. The other two drives are dedicated to **** and backup for documents. Please note those stars mean I have perverted stuff. :P

---

### Post by patrick295767 on 2006-11-19
> **Sef said:**
> Here's what [Wengo's]("http://www.openwengo.org/") site says about Wengo:

wengooo is quite well done program 
it also includes the aim messaging...

---

### Post by patrick295767 on 2006-11-19
> **Patrick K. said:**
> Man I got USB everything at this point. My sound is an external usb.

I got a total of 20 USB ports, 18 of them are being used.

Only thing on my computer that isn't USB is the friggin Video card. (AGP)

which one did you install to have skype working : 
Version: 1.3.0.53. Release date: October 04, 2006

RPM for SuSE 9 and newer (9.5 MB)

RPM for Fedora Core 3 (9.6 MB)

RPM for Fedora Core 4 (9.7 MB)

RPM for Fedora Core 5 (9.5 MB)

RPM for Mandriva 10.1 and newer (9.5 MB)

Debian package (9.6 MB)
Xandros, MEPIS, Ubuntu, other Debian-based distros

Dynamic binary tar.bz2 (9.4 MB)
Requires Qt 3.3

Static binary tar.bz2 with Qt compiled in (14.0 MB)

which alsa version do you have ?

---

### Post by patrick295767 on 2006-11-19
I just found that to have a working skype in/out with alsa
we need the Static binary tar.bz2 with Qt compiled in (14.0mb)

there is sthg wrong anyhow with their programming

---

### Post by patrick295767 on 2006-11-19
> **patrick295767 said:**
> I just found that to have a working skype in/out with alsa
we need the Static binary tar.bz2 with Qt compiled in (14.0mb)

there is sthg wrong anyhow with their programming

I could find that the probelms that usually persons have with the last release of skype is due to the PERMISSISONS

you run skype as root and it is fully workign.

If you would know, COuld you let me know how to change alsa permissions for shtg workign for users ?

thank you

---

### Post by mips on 2006-11-19
I'll vote for Wengo.

Last time I checked you could not send files while chatting like Skype.
The website needs some serious work as far as I'm concerned, still stuff in french within the english section. Also always defaults to french. I'm still waiting for my password I forgot and requested via the password recovery feature... It does not work ](*,)
Cannot register with my existing email address as it is in use, obviously...

Another problem is you cant shrink the window very small in the horizontal.

---

### Post by jdq997 on 2006-11-19
"Don't use Skype. It's one of the evilest pieces of work on the planet. It's closed source and uses proprietary protocols. The least they could do would be to have it support SIP."

WHAT??? Skype is an evil piece of work?  What planet are you on?

 - Jason

---

### Post by mips on 2006-11-19
> **jdq997 said:**
> 
WHAT??? Skype is an evil piece of work?  What planet are you on?

 - Jason

Not evil but they use proprietry protocols which is very annoying. Can you hear the words 'vendor lock in' ? They should use common industry or open standards like SIP for example.

---

### Post by sophtpaw on 2006-11-19
ok, my head is spinning. 

It's great that there is so much choice, but it can complicate things especially when there are half-a-dozen applications none which quite work...

So, i'm confused...how many voip phones are there? Ok, so skype is evil...what are the alternatives?

There is Ekiga, then i heard of gizmo here for the first time started trying to install it from binary (tar.gz) coz the i was told that it was better than using Debian's DEB package. But i only got as far as untarring it and no further, besides i immediately read (further along this thread) that gizmo is very buggy...
Then i hear about wengo. This is better than gizmo? Seems Ekiga, gizmo, and Wengo allow free calls from pc to pc, but requre payment to make any other type of call. 
So, what are the differences? and which offer the cheapest calls to landlines and mobiles?

---

### Post by .t. on 2006-11-19
Twinkle works alright. Anything's better than Skype :)

---

### Post by shining on 2006-11-19
> **sophtpaw said:**
> ok, my head is spinning. 

It's great that there is so much choice, but it can complicate things especially when there are half-a-dozen applications none which quite work...

So, i'm confused...how many voip phones are there? Ok, so skype is evil...what are the alternatives?

There is Ekiga, then i heard of gizmo here for the first time started trying to install it from binary (tar.gz) coz the i was told that it was better than using Debian's DEB package. But i only got as far as untarring it and no further, besides i immediately read (further along this thread) that gizmo is very buggy...
Then i hear about wengo. This is better than gizmo? Seems Ekiga, gizmo, and Wengo allow free calls from pc to pc, but requre payment to make any other type of call. 
So, what are the differences? and which offer the cheapest calls to landlines and mobiles?

Skype is the only one which works flawlessly for me. Nothing to configure, and it works quite well out of the box.
I had relative success with Ekiga and Wengo (didn't try gizmo), but they don't work as well, especially behind NAT (router).
I just tried the new 2.0 version of Wengo, and it doesn't work at all, but it's probably still the NAT problem..

So I can't do VOIP atm, and I'll just wait.

---

### Post by mips on 2006-11-19
> **sophtpaw said:**
> ok, my head is spinning. 

It's great that there is so much choice, but it can complicate things especially when there are half-a-dozen applications none which quite work...

So, i'm confused...how many voip phones are there? Ok, so skype is evil...what are the alternatives?

There is Ekiga, then i heard of gizmo here for the first time started trying to install it from binary (tar.gz) coz the i was told that it was better than using Debian's DEB package. But i only got as far as untarring it and no further, besides i immediately read (further along this thread) that gizmo is very buggy...
Then i hear about wengo. This is better than gizmo? Seems Ekiga, gizmo, and Wengo allow free calls from pc to pc, but requre payment to make any other type of call. 
So, what are the differences? and which offer the cheapest calls to landlines and mobiles?

Basically they do the same thing. the nice thing is that they use the SIP protocol which is a open industry standard.

Why ? Because any SIP device can talk to other SIP devices, be it a software client on a PC or a hardware Cisco IP phone etc.

The other nice thing is that there are various commercial SIP service providers on the net that have gateways into the PSTN (normal phone network). They allow you to buy credit from them and then to make calls to normal phones. Seeing there are more than one of them hopefully this stimulates competition and drives prices down which benefits us, the consumer. it also gives you choice, which you have none of when using skype.

---

### Post by .t. on 2006-11-19
Please don't lend yourselves to the proliferation of hate!

---

### Post by mips on 2006-11-19
> **.t. said:**
> Please don't lend yourselves to the proliferation of hate!

Who you talking to ? me ?

---

### Post by .t. on 2006-11-19
Eveyone using skype. Not necessarily you!

---

### Post by patrick295767 on 2006-11-20
whao, i found this : 
[http://209.85.129.104/search?q=cache:MwFed4BIh-gJ:jpl-conseil.typepad.com/jpl_conseil/voip_technologie/index.html+livebox+wanadoo+sip+voip&hl=en&ct=clnk&cd=8&client=opera](http://209.85.129.104/search?q=cache:MwFed4BIh-gJ:jpl-conseil.typepad.com/jpl_conseil/voip_technologie/index.html+livebox+wanadoo+sip+voip&hl=en&ct=clnk&cd=8&client=opera)

skype  and gizmo : iLBC; IETF (RFC3951 and RFC3952);
> iLBC is free
Unlike the other low bitrate codecs, iLBC is available for free and comes with full source code. If you would like to try it out and use it, please see freeware license..

[http://www.ilbcfreeware.org/](http://www.ilbcfreeware.org/)

and i am pleased to give you new softwares to try (M$ & LiNuX) : 
[http://www.ilbcfreeware.org/software.html](http://www.ilbcfreeware.org/software.html)
> mplementations

Here is the list of available implementations of iLBC.

Demo
GIPS/Hotsip SIP demo client 
Global IP Sound Developer Community 

Applications/Systems
Skype
Hotsip
Pandora Networks
Bellshare
Pingtel Instant Xpressa SIP client
Firefly
Xten networks X-Lite and X-Pro client 

HW IP Phones / IADs 
Ojo personal videophone
Grandstream Networks

Chip
Texas Instruments Incorporated 
AudioCodes
Leadtek
Mindspeed

Open Source
SIPfoundry
Public Domain SIP client Kphone
Asterisk Open Source PBX 
OpenH323 package 
GnomMeeting Open Source videoconferencing and VOIP application 

Info
More speech and sound processing tech.
iLBC - White Paper
If you are interested in fix point ANSI C, TI DSP, Motorola Starcore, etc. implementations please send a mail to Global IP Sound here.
 
  

> apt-get -f -y install asterisk
its in edgy repos.
    
Some reading : 

> Integrating Skype with Asterisk
Asterisk users have been clamoring for Skype integration since forever. Sure, you can use them side by side, but wouldn't it be nice to make Skype part of your Asterisk diaplan and network, instead of a separate service? So there are a number of projects in the works to bring the two together. Here are two Skype-to-Asterisk projects, or more accurately, Skype-to-SIP, that are worth taking a look at: 

ChanSkype
Chanskype takes a unique approach. It uses VNC, which is a cross-platform remote graphical desktop application, to run separate instances of the Skype client each in its own virtual display environment. The Skype instances appear to Asterisk as separate channels, so Asterisk admins can manage their Skype channels in the same way as any other channels. 

The free demo is rather bizarre- all you need is a SIP softphone, but then you're limited to three minutes' of testing on the ChanSkype servers. If you want to install and test it on your own server, calls are limited to 15 seconds, which is not enough time to test call quality or much of anything. A personal license is only $19, which is cheap enough for some serious testing. 

PSGw&#8212;Personal Skype to SIP and H.323 gateway
You can use this with a standalone Skype account, or with your Asterisk server. Configuring networking for Asterisk integration is a bit of a pain, because PSGw needs its own routable IP address to avoid port conflicts. Another problem is it doesn't forward DTMF tones, so you can't do the "press 1 to foo, press 2 to bar" dance, though support for this will appear in future releases. PSGw is inexpensive at $39.95 for the Windows version and $19.95 for Linux, and there is a free demo you can try. 

There are a number of hardware devices for integrating Skype with your iPBX, mostly on the expensive side. I haven't had a chance to look at any of them, so take a look at the Skype Gateways page on VoIP-Info.org to see what's available, and to get other useful information.

skype cheaper than gizmo:
> [http://blogs.zdnet.com/ip-telephony/?p=555](http://blogs.zdnet.com/ip-telephony/?p=555)

[www.kazil.comm](www.kazil.comm)
(looks craps, and coming crappy soon !)
> OTHER FEATURES
Besides the above all our members will enjoy additional features such as:

Caller ID
No more private calls that you can't screen before answering. Always know who is calling you, even before you pick up

Call-Waiting
Never lose another call as you are engaged on another. With Call-Waiting you can easily swap between calls and handle more than 1 call at anytime

3-way conference calls
Get on that important discussion by having a 3-way conference call. No messy calls, no difficult connections and it is free of charge

Call-Me button (coming soon)
Allow any website visitor and email recipient to call you for free simply by clicking your Call-Me button

Different ring tones (coming soon)
Choose your own ringtones to personalize your incoming phone call alerts

Voice mail (coming soon)
If you are unreachable at anytime, your caller can leave a voice mail and a link to playback the voice mail will be sent to your email address

Send SMS (coming soon)
Send a SMS to any mobile phone simply by entering the telephone number and the message on your SoftFone

Buddy List (coming soon)
Keep In close touch with all your Kazil members with a Buddy List which shows you who is online and offline

Instant messaging (coming soon)
Chat real-time with your Kazil members online, in a easy IM program, completely integrated with your SoftFone

[COLOR="RoyalBlue"]**Calling skype with GIZMO:**[/COLOR]
> Yes if you tell and convince them to install Gizmo on their computer and let it run at the start of Windows. If they do so, you all will be able to make free calls to PSTN landlines even outside USA. And you will be able to call them from Gizmo to Gizmo too. As Gizmo user you can register an ATA (grandstream.com) with your Gizmo account and use it 24/7 without any need of computer for calling to any Gizmo user. With a Skype account it is not possible to do so. 
You see now that Gizmo is better then Skype.
gateway, non free:[http://nch.com.au/skypetosip/index.html](http://nch.com.au/skypetosip/index.html)
  
Even better:
Chinese Programmers Hacked Skype Protocol
[http://www.gordonchoi.com/chinese-programmers-hacked-skype-protocol-20060909](http://www.gordonchoi.com/chinese-programmers-hacked-skype-protocol-20060909)
> He declined to name the research group, which is backed by venture capital funding. "They have plans to add presence, instant messaging, and a host of other features. Their end goal is to create a client 100 percent compatible with Skype," Paglee said."They are working night and day on a demo which they hope to launch before the end of August," he added. 




Man, I have the impression to be LIFEREA ! :-)

---

### Post by p0ssumtr0t on 2007-01-28
jajah is what I use it lets me set up a phone call and it calls me and connects me to a landline for 2,6 cents or if they are a jajah user it will call for free. I set up my mom and friends landline phones and it doesnt cost nuttin. :D

---

### Post by uboltun on 2007-04-28
I am subscribed to sipphone service and use both Gizmo and Ekiga. I prefer Ekiga since it is open source, but sometimes it drops calls and sends some strange sound to the other side. My connection is not great (10kb/90kb DSL) , but when I switch to Gizmo everything is smooth and normal. I am not sure if it is my settings or not , but SIP is open protocol, right? so both of them should work fine. However since Gizmo itself is not open , I suspect they play some strange game when Gizmo works better most of the times compared to other (free) software. I am still searching , but it looks like there are no perfect solution so far.

---

### Post by xyepblra on 2011-07-25
> **shining said:**
> Skype is the only one which works flawlessly for me. Nothing to configure, and it works quite well out of the box.Does that mean your Skype send text messages and transfers the phone number as your id?
Strange thing, I set it up on my Win7 machine at work, and it doesn't work on my Ubuntu laptop.

---

### Post by TenPlus1 on 2011-07-25
Google mail has a great feature that lets you chat inside the email window with your friends that appear on your buddy list, and with the new enhanced voice/video plugin lets you do this more smoothly and with better quality:

[http://www.google.com/chat/video?hl=en-GB](http://www.google.com/chat/video?hl=en-GB)

Go there, install ubuntu plugin for your 32-bit or 64-bit system then restart Firefox to enable...  Enjoy voice/video chatting to your google buddies :)

---

