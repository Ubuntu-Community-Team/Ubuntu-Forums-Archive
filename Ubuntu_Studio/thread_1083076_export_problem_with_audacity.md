---
title: "export problem with audacity"
date: 2009-02-28
forum: Ubuntu Studio
---

### Post by swdinesh on 2009-02-28
I'm running audacity 1.3.5 on ubuntu intrepid am64.

i'm trying to split a recorded wav file in pieces but when i save in wav or mp3 (i installed lame and /usr/lib/libmp3lame.so.0 form apt-get) the outputs file cannot be played by movie player. If i open them with VLC i hear hal;f second of sound and half second of silence. The only way to hear the file correctly is open and play it with audacity.
Can anyone help me to solve this problem?

Thanks 
Alex

---

### Post by babarosa on 2009-03-01
Hello swdinesh,

if it is a bug in audacity 1.3.5 go to [www.getdeb.net](www.getdeb.net) and download the most recent version for your system (8.10 or 8.04). 

Since March 3rd, it is audacity v1.3.7 for both Hardy Heron and Inusable Ibex ;-)

Greetings,
Michael

Since

---

### Post by cmay on 2009-03-01
> **swdinesh said:**
> I'm running audacity 1.3.5 on ubuntu intrepid am64.

i'm trying to split a recorded wav file in pieces but when i save in wav or mp3 (i installed lame and /usr/lib/libmp3lame.so.0 form apt-get) the outputs file cannot be played by movie player. If i open them with VLC i hear hal;f second of sound and half second of silence. The only way to hear the file correctly is open and play it with audacity.
Can anyone help me to solve this problem?

Thanks 
Alex
what happens if you just open a song from any random album you have in audacity and export it directly with out doing anything to the song.  

i use audacity a lot to make songs out of samples and i never encountered a problem like this before. maybe some settings are off or maybe the tracks you export are muted or lowered volume but it should not affect it this way. 

also when you say split a waw.file in pieces how do you mean exactly. when ever i cut and paste samples togheter and export them as modified samples all media players can play them. this is what i use audacity for the most. simply cut and adapt samples into a few tracks i can work on in my harddisk recorder with real instruments.

 i use samples of drums and export them modified all the time so this problem sounds strange to me. i do not think it has something to do with the codecs. i think it has something to do wiht the settings you are using in preferences in audacity.

---

### Post by swdinesh on 2009-03-02
First of all thenk you both of you for answering to my problem.

@Michael: i use the 1.3.5 as apt-get installed it. I try to upgrade to another version for my "Inusable Ibex"!

@cmay: I also use audacity on windows and now on linux i thios is the first time i have a problem.
I have some wav files of recorded lessons from my teacher. Each track is a mix of introduction, lesson, question with moment of silence. I extract the 3 sections (with copy form the original track and paste in a new track). 
Today i tried to do as you suggested me: the wav export is ok the mp3 export is not working (1/2 sec of sound and 1/2 sec of blank, and so on).
the input track is: Rate 8000 Hz, sample format 32bit-float. I export as mp3 at 56kbps constant rate (the lowest bitrate available). I'm wrong with this settings? 
ps.: cutting the first piece of track the wav export is still ok.

Thanks 
Alex

---

### Post by cmay on 2009-03-03
> **swdinesh said:**
> First of all thenk you both of you for answering to my problem.

@Michael: i use the 1.3.5 as apt-get installed it. I try to upgrade to another version for my "Inusable Ibex"!

@cmay: I also use audacity on windows and now on linux i thios is the first time i have a problem.
I have some wav files of recorded lessons from my teacher. Each track is a mix of introduction, lesson, question with moment of silence. I extract the 3 sections (with copy form the original track and paste in a new track). 
Today i tried to do as you suggested me: the wav export is ok the mp3 export is not working (1/2 sec of sound and 1/2 sec of blank, and so on).
the input track is: Rate 8000 Hz, sample format 32bit-float. I export as mp3 at 56kbps constant rate (the lowest bitrate available). I'm wrong with this settings? 
ps.: cutting the first piece of track the wav export is still ok.

Thanks 
Alex

i am not sure as i never use the mp3 format myself. always use waw and ogg.
 but i think it sounds like the codecs that should be used are to blame for this.  
can you look up somewhere what codecs audacity needs for mp3 export. 
if these things are installed and working fine in other programs than audacity it sounds kinda buggy to me.

---

### Post by swdinesh on 2009-03-04
@cmay: you gave me a good idea: i exported the sound in ogg vorbis and it worked. So the problem is in the lame codec and not in audacity. Unfortunately i need these files in mp3. I think i'm using wrong parameters to configure the lame-codec. 
Alex

---

