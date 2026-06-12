---
title: "Spare PC - Cool Uses??"
date: 2006-03-11
forum: The Cafe
---

### Post by ixus_123 on 2006-03-11
I have a spare PC that I am currently using as a web server although setting it up was a learning curve so I'm thinking about doing a fresh install.

I was wondering if people could perhaps suggest some cool uses for this extra PC I have, given that I already have a dual boot WinXP / Ubuntu system to take care of all my desktop needs.

The spec is as follows:

Mini-ITX board with N10000 via processor
512mb ram (32mb to shared video)
160gb hard drive
1 free PCI slot.

*onboard sound doesn't work due to something getting fried when I spilt water over it.  I have no problem adding a cheap PCI sound card if needed.

so far I have been thinking about a LAMP setup to run a Wordpress blog & gallery 2 / 1.5

ftp would be nice

A file server to stream video across my LAN would be cool - possible?  Easy to do?

I have also though about running Giantdisc - or at least trying to & buying a cheap ebay palm [http://www.giantdisc.org/]("http://www.giantdisc.org/")

any suggestions?  Possible problems?  What did / would you do?

---

### Post by Klaidas on 2006-03-11
Hm. I'd run a webserver if I had a spare PC. But you already do that. Hmmm :/
Maybe write a simple program to count number "pi" and do that 24/7 for a week?  \\:D/

---

### Post by Cyfr on 2006-03-11
I had a spare pc so installed gentoo. To try it out.. well i've now got apache running with torrentflux and samba. Samba lets you stream video from the server yes, and I assume it's very easy to setup in ubuntu as it's quite easy in gentoo

---

### Post by welsh_spud on 2006-03-11
MythTV!

---

### Post by beast2k on 2006-03-11
With a 160GB hard drive that PC screams out to be a file server and/or backup server this way when you do your backups there on a completely different PC and safe from all evil during the down time when it's not doing backups it can serve up files and be your firewall. For a firewall you may need a second lan card though but they are only about 20 dollars. I got a spare pc here as well and am wrestling with the same question. As an added bonus doing all this is a great learning tool without screwing up your regular PC setup. Best of luck keep us posted

---

### Post by ixus_123 on 2006-03-11
Yeah, a file / backup server seems like a good idea.  Novell's iFolder looks pretty cool in regard to this
[http://www.ifolder.com/index.php/Main_Page]("http://www.ifolder.com/index.php/Main_Page")

MythTV also looks cool although I only have one PCI slot & no working onboard sound so a TV card wouldn't work(?) unless maybe it was some sort of backend??

both options look sreally cool especially if (perhaps) I can afford an iBook cor duo later in the year (if they are any good & have >1024x768 resolution)

---

### Post by Ghetto_Smurf on 2006-03-11
use it as a backup server OR, if the pc case is small and fits in the living room, plug it to the tv and therefore you have an mp3 system and, with a dvd drive, dvd player!

thta's what i have done to a spare pc, altough it is a server now

---

### Post by bored2k on 2006-03-11
How about making it your own media center?

---

### Post by arctic on 2006-03-11
I use one of my spare pcs for distro-development and bug-testing. Not a bad option for an old box that otherwise serves no real purpose.

---

### Post by ixus_123 on 2006-03-11
[QUOTE=bored2k]How about making it your own media center?[/QUOTE]
what software would you use?

---

### Post by majikstreet on 2006-03-11
[QUOTE=ixus_123]what software would you use?[/QUOTE]
freevo or mythtv

---

### Post by simon_is_learning on 2006-03-11
Maybe upload your music-collection. 
Stream it with Icecast
[http://www.icecast.org/](http://www.icecast.org/)

I would really like to have a backup server myself. 
Someday I will find my perfect spare PC ;)

---

### Post by ssam on 2006-03-11
i use a via epia MII as a jukebox.

i log in with ssh -X from my main computer so that i can run rhythmbox displaying on my main computer, but with all the music store and sound coming out of the via epia. saves having to clog up my network with streaming music.

mine uses a usb iMic as a sound card (better than the built in sound).

let me know if you need more details.

i also use it for testing the developement branch of ubuntu, and trying out other distros.

---

### Post by majikstreet on 2006-03-11
[QUOTE=ssam]i use a via epia MII as a jukebox.

i log in with ssh -X from my main computer so that i can run rhythmbox displaying on my main computer, but with all the music store and sound coming out of the via epia. saves having to clog up my network with streaming music.

mine uses a usb iMic as a sound card (better than the built in sound).

let me know if you need more details.

i also use it for testing the developement branch of ubuntu, and trying out other distros.[/QUOTE]
you have to have xorg on the jukebox right?

---

### Post by Leo_01 on 2006-03-11
Try smooth wall...
it is a linux based firewall...
real sweet.

---

### Post by basketcase on 2006-03-12
IPCop?

---

### Post by basketcase on 2006-03-12
I'm actually waiting on a new case to arrive, where I hope to put a mini-itx board in it.  I'm gonna run D*mn Small Linux on it.

---

### Post by gord on 2006-03-12
spare pc's make great places to put your feet up on

---

### Post by Titus A Duxass on 2006-03-12
Have a play with GiantDisc "www.giantdisc.org"

Everything can be done from command line, and it's a great eduction.

---

### Post by simon_is_learning on 2006-03-12
How about doing all the options mentioned??

a  backup server
a  FTP file server
an Apache PHP/MYSQL webserver
a  movieserver
an audiostreaming server
a IPcop
a samba server


there you go - I solved all your free-time issues for a while.

:-D :-D :-D

---

### Post by ssam on 2006-03-12
[QUOTE=majikstreet]you have to have xorg on the jukebox right?[/QUOTE]

i think you can get away with just xauth now that xorg is modular.

---

### Post by ixus_123 on 2006-03-15
Oh, I like the sound of that & may try it.  I have an iMic under the bed somewhere that I'd totally forgotten about.  Is it just a plug & plaything with Linux or do I have install something to get the imic working?

[QUOTE=ssam]i use a via epia MII as a jukebox.

i log in with ssh -X from my main computer so that i can run rhythmbox displaying on my main computer, but with all the music store and sound coming out of the via epia. saves having to clog up my network with streaming music.

mine uses a usb iMic as a sound card (better than the built in sound).

let me know if you need more details.

i also use it for testing the developement branch of ubuntu, and trying out other distros.[/QUOTE]

---

### Post by joflow on 2006-03-15
How about you combine Asterisk, MisterHouse, MythTV backend, samba, apache, php and tie them all together with some scripts so that you can  make voip phone calls and check your voicemail via a mythTV frontend, watch your TV recordings in windows using samba, automatically dim the lights and close the curtains in your living room when you start a movie via a mythTV frontend.

Additionally, you could write some scripts to create a smart recording feature in mythtv that looks at the shows you record, picks similar shows and records them.  You could also have a script that automatically downloads tv shows via bittorrent.

---

### Post by tribaal on 2006-03-15
You could also consider donate it's computing power to something useful, such as proteins folding research...

Try the following links for extra info:

[BOINC]("http://boinc.berkeley.edu/")
[Rosetta@home]("http://boinc.bakerlab.org/rosetta/")

A binary version of the BOINC client (optimised for Ubuntu) can be found [here]("http://wiki.debian.org/BOINC#Installation"), along with the instructions on how to set it up!

Enjoy!

- Trib'

---

### Post by Netisan on 2006-03-16
Somewhere on the web I noticed an idea to put that spare PC as a hardware router/proxy/firewall. Thus you empower your main PC when using the public network, and additionally establish your own network with all consequent advantages. 
Please, if anybody has experience and/or theoretical comments, answer!
I've got a spare old box too.

---

### Post by ixus_123 on 2006-03-18
They both actually look pretty cool.  I've bookmarked them for now & will read a bit more in depth later - thanks for the links :)

[QUOTE=tribaal]You could also consider donate it's computing power to something useful, such as proteins folding research...

Try the following links for extra info:

[BOINC]("http://boinc.berkeley.edu/")
[Rosetta@home]("http://boinc.bakerlab.org/rosetta/")

A binary version of the BOINC client (optimised for Ubuntu) can be found [here]("http://wiki.debian.org/BOINC#Installation"), along with the instructions on how to set it up!

Enjoy!

- Trib'[/QUOTE]

---

