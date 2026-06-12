---
title: "AVCHD question &amp; camcorder feedback."
date: 2008-11-14
forum: Ubuntu Studio
---

### Post by transmutated on 2008-11-14
Hello everyone. I was wondering if there were any Ubuntu users currently converting AVCHD files to avi or anything else usable under Ubuntu. I am considering picking up a Canon HG20 and editing under Ubuntu with one of the NLEs available. 

According to this link, [http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/]("http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/"), it is possible to transcode the files under Ubuntu. I haven't tried it yet as I don't have the camcorder. 

The next dilemma I am facing is what camcorder to get and what users are having success with whichever ones you have. If I deviate from the HG20, I will go with a tape based camera, Canon HV30, as those are typically considered "better" quality since they avoid the compression element. Not to mention the fact you don't have to spend hours transcoding your video on import. 

So what Camcorders are you all using? I'd like to go with an HD camcorder, I'm saving for a new monitor to support a native HD 1080 resolution as my current 1680 x 1050 is just under it:) Lastly on feedback, what NLE do you use?

Oh yea, I almost forgot, if anyone is transcoding avchd video, what is your setup? I currently have an AMD X2 6000, 8gb ram, 2 180gb sata II hard drives, and a bunch of other stuff. From the sounds of it, I'll need a quad core to soften the blow of transcoding.

---

### Post by FakeOutdoorsman on 2008-11-15
Where I work we just got the Panasonic HMC150 AVCCAM last week.  I can transcode the files without problems on my old computer with just ffmpeg, but I compile my own ffmpeg.  I haven't had the chance to really use the camcorder yet, but I did get some raw test footage from dvxuser.com before buying it.  That's an excellent site to ask questions because there are some knowledgeable users hanging around there.  I haven't edited any footage yet either, but I use a Windows partition with Adobe Premiere Pro 2.0 for editing.  Adobe Creative Suite is the only reason I still have Windows.  CS 4 claims to have native AVCHD editing ability, but I haven't tried it yet and I have an older computer: P4 3 Ghz, 2 GB RAM, 2 500 GB SATA hard drive.  We won't be using my computer for the editing of AVCHD.  If I were to use my computer, one option would be to transcode to an easy to edit working proxy for editing and then send the project file to a faster computer to work with the AVCHD footage.

The HV30 is using an older format and isn't usually considered "better" visually, although it is considered easier to edit on an older machine.  Archiving is easy with tapes too.  Depending on your setup, how much you want to spend, and your final audience, HDV may work for you.  A friend of mine uses a JVC GY-HD110U HDV camcorder and sends to footage to several national cable stations for their programs and they are fine with it.  Read [Know Your Formats, Part 1]("http://digitalcontentproducer.com/hdhdv/depth/know_your_formats_0414/") and [Know Your Formats, Part 2]("http://digitalcontentproducer.com/hdhdv/depth/know_your_formats_0428/") for some comparisons of DV, HDV, DVCPRO-HD, XDCAM-HD, and AVCHD.

To compile your own ffmpeg:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

Also, check out the [Canon Vixia HG20 Camcorder Review]("http://www.camcorderinfo.com/content/Canon-Vixia-HG20-Camcorder-Review-35510.htm") and [Canon HV30 Camcorder Review]("http://www.camcorderinfo.com/content/Canon-HV30-Camcorder-Review-34401.htm") at camcorderinfo.com.

---

### Post by Malcy on 2008-11-17
I have mts2avi setup on my computer and it works well. It would be nice to be able to edit the files from my HG10 natively as I can in Windows with Sony Vegas. As for hardware, I had an Athlon 64 3200+ setup and it chugged when transcoding these files. I have since rebuilt to a quad core Intel Q660 running at just over 3GHz which takes the transcoding in it's stride.

---

