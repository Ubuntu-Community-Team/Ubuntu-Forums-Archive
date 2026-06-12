---
title: "How has your sound experience been in Ubuntu?"
date: 2009-07-11
forum: The Cafe
---

### Post by aysiu on 2009-07-11
Just a poll, because I'm curious. Please answer only if you are using a support version of Ubuntu (8.04, 8.10, or 9.04). Thanks!

---

### Post by FuturePilot on 2009-07-11
Everything "just works". I've had 0 problems with PulseAudio.

Edit: On 4 different computers too!

---

### Post by brandonsh on 2009-07-11
The sound works fine on my ThinkPad, but it is quite quiet. I'll find a way around it eventually :-D

---

### Post by Quake on 2009-07-11
I had to remove pulseaudio. I just hate that thing. It was resource heavy and crashed a lot.

For me, pulseaudio = virus.

---

### Post by swoll1980 on 2009-07-11
Neither I (on multiple machines) nor anyone I know, ever had a problem with PA.

---

### Post by deathsshadow77 on 2009-07-11
Personally, pulseaudio has been great. Imo it was a great decision, I hated how alsa only allowed one application to do sound at a time. 

Unfortunately it seems to be buggy for quite a few people. I do believe though that it works fine for most setups. It just seems like there are many problems with it because of all post on the forums.

---

### Post by Chame_Wizard on 2009-07-11
It's worked out of the box in 8.10 .:lolflag:

---

### Post by VCoolio on 2009-07-11
It worked out of the box, only when I bought a 5.1 set I needed to disable pulseaudio, disable onboard sound in the bios (I also bought a new sound card) and configure alsa to get it running, all with some difficult searching and using various howtos. But now I'm happy.

---

### Post by Firestem4 on 2009-07-11
Sound works pretty well...Biggest issue I have right now is on my new desktop trying to get Kubuntu 9.04 to play nicely with my Soundblaster X-Fi XtremeMusic.. Downloaded and installed the proprietary drivers just fine. Sound plays through the phonon-backend (system sounds). However application sounds do not.. =(

---

### Post by wojox on 2009-07-11
Everything worked perfectly out of the box. Only had one problem and found out I had not turned the speakers on. Operator error.

---

### Post by renkinjutsu on 2009-07-11
> **brandonsh said:**
> The sound works fine on my ThinkPad, but it is quite quiet. I'll find a way around it eventually :-D

brandonsh, have you tried running `alsamixer` in terminal? .. usually some things are turned waaay down so it's quiet.

sound capture doesn't work =[

---

### Post by NovaAesa on 2009-07-11
Works good for me. I'm using onboard sound hardware.

---

### Post by oldsoundguy on 2009-07-11
Finally got sound (digital surround with Pulse) to work after following the long and convoluted instructions that are STILL available on the forums.  Then an update happened. 
Bye bye sound .. including the analog and the front panel and headphone control on the 5.1 Creative card.  
Nothing I have tried has restored the sound including a complete  removal and a re-install using the guide I used before.
Running 8.4 LTS
The other three Ubuntu based machines work fine in analog out of the box and never had Pulse activated.  (two 9.4 machines and a Mint Elyssa)  But there is no DIGITAL outputs that have ever working on any of them!!

---

### Post by FuturePilot on 2009-07-11
> **deathsshadow77 said:**
> 

Unfortunately it seems to be buggy for quite a few people. I do believe though that it works fine for most setups. It just seems like there are many problems with it because of all post on the forums.

Exactly. For the people that don't have any problems, they have no need to post anything about it, so you never hear from them, only from the people having the problems.

---

### Post by bubbhasdance on 2009-07-11
The only problem I have is having to run alsamixer in the Terminal every time I want the sound to run through the headphones only, vice-versa. This is one of the most irritating things about the OS, and I haven't seemed to find an answer or way to fix this yet. A near deal-breaker.

---

### Post by Glucklich on 2009-07-11
On my Toshiba laptop (R.I.P.) I had to update the BIOS but on the desktop, everything worked great. On the new laptop, it doesn't detect when I plug-in the phones but I select it in the Mixer and can make the sound come out both ways (or just one of them if I want), which is very good. So, everything works even better than what I expected on the new lappy.

---

### Post by Gizenshya on 2009-07-11
Everything fine right out of the box.  Well, in 9.04 that is.  I had several issues in 8.10, but I've moved on and so have the problems ;)

---

### Post by Bart_D on 2009-07-11
PulseAudio has been great and worked fine out of the box.  I have had no problems with it.

---

### Post by gn2 on 2009-07-11
On my desktop PC with 8.04 I had to remove Pulseaudio.
On my laptop with 8.04 I had to edit /etc/modprobe.d/alsa-base, [bug 197779]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/197779")

---

### Post by RiceMonster on 2009-07-11
Last Ubuntu version I used was 8.04. I only experienced minor sound problems in tuxracer and related games. I haven't ran into any sound problems with Pulse Audio on Fedora 11, however.

---

### Post by WildeBeest on 2009-07-11
I had to follow a few Pulse Audios How To's.

Hardy and Jaunty. I skipped Ibex.

---

### Post by Irihapeti on 2009-07-11
I had to change a few system-preferences-sound settings. I was having some trouble with Audacity but I got that sorted. I have one desktop and two laptops, all running 8.04.

My son and daughter-in-law have 8.04 on their desktop. I think if they were having problems, I would have heard, because I'm their first line of tech support.

My son had a laptop (got stolen in the end - what a shock for the thieves to find Linux on it! :)) and he had to select the correct Alsa driver to get VoIP to work properly. I don't think that was a PulseAudio problem, though.

---

### Post by fballem on 2009-07-11
On ubuntu 9.04, I have to follow a very specific set of instructions to get PulseAudio to work. I found the basics in a how to located here: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

I did have to make a slight change in the order: I set up the users in the pulse, pulse-access, and pulse-rt groups first, before I follow the rest of the instructions.

I find the sound to be a little too quiet, but it does work. It's also quite easy to switch between my speakers (connected to the onboard sound card) and the Logitech USB headphones.

I'm hoping in Karmic that the installation of PulseAudio will be more automatic.

---

### Post by brandonsh on 2009-07-12
> **renkinjutsu said:**
> brandonsh, have you tried running `alsamixer` in terminal? .. usually some things are turned waaay down so it's quiet.

sound capture doesn't work =[

I just had a look. Everything seems OK. I must just have quiet speakers.

---

### Post by MasterNetra on 2009-07-12
Now that the blacklist of my intel card seems to be lifted everything seems to function perfectly!

---

### Post by Hobgoblin on 2009-07-12
Had to run alsamixer and set the volume to full there but after that it works fine.

> **brandonsh said:**
> I just had a look. Everything seems OK. I must just have quiet speakers.

Try turning the lineout down then back up to full in alsamixer.

---

### Post by chriskin on 2009-07-12
had to remove libsdl1.2debian-alsa and install libsdl1.2debian-pulseaudio, and make pulseaudio the default.
then all was ok

---

### Post by brandonsh on 2009-07-12
> **brandonsh said:**
> I just had a look. Everything seems OK. I must just have quiet speakers.

Ooh! Problem solved! It turns out the speaker hardware volume itself (The buttons on the front) was low, and the other volume has nothing to do with the actual speakers.

---

### Post by freacert on 2009-11-17
8.10 no problem, everything out of the box
9.04 3 days installed, and full with problems, reboot yes, reboot no sound. so upgraded to 9.10, kernel 2.6.31 and still no sound! Will be a hard day today...

---

### Post by lightningfox on 2009-11-17
Everything works perfectly out of the box on my computer (Ubuntu 9.10).

---

### Post by jon armand on 2009-11-17
After upgrading to 9.10 my M-audio audiophile 2496 no longer works. From bug-reports I understand that pulse-audio no longer supports this card. I had to install jack to make it work. I wasn't happy with this solution, and reinstalled 9.04.

---

### Post by t.rei on 2009-11-17
I am running an Asus Laptop with a subwoofer and two speakers.
When plugging in headphones the speakers got muted, but the sw didn't.
 
I had to edit the alsa configuration. Now the speakers still mute, and the subwoofer wont work at all. Wich is sad, but better than before.
 
So - sound worked nicely, just not with headphones... so... it didn't really work. So now it doesnt work nicely but with headphones.
 
*sigh*

---

### Post by koleoptero on 2009-11-17
Can you call 6 months old thread a zombie? Or is it too early in its decomposition? :-k

---

### Post by t.rei on 2009-11-17
Since "Sound" is an evergoing issue on all Operating-Systems except maybe Mac, I think this should not become a zombie. 
Sound is crud and considering the multimedia focus of PCs nowadays REALLY important.

---

### Post by RabbitWho on 2009-11-17
The Pigeon noises are always kind of.. feedbacky.. dunno how to describe it, there's this rattling noise that shouldn't be there.  And sometimes the sound in the web browsers just completely stops working for no apparent reason and the only thing that gets them going again is to restart. (With both Chrome and Firefox) 
But these are not major issues. 
Other than that i've no problems, I use Philips speakers plugged in through the headphone jack (somewhat inconveniently located) at the front of my Dell Inspiron 1545, and i've no other problems with sound.

---

### Post by oldsoundguy on 2009-11-17
Sound .. this old thread is still valid in a way.

The powers that be have yet to address the DIGITAL OUTPUT issue(s) on sound cards .. analog works just fine for playback and for streaming (if the source is fast enough). (now using 9.10 on a couple of boxes)

But remember, anything that is OVER THE WEB communications, such as Pidgin or any VoIP type communication, can and will have issues now and then.
I have them with my VoIP phone service.  So do NOT blame your hardware OR your software. It is just part of the beast right now.

---

### Post by RaZe42 on 2009-11-17
Let's just say that sound is easier to get working properly in Arch than in Ubuntu* ;)


* On my hardware, that is.

---

### Post by alphaniner on 2009-11-17
I chose other situation.  Volume was an issue for me.  I can't say I exhausted all resources, but I did turn up everything to 100% (GUI and cli) and sound on my monitor speakers was just not loud enough.

---

### Post by phrizek on 2009-11-17
Sound works great out of the box on my Asus UL80vt in 9.10.

---

### Post by Zoot7 on 2009-11-17
No big problems on either of my systems. 
The only issue was that I'd to route out the source code for the pulseaudio flash plugin, compile and install it to get sound with flash.

---

### Post by bhishan on 2009-11-17
Ubuntu 9.10 64 bit in Dell inspiron 1525 works perfect

---

### Post by arnab_das on 2009-11-17
been perfect! especially with karmic since it offers the "artificial" volume increase beyond 100% from the sounds menu.

---

### Post by JC Cheloven on 2009-11-19
I think people reporting no problems with sound, only use the basic apps for sound (tipically when browsing, through firefox).

I've been trying to completely switch to ubuntu since 2 years, but I do studio recording, composing, and many music stuff in general. It's a pain. Sound in linux is a terrible mess of (partially incompatible) sound servers "looking for its place in the world". 

I voted I had to remove pulse and tweak configuration files. Even so, there remain the problem of hardware suport for me to switch completely. Trying hard, despite this ;-)

---

### Post by xpod on 2009-11-19
> Re: How has your sound experience been in Ubuntu?

In a word....sound.

The only problem i`ve ever had with sound on any Ubuntu release was away back when i first installed 6.06 and the sound never worked with flash content, although it did with everything else.
I think that was more likely a flash issue than a sound issue but whatever it was it was fixed with a rather complicated(more so back then) looking command given to me by the creator(?) of a certain 3rd party application installer many people loved/loved to hate back in 2006/07.

---

### Post by user11 on 2009-11-19
What sound?

---

