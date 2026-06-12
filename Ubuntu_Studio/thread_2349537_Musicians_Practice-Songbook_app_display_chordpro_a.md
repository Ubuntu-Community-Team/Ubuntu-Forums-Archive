---
title: "Musicians Practice-Songbook app display chordpro and play mp3"
date: 2017-01-15
forum: Ubuntu Studio
---

### Post by vector on 2017-01-15
Hi all,
I play, fill in on bass, for a couple of bands and till now have been 3ring binder . But nowadays I find not everyone is on the same page, with transposition being a common problem.

I read TAB or CAL(chords above lyrics-two line format) and have most of my songs in doc format or pdf. I've been a bit slow to convert to digital.
Last week I had the opp to use a tablet with onSong ok I'm sold..well not quite, can't afford the iPad just for that. I found a lesser version for android  (the chordinator) and stole the wife's samsung tablet.
Hmm this could work.

What I think need/would like:
Verification this is the way to go?
Some app on Ubuntu studio that will allow me to batch convert the numerous docs and docx I have (i used that because not everyone I play for uses linux) into chordpro format.
       I might have to batch convert the docs to text first and then text to chordpro.

An app that will run on my Ubuntu PC that will:
       Read chordpro files and display them on screen as CAL with autoscroll  so I can practice
       Play or trigger the playing of an mp3 file(which i have created to play along with)
       Create a set list which auto displays the next song and triggers the next mp3 so I can just play thru the whole set list.

For practice, I currently have a media player playlist running with auto increment song and have to quickly jump onto my file manager and dble click the next pdf.


any thoughts on how and if any of this is available/possible?

---

### Post by Bucky Ball on 2017-01-15
Perhaps [this could get you started]("https://sourceforge.net/projects/tuxguitar/")? It is in the repositories I think so check there. Shouldn't need to download from elsewhere. 

Not sure it will do everything you're after, but might ease the burden.

---

### Post by vector on 2017-01-16
thanks but tuxguitar does not support chordpro.
I probably should have highlighted this ***Read chordpro files and display them on screen as CAL with autoscroll so I can practice***. Alot of the guys in the various bands use ipads and othe devices etc and have settled on chordpro as the most common simple export or importable format for everyone. Having read a fair bit on the web they seem to be right. But surprisingly linux seems to have little in the way of auto scrolling viewers.

---

### Post by vector on 2017-01-18
hey guys HELP,
this is driving me nuts.
chordpro, chordii,chord,chopro, pro whatever you want to call it is a simple markup language and every other platform I know of has apps to cater for it.
Windows,android,iPad have Songbook, chordinator, Onsong etc. I found songpress for linux which looks perfect but can't get it to build from source or run(yes even under wine) Just not smart enough to understand the program errors.

I just need something to read chordpro files, create a playlist and display them on my screen(as two line chords above lyrics) so I can practice..auto scroll would be nice.

maj also worked running under wine but the playlist would not create

please,,pulling my hair out here

---

### Post by igdfpm on 2017-01-18
I just had a quick look at songpress and couldn't get it to run... without a thorough packaging and patching job I don't think anyone will either... my general thinking with "unknown" applications is that if no-one has packaged it for the Arch Linux AUR then it is either seriously broken or not worth the effort ;)

Chordpro can export midi files - Tuxguitar can import midi files... job done?

---

### Post by vector on 2017-01-18
thanks for taking a look for me

I have managed to contact the author maybe we can get it sorted out. Would be a great boon to the linux community to have our own version of Songbook,OnSong

chordii may well export midi but its not what Im really after. I might have a word with tuxguitar to see if they are still active and can make an import filter. But tuxguitar does not support song lists etc either. 
Unfortunately I have a lot of songs to process

---

### Post by Bucky Ball on 2017-01-18
Your other option is to install Windows as a virtual machine in Virtualbox in Ubuntu. Not *exactly* what you are looking for, but means you don't need to boot out of Ubuntu to run your app.

I've only ever used Sibelius for anything serious and don't think that will ever be coming to Linux so have had a Windows install hanging about somewhere for that and some other pro audio apps for nearly a decade. There is nothing that comes close to Sibelius in Linux (IMHO) and sometimes that's just the way it is, but good luck. ;)

PS: The only obstacle to the virtual machine approach is the power of the machine. Plenty of RAM is required as the two OSs split the RAM. The host and client need some each, so if you have 4Gb, consider it 2Gb per OS.

---

