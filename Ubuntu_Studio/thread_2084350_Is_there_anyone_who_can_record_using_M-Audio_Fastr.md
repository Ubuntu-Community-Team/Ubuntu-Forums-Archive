---
title: "Is there anyone who can record using M-Audio Fastrak Pro?"
date: 2012-11-15
forum: Ubuntu Studio
---

### Post by Gnocco Di Gomma on 2012-11-15
I' m new about Linux and I'm trying Ubuntustudio. I have a Fastrack pro sound card and I was very happy when, for 35 seconds, I was able to record using Ardour and Jack.
After then I made a lot of tries without any result. I searched the forum, but I'm not able to find a post which shows how to solve my problem. 
On the contrary, I found a lot of persons writing that my sound card is not fully supported in Ubuntu and this is the reason why I can't record my music (by the way: I can hear music).  
As these posts are not so recent, my question is: 
Have I to make a choose between 
-1- change tha card to use Ubuntustudio 
-2- go back to windows to use the card?
Thank a lot to whom will spend his time to answer me.
(Excuse my bad english)

---

### Post by Gnocco Di Gomma on 2012-11-16
No one in the forum using this device?

---

### Post by Gnocco Di Gomma on 2012-11-19
No answers is an answer.
Thanks to everibody.

---

### Post by d_in_Conduct on 2012-11-20
I spent several days trying to get my Fastrak Pro to work, but it's been a couple of years.  I'll have to look again.

There's a lot of information available through Google.  If you check out
[http://joegiampaoli.blogspot.mx/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.mx/2011/06/m-audio-fast-track-pro-for-debian-linux.html) a ton of information, probably more than you can use.

It looks like there are better Linux distros available for the Fastrak Pro.

---

### Post by AstroLlama on 2012-11-20
when I was running Precise Pangolin my fast track pro worked out of the box on my toshiba laptop. If it worked for the first 30 seconds then it will work again, that's for sure.

EDIT: my mistake I had an M-Audio mobile pre...

Interesting link, I guess I will stay away from the fast track. That's disappointing M Audio makes nice products.

---

### Post by SwedO on 2012-11-21
Hi!

I'm using Fast Track Pro without problems in 12.04. Did you set the right input and output devices in Jack? "USB Audio #1" for input, and "USB Audio" for output.

Good luck!
/Ove

---

### Post by Gnocco Di Gomma on 2012-11-21
Thank you. 
I don't want to go back to windows, because those 35 seconds recording in Ardour were my best experience in recording. 
If you know some better distros, please, let me know how to achieve it.
Thank you mr. SwedO:  yes i have the same settings you wrote. 
From speakers i can hear tracks i have imported and the sound of what i am trying to record, but ardour does not record. 
I read and followed the instructions in ardour's manual, but - as i said - only once it worked. 
Have you any idea? 
Thanks

---

### Post by SwedO on 2012-11-21
You say you hear what you are trying to record. Do you hear your voice through the speakers when talking into the mic?

---

### Post by Gnocco Di Gomma on 2012-11-21
Yes, i can hear my voice, but i don't see vumeters moving in ardour mixer when i set them to "input" and nothing is recorded in the track

---

### Post by SwedO on 2012-11-21
Then I guess it's not a Fast Track Pro-problem...

Have you set the input for the track correctly? system:capture_1 (or 2)

---

### Post by Gnocco Di Gomma on 2012-11-21
I think you are right: this looks to be a problem in ardour or jack.
Yes, i did. I'm trying to record 2 mono tracks: voice and guitar.
In ardour i have 2 tracks that i imported and 2 new tracks i added and armed for recording.
In the ardour mixer window i assigned to these new tracks the input: system:capture_1 in one track and system:capture_2 in the other.
In jack i checked the connections and everything seems to be ok (for what i can understand). 
Capture_1 connects to audio1/in1
Capture_2 connects to audio2/in1
Audio1/out1 connects to master/in1 (Audio1/out2 to master/in2)
master/out 1 and 2 connect to playback_1 and _2.
At my eyes everything is well connected, but i guess it is not so.

---

### Post by SwedO on 2012-11-21
Hm, that's weird. Everything seems right to me.

Is your card always turned on? If yes - restart it. A longshot...

You could try a live-version of "Av Linux" [http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

---

### Post by Gnocco Di Gomma on 2012-11-21
Hi, mr. SwedO, 
my pc went sleeping during a short my absence and when i came back jack crashed. 
(I've read in the forum that such a things happened to other persons too).
Well, i quit jack and ardour and turned off the sound card. Immediately the machine  freezed and no way to close the system. So i turned it off. 
When restarting (while audio card off), after the bios, i got a kind of windows "blue screen" with a different color. So i had to turn off again. 
At the next boot i saw on the screen something like the following "HDIO_GET_IDENTITY failed for 'dev/sdc' " (maybe i missed something in the last part of the message).
By the way: as i've never used the internal sound card i deactivated it in the bios, so in this boot there were no sound card in the system. Could this create a problem?
Finally i tried to record, but nothing has changed. 
I'm checking the link to AV Linux that you sent. 
Thank you a lot.

---

### Post by Gnocco Di Gomma on 2012-11-23
Well, i tested AVlinux and everything is OK. I can play and i can record with Fast Track Pro.
I did not install AVlinux, i just boot it from CD.
Now, if someone is still reading this thread, the easy solution of the problem is to say that ubuntu studio can t work as well as AVlinux, but i am not sure about that.

I should like to understand what, in QjackCtl, server means and what is the difference between Jackd, jackstart, Jackdmp etc. 
I write this because i think that, when i use ubuntu studio, I save a Jack setup somewhere when i close, but i don t get it again on the next start. This can t happen in AVlinux because it stays on a CD.

---

### Post by jejeman on 2012-11-24
>  I should like to understand what, in QjackCtl, server means and what is the difference between Jackd, jackstart, Jackdmp etc. JACK is a sound server, that is what server means.
From the man page:
> jackd - JACK Audio Connection Kit sound server
 jackd  is  the  JACK  audio  server daemon, a low-latency audio server.
I dont know what jackstart is, there is no such executable on my system, Jackdmp is another name for JACK2. If you look carefully you can see
jack d mp = JACK daemon multi-processor
but the actual daemon name is the same for JACK1 and JACK2 = jackd
> the easy solution of the problem is to say that ubuntu studio can t work as well as AVlinux,  Yes, AVlinux performes better than Ubuntu studio. It's great for laptops and older desktops. But, you can probably optimise US to work as AVl.
For starters lighter DE, lesser services, JACK1, 32bit.
Also AVl uses different kernel than US, maybe there are some optimisations in there too.

---

### Post by Gnocco Di Gomma on 2012-11-24
Thank you mr. jejeman.
For my purposes and, overall, for my very old machine AVl is good enough to let XP die, which is my goal.
So thanks again to all of you.

---

### Post by solarbird on 2013-03-24
Hi! Much, much later, I find this thread. I recorded my entire first album on exactly this device, under Ubuntu, in Ardour+Jack. So, yeah, it can be done!

( [http://music.crimeandtheforcesofevil.com]("http://music.crimeandtheforcesofevil.com/album/****-tracy-must-die") if you're curious - **** Tracy Must Die. Which I see the forum censors because it doesn't know that's a _name_. Duck Tracy, only an I, not a U. Anyway, I play a lot of instruments, it's all multitracked.)

While I'm not using it regularly anymore, I have a working jackd config file for this device if you want it.

---

