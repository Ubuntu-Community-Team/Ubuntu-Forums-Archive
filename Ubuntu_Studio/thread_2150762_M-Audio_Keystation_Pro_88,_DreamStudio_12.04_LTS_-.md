---
title: "M-Audio Keystation Pro 88, DreamStudio 12.04 LTS - and Sibelius on Windows 7"
date: 2013-06-02
forum: Ubuntu Studio
---

### Post by tnob on 2013-06-02
[FONT=Arial][COLOR=#000000]Greetings all,

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]Some help please with a few matters I find rather confusing.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]I&#8217;m a musician,first and foremostly. Hence, I&#8217;d like to spend most of my precious time making music; constantly overcoming IT hurdles, as has been the case for rather awhile, was definitely not on my mind, when I first thought of developing a homestudio. And the ways in which Ubuntu and Windows interact (or fail to), in my particular system setup (see below), are really baffling.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]The centrepiece of my home studio is an IBM Intel ® Core &#8482; i-5 3470 CPU @ 320 GHz 3.20 GHz. It&#8217;s64-bit and has 4 Gb RAM on board. DDH is a whopping 750 Gb.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]My main platform (i.e.the one on which I intend to do most of my music production) is UbuntuDreamStudio 12.04 LTS. Yet for music notation and generating sounds of musical instruments I don&#8217;t play (to be recorded as audio, with Audacity or Ardour), I&#8217;m to divert to Sibelius, on a Windows 7 VirtualBox. The reason for this is that all music notation software on Ubuntu only allows for one note at a time &#8211; which is not always practical. 

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]Even with Windows switched on, Ubuntu remains perfectly accessible at all times (unless, of course, Windows has been set to full screen). This, too, is important to takenote of.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]My MIDI workstation is an M-Audio Keystation Pro 88  (fully wired up, but not operational yet) &#8211; and I&#8217;d like to align it, amongst others,with Sibelius on Windows 7. Some very useful guidance as to how to do this was found online.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]And yet&#8230;

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]Ubuntu doesn&#8217;t require any additional Pro 88 drivers at all, apparently &#8211; as various documents assure me. Windows 7, on the other hand, insists on an additional set of drivers (not included at the time of purchase) to beinstalled. But if I try to activate the Keystation with Ubuntu, I never detect any visible signs that DreamStudio actually recognizes the Keystation &#8211;regardless of JackCtl being on or off. And I&#8217;m not really sure as to how toinstall those additional drivers, if going in at the Windows end.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]All this raises some interesting questions:
[/COLOR][/FONT]
[LIST=1]
[*][FONT=Arial][COLOR=#000000]I assume that, on my system, Ubuntu and Windows are     sharing one and the same information pool. Is that correct? [/COLOR][/FONT]
[*][FONT=Arial][COLOR=#000000]On several occasions in the past (again, as far as my     particular setup goes), Ubuntu regularly registered drivers and other     external matter **only aft[B]er **being installed on Windows first. [/B]Consequently,     can it be argued that, in order to ensure that Ubuntu recognizes external     material (like those Pro 88 additional drivers aforementioned), does it     **necessarily** have to be brought in at the Windows end, for starters? [/COLOR][/FONT]
[*][FONT=Arial][COLOR=#000000]My Keystation Pro 88 will mainly be active on     DreamStudio. But it&#8217;ll also be required to serve as a MIDI USB interface     for Sibelius on Windows &#8211; meaning that those Pro 88 drivers (currently on     a memory stick) have to be installed on Windows 7 as well. Now remember:     Ubuntu remains entirely operational at all times &#8211; even with Windows,     simultaneously, in full flux. So in this light, would it then be possible     to employ DreamStudio, in one way or another, to those install drivers in     Windows 7?  And if yes, how?[/COLOR][/FONT]
[*][FONT=Arial][COLOR=#000000]And further to this reasoning: with my system&#8217;s setup specifics in mind, could operating Sibelius, in     Windows 7, from a Keystation Pro 88 in Ubuntu realistically be achieved?[/COLOR][/FONT]
[/LIST]
[FONT=Arial][COLOR=#000000][/COLOR][/FONT] 

[LIST=1]
[/LIST]
[FONT=Arial][COLOR=#000000]I&#8217;m trying to figurea way out of this heap of conundrums &#8211; yet neither side is yielding any result,as things are currently standing. I&#8217;d really appreciate some advice here.

[/COLOR][/FONT][FONT=Arial][COLOR=#000000]tnob[/COLOR][/FONT]

---

### Post by jejeman on 2013-06-02
If you need to use win application, and on win7 in VM why bother with dream studio? Why bother with VM?

---

### Post by BcRich on 2013-06-02
Hi tnob,
If you'll forgive me for saying this, but I think your setup seems to be quite complicated.
As it would seem that jejeman has hinted, if I'm not mistaken, I'd agree that simply trying to stick with one system or the other (i.e. Dreamstudio or Win7) might simplify the setup issues you are currently experiencing.
> [FONT=Arial][COLOR=#000000]The reason for this is that all music notation software on Ubuntu only allows for one note at a time[/COLOR][/FONT]
This I'll agree would certainly complicate things, but are you sure that Rosegarden and lilypond have this limitation?

---

### Post by Elfy on 2013-06-02
Hi Jejeman & BcRich,

Don't get me wrong here. To judge from your reactions, maybe a little more background should be in order here.

Some three years ago, I wasn't even aware of the existence of Ubuntu - or DreamStudio. So where I'm coming from is a ten year struggle in attempting to set up a more or less functional home studio on Windows. Suffice to say that this has been a nightmare I'm not keen to return to: give me the ease and reliability of DreamStudio any day!

That said, the only two things I'm not really happy with in DreamStudio are the quality of the notation software available. Rosegarden, for instance, is not particularlyuser-friendly, to my mind; with Lilypond, I don't have any experience.. Besides, the mindboggling complications of video capturing are something else doing my head in. And for these two reasons - and these alone! - I'm resorting to Windows, from time to time.

All Ubuntu notation software available seems to be based on wherever Sibelius, on Windows, comes from. But it is limited in that longer passages cannot be introduced in one fell swoop. And as far as I know, nothing on Ubuntu equals AudioScore &#8211; the score appearing on-screen as you&#8217;re singing it into a mic directly plugged into the computer!

The very moment Ubuntu has comparable technology on offer, I&#8217;ll back in a flash &#8211; believe me. But for now, Sibelius on Windows seems the only way to go, if it comes to notation &#8211; and much more beyond that.

So, as to my Keystation Pro 88, I&#8217;d prefer to run it on Ubuntu. Yet fact of the matter is that, if I want it also to serve as a MIDI interface for Sibelius, Pro 88 will have to be activated in Windows as well. And since both Ubuntu and Windows seem to be deriving their operational information from the same sources (whatever they may be) within my system, running Pro 88 in Ubuntu whilst, simultaneously, activating and operating Sibelius on Windows, might be not all that far-fetched, theoretically.

Assumed this is a distinct possibility, I&#8217;d still have no clue whatsoever as to where to start. But as I was thinking this over, several more angles came to the fore. Those are reflected in the four questions towards the end of my introductory post

Apart from this, there are quite a lot of buttons,knobs and sliders on a Pro 88. And the jargon in one of the two manuals I downloaded is impenetrable. so I'd appreciate it someone could explain to me, in plain English, how to tackle this!.

tnob

---

### Post by sidh on 2013-06-02
Hi Jejeman & BcRich,

Don't get me wrong here. To judge from your reactions, maybe a little more background should be in order here.

Some three years ago, I wasn't even aware of the existence of Ubuntu -  or DreamStudio. So where I'm coming from is a ten year struggle in  attempting to set up a more or less functional home studio on Windows.  Suffice to say that this has been a nightmare I'm not keen to return to:  give me the ease and reliability of DreamStudio any day!
 
That said, the only two things I'm not really happy with in DreamStudio  are the quality of the notation software available. Rosegarden, for  instance, is not particularlyuser-friendly, to my mind; with Lilypond, I  don't have any experience.. Besides, the mindboggling complications of  video capturing are something else doing my head in. And for these two  reasons - and these alone! - I'm resorting to Windows, from time to  time.
 
All Ubuntu notation software available seems to be based on wherever  Sibelius, on Windows, comes from. But it is limited in that longer  passages cannot be introduced in one fell swoop. And as far as I know,  nothing on Ubuntu equals AudioScore – the score appearing on-screen as  you’re singing it into a mic directly plugged into the computer!
 
The very moment Ubuntu has comparable technology on offer, I’ll back in a  flash – believe me. But for now, Sibelius on Windows seems the only way  to go, if it comes to notation – and much more beyond that.

So, as to my Keystation Pro 88, I’d prefer to run it on Ubuntu. Yet fact  of the matter is that, if I want it also to serve as a MIDI interface  for Sibelius, Pro 88 will have to be activated in Windows as well. And  since both Ubuntu and Windows seem to be deriving their operational  information from the same sources (whatever they may be) within my  system, running Pro 88 in Ubuntu whilst, simultaneously, activating and  operating Sibelius on Windows, might be not all that far-fetched,  theoretically.
 
Assumed this is a distinct possibility, I’d still have no clue  whatsoever as to where to start. But as I was thinking this over,  several more angles came to the fore. Those are reflected in the four  questions towards the end of my introductory post
 
Apart from this, there are quite a lot of buttons,knobs and sliders on a  Pro 88. And the jargon in one of the two manuals I downloaded is  impenetrable. so I'd appreciate it someone could explain to me, in plain  English, how to tackle this!.
 
tnob

---

### Post by CrocoDuck on 2013-06-02
Hi. How did you connect the keyboard to your computer? If you connected it by USB cable then you should be able to see the MIDI interface into the Qjackctl's ALSA tab. If you connected it to the midi ports of your soundacard then you just have to use your soundcard's sockets still into the ALSA tab. Even if I planned to make some experiment regarding linux, virtualbox and "audio interaction" (nothing promising at first sight), I never done it and I never tryed that kind of controllers or audio interfaces on virtualbox (I used win xp on virtualbox just for few things...). But after had properly configured virtualbox to use usb devices I noticed that virtualbox "monopolizes" somehow the device I connect (USB pendrive), letting me able (at first sight) to read and write on it just under virtual-xp (if I remember correctly, I didn't use virtualbox for a year...).

> 
On several occasions in the past (again, as far as my particular setup goes), Ubuntu regularly registered drivers and other external matter only after being installed on Windows first. Consequently, can it be argued that, in order to ensure that Ubuntu recognizes external material (like those Pro 88 additional drivers aforementioned), does it necessarily have to be brought in at the Windows end, for starters?


If I properly understood the question, No. This seems useful when the devices have some kind of programmable features that you have to set with propetary software that usually runs just under windows (sometimes on linux under wine). I never used (or just connected) my programmable controllers M-Audio keystation 88es and keystation mini32 on windows (yeah, I use only linux since 4 years), but they worked just out of the box (litterally) with all functionalities on my linux systems. Check your manual in order to understand what the additional drivers are intended to do. So, it depends just on support by the os-drivers: some devices work just out of the box, some need twakings and some have some feature that has to be configured with a software that is usually not released for linux by the producers (for example a digital mixer built-in into a soundcard, to be controlled with propietary software). Sometimes happens that some keyboard has to be manually configured in order to let the defalult os-driver to handle her, for example: [http://linuxmusicians.com/viewtopic.php?f=6&t=10614](http://linuxmusicians.com/viewtopic.php?f=6&t=10614) . Refer to your device manual to point out if you need some special configuration to ensure that ALSA handles the keyboard.

In the past I successfully run NI GuitarRig and NI Bandstand (windows software) on linux using wine and wineasio. If it works is a lot better than using a virtual machine for the audio purposes: if it works the windoze apps behaves like the linux ones (and less resources should be needed for the execution). Have a look, this is old but could be a place to start: [http://ubuntuforums.org/showthread.php?t=1575191](http://ubuntuforums.org/showthread.php?t=1575191) .

Also you could install both systems as dual boot on your machine... Probably is easier and you can use the two systems at full power (but, of course, not at same time).

---

