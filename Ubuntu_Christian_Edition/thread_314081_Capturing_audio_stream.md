---
title: "Capturing audio stream"
date: 2006-12-07
forum: Ubuntu Christian Edition
---

### Post by HareBall on 2006-12-07
I am wanting to capture some streaming audio from a website and I haven't been able to find anything that works for me except a windows program that costs about $50. I would like something more like FREE. I would prefer to do it with Ubuntu.
Any help would be appreciated. And keep it simple, if it needs code to run it, I will need a step by step tutorial. I keep having trouble with tar.gz files.](*,)

---

### Post by linuchsan on 2006-12-07
mplayer -dumpfile <file name> -dumpstream <URL>

---

### Post by doobit on 2006-12-07
You can also record in Audacity while playing in another program.

---

### Post by HareBall on 2006-12-07
> **doobit said:**
> You can also record in Audacity while playing in another program.
If the file is running in a Firefox window, how do I do this? Like I said I need it broken down to simple:) 

> **linuchsan said:**
> mplayer -dumpfile <file name> -dumpstream <URL>
This I don't understand either:confused:

---

### Post by Shay Stephens on 2006-12-07
We have been talking about this over here:
[http://ubuntuforums.org/showthread.php?t=305858](http://ubuntuforums.org/showthread.php?t=305858)

---

### Post by HareBall on 2006-12-07
> **Shay Stephens said:**
> We have been talking about this over here:
[http://ubuntuforums.org/showthread.php?t=305858](http://ubuntuforums.org/showthread.php?t=305858)
Well, I really don't care about setting up a timer to record this. Maybe later, but for now I will be there to start and stop this. I just want to be able to record things to listen to later in the car or on my mp3 player. Like concerts and such. Kind of like listening to a podcast. These concerts are streams, so I can't just download them and do it.

---

### Post by Shay Stephens on 2006-12-07
Why can't you just use the sound recorder then?  Go to "Applications - Sound & Video - Sound Recorder".  Press the red record button, and it should record whatever is playing on the computer at the time.

---

### Post by HareBall on 2006-12-07
> **Shay Stephens said:**
> Why can't you just use the sound recorder then?  Go to "Applications - Sound & Video - Sound Recorder".  Press the red record button, and it should record whatever is playing on the computer at the time.
I tried this and when I playback the file, I don't get any sound. Anything you can think of I am doing wrong? I have downloaded gstream and some other capture programs(transkode and streamripper), but I don't know how to install them](*,) 
Sorry if I am a pain. I just want this to work and I am about ready to give up:mad:

---

### Post by doobit on 2006-12-07
if it's not working, then you may have one of the input settngs muted. Double click on the little speaker icon to open up the mixer and unmute things until you get recordings with sound.

---

### Post by HareBall on 2006-12-07
> **doobit said:**
> if it's not working, then you may have one of the input settngs muted. Double click on the little speaker icon to open up the mixer and unmute things until you get recordings with sound.
Are you talking about the sound recorder(don't see one there) or on the panel? I made sure the ones on the panel were turned all the way up. They weren't up on capture. Still no sound.
Well now I have sound, but just scratchy static with some voices here and there. I am now trying to record something else to see what I get. It was set to record from mux and now I am trying capture. I am saving them as CD Quality Lossy. I'll let you know what I get shortly.
Same thing. Well, at least I am getting sound now. I'll check back later. I have to get ready for work.

---

### Post by Shay Stephens on 2006-12-07
Totem, the default playback program is having some trouble in edgy I notice.  I think it is the xine portion, because I get much better results if it is using the gstreamer backend (totem-gstreamer package in synaptic).

But my best and most reliable playback is to open the audio file with mplayer instead of totem.  You can install mplayer from synaptic if it is not installed already.  Once installed, you can right click on the file and open with mplayer.

---

### Post by Darrious on 2006-12-07
My totem player is doing just as good, if not better, than Mplayer. 

I just had to install the right codecs in order get it to work.

But still, I like mplayer better.

---

### Post by Shay Stephens on 2006-12-07
Ya if it is working, then good news.  If not though, trying some of the other suggestions might bring some joy :-)

I have a feeling this will all work a lot better for more people when feisty comes out.

---

### Post by Darrious on 2006-12-07
I hope so. Edgy is okay, although it was little disappointing. Dapper is one of the much more stable releases. Edgy actually had a few bugs when It was first released. I just hope that feisty will be a more stable release, like Dapper, when it comes out.

---

### Post by silvagroup on 2006-12-07
I believe firefox has some kind of extension that will capture video and audio streams, check the firefox extensions.

---

### Post by Darrious on 2006-12-08
Kinda like this?

[https://addons.mozilla.org/firefox/2838/](https://addons.mozilla.org/firefox/2838/)

---

### Post by HareBall on 2006-12-09
> **HareBall said:**
> I tried this and when I playback the file, I don't get any sound. Anything you can think of I am doing wrong? I have downloaded gstream and some other capture programs(transkode and streamripper), but I don't know how to install them](*,) 
Sorry if I am a pain. I just want this to work and I am about ready to give up:mad:
I assume nobody has a better answer than I have already gotten. Nothing I have tried so far has worked.
Somewhere along the way this kinda got off topic. I checked out extensions for Firefox. Didn't really seem to be anything for what I want to do. Don't want anything for video, just audio.
Thanx for the help I did receive.

---

### Post by Shay Stephens on 2006-12-09
The last you said you were getting sound recorded, but it was scratchy right?  Have you installed the totem-gstreamer package?  Did that make a difference?

---

### Post by HareBall on 2006-12-09
> **Shay Stephens said:**
> The last you said you were getting sound recorded, but it was scratchy right?  Have you installed the totem-gstreamer package?  Did that make a difference?
Yeah it was scratchy. Not exactly what I am wanting:) 
I have it installed, but I don't have a clue on how to get it to capture the stream I want it to capture:(  I can do very few things in Linux and this isn't one of them:confused: 
I really do need step-by-step instructions on how to do this. Sometimes I think I should just dump this and go back to using Windoze.](*,)

---

### Post by Shay Stephens on 2006-12-10
You use the sound recorder (Applications - Sound & Video - Sound Recorder) to capture the audio and save the file.  You use a different program to listen to the audio.  

In this case the default is a program called totem.  If you already have the totem-gstreamer package loaded, then you should be able to play the saved audio file and it should sound the way it is supposed to.  Just double click on the audio file and totem should pop up to play the file.  You can double check that by going to help - about.

So now the question is, what happens when you record some audio using the sound recorder and play it back with totem?

Oh and if you say "Sometimes I think I should just dump this and go back to using Windoze." again, I won't help you anymore ;-)  It can take a while to learn something new.  No pain, no gain right :-)

---

### Post by tuxcantfly on 2006-12-10
why don't you just do mplayer -dumpstream

---

### Post by HareBall on 2006-12-10
> **Shay Stephens said:**
> You use the sound recorder (Applications - Sound & Video - Sound Recorder) to capture the audio and save the file.  You use a different program to listen to the audio.  

In this case the default is a program called totem.  If you already have the totem-gstreamer package loaded, then you should be able to play the saved audio file and it should sound the way it is supposed to.  Just double click on the audio file and totem should pop up to play the file.  You can double check that by going to help - about.

So now the question is, what happens when you record some audio using the sound recorder and play it back with totem?

Oh and if you say "Sometimes I think I should just dump this and go back to using Windoze." again, I won't help you anymore ;-)  It can take a while to learn something new.  No pain, no gain right :-)
No, I say No Pain, No Pain!;) 
I am about to go and try again to do this. I'll let you know what happens later.

---

### Post by HareBall on 2006-12-10
> **Shay Stephens said:**
> You use the sound recorder (Applications - Sound & Video - Sound Recorder) to capture the audio and save the file.  You use a different program to listen to the audio.  

In this case the default is a program called totem.  If you already have the totem-gstreamer package loaded, then you should be able to play the saved audio file and it should sound the way it is supposed to.  Just double click on the audio file and totem should pop up to play the file.  You can double check that by going to help - about.

So now the question is, what happens when you record some audio using the sound recorder and play it back with totem?

Oh and if you say "Sometimes I think I should just dump this and go back to using Windoze." again, I won't help you anymore ;-)  It can take a while to learn something new.  No pain, no gain right :-)
Ok, I am still only getting noise with my stream with the volume being very low. I have to turn my speakers almost all the way up to even hear. I used the sound recorder set on both capture and mux as the record from input. I then played it back in totem. It was horrible.

---

### Post by HareBall on 2006-12-10
> **tuxcantfly said:**
> why don't you just do mplayer -dumpstream

I don't know what dumpstream is. Tell me more.

---

### Post by Shay Stephens on 2006-12-10
> **HareBall said:**
> Ok, I am still only getting noise with my stream with the volume being very low. I have to turn my speakers almost all the way up to even hear. I used the sound recorder set on both capture and mux as the record from input. I then played it back in totem. It was horrible.
Is there any intelligible sound or is it truly static?

Do you have mplayer installed?  Assuming you do...

Assuming there is some intelligible sound, try right clicking on the audio file and opening it with mplayer.

mplayer is not installed by default.  So you have to install that manually.  I install it using automatix.  automatix is a program that can install a number of programs dealing with multimedia in a fairly painless way.

You can get automatix for edgy here (assuming you are running edgy):
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.3-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.3-6.10edgy_i386.deb)

Download it, right click, run it with gdebi to install it.  When you run the program you will have a menu of different applications you can install.  Look for the multimedia types, I like installing mplayer, codecs, etc.  After the installation of the programs you want is done, then give the audio file another try and mplayer should be an option for running it when you right click on the audio file.

If something here makes no sense, just let me know :-)

---

### Post by arnieboy on 2006-12-10
The following is a howto to rip streaming audio.
[http://www.ubuntuforums.org/showthread.php?t=76658](http://www.ubuntuforums.org/showthread.php?t=76658)

---

### Post by HareBall on 2006-12-10
> **Shay Stephens said:**
> Is there any intelligible sound or is it truly static?

Do you have mplayer installed?  Assuming you do...

Assuming there is some intelligible sound, try right clicking on the audio file and opening it with mplayer.

mplayer is not installed by default.  So you have to install that manually.  I install it using automatix.  automatix is a program that can install a number of programs dealing with multimedia in a fairly painless way.

You can get automatix for edgy here (assuming you are running edgy):
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.3-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.3-6.10edgy_i386.deb)

Download it, right click, run it with gdebi to install it.  When you run the program you will have a menu of different applications you can install.  Look for the multimedia types, I like installing mplayer, codecs, etc.  After the installation of the programs you want is done, then give the audio file another try and mplayer should be an option for running it when you right click on the audio file.

If something here makes no sense, just let me know :-)

Everything makes perfect sense, but no matter what I play it with it sounds like it is just skipping about a 1/2 second at a time and is full of static. I can understand some of the words. Even then it is full of static. I got this same concert to record with wavepad in windoze, but there it was to low of a level to make it really useful for anything. Then I had to turn my speakers all the way up to hear it, but it was clean when I did that. This makes me think it is a sound recorder problem here in Ubuntu.:-k I also tried a shareware program that worked real well in windoze, but it is about $50. I can't justify that much for something I am just going to play with for the most part. Besides the shareware program inserts a "buy me" type of audio ad into the file every so often, so I can't even use that for what little I want this for. I am thinking about going back and rerecording it in widoze and then seeing what it sounds like when I open it with Totem.

---

### Post by HareBall on 2006-12-10
> **arnieboy said:**
> The following is a howto to rip streaming audio.
[http://www.ubuntuforums.org/showthread.php?t=76658](http://www.ubuntuforums.org/showthread.php?t=76658)
One problem. When i get to the part where I put this: 
```
x-terminal-emulator -e streamripper %q -d /mnt/Data01/Ripped -r -q
```
in the terminal I get an error message in another window and the window that opens closes.
Also after I installed streamripper, I tried to open it and nothing happens. It doesn't show up under Applications > Sound & Video either.
One more thing, everytime I try to connect to a station with streamtuner, I get a message telling me: "Failed to execute child process "Movie" (No such file or directory).

---

### Post by arnieboy on 2006-12-10
Blindly copying and pasting wont always fix issues for you. read the howto again. It tells you to paste that in the record path in streamtuner under Edit --> Preferences-> Record a stream
and also change /mnt/Data01/Ripped to a real path which exists (in your home directory for example?)
Also, streamripper is a command line app and is used by streamtuner (see the green record button?)

---

### Post by HareBall on 2006-12-10
> **arnieboy said:**
> Blindly copying and pasting wont always fix issues for you. read the howto again. It tells you to paste that in the record path in streamtuner under Edit --> Preferences-> Record a stream
and also change /mnt/Data01/Ripped to a real path which exists (in your home directory for example?)
Also, streamripper is a command line app and is used by streamtuner (see the green record button?)
OK, I understand that much, but I am pretty new to Ubuntu.
The streams I want to record are from this site [http://concerts.wolfgangsvault.com/Concerts.aspx?Page=1&ID=13edc078-f69a-43c0-b614-b58b7f3a702d&D=](http://concerts.wolfgangsvault.com/Concerts.aspx?Page=1&ID=13edc078-f69a-43c0-b614-b58b7f3a702d&D=)
I don't know what kind of stream it is and I'm not sure how to point streamtuner to it.

---

### Post by logos34 on 2006-12-11
Tried the HOWTO, arnieboy, and it works great!  Wish I'd seen it earlier. 

So tell me, is streamtuner + streamripper is the best way to rip streams if you want to avoid intermediate .wav files and setting the recording volume level?  Preferable to using mplayer -dumpfile method? I've tried 'arecord', which is nice in that you can set the recording duration (in secs), and it saves it in compressed format, but it apparently captures the PCM signal from your sound card so you have to set the recording volume to avoid clipping, distortion, etc.  And with the others -- Audacity and Gnome Sound Recorder for instance -- there's the volume AND at the end a huge wav file to compress.

---

### Post by HareBall on 2006-12-13
> **arnieboy said:**
> Blindly copying and pasting wont always fix issues for you. read the howto again. It tells you to paste that in the record path in streamtuner under Edit --> Preferences-> Record a stream
and also change /mnt/Data01/Ripped to a real path which exists (in your home directory for example?)
Also, streamripper is a command line app and is used by streamtuner (see the green record button?)

Still get error evn after I changed /mnt/Data01/Ripped to a real directory on my computer.

---

### Post by Shay Stephens on 2006-12-13
> **HareBall said:**
> Still get error evn after I changed /mnt/Data01/Ripped to a real directory on my computer.

We could help out faster and more efficiently if you would provide clear details.  You don't have to be so non-verbose ;)  go ahead and spell it out.  So you got an error...err...what was the error?  What is the directory you are saving too?  What is the full command you are using?

It feels like we are flying blind here and stabbing at the wind :)

---

### Post by HareBall on 2006-12-14
> **Shay Stephens said:**
> We could help out faster and more efficiently if you would provide clear details.  You don't have to be so non-verbose ;)  go ahead and spell it out.  So you got an error...err...what was the error?  What is the directory you are saving too?  What is the full command you are using?

It feels like we are flying blind here and stabbing at the wind :)
I'd love to tell you, but when it happens all I have time to do is see it say there is an error and the window closes.
In start with sudo apt-get install streamtuner.
Then I put in sudo apt-get install streamripper
Then when I get to x-terminal-emulator -e streamripper %q -d /mnt/Data01/Ripped -r -q, this is where I get the error.
This is what I tried to do [http://www.ubuntuforums.org/showthread.php?t=76658](http://www.ubuntuforums.org/showthread.php?t=76658)
Believe me, I tell as much as I can when I post these things.

---

### Post by father_je on 2008-02-11
Hello, can anybody help me, i'm having difficulty recording from a tape deck to ubuntu ce using sound recorder, when i try to save the file it won't save the recording i made, can anybody pls help, what is the right procedure in recording from tape deck to ubuntu ce...thank you very much

---

### Post by tsx2424 on 2010-12-03
> **linuchsan said:**
> mplayer -dumpfile <file name> -dumpstream <URL>

 It works.Thanks.

---

