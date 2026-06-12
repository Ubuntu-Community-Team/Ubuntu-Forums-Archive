---
title: "Making video from Cinelerra to upload to youtube"
date: 2010-01-12
forum: Ubuntu Studio
---

### Post by rapattack1 on 2010-01-12
Hi I have been experimenting with Cinelerra, Kino and Avidemux for a few months now after doing a Final Cut pro course and i make little videos to put on youtube but can't seem to get something smaller than the original file. What am i missing? I have tried a small frame size but that cuts some of the picture down at the sides/top in Cinelerra. I am finding it hard to find any info on this either googling or in Cinelerra tutorials.
I will start out with a file that is a dv because i captured in Kino from my camera and it is 1.5gb then whatever i render it as in Cinelerra is is huge. I have battled with this forever. Is there a way of putting a youtube preset in Cinelerra so that the file is what i need for uploading to youtube?

---

### Post by Linuxforall on 2010-01-12
Actually the easiest and best tool for uploading to youtube is Handbrake, Cinelerra is good for editing like Adobe Premiere but for a simple task of youtube, Handbrake with its easier interface does the job much better. Since you have checked out other editors as well, I also suggest you try out Handbrake and Open Shot, the later is excellent editor as well.

---

### Post by rapattack1 on 2010-01-12
Thanks but i had handbrake on the previous install of Ubuntu and got nowhere. I couldn't figure it out either.
I have never used Adobe premiere so i have no reference there.
Haven't heard of openshot. Might try it one day but i prefer to see if i can get these apps working for me. 
Ever other piece of editing things in those apps i mention works fine ...it is just when i go to render it is not happening for me.

---

### Post by wildhostile on 2010-01-13
> **rapattack1 said:**
>  . 

You will have to render your final video into dv format at first.
DV format has fixed size and framerate: 720x576 at 25fps for DV PAL. (I don't know for NTSC).
When done, use a converter to reduce the weight of your file. Handbrake, Avidemux, Tabencode, Winff, MobileMediaConverter, tovid-interactive.

Handbrake is very interesting since it permits you to resize your video (with picture settings option). To know what format/codec to use maybe you should look if youtube has recommendations.

---

### Post by EricDrijv on 2010-01-13
Openshot has a build in saving function for Youtube and Youtube HD

---

### Post by rapattack1 on 2010-01-13
Actually i was told to import into Kino which renders as a dv then take it into cinelerra and that worked...otherwise i couldn't get it into cinelerra.
I tried so many of those apps and I got nowhere so i need something more specific. Sorry just still very new to the Linux way of doing things especially video production.
FCP does a lot for you and is pretty mazy i know but that is all i know how to use. I was bashing my head understand a lot before i did that course it has helped me heaps!

OK I am getting Openshot now and hopefully will figure it out. Can you tell me exactly how to render it as a file for youtube please!!!! I could not get it to render anything and may have even had trouble loading files into handbrake. I will give it a try tomorrow as it it time to Zzzzzzzzzzzzzzz:D

---

### Post by rapattack1 on 2010-01-13
Hi I tried to install openshot but got it wrong. I used the Koala Ubunut 32bit version from this url [http://www.openshotvideo.com/2008/04/download.html](http://www.openshotvideo.com/2008/04/download.html)
The first file didn't install via the gdebi installer. The 2nd and 3rd did so i am not sure what to do from here.

---

### Post by LuridCinema on 2010-01-15
I have been working on this myself. I rendered the video .mov or .avi  at 1920x1080 then converted in ffmpeg as below...

ffmpeg -i FILE.mov -s 1280x720 -sameq -ar 44100 FILE.flv

I couldnt get it to work with the audio at 48000 so I changed the audio to 44100 and had to change the resolution to 1280x720
 
I had mucho probs getting the vids to upload to Youtube until I used the bulk uploader.

Here is a link to a video I did this way :

[http://www.youtube.com/watch?v=vL4s8CnI0jo](http://www.youtube.com/watch?v=vL4s8CnI0jo)

good luck !!!

---

### Post by rapattack1 on 2010-01-15
Yeah I finally got something using Winff which is ffmpeg. I converted like you said and there was a preset for 'flash flv' so that worked really well. Made file much smaller too so it didn't take forever to upload to youtube. I knew that flv was the youtube format as i have downloaded them many times.

I will look at your video later as my internet speed has been stepped down as i have used it all for this month.

Thanks heaps!!!

---

