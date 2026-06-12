---
title: "Why are so many users having issues with sound?"
date: 2008-01-19
forum: The Cafe
---

### Post by ubuntu-freak on 2008-01-19
Is it because of how manufactures implement it?
 
It's really bothering me. I've never had sound problems myself so I'm completely useless at helping others to resolve it. At least when people have graphics issues it means they either have to set the screen resolutions themselves, forcing it, or maybe some have to wait a few months before they can enjoy desktop effects.
 
I hope it gets resolved in Hardy. I can only guess that manufacturers (of laptops mainly) are completely random in the way they implement sound. Must be a total nightmare for the devs.
 
Nathan

---

### Post by Praadur on 2008-01-19
This is one area where (sadly) Linux is like Windows, and only because we're either at the mercy of manufacturers or we have to use frequently updated software as hardware is reverse-engineered and the boffins at ALSA figure out more about the different sound hardware out there.

I've fixed sound on a few machines now and usually it's just a matter of snagging and compiling alsa-firmware, alsa-libs, and alsa-driver from the site (sometimes alsa-utils too, so it's generally best to do it all, but you can get away with just those three or four).  I've never seen a sound issue that that can't cure.  You have to keep in mind though that alsa-driver has compile switches, such as '--with-cards=hda-intel', which can provide drivers for on-board sound.  So when compiling ALSA it's always good to do an lspci first, find out which family of cards it is, then look over the documentation to find out which compile switches you need.

Hardy Heron will likely solve issues with *this* generation of sound-cards but as that version of ALSA falls behind, people will likely come up against the problem again, needing to compile to a more recent ALSA to obtain drivers for newer cards, and so on.

Possibly the only real solution to this would be to have ALSA drivers updated more frequently, with debs available for all the compile switches.  So the updater could detect the particular compile needed and grab the very latest deb.  That's probably the best way to handle this as I believe it's a vital thing to do.

At the very least they could include a repository--and perhaps one that's disabled by default--that's dedicated to providing the latest drivers, such as ATi, nVidia, ALSA, and others... this would help smooth over the process of moving into Ubuntu, I'd think.

This is just my opinion though and I'm very likely wrong, but all I can do is speak from an anecdotal stance concerning the sound problems I've seen and the only solution I can think of, which is the above one.

---

### Post by bufsabre666 on 2008-01-19
ive never had any sound problems with ubuntu.... ever.... even back in the warty and hoary days, and ive used the dreaded soundblaster live which so many people complain of

---

### Post by ubuntu-freak on 2008-01-19
You're right Praadur. Maybe a wizard could pop up when you first install Ubuntu and ask you if your sound works, resolution works and can be changed to what you know is correct. Something like that. And yeah, a special repo.
 
It's an ugly problem for newbies. Sometimes their sound is switched off by default, that seems odd to me. Why doesn't the boot process switch it on? Then there's compiling to get sound working. Newbies compiling? Jumping into the deep end or what?
 
It's good to throw ideas about this around. 
 
Nathan

---

### Post by Praadur on 2008-01-19
Oh, another fun element I forgot to mention is that a newbie might compile ALSA but the ALSA channels are muted by default, so fiddling with the gnome panel mixer won't result in any sound even if the compile was a success.  There is a warning about this at the end of the compile, but it's not something that an end-user just following instructions is likely to take note of.

Basically, after compiling, one has to call a terminal app named alsamixer and then proceed to unmute each of the channels.

So indeed, some kind of wizard that deals with fetching and properly setting up the latest drivers would be the way to go.  Even though a stable desktop might rely on older technology, drivers are the reverse.  It's almost always better to have the most recent driver in any situation.

-

I'm not really thinking ill of Ubuntu here though as it is my distro of choice and I'd note use anything else, for me it's near perfection.  I just think though that for the end-user, having the step of the drivers.. the most complicated step... sorted out for them will really help.

Oh and I forgot wireless drivers too.  When I first started using Linux, setting those up properly was the bane of my existance as it often involved compiling ndiswrapper, installing Windows drivers via inf files, then running depmod -a, modprobing it and so on.

This isn't a criticism of Ubuntu though but simply a default Linux install in general, any distro really.  Now if there was a command center to manage all this with some level of automation and user-friendly prompts, it'd really help for pulling people who aren't used to Linux into the fold.

If I felt confident enough (which I don't, I greatly lack confidence) then I'd even give this a shot myself...

---

### Post by ubuntu-freak on 2008-01-19
Isn't there a GUI alsamixer too? Think I had it in Debian.
 
Help this kid if you can [http://ubuntuforums.org/showthread.php?t=659206&page=4](http://ubuntuforums.org/showthread.php?t=659206&page=4)
 
He's 15 and wants to be a 'Linux pro'. I think he's a bit down cos his sound wont work. He installed Hardy, which cured his desktop effects problem but not the lack of sound.
 
It was my idea he install Hardy. Bit drastic though. Just the kernel and graphics driver might have enabled effects. Although, he still has windows so it's not too bad.
 
Nathan

---

### Post by marco123 on 2008-01-19
I use the 64bit version, and went back to Feisty after using Gutsy for a while, had too many problems with sound.  Only one program would work at a time?  I have a standard onboard Realtek HD soundcard so nothing fancy.:confused:
For some reason I also get problems with Nautilus after a couple of days, whereas Feisty stays up for months for me, until I'm ready to restart or shutdown. (Going on holidays or whatever.)

---

### Post by ubuntu-freak on 2008-01-19
> **marco123 said:**
> I use the 64bit version, and went back to Feisty after using Gutsy for a while, had too many problems with sound.  Only one program would work at a time?  I have a standard onboard Realtek HD soundcard so nothing fancy.:confused:
For some reason I also get problems with Nautilus after a couple of days, whereas Feisty stays up for months for me, until I'm ready to restart or shutdown. (Going on holidays or whatever.)

 
Yeah I've seen quite a few going back to Fiesty. I would have been smarter telling him to do that. Maybe I should keep my gob shut when I'm not familar with a certain issue eh?
 
Nathan

---

### Post by ~LoKe on 2008-01-19
> **marco123 said:**
> I use the 64bit version, and went back to Feisty after using Gutsy for a while, had too many problems with sound.  Only one program would work at a time?  I have a standard onboard Realtek HD soundcard so nothing fancy.:confused:

That's how ALSA was made.  Only one applications may use the sound device at a time.  This is being corrected* by PulseAudio, which is supposed to be default in Hardy.

*I say corrected simply because PulseAudio does not support s/pdif passthrough, which makes it almost useless for me and others.

---

### Post by ubuntu-freak on 2008-01-19
> **~LoKe said:**
> That's how ALSA was made.  Only one applications may use the sound device at a time.  This is being corrected* by PulseAudio, which is supposed to be default in Hardy.

*I say corrected simply because PulseAudio does not support s/pdif passthrough, which makes it almost useless for me and others.

I've had more than one sound source playing at one time in Gutsy.
 
Nathan

---

### Post by SZF2001 on 2008-01-19
> **bufsabre666 said:**
> ive never had any sound problems with ubuntu.... ever.... even back in the warty and hoary days, and ive used the dreaded soundblaster live which so many people complain of
"Dreaded" ShoundBlaster Live! ? Huh... I've had that card even before Ubuntu (with Debian) and it was NEVER a problem...

> **reassuringlyoffensive said:**
> I've had more than one sound source playing at one time in Gutsy.
 
Nathan
Same here. And in Breezy, Dapper, Feisty, etc.

---

### Post by ubuntu-freak on 2008-01-19
> **SZF2001 said:**
> "Dreaded" ShoundBlaster Live! ? Huh... I've had that card even before Ubuntu (with Debian) and it was NEVER a problem...


Same here. And in Breezy, Dapper, Feisty, etc.


Shoundblaster? That's what James Bond used to shake that bad guys hideout to pieces. 
 
He was thinking of oss. Alsa can play from multiple sources.
 
Nathan

---

### Post by ~LoKe on 2008-01-19
> **reassuringlyoffensive said:**
> I've had more than one sound source playing at one time in Gutsy.
 
Nathan

Not over one device with ALSA.

---

### Post by ubuntu-freak on 2008-01-19
> **~LoKe said:**
> Not over one device with ALSA.

 
Device? I'm talking applications. OSS was limited to one application at a time from what I know.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
Just notice you're a Ubuntu dev! Sweet. I've attracted a dev. Nice one.
 
Nathan

---

### Post by ~LoKe on 2008-01-19
> **reassuringlyoffensive said:**
> Device? I'm talking applications. OSS was limited to one application at a time from what I know.
 
Nathan

In my post, I said it wasn't possible to play more than one sound over the same device using ALSA.  OSS hasn't been default in a long time (well before Feisty), so it's natural to assume he was speaking of ALSA.

And I'm not an Ubuntu dev, I just use a distro in development. ;)

---

### Post by ubuntu-freak on 2008-01-19
Need to get my eyes checked again. Missed the 'user' bit at the end.
 
Nathan

---

### Post by Dreamlocked on 2008-01-19
I also had problems get two programs to share sound.
But then I learned you can add "aoss" in front of each program, and then you can have as many sound-using programs a you want.

Example :
```

aoss skype

```
```

aoss wine <insert name of windows program.exe>

```

It gets tedious to open a terminal and type all that each time you want to launch an app, so I suggest you do quick launch icons of the ones you use the most.

---

### Post by SZF2001 on 2008-01-19
> **reassuringlyoffensive said:**
> Shoundblaster? That's what James Bond used to shake that bad guys hideout to pieces. 
 
He was thinking of oss. Alsa can play from multiple sources.
 
Nathan

Shorry about that, friend. Shay, shhouldn't vwe hawve shome Kool_Aiwde?

---

### Post by ubuntu-freak on 2008-01-19
> **~LoKe said:**
> In my post, I said it wasn't possible to play more than one sound over the same device using ALSA.  OSS hasn't been default in a long time (well before Feisty), so it's natural to assume he was speaking of ALSA.

And I'm not an Ubuntu dev, I just use a distro in development. ;)

 
Yeah but you quoted me and I wasn't talking about devices, just applications. The original poster was talking about applications too. That's why I said he was getting alsa confused with oss.

---

### Post by ~LoKe on 2008-01-19
> **reassuringlyoffensive said:**
> Yeah but you quoted me and I wasn't talking about devices, just applications. The original poster was talking about applications too. That's why I said he was getting alsa confused with oss.

Err...I quoted Marco and mentioned an ALSA limitation, and you quoted **me** and mentioned something else as if you were trying to counter my point... :confused:

---

### Post by ubuntu-freak on 2008-01-19
> **SZF2001 said:**
> Shorry about that, friend. Shay, shhouldn't vwe hawve shome Kool_Aiwde?

 
It's okay :). At least we got some crappy Bond jokes in.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
> **~LoKe said:**
> Err...I quoted Marco and mentioned an ALSA limitation, and you quoted **me** and mentioned something else as if you were trying to counter my point... :confused:

 
Did I? This is getting weird. I am on my phone though. Not a comp. That's my excuse. :)
 
Nathan

---

### Post by conehead77 on 2008-01-19
I had sound problems with Gutsy too (and in Feisty before) and one simple command solved all my problems:
sudo apt-get install linux-backports-modules-generic 

I really dont know what this package does, but it works :)
Does anybody know something about it?

---

### Post by ubuntu-freak on 2008-01-19
Just read them all over again. Did you mean one device on page 1? You said one application, and that's why I said I've had more than one application playing sound.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
> **conehead77 said:**
> I had sound problems with Gutsy too (and in Feisty before) and one simple command solved all my problems:
sudo apt-get install linux-backports-modules-generic 

I really dont know what this package does, but it works :)
Does anybody know something about it?

 
Is it an oldish system? Maybe Ubuntu should be a 2 cd installation eh? A cd of popular apps and helpful apps.
 
Nathan

---

### Post by Bungo Pony on 2008-01-19
Ugh, sound in Ubuntu.

I also have an onboard Realtek sound card, and it has some really nice features like multiple inputs and outputs. It's fantastic for people like me who need lots of those! It works quite well in Windows, but works like crap in Linux. Jack audio control hates it. Gutsy hates it. Pretty much all of Linux hates it. It's pretty sad since I enjoyed using the headphone jack on the front of my PC for my FM transmitter to transmit music all over the house.

You won't believe the solution I came up wit to fix my sound card woes. I installed another sound card in the PC, an old Creative card which works extremely well with Linux. Jack audio control loves it, Gutsy loves it. Although I set the Realtek card as my default, Gutsy decided that it didn't like that, and so it never chooses it.

Now, I have to switch between sound cards to get whatever features I want. I built up a switchbox to direct the inputs and outputs to whatever sound card I'm using. That way, I'm not constantly plugging things in and out. Hey, it works :)

---

### Post by ubuntu-freak on 2008-01-19
> **Bungo Pony said:**
> Ugh, sound in Ubuntu.

I also have an onboard Realtek sound card, and it has some really nice features like multiple inputs and outputs. It's fantastic for people like me who need lots of those! It works quite well in Windows, but works like crap in Linux. Jack audio control hates it. Gutsy hates it. Pretty much all of Linux hates it. It's pretty sad since I enjoyed using the headphone jack on the front of my PC for my FM transmitter to transmit music all over the house.

You won't believe the solution I came up wit to fix my sound card woes. I installed another sound card in the PC, an old Creative card which works extremely well with Linux. Jack audio control loves it, Gutsy loves it. Although I set the Realtek card as my default, Gutsy decided that it didn't like that, and so it never chooses it.

Now, I have to switch between sound cards to get whatever features I want. I built up a switchbox to direct the inputs and outputs to whatever sound card I'm using. That way, I'm not constantly plugging things in and out. Hey, it works :)

 
Well that was creative! Haha me funny...
 
How did it work in Fiesty? Or only used Gutsy?
 
Nathan

---

### Post by ~LoKe on 2008-01-19
> **Bungo Pony said:**
> Ugh, sound in Ubuntu.

Now, I have to switch between sound cards to get whatever features I want. I built up a switchbox to direct the inputs and outputs to whatever sound card I'm using. That way, I'm not constantly plugging things in and out. Hey, it works :)

Check out pulse audio.  It allows you to move a stream onto a different device, or onto multiple devices.  Playback doesn't even skip.

---

### Post by conehead77 on 2008-01-20
> **reassuringlyoffensive said:**
> Is it an oldish system? Maybe Ubuntu should be a 2 cd installation eh? A cd of popular apps and helpful apps.
 
Nathan

After thinking about it, my comp is about 3 years old (P4 Dual Core) with a integrated Intel sound card as far as i can tell.
Maybe its time to replace it somewhen with a 100% Linux compatible box.

---

### Post by ubuntu-freak on 2008-01-20
> **conehead77 said:**
> After thinking about it, my comp is about 3 years old (P4 Dual Core) with a integrated Intel sound card as far as i can tell.
Maybe its time to replace it somewhen with a 100% Linux compatible box.

 
Sef (Ubuntu mod) told me that package can cause problems. He posted another possible fix involving modules
 
[http://ubuntuforums.org/showthread.php?p=4170211#post4170211](http://ubuntuforums.org/showthread.php?p=4170211#post4170211)
 
Nathan

---

### Post by herbster on 2008-01-20
I have an M-Audio Revolution 7.1 card and haven't had any problems once I got my .asoundrc set up, which took some tweaking for sure, but now I can have multiple apps using sound at once, 5.1, 2.0 upmixed to 5 channels, etc.

Last I checked sound in linux is all about the hardware company playing nice with putting out drivers for linux. I had tried a couple Creative cards and a Turtle Beach, then settled on the Revo as the quality is superb and it works great.

---

### Post by HermanAB on 2008-01-20
I have come to the conclusion that very few users have trouble with sound.  It is just that the ones that do sound off a lot about it...

---

### Post by Bungo Pony on 2008-01-20
> **reassuringlyoffensive said:**
> Well that was creative! Haha me funny...
 
How did it work in Fiesty? Or only used Gutsy?
 
Nathan

It actually worked a lot better in Feisty. I could (almost) command which ever sound card I wanted to. It would usually use the onboard, but sometimes it would randomly pick the Creative card when it booted.

I had worse trouble when I used Edgy. When I finally got ANY sound to work, it sounded terrible.

I've been doing a very slow migration over to Ubuntu, and things seem to slowly be getting better. I haven't tinkered much with Gutsy since I'll be moving to Hardy (and staying there) when it finally comes out.

And I may just give Pulse Audio a try.

---

### Post by conehead77 on 2008-01-20
> **reassuringlyoffensive said:**
> Sef (Ubuntu mod) told me that package can cause problems. He posted another possible fix involving modules
 
[http://ubuntuforums.org/showthread.php?p=4170211#post4170211](http://ubuntuforums.org/showthread.php?p=4170211#post4170211)
 
Nathan

Thanks for the link, i bookmarked it in case i get a problem with the current solution.

---

### Post by Xizorbg on 2008-01-20
Hey All-

I have  an M-Audio Revo 7.1 and love it.  Except for 3 main issues:

1)  Sometimes if I launch another app that uses sound (movieplayer, youtube videos) the sound will stop working and I have to do a cold reboot

2)  I cannot control volume from the ubuntu volume control applet.  I am using the PCM (digital) sound out, BTW

3)  I really want to use audacity to edit mp3s for my upcoming wedding slideshow and cannot hear the mp3s play via my PCM


Thanks for any help.

Take care,
X:guitar:

---

