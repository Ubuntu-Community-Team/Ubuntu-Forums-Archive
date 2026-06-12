---
title: "I HAVE to program an open-source software, what do you need?"
date: 2009-05-09
forum: The Cafe
---

### Post by Gucko on 2009-05-09
Hi guys, I'm a computer engineering student and I have a project this semester i.e seminar.
Each group has to do a software. I'm not in a group and I want to do a project individually.

I just was wondering what does the open source community need? I'm collecting opinions so please give me what you need or what you miss.

Please consider that I'm alone in this project so I really don't have a lot of time to do a big project. The professor wants  us to do a complete project as if we were working in a software company. That means we have to question people, collect feedback, model the software in UML, start coding, document the code and then document the software.....so I will do all these stuff alone :)

As I said I don't want a big project cuz as you saw I have plenty of work to do by my self ;)

I did some research and found that we miss a STANDARD address book software. I want to create a standard address book that has booth Desktop environment and web environment. So you can add your contacts offline on your desktop or on the software website. After that if you want you can sync your contacts in your PC with the website. The address book supports vCards and CSV.

What I mean by standard is that you add your contacts only once. I really found that Evelution's export capability for contacts is weak cuz it doesn't make a good vCard. Same thing with Hotmail for example, when I exported my contacts and imported them using Evolution or Thunderbird, it was all wrong!
I had to rewrite my contacts again for evolution and I don't really know if Thunderbird can understand Evelution's vCards!

I think this is a good project for me and for the community. If you have other better ideas, please tell me.:guitar:

---

### Post by lykwydchykyn on 2009-05-09
Just an observation, your idea is good from the standpoint of need, but establishing a standard for all email/PIM applications is a little ambitious for a school project.

Someone mentioned on here the other day wanting a dictionary program where you could just click any word on the screen and get a definition.  Seems like that would be easy to do if you leveraged dictd as a backend.

---

### Post by t0p on 2009-05-09
Good thing about open source is that you can freely adapt the open source software released by someone else.  Just remember to keep an eye on licensing - both for your own software and that of the software you've stolen^H^H^H^H^H^Hadapted.

---

### Post by HavocXphere on 2009-05-09
Make 100% sure you pick something you can complete.

Lecturers will not be impressed by a half-finished bug-fest.

It needs to look clean & work flawlessly. *Then* you can start adding fancy things if you've got time left.

I'd suggest you pick something that is visual & easy to demonstrate. e.g. a visual representation of the filesystem...like filelight. Perhaps 3D?

---

### Post by gnomeuser on 2009-05-09
if you want to do your contacts project look at "contacts" for your base.

Aside that I would like to see improved handling of downloads in Banshee including finishing the support for monotorrent-dbus to allow for torrent downloads.

UML in Monodevelop would be nice as well.

lots of little ideas, mostly I think we need to finish off functionality not build entirely new software.

---

### Post by TheLions on 2009-05-09
suggestion:
~ make a powerful, simple glossy calculator with natural fraction display
(see Casio FX-991)
~ a iCal calendar viewer/organizer
~ Rhytbox plugin for listening Shoutcast audio (see Amaroks Internet radio)
~ Wizard for creating Debian packages

also check Ubuntu brainstorm for more programs requests:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Corelogik on 2009-05-09
Personally I would like a Linux native version of something like Visual Hub. It uses ffmpeg and mencoder and has presets for just about anything, iTunes, iPhone, PSP, DV, DVD, AVI MP4, WMV etc,.. you drag your video into the window, select format to output to, and click start. It outputs the files in the right format/size without the user having to adjust anything,... something like that, a one or two click video transcoder would be awesome.

If there is already something like this, ignore me. Also if something like this does exist, can someone point me to where I can find it.

Or,

Something like Nicecast, [http://rogueamoeba.com/nicecast/](http://rogueamoeba.com/nicecast/), that will let you broadcast from one of the Linux audio players to a shoutcast stream would be awesome too.

---

### Post by monsterstack on 2009-05-09
> **t0p said:**
> Good thing about open source is that you can freely adapt the open source software released by someone else.  Just remember to keep an eye on licensing - both for your own software and that of the software you've stolen^H^H^H^H^H^Hadapted.

Yes. Make sure you go for GPL-licensed stuff, which can't be stolen, simply by virtue of being GPL'd. That is unless you rip off the source without attribution and distribute it as a proprietary app.

---

### Post by LightB on 2009-05-09
hah, yeah right, how about a decent mplayer gui for a change? You could fork gnome-mplayer.

---

### Post by LightB on 2009-05-09
> **Corelogik said:**
> Personally I would like a Linux native version of something like Visual Hub. It uses ffmpeg and mencoder and has presets for just about anything, iTunes, iPhone, PSP, DV, DVD, AVI MP4, WMV etc,.. you drag your video into the window, select format to output to, and click start. It outputs the files in the right format/size without the user having to adjust anything,... something like that, a one or two click video transcoder would be awesome.

Yes, this sounds good, too; too good to be true, that is. Especially considering that it would most likely be based on mencoder or ffmpeg, and those are in constant flux.

---

### Post by hobo14 on 2009-05-09
A GUI frontend to change webcam settings: gamma, brightness, colour etc.

And a test view that updates according to the settings in real time.

---

### Post by Brian B. on 2009-05-09
> **TheLions said:**
> suggestion:
~ make a powerful, simple glossy calculator with natural fraction display
(see Casio FX-991)


I second this, but rather than reinvent one, try to make the best free graphing calculator currently available easy to install for Ubuntu. I can't figure it out. 

[http://www.graphcalc.com/](http://www.graphcalc.com/)

Thanks.

---

### Post by Polygon on 2009-05-09
> **LightB said:**
> hah, yeah right, how about a decent mplayer gui for a change? You could fork gnome-mplayer.

smplayer is already a great GUI for mplayer, but it is in qt.

---

### Post by ubuntu27 on 2009-05-09
I wish there was an [Off-the-Record Messaging]("http://www.cypherpunks.ca/otr/") plugins for [aMSN]("http://www.amsn-project.net/")

---

### Post by mangar on 2009-05-09
1. A tag editor that can use Amazon's database (like tag and rename for windows), including album art and lyrics.

2. Integrate Meld (diff viewer) with Nautilus (there's a plugin called Meld-ext, but it's broken).

3. fix koctave, update to support octave 3.

4. port Basket to qt4.

5. Programmer's calculator, allows for bit-wise calculations, per bit setting (so you'll be able to set what bits the number mask), hex functions, etc.

---

### Post by Corelogik on 2009-05-09
> **LightB said:**
> Yes, this sounds good, too; too good to be true, that is. Especially considering that it would most likely be based on mencoder or ffmpeg, and those are in constant flux.

Well, VisualHub did it for Mac OS X, unfortunately, the developer is no longer developing it. [http://www.techspansion.com/](http://www.techspansion.com/)

Since it's based on 'Nix tools, I can't imagine a similar GUI would be too hard to craft for it for Linux. I imagine someone did it, and ported a Mac and maybe a Windows version, you might even be able to make a few bucks too. People were paying $39.95 for the OS X version before they quit development.

Wish I was a programmer, I'd definitely take something like that on.

---

### Post by Vostrocity on 2009-05-09
Hey I'm doing a big end-of-year CS project too! But I'm only in AP CS A (first year Java) so big for me is Space Invaders or Pac-Man or something. :)

About your original idea, [Google Contacts plus Thunderbird]("http://lifehacker.com/5101498/google-contacts-syncs-your-google-address-book-with-thunderbird") works pretty well imo. Alternatively there's [GcalDaemon]("http://lifehacker.com/software/google-calendar/geek-to-live--sync-google-calendar-and-gmail-contacts-to-your-desktop-251279.php"). Just as a school project, I think your idea's fine but not if you actually want people to use your service instead of Google's. :|


> **lykwydchykyn said:**
> 
Someone mentioned on here the other day wanting a dictionary program where you could just click any word on the screen and get a definition.  Seems like that would be easy to do if you leveraged dictd as a backend.
I second that idea. Kinda like the Answers.com extention for FF but hopefully slicker and system-wide.


> **TheLions said:**
> suggestion:
~ make a powerful, simple glossy calculator with natural fraction display
(see Casio FX-991)
~ a iCal calendar viewer/organizer

~ Lol glossy. I find entering fractions in line a lot neater and 
copypasteable. :)
~ iCal!? What's so great about that? Sunbird/Gcal ftw!


> **mangar said:**
> 1. A tag editor that can use Amazon's database (like tag and rename for windows), including album art and lyrics.

Why use the Amazon db?

---

### Post by dspari1 on 2009-05-09
I need better midi integration with Linux. Timidity by default has many missing instruments and doesn't sound very good.

To get midi working properly, users have to go through this:
[https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

Another problem is that there is no proper midi plugin for Firefox, so websites that uses midi have to use Timidity through mozplugger. Visit [www.livio.com](www.livio.com) to see what I mean.

BTW, thank you very much for offering yourself to the community.

---

### Post by days_of_ruin on 2009-05-09
> **HavocXphere said:**
> Make 100% sure you pick something you can complete.

Lecturers will not be impressed by a half-finished bug-fest.

It needs to look clean & work flawlessly. *Then* you can start adding fancy things if you've got time left.

I'd suggest you pick something that is visual & easy to demonstrate. e.g. a visual representation of the filesystem...like filelight. Perhaps 3D?

Maybe a simple cover-flow file manager. It would look cool:D
Easiest way would be to use clutter.[http://www.clutter-project.org/]("http://www.clutter-project.org/")

---

### Post by Vostrocity on 2009-05-09
> **Corelogik said:**
> Personally I would like a Linux native version of something like Visual Hub. It uses ffmpeg and mencoder and has presets for just about anything, iTunes, iPhone, PSP, DV, DVD, AVI MP4, WMV etc,.. you drag your video into the window, select format to output to, and click start. It outputs the files in the right format/size without the user having to adjust anything,... something like that, a one or two click video transcoder would be awesome.

If there is already something like this, ignore me. Also if something like this does exist, can someone point me to where I can find it.

Or,

Something like Nicecast, [http://rogueamoeba.com/nicecast/](http://rogueamoeba.com/nicecast/), that will let you broadcast from one of the Linux audio players to a shoutcast stream would be awesome too.

Have you looked at HandBrake? It's got all the presets you mentioned and it can rip DVDs. :)
[IMG]http://trac.handbrake.fr/raw-attachment/wiki/BuiltInPresets/bitrate-graph.png[/IMG]

Nicecast would be a nice thing to have though.

---

### Post by monsterstack on 2009-05-09
I'd love a functional-programming scripting environment. Or more simply, a spreadsheet application, with some extra tweaks.

Each cell could be programmed not just with simple formulae, but with fully-fledged scripts. Once you're done editing the contents of the cell, it collapses back to whatever value it computes.

Compare the readability of

```
def compute(a,b,c,x):
   step1 = sin(a)/tan(b)
   step2 = sin(b)/tan(c)
   step3 = abs(step1 - step2)
   if step3 > x:
     result = atan(pow(step3,2))
   else:
     result = atan(pow(step3,3))
   return result
```

with

```
=IF(ABS((SIN(A1)/TAN(B1))-(SIN(B1)/TAN(C1))))>3;ATAN(POW,(ABS((SIN(A1)/TAN(B1))-(SIN(B1)/TAN(C1)))),2);ATAN(POW,(ABS((SIN(A1)/TAN(B1))-(SIN(B1)/TAN(C1)))),3))
```

I do lots of mathematical stuff and I mostly use python to do it because I find it is easier to express ideas there than it is in spreadsheet applications. Maybe I'm talking nonsense, who knows.

---

### Post by Corelogik on 2009-05-10
> **Vostrocity said:**
> Have you looked at HandBrake? It's got all the presets you mentioned and it can rip DVDs. :)
[IMG]http://trac.handbrake.fr/raw-attachment/wiki/BuiltInPresets/bitrate-graph.png[/IMG]

Nicecast would be a nice thing to have though.

They don't have a version with all the cool new stuff for ppc. Maybe when I switch to Ubuntu in a couple months I'll have another look.

---

### Post by Vostrocity on 2009-05-10
@monsterstack
That's actually a good idea. Is there anything like that so far for other platforms or did you come up with that idea yourself?

@Corelogik
Lol didn't know you weren't on Ubuntu.

---

### Post by monsterstack on 2009-05-10
> **Vostrocity said:**
> @monsterstack
That's actually a good idea. Is there anything like that so far for other platforms or did you come up with that idea yourself?


It just occurred to me one day whilst struggling with a spreadhseet somebody had sent me. I have no idea if anything like that exists already. I should probably look into it.

---

### Post by Corelogik on 2009-05-10
> **Vostrocity said:**
> @monsterstack
That's actually a good idea. Is there anything like that so far for other platforms or did you come up with that idea yourself?

@Corelogik
Lol didn't know you weren't on Ubuntu.


NP, I'm working on it,. need to finish the fund savings to buy some new hardware.  I have the disc's downloaded and burned, waiting,..

---

### Post by MaxIBoy on 2009-05-10
Well, this was something I was planning to do, but I wouldn't mind if someone beat me to it: A kernel filesystem driver for the Git software. Let's call it "GitFS."

Kernel filesystem drivers aren't hard to make, as long as there isn't actually a filesystem. In this case, you're not mucking around with ones and zeroes on a disk. I found a little tutorial on the subject a while back: [http://inglorion.net/documents/tutorials/tutorfs/](http://inglorion.net/documents/tutorials/tutorfs/)

In this example, the driver you write will be asked to write a file to the disk, and it'll be able to do so with fwrite or whatever. Then, you call some external programs (the git software,) and you're done.

The Git Version Control System software is also not hard to use. The documentation is easy to understand, and can be found here: [http://git-scm.com/documentation](http://git-scm.com/documentation)


So, here's an example of how this would go down:

[LIST]
[*]Create an empty directory called ~/example.
[*]In the command line, run "git init && git add ." in the directory to create a git project.
[*]Everything past this step will have to be programmed by you.
[*]Then run "sudo gitFS new" in the directory to create a new "disk" formatted with gitFS. Since this is our first gitFS filesystem ever, the disk will be called /dev/gitfsa. If this had been our second, it would have been called /dev/gitfsb. Sort of like /dev/hda is the first IDE drive and /dev/hdb is the second IDE drive.
[*]You can then "mount /dev/gitfsa -t gitfs /whatever/you/want/the/mount/point/to/be" to bring our kernel driver online.
[*]Every time you change something in the directory "/mount/point," the Linux kernel runs the kernel driver, saying, "hey, could you write this data to that disk for me?" The kernel driver simply writes your files to the directory the way you'd write any other file, and does a "git commit." Heck, you could probably do all the actual work in a shell script and it would be easier (don't.) If you wanted to get fancy, you could take the name of the program modifying the file, and use it as the update description.
[*]Now, you can go back to ~/example and look at your history.
[/LIST]


Now what would this be for? Simple. It turns your ordinary filesystem into a versioning filesysem (like VMS,) so even if you accidentally overwrite an important file with garbage, you can still go into the changelog and check-out the old version you need. 

Alternately, you could say that it does all the "git commit" stuff automatically so you don't have to remember to run that every time.



Probably doable by one person. I know I could do it, if I had the time. But if someone else could get it done sooner, that'd be great, because I really want to have this functionality.

---

### Post by Gucko on 2009-05-11
Thanks for all your ideas but I'm going to do the address book because it suits me. 
What features do you suggest?

---

