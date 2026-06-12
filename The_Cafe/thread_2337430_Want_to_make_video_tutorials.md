---
title: "Want to make video tutorials"
date: 2016-09-18
forum: The Cafe
---

### Post by tech291083 on 2016-09-18
Hi Friends,

A group of my Linux enthusiasts friends want to make some easy videos with audio and upload on YouTube, but none of them, including myself has ever dealt with video production ever. We want to do a topic on our own PCs then add audio as we go along or afterwards, I think this type of software are called screen cast or something similar. Can you suggest some easy to use, good quality, totally free and open-source software for this very purpose based on your own personal experience, if any? Have you ever uploaded video tutorials on YouTube etc?

Thanks a lot

---

### Post by TheFu on 2016-09-18
**OBS** if you want to live record audio and video. Use their PPA for the installs.  Multiple video and audio inputs can be muxed into a single stream.

**simplescreenrecorder** if you want to capture a window or entire desktop.

**audacity** to record audio afterwards .... or more likely, replace the existing audio that you got with the video.

Use whatever video tools you like to mux the video and audio back together. OBS, ffmeg, avcon, whatever.

I've never uploaded to youtube (political reasons), but publish the files to our groups.

---

### Post by ventrical on 2016-09-18
Openshot found in the repositories is a must. If you have stills and want to add them together in a slideshow and add an audio track this is the app for creating instructional development tutorials , bar none.

Regards..

---

### Post by Bucky Ball on 2016-09-18
Not about the software, but a couple of tips as you mention you have no experience with AV. The more you can get 'on the day' the better. In this case, meaning if you can record audio and video simultaneously into the same file (as mentioned previously), so the audio/video tracks are 'synced' together from the start, it is going to save time in 'post', where you are going to have to scale another learning curve: you'll need to 'lay' the post-recorded audio tracks (audio recorded after the video and separately) on to the video tracks.

If you don't have actual talking heads on-screen, or if you have some experience with syncing time codes, this is not too much of an issue once you've figured out how to do it. If you do have talking heads, put away some time (possibly considerable depending of how much you need to post-produce) for sound-post (laying the post-audio on to the vid in this case).

Of course, for your purposes, it may be real easy to simply put all vid clips together, plug in a mic and record audio directly to the same AV file as the vid. May take a few tries but perhaps quicker in the end and you'll get the hang of it which will also speed up the process.

Something to always keep in mind when creating AV stuff of any kind: what is going to be easiest in post??? It is often straightforward and fun grabbing a camera or putting together some screen cast stuff on computer and grabbing the audio to go with it, but then ... you realise you've got thirty hours work putting it all together!

With a bit of thought in pre- you can save a lot of time in post-. Just throwing that in and hope it helps in some way. Good luck. :)

---

### Post by TheFu on 2016-09-18
Hey Bucky!  --- OBS [https://obsproject.com/](https://obsproject.com/) makes this muxing of different video and audio sources during the "live" capture pretty easy.  The normal "presentation" + "talking head" stuff is just done with an HDMI capture + webcam.  OBS can handle as many inputs as your hardware can support and has methods to transition between different shots (or swap the presentation/talking-head video inputs).  This is how we do it at my LUG, DC and PM groups.  I have a Core i3 chromebook (running a lite-ubuntu setup) and it handles 3 audio and 2 hidef video inputs without issue.  My prior Celeron-based Chromebook couldn't deal with both hidef video inputs.

At conferences, I've seen people use simple screen capture software and x2go remote desktops into the laptop used by speakers. The speakers weren't allowed to bring their own laptops. They had to use provided ones which were pre-configured.

The hardest part for me is the front and trailing leaders ... title screens and credits. The recording parts and muxing are really quite trivial thanks to OBS.

---

### Post by tech291083 on 2016-09-18
> **Bucky Ball said:**
> 

In this case, meaning if you can record audio and video simultaneously into the same file (as mentioned previously), so the audio/video tracks are 'synced' together from the start, it is going to save time in 'post', where you are going to have to scale another learning curve: 



Ya, I intend to record audio and video (screen activity on my PC) simultaneously only, but right now I do not have a working microphone, so I will just turn off audio recording if the software permits that, or simply there will be no audio automatically. 

I agree with you in the sense that my lack of experience with AV, might make it difficult for me to add audio in a video clip afterwards, but you are 100% right, practically speaking. 

Please always fl free to jump in with any tips/suggestions you have, I am always ready to take them on board.

Many thanks & regards,

---

### Post by tech291083 on 2016-09-18
> **TheFu said:**
> 

 OBS [https://obsproject.com/](https://obsproject.com/) makes this muxing of different video and audio sources during the "live" capture pretty easy.  


I am sorry, but if I understand correctly, then muxing means incorporating different types of files into an already existing video file right? ie audio and other stuff, which i cannot even think of, just due to my lack of experience in this area.

> 
The normal "presentation" + "talking head" stuff is just done with an HDMI capture + webcam.  OBS can handle as many inputs as your hardware can support and has methods to transition between different shots (or swap the presentation/talking-head video inputs).  


You have described the advantages to using OBS pretty well, I would probably try OBS only.

> 
The hardest part for me is the front and trailing leaders ... title screens and credits. The recording parts and muxing are really quite trivial thanks to OBS.


I will keep this in mind.

Thanks a lot for your time, regards.

---

### Post by Bucky Ball on 2016-09-18
> **TheFu said:**
> Hey Bucky!  --- OBS [https://obsproject.com/](https://obsproject.com/)

Thanks for that. Excellent info.  :) I have no *immediate* use for OBS, though might if I have the time to expand the project I'm doing at the moment, but will definitely keep OBS up my sleeve for future investigation as the opportunity to take it for a spin will no doubt arise one 'o these days.

Besides, I want to play with it! :)

---

### Post by TheFu on 2016-09-18
> **tech291083 said:**
> You have described the advantages to using OBS pretty well, I would probably try OBS only.

OBS isn't everything for everyone.  There are times to use other tools - like if I was going to use a screen capture + audio, I probably wouldn't use OBS. OBS is heavy, complex to use (though very intuitive for video production gurus).  For a simple screencast, start with SSR - simpleScreenRecorder. It may be all you need.

Yes, muxing is the process of merging video and/or audio streams into a single file.  Those streams can be from files or from live inputs, at least with OBS.  Another tool that people use to merge/mux video + audio is avidemux, but getting the audio and video to sync can be non-trivial if recorded separately. For simplicity, I'll record the audio from all the webcams too - just to have the audio sync'd during editing even if I have a separate mic for the speaker. Dump the webcam audio after I get everything sync'ed and only use the best quality from a USB mic or best quality audio.  Oddly, getting good audio in a crowded room is very hard. At home, I can completely recommend the $35 USB Samson Go-Mic [https://www.amazon.com/Samson-Mic-Portable-Condenser-Microphone/dp/B001R76D42/](https://www.amazon.com/Samson-Mic-Portable-Condenser-Microphone/dp/B001R76D42/) (now $40). Works out of the box with Linux. You can spend 2-4x more for a Yeti, if you like, and the sound will be a tiny bit better, but for $35, the Samson is AMAZING - much better than any built-in mic on a laptop.

---

### Post by Bucky Ball on 2016-09-18
> **TheFu said:**
> For simplicity, I'll record the audio from all the webcams too - just to have the audio sync'd during editing even if I have a separate mic for the speaker ...

Yessum. The only way to fly for that sort of stuff, with or without audio mark(clapper board). Makes things soooo much easier to sync separately recorded audio/video. On the day, when I have camera and audio recorders rolling, a finger click and old-school 'speed' and post- is a breeze ... (well, the syncing's easier than otherwise!).

@OP: but yea, a screen caster sounds like it might cover it and maybe put stuff together with a vid editor (to lay audio tracks) later. And also yea, a separate plug in mic will usually be better than any in-built lappy one.

If there's a few people involved and you all feel like pitching in, [something like this]("http://www.rode.com/microphones/videomic") would do the audio trick, no probs. Depends on how good you want/need the audio.

It has a 'cold shoe' on it, which means you can attach it to cameras, camera stands, all sorts of stuff (or fix it some other way) and avoid handling noise when recording. Great for indoor/outdoor dialogue, so usable well beyond this project. :)

* So to those who know, once you have the media (vision and audio) for the project together  would the chain be to put your digital clips/slides/pics in order using screencaster> the screencast is output 'packaged' as one file> you then open that file in Openshot or other vid editor and sync the pre-recorded audio to the video? 

Curious myself now ...

---

### Post by uRock on 2016-09-20
I can give a +1 for SimpleScreenRecorder. I have been using it for over a year. The only time I ever had a problem was when I selected the YouTube profile on it without realizing it check the box for "Separate file per segment" which causes it to create a new file every time I hit the pause button.

The two vids linked in my signature were created with Simple Screen Recorder, if you want to see the quality. Forgive me for being boring and not adding sound. Both were recording a VM without any heavy load on my CPU.

---

### Post by Remson_Felipa on 2016-09-22
Thanks to you all for information

---

### Post by tech291083 on 2016-10-18
Friends. thanks a lot for various suggestions.

---

