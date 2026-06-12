---
title: "Jack and BruteFIR - need help to route audio from player to BruteFIR"
date: 2010-12-06
forum: Ubuntu Studio
---

### Post by Shefffield on 2010-12-06
Cheers,

I'm trying to get my convolving PC to play music files from its hard disk via BruteFIR. For easier routing I've settled on Jack, but there is no documentation availbale for either BruteFIR nor Jack on how to get it to work.

As far as I understand it the crucial pont lies in the BruteFIR configuration file. [http://www.ludd.luth.se/~torger/brutefir.html#config_4]("http://www.ludd.luth.se/%7Etorger/brutefir.html#config_4")

So far I only managed on an other machine to use ALSA to receive audio data from an external ADC, pass it over to BruteFIR and push it out agan into an external DAC. 

Can anybody point me to a solution on how to play and convolve on the same host?

Thanks in advance,
Axel

---

### Post by martinward on 2010-12-12
Hi
 
I am a linux newbie and on the same journey - seeking to build a pc to store music which can then be played and filtered through Brutefir before passing to amps for each speaker unit. I have yet to get it working properly but have made some significant progress which may help you. This is my progress to-date:
 
1 I have installed Zorin OS3 to get to know linux. However have now installed KDE, which I prefer, so I guess I am running a form of Kubuntu. So the kernel is an up-to-date Ubuntu one.
 
2 Next came Jack audio. There are a couple of very good youtube vids which show you how to prepare for realtime audio and set up Jack. These are:
 
[http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related](http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related) and
 
[http://www.youtube.com/watch?v=fMz6fDGBnA4](http://www.youtube.com/watch?v=fMz6fDGBnA4)
 
I have managed to setup Jack but cannot get it to run in realtime - it crashes. This is where I am concentrating my efforts. I won't comment more about Jack as these tutorials are very informative except to say that I am using the Audacious player with the Jack plugin selected. I also have Patchage installed which shows the connections through Jack visually.
 
3 Now to brutefir. I have managed to get this working by playing a file direct to alsa but cannot get it to connect to Jack. I guess this is because it isnt running in realtime!! I am starting brutefir with the following command (doubt this is the best)
sudo brutefir -nodefault /home/mypath/myconfigfile
 
There are a couple of examples of brutefir configs which use Jack for routing. These are shon at the bottom of:
 
[http://www.duffroomcorrection.com/wiki/Brutefir](http://www.duffroomcorrection.com/wiki/Brutefir)
 
I understand that there has been a change in port nomenclature so refernces to "alsa_pcm" need to be changed to "system". You can see a list of your Jackd ports by typing Jack_lsp into your terminal.
 
When I have solved the realtime and porting issues I plan to look into how to control Jack and Brutefir via perl scripts. I am hoping to be able to address volume control and sample rate changes. Very excited that I have got Brutefir to work on a test file but not sure how to fix Jack. Maybe a less bloated form a linux is the way to go....
 
Happy to help further if I can and also interested in your journey.
 
Regards
 
Martin

---

### Post by cchhrriiss121212 on 2010-12-12
I have no ideas on BruteFIR or what it is used for, but I know that jack will only work with apps specifically designed for it. 

You can get ALSA to go through jack [like this]("http://ubuntuforums.org/showpost.php?p=9344940&postcount=6"), but from the looks of it you don't really need jack at all.

---

### Post by Pablo_F on 2010-12-12
I suggest jconvolver instead of brutefir. It is a jack-aware convolution engine. 

See [http://ubuntuforums.org/showthread.php?t=1623984&highlight=jconvolver](http://ubuntuforums.org/showthread.php?t=1623984&highlight=jconvolver)

Cheers, Pablo

---

### Post by martinward on 2010-12-13
As a linux newbie I am feeling quite chuffed to now have a working prototype system running Alsa player through Brutefir on Jack audio. I still have a lot to learn but at least I have a working system and can start to work on the next phase, sorting out the filters and controlling Brutefir and Jack through Perl. To help others this is what I have done to get to this stage:
 
1 Install latest version of Ubuntu
2 Install Jack - see reference to previous post for reference to youtube vids which I followed.
3 Install Brutefir via Synaptic
4 Install Patchage via Synaptic
5 Install alsaplayer via Synaptic
6 To enable both Jack and Brutefir to run without sudo modify the sudoers file as follows:
 
visudo -f /etc/sudoers
then add the following lines and save
jackd ALL=(ALL) ALL
brutefir ALL=(ALL) ALL
 
7 after a reboot (not sure if this is necessary) I then started Jack Control which is a gui for Jackd. I then made the settings recommended by the youtube vids from previous post and was pleased to see Jack running in realtime.
8 I then started Brutefir in a new terminal:
brutefir -nodefault /home/martin/Brutefir/setup_drc_conf where setup_drc_conf is my Brutefir config file. This file includes the following for input:
device: "jack" { };
sample: "AUTO";
 
and for output:
device: "jack" { ports: "system:playback_1", "system:playback_2";}
sample: "AUTO";
After starting Brutefir I opened Patchage and saw that the Brutefir ports were listed with Brutefir:out-0 and 1 connected to system: playback_0 and 1. Brutefir:in-0 and 1 were not connected.
9 I then started Alsaplayer and immediately noticed that in Patchage it was listed and connected to the system:playback_1 and 2 ports which I didn't want. Disconnected these in Patchage and connected them to Brutefir:in-0 and 1, pressed "play" and was thrilled to hear my CD playing with the Brutefir processing within the Brutefir config file and filters.
 
As I said earlier I have a long way to go but by using the gui form of Jack and Patchage us linux newbies are able to get to see how Jack works. Next I need to learn how to do this from the terminal and also to get Alsaplayer to connect directly to Brutefir.
 
Onwards and upwards! Hope this has been of help to someone. I am sure that there are better ways of achieving the desired endpoint but it is difficult to track down information for us newbies. A tutorial of how to set up a Brutefir (or other convolver) on a Ubuntu machine providing audio crossovers and DRC would, I am sure, be very well received and enable many more Windows users like me to take the plunge!
Thanks to everyone for their inputs into this subject.
 
Kind regards
 
Martin

---

### Post by martinward on 2010-12-13
Dont know where the smiley faces have come from - substitute the smiley face with a colon and p......

---

### Post by AutoStatic on 2010-12-13
> **martinward said:**
> 6 To enable both Jack and Brutefir to run without sudo modify the sudoers file as follows:
 
visudo -f /etc/sudoers
then add the following lines and save
jackd ALL=(ALL) ALL
brutefir ALL=(ALL) ALL

...

I am sure that there are better ways of achieving the desired endpoint but it is difficult to track down information for us newbies.Yes, there are better ways than modifying /etc/sudoers in order to get JACK to work in real-time. I'd discourage changing system wide permissions for these kind of things.

[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Best,

Jeremy

---

### Post by martinward on 2010-12-13
Thanks for this Jeremy. I remain a little puzzled. I edited the limits.conf file and added the relevant lines, made sure I was a member of the audio group and set up Jack Control exactly as specified. For some reason I was unable to run Jack in realtime and have spent a good deal of time trying to find out why. I have installed other software - to run TightVNC - and found a recommendation somewhere that the sudoers file should be edited to give Jack and Brutefir sudo rights. After that I was able to run Jack in realtime! I do accept that this is probably technically inappropriate but I am just glad that I can run Jackd in realtime.
 
I have a problem and need some help. I currently run jackd in my normal user terminal, i.e. jackd -blah -blah -blah and in a different terminal run brutefir by entering:
brutefir -nodefault /home/martin/Brutefir/setup_drc_conf.
I want these two processes to run at startup. I have tried adding lines to /etc/init.d/rc.local and then to /etc/rc.local. Unfortunately neither has worked.
Any help to sort this would be greatly appreciated.
 
I have also deleted my .asoundrc file and edited the config file in .alsasound. I have changed the jack port references to Brutefir:input-0 and 1. So now Alsasound connects to Brutefir within Jack on opening. If there is a better way of doing this I would welcome the advice.
 
Thanks in advance for any help
 
Kind regards
 
Martin

---

### Post by Capoeira on 2010-12-22
> **Pablo_F said:**
> I suggest jconvolver instead of brutefir. It is a jack-aware convolution engine. 

See [http://ubuntuforums.org/showthread.php?t=1623984&highlight=jconvolver](http://ubuntuforums.org/showthread.php?t=1623984&highlight=jconvolver)

Cheers, Pablo


yes man, use jconvolver if you want to use jack...its configuered in 5 minutes

---

