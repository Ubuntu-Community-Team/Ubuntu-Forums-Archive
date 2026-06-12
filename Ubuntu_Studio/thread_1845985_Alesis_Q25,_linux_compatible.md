---
title: "Alesis Q25, linux compatible?"
date: 2011-09-18
forum: Ubuntu Studio
---

### Post by oscarivera9 on 2011-09-18
I recently purchased an Alesis Q25 USB/MIDI keyboard controller at the local Guitar Center for $39.99.  Usually, what I've done in the past is do my homework to find out if the hardware I'm planning on buying is Linux compatible, but with this one I didn't check compatibility because I bought it spur of the moment to take advantage of the low price (regular price is $180).  With my Windows 7 setup I've been able to use it with various Native Instruments apps (Reaktor 5 especially).  Does anyone know:
1. Is the Alesis Q25 linux compatible?

2. With   what Linux software can I use it?

---

### Post by jejeman on 2011-09-18
1. Plug it and see.
2. Any soft synth For example Phasex.

---

### Post by oscarivera9 on 2011-09-19
> **jejeman said:**
> 1. Plug it and see.
2. Any soft synth For example Phasex.

It's definitely recognized.  I knew that already but I just haven't been able to find software that I can use with it.  I'll try Phasex.  
Thanx

---

### Post by sgx on 2011-09-20
You can use zynaddsubfx, or its updated version, yoshimi.
yoshimi will need a2jmidid installed, and after starting
jackd, issue the command

a2jmidid -j default

this will place a midi connection for yoshimi in the middle
midi tab of qjackctl connection panel. zynaddsubfx will have
it's midi connection in the alsa tab. They use the same sounds,
placed in their respective /usr/share  folders.
World class instruments!

The hydrogen drum machine/sample playback sequencer will receive midi
keyboard input, to supplement beats/sequences you create.
Two gscw kits are on the googlenet, very good percussion.

rakarrack is a great multi-fx app, which all of the above
can be connected to. The three make a great core production trio,
not easily bested, even if spending hundreds of dollars in windows audio apps.
Cheers

---

### Post by oscarivera9 on 2011-09-21
> **sgx said:**
> You can use zynaddsubfx, or its updated version, yoshimi.
yoshimi will need a2jmidid installed, and after starting
jackd, issue the command

a2jmidid -j default

this will place a midi connection for yoshimi in the middle
midi tab of qjackctl connection panel. zynaddsubfx will have
it's midi connection in the alsa tab. They use the same sounds,
placed in their respective /usr/share  folders.
World class instruments!

The hydrogen drum machine/sample playback sequencer will receive midi
keyboard input, to supplement beats/sequences you create.
Two gscw kits are on the googlenet, very good percussion.

rakarrack is a great multi-fx app, which all of the above
can be connected to. The three make a great core production trio,
not easily bested, even if spending hundreds of dollars in windows audio apps.
Cheers

[B][FONT=Palatino Linotype][SIZE=3]
MOST AWESOME!!!!!!!!!!!!!!!!!!!!!!!!!!!![/SIZE][/FONT][/B]

This is exactly what I was looking for!
I suppose it's ok for people to say things like "plug it in" to see if it works.  The thing with me is that if I'm posting something here it's because I've already tried to plug it in and it didn't work which is why I'm asking for help.
On the other hand sgx definitely helped me.  This response was very good and straight to the point.    
Being that I have Ubuntu Studio, I already have everything you suggested I try, so I went down the list.  I started with **zynaddsubfx** and that's all I've tried so far because after messing with it for a while I GOT IT TO WORK!!!  Once it was working, I kind of stayed there for a while trying out all of the different sounds, options, parameters, etc.  
So needless to say, I haven't tried **Yoshimi**, or **Hydrogen**, or anything else for that matter, but at least now I know where to go.  It's late Tuesday night and I must get to bed because I have to play a gig tomorrow but you better believe I'll be trying hydrogen and rackarrack first thing Thursday morning.

Thank you so much for taking the time to help me out.  This is exactly what I was looking for.  Now, I can say for certain that YES the Alesis Q25 definitely IS linux compatible.

---

### Post by sgx on 2011-09-22
[http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date](http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date)

go here and get some extra zynaddsubfx banks

Collection Final
CormiCollection 1.2
laba170 bank1 version2

these hold more than 200 sounds, many of them are excellent

This is another good one, I right-click, and choose 'save as' in my browser:

[http://www.gospel.bo.it/albums/userpics/10222/Adri](http://www.gospel.bo.it/albums/userpics/10222/Adri) ano_Petrosillo_Banks_-_06-Nov-09_tar.gz

as if that is not enough treasure, go here, and get the
unsorted-parameters file:

[http://zynaddsubfx.sourceforge.net/doc/instruments/](http://zynaddsubfx.sourceforge.net/doc/instruments/)

the author donated these!

The 'Files --> Parameters' menu option is used to open the .xmz sound files in the archive. It helps to put a folder named aaaunsortedZYN or similar, containing them, into the

/usr/share/zynaddsubfx/banks

folder, so they always show up atop the file requester.
Lots of great patches and variations in there! You load them individually, using the menu item

'open all parameters' or similar. You can save your multi-timbral
sound masterpieces using the 'save all parameters' menu option.

to go multi-timbral, activate a second sound, by clicking a widget, then in another widget, change it's midi channel from 2, back to one, add a third, and repeat, up to 16, if you have a monster cpu :)

I went through them, and renamed each one, according to my senses,
you may want to do similar, as there are a few world-class sounds!

and Thankyou for the kind words. :guitar:

these all work in yoshimi too, the yoshimi gui is a little different, but some old zyn bugs were fixed.

---

### Post by oscarivera9 on 2011-09-24
sgx, I cannot find the words to thank you!!!  
What a delightful wealth of information.
A real treasure.  
I went from being alone in the dark, to rockin' with lots of great sounds in the sun!!!

Everyone needs a friend like you....thanx again!

---

