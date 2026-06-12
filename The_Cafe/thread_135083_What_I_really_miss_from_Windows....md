---
title: "What I *really* miss from Windows..."
date: 2006-02-23
forum: The Cafe
---

### Post by Kerberos on 2006-02-23
On Explorer (you know, the file browser) there is a type-in box that lets you enter paths E.G. I can type in c:\temp to go there automatically - it also has autocomplete (which is nice) and lets you go directly to network shares just by typing \\squirrel\incoming\ and the like.  With Ubuntu I find I have to go through the laborious process of adding a network server or waiting ages on the network connections folder to get to a network resource (if it even shows up).

Is there a way to turn it on, or does it not exist under Linux?

---

### Post by DrFunkenstein on 2006-02-23
Well, first off, what file manager are you using?

If it's nautilus, hit Ctrl+L to get a type-in box. On the upcoming nautilus in dapper there'll also be an option to use this box by default.

As to connecting to a network, you should be able to simply use everything that gnome-vfs supports, for example: smb://location

Hope this helps and have fun.

---

### Post by DaMasta on 2006-02-23
Or just add the location bar permanately via gconf.

---

### Post by Virogenesis on 2006-02-23
Press ALT + F2 then type in type gconf-editior then press enter.

After that you'll see a tree menu Click apps it should then open up scroll down til you get to nautilus then click the folder preferences.

You'll see some crap open up in the other pane tick the box always_use_location_entry Then close down the program

---

### Post by PatrickMay16 on 2006-02-23
Once you've gotten the location bar, here's how to get to network shares easily.

Just type in **smb://***machine***/***share***/** , and you'll find it works much like **\\***machine***\***share***\**

EDIT: Oh, I see someone already said this. Sorry.

---

### Post by abhaysahai on 2006-02-23
My list of things that I miss from Windows
1) Playing music from Raaga.com  
2) Logging on to hsbc.co.in
3) google talk ( voice ) - though spyke is anytime better.  
4) Decent real media player -- VLC does but not as good as Windows Real Player.
5) Cannon Camera Software, though I can do most of the work with gtkam + gimp, but the Cannon Camera software had evrey thing integrated. Same goes for HP Printer/Scanner software, it has excellent MS Office integration. 

and last not the least -- 
6) VIRUSES. 

Abhay

---

### Post by T_Stormcrowe on 2006-02-23
What do I miss with Windows? NOTHING!

---

### Post by curuxz on 2006-02-23
I miss how slow it was, and always having to reformat. Oh yea and losing all my work because of the latest open socket expl..... fun fun fun.

I have not seen a single thing in thie thread that can not be done easly in ubuntu, exept for ms office intergration ;)

---

### Post by abhaysahai on 2006-02-23
[QUOTE=curuxz]I miss how slow it was, and always having to reformat. Oh yea and losing all my work because of the latest open socket expl..... fun fun fun.

I have not seen a single thing in thie thread that can not be done easly in ubuntu, exept for ms office intergration ;)[/QUOTE]

Really!!!! 
 I would be very happy if you have an solution for these
1) Playing music from Raaga.com
2) Logging on to hsbc.co.in

If you can do this, then please do write a howto so that I can follow and prevent myself from loggin to windows.

---

### Post by Mr.X on 2006-02-23
[QUOTE=abhaysahai]Really!!!! 
 I would be very happy if you have an solution for these
1) Playing music from Raaga.com
2) Logging on to hsbc.co.in

If you can do this, then please do write a howto so that I can follow and prevent myself from loggin to windows.[/QUOTE]


raaga.com is a streaming thingy? I can stream through VLC :P
And there is also realplayer10 in ubuntu :P
And wtf is hsbc.co.in?

---

### Post by Kerberos on 2006-02-23
[QUOTE=curuxz]I miss how slow it was, and always having to reformat. Oh yea and losing all my work because of the latest open socket expl..... fun fun fun.
[/QUOTE]
Learn how to use a firewall and secure your system then - it can be done.  Your also confusing usability with security and stability.  While Linux has security and stability down it lacks in usability, while Windows has had a lot of work in the HCI area it also gets pretty unreliable due to the single-user mode (which is fixed in Vista).

What I'd also like is for Ubuntu to boot in less than 5 minutes.  Especially considering I have to reboot immediatley as the Wireless Network never works first boot for some reason (sometimes it takes 3 reboots).  I guess a reformat and reinstall would fix this problem though.  :D

Thanks for all the comments, I'll give it a try when I get home.

---

### Post by Mr.X on 2006-02-23
[QUOTE=Kerberos]Learn how to use a firewall and secure your system then - it can be done.  Your also confusing usability with security and stability.  While Linux has security and stability down it lacks in usability, while Windows has had a lot of work in the HCI area it also gets pretty unreliable due to the single-user mode (which is fixed in Vista).

What I'd also like is for Ubuntu to boot in less than 5 minutes.  Especially considering I have to reboot immediatley as the Wireless Network never works first boot for some reason (sometimes it takes 3 reboots).  I guess a reformat and reinstall would fix this problem though.  :D

Thanks for all the comments, I'll give it a try when I get home.[/QUOTE]

From the time when i press the power button till im in ubuntu is 1 minute.
I hardly reboot lol.

---

### Post by abhaysahai on 2006-02-23
[QUOTE=Mr.X]raaga.com is a streaming thingy? I can stream through VLC :P
And there is also realplayer10 in ubuntu :P
And wtf is hsbc.co.in?[/QUOTE]

1) Have u ever tried raaga.com --- try it once. Its a known issue in Linux community. The only possible solution is installing IE inside wine.. 
Its eaasy to say that you can do things, its different to actually try them. 

2) Long time since I saw such language "wtf" on forum.. 
HSBC is one of the biggest bank in Asia/Pacific. Now don't ask "wtf" is Asia/Pacific.  And yes it is present in USA/UK/Australlia.

---

### Post by Perfect Storm on 2006-02-23
If you want your system to boot fast try initng, this may require a bit fiddle and tinkering. But when get it works you boot fast. I boot my system within 15 secs. (from turning the power on to I see the login screen).

Back to topic: Well in the start I missed photoshop, but then I found pixel32. So with a mix of gimp and pixel32 I got what I need.

---

### Post by Kerberos on 2006-02-23
[QUOTE=Mr.X]From the time when i press the power button till im in ubuntu is 1 minute.
I hardly reboot lol.[/QUOTE]
I would use hibernate as a solution (as I always did with XP), but it doesn't work either.  XP for me booted in around ~30s, and uptime was generally into the weeks time range - only Windows based on the 9x kernel needed frequent reboots.

---

### Post by lolocaust on 2006-02-23
[QUOTE=abhaysahai]HSBC is one of the biggest bank in Asia/Pacific. Now don't ask "wtf" is Asia/Pacific.  And yes it is present in USA/UK/Australlia.[/QUOTE]

From ubuntu, I can log into hsbc.co.uk with no problems at all. Its up to the webmaster who blocked out browsers that aren't IE (which is stupid imho, any browser that follows standards will work). Just send a friendly email asking to have other browsers supported, after just a few emails from people, they will most likely fix it :)

---

### Post by Mr.X on 2006-02-23
[QUOTE=Kerberos]I would use hibernate as a solution (as I always did with XP), but it doesn't work either.  XP for me booted in around ~30s, and uptime was generally into the weeks time range - only Windows based on the 9x kernel needed frequent reboots.[/QUOTE]
My windows use to load in about 5 seconds. \\:D/

---

### Post by midwinter on 2006-02-23
[QUOTE=abhaysahai]1) Have u ever tried raaga.com --- try it once. Its a known issue in Linux community. The only possible solution is installing IE inside wine.. 
Its eaasy to say that you can do things, its different to actually try them. 

2) Long time since I saw such language "wtf" on forum.. 
HSBC is one of the biggest bank in Asia/Pacific. Now don't ask "wtf" is Asia/Pacific.  And yes it is present in USA/UK/Australlia.[/QUOTE]

Hi, 

I use this extension in firefox to make the hsbc site think i'm using IE.  Works fine.

[https://addons.mozilla.org/extensions/moreinfo.php?id=59&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=59&application=firefox)

I do keep meaning to write them an email though.

---

### Post by Kerberos on 2006-02-23
[QUOTE=Mr.X]My windows use to load in about 5 seconds. \\:D/[/QUOTE]
And your point of relevance to this thread is?

---

### Post by rickyjones on 2006-02-23
I've always wondered... why can't we also do standard UNC paths for accessing file servers via samba? I mean, **\\servername\resource** is a UNC standard thing, I thought that Linux was all about standards?

-Richard

---

### Post by Brunellus on 2006-02-23
[QUOTE=rickyjones]I've always wondered... why can't we also do standard UNC paths for accessing file servers via samba? I mean, **\\servername\resource** is a UNC standard thing, I thought that Linux was all about standards?

-Richard[/QUOTE]
the standard in the *nix world is the forward slash;  backslashes are escape characters.  So in this respect, it is Microsoft's decision to use the backslash back in MS-DOS that was non-standard.

---

### Post by LordBug on 2006-02-23
The only thing I truly miss is ACDSee.  It's auto-sizing capabilities is something I've not yet found in Linux.  GQView has similar, but it's not as smart as ACDSee.

---

### Post by rickyjones on 2006-02-23
[QUOTE=Brunellus]the standard in the *nix world is the forward slash;  backslashes are escape characters.  So in this respect, it is Microsoft's decision to use the backslash back in MS-DOS that was non-standard.[/QUOTE]

Hmmm, I did not know that. Look at that, you learn something new everyday! Now, if only we could get rid of that pesky smb://.... lol.

-Richard

---

### Post by abhaysahai on 2006-02-23
[QUOTE=Mr.X]My windows use to load in about 5 seconds. \\:D/[/QUOTE]

Your ubuntu boots in 1 min and Windows in 5 sec.  Are you trying to prove a point??

---

### Post by earobinson on 2006-02-23
I would like to see google desktop, or a good clone for it in linux. I guess you could say i miss that.

---

### Post by GoA on 2006-02-23
I'm fleiming a bit but it seems that many users have had problems with viruses here. Ad-aware etc. How is that possible? You can use linux, shouldn't you be able to use windows in a way that it doesn't got these problems? ;) I haven't had any problems with windows xp after I first time read something about firewall and firefox/opera. No viruses, no adware, no security problems etc. It just works and keeps going on. Same thing in linux, it just works, IF you know what to do. And yes I know, it would be nice if windows just would be safe. However, with a little bit of knowledge, it stays clean.

EDIT: And yes, I miss Daemon tools and Windows media player/ffdshow.

---

### Post by earobinson on 2006-02-23
Not true, an expert linux user should be able to use windows without gunking it up. But like ubuntu is also great for people who dont know how to use computers because once it is set up it is harder to break, espicaly if they dont have admin privs.

---

### Post by OneSeventeen on 2006-02-23
As for the individual who has to reboot to get wireless working, have you tried configuring your wireless, and re-selecting the ESSID you already have selected?  (sound silly, and it is, but it works for me)

Anyway, What I miss from Windows is hardware support.

I know that is a hardware manufacturer's decision, but it's still true.

All the software I use runs on both Windows and Linux, but for some reason most of the hardware manufacturers that I regretfully bought products for don't write linux drivers.

(The card reader in my laptop, a vinyl cutter, and a scanner are the big things that come to mind)

Fortunately, I found another scanner with worse quality, but works in linux, and the next version of gnutenprint (or whatever gimp-print will be called) will let me print to CDs using my photo printer, and I have an external card reader for my laptop.  (not so fortunately, my mother-in-law will be taking her vinyl cutter back in the summer)

So in reality, as far as software is concerned, the only thing I could possibly miss is photoshop, but it looks like pixel32 might someday get close enough for me to use.

---

### Post by Kerberos on 2006-02-23
[QUOTE=OneSeventeen]As for the individual who has to reboot to get wireless working, have you tried configuring your wireless, and re-selecting the ESSID you already have selected?  (sound silly, and it is, but it works for me)[/quote]
I am not entirely sure what you mean - the Wireless doesn't even appear in the network list until I reboot again.  I have to configure it from scratch each time it starts
> All the software I use runs on both Windows and Linux, but for some reason most of the hardware manufacturers that I regretfully bought products for don't write linux drivers.

Amusingly the laptop in question is an AMD64 one, and Intel classify Windows 64 as 'unsupported' and refuse to write a driver for it or support it, yet Ubuntu sees it straight away (despite the constant reboots required).

---

### Post by Stormy Eyes on 2006-02-23
I have to use Windows at work. I don't miss it when I'm at home.

---

### Post by zachtib on 2006-02-23
I miss the constant crashes, seriously, now there's less excuse for me to turn a project in late, because I never lose all my data to a huge system crash.  Oh well, I guess that's what Xgl is for...

---

### Post by Bandit on 2006-02-23
I have really thought this through and I honestly don't miss a damn thing about windows.. :twisted: 

Cheers,
Joey

---

### Post by xequence on 2006-02-23
> VLC does but not as good as Windows Real Player.

VLC beats all other video players.

---

### Post by Protostar on 2006-02-23
I don't miss anything. I never got viruses, but I did get spyware. It was easy enough to clean with Adware, but I got sick of doing that. Why should I waste my time cleaning my computer with spyware from Windows XP, when I can use Ubuntu and not have to worry about any spyware period. I'm an avid porno watcher (not addicted, just watched it alot), and in Windows you stand to get alot of spyware (and some viruses to) by going to some porno sites. In Linux you are immune which is why I refer to Linux as the "Porno user's OS" when joking around with my friends. I also got sick of the slowness. Sure it was moderately fast when you first installed, but as time went on it got slower and slower and slower. Programs would sometimes take a minute or more to maximize from the minimized state, and it would sometimes take close to 5 minutes to bring my laptop back from sleeping. In Ubuntu it's almost instanenous. I don't miss anything about Windows. I do miss Office 2003 though. OpenOffice is so slow.

---

### Post by zachtib on 2006-02-23
[QUOTE=xequence]VLC beats all other video players.[/QUOTE]

i agree completely, I've yet to find a video file that vlc won't play

---

### Post by benplaut on 2006-02-23
i miss some games, namely warrock and vietcong2. I'm dual booting once i have a good enough computer to make it worth-while :)

---

### Post by K.Mandla on 2006-02-24
[QUOTE=Kerberos]What I *really* miss from Windows...[/QUOTE]
I miss defragmenting. I liked watching the little colored blocks shuffle into place. :neutral:

---

### Post by awakatanka on 2006-02-24
[QUOTE=zachtib]I miss the constant crashes, seriously, now there's less excuse for me to turn a project in late, because I never lose all my data to a huge system crash.  Oh well, I guess that's what Xgl is for...[/QUOTE]
Dude i think its time you upgrade youre windows ME version to 2k our xp because it hardly crashes.

And mostly windows crashes because the crappy drivers from 3th party.

---

### Post by Iandefor on 2006-02-24
I don't really miss that much from Windows. In fact, I don't miss a thing. Linux meets my needs more than adequately.

---

### Post by GoA on 2006-02-24
Actually, I would instantly switch back to Ubuntu as my main system if I wouldn't download movies, dvd's and so on from bittorrent. Yes, those work somehow in linux, but it just is easier in windows. And why, o why has to VLC be so plain ugly? 

And then in generally speaking of appearance: Firefox looks very nice in Ubuntu but not in Kubuntu. And then Opera is the opposite. :( 

And yes, this isn't so good argument but what can you do, I'm just  an eyecandy person. :)

---

### Post by Perfect Storm on 2006-02-24
[QUOTE=GoA]Actually, I would instantly switch back to Ubuntu as my main system if I wouldn't download movies, dvd's and so on from bittorrent. Yes, those work somehow in linux, but it just is easier in windows. And why, o why has to VLC be so plain ugly? 

And then in generally speaking of appearance: Firefox looks very nice in Ubuntu but not in Kubuntu. And then Opera is the opposite. :( 

And yes, this isn't so good argument but what can you do, I'm just  an eyecandy person. :)[/QUOTE]

Because VLC accidently was compiled with GTK1 instead of GTK2. That will change in Dapper or if you can't wait you might want to compile it by yourself in breezy, here's what you need: [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html) here's some more info about flag options for VLC: [http://developers.videolan.org/vlc/nix-compile.html](http://developers.videolan.org/vlc/nix-compile.html)

Firefox: I heard they are working on a QT version so it will intergrate better in in the KDE envoriment. Opera have it's own system, complain to opera not linux fault.

---

### Post by DrFunkenstein on 2006-02-24
[QUOTE=Artificial Intelligence]Because VLC accidently was compiled with GTK1 instead of GTK2. That will change in Dapper or if you can't wait you might want to compile it by yourself in breezy, here's what you need: [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html) here's some more info about flag options for VLC: [http://developers.videolan.org/vlc/nix-compile.html](http://developers.videolan.org/vlc/nix-compile.html)
[/quote]
And of course there are other great player that will play anything you download via bittorrent, like mplayer or xine.

[QUOTE=Artificial Intelligence]
Firefox: I heard they are working on a QT version so it will intergrate better in in the KDE envoriment. Opera have it's own system, complain to opera not linux fault.[/QUOTE]
The Qt version of Firefox is far from stable, but there are several themes that will integrate Firefox much better into KDE and of course one can also give the gtk-qt engine a try.

As for opera, go hit their theme site. IIRC there are some gnome-themes available there.

---

### Post by GoA on 2006-02-24
Yes, Dapper is going to change a lot of things and I'm exited to wait for it launch. In generally speaking my only problems with linux is the inability to mount bin, nrg and so on files but VLC should handle them automatically. 

Then my soundcard gives me trouble in linux. Terratec Aureon sky 5.1. It works in Breezy with ESD but I cannot play to sounds at the same time. Once I managed to get it working but it required some tuning. I hope Dapper fixes also that. :) I already tested Dapper live cd at work and it was SWEET. So I have high  hopes for Dapper and future of linux/Ubuntu. 

But because I'm a rational human being, I use the system which suites me better and currently it it Windows XP. So please don't hang me for this. :P

---

### Post by zachtib on 2006-02-24
[QUOTE=awakatanka]Dude i think its time you upgrade youre windows ME version to 2k our xp because it hardly crashes.

And mostly windows crashes because the crappy drivers from 3th party.[/QUOTE]

That was called sarcasm.

Fortunately, I've never had to use ME, but after using XP for about a year, I switched to linux and haven't used Windows since

---

### Post by WalterDirt on 2006-02-24
Wow, what is it with people saying how often there windows crashes? I would seriously think about buying better hardware or maybe stop touching your motherboards after rubbing your feet on the carpet to gain electrical charge.

There (MS) operating system has gotten tremendously better since windows 98.

I bring this up because I realize now that I've recently made the switch that the software works great if you know what you're doing. I'm new to Ubuntu and in the course of a month I've managed to lock up Ubuntu five times. I haven't had a system crash in my XP, well since I installed it back at the turn of the century.

Do I blame Ubuntu for the crashes, no, most likely it was my dumba** fault for not being familiar with the limitations. And maybe there was some way I could have brought it back to life, maybe logging in remotely or something, but I don't posses the expertise at this point.

So instead of being total fanboys who need to bash other operating systems to justify your choice why not just enjoy what you got and realize the other stuff isn't for you?

---

### Post by DrFunkenstein on 2006-02-24
[QUOTE=WalterDirt]Wow, what is it with people saying how often there windows crashes? [/QUOTE]
What about, it simply crashes for them?

[QUOTE=WalterDirt]
There (MS) operating system has gotten tremendously better since windows 98.
[/QUOTE]
There can be no doubt about this.

[QUOTE=WalterDirt]
So instead of being total fanboys who need to bash other operating systems to justify your choice why not just enjoy what you got and realize the other stuff isn't for you?[/QUOTE]
Though I agree with you that many of the posts here are quite childish, I'd also warn against taking your personal experience as an absolute truth. Just because your XP is rock solid doesn't mean it has to be for other people too, does it?

---

### Post by WalterDirt on 2006-02-24
What about, it simply crashes for them?
No, they come off as if as soon as windows boots up it crashes, then you reboot and you open a program again and it crashes. It's just become some kind of fanboy mantra and its seriously grating.

I spent quite a bit of time in desktop support in college and more often than not when we had to fix a computer it was user related, or cheap hardware breaking. So no, don't assume that I'm basing this from my one personal experience but from working on hundreds of machines at a major university.

---

### Post by zachtib on 2006-02-24
[QUOTE=WalterDirt]Wow, what is it with people saying how often there windows crashes? I would seriously think about buying better hardware or maybe stop touching your motherboards after rubbing your feet on the carpet to gain electrical charge.[/QUOTE]

Because making fun of Microsoft is fun ;)

Serously, though, I have used Windows 98, 2K, and XP, and even I will admit that the OS has gotten much better in terms of stability, but its not just the OS itself that causes stability.  The vast amount of spyware and viruses in existance also affect a computer's stability.

Anyways, some of you people need to learn how to take a joke.  Everytime someone cracks an anti-Linux joke, I just smile and throw another back at them.

---

### Post by satchm0h on 2006-02-24
Audio, audio, audio, and did I mention audio. What I miss from windows is the fact that I need to know absolutly nothing about my onboard sound hardware to get basic stereo sound coming out of the speakers...in flash...from movies..from CDs..mp3s...etc. I don't want to have to learn anything about esd (wasnt enlightenment a windowmanager?), alsa, oss, etc... It should just freakin' work. 

Dont get me wrong, I'm one of the fanboys. I sit in front of Ubuntu 8+ hours a day, by choice. I've converted co-workers etc. The audio thing is annoying but really just one example of the deeper issue. The casual computer user will not, and should not have to, learn about the backend to make core features work. 

just my $0.02

---

### Post by WalterDirt on 2006-02-24
I really miss the well intentioned and consumer oriented licensing schemes. *hoowaa*

/and also a lot of my familiar programs (PS, winamp, newsbin pro, dreamweaver)

---

### Post by zachtib on 2006-02-24
Ok, for a serious answer:
At first I missed Photoshop, but I'm getting used to GIMP.  There are a few things I havent figured out yet.
I haven't yet found a good video editor for Linux.  I've installed Kino, but havent='t used it much.
I also miss Dreamweaver. I've been using Nvu, which is okay, but it also lacks a lot or features.
I miss not having to fight with my ATI drivers.
I miss having iTunes to manage my iPod.  I tried GTKPod, hated it, didn't care that much for banshee, though its gotten better, and am currently using Yamipod

Basically, if Adobe ported all their stuff to linux, I would be very happy.  Mark my words: "If Adobe releases a Linux port of Photoshop, and does it well, I will buy (read: not pirate) a copy" Open-source zealots will say no to proprietary software, but if its good quality, I don't mind paying for it.

EDIT:
[quote=WalterDirt]/and also a lot of my familiar programs (PS, winamp, newsbin pro, dreamweaver)[/quote]
looks like we miss some of the same things.  have you tried XMMS for a winamp replacement?

---

### Post by WalterDirt on 2006-02-24
I need a media library and as of right now I'm quite please with gmusicbrowser. It has a great streamlined interface and super fast access to my entire library. 

Click the artist name and a box pops up with an alphabetical listing of all artists in your music library, and quickly drill down from there. I love the concept, a bit different from winamp sure. 

Don't like the streamlined interface, check the preferences and you can make it look like itunes. Plus, with my large library it only eats up about 50MB of resources. Not bad considering that other players would freeze up my system when I just attempted to load my library.

---

### Post by Miguel on 2006-02-24
I miss two things: games (though I'm deintoxicating myself) and half-decent ATi drivers (though in my laptop I can only use those provided directly by Dell).

I used to miss some sound quality. For some reason, and though this is a laptop that sounds like a laptop, windows had much better sound than Ubuntu. I guess it was because, on laptop settings, WinXP did some kind of bass equalizing which I couldn't do in ubuntu. This has changed in Dapper. Maybe this is the placebo effect, but I feel the sound in dapper (using gstreamer 0.10) much better. Please bear in mind that I use my wired gigantic headphones pretty often, and these do not have the bass restriction of a laptop.

Now, for a change, I will tell you what I miss when I boot into WinXP. First, I miss the security effect of not running as root. I miss the feeling that if I touch something, I can fix it. I used to miss virtual desktops (I don't know why I installed MS virtual manager, as I boot windows only for playing). I miss some nice keyboard shortcuts. I miss (behold!!!) a good CLI. I miss a good ssh (no, putty, plus winscp won't do it). I miss easy theming. I miss a software package manager. And, on the political side, I miss the freedom.

---

### Post by daredevil on 2006-02-26
nothin as am able to do everything that i do with win

---

### Post by guano on 2006-03-25
Well I haven't used windows in a long time. For the past three year, my machines (desktop and notebook) run Linux. 

One thing I start missing from Windows, after I get my notebook, is that in windows, it is really easy to get video out to a vga beamer or to the tv, but in linux... my notebook has a video card from intel, and their support to the linux community sucks, IMO. NVIDIA has excellent support, though.

I will try Pixel32, I think that GIMP is pretty good, but no one can beat Photoshop...

Besides that, every time I have to use a windows machine, I feel bad.. just one desktop.. ugly windows...:evil:

---

### Post by bored2k on 2006-03-25
I miss running Microsoft Office 2003 as native. I also miss computer games.

---

### Post by IYY on 2006-03-25
Here's what I miss (and it's not much):

- Photoshop: I love Gimp, but it doesn't do CMYK right, and I don't like its multi window design. Of course, Photoshop runs fine in Wine.

- Macromedia Flash. It's very important for web design. Even if the geeks don't like Flash sites (I'm no fan myself), you can make some good money selling them to people.

- MSPaint: I do a lot of pixelart as a hobby, and while there are many similar programs for GNU/Linux, none of them have the same level of simplicty as MSPaint. It comes from a time period when MS actually made lightweight apps with simple and intuitive GUI's (Notepad, Office 95).

- Winamp. XMMS is almost as good, but not quite.

- Office. OO2 is good enough, and is better in some ways (save as PDF, better equation editor), but is still a bloated app designed quite poorly.

The one thing I miss most of all is a small detail, but still:
Explorer uses an image named folder.jpg as the picture of the folder. This makes MP3 collections much neater, because it's possible to store the album art for each folder. The worst part is that Nautilus, Konqueror and even ROX are fully capable of displaying a folder image, but just don't implement this simple little feature!

I think that's it, really...

---

### Post by IYY on 2006-03-25
[QUOTE=WalterDirt]Wow, what is it with people saying how often there windows crashes? I would seriously think about buying better hardware or maybe stop touching your motherboards after rubbing your feet on the carpet to gain electrical charge.

There (MS) operating system has gotten tremendously better since windows 98.

I bring this up because I realize now that I've recently made the switch that the software works great if you know what you're doing. I'm new to Ubuntu and in the course of a month I've managed to lock up Ubuntu five times. I haven't had a system crash in my XP, well since I installed it back at the turn of the century.

Do I blame Ubuntu for the crashes, no, most likely it was my dumba** fault for not being familiar with the limitations. And maybe there was some way I could have brought it back to life, maybe logging in remotely or something, but I don't posses the expertise at this point.

So instead of being total fanboys who need to bash other operating systems to justify your choice why not just enjoy what you got and realize the other stuff isn't for you?[/QUOTE]

You're right. While I like GNU/Linux much more than Windows, I have to admit that XP crashes about as often as Ubuntu if managed correctly. The problems really only arise when infected by malware, or running an unupdated version. Of course, the problem is that many novices -will- install malware, and will -not- install the updates. The fact is: grandma's XP box has porn popups and crashes every 5 minutes.

---

### Post by Swiss on 2006-03-25
Whats to miss? [img]http://smileys.smileycentral.com/cat/36/36_1_19.gif[/img]

---

### Post by roachk71 on 2006-03-25
Absolutely Nothing:

If you know what you're doing in Linux, your computer can be much more useful and efficient. Since I've learned how to rebuild the kernel and install NDiswrapper from source, my Belkin wireless-G card works quite smoothly.

Linux also has a terrific suite of office apps compatible with many formats, and I could never figure Dad's Corel Draw out. I'll stick with the GIMP.

Why would I want to go back? :KS

---

### Post by Wallakoala on 2006-03-26
I can help with the streaming audio from a website (raaga.com or whatever it was called)

First off, use firefox. You have to download a firefox extension called MediaPlayerConnectivity (sp?). Just do a search on the firefox addons website. 
Next, you have to download vlc and set MediaPlayerConnectivity to use vlc. Now, whenever you want to stream something, instead of listening to it within the browser, you can click on it and then vlc will stream it out of the web browser.

---

### Post by Tatey on 2006-03-26
I miss native support for many Games in addition to Adobe Photoshop. Now, Photshop runs under wine, but it's still not 100% perfect like it is under Windows or Mac OS X. That said, I've been playing with GIMP and while it's nice to do simple touch ups and image resizing, it's still not Photoshop. I'm going to give that Pixel32 a try as well, the licence is alot cheaper than Photoshop too ;). 

Anyhow, one thing I still haven't ever been able to sovle with GNOME is the size of the buttons on the "Window List" of the Panel. Now, this point may seem trivial, but both KDE and Windows have "fixed" sizes for these buttons where as with GNOME, if you only have one application open the button will take up 3/4 of the panel, and then if you open 2, both buttons split in half and take up the entire window list. While I'm slowly getting use it, I'd still prefer fixed sizes.

---

### Post by Danni on 2006-03-26
There is only one thing I miss from Windows (and I use my partner's super pc for this) and that's The Sims 2. I have all the expansion packs, and apart from solitaire and tetris and mines and things it's the only game I play. If Cedega could play it, I wouldn't use Windows for anything (except in college).

My partner won't use Linux, simply because he's a big gamer (it's not the only thing he uses his pc for, but it's a big part of it). However, the server we rent runs CentOS, and he agrees that Windows is no good for servers, especially as we can't monitor it all the time. My daughter is going to be taught both Windows and Linux, as we feel it's important she knows both.

---

### Post by midwinter on 2006-03-26
[QUOTE=Tatey]
Anyhow, one thing I still haven't ever been able to sovle with GNOME is the size of the buttons on the "Window List" of the Panel. Now, this point may seem trivial, but both KDE and Windows have "fixed" sizes for these buttons where as with GNOME, if you only have one application open the button will take up 3/4 of the panel, and then if you open 2, both buttons split in half and take up the entire window list. While I'm slowly getting use it, I'd still prefer fixed sizes.[/QUOTE]

If you right click on the window list you can set the maximum and minimum size for the buttons - just set them the same size.. 

at least I think this is what you mean.

---

### Post by Tatey on 2006-03-26
[QUOTE=midwinter]If you right click on the window list you can set the maximum and minimum size for the buttons - just set them the same size.. 

at least I think this is what you mean.[/QUOTE]

Unfortunately that only lets you specify the size in pixels of the actual window list, not the buttons itself. Thanks though :)

---

### Post by Kaneda on 2006-03-26
I miss feeling like I know what I'm doing...  But that will change with time.

---

### Post by frustschieber on 2008-06-29
plug&play für external Monitors and Beamers
runs still not on kubuntu 8.04

---

### Post by Canis familiaris on 2008-06-29
Spyware and Viruses. :lolflag:

No, seriously, I do not miss much, only I miss games which do not run well in WINE.

---

### Post by zmjjmz on 2008-06-29
I always hated Windows, I'll never miss much.
On the other hand, I miss iMovie and iChat from OSX. Those were amazing.

---

### Post by maradr on 2008-06-29
I miss having to pay hundreds of dollars to upgrade.
I miss having to reboot after every security patch.
I miss all the pop ups and viruses and spyware that came along with them.
I miss spending hours on micro$ucks knowledge base to find an answer for a simple problem.

---

### Post by madjr on 2008-06-29
necros !

---

### Post by angryfirelord on 2008-06-29
Ahh! Zombie thread!

[IMG]http://hometown.aol.com/johnmscalzi/zombie0519a.jpg[/IMG]

---

### Post by RebounD11 on 2008-06-29
> **maradr said:**
> I miss having to pay hundreds of dollars to upgrade.
I miss having to reboot after every security patch.
I miss all the pop ups and viruses and spyware that came along with them.
I miss spending hours on micro$ucks knowledge base to find an answer for a simple problem.

2 things... if you didn't know how to solve the problem, I don't think it was that simple... and calling them micro$ucks doesn't do to much good to your apparent intelligence.

---

### Post by Enthralled on 2008-06-29
I miss only the games (the ones that I'm unable to emulate). Nothing more.

---

### Post by toupeiro on 2008-06-30
Things I miss from windows:

1. mspaint.exe Don't get me wrong, Gimp is great and ultra-powerful, but mspaint is quicker and dirtier than anything I've found on Linux so far for the quick screenshot manipulations or quickly taking graphics from clipboard and converting/manipulating them.

2. mmc.exe  A snap-in based local and remote management GUI that provides a standard form factor for all vendor and MS native tools to use, and you can customize it to hold whatever snapins you want, controlling as little, or as many tools, systems, or domains as you want.  Most people probably use this for their programs more than they realize.

3.  Visio.  Because there is no worthy peer to it in Linux.

Aside from these things, good riddance to it.  Life for me is better on this side of the fence overall.  I run it at work for the Windows systems I support, and thats fine.  It has its place, and likely always will have its place in the corporate world, but as far as I am concerned Microsoft has to completely alter the course of their current OS developments to ever get me interested in using one of their OS'es again, and with Ballmer at the wheel I only see things getting much, much worse.

---

### Post by Eion on 2008-06-30
I miss the games.  Thats all, Wine works sometimes, for some stuff.  But I have my 360 so it's not that bad ;)

---

### Post by ice60 on 2008-06-30
> **toupeiro said:**
> Things I miss from windows:

1. mspaint.exe Don't get me wrong, Gimp is great and ultra-powerful, but mspaint is quicker and dirtier than anything I've found on Linux so far for the quick screenshot manipulations or quickly taking graphics from clipboard and converting/manipulating them.
have you tried any of the mspaint clones? these 3 or 4 i think. i use KolourPaint, but it's qt, there's a gtk one i think.

i miss windows security most. i spent a lot of time on security forums. linux users just aren't interested with security, have a look for apparmor threads and you'll see what i mean!!

---

### Post by toupeiro on 2008-06-30
> **ice60 said:**
> have you tried any of the mspaint clones? these 3 or 4 i think. i use KolourPaint, but it's qt, there's a gtk one i think.

i miss windows security most. i spent a lot of time on security forums. linux users just aren't interested with security, have a look for apparmor threads and you'll see what i mean!!

I'm not familiar with KolourPaint, but I'll check it out.  Thanks for sharing that. :) 

As far as AppArmor, I can't say I've used it.  I'm more of an SELinux/PAM kinda guy, which I know has the gross learning curve, but it's pretty solid.  I first started playing with SELinux in RHEL.  Using it, I can build linux machines that from a security standpoint the box qualifies as an appliance in an audit. Other times, I may slack on some aspects of security if I know I am addressing them off the host.  You have seven layers to isloate security issues from a network standpoint, and they don't always all have to be applied and originating on a target host unless you are under strict guidelines to do so. :)

---

### Post by doorknob60 on 2008-06-30
> **toupeiro said:**
> I'm not familiar with KolourPaint, but I'll check it out.  Thanks for sharing that. :) 


Yeah, I was gonna say that. I used it all the time before I finally learned GIMP. It's interface is nearly identical to MS paint's but it also has a few little extras. Really a great program for people that are bad with graphic editing and GIMP makes their head hurt :-P

What I miss is Windows MOvie Maker. I've tried *everything*! The only program I liked was KDEnlive, but it produced badly out of sync videos...oh well I still got an XP partition for games (which I miss too but most of my games work in Wine).

---

### Post by toupeiro on 2008-06-30
> **doorknob60 said:**
> Yeah, I was gonna say that. I used it all the time before I finally learned GIMP. It's interface is nearly identical to MS paint's but it also has a few little extras. Really a great program for people that are bad with graphic editing and GIMP makes their head hurt :-P

What I miss is Windows MOvie Maker. I've tried *everything*! The only program I liked was KDEnlive, but it produced badly out of sync videos...oh well I still got an XP partition for games (which I miss too but most of my games work in Wine).

hehe I just think gimp is .. too much for graphics work that a system-admin does.  I like a minimal, single, interface thats easily hotkey-able and I can have it cropped and saved as fast as I can and move on to the next task.  I don't want to sift through toolbars and histogram windows.  When I want to do some transparancy layers and *change* a graphic, then gimp would be my first choice.  Gimp is for working on graphics.  mspaint, and perhaps kolourpaint, to me is to more quickly make the graphic I want available for whatever I am doing (e.g. quick documentation screen captures where the exact color pitch or compression doesn't really matter as much.)

---

### Post by ice60 on 2008-06-30
> **toupeiro said:**
> I'm not familiar with KolourPaint, but I'll check it out.  Thanks for sharing that. :) 

As far as AppArmor, I can't say I've used it.  I'm more of an SELinux/PAM kinda guy, which I know has the gross learning curve, but it's pretty solid.  I first started playing with SELinux in RHEL.  Using it, I can build linux machines that from a security standpoint the box qualifies as an appliance in an audit. Other times, I may slack on some aspects of security if I know I am addressing them off the host.  You have seven layers to isloate security issues from a network standpoint, and they don't always all have to be applied and originating on a target host unless you are under strict guidelines to do so. :)
i don't know if kolourpaint is any better then the others, it's just what i've always used.

i found being interested in computer security helped me learn so much about computers because of the all the malware attack vectors - ring0, userspace, DLL injection, buffer overruns, firewalls, internet protocols, hacktivex, killbits, JS, registry startups, etc, i'm still pretty clueless, but i learned more then if i'd been interested in gaming. 

since i've used linux everyday i learned how to run linux, then stopped learning because you don't really have linux security forums like you have windows forums.

---

### Post by toupeiro on 2008-06-30
> **ice60 said:**
> i don't know if kolourpaint is any better then the others, it's just what i've always used.

i found being interested in computer security helped me learn so much about computers because of the all the malware attack vectors - ring0, userspace, DLL injection, buffer overruns, firewalls, internet protocols, hacktivex, killbits, JS, registry startups, etc, i'm still pretty clueless, but i learned more then if i'd been interested in gaming. 

since i've used linux everyday i learned how to run linux, then stopped learning because you don't really have linux security forums like you have windows forums.

Interesting point. :)

I think I learned the most about windows security by being a Windows Application packager for a few years and applying that set of skills to my system admin skillset I've learned over the years.  You get pretty intimate with windows installer technology, the registry, the TCP Stack, Installation and uninstallation GUIDS, silent registration, library isolation, execution stack etc etc..  Its precisely this view that makes me appreciate the approach in linux applications and the overall security model.

---

### Post by acelin on 2008-06-30
I miss a good looking interface.

---

### Post by toupeiro on 2008-06-30
> **acelin said:**
> I miss a good looking interface.

See thats one thing I always felt Windows never had.  It was probably good looking to the person/people that designed it, but its not like you had a slew of options if you didn't, and things like stardock were too bloated.  I could always make KDE or Gnome look and feel pretty much the way I wanted from day one.

---

### Post by Martje_001 on 2008-06-30
Jeez.. this thread is 2 years old :P

That's what you call a topic kick..

---

### Post by maradr on 2008-07-05
> **RebounD11 said:**
> 2 things... if you didn't know how to solve the problem, I don't think it was that simple... and calling them micro$ucks doesn't do to much good to your apparent intelligence.

?????....WoW! Nice to meet you too buddy!

---

### Post by Roasted on 2008-07-05
What I miss is being able to pop in a live concert DVD and it fires right up.

I've been fighting with codecs and other ******** ever since I started on Ubuntu, way back almost 3 years ago now.

Still, to this day, even with Hardy Heron, I have no audio when I put in a dvd and play it through VLC.

Perhaps a full blown install of XP is due in the near future, sadly. :( But hey, at the end of the day, you gotta go with what works...

---

### Post by imari2542 on 2008-11-09
Viruses, spyware, excessive bloat and use of system resources

Aside from that, I still haven't gotten my Canon scanner to work but I'm working on that.  Did get the printer part of my Canon to work.

Alas, I will still always use windows if only on a limited basis to keep my Windows skills honed as I fix Windows PC's.  

I am always trying to convert people over to Linux and have had little success (1 person) but it's a start.  I've got others to at least try it.

---

### Post by Jengajam2 on 2008-11-09
nothing compares to windows movie maker...as in simplicity, of course.

---

