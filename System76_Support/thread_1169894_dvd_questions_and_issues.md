---
title: "dvd questions and issues"
date: 2009-05-25
forum: System76 Support
---

### Post by miniyak on 2009-05-25
i just got my new Pangolin Performance last tuesday and have been having a hard time with some of the "bells and whistles" (hdmi,mic,webcam,ect.). I understand that these are inherent linux issues normally. I just figured System 76 was going to have a lot basic user bug squashing taking care of out of the box. oh well, i guess... ill post the questions and problems individually.

Right now i'm attempting to get the dvd player playing/ripping dvds

when i first fired up the drive it made some god awful sounds then had read error, this has since stoped. a music cd loaded up just fine so i assume it would be the same with other type of cds. dvds are a different matter though.

are dvd movies suppose to work on s76 machines out of the box? 

it seem that everything(extras and such) is install for them to work. but they just wont work for me. i tried vlc, dragon, mplayer with xine, and ripping with handbreak, acidrip. acidrip seemed to be doing something but was taking an absurd amount of time so i stopped it. Am i missing something? i have an external dvd ill try with that and post back

---

### Post by jml on 2009-05-25
No, even with System 76, the computer is not able to play or rip encrypted DVD's.  Most commercial DVD's are encrypted and therefore will not play out of the box.  The decryption codecs are not included because they are not open source, and they are patent encumbered.  

You have two options.  The first time you try to play a DVD, you should get a message stating that you do not have the required codecs and you should be given the opportunity to click on a link to purchase and download a licensed copy of the codecs.

An alternative is to add the Medibuntu repository to your sources list and then download LIBDVDCSS2 and either W32Codecs or W64codecs(depending on what version of Ubuntu you are running.  Be aware that this may be illegal in the area where you live.  

If you need more detailed instructions, search this forum and the WIKI for restricted codecs and you will find more information.

Joe

---

### Post by jdb on 2009-05-25
> **miniyak said:**
> i just got my new Pangolin Performance last tuesday and have been having a hard time with some of the "bells and whistles" (hdmi,mic,webcam,ect.). I understand that these are inherent linux issues normally. I just figured System 76 was going to have a lot basic user bug squashing taking care of out of the box. oh well, i guess... ill post the questions and problems individually.

Right now i'm attempting to get the dvd player playing/ripping dvds

when i first fired up the drive it made some god awful sounds then had read error, this has since stoped. a music cd loaded up just fine so i assume it would be the same with other type of cds. dvds are a different matter though.

are dvd movies suppose to work on s76 machines out of the box? 

it seem that everything(extras and such) is install for them to work. but they just wont work for me. i tried vlc, dragon, mplayer with xine, and ripping with handbreak, acidrip. acidrip seemed to be doing something but was taking an absurd amount of time so i stopped it. Am i missing something? i have an external dvd ill try with that and post back

DVD movies are encrypted & it may not be legal to run unlicensed software to to play them, but this link might help you out: ;)

[http://knowledge76.com/index.php/Installing_Restricted_Formats]("http://knowledge76.com/index.php/Installing_Restricted_Formats") 

jdb

---

### Post by miniyak on 2009-05-25
in the add/remove application it says that the dvd codecs and restricted extras are installed. this is probably because i was prompted to play a wmv file i had. all the missing plugins must have been installed then. unless it only installed the wmv codecs?

i just enabled the medibuntu repositories and installed the appropriate packages as directed in the link provided by jdb, it worked... except everyone looks like their from the blue man group. i just popped in V for Vendetta and Guy Fawkes looks like Papa smurf, everything is an tint of blue! Anybody have an idea as to whats going on?

---

### Post by miniyak on 2009-05-25
the matrix is purple.... this time i tried with vlc. last time was with mplayer, i'll keep trying different programs.

should i reinstall the packages? if so, whats the best way to reinstall? will the same command over write the broken packages?

---

### Post by doas777 on 2009-05-25
easy answer for media playback is to paste this into a terminal :

for 32 bit:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update; sudo apt-get update; sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras mplayer vlc

```

for 64bit:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update; sudo apt-get update; sudo apt-get install libdvdcss2 w64codecs ubuntu-restricted-extras mplayer vlc

```

this will install the medibuntu repositories ( a place for non-free codecs), and the dvd decryption software, and windows codecs. it will also install the ubuntu-restricted-extras package, with flash, acrobat, sun java, etc. there are also a pair of good mediaplayers in there; mplayer, and vlc. if you have trouble with a file, try another player. mplayer is the most robust and will play almost anything, but is a little clunky on the interface.

i'm sure someone else can point out a good ripper. 
good luck

---

### Post by miniyak on 2009-05-26
i just noticed this mourning that my videos in miro are also tinted now...:(

this must be some sort of oddity. i found someone with a similar problem here, "http://ubuntuforums.org/showthread.php?t=1133691" however it seems that the tread has been idle for a few weeks, may be because he called himself a "poopy fingered n00b", but really, im guessing this problem might be uncommon. Has any one else had a similar issue? should i start a new thread for this?

---

### Post by miniyak on 2009-05-26
problem solved! restart computer... turns out im getting a little to used to using ubuntu... lol, another thing besides kernel updates that require restarts i guess.

---

