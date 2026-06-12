---
title: "Line-Out to Line-In audio daisy-chaining"
date: 2009-04-27
forum: System76 Support
---

### Post by glacialfury on 2009-04-27
I've got a Serval (serp4) running Intrepid and a desktop running Jaunty; I'd like to play music from the laptop on speakers that are hooked up to the desktop, and from what I've been able to find, this can be done by putting a 3.5mm male-male jack from the laptop's audio out (headphone/speaker jack) into the line-in on the desktop's soundcard.

I've done this, and I can't get any sound to play through the line.  The desktop's sound works fine independently, but I can't hear anything the laptop is playing.  All the instructions I can find online are for Windows.

Nothing is muted on either system.  Any tips?

---

### Post by thomasaaron on 2009-04-28
I don't know for sure if that's safe. You may run into some impedence mis-matching between those two ports.

---

### Post by glacialfury on 2009-04-28
Interesting; I'll look into that.  Most of what I'd been reading said this *was* the safe/good method, and that solutions like using a "Y-adapter" had the most potential for impedance, feedback, and volume problems.

There are a number of options for sharing sound (in this case, music) across multiple systems.  I'd love to hear comments from users with more experience.

**1. Use a Y-adapter**  
*Pros:* Simple and cheap, works without configuration.  This is frequently recommended in tutorials on sharing speakers.
*Cons:* Experienced users *always* point out in the comments of those tutorials the potential danger for hardware problems with y-adapters.  For example, in  [SIZE="3"][COLOR="Blue"][this article]("http://articles.techrepublic.com.com/5100-10878_11-5238134.html")[/COLOR][/SIZE]:
[INDENT]a) "y-adapters are generally intended to split output (and will generally reduce impedence by about 1/2 which can be a ver bad idea if using 4 ohm speakers). Piggybaacking line/out to line/in and using mixer is much more straightforward and avoids impedence issues altogether."
b) "First rule for ANY AV hookup= NEVER connect two outputs directly together! (Two inputs OK). =Frank= "[/INDENT]

**2. Line-out -> Line-in:**  
*Pros:* Simple (at least with Windows), supposedly avoids impedance issue altogether (see above comment under Y-switch).  
*Cons:* Could require complicated configuration on Linux (unsubstantiated claim in an article comment).  For me, at least, it did not "plug and play" from one Ubuntu system to another.

**3. KVM with audio support (KVMA):** 
*Pros:* Easy to switch, does not require any software configuration.
*Cons:* Expensive (minimum $40, average above $80).  One user claimed a noticeable decrease in sound quality using a KVMA.

**4. Use the network:** 
*Pros:* Multiple methods (network share, streaming, etc)
*Cons:* Could lag with high network traffic; also, I'm unsure of how the media players work.  When they need to write configuration settings, or adjust the file info, will they do it in the right place?  To adjust tags, I'm assuming the files would have to be setup with appropriate permissions.  I wouldn't want one computer "altering" the setup of the music files for the other without permission :-)

**5. Use a VCR/game console switcher:**
*Pros:* Free (I have one sitting around); easily switch from one system to another.
*Cons:* I lose surround sound on BOTH systems instead of just one, and it requires multiple cable adapters to switch the 3.5 jacks to RCA.  Takes up a fair bit of desk space.

---

### Post by thomasaaron on 2009-04-28
> I'd love to hear comments from users with more experience.

Me too. 

My primary concern would be that I'm not sure if the impedance from a desktop system jack designed for running speakers is properly matched with an laptop jack meant to detect input from a microphone.

My guess would be that it is fine, but I couldn't swear to it. Thus the cautionary note.

---

### Post by jdb on 2009-04-28
> **thomasaaron said:**
> Me too. 

My primary concern would be that I'm not sure if the impedance from a desktop system jack designed for running speakers is properly matched with an laptop jack meant to detect input from a microphone.

My guess would be that it is fine, but I couldn't swear to it. Thus the cautionary note.

I also suspect that 'line in' should match up to 'line out' but I've never seen any specs on it.

I've never done what your trying to do but I often use a patch cord between 'line in' & 'line out' on the same computer.

It's a great way to record anything you would normally hear on your speakers, like streaming audio for instance.

I use alsamixer to set the levels & audacity to record it & then export it to an MP3.

jdb

---

### Post by edm1 on 2009-04-28
Are the computers on the same network because pulse audio can do this easily. Just install the pulse audio guis:

> sudo apt-get padevchooser paman paprefs pavucontrol pavumeter

Then run padevchooser, or add it to your start up list (System>Prefs>Start up applications).

Then on the desktop, click the padevchooser icon in the notification tray and go to 'Configure local sound server' and tick everything in Network Access.

On laptop, do the same. Then run music application. Click on padevchooser icon, go to volume control, right click on the correct stream under Playback and select your desktop computer.

The stream should now play through your desktop speakers. And people say pulse audio is ****.

---

### Post by glacialfury on 2009-04-28
> **thomasaaron said:**
> Me too. 

My primary concern would be that I'm not sure if the impedance from a desktop system jack designed for running speakers is properly matched with an laptop jack meant to detect input from a microphone.

My guess would be that it is fine, but I couldn't swear to it. Thus the cautionary note.


I think you got me backwards - the music is currently stored on the laptop, and I'm using the laptop's headphone jack as the line out.  This runs to the "line-in" on the desktop, which has the speakers plugged in.

edm1: that's a good idea; I have pulseaudio on both computers, but I've never played with any of the gui tools (or done anything with it, really).  I'll mess around with those and see how it goes.

---

### Post by jeamer on 2009-04-28
I've successfully used the line in out method, out from the laptop, in to a digital countertop cd player, and not had any problems. So I would say if you want this method to work, all the fiddling should be focused on the desktop.

---

### Post by Scotty Bones on 2009-04-28
I use a SoundBlaster USB MP3+ (don't know if they still make that model or not).  It's a usb sound card with RCA and optic input/outputs. 

I just dug it out of storage a few weeks ago so that I could connect it to my stereos optic input.  It was automatically detected by Jaunty, no problems at all.  All I had to do was direct the appropriate audio stream to it using PulseAudio and I was in business.



EDIT:
If your trying to go from computer to computer; you might just want to make you music folder a share and access it from the other.

---

### Post by 3Miro on 2009-04-28
I have used line in - line out between stereo and computer to make tapes from mp3/mp3 from old tapes.

---

### Post by Scotty Bones on 2009-04-28
The only problem with this method is that the Mic jack is mono only; so if your looking for stereo or surround, your out of luck.

---

### Post by jdb on 2009-04-29
> **Scotty Bones said:**
> The only problem with this method is that the Mic jack is mono only; so if your looking for stereo or surround, your out of luck.

I just did a test recording using the mic jack on my Daru2 & it is definitely sterio if you plug a sterio jack into it.
If you plug a mono jack into it you will only record one channel.
I also tried it on my desktop & got the same results.

I did a little digging on the 'line in' & 'line out' specs.
The 'line out', 'Speaker out', and 'headphone out' are low impedance.
The 'line in' and 'Mic in' are high impedance.

When you connect them together it is know as a 'bridging match' which won't give maximum power transfer but does give maximum voltage transfer & minimum distortion.
It also allows one output to be connected to multiple inputs without overloading anything.

The main difference between the 'line in' & 'mic in' is that the
'mic in' supplies a 3 Volt bias to power an electret microphone.
The bias is through high impedace and current limited to less than 2 milli Amps so it will cause no problems if connected to a 'line out'.

As long as you never connect two outputs together, you should have no problems.



jdb

---

### Post by ProfDecoy on 2009-04-30
I did this with two of my desktops, going from the spk-out on one to the line-in on the other.  I ran into two problems with this, one the stereo channels got reversed for the the output from the 1st desktop, and secondly I started getting a lot of 60hz noise from the power cables coming in as well, so I ended up disconnecting it.

I think setting up the pulse-audio would be the better idea, since that's one of the things it was designed to do.  However, I have not yet tried setting it up, so I can't provide my personal experience for it.

---

### Post by jdb on 2009-04-30
> **ProfDecoy said:**
> I did this with two of my desktops, going from the spk-out on one to the line-in on the other.  I ran into two problems with this, one the stereo channels got reversed for the the output from the 1st desktop, and secondly I started getting a lot of 60hz noise from the power cables coming in as well, so I ended up disconnecting it.

I think setting up the pulse-audio would be the better idea, since that's one of the things it was designed to do.  However, I have not yet tried setting it up, so I can't provide my personal experience for it.

It may have been a bad cable, an open ground/shield can cause the hum & reversed wires can swap the channels.

Another cause of hum can be one of the computers isn't grounded properly, for instance a three pronged plug in a two prong socket.

I've connected my sterio out to my desktop in, my desktop out to my sterio in, my laptop to my desktop & my desktop to another desktop, all with perfect fidelity.
I didn't do all these at the same time :)

On the other hand, sometimes if a circuit isn't designed properly, hum can be almost impossible to get rid of.

jdb

---

### Post by glacialfury on 2009-05-02
PulseAudio server intrigues me, but I went for the easiest solution in the short-term; I installed "Tangerine Music Sharing", which, with one button, shared all my banshee libraries across the network.

jdb, thanks for the clarification on line in/line out.

---

### Post by daniel_gv93 on 2009-07-10
I'm trying to use the line out-line in method to connect my piano to the computer and record some songs... any idea on how to do this?.. I have connected it as mic and worked but at very very low quality..=S I think i need to do it with the line in but I dont know how. Please any help will be appreciated.

---

### Post by Derath on 2009-07-10
Daniel, I think you may have the lines backwards, if you want to record from your piano, you'll need to use Line-in, Under the volume control settings, I believe there might be an option to select the Line In as the capture source. If not there, it might be in the sound recorder you're using.

As far as microphones go, I had a similar issue on just general PC's... the microphone jack is low powered, and generally even a good mic will not sound good on it, I had heard somewhere that a "powered mic", or an "amplified mic" (external amplifier I imagine) would help with sound quality, but I am not terribly experienced in that.

I did some recordings/mixing with a large plug microphone (big barrel connecter with 4 pins in it) and converted that to the 1/8th (or is it 1/16th?) but had to do a lot of boosting and tweaking in audacity to get it to sound good.

Alternatively, if you can get your hands on a 2-3 channel mixer/amp set up, I would record from that into the line-in jack.

Hope at least some of this helps!

---

### Post by jdb on 2009-07-10
> **daniel_gv93 said:**
> I'm trying to use the line out-line in method to connect my piano to the computer and record some songs... any idea on how to do this?.. I have connected it as mic and worked but at very very low quality..=S I think i need to do it with the line in but I dont know how. Please any help will be appreciated.

Does it have hum or buzzing or is it just distorted?

Distortion usually happens because the output (the piano) is overdriving the input (the mic).
It doesn't do any damage but sounds pretty bad.
Line-in jacks if one is present can usually handle higher signal levels.
If you put a resitive pad between the piano & mic that would fix it.
I usually make them, I don't know what's available.

Hum or buzz is picked up from the AC power line, using a grounded AC plug on the piano or flipping it over if it's non-polarized may help.
The same goes for the computer.
If its a laptop unplugging the charger to isolate it from the power grid may help or may make it worse because it would lose it's ground reference.
It depends on the circuit layout.

jdb

---

