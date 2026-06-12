---
title: "HOWTO: Proper Screencasting on Linux"
date: 2010-01-27
forum: Tutorials
---

### Post by verb3k on 2010-01-27
post withdrawn, sorry for the inconvenience.

---

### Post by Bonster on 2010-01-29
**Note:** *This was the original post not done by me, but i will try to update if anything new comes up*
> Demo Video [http://www.youtube.com/watch?v=Ewxm6T6rXP0]("http://www.youtube.com/watch?v=Ewxm6T6rXP0") 


While many screencasting tools exist on Linux, none of them is able to really pull a high-quality screencast. I&#8217;ve tried almost all existing tools such as recordmydesktop, xvidcap, istanbul, wink etc.. and all of them produced poor results. Horrible video/audio quality, bad sync, lots of limitations, and some even simply segfault while doing the recording. The real solution and the ultimate answer to all your screencasting needs on Linux has been there for quite a long time. It is called FFmpeg. I am surprised to see that many people would just overlook this awesome piece of software.

**[SIZE="4"][COLOR="DarkRed"]What is FFmpeg?[/COLOR][/SIZE]**

From the official website:

Quote:
> FFmpeg is a complete, cross-platform solution to record, convert and stream audio and video. It includes libavcodec &#8211; the leading audio/video codec library.

In this tutorial, I&#8217;ll suppose you&#8217;re using Ubuntu Linux Karmic or Lucid, but the tutorial should also work for other versions with slight modifications.

**[SIZE="4"][COLOR="black"][COLOR="DarkRed"]Preparation:[/COLOR][/COLOR][/SIZE]**

For this tutorial, you&#8217;ll need FFmpeg (preferably a recent revision) compiled with "--enable-x11grab" and the following libraries:

* libx264
* libfaac
* libvpx
* libvorbis
* libxvid
* libmp3lame
* libtheora

Because the version of FFmpeg that is available in the repositories is not compiled with these libraries, you need to compile it yourself. There is an easy-to-follow guide for compiling FFmpeg on ubuntu with those libraries here:

> [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

At this point, you should have the latest FFmpeg built with the needed encoding libraries. Let&#8217;s go to our main subject:

**[SIZE="4"][COLOR="DarkRed"]Screencasting:[/COLOR][/SIZE]**

We will do screencasting in 2 steps:

* Capture a lossless, crystal-clear video stream with lossless audio.
* Encode the resulting lossless file to a compressed version suitable for internet use.

The reason we&#8217;re doing it in a 2-step scheme (instead of just encoding directly as we capture) is that compressing a video with good quality takes some time and processing power that isn&#8217;t possible on the fly. The idea is to use the first step to only capture lossless audio/video feeds as fast as possible and store them, then use the 2nd step to do the real compression and get a better result. The 2nd step is needed because the losslessly-captured file is tremendously large to be used on the web.

**[SIZE="4"]Step 1:[/SIZE]**

Just for the record, basic ffmpeg syntax is:

Code:
> ffmpeg [input options] -i [input file] [output options] [output file]

Learn by example, fire up your terminal application and enter the following command:

Code:
> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv


Then press Enter to start the capturing process. To stop recording, go back to the terminal and press q.

In the above command, we capture audio from pulse (pulseaudio sound server) and encode it to lossless raw PCM with 2 audio channels (stereo). Then, we grab a video stream from x11 at a frame rate of 30 and a size of 1024×768 from the display :0.0 and encode it to lossless h264 using libx264. Using -threads 0 means automatic thread detection. If your distribution does not use the pulseaudio sound system, see FAQ section. The resulting streams will be muxed in a Matroska container (.mkv). The output file &#8220;output.mkv&#8221; will be saved to the current working directory.

Before we move to step 2, let&#8217;s look at things you can change in step 1. Obviously, the most important of which is the resolution. If you want to capture your entire desktop, then you have to enter the screen resolution you&#8217;re working at. It is also possible to capture a specific area of the screen by specifying a capture size that is smaller than the resolution. You can optionally offset this area by adding +X,Y after :0.0 which means it will look something like this:

Code:
> -s 800x600 -i :0.0+200,100

This tells it to capture a rectangle of 800×600 with an X offset of 200 pixels and a Y offset of 100 pixels (the offset starting point is the top-left corner of the screen). Note that if you offset the capture area out of the screen, it will give you an error.

Another thing you can change is the video frame rate (FPS). In the example above we used -r 30 which means capture at 30 FPS. You can change this value to whatever frame rate you want.

**[SIZE="4"]Step 2:[/SIZE]**

Now that we have the lossless file, let&#8217;s encode it to suit our needs. From here on, it all depends on what you&#8217;re planning to do with your screencast, but we&#8217;ll provide some basic examples and from there you move on.

**Example 1:**

Code:
> ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -preset slow -crf 22 -threads 0 our-final-product.mp4

In the above example, we encode the audio to AAC at a bitrate of 128k with 2 audio channels (stereo). We encode the video to the high quality H.264 video compression standard. We use the preset "slow" and a CRF value of 22 for rate control. The output file will be named &#8220;our-final-product.mp4&#8243; and will be muxed in an .mp4 container. Note that FFmpeg determines the container format of the output file based on the extension you specify (i.e. if you specify the extension as .mkv, your file will be muxed into an .mkv matroska container). You can tweak the CRF value to get different results. The lower you set the CRF value, the better your video&#8217;s quality will be, and consequently the file size and encoding time will increase, and vice-versa.

**Example 2:**

WebM is a new, high-quality, free/open format that can be played in modern web browsers that support the HTML5 <video> tag. Since libvpx does not have a constant quality mode yet, we're doing the encode in 2 passes:

Pass 1:
Code:
> ffmpeg -i output.mkv -an -vcodec libvpx -b 1000k -pass 1 our-final-product.webm

Pass 2:
Code:
> ffmpeg -i output.mkv -acodec libvorbis -ab 128k -ac 2 -vcodec libvpx -b 1000k -threads 2 -pass 2 our-final-product.webm

Change the bitrate (-b 1000k) to control the size/quality tradeoff. Also, change the number of threads (-threads 2) to suit the number of threads your CPU has. If your CPU is not multi-threaded, you can omit the -threads option completely. If you have a modern web browser, you can open the file and play it natively inside it. A WebM file consists of VP8 video and Vorbis audio mulitplexed into a .webm container (which is basically a subset of the Matroska container, aka .mkv).

**Example 3:**

Code:
> ffmpeg -ss 00:00:10 -t 00:07:22 -i output.mkv -acodec libvorbis -ab 128k -ac 2 -vcodec libx264 -preset slow -crf 22 -threads 0 our-final-product.mkv

Usually when you start screencasting, there will be a few moments of &#8220;getting ready&#8221; that you may want to cut out of your final product. Same thing near the end. It is possible to only encode a specific range of the original lossless file you captured using the -ss and -t options. These options can come before the input file option (i.e. before -i output.mkv) or after it. If they are specified after it, seeking will be more accurate but a lot slower. In the above example, we specified the starting point of the encoding of our final product after 10 seconds from the start of the original input file using -ss 00:00:10. We also specify the duration of the encoding to be 7 minutes and 22 seconds, because we want to effectively cut something at the end we don&#8217;t want to show. If there isn&#8217;t anything you want to hide at the end, you can just omit the -t option altogether. We use Vorbis and H.264 for the audio and video respectively and mux the entire thing to an .mkv container. This mix of Vorbis/H.264/Matroska is my favorite .

**Example 4:**

Code:
> ffmpeg -i output.mkv -acodec libmp3lame -ab 128k -ac 2 -vcodec libxvid -qscale 8 -me_method full -mbd rd -flags +gmc+qpel+mv4 -trellis 1 -threads 0 our-final-product.avi

Here we have a typical avi with xvid and mp3. The options from &#8220;-me_method full&#8221; to &#8220;-trellis 1&#8243; are encoding parameters for libxvid. You can see that we used libmp3lame to encode the audio with the same options we used for the other examples. For video, tweaking the value of -qscale will give different results. Smaller value means higher video quality but increased file size and encoding time (Similar to libx264&#8217;s -crf in the first example) . The output file is muxed into an .avi container.

Example 5:

Code:
> ffmpeg -i output.mkv -acodec libvorbis -ab 128k -ac 2 -vcodec libtheora -b 1000k our-final-product.ogg

In the above example, we have a completely free file , with vorbis for audio and theora for video. The video is encoded at 1000k bitrate and the output file is muxed to an .ogg container. The audio quality should be great since vorbis is a great audio codec, but the video quality will not be as good. Theora lags behind in almost every aspect of video compression. See the WebM example above (example 2) for a better free and open alternative.

There are many tricks you can use with step 2. You can record your entire desktop at step 1 and then crop it in step 2 to only cover the area you worked on. You can also resize your screencast in step 2. Dealing with these situations and many others is beyond the scope of this tutorial.


**[SIZE="4"][COLOR="DarkRed"]FAQ:[/COLOR][/SIZE]**

**[COLOR="SeaGreen"]Q:[/COLOR]** **How do I get the exact size and coordinates of a specific window I want to capture?**
**[COLOR="Blue"]A:[/COLOR]** Use a command called &#8220;xwininfo&#8220;. Basically, you run this command and then click on the window that you want to capture. It will then print the window information to the terminal. This command prints a lot of information, but what you need are the following lines:

Absolute upper-left X:
Absolute upper-left Y:
Width:
Height:

If the command, for example, prints:

Absolute upper-left X: 383
Absolute upper-left Y: 184
Width: 665
Height: 486

Then, you will adapt it to FFmpeg like this:

-s 664x486 -i :0.0+383,184

Note that we used 664 instead of 665 for the width since ffmpeg only accepts resolutions divisible by 2.
You can use the following command line combination with "xwininfo" to only print the information you&#8217;ll be needing:

Code:
> xwininfo | grep -e Width -e Height -e Absolute

**[COLOR="SeaGreen"]Q:[/COLOR]** **How can I control PulseAudio input? (e.g. capture application audio instead of mic)**
**[COLOR="Blue"]A:[/COLOR]** Install &#8220;pavucontrol&#8220;. Start recording with ffmpeg. Start pavucontrol. Go to the &#8220;Recording&#8221; tab and you&#8217;ll find ffmpeg listed there. Change audio capture from &#8220;Internal Audio Analog Stereo&#8221; to &#8220;Monitor of Internal Audio Analog Stereo&#8220;.
Now it should record system and application audio instead of microphone.

This setting will be remembered. The next time you want to capture with FFmpeg, it will automatically start recording system audio. If you want to revert this, use pavucontrol again to change back to microphone input.

**[COLOR="SeaGreen"]Q:[/COLOR]** **What are the recommended codecs/container to use if I&#8217;m planning to upload my screencast to YouTube?**
**[COLOR="Blue"]A:[/COLOR]** YouTube recommends uploading clips using H.264 for the video and AAC for the audio in an .mp4 container (as in example 1 of step 2). This is the safest format to upload into because some codecs do have issues with YouTube. Refer to this page for other recommended codecs and containers for YouTube.

**[COLOR="SeaGreen"]Q:[/COLOR]** **What do I do if my system does not use the PulseAudio sound server?**
**[COLOR="Blue"]A:[/COLOR]** Most recent Linux distributions have PulseAudio installed by default, but if your system does not have PulseAudio, then try replacing &#8220;-f alsa -ac 2 -i pulse&#8221; with something like:

-f alsa -ac 2 -i hw:0,0

Many users of this guide reported success with the above options. You might have to change the 0,0 to match that of your sound device. You could also try:

-f alsa -ac 2 -i /dev/dsp

Other users reported success with:

-f oss -ac 2 -i /dev/dsp

Basically there are many ways to do it, and it depends on your system&#8217;s sound configurations and hardware.

**[COLOR="SeaGreen"]Q:[/COLOR]** **How can I pause/resume screencasting?**
**[COLOR="Blue"]A:[/COLOR]** That isn&#8217;t possible with ffmpeg yet, but you can use mkvmerge to achieve the same result. You can install this program from your distribution&#8217;s package management system under the package name mkvtoolnix, or download it from the official website. This program allows you to concatenate mkv files with identically-encoded streams to a single file. Meaning that if you want to make a pause from screencasting, you&#8217;ll just stop recording part 1, then start recording part 2 as another file, and finally concatenate (i.e. add) these 2 parts into a single screencast ready for final compression. You can do this for as many parts as you like. Example:

Code:
> mkvmerge -o complete.mkv part1.mkv +part2.mkv +part3.mkv +part4.mkv

This command pruduces a video file named &#8220;complete.mkv&#8221; that has all the parts put together in the order they were specified into on the command line.

However, note that all the parts you want to concatenate must have exactly the same size/framerate/encoding parameters, otherwise it won&#8217;t work. You can&#8217;t add files with different encoding options to each other.

Final note, before you start recording part 2 of your screencast, be sure to change the output file name, or else your previous precious work might be overwritten.

**[COLOR="SeaGreen"]Q:[/COLOR]** **I want to select an area of the screen with my mouse and get ffmpeg to record it. Is it possible?**
**[COLOR="Blue"]A:[/COLOR]** Yes! There is a simple tool called "xrectsel" that you can use to select an area of the screen by drawing with your mouse, and it will print your selection coordinates which you can then use in ffmpeg. This tool comes as an auxiliary tool with the "FFcast2" bash script that wraps around ffmpeg's screencasting abilities

> [https://bbs.archlinux.org/viewtopic.php?id=127570]("https://bbs.archlinux.org/viewtopic.php?id=127570")
> [https://github.com/lolilolicon/FFcast2#readme]("https://github.com/lolilolicon/FFcast2#readme")

**[COLOR="SeaGreen"]Q:[/COLOR]** **How do I hide the mouse cursor?**
**[COLOR="Blue"]A:[/COLOR]** Add "+nomouse" after ":0.0" to look like this:
Code:
> :0.0+nomouse

(thanks again FakeOutdoorsman)

**[COLOR="SeaGreen"]Q:[/COLOR]** **I have a problem, error message, or ffmpeg doesn't work the way I expected it to do. How do I get help?**
**[COLOR="Blue"]A:[/COLOR]** The best way to get help with ffmpeg is to login to the official IRC support channel for ffmpeg #ffmpeg @ irc.freenode.net, because 1) you will get an instant reply or engage in discussion about your problem and provide realtime feedback 2) the developers of ffmpeg know more about ffmpeg and its problems than we do (and they almost always hang around there and help people). If you want to ask for help here, you're most welcome. We'll try our best to support you, but bear in mind that the answer might come late, or we may not be able to help you with your problem.



**Credits**

verb3k
Dark_Shikari
FakeOutdoorsman

> [http://blog.devinrkennedy.com/2009/10/live-screencasting-using-ffmpeg.html]("http://blog.devinrkennedy.com/2009/10/live-screencasting-using-ffmpeg.html")


Updates:
Added FFcast2 reference link
changed syntax for new presets format on step1 (Thanks FakeOutdoorsman)
Removed all broken links, other junks

---

### Post by hachel on 2010-02-01
how would you encode to flv so that I can share it on my website with the JW Player?

---

### Post by verb3k on 2010-02-01
> **Bonster said:**
> Question: how u make it record speaker sound instead of mic sound, or make it record both at the same time?

I honestly don't know :) I would like to know the answer too.


[QUOTE=hachel]how would you encode to flv so that I can share it on my website with the JW Player? [/QUOTE]

You would use almost the same commandline for the Example 1:

```
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -wpredp 0 -crf 22 -threads 0 our-final-product.flv
```

The only difference is the use of "-wpredp 0" after "-vpre slow" and the changing of the file extension to .flv.
(Thanks for pasteeater and Dark_Shikari at #ffmpeg who actually provided the answer)

---

### Post by FakeOutdoorsman on 2010-02-03
Added a link to your guide on [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).  I'll make sure to forward disgruntled recordMyDesktop users here.

---

### Post by kung fu buntu on 2010-02-07
> **Bonster said:**
> Question: how u make it record speaker sound instead of mic sound, or make it record both at the same time?

> **verb3k said:**
> I honestly don't know :) I would like to know the answer too.
So do I. And there is an ongoing dicussion [here]("http://ubuntuforums.org/showthread.php?p=8762089#post8762089")


> **verb3k said:**
> -vcodec libx264 -vpre hq -crf 22 -threads 0
Using those settings eats all my cpus.
How could I record it "lossless" and then after the recording is finished encode it with these hardcore settings?

It is possible to set some kind of shortcut key that then allows you to pause recording? (like in recordmydesktop)

---

### Post by FakeOutdoorsman on 2010-02-07
> **kung fu buntu said:**
> Using those settings eats all my cpus.
How could I record it "lossless" and then after the recording is finished encode it with these hardcore settings?

Recording a desktop using a lossless preset is often faster and results in more fps being recorded.  However, the resulting file can end up being fairly large and re-encoding with the lossy preset gives the advantage of a smaller file size in exhange for a small (often unnoticed by some) loss of quality.

If the lossless output works for you then you can skip the re-encoding.

---

### Post by Anubis on 2010-02-07
> **Bonster said:**
> Question: how u make it record speaker sound instead of mic sound, or make it record both at the same time?

Use gtk-recordmydesktop, and skip this tortuous method.

---

### Post by kung fu buntu on 2010-02-08
> **Anubis said:**
> Use gtk-recordmydesktop, and skip this tortuous method.
If you know a workaround for RMD problems, I would be gratefull. See [here]("http://ubuntuforums.org/showthread.php?p=8790472#post8790472")

And the tutorial is very good in my opinion.

---

### Post by sbelz79 on 2010-03-02
I got errors trying to install the libvorbis/libtheora libraries:


```
user@computer:~$ sudo add-apt-repository ppa:towolf/codecs && sudo apt-get update && sudo apt-get install libvorbis0a libvorbis-dev libtheora0 libtheora-dev
[sudo] password for user: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 97C2201DE6018A3EFD75D884105054032EE163BB
gpg: requesting key 2EE163BB from hkp server keyserver.ubuntu.com
gpg: key 2EE163BB: "Launchpad PPA for Tobias Wolf" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg                                                                                                                                                           
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                                                                                                                                                
Hit http://security.ubuntu.com karmic-security Release.gpg                                                                                                                                                    
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                                                                                                                                         
Ign http://archive.ubuntu.com karmic Release.gpg                                                                                                                                                              
Ign http://archive.ubuntu.com karmic/main Translation-en_US                                                                                                                                                   
Hit http://archive.canonical.com karmic Release.gpg                                                                                                                                                           
Ign http://archive.canonical.com karmic/partner Translation-en_US                                                                                                                                             
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                                                                               
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                                                     
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                                                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                                                     
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                                                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                                                     
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US                                                                                                                           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US                                                                                                                 
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US                                                                                                               
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                                                                                                                        
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US                                                                                                             
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US                                                                                                       
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US                                                                                                         
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US                                                                                                       
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                                                                                                        
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                                                                                                          
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                                                                                                        
Hit http://us.archive.ubuntu.com karmic Release                                                                                                                                    
Hit http://security.ubuntu.com karmic-security Release                                                                                                                             
Hit http://ppa.launchpad.net karmic Release                                                                                                                                        
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                                                                                                                    
Hit http://archive.canonical.com karmic Release                                                                                                                                                         
Ign http://archive.ubuntu.com karmic Release                                                                                                                                                            
Hit http://repository.glx-dock.org karmic Release.gpg                                                                                                        
Ign http://repository.glx-dock.org karmic/cairo-dock Translation-en_US                                                                                                             
Hit http://us.archive.ubuntu.com karmic-updates Release                                                                                                                            
Hit http://ppa.launchpad.net karmic Release                                                                                                                                                             
Hit http://ppa.launchpad.net karmic Release                                                                                                                                                             
Hit http://ppa.launchpad.net karmic Release                                                                                                                                                             
Hit http://packages.medibuntu.org karmic Release.gpg                                                                                                                                                    
Ign http://packages.medibuntu.org karmic/free Translation-en_US                                                                                                                                         
Hit http://security.ubuntu.com karmic-security/main Packages                                                                                                                                            
Hit http://archive.canonical.com karmic/partner Packages                                                                                                                                                
Ign http://archive.ubuntu.com karmic/main Packages                                                                                                                                 
Hit http://repository.glx-dock.org karmic Release                                                                                                            
Hit http://us.archive.ubuntu.com karmic/main Packages                                                                                                      
Hit http://us.archive.ubuntu.com karmic/restricted Packages                                                                            
Hit http://us.archive.ubuntu.com karmic/main Sources                                                                                                         
Hit http://us.archive.ubuntu.com karmic/restricted Sources                                                                                                   
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                            
Hit http://ppa.launchpad.net karmic/main Sources                                                                                                             
Hit http://security.ubuntu.com karmic-security/restricted Packages                                                                                           
Hit http://security.ubuntu.com karmic-security/main Sources                                                                            
Hit http://security.ubuntu.com karmic-security/restricted Sources                                                                      
Hit http://security.ubuntu.com karmic-security/universe Packages                                                                       
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US                                                                                          
Hit http://packages.medibuntu.org karmic Release                                                                                                             
Ign http://archive.ubuntu.com karmic/universe Packages                                                                                                       
Hit http://us.archive.ubuntu.com karmic/universe Packages                                                                              
Hit http://us.archive.ubuntu.com karmic/universe Sources                                                                               
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                                                                            
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                                                                             
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                            
Hit http://us.archive.ubuntu.com karmic-updates/main Packages                                                                                                
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages                                                                                          
Hit http://security.ubuntu.com karmic-security/universe Sources                                                                                              
Hit http://security.ubuntu.com karmic-security/multiverse Packages                                                                                           
Hit http://security.ubuntu.com karmic-security/multiverse Sources                                                                                            
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                                                                                                 
Hit http://ppa.launchpad.net karmic/main Packages                                                                                      
Hit http://ppa.launchpad.net karmic/main Packages                                                                                      
Hit http://packages.medibuntu.org karmic/free Packages                                                                                 
Ign http://archive.ubuntu.com karmic/main Packages                                                               
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources                         
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages                          
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources                           
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages                                              
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources                                               
Hit http://packages.medibuntu.org karmic/non-free Packages                                                       
Ign http://archive.ubuntu.com karmic/universe Packages                                     
Err http://archive.ubuntu.com karmic/main Packages                   
  404  Not Found [IP: 91.189.88.45 80]
Hit http://repository.glx-dock.org karmic/cairo-dock Packages
Err http://archive.ubuntu.com karmic/universe Packages
  404  Not Found [IP: 91.189.88.45 80]
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/main Translation-en_US
Get:2 http://dl.google.com stable Release [2,540B]
Get:3 http://dl.google.com stable/main Packages [909B]
Fetched 3,638B in 3s (1,201B/s)
W: Failed to fetch http://archive.ubuntu.com/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/dists/karmic/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I've been getting the same 404 and failed to fetch errors when I open the update manager and click "check."

I'm running Ubuntu 9.10 x86_64

---

### Post by verb3k on 2010-03-02
You can do the commands one by one:
```
sudo add-apt-repository ppa:towolf/codecs
```
```
sudo apt-get update
```
```
sudo apt-get install libvorbis0a libvorbis-dev libtheora0 libtheora-dev
```
You should be able to install the libvorbis/theora even if some repositories fail to update.

---

### Post by ccleanerfan on 2010-03-03
A GUI would be nice =/

---

### Post by sbelz79 on 2010-03-04
It's been a bumpy road, but I'm getting there.  I installed ffmpg successfully, and I can make a lossless video recording of my desktop- but there's no sound.  I have pulseaudio, but I already tried replacing "-i pulse" with "-i /dev/dsp", but got a message that there's no such file or directory named /dev/dsp.  

Here's my output from  recording a test video (where I play music in songbird and play a movie with vlc):

```
usr@cmptr:~/screencasts$ ffmpeg -f alsa -i pulse -f x11grab -r 30 -s 1680x1050 -i :0.0 -acodec flac -vcodec libx264 -vpre lossless_ultrafast -threads 0 output03.mkv
FFmpeg version SVN-r22170, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar  3 2010 08:46:02 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.55. 0 / 52.55. 0
  libavformat   52.54. 0 / 52.54. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0x2bce3c0]capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x2bce3c0]Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1267689871.428564, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
[x11grab @ 0x2bedad0]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1050
[x11grab @ 0x2bedad0]shared memory extension  found
[x11grab @ 0x2bedad0]Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1267689871.649909, bitrate: 1693440 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1680x1050, 1693440 kb/s, 30 tbr, 1000k tbn, 30 tbc
[libx264 @ 0x2bfcb90]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x2bfcb90]profile High 4:4:4 Predictive, level 4.0
Output #0, matroska, to 'output03.mkv':
  Metadata:
    encoder         : Lavf52.54.0
    Stream #0.0: Video: libx264, yuv420p, 1680x1050, q=10-51, 200 kb/s, 1k tbn, 30 tbc
    Stream #0.1: Audio: flac, 44100 Hz, 1 channels, s16, 64 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=  883 fps= 24 q=-1.0 Lsize=   24540kB time=36.78 bitrate=5465.8kbits/s dup=0 drop=18    
video:24527kB audio:4kB global headers:0kB muxing overhead 0.037449%
[libx264 @ 0x2bfcb90]frame I:4     Avg QP: 0.00  size:802543
[libx264 @ 0x2bfcb90]frame P:879   Avg QP: 0.00  size: 24920
[libx264 @ 0x2bfcb90]mb I  I16..4: 32.8%  0.0% 67.2%
[libx264 @ 0x2bfcb90]mb P  I16..4: 10.1%  0.0%  0.0%  P16..4:  1.4%  0.0%  0.0%  0.0%  0.0%    skip:88.5%
[libx264 @ 0x2bfcb90]coded y,uvDC,uvAC intra: 23.8% 20.4% 20.3% inter: 1.2% 1.3% 1.3%
[libx264 @ 0x2bfcb90]i16 v,h,dc,p: 87% 13%  0%  0%
[libx264 @ 0x2bfcb90]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 23% 36%  3%  2% 29%  2%  2%  1%  2%
[libx264 @ 0x2bfcb90]kb/s:6826.21
```

And here's what I got in the terminal when I played the resulting video in vlc:
```
usr@cmptr:~/screencasts$ vlc output03.mkv 
VLC media player 1.0.2 Goldeneye
[0x23d0888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x3443ad8] pulse audio output: No. of Audio Channels: 1
[0x2823028] main input error: ES_OUT_RESET_PCR called
usr@cmptr:~/screencasts$
```

---

### Post by verb3k on 2010-03-04
From what I see, the pulseaudio recording is working fine for you. Make sure the microphone is connected properly and (more importantly) that it is not muted or turned down.

EDIT: Are you trying to record sound from microphone or sound from your desktop? if it's the second case, then it should be possible but I don't actually know how.

---

### Post by sbelz79 on 2010-03-04
The 2nd case- I was trying to record sound from my desktop (from VLC and Songbird).  I don't have a mic, so I can't test to see if that works.

---

### Post by mocha on 2010-03-05
To capture sounds from within the computer (like from webpages or media players) when using ffmpeg x11grab, after you execute ffmpeg just go to the pulseaudio volume control, select the recording tab and you should see ffmpeg appear there.  Then move it's stream to the monitor of internal audio... or whatever it's called on your system.  Once your audio starts playing you'll see the recording VU meter bumping.  This is the real power of pulseaudio.

BTW, thanks very much for this tutorial!  I will use ffmpeg to start capturing videos that I can't rip from certain websites.  recordmydesktop feels a bit long in the tooth after trying the x11grab method.

---

### Post by hachel on 2010-03-05
thanks,
that works, though the recorded sound sounds like it has been recorded with a mic with the levels upped to the max.

note: I had to install pavucontrol in order to get the pulseaudio-controlcenter

Now, if there were a way to shift the stream via the terminal (and beforehand), that would be awesome...

---

### Post by verb3k on 2010-03-05
Based on expert recommendations (relaxed at #ffmpeg), the guide has been updated to use pcm_s16le in step 1 instead of flac, because it is faster and utilizes less CPU. This shouldn't make a big difference to end users because both formats are lossless.

---

### Post by mocha on 2010-03-06
I've been using this method and it works really well for grabbing videos from webpages that can't be grabbed in any other way.  You can add "-t hh:mm:ss" to limit the capture time for unattended recording.

One thing I noticed is that this method is only "seeing" mono audio.  I always see this regardless of the source audio:

Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s

What exactly is the options "-f alsa -i pulse" doing?  I also tried "-ac 2" which produces an output file with 2 channels, but the problem is on the input side.  The input only sees 1 channel for some reason.

---

### Post by andrew.46 on 2010-03-07
Hi verb3k,

Thanks for the great guide :). A small query about Example 4: had you considered using the FFmpeg native 'Xvid' (MPEG-4) encoder rather than the external xvid library? Some details here:

3.10 How do I encode Xvid or DivX video with ffmpeg?
[http://www.ffmpeg.org/faq.html#SEC22](http://www.ffmpeg.org/faq.html#SEC22)

In my experience the FFmpeg version looks better and runs faster, but I would be interested to hear the experiences of others with this...

All the best,

Andrew

---

### Post by verb3k on 2010-03-08
> **andrew.46 said:**
> Hi verb3k,

Thanks for the great guide :). A small query about Example 4: had you considered using the FFmpeg native 'Xvid' (MPEG-4) encoder rather than the external xvid library? Some details here:

3.10 How do I encode Xvid or DivX video with ffmpeg?
[http://www.ffmpeg.org/faq.html#SEC22](http://www.ffmpeg.org/faq.html#SEC22)

In my experience the FFmpeg version looks better and runs faster, but I would be interested to hear the experiences of others with this...

All the best,

Andrew

Actually I hadn't :D
I hardly encode anything to MPEG-4 ASP, so for the sake of the guide I went straight to xvid because I thought FFmpeg's ASP encoder wasn't as good as xvid, which turned out to be a surprise. Your comment triggered my interest to do a small comparison and the result was that they were visually very close, I couldn't make out any real difference between the two. The internal encoder had a huge edge in speed as you said. I will perhaps update the guide with a fifth example. (xvid's presence is a must to assure those who want nothing but "xvid" :D )

Thanks for your useful suggestion,
verb3k

---

### Post by mocha on 2010-03-28
Verb3k,

There's a minor problem with the order of command line options in the first post which causes ffmpeg to only "see" 1 audio channel on the incoming side.  The proper syntax order for 2 channel capture is therefore:

```
ffmpeg [COLOR="Red"]-f alsa -ac 2 -ab 128k -i pulse -acodec pcm_s16le[/COLOR] -f x11grab -r 30 -s 1280x1024 -i :0.0 -aspect 4:3 -vcodec libx264 -vpre lossless_ultrafast -threads 0 SCREENCAST.mkv
```

You can also specify an audio bitrate after the "-ac 2" part as I've shown, but if you don't it just defaults to 64 kbps.  This method always captures to MP2 audio and I'm not sure why.  I experimented with AAC audio capture and MPEG4 and AVI containers, but they don't work very well.

Thanks for making this tutorial!  I'll never touch recordmydesktop again!

---

### Post by hugmenot on 2010-03-28
You could add a use case for encoding using flashsv codec.

It as four advantages:

[LIST]
[*]Fast
[*]Good for postproduction editing. 
[*]Output file is directly playable in browser using Flash Plugin.
[*]Encoding is lossless /and/ RGB. This means that you get true losslessness and not YUV color subsampling as in x264
[/LIST]

Disadvantage, it is high bitrate. FFMpeg is looking at flashsv2, which is more efficient, but there are few bitstream examples in the wild.

Byzanz offers flashsv nowadays too.

---

### Post by verb3k on 2010-03-28
> **mocha said:**
> Verb3k,

There's a minor problem with the order of command line options in the first post which causes ffmpeg to only "see" 1 audio channel on the incoming side.  The proper syntax order for 2 channel capture is therefore:

```
ffmpeg [COLOR="Red"]-f alsa -ac 2 -ab 128k -i pulse -acodec pcm_s16le[/COLOR] -f x11grab -r 30 -s 1280x1024 -i :0.0 -aspect 4:3 -vcodec libx264 -vpre lossless_ultrafast -threads 0 SCREENCAST.mkv
```

You can also specify an audio bitrate after the "-ac 2" part as I've shown, but if you don't it just defaults to 64 kbps.  This method always captures to MP2 audio and I'm not sure why.  I experimented with AAC audio capture and MPEG4 and AVI containers, but they don't work very well.

Thanks for making this tutorial!  I'll never touch recordmydesktop again!

You don't need to specify a bitrate when you capture raw PCM. Also, since the input is usually a mic, so there is no difference whether you record with -ac 2 or not. It will have the same audio on 2 channels once you encode your compressed version.

I'm glad you found the tutorial useful :)

---

### Post by 2hot6ft2 on 2010-03-29
> **verb3k said:**
> 
[SIZE="4"]**Step 2:**[/SIZE]

**Example 3:**

```
ffmpeg -ss 10 -t  07:22 -i output.mkv -acodec libvorbis -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 22 -threads 0 our-final-product.mkv
```

In the above example, we specified the starting point of the encoding of our final product after 10 seconds from the start of the original input file using -ss 10. We also specify the duration of the encoding to be 7 minutes and 22 seconds

**Example 4;**

```
ffmpeg -i output.mkv -acodec libmp3lame -ab 128k -ac 2 -vcodec libxvid -qscale 8 -me_method full -mbd rd -flags +gmc+qpel+mv4 -trellis 1 -threads 0 our-final-product.avi
```

Here we have a typical avi with xvid and mp3.
Shortened version of the guide above for quick reference.

If I take the first part in example 3 and add it to the command in example 4 to specify the duration of the encoding.
Example
```
ffmpeg -t  03:48 -i output.mkv -acodec libmp3lame -ab 128k -ac 2 -vcodec libxvid -qscale 8 -me_method full -mbd rd -flags +gmc+qpel+mv4 -trellis 1 -threads 0 our-final-product.avi
```

Using a capture length of 3 min.54 sec. and using -t 03:48 should trim it at 3 min. 48 sec. but instead trims it at 3.0 seconds.
Changing it to - t 00:03:48 trims it properly at 3 min. 48 sec..

Also the file size of the avi is too big (almost 3/4 the size of the mkv) so I found this.
> To have a constant quality (but a variable bitrate), use the option '-qscale n' when 'n' is between 1 (excellent quality) and 31 (worst quality).
So a larger number makes the file smaller (with lower quality) and a lower number makes the file larger (with higher quality).
A setting of 13-14 will make it about 1/2 the size of the mkv file.

Excellent how to, thank you for all your time and effort in creating it. I will be sending people here when they complain about the record my desktop applications in ubuntu.

---

### Post by Nisal on 2010-03-30
ok going to try this thanks /:D

---

### Post by Yesirom on 2010-04-23
What is the best way to record a video for sites like Youtube, Blip etc. ?

I tried a few methods with this but it simply turns out to be crap after the Youtube or Blip finishes with it (making the video literally unrecognizable). 

The quality before is very nice and I love it (HD ftw) ^^

---

### Post by jarmore on 2010-04-24
Thank you this is the cats meow of screencast with mic. I tried everything ... all else had sound sync fail. I'm a copy paste guy ... worked flawlessly. The output was spot on ... actually the sound 'gained' a few after youtube processing. 720 HD eh all :) Thanks!

---

### Post by Yesirom on 2010-04-25
> **jarmore said:**
> Thank you this is the cats meow of screencast with mic. I tried everything ... all else had sound sync fail. I'm a copy paste guy ... worked flawlessly. The output was spot on ... actually the sound 'gained' a few after youtube processing. 720 HD eh all :) Thanks!

So you have no problems? What are your settings?

---

### Post by e_torano on 2010-04-25
Very useful guide thanks. I've been using capturemydesktop but I've found that it doesn't work too well with compiz. How's this solution with it?

---

### Post by verb3k on 2010-05-01
Added explanation of "xwininfo" usage as FAQ stub.
If there is anything you feel this guide is lacking, please tell. Contribution is very welcome.

---

### Post by hugmenot on 2010-05-01
This script automating all this is interesting:

[http://github.com/lolilolicon/ffcast](http://github.com/lolilolicon/ffcast)

I found it when looking for some way to select an area with the mouse. The included xrectsel.c does exactly that and it outputs a geometry tuple.

here&#8217;s the manpage:
```

FFCAST(1)                                                                    FFCAST(1)



NAME
       ffcast - Take screencast using ffmpeg with the help of xwininfo and xrectsel

SYNOPSIS
       ffcast [options]

DESCRIPTION
       ffcast  is  a screencast script written in bash. It calls ffmpeg to capture any
       specified area on the target X11 display. It supports all video codecs and for&#8208;
       mats  ffmpeg supports. Before ffcast actually calls ffmpeg to record the video,
       it determines the capture area either  by  interactively  asking  the  user  to
       select one, or by reading the geometry defined by command line. In the interac&#8208;
       tive mode, the user can either freely select a rectangle area, or select one or
       more windows by clicking them.

OPTIONS
       -o, --output <outfile>
              Specify  output  filename.  Filename extension is essential if FORMAT is
              not set either by config file or from command line  using  --format.  If
              <outfile>  is  -,  output  goes to standard output, in which case FORMAT
              must be set.

       -d, --display <display>
              Display to connect  to.  Format:  [hostname]:number.screen_number,  e.g.
              `:0.1'.  By  default,  ffcast  reads the environment variable DISPLAY as
              display.

       -a, --fullscreen
              Capture full screen, identical to `--winid root'

       -w, --xwininfo
              Use xwininfo to define capture area, either by click  or  by  specifying
              window  ids with the --winid option. This is useful for capturing events
              inside an existing window. You can also select multiple windows,  speci&#8208;
              fying window number with the --winno option.

       -s, --xrectsel
              Freely select capture area by mouse dragging using xrectsel. When ffcast
              is triggered with this option, your mouse cursor changes to a cross. You
              select  your  capture area by dragging your mouse with button 1 pressed.
              Then, if button 1 is released, capture will start instantly; if keyboard
              is pressed instead, capture will abort. Think about `scrot -s'.

       -j, --xjustcap <geometry>
              This option enables the user to tell ffcast about the exact capture area
              using <geometry>, thus no manual selection is performed.  This  is  free
              selection,  like  --xrectsel,  just  without  the  need of touching your
              mouse.

              Supported <geometry> formats are:
              *1) "(x1,y1) (x2,y2)"
              (x1,y1) and (x2,y2) are the positions of two  diagonal  corners  of  the
              rectangle area in question.
              The  comma  between  xN  and  yN  is  required,  but the parentheses are
              optional.
              Any of the x1, y1, x2, y2 parameters consists of digits, or  is  a  per&#8208;
              centage value written as digits%
              If  any  of  x1,  y1,  x2,  y2 is written as percentage, e.g. 20%, it is
              equivalent to 20% of the full x or y resolution of you screen.
              *2) "wxh-x+y gravity"
              w: Width of the rectangle area.
              h: Height of the rectangle area.
              -x: Additional horizontal positioning of the  rectangle,  added  to  the
              initial positioning by gravity. Optional.
              +y:  Additional vertical positioning of the rectangle, added to the ini&#8208;
              tial positioning by gravity. Optional.
              gravity: Determines the initial positioning of the rectangle. Valid val&#8208;
              ues are: Northwest, North, Northeast, East, Southeast, South, Southwest,
              West and Center(or Centre). Optional.
              Any of w, h, x, y parameters consists of  digits,  or  is  a  percentage
              value written as digits%

       -M, --mod16
              Force  capture frame size to be mod 16. ffmpeg requires video frame size
              to be mod 2, which is the default behavior  of  ffcast.  By  using  this
              option,  you  tell  ffcast  to always adjust capture geometry to mod 16.
              This may improve video quality for the x264 encoder, but not too much.

       -n, --winno <number>
              Number of window(s) to be captured. Only effective with --xwininfo,  and
              without  --winid  option. This enables capturing multiple windows. Think
              about the GIMP, and you'll find this option useful.

       -i, --winid <idlist>
              Specify windows to be capture by window  ids.  <idlist>  is  a  list  of
              whitespace  seperated  window ids quoted inside double or single quotes,
              e.g. "0x80000a 0x800039 0x160003c". see xwininfo(1) -id option.

       -b, --borderless
              Ignore borders of window(s).

       -B, --border
              Do not ignore borders. This, as well as --borderless, is only  effective
              with --xwininfo, obviously.

       -c, --codec <codec>
              Force  Output  Video  Codec.  Default value: 'x264'. Use ? or list for a
              list. Use '' to let ffmpeg guess video codec from output extension.

       -f, --format <format>
              Force Output Format. Default value: 'h264'. Use ? or list  for  a  list.
              Use '' to let ffmpeg guess video format from output extension.

       -p, --preset <ffpreset>
              x264  preset.  Default value: 'lossless_slow'. Use ? or list for a list.
              Dive into /usr/share/ffmpeg/*.ffpreset for details.  See  ffmpeg(1)  for
              more info (`Preset files' section).

       -r, --rate <fps>
              Set frame rate (fps). Default value: 15. Set it to a higher level if you
              find your video choppy.

       -t, --duration <time>
              Restrict cast video duration in seconds. hh:mm:ss[.xxx] format  is  also
              fully supported. This is useful for usage in scripts. It's also reported
              by lazy people how this has saved there lives by escaping them from  the
              final [q] press.

       --printcmd
              Don't  actually call ffmpeg, but print the ffmpeg command line and exit.
              You can then further customize this command and then run it directly  to
              do the real job. It is meant for slightly advanced users or curious peo&#8208;
              ple who likes to experiment.

       -v, --debug
              Print verbose debug info to standard error.

       --nocolor
              Disable colors in messages.

       -h, --help
              Print help message, then exit.

       --version
              Print version info, then exit.

CONFIGURATION
       At  start  up,  ffcast  reads  user   configurations   defined   in   $XDG_CON&#8208;
       FIG_HOME/ffcast/ffcast.conf,  if  $XDG_CONFIG_HOME  is not defined, $HOME/.con&#8208;
       fig/ffcast/ffcast.conf is read instead.  An  example  configuration  file  with
       default     values     and     comments     can     be     found    at    $PRE&#8208;
       FIX/share/ffcast/doc/ffcast.conf, where  $PREFIX  is  usually  either  /usr  or
       /usr/local as per build-time settings.  Configuration options in the configura&#8208;
       tion file are all available from the command line, and  will  be  overriden  by
       command line options.

ENVIRONMENT
       DISPLAY To get the default host and display number.

EXAMPLE
       I  want  to  test  a  new  window  manager  inside a window. So I first edit my
       ~/.xinitrc to tell startx to run it instead of my current wm.

       Then I start a new X session inside a new window with

              startx -- /usr/bin/Xephyr :2

       Then I'd like to record this window by clicking it with

              ffcast -d :2.0 -o wmtest.mp4

NOTES
       GIF output is huge and uncompressed due to very limited gif support  from  ffm&#8208;
       peg.  It's best not to use gif output. But if you must, a workaround for now is
       piping output to convert (from ImageMagick):

              ffcast -s -t 6 -r 3 -f gif -o - | convert gif:- ffcast.gif

FILES
       /usr/bin/ffcast
       /usr/bin/xrectsel
       /usr/share/ffcast/doc/ffcast.conf
       Locations may differ due to make settings.

SEE ALSO
       ffmpeg(1), xwininfo(1)

AUTHORS
       ffcast is written by lolilolicon<lolilolicon@gmail.com>



ffcast 0.2                            2009-11-25                             FFCAST(1)

```

---

### Post by alex188 on 2010-05-03
Hi everyone,

  I have a special application. That is I need to use VNC Client to login server and control the server to do something. Then I need to record my VNC screen. So, I used the command "sudo ffmpeg -f x11grab -r 30 -s 800x600 -i :0.0 -vcodec libx264 -vpre hq -threads 0 out1.avi" to record screen, but the video content is server screen not my VNC screen. 

  I check my export variable and get the DISPLAY variable is ":2.0". So I change my command to record ":2.0" and there is error occur. The following is error message.

[alex@taipei:~$] export | grep DISPLAY
declare -x DISPLAY=":2.0"
[alex@taipei:~$] sudo ffmpeg -f x11grab -r 30 -s 800x600 -i :2.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 out1.avi

FFmpeg version SVN-r23008, Copyright (c) 2000-2010 the FFmpeg developers
  built on May  3 2010 11:42:42 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.15. 0 / 50.15. 0
  libavcodec    52.66. 0 / 52.66. 0
  libavformat   52.62. 0 / 52.62. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[x11grab @ 0xaa38420]device: :2.0 -> display: :2.0 x: 0 y: 0 width: 800 height: 600
Xlib:  extension "Generic Event Extension" missing on display ":2.0".
[x11grab @ 0xaa38420]shared memory extension  found
Segmentation fault
[alex@taipei:~$]  

Could anyone give some suggestions for this problem. Thanks a lot!!

---

### Post by verb3k on 2010-05-23
Guide updated.
Removed libvorbis installation instructions as FFmpeg's building guide was updated to include it. Also, expanded the FAQ section.

---

### Post by bashologist on 2010-06-14
Using what I believe to be the latest ffmpeg and I'm getting this error when trying to record from pulse. I've also updated alsa using the upgrade script [http://ubuntuforums.org/showthread.php?p=6589810]("http://ubuntuforums.org/showthread.php?p=6589810").
```
ffmpeg -f alsa -ac 2 -i pulse test.mp3
FFmpeg version SVN-r23603, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 14 2010 07:11:00 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.76. 0 / 52.76. 0
  libavformat   52.68. 0 / 52.68. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM pulse
[alsa @ 0x3104470]cannot open audio device pulse (No such file or directory)
pulse: Input/output error

```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

This command works but it's 100% silent.
```
ffmpeg -f alsa -ac 2 -i hw:0,0 test.mp3
```

If I try to use hw:1,3 which is my hdmi I believe according to aplay I get this.
```
ffmpeg -f alsa -ac 2 -i hw:1,3 test.mp3
FFmpeg version SVN-r23603, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 14 2010 07:11:00 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.76. 0 / 52.76. 0
  libavformat   52.68. 0 / 52.68. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0x1eb7470]cannot open audio device hw:1,3 (No such file or directory)
hw:1,3: Input/output error
```

Any help would be greatly appreciated, thank you.

---

### Post by verb3k on 2010-06-14
If you say this works:
> ffmpeg -f alsa -ac 2 -i hw:0,0 test.mp3
but is silent, then maybe it's an issue with your microphone or input volume?
That usually happens. You can verify if the file has recorded audio but with very low volume by playing it in mplayer and amplifying the audio:

```
mplayer test.mp3 -af volume=60
```

Still this won't work if the input volume is muted. 

If this doesn't help, sorry, but this is uncharted waters for me; I really may not be able to help with this. If no one can help you in this thread, then you'll surely get support in FFmpeg's official support channel on IRC: #ffmpeg @ irc.freenode.net.

If you ever manage to figure it out, please post how you did it. This will be a good reference in the future for users who might encounter the same problem.

---

### Post by mocha on 2010-06-14
Is pulseaudio running on your system?  Did you change any of the pulse or alsa config files, such as the ~/.asoundrc file?

---

### Post by bashologist on 2010-06-16
Following this guide [http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

Installed latest alsa snapshot.

Added below line to /etc/modprobe.d/alsa-base.conf
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

Added below line to /etc/pulse/default.pa
load-module module-alsa-sink device=hw:1,3

Added my user to the necessary groups.

Unmuted the s/pdif audio channels and changed my output device to hdmi in the sound preferences.

Pulse works perfectly with rythmbox, mplayer, vlc, xine, aplay etc.

```
ffmpeg -f alsa -ac 2 -i pulse test.mp3
FFmpeg version SVN-r23603, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 14 2010 07:11:00 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.76. 0 / 52.76. 0
  libavformat   52.68. 0 / 52.68. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM pulse
[alsa @ 0x2a2b470]cannot open audio device pulse (No such file or directory)
pulse: Input/output error
```

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  8 2010 for kernel 2.6.32-22-generic (SMP).
```

Maybe the correct place to ask would be an alsa thread? But I'm confused since it seems to work fine for everything else and I have the latest ffmpeg and alsa. I'm so confused lol. Thanks for the help.

---

### Post by bashologist on 2010-06-20
On another computer it's working fine except the sound's very low and sounds terrible. Is it supposed to sound like that?

---

### Post by verb3k on 2010-06-20
UPDATES:
*Expanded FAQ section to cover recording on systems which do not use PulseAudio. I think this can still be improved a lot, but a stub is better than nothing :)

---

### Post by verb3k on 2010-06-20
> **bashologist said:**
> On another computer it's working fine except the sound's very low and sounds terrible. Is it supposed to sound like that?

There can be many reasons for this, and it depends on your source of audio (mic? system audio?). Again, have you checked input/output volumes? 
How did your commandline look like? Posting it here might help. 

If audio options get misplaced in the commandline, you might end up recording to mp2 (which is the default in ffmpeg) and therefore end up with terrible quality audio.

EDIT: and no, it's not supposed to sound like that. (unless your mic is of low quality, like the ones integrated with laptops)

---

### Post by bashologist on 2010-06-21
Trying to record system sounds. The command line for testing I used was actually pretty complicated for just a test lol. This is from my $HISTFILE.

```
output=$(tempfile -s .mp3)
mplayer -ao alsa:device=hw=0.0 /usr/share/sounds/alsa/*.wav &> /dev/null < /dev/null &
sleep 1
ffmpeg -f alsa -ac 2 -i hw:0,0 -ab 320k -y "$output" &> /dev/null < /dev/null &
sleep 5
kill -2 %1 %2
sleep 1
mplayer "$output" &> /dev/null < /dev/null

```

Also tried with flac etc... The sound is hearable if I turn my volume up about 200%. It's also very staticy. I redirected the stderr but there's no errors or warnings with ffmpeg. Tried with "-i pulse". Can't think of anything else to test. Maxed out everything in alsamixer and sound preferences.

---

### Post by verb3k on 2010-06-21
> **bashologist said:**
> Trying to record system sounds. The command line for testing I used was actually pretty complicated for just a test lol. This is from my $HISTFILE.

```
output=$(tempfile -s .mp3)
mplayer -ao alsa:device=hw=0.0 /usr/share/sounds/alsa/*.wav &> /dev/null < /dev/null &
sleep 1
ffmpeg -f alsa -ac 2 -i hw:0,0 -ab 320k -y "$output" &> /dev/null < /dev/null &
sleep 5
kill -2 %1 %2
sleep 1
mplayer "$output" &> /dev/null < /dev/null

```

Also tried with flac etc... The sound is hearable if I turn my volume up about 200%. It's also very staticy. I redirected the stderr but there's no errors or warnings with ffmpeg. Tried with "-i pulse". Can't think of anything else to test. Maxed out everything in alsamixer and sound preferences.

When recording system sound, maxing out volume above 100% might result in some statics. It's better if you record with the normal volume and then increase the volume with ffmpeg. Also, it's better to explicitly set the audio codec on the command line.

So, what I suggest is replacing your commandline with this one:

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -acodec pcm_s16le -vol 400 -y output.wav
```

Note the -vol 400 to increase the audio volume, you can change this value up or down according to your desired amplification. Also note that we used pcm instead of mp3, becuase it's always better to record in lossless first and then do the compression to mp3 later.

One question though, how did you get -i hw:0,0 to record system audio? :)
Doesn't that usually record mic input?

---

### Post by bashologist on 2010-06-21
Edit: Got everything working on one of my computers. Just didn't follow the great guide well enough.

Edit 2: Yay, got it working on both computers. My first problem where I manually installed a new alsa was solved by adding the below lines to /etc/asound.conf.

```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

These lines may need to be manually added after you manually install alsa.

---

### Post by verb3k on 2010-06-23
*Updated the guide with info on how to use mkvmerge concatenation as an alternative of pausing/resuming.

---

### Post by hugmenot on 2010-06-24
Can’t you send SIGSTOP the process? Would be easy to assign a shortcut to that.

```
pkill -f -s STOP ffmpeg.*x11grab
pkill -f -s CONT ffmpeg.*x11grab
```

---

### Post by verb3k on 2010-06-24
> **hugmenot said:**
> Can&#8217;t you send SIGSTOP the process? Would be easy to assign a shortcut to that.

```
pkill -f -s STOP ffmpeg.*x11grab
pkill -f -s CONT ffmpeg.*x11grab
```

Didn't seem to work properly. Also, your syntax didn't work for me:
```
pkill: invalid session id: STOP
```

---

### Post by hugmenot on 2010-06-24
> **verb3k said:**
> Didn't seem to work properly. Also, your syntax didn't work for me:
```
pkill: invalid session id: STOP
```

Sorry for that. I mixed the syntax of killall and pkill.
Try this:

```
pkill -f -STOP ffmpeg.*x11grab
pkill -f -CONT ffmpeg.*x11grab
```

---

### Post by verb3k on 2010-06-24
> **hugmenot said:**
> Sorry for that. I mixed the syntax of killall and pkill.
Try this:

```
pkill -f -STOP ffmpeg.*x11grab
pkill -f -CONT ffmpeg.*x11grab
```

That also doesn't work :p:
```
pkill: invalid option -- 'S'
```

However changing to "pkill -STOP ffmpeg" does stop the recording, but the output file is wrecked (Pause time still recorded showing the last frame before the pause). I think mkvmerge is a safer solution until ffmpeg supports concatenation or pausing the encode :)

---

### Post by hugmenot on 2010-06-25
> **verb3k said:**
> That also doesn't work :p:
```
pkill: invalid option -- 'S'
```

However changing to "pkill -STOP ffmpeg" does stop the recording, but the output file is wrecked (Pause time still recorded showing the last frame before the pause). I think mkvmerge is a safer solution until ffmpeg supports concatenation or pausing the encode :)

Gah! Ya, the -f has to come before the process regex. Scusa.
But when you encode the second time around it drops the idle time. And mplayer skips it during play.

---

### Post by FakeOutdoorsman on 2010-07-01
FFmpeg still seems to have trouble with mouse themes that include a drop shadow with transparency and renders it with a black border (see *mouse-shadow.png*). If you want to avoid the ugly mouse border use a mouse theme that doesn't include a mouse shadow with transparency, such as the somewhat ugly basic x11 mouse theme.  It may be included in Ubuntu by default, but a similar [Basic theme](http://gnome-look.org/content/show.php/Basic?content=126559) is available at gnome-look.org.  You can change the mouse theme in *System > Preferences > Appearance > Theme Tab > Customize > Pointer*.


**[color=#FF0000]Update:[/color]** Fixed by FFmpeg revision 25690: [Make x11grab cursor drawing suck less](http://git.ffmpeg.org/?p=ffmpeg;a=commit;h=191a50db964768ca4418bdf00b26159a77879b9c).

---

### Post by FakeOutdoorsman on 2010-07-01
I also submitted a bug report on the very slow FFmpeg issue tracker:

[Issue 2056: x11grab fails to render mouse shadow transparency](https://roundup.ffmpeg.org/issue2056)

**[color=#FF0000]Update:[/color]** Fixed by FFmpeg revision 25690: [Make x11grab cursor drawing suck less](http://git.ffmpeg.org/?p=ffmpeg;a=commit;h=191a50db964768ca4418bdf00b26159a77879b9c).

---

### Post by verb3k on 2010-07-30
The examples were updated to use the new libx264 presets, which are now part of an official release (i.e. FFmpeg 0.6).

---

### Post by cfriedt on 2010-08-07
This is excellent! Thanks for posting. 

I had the exact same problem and tried each of the apps that you mentioned above. 

Is there anything that ffmpeg does **not** do?

---

### Post by verb3k on 2010-08-09
Guide update: Rewrote a paragraph, made more verbose.

> **cfriedt said:**
> This is excellent! Thanks for posting. 

I had the exact same problem and tried each of the apps that you mentioned above. 

Is there anything that ffmpeg does **not** do?

FFmpeg can't pause/resume screencasting, but, as explained in the guide, there are workarounds for this issue. It is also not possible to hide the mouse cursor. Maybe there are more, too.

---

### Post by Stoneface on 2010-08-17
Great guide. Thanks a lot! Just tried one screencast using this line ```
me@ubuntu:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1440x780 -i :0.0+0,24 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output2.mkv
``` It started to run```

FFmpeg version SVN-r24757, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 10 2010 10:45:27 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 3. 0 /  0. 3. 0
  libavcodec    52.84. 3 / 52.84. 3
  libavformat   52.78. 1 / 52.78. 1
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.31. 0 /  1.31. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0xa2f7470] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0xa2f7470] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1282035130.989986, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[x11grab @ 0xa308c90] device: :0.0+0,24 -> display: :0.0 x: 0 y: 24 width: 1440 height: 780
[x11grab @ 0xa308c90] shared memory extension  found
[x11grab @ 0xa308c90] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0+0,24':
  Duration: N/A, start: 1282035131.788161, bitrate: 1078272 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1440x780, 1078272 kb/s, 30 tbr, 1000k tbn, 30 tbc
[buffer @ 0xa317680] w:1440 h:780 pixfmt:bgra
[ffmpeg_output @ 0xa331bf0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0xa330ad0] w:1440 h:780 fmt:bgra -> w:1440 h:780 fmt:yuv420p flags:0xa0000004
[libx264 @ 0xa316d70] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0xa316d70] profile High 4:4:4 Predictive, level 3.2, bit depth 8
[libx264 @ 0xa316d70] 64 - core 104 r1688 0b36c6d - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=1:0:0 analyse=0x1:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output2.mkv':
  Metadata:
    encoder         : Lavf52.78.1
    Stream #0.0: Video: libx264, yuv420p, 1440x780, q=10-51, 200 kb/s, 1k tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding

```
, but it stopped after a while with errors:
```

[matroska @ 0xa315820] st:1 error, non monotone timestamps 4790 >= 4790/s    
av_interleaved_write_frame(): Operation not permitted
```

Googled and reading [https://roundup.ffmpeg.org/issue807](https://roundup.ffmpeg.org/issue807) now..

---

### Post by verb3k on 2010-08-17
> **Stoneface said:**
> Great guide. Thanks a lot! Just tried one screencast using this line ```
me@ubuntu:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1440x780 -i :0.0+0,24 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output2.mkv
``` It started to run```

FFmpeg version SVN-r24757, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 10 2010 10:45:27 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 3. 0 /  0. 3. 0
  libavcodec    52.84. 3 / 52.84. 3
  libavformat   52.78. 1 / 52.78. 1
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.31. 0 /  1.31. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0xa2f7470] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0xa2f7470] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1282035130.989986, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[x11grab @ 0xa308c90] device: :0.0+0,24 -> display: :0.0 x: 0 y: 24 width: 1440 height: 780
[x11grab @ 0xa308c90] shared memory extension  found
[x11grab @ 0xa308c90] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0+0,24':
  Duration: N/A, start: 1282035131.788161, bitrate: 1078272 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1440x780, 1078272 kb/s, 30 tbr, 1000k tbn, 30 tbc
[buffer @ 0xa317680] w:1440 h:780 pixfmt:bgra
[ffmpeg_output @ 0xa331bf0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0xa330ad0] w:1440 h:780 fmt:bgra -> w:1440 h:780 fmt:yuv420p flags:0xa0000004
[libx264 @ 0xa316d70] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0xa316d70] profile High 4:4:4 Predictive, level 3.2, bit depth 8
[libx264 @ 0xa316d70] 64 - core 104 r1688 0b36c6d - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=1:0:0 analyse=0x1:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output2.mkv':
  Metadata:
    encoder         : Lavf52.78.1
    Stream #0.0: Video: libx264, yuv420p, 1440x780, q=10-51, 200 kb/s, 1k tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding

```
, but it stopped after a while with errors:
```

[matroska @ 0xa315820] st:1 error, non monotone timestamps 4790 >= 4790/s    
av_interleaved_write_frame(): Operation not permitted
```

Googled and reading [https://roundup.ffmpeg.org/issue807](https://roundup.ffmpeg.org/issue807) now..

This happens when you run out of disk space. As explained in the guide, the first step is _lossless_, therefore it takes a huge amount of disk space. That's why we have a second step to compress the screencast.

Make sure you have enough free space, you probably need several gigabytes.

---

### Post by Stoneface on 2010-08-17
If I run ```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1440x780 -i :0.0 -acodec flac -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mk
``` it runs and stores. used flac instead of earlier mentioned acodec. Only Totem somehow won't play it. Maybe a missing codec. Will convert it shortly..

---

### Post by FakeOutdoorsman on 2010-08-17
You may need to install **gstreamer0.10-ffmpeg** to allow Totem to decode the video.  Note: I am guessing here. I am not a Totem user.

---

### Post by d3v1150m471c on 2010-08-24
you, my friend, are a genius.

---

### Post by AutoStatic on 2010-08-28
Thanks for the howto! I've installed the latest versions of FFmpeg and x264 and it all works well, but... After having uploaded a testvid to YouTube the result is horrible! So I'm wondering if the quality loss could be solved on my side or that it's simply YouTube that degrades the quality.

Here's the little script I'm using:```
#!/bin/bash

DATE=`date +%Y%m%d`
TIME=`date +%Hh%M`

(sleep 3;qtractor $HOME/Screencasts/Screencast.qtr) &
xterm -e jack_capture -b 24 $HOME/Screencasts/screencast_audio_$DATE-$TIME.wav &
ffmpeg -an -f x11grab -r 30 -s 1920x1080 -i :0.0+1920,0 -vcodec libx264 -vpre lossless_ultrafast -threads 4 $HOME/Screencasts/screencast_video_$DATE-$TIME.mkv

killall jack_capture
```

The video that comes out looks really good, and it still looks good after I've edited it with OpenShot. I render it to a mp4 container with x264 as the video codec and mp3 as the audio codec and keep the fps at 30 (as advised here: [http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460](http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460)). I also tried uploading just the mkv file from FFmpeg, same result. Could it be my resolution? 1920x1080 should be supported.

Here are some snapshots from VLC. [One from the original mkv file]("http://imagebin.ca/img/i_kiaaNY.png") and [one from the YouTube flv file]("http://imagebin.ca/img/ddOyfi.png"). The difference is really obvious.

Thanks,

Jeremy

---

### Post by verb3k on 2010-08-29
> **AutoStatic said:**
> Thanks for the howto! I've installed the latest versions of FFmpeg and x264 and it all works well, but... After having uploaded a testvid to YouTube the result is horrible! So I'm wondering if the quality loss could be solved on my side or that it's simply YouTube that degrades the quality.

Here's the little script I'm using:```
#!/bin/bash

DATE=`date +%Y%m%d`
TIME=`date +%Hh%M`

(sleep 3;qtractor $HOME/Screencasts/Screencast.qtr) &
xterm -e jack_capture -b 24 $HOME/Screencasts/screencast_audio_$DATE-$TIME.wav &
ffmpeg -an -f x11grab -r 30 -s 1920x1080 -i :0.0+1920,0 -vcodec libx264 -vpre lossless_ultrafast -threads 4 $HOME/Screencasts/screencast_video_$DATE-$TIME.mkv

killall jack_capture
```

The video that comes out looks really good, and it still looks good after I've edited it with OpenShot. I render it to a mp4 container with x264 as the video codec and mp3 as the audio codec and keep the fps at 30 (as advised here: [http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460](http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460)). I also tried uploading just the mkv file from FFmpeg, same result. Could it be my resolution? 1920x1080 should be supported.

Here are some snapshots from VLC. [One from the original mkv file]("http://imagebin.ca/img/i_kiaaNY.png") and [one from the YouTube flv file]("http://imagebin.ca/img/ddOyfi.png"). The difference is really obvious.

Thanks,

Jeremy

I hope you get an answer soon. You can join the FFmpeg support channel #ffmpeg @ irc.freenode.net, many people there can help.

---

### Post by AutoStatic on 2010-08-29
Hello verb3k, thanks for the reply. It has got something to do with the 1920x1080 setting. If I downscale the video to 1280x720 and upload it to YouTube the quality is much better. So for me, issue solved, from now on I'll do screencasts in 1280x720.

---

### Post by FakeOutdoorsman on 2010-08-29
I can confirm that YouTube creates an ugly output with 1920x1080 for the few tests I did.  Good to know that YouTube can now properly decode lossless video from x264 (at least with my limited tests).  YouTube didn't like my previous attempts, but that was months ago.

As for your command, the only thing I can recommend is to change *-threads 4* to *-threads 0* which will automatically choose a correct value for your CPU, unless for some reason you want to use a certain value.

---

### Post by AutoStatic on 2010-08-30
> **FakeOutdoorsman said:**
> As for your command, the only thing I can recommend is to change *-threads 4* to *-threads 0* which will automatically choose a correct value for your CPU, unless for some reason you want to use a certain value.My system has 4 CPU's. I've checked both 0 and 4 with htop and it seems a setting of 4 spreads the load better.

---

### Post by Stoneface on 2010-09-02
Just ran ```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x998 -i :0.0+0,24 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
``` for a while and played it in Totem. Only saw a black screen and my mouse moving. Same result I had using RecordMyDesktop. I wonder what is going on. Is Compiz - which I just started to use -  a problem?

Did ```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1408x890 -i :0.0 -acodec flac -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv

```, converted it to an mp4 and got the same result: mouse pointer moving around on a black screen with my voice in the background. Very odd..

---

### Post by verb3k on 2010-09-02
Did you disable Compiz and try again? It works fine in Totem, and I don't think it's a player problem since the pointer is there. It might be something going wrong during the recording, or a bug in ffmpeg.

---

### Post by Stoneface on 2010-09-03
@ Verb3k I think it is an issue with Compiz and recording using Lucid Lynx in VirtualBox that causes the black screen where audio is good but only the mouse pointer is sees. As the same happened using Ffmpeg and RecordMyDesktop. I hope I can solve this though as I love to use Compiz for its zoom function.
I did ran RecordMydesktop without Compiz in VMWare Fusion (cannot handle Compiz) and all went well, except for misformed audio (my voice) for about three seconds.

---

### Post by Mampir on 2010-09-06
On my recordings the mouse cursor doesn't change depending context. For example, when the cursor is over a text field it does not change to an "[FONT=Times New Roman][SIZE=5]I[/SIZE][/FONT]" shape. Also, the regular cursor comes out with different shape, but that's not a big issue. Is there a way to deal with this?

I'm using Trisquel GNU/Linux 3.5, which is based on Ubuntu Karmic Koala.

---

### Post by FakeOutdoorsman on 2010-09-06
Did you compile FFmpeg, or are you using an older version from a repository?  The reason I ask is because your FFmpeg may be too old to be able to record the system mouse.  Show the output of *ffmpeg -version*.  This should indicate how old your version is.

If you decide to compile FFmpeg, be aware that it does not properly render a mouse that uses transparency (such as a dropshadow).  I recommend using a mouse theme without any transparency effects when using FFmpeg to record your screen.

---

### Post by Mampir on 2010-09-06
No, I haven't compiled anything. I'm using the version from the Trisquel's repository, which should be the same one as the Ubuntu's Karmic Koala version. Here is FFmpeg's output:
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
```If you think the problem arises because my version is older, then maybe is best to just wait for the new Trisquel release (based on Lucid Lynx) which should come out soon.

---

### Post by FakeOutdoorsman on 2010-09-06
I believe Lucid's FFmpeg is also to old, if I remember correctly.

---

### Post by Mampir on 2010-09-10
You are probably right. I've just tried version "FFmpeg SVN-r0.5.1-4:0.5.1-1ubuntu1" and with it too the cursor doesn't change.

---

### Post by Cavsfan on 2010-09-10
I used this tutorial to update ffpmeg [[COLOR=blue]_HOWTO: Install and use the latest FFmpeg and x264 _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

Here is my fmpeg version:
```
ffmpeg version
FFmpeg version SVN-r25017, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep  1 2010 14:13:10 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.87. 0 / 52.87. 0
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.38. 1 /  1.38. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

```HTH

---

### Post by Hrodebert on 2010-09-18
Greetings.
I'm sure most of you have done something more advanced but I didn't think about it when I started doing recordings so I'm posting it anyway in case someone like me is reading this.
Here's what I did, just because I'm lazy..

First I made a script
```
#!/bin/bash
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 zzz.mkv
mv ~/zzz.mkv ~/recs/$(date +%F_%A_at_%H:%M:%S).mkv
```

Pretty self-explanatory, especially if you read verb3k's excellent post in the beginning of this thread.
It's recording to zzz.mkv. I'm using a stupid name like that because sometimes I want to know the filesize when I'm recording, and zzz.mkv makes it quick to find in Nautilus. Yes, I have a lot of crap in my ~/
When I stop recording it automagically moves the file to my recordings folder called recs and renames it to something like this 2010-09-18_saturday_at_03:51:10.mkv

Make a starter on one of your bars or panels and point it at your script.
Click starter
Press q in CLI when done
Click your starter again
????
Profit

No more manual moving and renaming! Sweet :)

---

### Post by verb3k on 2010-09-19
Guide update: More robust "xwininfo" usage. Previously used -geometry parameter does not always return correct values for window coordinates.

---

### Post by Cavsfan on 2010-09-26
Just curious: I have a 1920x1200 native res. monitor and have used **FakeOutdoorsman**'s Tutorial to compile FFmpeg with x264 and all 
available options. My refresh rate is 60hz and no matter what I do I get flicker when using the commands on page one. I also get the same
with Recordmydesktop. Even when I do a screen print, it is not quite right if I tilt the cube or do anything. A regular screenprint comes out OK. 
I am using the absolute latest nVidia drivers and everything is amazing!

60hz is the max. for my monitor and I cannot figure out why I get the flicker. I even tried using fps=50 instead of 30 and still I get flicker.

Any help would be greatly appreciated! ](*,)

---

### Post by shantiq on 2010-09-28
thanx that is just what i was looking for   ffmpeg really roks:KS:KS:KS



ok changed it a tad so the file ends up on desktop which i prefer


```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv
```


i have a question tho     how can i do this and also add myself being recorded on the cam    can it be done?

---

### Post by FakeOutdoorsman on 2010-09-29
Let's install [ffcast](http://github.com/lolilolicon/ffcast)!  This script is good for those who want to simply click on a window or click and drag an area to record.

First you need to install FFmpeg. I prefer to compile it myself, but there are several options here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now for FFcast:
```
sudo apt-get install git-core libx11-dev checkinstall
cd
git clone git://github.com/lolilolicon/ffcast.git
cd ffcast
wget http://fakeoutdoorsman.com/ffmpeg/enable_threads.diff
patch -p1 < enable_threads.diff
make
sudo checkinstall --pkgname=ffcast --pkgversion="$(date +%Y%m%d)" --backup=no \
    --deldoc=yes --fstrans=no --default
```

Some examples.  Capture fullscreen and manually give an output name (by default it games an output file name like *ffcast.100928220623.mkv*):
```
ffcast -a -o screencast.mkv
```

Select an area to record by dragging the mouse and change the frame rate (by default it's *-r 15*):
```
ffcast -s -r 30
```

Or show the command without recording:
```
ffcast -s -r 30 --printcmd
```

See *ffcast -h* for more options.

---

### Post by verb3k on 2010-09-29
@FakeOutdoorsman: Problem with ffcast is that it doesn't support audio, does it?. However, the xrectsel tool is particularly useful. It is brilliant. I think I might add it to the guide.

Anyone can wrap a script or an alias or whatever to get ffmpeg to screencast. I know people who streamlined their entire screencasting pipeline with scipts and aliases. ffcast isn't bad and does what it advertises, but nothing more (no audio, no compression to various target formats etc).

I think it is always better for people to be at "ground zero" and learn ffmpeg itself instead of learning a single purpose interface of another interface. It is for their own good :)

---

### Post by shantiq on 2010-09-29
thanx for that so coool FOM
so handy



one more example

```
ffcast --xwininfo  -v -t 00:00:30 -r 40 -o  ./Desktop/screencast.mkv
```


start it click once on the window of your choice and you have 30 seconds recorded in mkv to your desktop      brilliant tool


could one add sound?

---

### Post by FakeOutdoorsman on 2010-09-29
> **verb3k said:**
> @FakeOutdoorsman: Problem with ffcast is that it doesn't support audio, does it?. However, the xrectsel tool is particularly useful. It is brilliant. I think I might add it to the guide.
> **shantiq said:**
> could one add sound?

No, it doesn't deal with audio.  It's one of the TODOs, but this script has not been updated since December 2009.  Someone with more interest in using this script and a little bash experience could easily add audio support though.

The best part of this script is definitely xrectsel.

> **verb3k said:**
> I think it is always better for people to be at "ground zero" and learn ffmpeg itself instead of learning a single purpose interface of another interface. It is for their own good :)

Yes, I agree, but it is good to have options.  I've seen some Ubuntu users interested in this script, but they thought it was for Arch Linux only or didn't know how to get it working or installed.

---

### Post by shantiq on 2010-09-29
it is  a really cute tool. ffmpeg "raw" is really quite daunting and yes it has to be one of the best tools ever designed but to learn to use it is really quite a task

what i am saying is that one does not preclude the other

ffmpeg is the forest ffcast a nice glade:KS:KS:KS anyway that's my tuppence worth

---

### Post by verb3k on 2010-09-29
Guide update: Added information about the xrectsel tool to the FAQ section.

---

### Post by verb3k on 2010-09-29
> **shantiq said:**
> thanx that is just what i was looking for   ffmpeg really roks:KS:KS:KS



ok changed it a tad so the file ends up on desktop which i prefer


```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv
```


i have a question tho     how can i do this and also add myself being recorded on the cam    can it be done?

You can record webcam feed with ffmpeg by using -f video4linux2 -i /dev/video0. You can record infinite number of streams simultaneously. For example, you can record audio from mic, audio from application, video from screen and video from webcam and store them as 4 tracks in a single file, which you can then import to a video editor like openshot and overlay, mix etc... to get the result you wanted. However, note that the likelihood of your streams getting out of sync is quite high, especially if your computer isn't the latest specs or some Alien technology :D

---

### Post by verb3k on 2010-09-29
> **Cavsfan said:**
> Just curious: I have a 1920x1200 native res. monitor and have used **FakeOutdoorsman**'s Tutorial to compile FFmpeg with x264 and all 
available options. My refresh rate is 60hz and no matter what I do I get flicker when using the commands on page one. I also get the same
with Recordmydesktop. Even when I do a screen print, it is not quite right if I tilt the cube or do anything. A regular screenprint comes out OK. 
I am using the absolute latest nVidia drivers and everything is amazing!

60hz is the max. for my monitor and I cannot figure out why I get the flicker. I even tried using fps=50 instead of 30 and still I get flicker.

Any help would be greatly appreciated! ](*,)

Even I tried capturing more than 30 fps and couldn't do it. There seems to be a bottleneck somewhere. You can ask the people at #ffmpeg on irc.freenode.net, they might be able to help.

---

### Post by verb3k on 2010-09-29
Guide updated: Expanded the FAQ section to include information on how to get help.

---

### Post by shantiq on 2010-09-29
> **verb3k said:**
> You can record webcam feed with ffmpeg by using -f video4linux2 -i /dev/video0. You can record infinite number of streams simultaneously. For example, you can record audio from mic, audio from application, video from screen and video from webcam and store them as 4 tracks in a single file, which you can then import to a video editor like openshot and overlay, mix etc... to get the result you wanted. However, note that the likelihood of your streams getting out of sync is quite high, especially if your computer isn't the latest specs or some Alien technology :D


Verb thanx for that  :KS   and God i wish i had the alien technology



this is almost alien and gives me a great webcam with voice combo thanx for the info:KS

```
ffmpeg -f alsa -ac 2 -i pulse  -f video4linux2 -i /dev/video0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -s 320x240   -r 30   ./Desktop/mywebcam.avi
```






and if you fancy direct recording to other codecs   [ read here]("http://ubuntuforums.org/showthread.php?p=9912412#post9912412")




:rolleyes::rolleyes::roll::roll:

---

### Post by dannyboy79 on 2010-10-04
id like to add to this thread about the hours I spent trying over and over, uploading over and over to youtube and spending time on IRC with FFMPEG people so others won't have to spend the time I did.

When i capture to mkv using this command:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab **-r 29.97** -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```
the audio at the end prior to me hitting "q" is cutoff. not sure why but i can repeat the audio being cutoff all the time. Anyone else seeing this? I added the -r 29.97 because apparently youtube doesn't like anything non-standard FPS and the people on ffmpeg irc chat told me to add it.

Also, when I try to encode it for youtube using the command 
```
ffmpeg -i output-new.mkv -acodec libfaac -ab 128k -ac 2 -r 29.97 -vcodec libx264 -vpre slow -crf 22 -threads 0 pm_message_settings.mp4
```
youtube totally f's up my clip from a 36 second clip to 3 second clip. it appears to make video super fast and audio normal.

So the great people on ffmpeg irc chat told me to add -vsync 1 to my encode line and it now works. final render command is this:
```
ffmpeg -i output-new.mkv -acodec libfaac -ab 256k -ac 2 -r 29.97 -vsync 1 -vcodec libx264 -vpre slow -crf 22 -threads 0 pm_message_settings.mp4
```

I am using ffmpeg SVN-r25112 with the following compile options. configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab

I do have composite extra enabled on 10.04 Lucid Lynx for zooming in during my screencast. I have the NVIDIA 96.43.17 driver installed.

SO if anyone else can help with the audio being cutoff prior to hitting the q button please let me know. Shouldn't the audio stop with the video when you hit "q"?  thanks for any help

---

### Post by verb3k on 2010-10-04
> **dannyboy79 said:**
> id like to add to this thread about the hours I spent trying over and over, uploading over and over to youtube and spending time on IRC with FFMPEG people so others won't have to spend the time I did.

When i capture to mkv using this command:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab **-r 29.97** -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```
the audio at the end prior to me hitting "q" is cutoff. not sure why but i can repeat the audio being cutoff all the time. Anyone else seeing this? 

This happens when you are recording through pulse (bug?). If you're recording through microphone, replacing -i pulse with -i hw:0,0 will solve your problem.
> I added the -r 29.97 because apparently youtube doesn't like anything non-standard FPS and the people on ffmpeg irc chat told me to add it.
Youtube works fine for 30 fps. Both lossless and compressed mp4.
> 
Also, when I try to encode it for youtube using the command 
```
ffmpeg -i output-new.mkv -acodec libfaac -ab 128k -ac 2 -r 29.97 -vcodec libx264 -vpre slow -crf 22 -threads 0 pm_message_settings.mp4
```
youtube totally f's up my clip from a 36 second clip to 3 second clip. it appears to make video super fast and audio normal.

Not reproducible. Clips compressed with AAC and H.264 in .mp4 are handled properly by youtube and stay at full length.

---

### Post by dannyboy79 on 2010-10-05
> **verb3k said:**
> 
Not reproducible. Clips compressed with AAC and H.264 in .mp4 are handled properly by youtube and stay at full length.
Im not sure if you actually tried to upload your clip to youtube but it's weird. the file does play fine in vlc and totem but it's only after it uploads to youtube that it's all screwed if I don't use the "-vsync 1" option to the encode line. Here's a sample if you don't believe me.

[http://www.youtube.com/watch?v=kJ7_5b6kw0c]("http://www.youtube.com/watch?v=kJ7_5b6kw0c")

if i run a ffmpeg -i on the mp4 prior to uploading to youtube, the one without the -vsync 1, you can see this.
Stream #0.0(und): Video: h264, yuv420p, 1024x768 [PAR 1:1 DAR 4:3], 226 kb/s, **2.60 fps**, 29.97 tbr, 30k tbn, 59.94 tbc

BUT when I use the -vsync 1 the fps and tbr match.
Stream #0.0(und): Video: h264, yuv420p, 1024x768 [PAR 1:1 DAR 4:3], 559 kb/s, **29.97 fps**, 29.97 tbr, 2997 tbn, 59.94 tbc

as i stated someone on the ffmpeg irc chat pointed this out to me. whats more weird is that if you don't use the -vsync 1 and instead of using the mp4 container and you use a mkv container on the end of the file name the fps and tbr DO match. So this may be a bug with mp4 but I am not sure.


Next problem is the audio, I will try that although I remember trying to enter that in gtk-recordmydesktop and it returned that it couldn't configure the sound but that may be gtk-recordmydesktop problem. Thanks for trying to help. I'll post back sound result using hw:0,0 after work.

---

### Post by verb3k on 2010-10-05
I'm not saying I don't believe you. I'm saying that I could not get what you desrcibed in the tests I've conducted. I know ffmpeg is one buggy piece of software; it's not unbelievable that problems like that occur to its users :)

---

### Post by techunit on 2010-10-05
> **verb3k said:**
> While many screencasting tools exist on Linux, none of them is able to really pull a high-quality screencast. I&#8217;ve tried almost all existing tools such as recordmydesktop, xvidcap, istanbul, wink etc..  and all of them produced poor results. Horrible video/audio quality,  bad sync, lots of limitations, and some even simply segfault while doing the recording. The real solution and the ultimate answer to all your screencasting needs on Linux has been there for quite a long time. It is called **FFmpeg**. I am surprised to see that many people would just overlook this awesome piece of software.

I disagree for one reason. Most people who are going to do screencasts seriously are going to be using a VM thus there needs to be something else doing the recording. I ffmpeg is far to hard to get going and it can't be run in a vm.

---

### Post by FakeOutdoorsman on 2010-10-05
> **techunit said:**
> I disagree for one reason. Most people who are going to do screencasts seriously are going to be using a VM thus there needs to be something else doing the recording. I ffmpeg is far to hard to get going and it can't be run in a vm.

Please don't quote the whole post.  I just created a screencast of a VM creating a screencast: [ffmpegvm.mkv](http://fakeoutdoorsman.com/ffmpeg/ffmpegvm.mkv).

---

### Post by .35Whelen on 2010-10-12
My goal is to show a screencast of Ubuntu 10.04LTS with Compiz Fusion,  full cube rotation, all the great eyecandy in a high graphic  environment.
I have followed the tutorial provided by Verb3K


     Code:
     ffmpeg [COLOR=Red]-f alsa -ac 2 -ab 128k -i pulse -acodec pcm_s16le[/COLOR] -f x11grab -r 30 -s 1280x1024 -i :0.0 -aspect 4:3 -vcodec libx264 -vpre lossless_ultrafast -threads 0 SCREENCAST.mkv 
Encode

     Code:
     ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 our-final-product.mp4 


 This gives me a choppy and lagging fps rate. The bigger problem is audio is not working. I have  PulseAudio and pavucontrol set to Microphone1 and have tried it on  Amplifier to no avail. What could I be missing? Any info or lead to  track down would be appreciated.

---

### Post by ron999 on 2010-10-12
> **.35Whelen said:**
> 
I have followed the tutorial provided by Verb3K


     Code:
     ffmpeg [COLOR=Red]-f alsa -ac 2 -ab 128k -i pulse -acodec pcm_s16le[/COLOR] -f x11grab -r 30 -s 1280x1024 -i :0.0 -aspect 4:3 -vcodec libx264 -vpre lossless_ultrafast -threads 0 SCREENCAST.mkv 


That command is not the one used in the tutorial.

---

### Post by .35Whelen on 2010-10-12
It was posted #22 on page 3 and seems viable. I have also used the first example:


     Code:
     ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv 

from the tutorial and all record and encode combinations that Verb3K was kind enough to provide. My preparation consisted of:


For this tutorial, you’ll need FFmpeg (preferably a recent revision)  compiled with "--enable-x11grab" and the following libraries:

    * libx264
    * libfaac
    * libmp3lame
    * libxvid
    * libtheora
    * libvorbis

to no avail.

---

### Post by mocha on 2010-10-13
> **.35Whelen said:**
>  This gives me a choppy and lagging fps rate. The bigger problem is audio is not working. I have  PulseAudio and pavucontrol set to Microphone1 and have tried it on  Amplifier to no avail. What could I be missing? Any info or lead to  track down would be appreciated.


You probably didn't select the proper audio input source in the Pulseaudio recording section after you started ffmpeg.  As for lagging capture, maybe your computer specs are too low?  What hardware are you running?

---

### Post by wgilthorpe on 2010-10-14
HELP!

Please excuse the yelling, but I am at wits end.  I have been successfully recorded a couple of screencasts with ffmpeg and they come out beautifully.  My only problem (and it is driving me crazy) is that I want to record both my microphone input and the system sounds simultaneously.  I am trying to show a friend who lives far away my Ubuntu theme.  I would like to narrate while doing so.  If anyone knows how i might accomplish this I would be most grateful.

---

### Post by .35Whelen on 2010-10-16
wgilthorpe


HELP!

Please excuse the yelling, but I am at wits end.  I have been  successfully recorded a couple of screencasts with ffmpeg and they come  out beautifully.  My only problem (and it is driving me crazy) is that I  want to record both my microphone input and the system sounds  simultaneously.  I am trying to show a friend who lives far away my  Ubuntu theme.  I would like to narrate while doing so.  If anyone knows  how i might accomplish this I would be most grateful.

Ya, I'm not sure why you hijacked my post?

---

### Post by user1220 on 2010-10-19
Hi,

I have tried to do some recordings using this method, and everything works for me with the exception that audio and video are out of sync. This was a bitter disappointment for me, because other than the audio/video sync problem, I found ffmpeg/x11grab to be far superior to any other screencasting software on linux.

The audio seems to be delayed about 1 second or so, here is an example video: [http://www.youtube.com/watch?v=1-dIQrZ_EPg](http://www.youtube.com/watch?v=1-dIQrZ_EPg)
(The click sound is actually played at the same time when "Click" is echoed in the console.)

This is what the console said after entering the command:
```
jacob@ubuntu:~/Desktop$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s 800x600 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 video.mkv
FFmpeg version 0.6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct 19 2010 21:18:26 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab --enable-pthreads
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0x2868420]capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x2868420]Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1287516545.387204, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[x11grab @ 0x2887fc0]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 800 height: 600
[x11grab @ 0x2887fc0]shared memory extension  found
[x11grab @ 0x2887fc0]Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1287516545.801613, bitrate: 384000 kb/s
    Stream #1.0: Video: rawvideo, bgra, 800x600, 384000 kb/s, 25 tbr, 1000k tbn, 25 tbc
[libx264 @ 0x2897430]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x2897430]profile High 4:4:4 Predictive, level 3.1, bit depth 8
[libx264 @ 0x2897430]64 - core 107 r1745 4785e8e - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=1:0:0 analyse=0x1:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'video.mkv':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: libx264, yuv420p, 800x600, q=10-51, 200 kb/s, 1k tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=  670 fps= 25 q=0.0 Lsize=    6433kB time=26.52 bitrate=1987.0kbits/s    
video:1828kB audio:4569kB global headers:0kB muxing overhead 0.564713%
[libx264 @ 0x2897430]frame I:3     Avg QP: 0.00  size:304422
[libx264 @ 0x2897430]frame P:667   Avg QP: 0.00  size:  1437
[libx264 @ 0x2897430]mb I  I16..4: 42.2%  0.0% 57.8%
[libx264 @ 0x2897430]mb P  I16..4:  0.4%  0.0%  0.0%  P16..4:  0.1%  0.0%  0.0%  0.0%  0.0%    skip:99.5%
[libx264 @ 0x2897430]coded y,uvDC,uvAC intra: 87.2% 86.2% 85.9% inter: 0.1% 0.1% 0.1%
[libx264 @ 0x2897430]i16 v,h,dc,p: 41% 25% 32%  2%
[libx264 @ 0x2897430]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 30% 26% 16%  5%  4%  3%  4%  4%  8%
[libx264 @ 0x2897430]i8c dc,h,v,p: 28% 15% 54%  3%
[libx264 @ 0x2897430]kb/s:558.68
jacob@ubuntu:~/Desktop$ 

```

I had the idea to add **-itsoffset 1** to the first command in "Step 1" of the first post, which at first seemed to work, as the output file had synchronous audio and video: 
```
ffmpeg -f alsa -ac 2 -i pulse **-itsoffset 1** -f x11grab -r 25 -s 800x600 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 video.mkv
```
However, when I tried to encode the lossless video file using the first command in "Step 2" of the first post, the audio delay was present again in the encoded video file.
Even when I added **-itsoffset 1** to the command for the encoding, the delay was still there, as if the itsoffset option would not have changed anything:
```
ffmpeg -i video.mkv -acodec libfaac -ab 128k -ac 2 **-itsoffset 1** -vcodec libx264 -vpre slow -crf 22 -threads 0 video-final.mp4
```

I don't understand why the itsoffset option did not work for the encoding. Did I use it in the wrong way? But even if did, the itsoffset should have had a permanent effect on the recording and therefore the offset should stay intact while reencoding, shouldn't it?

I tried several other things, but none of them worked:
[LIST]
[*]I compiled ffmpeg with and without pthreads
[*]I disabled compiz
[*]I ran the encoding and recording with -threads 1 and -threads 0
[*]I tried to use -async and -vsync, but I suppose they are meant for a completely different matter, right?
[*]I tried hw:0,0 and /dev/dsp instead of pulse
[/LIST]

Edit: By the way, converting regular video files works trouble-free with ffmpeg, so it's not a general issue with my ffmpeg installation.

I use Ubuntu 10.10 64bit.

I'd be deeply grateful if someone could help me with that... I am despairing. :(

Thanks a lot!

---

### Post by mocha on 2010-11-01
What happens if you rearrange your capture command slightly?  Is it in sync this way?

```
ffmpeg -f alsa -ac 2 -i pulse **-acodec pcm_s16le** -f x11grab -r 25 -s 800x600 -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 video.mkv
```

---

### Post by FakeOutdoorsman on 2010-11-07
The ugly mouse cursor issue has been fixed by FFmpeg revision 25690: [Make x11grab cursor drawing suck less](http://git.ffmpeg.org/?p=ffmpeg;a=commit;h=191a50db964768ca4418bdf00b26159a77879b9c).

---

### Post by shantiq on 2010-11-16
hi there


wonder if this can be done


i want to record myself TO DO a rosegarden presentation


so i need to record microphone   and also music coming out of desktop


basically **all** sound


now 

this here

> Q: How can I control PulseAudio input? (e.g. capture application audio instead of mic)
A: Install &#8220;pavucontrol&#8220;. Start recording with ffmpeg. Start pavucontrol. Go to the &#8220;Recording&#8221; tab and you&#8217;ll find ffmpeg listed there. Change audio capture from &#8220;Internal Audio Analog Stereo&#8221; to &#8220;Monitor of Internal Audio Analog Stereo&#8220;.
Now it should record system and application audio instead of microphone.

This setting will be remembered. The next time you want to capture with FFmpeg, it will automatically start recording system audio. If you want to revert this, use pavucontrol again to change back to microphone input.



does not say how to record all sound sources at once  only one or the other



can this be done?


ps   and compounded problem i use a lexicon alpha box   and it does not allow for the options listed here

>  can I control PulseAudio input? (e.g. capture application audio instead of mic)
A: Install &#8220;pavucontrol&#8220;. Start recording with ffmpeg. Start pavucontrol. Go to the &#8220;Recording&#8221; tab and you&#8217;ll find ffmpeg listed there. Change audio capture from &#8220;Internal Audio Analog Stereo&#8221; to &#8220;Monitor of Internal Audio Analog Stereo&#8220;.
Now it should record system and application audio instead of microphone.

SEE IMAGE



thank you   shan

---

### Post by /\\/_\\/\\/ on 2011-01-10
I'm not user1220 but I do have this same problem that my audio is out of sync by a little over a second and I can say no, rearranging the command to put the -acodec earlier does not help, what I have to do to fix the offset in the second step is to do

```

ffmpeg -i video.mkv -itsoffset 2.00 -i video.mkv -map 1:0 -map 0:1 -acodec libfaac -threads 0 -ab 128k -ac 2 -vcodec libx264 -vpre slow -threads 0 video.mp4

```

To use -map you need to specify the input twice, once (in my case) two seconds offset.

---

### Post by achmorrison on 2011-01-11
I *love* this tutorial!

I do notice, though, when I record a screencast, that my fps shown in the terminal window is very low, usually around 3 fps.

What can I do to make it faster?

Thanks!

---

### Post by xaprb on 2011-03-12
Here is a small shell script that wraps around the first example provided in the tutorial.  To use it, save it and make it executable.  Either invoke it from the command line or double-click and run it.  It will prompt you for the file to save, and then ask you to select a window with your mouse, which will set the region of the screen to capture.

```
#!/bin/sh

if [ -z "$1" ]; then
   file="$(zenity --title="Select an output file" --file-selection --filename=screencast.mkv --save --confirm-overwrite --file-filter=mkv)"
else
   file="$1"
fi
rm -f "$file"

echo "Select the window to capture"

region="$(xwininfo | awk "
   /Absolute upper-left X/{ulx=\$4}
   /Absolute upper-left Y/{uly=\$4}
   /Width/{w=\$2}
   /Height/{h=\$2}
   END {
      printf \"-s %dx%d -i ${DISPLAY}+%d,%d\", 2*sprintf(\"%d\", w/2), 2*sprintf(\"%d\", h/2), ulx, uly
   }")"

echo "Will record region $region"
read -p "Press Enter to begin"

set -x
ffmpeg -f alsa -ac 1 -i pulse -f x11grab -r 30 $region \
   -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 "$file"

```

---

### Post by jddalton on 2011-03-17
Is it possible to use ffmpeg to push output to a media server or setup a live streaming video feed of the X11 session?

---

### Post by morean51 on 2011-03-17
thank you that works great it is simply smooth love this tutorial

---

### Post by verb3k on 2011-03-20
Someone is working on a python GUI application for screencasting with ffmpeg+x264:
[https://code.launchpad.net/kazam](https://code.launchpad.net/kazam)

---

### Post by Ixtao on 2011-03-25
Oh, thank you so much for the tutorial!! I wanted to do screencasting for a long time now and when I finally found something I could really use it for (pitching a solution for sharing pictures that is made at our education, with the use of gallery3) I stumbled upon this tutorial. 

As I want to use open source solutions regardless of a whatever lack of quality as long as it's getting the point across this worked out beautifully. I didn't experience a lack of quality in the .ogg end result at all actually.. I was surprised the 'lossless' .mkv file went from 100mb to only 60mb in the .ogg result.. 

Btw; I anticipated that explaining how to use program you don't need 30fps, so I set it to 23fps which was fine..

---

### Post by verb3k on 2011-03-25
You can encode to the new open format "WebM", which should give you much better quality than .ogg with Theora. Just replace libtheora with libvpx (assuming you followed the ffmpeg building guide, you should have that included as well) and encode the file in 2 passes with the -pass 1/2 option. Also, change the extension to .webm instead of .ogg.

**Example**:
Pass 1:```
ffmpeg -i output.mkv -an -vcodec libvpx -b 1000k -pass 1 our-final-product.webm

```Pass 2:```
ffmpeg -i output.mkv -acodec libvorbis -ab 128k -ac 2 -vcodec libvpx -b 1000k -threads 2 -pass 2 our-final-product.webm
```
Change the bitrate (-b 1000k) to control the size/quality tradeoff. Also, change the number of threads (-threads 2) to suit the number of threads your CPU has. If your CPU is not multi-threaded, you can omit the -threads option completely. If you have a modern web browser, you can open the file and play it natively inside it. A WebM file consists of VP8 video and Vorbis audio mulitplexed into a .webm container (which is basically a subset of the Matroska container, aka .mkv).

---

### Post by verb3k on 2011-03-26
Guide update: Added WebM example, updated the guide to reflect the change from "q" to "ctrl-c" to stop recording.

---

### Post by HolgerB on 2011-04-04
Hi there,

I've been searching this thread and read various postings in the www but didn't find a real answer to my issue.
It has been awhile since I captured some gaming videos under Linux with ffmpeg but on my newly set up Ubuntu 10.04 x64 box ffmpeg (with x11grab) records an ugly white mouse cursor in the middle of the screen even if no cursor should be visibile (e.g. playing Q3A in fullscreen mode).
On the same system with archlinux x64 I never experience such behaviour. Of course it is possible that this was an older version of ffmpeg which didn't capture mouse pointers at all ?
Is there an option to disable any mouse cursor capturing ?

Edit: I would be fine with rebuilding ffmpeg from source.

TIA,
Holger

P.S.: A small note to those who experience audio delay with ffmpeg and PA. I found out that my system produces a constant delay of 2100 ms. If I resync audio and video afterwards by this value everything is perfectly in sync.

---

### Post by FakeOutdoorsman on 2011-04-04
> **HolgerB said:**
> Is there an option to disable any mouse cursor capturing ?
There is a *nomouse* option:
```
-i :0.0+nomouse
```
Works with FFmpeg from the repository for Maverick at least.

---

### Post by verb3k on 2011-04-04
> **FakeOutdoorsman said:**
> There is a *nomouse* option:
```
-i :0.0+nomouse
```
Works with FFmpeg from the repository for Maverick at least.

Awesome. Works on git FFmpeg too. NB4 I add it to the guide.
Thanks.

EDIT: Added. Thanks again.

---

### Post by HolgerB on 2011-04-06
> **FakeOutdoorsman said:**
> There is a *nomouse* option:
```
-i :0.0+nomouse
```Works with FFmpeg from the repository for Maverick at least.
Thanks for your hint but at least my version SVN-r0.5.1-4:0.5.1-1ubuntu1.1 does not seem to care :lolflag:

---

### Post by M759 on 2011-04-07
I've had some experience with gtk-recordMyDesktop, but after I switched from a 32-bits desktop pc to a 64-bits laptop (Ubuntu 10.10), RMD started performing badly: The last part of the captured video does not show up in the final ogv video:confused:

I tried ffmpeg using this and many other guides, without the expected/promised result. You're claiming a zero-quality loss, although I experience the opposite: see attachment.
The upper part of the screenshot shows the original sample, the bottom part shows the result after capturing: A very perceivable result. The colors are different, and some particles are faded.

How can I capture a part of my screen **without any loss in quality**? I want to edit the captured screen using Kdenlive, then upload it to YouTube (using h.264).

I used the following code:
```
ffmpeg -f x11grab -r 15 -s 768x512 -i :0.0+810,55 -vcodec libx264 -vpre lossless_ultrafast -threads 0 /tmp/ffmpeg-tests/out.mkv
```I tried all possible vpre options and over twenty file extensions, yet no satisfying result. Could anyone help me with solving this extremely annoying issue?

---

### Post by HolgerB on 2011-04-07
> **M759 said:**
> I my screen **without any loss in quality**? I want to edit the captured screen using Kdenlive, then upload it to YouTube (using h.264).

I would go for huffyuv for video codec which is lossless. Audio could be plain pcm or flac.
You should always check out the captured video in mplayer or vlc if you experience image corruption in kdenlive or any other video editing software.

I can post my ffmpeg rec command this evening if you like.

---

### Post by verb3k on 2011-04-07
> **M759 said:**
> I've had some experience with gtk-recordMyDesktop, but after I switched from a 32-bits desktop pc to a 64-bits laptop (Ubuntu 10.10), RMD started performing badly: The last part of the captured video does not show up in the final ogv video:confused:

I tried ffmpeg using this and many other guides, without the expected/promised result. You're claiming a zero-quality loss, although I experience the opposite: see attachment.
The upper part of the screenshot shows the original sample, the bottom part shows the result after capturing: A very perceivable result. The colors are different, and some particles are faded.

How can I capture a part of my screen **without any loss in quality**? I want to edit the captured screen using Kdenlive, then upload it to YouTube (using h.264).

I used the following code:
```
ffmpeg -f x11grab -r 15 -s 768x512 -i :0.0+810,55 -vcodec libx264 -vpre lossless_ultrafast -threads 0 /tmp/ffmpeg-tests/out.mkv
```I tried all possible vpre options and over twenty file extensions, yet no satisfying result. Could anyone help me with solving this extremely annoying issue?

This is probably because libx264 does not yet support the 4:4:4 color space; edges of very small and sharp lines might appear a bit blurred. Go ask the x264 developers to add it.

---

### Post by M759 on 2011-04-07
> **HolgerB said:**
> I would go for huffyuv for video codec which is lossless. Audio could be plain pcm or flac.
You should always check out the captured video in mplayer or vlc if you experience image corruption in kdenlive or any other video editing software.

I can post my ffmpeg rec command this evening if you like.

Please:)

I use VLC to check my video's.

---

### Post by HolgerB on 2011-04-07
```
# Auflösung für Screencapture wählen"
RES=$(zenity --text="Aufnahmeauflösung auswählen" --list --title "Auflösung:" --column "Bildschirmauflösung:" "1920x1080" "1360x768" "1280x960" "1024x768" "960x600" "960x540" "640x480" --height=220)

# Gewählte Bildschirmauflösung setzen
xrandr -s $RES

# Aufnahmenamen generieren
TIME_STAMP=$(date +day%j-%Hh%Mmin)
CAPTURE_NAME="gamerec-$TIME_STAMP-huffyuv-$RES.avi"

echo $CAPTURE_NAME
# Aufnahme per ffmpeg starten
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s $RES -i :0.0+nomouse -acodec pcm_s16le -vcodec huffyuv -sameq $CAPTURE_NAME
```

Some comments are german but I guess the commands speak for themselve

:mrgreen:

---

### Post by M759 on 2011-04-07
Unfortunately, I still don' get the expected output (see attachment). What could be wrong?
```
ffmpeg -f x11grab -r 15 -s 768x512 -i :0.0+810,55 -sameq -vcodec huffyuv /tmp/ffmpeg-tests/out.avi
```Which codec do support the features described by verb3k?

---

### Post by HolgerB on 2011-04-07
Hm, strange...for me this works fine. Even when capturing games with OpenGL acceleration.

Unfortunately your screenshot does reveal nothing to me.

BTW: No need always to do full-quotes.

Edit: Yes, much better readable without full-quotes ;)
I see your issue now but this is not the usual behaveiour. I would suspect any other issues. Did you disable any desktop effects ? 
As pointed out: This works perfectly for me during capturing games up to 800x600 at 30 fps without any visual impact in 1:1 quality.

---

### Post by M759 on 2011-04-07
I've disabled desktop effects. My screen resolution is 1600x900.

Can you record my screenshot using my supplied command, and tell me whether your results equal mine, in order to determine whether the issue is caused by ffmpeg, or my configuration/files?

---

### Post by HolgerB on 2011-04-07
Shure I can try your commandline. What would you like me to capture ?
Didn´t the ffmpeg output reveal any issues ? BTW: What about audio ?
Do you set your audio codec ?
And for huffyuv -sameq is not needed since the codec is lossless in general.

---

### Post by M759 on 2011-04-07
```
ffmpeg -f x11grab -r 15 -s 768x512 -i :0.0+810,55 -vcodec libx264 -vpre lossless_ultrafast -threads 0 /tmp/ffmpeg-tests/out.mkv
```This picture. Attach a snapshot of your screen capture to your next reply.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188389&stc=1&d=1302202461[/IMG]

---

### Post by M759 on 2011-04-08
I'm back to recordMyDesktop :P
I found the cause of the throw-away of all frames after fram ~3200. I mounted my /tmp to the RAM, allowing a maximum virtual disk space of 2 GB. After about 3.2k frames, my /tmp was full, denying any attempt to store more data.

---

### Post by varunvats on 2011-05-28
Hi verb3k!

First of all, thanks for the great tutorial! It has been of great help!

I followed the instructions as listed by FakeOutdoorsman [here ]("http://ubuntuforums.org/showthread.php?t=786095")to complete the installation without any errors. However, when I try to use the command in Step 1: 
```

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv 

```I get the following output:
```

ffmpeg version git-N-30357-gb2a6f25, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 28 2011 13:44:51 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil    51.  3. 0 / 51.  3. 0
  libavcodec   53.  6. 1 / 53.  6. 1
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  1. 0 / 53.  1. 0
  libavfilter   2. 11. 0 /  2. 11. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[alsa @ 0x9635b40] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x9635b40] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1306618191.989985, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[x11grab @ 0x9626920] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0x9626920] shared memory extension found
[x11grab @ 0x9626920] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1306618192.390409, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
File 'output.mkv' already exists. Overwrite ? [y/N] y
[buffer @ 0x9633f60] w:1024 h:768 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[ffsink @ 0x96374c0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x96367c0] w:1024 h:768 fmt:bgra -> w:1024 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x9634700] --psnr used with psy on: results will be invalid!
[libx264 @ 0x9634700] --tune psnr should be used if attempting to benchmark psnr!
[libx264 @ 0x9634700] interlace + weightp is not implemented
[libx264 @ 0x9634700] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[COLOR=Red][libx264 @ 0x9634700] constant rate-factor is incompatible with 2pass.[/COLOR]
Output #0, matroska, to 'output.mkv':
    Stream #0.0: Video: libx264, yuv420p, 1024x768, q=0-69, pass 1, pass 2, 200 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, pass 1, pass 2, 1411 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
[COLOR=DarkOrange]Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height[/COLOR]

```I believe the problem is with the line in red. My understanding is that CRF (Constant Rate-Factor) is a single-pass encoding scheme and somewhere (probably in the preset file) 2pass is being specified. I looked at the preset file in ~/ffmpeg/ffpresets/libx264-lossless_ultrafast.ffpreset for any such specification but couldn't find any. Neither could I find a specification for CRF (-crf).

Any pointer to what I could do to sort this out? 

By the way, I tried 
```

-preset slower 

```and 
```

-preset slow 

```instead of 
```

-vpre lossless_ultrafast // and other lossless presets.

```which seemed to work fine. However, I'm not satisfied with the video quality resulting from these options and am not to keen on using them. 

Could this be an issue with the hardware? The relevant  system specs are listed below:
OS: Ubuntu 11.04 (32-bit)
RAM: 4GB
GPU: ATI Radeon HD 5730 (has been an issue with Unity in Ubuntu 11.04)

I also tried re-installing all the components, which wasn't of any help.

Any directions on where I should look are appreciated.

Thank you for your time!

---

### Post by varunvats on 2011-05-28
Well, the best video quality that I could get  was with these options:
```

ffmpeg -f x11grab -s 1366x768 [COLOR=Blue]-r 30[/COLOR] -i :0.0 -vcodec libx264 out.mkv

```The output: 

```

ffmpeg version git-N-30357-gb2a6f25, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 28 2011 13:44:51 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil    51.  3. 0 / 51.  3. 0
  libavcodec   53.  6. 1 / 53.  6. 1
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  1. 0 / 53.  1. 0
  libavfilter   2. 11. 0 /  2. 11. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[x11grab @ 0xab51b40] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768
[x11grab @ 0xab51b40] shared memory extension found
[x11grab @ 0xab51b40] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1306628110.928816, bitrate: 1007124 kb/s
    Stream #0.0: Video: rawvideo, bgra, 1366x768, 1007124 kb/s, 30 tbr, 1000k tbn, 30 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0xab5eac0] w:1366 h:768 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[ffsink @ 0xab5eb20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0xab42040] w:1366 h:768 fmt:bgra -> w:1366 h:768 fmt:yuv420p flags:0x4
[COLOR=DarkOrange][libx264 @ 0xab444e0] Default settings detected, using medium profile[/COLOR]
[libx264 @ 0xab444e0] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0xab444e0] profile High, level 3.2
[libx264 @ 0xab444e0] 264 - core 115 r1995 c1e60b9 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, matroska, to 'out.mkv':
  Metadata:
    encoder         : Lavf53.2.0
    Stream #0.0: Video: libx264, yuv420p, 1366x768, q=2-31, 200 kb/s, 1k tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop, [?] for help
frame=   80 [COLOR=Blue]fps= 16[/COLOR] q=27.0 Lsize=     206kB time=3.90 bitrate= 431.6kbits/s    its/s    
video:204kB audio:0kB global headers:0kB muxing overhead 0.506686%
frame I:1     Avg QP:18.76  size: 66434
[libx264 @ 0xab444e0] frame P:21    Avg QP:22.86  size:  6545
[libx264 @ 0xab444e0] frame B:58    Avg QP:28.54  size:    83
[libx264 @ 0xab444e0] consecutive B-frames:  2.5%  2.5%  0.0% 95.0%
[libx264 @ 0xab444e0] mb I  I16..4: 71.6%  3.7% 24.7%
[libx264 @ 0xab444e0] mb P  I16..4:  0.3%  0.0%  1.4%  P16..4:  1.6%  0.1%  0.1%  0.0%  0.0%    skip:96.6%
[libx264 @ 0xab444e0] mb B  I16..4:  0.1%  0.0%  0.0%  B16..8:  0.9%  0.0%  0.0%  direct: 0.0%  skip:99.0%  L0:37.9% L1:62.1% BI: 0.0%
[libx264 @ 0xab444e0] 8x8 transform intra:2.9% inter:35.2%
[libx264 @ 0xab444e0] coded y,uvDC,uvAC intra: 30.6% 36.8% 34.2% inter: 0.1% 0.2% 0.1%
[libx264 @ 0xab444e0] i16 v,h,dc,p: 66% 34%  0%  0%
[libx264 @ 0xab444e0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 11% 54% 26%  1%  1%  2%  2%  1%  2%
[libx264 @ 0xab444e0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 28% 33% 17%  2%  3%  4%  4%  3%  5%
[libx264 @ 0xab444e0] i8c dc,h,v,p: 63% 18% 17%  2%
[libx264 @ 0xab444e0] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0xab444e0] ref P L0: 68.0%  6.2% 24.1%  1.8%
[libx264 @ 0xab444e0] ref B L0: 64.4% 32.8%  2.8%
[libx264 @ 0xab444e0] ref B L1: 92.0%  8.0%
[libx264 @ 0xab444e0] kb/s:410.54


```

Again, this is only video, no audio.

One thing that intrigued me was even though I set the fps to 30, the output shows it was changed to 16! Any reason why that could be happening? Something to do with the line "[COLOR=DarkOrange]Default settings detected, using medium profile[/COLOR]"?

Thanks!

---

### Post by varunvats on 2011-05-28
In Step 2 **Example 1**, instead of 
```

ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 [COLOR=Red]-vpre slow[/COLOR] -crf 22 -threads 0 our-final-product.mp4

```I had to use
```

ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 [COLOR=Blue]-preset slow[/COLOR] -crf 22 -threads 0 our-final-product.mp4

```
Not sure if the recent updates are the reason. Quoting from [http://ffmpeg.org/index.html](http://ffmpeg.org/index.html)
> 
 FFmpeg now accesses x264 presets via libx264. This extends functionality by introducing several new libx264 options including *-preset*, *-tune*, and *-profile*. You can read more detailed information about these options with "x264 --fullhelp". 

   The syntax has changed so be sure to update your commands. Example: 
ffmpeg -i input -vcodec libx264 -preset fast -tune film -profile main -crf 22 -threads 0 output 

Thanks.

---

### Post by verb3k on 2011-05-29
Hi varunvats,

I've updated the guide to the new -preset syntax.

Regarding the low fps, that's probably because you're not using the lossless_ultrafast preset. If you don't specify a preset, it defaults to "medium" which is very slow for encoding on-the-fly. Also, I'm not getting "constant rate-factor is incompatible with 2pass." with lossless preset. Maybe you messed the preset file by editing it?

---

### Post by Saiko Berry on 2011-06-03
Hi. Im getting the same error the guy got one page ago. I switched to 

```

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset slow -threads 0 big.mkv
```But I get a ridiculously laggy 1-3fps recovering with lossy video. None of the solutions in this thread seem to have remotely helped, and gtk-recordmydesktop has terrible sync issues so there is no using that.. (It also takes a year to encode... >.<)

Help please?

```
[libx264 @ 0xaa75500] constant rate-factor is incompatible with 2pass.
Output #0, matroska, to 'big.mkv':
    Stream #0.0: Video: libx264, yuv420p, 1024x768, q=0-69, pass 1, pass 2, 200 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, pass 1, pass 2, 1411 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```This is the syntax that gives me the error

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 big.mkv
```

Side note, when I do use slow, I get this kind of ****. See brackets.

```
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop, [?] for help
frame=  122 <<<fps=  1>>> q=13.0 Lsize=    6048kB time=00:00:26.33 bitrate=1881.1kbits/s    

```

---

### Post by verb3k on 2011-06-03
ok, let's try to troubleshoot the problem. In the ffmpeg source folder (from which you compiled ffmpeg), there is a directory calld 'ffpresets'. We are going to instruct ffmpeg to use that preset instead of the one installed on your system.


```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -fpre /home/user/ffmpeg/ffpresets/libx264-lossless_ultrafast.ffpreset -threads 0 big.mkv

```

replace "/home/user/ffmpeg/ffpresets/libx264-lossless_ultrafast.ffpreset" with the path to the preset in ffmpeg source directory on your system. Also note we're using "-fpre" not "-vpre".

Can you reproduce the problem with that method described above?

---

### Post by FakeOutdoorsman on 2011-06-03
I can reproduce this on 32-bit Natty, but not on x86_64 Arch or Lucid. I'm currently attempting a *git bisect* because this confounds me.

---

### Post by verb3k on 2011-06-03
> **FakeOutdoorsman said:**
> I can reproduce this on 32-bit Natty, but not on x86_64 Arch or Lucid. I'm currently attempting a *git bisect* because this confounds me.

Thanks for the confirmation FakeOutdoorsman. I'm on Natty 64-bit and can't reproduce the problem.

---

### Post by FakeOutdoorsman on 2011-06-03
Maybe I missed something simple, but it looked like a regression to me, so I filed a bug report:
[https://ffmpeg.org/trac/ffmpeg/ticket/264](https://ffmpeg.org/trac/ffmpeg/ticket/264)

---

### Post by FakeOutdoorsman on 2011-06-13
The bug report I mentioned in my previous post (x11grab w/ libx264 fails on 32-bit) is getting no attention from the developers right now, and I have no idea how to fix it, so if anyone else is being affected by it then it might be a good idea to add a comment to the report.

---

### Post by verb3k on 2011-06-13
Ive added a comment to the bug, requesting some developer attention and a fix.
(p.s. bug number is somewhat unique and related to the bug :))

---

### Post by FakeOutdoorsman on 2011-06-22
Thanks for the comments. This bug has been fixed: [eval: Fix 32bit unsigned parsing](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=940a55ccf4898c641d0b3b7138d679943611e1d6).

---

### Post by Cavsfan on 2011-06-24
> **FakeOutdoorsman said:**
> Thanks for the comments. This bug has been fixed: [eval: Fix 32bit unsigned parsing]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=940a55ccf4898c641d0b3b7138d679943611e1d6").

Thanks! So, would it be necessary to remove and re-install according to page 1? 
I hope that is not a dumb question but, I somehow feel that it is! :oops:

---

### Post by FakeOutdoorsman on 2011-06-24
Correct. You will need to update your source files and re-compile FFmpeg to take advantage of this bug fix (assuming your FFmpeg is older than the bug fix).

See the **Updating FFmpeg and x264** section of [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).

---

### Post by cadens on 2011-07-27
Hi,

I followed the instruction  on** [HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")**             
             and always get the same error when screncasting with the following command:
> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkvI uninstall and install again ffmpeg and this is the error I get each time:
> ................
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop, [?] for help
[COLOR=Red][matroska @ 0x981a040] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1[/COLOR]
av_interleaved_write_frame(): Invalid argument
 

I Remember that all this worked before in kernel ** 2.6.35-27-generic-pae**.
Anyone can help me please, I'm runningkernel** 2.6.35-30-generic-pae**.

I am grateful for any advice.

PS: I'm gonna uninstall and re-install again ffmpeg...

---

### Post by ron999 on 2011-07-27
> **cadens said:**
> 
I am grateful for any advice.


Hi
I have exactly the same problem - "non monotonically increasing dts"
It used to work OK, but not anymore.

I can work around it by using "-acodec flac" instead of "-acodec pcm_s16le".

---

### Post by cadens on 2011-07-27
> **ron999 said:**
> Hi
I have exactly the same problem - "non monotonically increasing dts"
It used to work OK, but not anymore.

I can work around it by using "-acodec flac" instead of "-acodec pcm_s16le".

Hi Ron999!
It's working here with "**-acodec flac**" instead of "**-acodec pcm_s16le**".
Thanks! 

So the problem is the pcm audio codec?

---

### Post by ron999 on 2011-07-27
> **cadens said:**
> 
So the problem is the pcm audio codec?
Hi
The problem seems to be when using pcm in mkv or mka files.

pcm works OK for me when used like this:-
```
ffmpeg -y -f alsa -ac 2 -i pulse -acodec pcm_s16le audio1.wav
```

But gives me monotonic errors when used like this:-
```
ffmpeg -y -f alsa -ac 2 -i pulse -acodec pcm_s16le audio1.mka
```

---

### Post by mocha on 2011-07-28
> **ron999 said:**
> Hi
The problem seems to be when using pcm in mkv or mka files.

pcm works OK for me when used like this:-
```
ffmpeg -y -f alsa -ac 2 -i pulse -acodec pcm_s16le audio1.wav
```

But gives me monotonic errors when used like this:-
```
ffmpeg -y -f alsa -ac 2 -i pulse -acodec pcm_s16le audio1.mka
```

This is probably either a new bug in ffmpeg or some intentional change they made.  We need to search the git logs.  I use an ffmpeg compiled from git about 3 weeks ago that does not exhibit this issue.

---

### Post by FakeOutdoorsman on 2011-07-28
Looks like [alsa: limit buffer_size to 32768 frames](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=e35c674d13a7f180412cfe058530a2e7f1d49a90) is the problem. Anyone want to confirm?
```
sudo apt-get remove ffmpeg
cd ~/ffmpeg
make distclean
git checkout e35c674d13a7f180412cfe058530a2e7f1d49a90
./configure
make
./ffmpeg -f alsa -ac 2 -i pulse -acodec pcm_s16le -y ~/output.mkv
make distclean
git checkout master
```

---

### Post by ron999 on 2011-07-28
> **FakeOutdoorsman said:**
>  Anyone want to confirm?

Watch this space.:)

Edit
Wait a minute, there's no need for me to do this. I've already got the fault.

---

### Post by ron999 on 2011-07-28
For me, the problem's still there with parent of git checkout e35c674d13a7f180412cfe058530a2e7f1d49a90

git checkout 8bfd7f6a475225a0595bf657f8b99a8fffb461e4

> ron@ubuntu:~/GITS/ffmpeg$ ./ffmpeg -f alsa -ac 2 -i pulse -acodec pcm_s16le -y ~/output.mkv
ffmpeg version 8bfd7f6, Copyright (c) 2000-2011 the Libav developers
  built on Jul 28 2011 22:46:07 with gcc 4.4.3
  configuration: 
  libavutil    51.  8. 0 / 51.  8. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
[alsa @ 0x93a22c0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x93a22c0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1311889656.860130, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Output #0, matroska, to '/home/ron/output.mkv':
  Metadata:
    encoder         : Lavf53.2.0
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
[matroska @ 0x93bb040] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 387 >= 387
av_interleaved_write_frame(): Invalid argument

---

### Post by FakeOutdoorsman on 2011-07-28
If you want to use the last commit that worked then do:
```
sudo apt-get remove ffmpeg
cd ~/ffmpeg
make distclean
git pull
git checkout 8bfd7f6a475225a0595bf657f8b99a8fffb461e4
./configure, make, checkinstall as shown in the [FFmpeg compile guide](http://ubuntuforums.org/showthread.php?t=786095).
make distclean
git checkout master
```

**ron999:** I didn't see your last post. Strange. This commit works for me on 32-bit Natty.

---

### Post by cadens on 2011-07-28
> **FakeOutdoorsman said:**
> If you want to use the last commit that worked then do:
```
sudo apt-get remove ffmpeg
cd ~/ffmpeg
make distclean
git pull
git checkout 8bfd7f6a475225a0595bf657f8b99a8fffb461e4
./configure, make, checkinstall as shown in the [FFmpeg compile guide]("http://ubuntuforums.org/showthread.php?t=786095").
make distclean
git checkout master
```**ron999:** I didn't see your last post. Strange. This commit works for me on 32-bit Natty.

The following command works for me! Thanks FakeOutdoorsman!
> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv

By the way, why have "ctrl+c" to stop screencasting instead of "q"?

---

### Post by FakeOutdoorsman on 2011-07-28
> **cadens said:**
> By the way, why have "ctrl+c" to stop screencasting instead of "q"?

I blame [ffmpeg: get rid of the 'q' key schizofrenia](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=8fb566fdf839206584b1dec7da2eb9c9540108fa).

I think it's some flotsam that was merged from libav (the FFmpeg fork).

---

### Post by FakeOutdoorsman on 2011-08-02
Two new x11grab options have been added: follow_mouse and show_region.
```
-follow_mouse 100 -show_region 1
```
From the documentation:
[list]
[*]**follow_mouse** - Only follows when mouse pointer reaches within 100 pixels to the edge of region.
[*]**show_region** - The grabbing region will be indicated on screen.
[/list]
If you use both options then, "the grabbing region indication will follow the mouse pointer".

---

### Post by FakeOutdoorsman on 2011-08-03
> **rongden said:**
> great guide . I'll test :)

Are you a robot?

---

### Post by RottNKorpse on 2011-08-09
> **verb3k said:**
> **Example 1:**

```
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -preset slow -crf 22 -threads 0 our-final-product.mp4
```In the above example, we encode the audio to AAC at a bitrate of 128k with 2 audio channels (stereo). We encode the video to the high quality H.264 video compression standard. We use the preset "slow" and a CRF value of 22 for rate control. The output file will be named “our-final-product.mp4&#8243; and will be muxed in an .mp4 container. Note that FFmpeg determines the container format of the output file based on the extension you specify (i.e. if you specify the extension as .mkv, your file will be muxed into an .mkv matroska container). You can tweak the CRF value to get different results. The lower you set the CRF value, the better your video’s quality will be, and consequently the file size and encoding time will increase, and vice-versa.
When I tried to use this (Ubuntu 10.10 / ffmpeg SVN-r25943) an error occurred stating **"Unrecognized option 'preset'"**

I seem to have fixed it though by replacing "-preset" with "-vpre" although I didn't take into account "-apre" so I don't know if leaving that out would cause any issues.

I have tested the final output file when using -vpre and it seems to work fine without utilizing -apre

Hope this helps anyone having the same issue.

---

### Post by OlympicSoftworks on 2011-08-11
:KSGreat tutorial:KS

I get magnificent grabs of World of Warcraft with this, and can run them through re-encoding for upload to youtube for my guild.  No problemo, but...I cannot find a video editor that reads the raw output of the tutorial's command.  I could re-encode it to a lower quality format and then edit it, but that really defeats the purpose.

So, what editor is recommended to edit the raw...or is there a better version of raw to use if editing is desired?

btw, WinFF is also a very nice front-end for anyone not understanding the nuts and bolts of the command line for re-encoding...just sayin.

Thanks for any help on this folks.

---

### Post by debd on 2011-08-13
very nice tutorial ^^  

btw.. anybody know how to use the -newaudio option in ffmpeg ??...I mean the syntax sequence? In the man page its not clear :-/

I want to add a new audio stream to a video recorded with -an (no audio).

---

### Post by Bonster on 2011-09-04
> **cadens said:**
> Hi Ron999!
It's working here with "**-acodec flac**" instead of "**-acodec pcm_s16le**".
Thanks! 

So the problem is the pcm audio codec?

Thanks i will try flac now

This error only occurs when im using pulse ( ***-i pulse***), with alsa ( ***-i hw:0,0*** ) it runs fine if anyone is wondering.

[COLOR="Red"][matroska @ 0x981a040] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1[/COLOR]

---

### Post by scratchr on 2011-09-06
Why did you delete your post!? ARGGG!
[http://web.archive.org/web/20100322194101/http://ubuntuforums.org/showthread.php?t=1392026]("http://web.archive.org/web/20100322194101/http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by FakeOutdoorsman on 2011-09-06
Requesting a mod to move the thread to [Outdated Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=255) would have been a better way of retiring it, in my opinion.

---

### Post by OlympicSoftworks on 2011-09-07
Wow.  The thread started a year ago, was updated from time to time by Verb3k, and it has had continuing activity weekly ever since.  I don't even know that it was a candidate for retiring yet.

Maybe he did it so he wouldn't be asked any more questions about it?  Kinda lame to remove all the data he had been updating the whole time instead of just saying "you're on your own now people".  But whatever.

Wayback only archived it once, a year ago.  But that's enough to piece together most of what he had.  Thanks for that link Scratchr.

---

### Post by Bonster on 2011-09-07
Since i got the 2nd post on this thread, ill post it up again in a bit =)

---

### Post by OlympicSoftworks on 2011-09-09
Thanks Bonster, well done=D>.  I'll add a bit of what I've been able to accomplish on this subject next week after I'm done moving.

---

### Post by rulet on 2011-10-01
Hello. I'm trying to record directly to webm using f.e. this command:

> ffmpeg -f alsa -ac 2 -i pulse -an -f x11grab -r 30 -s 1440x900 -i :0.0 -threads 4 -y 1.webm

But I get only video without a sound(not from microphon nor from internal sound).
Any ideas?

... I just have to take away -an option(which meens without audio) and now it records sound also but with soma delay in 1sec.
 So command is


> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1440x900 -i :0.0 -threads 4 -y 1.webm

---

### Post by FakeOutdoorsman on 2011-10-03
The example in *Step 1* need to be updated because the text file based lossless presets have been depreciated in favor of directly accessing the presets via libx264:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 **-preset ultrafast -crf 0** -threads 0 output.mkv
```
A nice side effect is that this method encodes faster in my tests, but I only tested file inputs and not x11grab which could be a bottleneck.

---

### Post by hellxwxrld on 2011-10-04
Hi, FYI FFcast has been updated to 1.0 and now supports audio recording and everything else.
The syntax has changed and all but it's a real win. For example, FakeOutdoorsman's FFmpeg example above translated into FFcast syntax would be something like this: ```
 ffcast -s ffmpeg -f alsa -ac 2 -i pulse -r 30 -- -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv 
``` which prompts the user to select a region (xrectsel) and records that region. 

Check out the [**announcement**]("https://bbs.archlinux.org/viewtopic.php?id=127570") and [**README**]("https://github.com/lolilolicon/FFcast2#readme").

---

### Post by Bonster on 2011-10-06
Oh they changed presets again, ill update it in a bit then. Thanks

---

### Post by OlympicSoftworks on 2011-10-07
All posts in this thread should really make use of the new presets in the current (compiled) version of FFMPEG.  It's a shame that the version of FFMPEG currently maintained with the LTS version of Ubuntu is now so different from the mainstream version, but that is the nature of F/LOSS.

---

### Post by perspectoff on 2011-10-07
> **OlympicSoftworks said:**
> All posts in this thread should really make use of the new presets in the current (compiled) version of FFMPEG.  It's a shame that the version of FFMPEG currently maintained with the LTS version of Ubuntu is now so different from the mainstream version, but that is the nature of F/LOSS.

That's the nature of all software, not just F/LOSS. Stop sniping.

---

### Post by OlympicSoftworks on 2011-10-07
Whoa there bucky; I'm making a suggestion, not sniping.  F/LOSS moves very fast sometimes and often leaves less well-informed users wondering where to get up-to-date info on their software.  I've been using GNU/Linux for 9 years now and have had to play catch-up often enough to be used to it now, less experienced users of GNU/Linux may well be caught off-guard by this.

I was suggesting that anyone posting in this thread to help should be conscious of this.  And trying to acknowledge to anyone following this thread to seek help that there have been some serious changes in the FFMPEG utility that may lead to frustration, and they should be aware of it.  The base of user documentation will catch up before too long and everyone will be rockin along with the improvements.

As to the other assertion; yes all software changes and advances but proprietary software usually doesn't go through radical changes without much fanfare and a conscientious effort to iterate versions so that people looking for updated info are not confused.  In the Free-Software camp however this almost never happens.  It simply is not possible with all the vendors and iterations/versions of the same software still in circulation.

This is only made more problematic for some people by the fact that various projects seem to stay consistent in improvements & bug-fixes while other projects seem to lurch forward from time to time with significant changes that create ripples in related efforts.  Progress is progress though, and due to the nature of co-operation needed for these things to move, I will absolutely take this occasional difficulty over stagnation any day of the week.

So, just cool your jets man.  I'm on the right side of this.

---

### Post by FakeOutdoorsman on 2011-10-27
I propose changing the example from step 1 to:
> ffmpeg -f alsa -acodec pcm_s16le -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -acodec pcm_s16le output.mkv
Changes:
[list]
[*]removed *-threads 0* because it is now default with libx264
[*]move *-acodec pcm_s16le* as an input option
[/list]
A common error I see in *#ffmpeg* IRC from users of this guide is:
```
[matroska @ 0x3459040] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 62 >= 62
av_interleaved_write_frame(): Invalid argument

```
This seems to occur with PCM audio in matroska container when following the *pavucontrol* instructions from this guide, or when replacing pulse with hw:0,0 or equivalent. For some reason moving the acodec option as an input option seems to prevent this error during my tests (as discovered by Sworddragon on the forum). It does not make sense to me because FFmpeg already detects the input as pcm_s16le.

However, I'm unsure if the audio input devices ever output something other than pcm_s16le, and if they do forcing that format may cause issues.

**Update:** Maybe this isn't such a good suggestion. pavucontrol seems to work with it, but there might be something else going on there. The switch from pulse to hw:0,0 is still not working. I thought it was, but there was a simple mistake in my initial tests. This is an alternative that will probably work, but I'd rather find a way to get everything working in one output:
```
ffmpeg -f alsa -i hw:0,0 -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -an -y output.mkv -acodec pcm_s16le -y output.wav
ffmpeg -i output.mkv -i output.wav -vcodec copy -acodec copy output2.mkv
```

---

### Post by Max Jerry Horowitz on 2012-01-26
Thank you for your great guide! Maybe it should be mentioned that the width and height (parameter -s) should be divisible by 16? In my case, I can notably increase the frame rate by observing this rule! And it is recommended in a lot of tutorials.

P.S. Sorry for my poor English

---

### Post by FakeOutdoorsman on 2012-01-26
> **Max Jerry Horowitz said:**
> Maybe it should be mentioned that the width and height (parameter -s) should be divisible by 16?
For x264 this is not as important as most people believe according to a x264 developer on *#x264* IRC.

> **Max Jerry Horowitz said:**
> In my case, I can notably increase the frame rate by observing this rule!
Can you show any benchmarks?

> **Max Jerry Horowitz said:**
> P.S. Sorry for my poor English
Your English is just fine. I personally believe that non-native English speakers should never include this unfortunately popular phrase, and if the English is too poor we can always ask for clarification.

---

### Post by Max Jerry Horowitz on 2012-01-27
> Can you show any benchmarks?
Two screencasts: The first one with 1024x768, the second with 1022x768. In both cases, the framerate of 30 isn't reached. But the framerate of the first screencast (divisible by 16) is twice as high as the framerate of the second one.
```
user:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s [COLOR=Red]1024x768[/COLOR] -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
ffmpeg version git-2012-01-26-ee0cab7 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 26 2012 13:25:36 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-libvpx
  libavutil      51. 34.101 / 51. 34.101
  libavcodec     53. 60.100 / 53. 60.100
  libavformat    53. 31.100 / 53. 31.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 60.100 /  2. 60.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[alsa @ 0xa5eeb60] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1327641305.824548, bitrate: N/A
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0xa5e9040] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0xa5e9040] shared memory extension found
[x11grab @ 0xa5e9040] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1327641305.876321, bitrate: 754974 kb/s
    Stream #1:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
File 'output.mkv' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0xa60a940] w:1024 h:768 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0xa60ac20] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0xa60b180] w:1024 h:768 fmt:bgra -> w:1024 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0xa5efee0] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0xa5efee0] profile High 4:4:4 Predictive, level 3.1, 4:2:0 8-bit
[libx264 @ 0xa5efee0] 64 - core 120 r2146 bcd41db - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf53.31.100
    Stream #0:0: Video: h264, yuv420p, 1024x768, q=-1--1, 1k tbn, 30 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #0:1 (pcm_s16le -> pcm_s16le)
Press [q] to stop, [?] for help
frame=   10 fps=  0 q=0.0 size=     513kB time=00:00:02.70 bitrate=1553.6kbits/s
frame=   21 fps= 20 q=0.0 size=     673kB time=00:00:03.30 bitrate=1669.2kbits/s
frame=   30 fps= 19 q=0.0 size=     769kB time=00:00:03.73 bitrate=1685.8kbits/s
frame=   42 fps= 20 q=0.0 size=     929kB time=00:00:04.36 bitrate=1741.6kbits/s
frame=   54 fps= 21 q=0.0 size=    1089kB time=00:00:04.90 bitrate=1819.6kbits/s
frame=   65 fps= 21 q=0.0 size=    1219kB time=00:00:05.40 bitrate=1849.0kbits/s
frame=   75 fps= 21 q=0.0 size=    1315kB time=00:00:05.83 bitrate=1846.3kbits/s
frame=   85 fps= 20 q=0.0 size=    1475kB time=00:00:06.36 bitrate=1897.6kbits/s
frame=   97 fps= 21 q=0.0 size=    1603kB time=00:00:06.96 bitrate=1884.6kbits/s
frame=  107 [COLOR=Red]fps= 20[/COLOR] q=0.0 size=    1731kB time=00:00:07.43 bitrate=1907.3kbits/s
video:1619kB audio:5106kB global headers:0kB muxing overhead 2.138274%
[libx264 @ 0xa5efee0] frame I:3     Avg QP: 0.00  size:  4446
[libx264 @ 0xa5efee0] frame P:500   Avg QP: 0.00  size:  3288
[libx264 @ 0xa5efee0] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0xa5efee0] mb P  I16..4: 94.0%  0.0%  0.0%  P16..4:  0.0%  0.0%  0.0%  0.0%  0.0%    skip: 6.0%
[libx264 @ 0xa5efee0] coded y,uvDC,uvAC intra: 0.0% 0.0% 0.0% inter: 0.0% 0.0% 0.0%
[libx264 @ 0xa5efee0] i16 v,h,dc,p: 100%  0%  0%  0%
[libx264 @ 0xa5efee0] i8c dc,h,v,p: 98%  2%  0%  0%
[libx264 @ 0xa5efee0] kb/s:479.23
user:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s [COLOR=Red]1022x768[/COLOR] -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
ffmpeg version git-2012-01-26-ee0cab7 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 26 2012 13:25:36 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-libvpx
  libavutil      51. 34.101 / 51. 34.101
  libavcodec     53. 60.100 / 53. 60.100
  libavformat    53. 31.100 / 53. 31.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 60.100 /  2. 60.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[alsa @ 0xa770b60] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1327641350.964678, bitrate: N/A
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0xa76b040] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1022 height: 768
[x11grab @ 0xa76b040] shared memory extension found
[x11grab @ 0xa76b040] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1327641351.023040, bitrate: 753500 kb/s
    Stream #1:0: Video: rawvideo (BGRA / 0x41524742), bgra, [COLOR=Black]1022x768[/COLOR], 753500 kb/s, 30 tbr, 1000k tbn, 30 tbc
File 'output.mkv' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0xa78c8c0] w:1022 h:768 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0xa78cba0] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0xa78d100] w:1022 h:768 fmt:bgra -> w:1022 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0xa771f40] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0xa771f40] profile High 4:4:4 Predictive, level 3.1, 4:2:0 8-bit
[libx264 @ 0xa771f40] 64 - core 120 r2146 bcd41db - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf53.31.100
    Stream #0:0: Video: h264, yuv420p, 1022x768, q=-1--1, 1k tbn, 30 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #0:1 (pcm_s16le -> pcm_s16le)
Press [q] to stop, [?] for help
frame=    7 fps=  0 q=0.0 size=       1kB time=00:00:00.00 bitrate=   0.0kbits/s
frame=   11 fps= 10 q=0.0 size=     545kB time=00:00:02.76 bitrate=1611.8kbits/s
frame=   17 fps= 10 q=0.0 size=     673kB time=00:00:03.40 bitrate=1620.1kbits/s
frame=   22 fps= 10 q=0.0 size=     769kB time=00:00:03.90 bitrate=1613.2kbits/s
frame=   28 fps= 10 q=0.0 size=     929kB time=00:00:04.53 bitrate=1677.1kbits/s
frame=   33 fps= 10 q=0.0 size=    1025kB time=00:00:05.00 bitrate=1678.4kbits/s
frame=   38 fps= 10 q=0.0 size=    1142kB time=00:00:05.50 bitrate=1700.4kbits/s
frame=   43 fps= 10 q=0.0 size=    1270kB time=00:00:06.06 bitrate=1714.3kbits/s
frame=   48 fps= 10 q=0.0 size=    1366kB time=00:00:06.56 bitrate=1703.5kbits/s
frame=   53 [COLOR=Red]fps= 10[/COLOR] q=0.0 size=    1494kB time=00:00:07.11 bitrate=1719.7kbits/s
video:419kB audio:2819kB global headers:0kB muxing overhead 2.428442%
[libx264 @ 0xa771f40] frame I:1     Avg QP: 0.00  size:  4442
[libx264 @ 0xa771f40] frame P:129   Avg QP: 0.00  size:  3288
[libx264 @ 0xa771f40] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0xa771f40] mb P  I16..4: 94.0%  0.0%  0.0%  P16..4:  0.0%  0.0%  0.0%  0.0%  0.0%    skip: 6.0%
[libx264 @ 0xa771f40] coded y,uvDC,uvAC intra: 0.0% 0.0% 0.0% inter: 0.0% 0.0% 0.0%
[libx264 @ 0xa771f40] i16 v,h,dc,p: 100%  0%  0%  0%
[libx264 @ 0xa771f40] i8c dc,h,v,p: 98%  2%  0%  0%
[libx264 @ 0xa771f40] kb/s:215.19

```I notice this behavior especially when there is any kind of animation on the screen (in this case a running video).

---

### Post by FakeOutdoorsman on 2012-01-27
That's quite the difference, but my tests show no difference:
```
$ ffmpeg -f x11grab -r 60 -s 1680x1040 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 10 -y output.mkv
ffmpeg version N-37154-g01e5e97 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 25 2012 17:19:53 with gcc 4.6.2 20111223 (prerelease)
  configuration: --prefix=/usr --enable-gpl --enable-frei0r --enable-libfaac --enable-libmp3lame --enable-libutvideo --enable-libtheora --enable-libvo-aacenc --enable-version3 --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      51. 34.101 / 51. 34.101
  libavcodec     53. 60.100 / 53. 60.100
  libavformat    53. 30.100 / 53. 30.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 60.100 /  2. 60.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[x11grab @ 0x26015e0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1040
[x11grab @ 0x26015e0] shared memory extension found
[x11grab @ 0x26015e0] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1327700470.316064, bitrate: N/A
    Stream #0:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1680x1040, -2147483 kb/s, 60 tbr, 1000k tbn, 60 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x2614820] w:1680 h:1040 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x260f920] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x2610120] w:1680 h:1040 fmt:bgra -> w:1680 h:1040 fmt:yuv420p flags:0x4
[libx264 @ 0x260e860] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x260e860] profile High 4:4:4 Predictive, level 4.2, 4:2:0 8-bit
[libx264 @ 0x260e860] 64 - core 120 r2146 bcd41db - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=12 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf53.30.100
    Stream #0:0: Video: h264, yuv420p, 1680x1040, q=-1--1, 1k tbn, 60 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> libx264)
Press [q] to stop, [?] for help
frame=   22 fps=  0 q=0.0 size=     449kB time=00:00:00.23 bitrate=15702.8kbits/s
frame=   43 fps= 41 q=0.0 size=     545kB time=00:00:00.76 bitrate=5816.0kbits/s
frame=   64 fps= 41 q=0.0 size=     673kB time=00:00:01.28 bitrate=4290.9kbits/s
frame=   85 fps= 41 q=0.0 size=     769kB time=00:00:01.81 bitrate=3465.0kbits/s
frame=  106 fps= 41 q=0.0 size=     865kB time=00:00:02.33 bitrate=3034.4kbits/s
frame=  127 fps= 41 q=0.0 size=     993kB time=00:00:02.85 bitrate=2852.9kbits/s
frame=  148 fps= 40 q=0.0 size=    1089kB time=00:00:03.38 bitrate=2635.1kbits/s
frame=  169 fps= 40 q=0.0 size=    1217kB time=00:00:03.90 bitrate=2555.4kbits/s
frame=  190 fps= 40 q=0.0 size=    1313kB time=00:00:04.43 bitrate=2425.0kbits/s
frame=  211 fps= 40 q=0.0 size=    1441kB time=00:00:04.95 bitrate=2384.0kbits/s
frame=  232 fps= 40 q=0.0 size=    1557kB time=00:00:05.46 bitrate=2332.5kbits/s
frame=  253 fps= 40 q=0.0 size=    1685kB time=00:00:06.00 bitrate=2300.1kbits/s
frame=  274 fps= 40 q=0.0 size=    2152kB time=00:00:06.51 bitrate=2704.6kbits/s
frame=  295 fps= 40 q=0.0 size=    2248kB time=00:00:07.03 bitrate=2617.6kbits/s
frame=  316 fps= 40 q=0.0 size=    2344kB time=00:00:07.56 bitrate=2537.2kbits/s
frame=  337 fps= 40 q=0.0 size=    2440kB time=00:00:08.08 bitrate=2472.2kbits/s
frame=  358 fps= 40 q=0.0 size=    2536kB time=00:00:08.60 bitrate=2415.3kbits/s
frame=  379 fps= 40 q=0.0 size=    2632kB time=00:00:09.13 bitrate=2360.2kbits/s
frame=  400 fps= 40 q=0.0 size=    2728kB time=00:00:09.65 bitrate=2315.5kbits/s
frame=  401 fps= 40 q=-1.0 Lsize=    2816kB time=00:00:09.99 bitrate=2306.7kbits/s    
video:2812kB audio:0kB global headers:0kB muxing overhead 0.119283%
[libx264 @ 0x260e860] frame I:2     Avg QP: 0.00  size:347847
[libx264 @ 0x260e860] frame P:399   Avg QP: 0.00  size:  5472
[libx264 @ 0x260e860] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0x260e860] mb P  I16..4: 50.5%  0.0%  0.0%  P16..4:  0.0%  0.0%  0.0%  0.0%  0.0%    skip:49.5%
[libx264 @ 0x260e860] coded y,uvDC,uvAC intra: 0.6% 0.4% 0.4% inter: 0.0% 0.0% 0.0%
[libx264 @ 0x260e860] i16 v,h,dc,p: 100%  0%  0%  0%
[libx264 @ 0x260e860] i8c dc,h,v,p: 86%  3% 11%  0%
[libx264 @ 0x260e860] kb/s:2299.51

```

```
$ ffmpeg -f x11grab -r 60 -s 1676x1050 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 10 -y output.mkv
ffmpeg version N-37154-g01e5e97 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 25 2012 17:19:53 with gcc 4.6.2 20111223 (prerelease)
  configuration: --prefix=/usr --enable-gpl --enable-frei0r --enable-libfaac --enable-libmp3lame --enable-libutvideo --enable-libtheora --enable-libvo-aacenc --enable-version3 --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      51. 34.101 / 51. 34.101
  libavcodec     53. 60.100 / 53. 60.100
  libavformat    53. 30.100 / 53. 30.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 60.100 /  2. 60.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[x11grab @ 0x17475e0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1676 height: 1050
[x11grab @ 0x17475e0] shared memory extension found
[x11grab @ 0x17475e0] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1327700329.009954, bitrate: N/A
    Stream #0:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1676x1050, -2147483 kb/s, 60 tbr, 1000k tbn, 60 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x175a820] w:1676 h:1050 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x1755920] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x1756120] w:1676 h:1050 fmt:bgra -> w:1676 h:1050 fmt:yuv420p flags:0x4
[libx264 @ 0x1754860] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x1754860] profile High 4:4:4 Predictive, level 4.2, 4:2:0 8-bit
[libx264 @ 0x1754860] 64 - core 120 r2146 bcd41db - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=12 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf53.30.100
    Stream #0:0: Video: h264, yuv420p, 1676x1050, q=-1--1, 1k tbn, 60 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> libx264)
Press [q] to stop, [?] for help
frame=   21 fps=  0 q=0.0 size=     417kB time=00:00:00.21 bitrate=15797.8kbits/s
frame=   41 fps= 41 q=0.0 size=     545kB time=00:00:00.73 bitrate=6077.5kbits/s
frame=   61 fps= 40 q=0.0 size=     673kB time=00:00:01.23 bitrate=4464.7kbits/s
frame=   81 fps= 40 q=0.0 size=     769kB time=00:00:01.73 bitrate=3633.0kbits/s
frame=  101 fps= 40 q=0.0 size=     897kB time=00:00:02.23 bitrate=3287.6kbits/s
frame=  121 fps= 40 q=0.0 size=     993kB time=00:00:02.73 bitrate=2974.0kbits/s
frame=  141 fps= 40 q=0.0 size=    1089kB time=00:00:03.24 bitrate=2744.6kbits/s
frame=  161 fps= 40 q=0.0 size=    1217kB time=00:00:03.75 bitrate=2657.6kbits/s
frame=  181 fps= 40 q=0.0 size=    1313kB time=00:00:04.25 bitrate=2530.0kbits/s
frame=  201 fps= 40 q=0.0 size=    1441kB time=00:00:04.74 bitrate=2484.9kbits/s
frame=  221 fps= 40 q=0.0 size=    1582kB time=00:00:05.25 bitrate=2469.1kbits/s
frame=  241 fps= 40 q=0.0 size=    1710kB time=00:00:05.75 bitrate=2436.8kbits/s
frame=  261 fps= 40 q=0.0 size=    1838kB time=00:00:06.26 bitrate=2403.4kbits/s
frame=  281 fps= 40 q=0.0 size=    2279kB time=00:00:06.76 bitrate=2759.2kbits/s
frame=  301 fps= 40 q=0.0 size=    2375kB time=00:00:07.26 bitrate=2677.6kbits/s
frame=  321 fps= 40 q=0.0 size=    2471kB time=00:00:07.76 bitrate=2606.8kbits/s
frame=  341 fps= 40 q=0.0 size=    2567kB time=00:00:08.26 bitrate=2543.9kbits/s
frame=  361 fps= 40 q=0.0 size=    2663kB time=00:00:08.76 bitrate=2488.5kbits/s
frame=  381 fps= 40 q=0.0 size=    2759kB time=00:00:09.28 bitrate=2434.9kbits/s
frame=  397 fps= 40 q=-1.0 Lsize=    2913kB time=00:00:10.00 bitrate=2386.5kbits/s    
video:2910kB audio:0kB global headers:0kB muxing overhead 0.114339%
[libx264 @ 0x1754860] frame I:2     Avg QP: 0.00  size:337367
[libx264 @ 0x1754860] frame P:395   Avg QP: 0.00  size:  5834
[libx264 @ 0x1754860] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0x1754860] mb P  I16..4: 53.5%  0.0%  0.0%  P16..4:  0.1%  0.0%  0.0%  0.0%  0.0%    skip:46.4%
[libx264 @ 0x1754860] coded y,uvDC,uvAC intra: 0.5% 0.2% 0.2% inter: 0.1% 0.0% 0.0%
[libx264 @ 0x1754860] i16 v,h,dc,p: 100%  0%  0%  0%
[libx264 @ 0x1754860] i8c dc,h,v,p: 91%  1%  8%  0%
[libx264 @ 0x1754860] kb/s:2383.36

```
I'd be interested in seeing results from more users.

---

### Post by Max Jerry Horowitz on 2012-01-30
I made two tests on my wife's laptop: 
```
$ ffmpeg -f x11grab -r 60 -s [COLOR="Red"]1024x768[/COLOR] -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 10 -y output.mkv
ffmpeg version git-2012-01-30-2ab5fea Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 30 2012 20:34:35 with gcc 4.5.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-libvpx
  libavutil      51. 35.101 / 51. 35.101
  libavcodec     54.  0.102 / 54.  0.102
  libavformat    54.  0.100 / 54.  0.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 60.100 /  2. 60.100
  libswscale      2.  1.100 /  2fps= 35.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[x11grab @ 0x18c1620] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0x18c1620] shared memory extension found
[x11grab @ 0x18c1620] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1327952308.947459, bitrate: 1509949 kb/s
    Stream #0:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1024x768, 1509949 kb/s, 60 tbr, 1000k tbn, 60 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x18d7740] w:1024 h:768 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x18d5800] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x18d60c0] w:1024 h:768 fmt:bgra -> w:1024 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x18d4600] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x18d4600] profile High 4:4:4 Predictive, level 3.2, 4:2:0 8-bit
[libx264 @ 0x18d4600] 64 - core 120 r2146 bcd41db - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf54.0.100
    Stream #0:0: Video: h264, yuv420p, 1024x768, q=-1--1, 1k tbn, 60 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> libx264)
Press [q] to stop, [?] for help
frame=  354 [COLOR="Red"]fps= 35[/COLOR] q=-1.0 Lsize=    1519kB time=00:00:10.00 bitrate=1244.5kbits/s    
video:1516kB audio:0kB global headers:0kB muxing overhead 0.198902%
[libx264 @ 0x18d4600] frame I:2     Avg QP: 0.00  size:204444
[libx264 @ 0x18d4600] frame P:352   Avg QP: 0.00  size:  3247
[libx264 @ 0x18d4600] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0x18d4600] mb P  I16..4: 44.9%  0.0%  0.0%  P16..4:  0.0%  0.0%  0.0%  0.0%  0.0%    skip:55.0%
[libx264 @ 0x18d4600] coded y,uvDC,uvAC intra: 0.8% 6.2% 6.2% inter: 0.0% 0.0% 0.0%
[libx264 @ 0x18d4600] i16 v,h,dc,p: 100%  0%  0%  0%
[libx264 @ 0x18d4600] i8c dc,h,v,p: 89%  3%  8%  0%
[libx264 @ 0x18d4600] kb/s:1239.52
```

```
$ ffmpeg -f x11grab -r 60 -s [COLOR="Red"]1022x768[/COLOR] -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 10 -y output.mkv
ffmpeg version git-2012-01-30-2ab5fea Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 30 2012 20:34:35 with gcc 4.5.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-libvpx
  libavutil      51. 35.101 / 51. 35.101
  libavcodec     54.  0.102 / 54.  0.102
  libavformat    54.  0.100 / 54.  0.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 60.100 /  2. 60.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[x11grab @ 0x2aa2620] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1022 height: 768
[x11grab @ 0x2aa2620] shared memory extension found
[x11grab @ 0x2aa2620] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1327952327.890540, bitrate: 1507000 kb/s
    Stream #0:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1022x768, 1507000 kb/s, 60 tbr, 1000k tbn, 60 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x2ab8740] w:1022 h:768 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x2ab6800] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x2ab70c0] w:1022 h:768 fmt:bgra -> w:1022 h:768 fmt:yuv420p flags:0x4reads=6
[libx264 @ 0x2ab5600] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x2ab5600] profile High 4:4:4 Predictive, level 3.2, 4:2:0 8-bit
[libx264 @ 0x2ab5600] 64 - core 120 r2146 bcd41db - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 thfps= 14reads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf54.0.100
    Stream #0:0: Video: h264, yuv420p, 1022x768, q=-1--1, 1k tbn, 60 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> libx264)
Press [q] to stop, [?] for help
frame=  139 [COLOR="Red"]fps= 14[/COLOR] q=-1.0 Lsize=     901kB time=00:00:09.95 bitrate= 741.5kbits/s    
video:899kB audio:0kB global headers:0kB muxing overhead 0.168352%
[libx264 @ 0x2ab5600] frame I:1     Avg QP: 0.00  size:239345
[libx264 @ 0x2ab5600] frame P:138   Avg QP: 0.00  size:  4933
[libx264 @ 0x2ab5600] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0x2ab5600] mb P  I16..4: 45.2%  0.0%  0.0%  P16..4:  0.1%  0.0%  0.0%  0.0%  0.0%    skip:54.7%
[libx264 @ 0x2ab5600] coded y,uvDC,uvAC intra: 1.5% 6.8% 6.8% inter: 0.1% 0.1% 0.1%
[libx264 @ 0x2ab5600] i16 v,h,dc,p: 99%  1%  0%  0%
[libx264 @ 0x2ab5600] i8c dc,h,v,p: 88%  3%  8%  0%
[libx264 @ 0x2ab5600] kb/s:736.12
```
It is the same behavior as on my laptop. Incidentally, the frame-rate in this test seems to be independent from the height of the captured area, only the width has to be divisible by 16. And it doesn't matter whether I am filming an animation or not.
Do you think, that it depends on the graphics card, whether I have to follow the "divisible by 16"-rule? Both of the tested laptops are using an Intel-HD graphics card. Or, there is no rule, and I simply made a mistake?

---

### Post by SeanIM on 2012-02-09
Seems like a lot of tutorials are out there, and I've tried almost everyone of them with no luck.

What are the chances of someone building a bit of code/app just to handle this and let us just pay for it.

I shelled out around 300 bucks for Camtasia for my windows machine and would be happy to pay a similar price if one was available for Ubuntu.

Whew, this is the only thing holding me up from going full Ubuntu.

---

### Post by FakeOutdoorsman on 2012-02-09
> **SeanIM said:**
> Seems like a lot of tutorials are out there, and I've tried almost everyone of them with no luck.
Did you try this one? If you did, what is wrong with it?

> **SeanIM said:**
> What are the chances of someone building a bit of code/app just to handle this and let us just pay for it.
You can always try gtk-recordMyDesktop.

---

### Post by dannyboy79 on 2012-02-10
> **FakeOutdoorsman said:**
> Did you try this one? If you did, what is wrong with it?


You can always try gtk-recordMyDesktop.i use this script and it works fine on my computer. 

[http://pastebin.com/FUVS1H0V]("http://pastebin.com/FUVS1H0V")

---

### Post by IanSWilliams on 2012-02-24
This has been very helpful, thanks a lot.

---

### Post by piotao on 2012-02-26
I said this in another thread on this forum, but I feel obbligated to crosspost it here, because I think the author definitely deserves this. So here's my answer and thanksgiving.

---

Man, dear... author of the first post in this thread.

I, hereby, admit, that your work is greatly appreciated, to unbelivelable extent. Your work and information given in this post saves me.

I worked hard on screencasting using a number of diffrent apps, like recordmydesktop, istanbul, winff, wink, kazam and vlc. Only recordmydesktop gave me some results, but again, youtube stopped processing them. So I was stuck. I struggled for half a month, with no luck, being constantly more stressed and pissed off.

After reading your post, I compiled and installed all ffmpeg related software and they were working. Then I started to record my screen and this was working too. Finally I converted them into mkv format and they worked brilliantly! Also, youtube uploaded them with no problems, so now I'm so happy and relaxed because of you! YOU!

So I would like to say big THANK YOU and with this let me express my love to the open source community and all *unix related world!

You give me outstanding help and thank's to you I've do awesome job. LOVE YOU! 

I wish all of you the best!

---

### Post by wilsonmak on 2012-03-26
Hi all,

I try to have a screenshot on my desktop that has a video playback.  But it just shows a black/blank screen on the video portion.  All screenshots of others stuffs on my desktop are fine.  

Command:
ffmpeg -f x11grab -r 25 -s 1920x1080 -i:0.0 -vcodec libx264 output.avi

P.S.  
1) I use gnome-mplayer with VDPAU enabled.
2) If I use VLC without hardware acceleration(very poor video quality), I can capture the video playback with ffmpeg 

Is it because of the hardware acceleration enabled by VDPAU?  
And how to fix that?

Many thanks,
Wilson

---

### Post by trondhuso on 2012-04-14
Honestly though. Although using the commandline / shell to create a screen capture / screencast, it shouldn't have to be like this in 2012. 

Recordmydesktop (RMD) should have been upgraded so that it really does what it is supposed.
Same goes with Kazam and any other screencast software.

Maybe if we came up with a list of what features are missing or are not good enough, and then someone else came forward and did some coding, maybe the above mentioned software would reach 1.0 at least...

on my 10.04 the version of RMD is 0.3.8.

Trond

---

### Post by jasondean on 2012-04-25
> **trondhuso said:**
> Honestly though. Although using the commandline / shell to create a screen capture / screencast, it shouldn't have to be like this in 2012. 

Recordmydesktop (RMD) should have been upgraded so that it really does what it is supposed.
Same goes with Kazam and any other screencast software.

Maybe if we came up with a list of what features are missing or are not good enough, and then someone else came forward and did some coding, maybe the above mentioned software would reach 1.0 at least...

on my 10.04 the version of RMD is 0.3.8.

Trond

The unstable branch of Kazam works really well it but it's only for Oneiric and Precise 


[IMG]http://img7.imagebanana.com/img/cwr4joyp/KazamScreencaster_001.png[/IMG]

---

### Post by jwiggs on 2012-05-18
First, kudos to the original poster; this howto has proven to be an absolute Godsend.  The closest I've been able to get to a working setup previously was with Kazam under 10.04.  It worked for a while, but at some point for reasons completely unknown, recording a desktop with a webcam display inset stopped working (the webcam window displayed cam footage while recording the desktop, but when you viewed the resulting capture file, the contents of the webcam window were just black).

I'm now successfully using this under 12.04, with one annoying glitch: the sound seems to cut out about 5-6 seconds before the end of the video.  The sound quality is good, and when I capture the desktop with an inset webcam window, the sound is in sync with the webcam, but in the final capture video, the sound cuts out before the video ends.  I've had to get into the habit of waiting 5 seconds before hitting Ctrl-C to stop the desktop capture, then chop off those last 5 seconds of video when I transcode the .mkv file over to a final MP4 or FLV file.

Does anyone have any idea what might be causing this behavior?  It's almost as if pulse is buffering some audio, and when you kill the capture, that audio is getting dumped on the floor instead of muxed in with the video stream.

Any suggestions on how to prevent this?

thanks,
Jim

PS I wrote some simple PHP wrapper scripts to hide some of the complexity of the avconv command-line, and to provide a nice little "countdown" before the capture starts.  If anyone is interested, I'd be happy to post them here.

---

### Post by SeanIM on 2012-05-24
Great thread...I'm still struggling with this issue but before I try again I am going to upgrade to the latest distro.

I wish Camtasia would port a linux version. :/  I'd soooo pay for that.

---

### Post by Meelis on 2012-06-19
Hi

Is there a GUI based program to screencast Blender and desktop with Lagarith Lossless Video Codec or similar that does super fast scene change detection and compresses unchanged blocks of frames together and saves disc space?

---

### Post by cannon_dt on 2012-09-04
Has anyone figured out how to record both the on screen audio and the mic in? Ffmpeg and pulse work fine to capture on screen sound but what about voice over from a microphone?

---

### Post by FakeOutdoorsman on 2012-09-04
I've never tried it myself. Maybe you can simply add another audio input; though you'll end up with two audio streams. Other than the official documentation [Capturing audio with FFmpeg and ALSA](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSA) might give some additional clues.

---

### Post by nehaljwani on 2012-10-06
To view the method mentioned above in action, visit:

[https://www.youtube.com/watch?v=B-ry-f3Mpx4](https://www.youtube.com/watch?v=B-ry-f3Mpx4)

---

### Post by nehaljwani on 2012-10-09
Visit: [http://www.commandlinefu.com/commands/matching/ffmpeg-x11grab/ZmZtcGVnIC14MTFncmFi/sort-by-votes](http://www.commandlinefu.com/commands/matching/ffmpeg-x11grab/ZmZtcGVnIC14MTFncmFi/sort-by-votes)

---

### Post by FakeOutdoorsman on 2012-10-09
> **nehaljwani said:**
> To view the method mentioned above in action, visit:

[https://www.youtube.com/watch?v=B-ry-f3Mpx4](https://www.youtube.com/watch?v=B-ry-f3Mpx4)
Do not use the *-sameq* option when using x11grab. See [sameq does not mean "same quality"](http://superuser.com/a/478550/110524).

---

### Post by rulet on 2012-10-11
So, how to do screencast with ffmpeg with simultaneous capturing internal(which goes to speakers) and with external(which recorded by microphone) sound?

---

### Post by dannyboy79 on 2012-12-11
> **rulet said:**
> So, how to do screencast with ffmpeg with simultaneous capturing internal(which goes to speakers) and with external(which recorded by microphone) sound?
using pavucontrol and all streams. you can create loopbacks so it records both internal audio and mic using pactl, see here for a hint: [http://ubuntuforums.org/showthread.php?t=2084420&highlight=twitch](http://ubuntuforums.org/showthread.php?t=2084420&highlight=twitch)

---

### Post by dannyboy79 on 2012-12-21
when trying this
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x720 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
```
i get this
```
[matroska @ 0x1668bc0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1
av_interleaved_write_frame(): Invalid argument
```
What gives?

---

### Post by FakeOutdoorsman on 2012-12-21
I don't have a "real" solution, but you can output the audio separately and then mux it afterwards. Untested example:

```
ffmpeg -f x11grab -r 30 -s 1280x720 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 output-v.mkv -f alsa -ac 2 -i pulse -acodec pcm_s16le output-a.wav
ffmpeg -i output-v.mkv -i output-a.wav -c copy output.mkv

```

Note that "-threads 0" is default so you don't need to include it.

---

### Post by VinisLentoje on 2013-01-26
Hello!

I've got a bit of a problem with recording - my video & audio get increasingly desynchronized. The longer the video, the longer the gap. For example, in one of the videos I recorded, a couple of minutes in, the video is behind audio by a couple of seconds, @ 1 hour mark - almost a minute, at 2 hour mark - a bit more than two minutes.

I run the capture with
```
./ffmpeg -f alsa -ac 2 -i pulse -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x720 -i +foo,bar -filter_complex amix=inputs=2:duration=first:dropout_transition=3 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -x264opts crf=0 -threads 0 /foo/bar.mkv
```

I tried running it with -vsync, with aresample=async=1000 audio filter, and tried with both at the same time. Tried recording both audio stream without mixing them on the fly. Tried recording only one audio stream. I still get the same going out of sync problem. Could anyone help me? 'Cause I am out of ideas.

---

### Post by marvalis on 2013-02-13
I seem to have the same problem. Video and audio got out of sync too on my ~40 min video.

---

### Post by dannyboy79 on 2013-02-13
i would suggest turning down your frames per second. give that a try

---

### Post by VinisLentoje on 2013-02-13
> **dannyboy79 said:**
> i would suggest turning down your frames per second. give that a try

I tried that. When I lower the framerate, the desynchronization actually becomes a bit *higher*.
+ my computer is powerful enough to handle such framerates easily. Heck, I can even even run it with "veryfast" preset and still have a lot of CPU headroom. I actually get a *less* desynchronization if I run it with "veryfast" preset along with using a bit more compression on-the-fly.

Yes, I know, that makes no sense.
I would really like to figure out what exactly goes wrong. As I not only want to properly record videos, but it also "activated my curiosity". Weird things are interesting ;)

---

### Post by coldraven on 2013-02-14
I followed the instructions on the ffmpeg site for ubuntu (precise) and successfully compiled all the tools.
I used ffmpeg to make a screencast (mkv) but when I try to convert it to webm I get an error.

```
ffmpeg version git-2013-02-13-15e7533 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 13 2013 19:59:40 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 17.101 / 52. 17.101
  libavcodec     54. 91.103 / 54. 91.103
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 37.101 /  3. 37.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100

``````
coldraven@happy:~$ ffmpeg -i our-final-product.mkv -vcodec libvpx -acodec libvorbis test.webm
ffmpeg version git-2013-02-13-15e7533 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 13 2013 19:59:40 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 17.101 / 52. 17.101
  libavcodec     54. 91.103 / 54. 91.103
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 37.101 /  3. 37.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[matroska,webm @ 0x2b74020] max_analyze_duration 5000000 reached at 5017000 microseconds
[matroska,webm @ 0x2b74020] Could not find codec parameters for stream 0 (Video: h264, 680x430): unspecified pixel format
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, matroska,webm, from 'our-final-product.mkv':
  Metadata:
    ENCODER         : Lavf54.63.100
  Duration: 00:00:40.67, start: 0.000000, bitrate: 163 kb/s
    Stream #0:0: Video: h264, 680x430, SAR 1:1 DAR 68:43, 25 fps, 25 tbr, 1k tbn, 2k tbc (default)
    Stream #0:1: Audio: vorbis, 48000 Hz, stereo, fltp (default)
File 'test.webm' already exists. Overwrite ? [y/N] y
[COLOR=Red]Unable to parse option value "-1" as pixel format[/COLOR]
Error opening filters!
```Any ideas?

---

### Post by FakeOutdoorsman on 2013-02-14
I can't duplicate the issue. Can you provide the input?

---

### Post by coldraven on 2013-02-15
> **FakeOutdoorsman said:**
> I can't duplicate the issue. Can you provide the input?

Please excuse the bad quality audio, that was going to be another question.
This is Kubuntu 12.04 and the sound mixer  Kmix crashes on loading.
I want to go back to Ubuntu but my laptop video card has problems with Unity.

The source file is here:
[http://ubuntuone.com/2ESC5TMnzQi95UIuFP4y8p](http://ubuntuone.com/2ESC5TMnzQi95UIuFP4y8p)


Thanks for looking :)

---

### Post by FakeOutdoorsman on 2013-02-15
> **coldraven said:**
> 
[matroska,webm @ 0x2b74020] max_analyze_duration 5000000 reached at 5017000 microseconds
[matroska,webm @ 0x2b74020] Could not find codec parameters for stream 0 (Video: h264, 680x430): unspecified pixel format
Consider increasing the value for the 'analyzeduration' and 'probesize' options


This is the important message, although it understandably might be confusing given the un-user-friendly "Unable to parse option value "-1" as pixel format" error.

So you need to increase the -analyzeduration value (default is 5000000). Generally you don't have to do this, and I'm not sure what is going on with your file. How did you make the file/what was your encoding command? Also, since your input already contains Vorbis audio you probably don't need to re-encode it:

```
ffmpeg -analyzeduration 6000000 -i our-final-product.mkv -vcodec libvpx -acodec copy test.webm
```

I wish I had some more advice to give about using libvpx, because the default settings are probably poor, but that's an encoder I have no experience with.

> **coldraven said:**
> Please excuse the bad quality audio, that was going to be another question.
This is Kubuntu 12.04 and the sound mixer  Kmix crashes on loading.
Sorry, I've never used Kmix. I generally just use alsamixer. Some info: [Capturing audio with FFmpeg and ALSA](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSA).

> **coldraven said:**
> I want to go back to Ubuntu but my laptop video card has problems with Unity.
Everything has problems with Unity.

---

### Post by coldraven on 2013-02-15
> but that's an encoder I have no experience with.
You are lucky :) I have no experience with any of this stuff!

I just wiped my drive and installed Ubuntu 12.10 so I may not try your suggestions for a day or so.
 I had previously tried alsamixer but the microphone level controls would jump from 53% to 100%. That's why the sound is distorting.
Do you think that the ffmpeg deb files I compiled for Precise will work in Quantal or would it be better to compile them again?

In case you are wondering, the videos are for a friends cattle program as tutorials.
He tried using Windows programs and the result was low res, and large file size.

The good news is that 12.10 and Unity are behaving nicely on my laptop :p
Thanks for your time.

---

### Post by FakeOutdoorsman on 2013-02-15
> **coldraven said:**
> Do you think that the ffmpeg deb files I compiled for Precise will work in Quantal or would it be better to compile them again?

You should re-compile. Also, the so-called "ffmpeg" version from the repo is quite buggy, so there's another reason to compile.

---

### Post by coldraven on 2013-02-15
> **FakeOutdoorsman said:**
> You should re-compile. Also, the so-called "ffmpeg" version from the repo is quite buggy, so there's another reason to compile.
Thanks, I had a feeling that would be the answer.
I just realised that I had not replied with my original command, I copied it from the beginning of this thread and added the crop dimensions.
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s 680x430 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 2 output.mkv 
```

What format would you recommend for a cross platform web video?

---

### Post by FakeOutdoorsman on 2013-02-15
> **coldraven said:**
> ```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s 680x430 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 2 output.mkv 
```

This doesn't look like what you used to make the troublesome sample because this has pcm_s16le audio and the sample contained Vorbis audio.

See "How do I get the exact size and coordinates of a specific window I want to capture?" in the tutorial at the beginning of this thread on how to capture just the program window and not extra desktop stuff.

> **coldraven said:**
> What format would you recommend for a cross platform web video?

Other than being lazy and using YouTube or Vimeo? Probably something like the free [videojs](http://videojs.com/) or [mediaelementjs](http://mediaelementjs.com/) with both a H.264 video with AAC audio in mp4 container, and VP8 video and Vorbis audio in webm container. Don't waste your time with Theora video and Vorbis audio in ogg for that shrinking 5% browser market share.

---

### Post by coldraven on 2013-02-16
> Other than being lazy and using YouTube or Vimeo? Probably something like the free [videojs]("http://videojs.com/") or [mediaelementjs]("http://mediaelementjs.com/")  with both a H.264 video with AAC audio in mp4 container, and VP8 video  and Vorbis audio in webm container. Don't waste your time with Theora  video and Vorbis audio in ogg for that shrinking 5% browser market  share.Thanks, those links look like what I need.
I will re-compile ffmpeg later today and do some more research and experimenting.

Just one quick question, if I want medium quality mono sound where do I alter the argument?
Is it ?
alsa -ac 1

I cannot seem to find the correct piece of documentation and all examples are for high quality stereo.
I'm presuming that it is better to capture directly into the format I want rather than transcoding afterwards.
Cheers!

---

### Post by FakeOutdoorsman on 2013-02-16
> **coldraven said:**
> if I want medium quality mono sound where do I alter the argument?

As an output option (anywhere after "-i input" and before "output.foo") you can add "-ac 1". If you apply as an input option you are telling the decoder that the input is i channel, even if it is stereo, which probably isn't something you want to do (or maybe ffmpeg will ignore it).

Vorbis CBR:
```
ffmpeg -i input -c:v libvorbis -ac 1 -b:a 32k -c:v libvpx ... output.webm
```

Vorbis VBR:
```
ffmpeg -i input -c:v libvorbis -ac 1 -q:a 3 -c:v libvpx ... output.webm
```

See [Recommended Vorbis Encoder Settings](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis#Recommended_Encoder_Settings) for an idea of what "-q:a" value to use.

I'd like to figure out how to use libvpx and then write a proper FFmpeg guide for it (and HTML5 video with ffmpeg)... but hopefully someone will beat me to it.

See the [FFmpeg and AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide) for full details and examples for AAC encoding, and [FFmpeg and AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for encoding to H.264 video.

> **coldraven said:**
> I'm presuming that it is better to capture directly into the format I want rather than transcoding afterwards.

The main example in this guide attempts to capture as fast as possible without having to work on compressing things very much so you can achieve your desired framerate (assuming your CPU is the bottleneck). It then suggests re-encoding this temporary, large, lossless output to your desired final output(s). This may also be the best choice for you if you're going to make a mp4 and webm from the same source.

---

### Post by coldraven on 2013-02-17
> The main example in this guide attempts to capture as fast as possible  without having to work on compressing things very much so you can  achieve your desired framerate (assuming your CPU is the bottleneck). It  then suggests re-encoding this temporary, large, lossless output to  your desired final output(s). This may also be the best choice for you  if you're going to make a mp4 and webm from the same source.

Aha! Thanks for that. Progress has been delayed by a visit to the pub :)
You will probably hear from me later after I have become totally confused, I need to get my head around all these switches and codecs.
<goes off to wiki page>

---

### Post by moonliter on 2013-02-19
Hi after reading this tutorial I tried to find gui ffmpeg and found amazing softvare  recently released. It is Screencastor. There is also video explaining by some guy how to use it

```
http://www.youtube.com/watch?v=UQ43XnHM8gI
```

I have found official link for screencastor 

```
https://launchpad.net/~hizo/+archive/screencastor
```

Happy casting!!

---

### Post by VinisLentoje on 2013-02-25
Hello again!

So, any ideas on my (and marvalis', apparently) desync problem?

> **dannyboy79 said:**
> i would suggest turning down your frames per second. give that a try

As I said - this does not help at all - even if I record in 960x540 @ 15 fps, it desyncs the same way as when I record, for example, in 1920x1080 @ 40 fps. I can see my CPU is mostly idle when recording in low res && low fps, and my HDD is accessed rather rarely. When recording in 1920x1080@40, my CPU still has a lot of headroom. And I can also see my HDD can take it all with no problems. Thus, it's definitely not a performance problem.

MEANWHILE!!! I tried "-tune zerolatency" option today. It eliminates desycing almost completely! But - it is not usable, unfortunately. Sooner or later, I start seeing things like this spammed in ffmpeg's output:
```
[matroska @ 0x2b8e420] st:0 PTS: 922148 DTS: 922148 < 922246 invalid, clipping
```
And when that starts, I get severe audio corruption - all the sound that is recorded after this starts is virtually unusable (parts full of "clicks", periods of silence, parts with the audio "jumping over" by a couple of secs, and so on).

Any ideas? Please - I REALLY don't want to be forced to use Windoze just to record things (where I get no such issues whatsoever) :frown:

---

### Post by gr8 on 2013-03-09
Same problem here. I am doing one hour screencasts. When I start the screencast the audio is in sync. As time progresses the audio/video become more and more out of sync. I suspect all ffmpeg users have this problem, they just don't know it. If you do a five minute screencast you won't see the de-sync issues. After one hour of video it becomes apparent.

---

### Post by Jacob Mischka on 2013-03-17
Recording audio seems to be broken with avconv. The problem is that it records audio at a pretty significantly faster rate than video, so in the recording the audio rate is slower than the video rate, causing them to be out of sync, and even causing the audio to have a lower tone. You can even try recording just audio to a .wav and recording just video to an .mp4 at the exact same time in separate windows, and you'll notice that the resulting audio file is significantly longer (9-10% longer in my quick, inaccurate tests). Even the timestamps in the avconv output for audio recording reports that the recording time is increasing faster than realtime. I am currently looking into possible solutions. Are all of the rest of you also using the avconv version from libav-tools? It may be a bug that has been fixed since then. I'll try compiling the most recent version and see if that fixes the issue. 

It's a real shame too, because video recording works so perfectly.

Edit:[COLOR=#000000] VenisLentoje, I just realized you said you were using ffmpeg. Can you tell me what version you're using please? I'm using the avconv from libav-tools, version 8.5. I'm really interested as to whether this is just a setting issue, or if the way that they both record audio is just garbage. [/COLOR]

---

### Post by FakeOutdoorsman on 2013-03-17
This guide is designed for real ffmpeg, not avconv or the fake, bizarro "ffmpeg" from the repositroy. From what I've seen avconv is fairly buggy, but you can [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) and see if it makes a difference.

---

### Post by Jacob Mischka on 2013-03-17
The two other people that complained about the same issue were using your precious ffmpeg, so unless one of them says their issue is different from mine, that means nothing in this case.

But I'll try compiling ffmpeg and seeing if that fixes the issue, which I rather doubt. If it does this will be the first time I've seen the two differ at all in actual usage.

Edit: Done, same thing happens. Audio is stretched, therefore lower toned, and becomes increasingly out of sync as time goes on. It's either a setting issue, a hardware issue (which I doubt), or simply the way they both capture audio is bad.

Edit: I realize my mention of stretched audio brings async to mind (or whatever equivalent option is in ffmpeg), but using it doesn't help as someone else already mentioned.

Edit again: I have also used multiple sound cards to no effect, and captured directly from microphone input and output.monitor sources. So it's not our cards, and it's not pulse loopbacks being bad. And it even happens when recording only audio .wavs, so it isn't our cpu not being able to handing the encoding. And of course audio capture with other applications is normal and works as intended.

---

### Post by FakeOutdoorsman on 2013-03-18
> **Jacob Mischka said:**
> The two other people that complained about the same issue were using your precious ffmpeg, so unless one of them says their issue is different from mine, that means nothing in this case.
My preciousss...

> **Jacob Mischka said:**
> But I'll try compiling ffmpeg and seeing if that fixes the issue, which I rather doubt. If it does this will be the first time I've seen the two differ at all in actual usage.
I seen the opposite on many occasions. You seem annoyed that I've asked you to try a recent build. The reason for this test is that FFmpeg development is very active and this is **always** the first step to determine if you are experiencing an already fixed bug. Otherwise you are wasting your time and the time of anyone attempting to help you.

Now that you got that step out of the way I recommend you ask for assistance at the [ffmpeg-user](http://ffmpeg.org/contact.html) mailing list; developers and other usually knowledgeable users try to answer most questions. Since they are all volunteers, and since there can be many questions per day, asking a well thought out and detailed question will get a better chance of an answer. This means that at a minimum you need to: use a recent ffmpeg build, include your full ffmpeg command, and include your complete ffmpeg console output (or at least the first 50 and last 50 lines). Responses may seem terse, but this is just the effect of trying to be efficient due to a large questions to answering volunteers ratio.

If you are convinced this is a bug then consider [reporting](https://ffmpeg.org/bugreports.html) it.

---

### Post by Jacob Mischka on 2013-03-18
Not really that you asked me to try a newer build, just that you seemed to cast it off as a solely avconv issue when they are nearly identical and when two people already reported the same issue. I guess I'll submit a bug report. I would have anyway, I was just hoping someone around here would have heard of the issue. Especially since the sole purpose of this thread is about capturing audio along with video. I find it difficult to believe others are having flawless lossless audio recording with these tools, as many people have issues with it. Googling returns nothing, since so many people have different problems with avconv/ffmpeg capturing audio.

I will try using jack or selecting a specific card with alsa so to bypass pulse and see if that changes anything and report back.

---

### Post by Jacob Mischka on 2013-03-19
Okay, well, I seem to have fixed it for now. Though I'm not entirely sure what did it. I setup a loopback with snd-aloop instead of using a null sink in pulse. I then tried to record from that via "-f alsa -i hw:3,1". That worked, and the audio was being recorded at the correct rate, but it still wasn't good. On the old avconv from the ubuntu repo, I received a single "Alsa buffer xrun" error at the beginning of the recording, and from that point onward my audio was exactly two seconds *ahead* of my audio. On both the ffmpeg and avconv compiled from source, I had many more of those errors. I then added several libraries via apt-get and the ubuntu repository: libxvidcore-dev, libx264-dev, x264, libffms2-2. I know all of you are likely using versions of those compiled from source, as that is what the ffmpeg guide posted here said to do. After a while I tried just using "-f alsa -i pulse" again but with the new alsa loopback, and that worked better. I thought during my 1.5 hour recording that I was using the avconv version that I compiled, but I was actually using the old version from the repo. Both of my compiled versions seem to not run very well, but that's likely because I'm not using the most recent versions of some libraries. I have no idea.

My steps to get this working were (without the braces):
```

$sudo modprobe snd-aloop

```
I think pulseaudio should recognize the new "card" immediately, though you may need to --kill and --start it.
```

$pactl load-module module-combine-sink slaves=[my actual soundcard's sink name],[the loopback's sink name]
$pactl load-module module-loopback sink=[loopback sink name] source=[pulse's source name for my microphone]

```

I then used pavucontrol to mix the audio streams. Any application you want to capture audio from, you tell it to use the combined sink. Anything you don't want to be captured you just send straight to your own sound card. 

I then used the following command to actually record:
```

$avconv -f x11grab -r 30 -s hd1080 -i :0.0 -f alsa -i pulse -s hd720 -acodec libmp3lame -b 1024k -vcodec libx264 -ar 44100 /tmp/cake.mp4

```

In theory it should work as well to use "-f pulse -i [loopback's pulse name]".

I'm not really entirely sure if it was the alsa loopback, or the libraries I added/updated, but it seems to be holding for now, and pulse is too temperamental for me to try prodding at it until it breaks again. 

Edit: I don't believe it was the libraries, as I was previously having issues even recording .wavs, and none of those video codec updates should have affected that at all.

I realize what I did was extremely sloppy, but it seems to work for me, so I'm just posting it here. I also realize what I did may not actually help anyone since you're all using ffmpeg, but it may, and the commands are the exact same aside from replacing avconv with ffmpeg. 

Tomorrow I'll try testing to see what exactly I did helped solve the issue.

---

### Post by wachin on 2013-06-06
Thanks ron999, working fine for me on UbuntuStudio 13.04, great thanks, your solution my problem.

This is that working now:

ffmpeg -f alsa -i pulse -f x11grab -r 25 -s 1600x900 -i :0.0 -acodec flac -vcodec libx264 -vpre lossless_ultrafast -threads 0 out01.mkv

(Mi Laptop is Dell Inspiron 1750 with a monitor of 1600x900)
Good Job

---

### Post by Akovia on 2013-07-13
I am having trouble with the playback of my files. They work fine on my computer using smplayer, but others that view them are having troubles. 
After investigating some, I noticed that if I import the videos into avidemux, the playback time is always much shorter than in smplayer. I'm assuming this is an FPS issue?
I was using an older version of ffmpeg, but I just updated it and have also tried the "Screencastor" app mentioned in this thread, but the results seem to be the same. I've lowered my framerate to 25 but I didn't notice a difference.
This is the command line:```
ffmpeg -ss "00:00:06" -f "x11grab" -r:v "25" -s:v "1680x1026" -i ":0+0,0" -codec:v "libx264" -crf "20" -me_method "epzs" -g "250" -subq "6" -keyint_min "25" -trellis "1" -bf "16" -threads "0" -b:v "700k" -bt "4000k" -r:v "20" "/home/akovia/Videos/Screencasts/Screencastor_1373735425.mkv"
```
Any ideas how I could fix this, or re-encode the video afterwards to to compensate for the framerate?
Thanks.

---

### Post by FakeOutdoorsman on 2013-07-13
Why not use the commands and method as shown in this HOWTO?

---

### Post by Akovia on 2013-07-13
> **FakeOutdoorsman said:**
> Why not use the commands and method as shown in this HOWTO?
That's what I've been using, I only tried screencastor since it wasn't working properly anyway. I thought that screencastor was just an ffmpeg command builder anyway, not adding anything of it's own. Am I wrong?

---

### Post by Akovia on 2013-07-13
I'm happy to try anything to get some help here. I went ahead and ran the simplest command from page 1 with no audio.
```
ffmpeg -f x11grab -r 30 -s 1680x1026 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
```
The result is the same.
In smplayer, the time is 01:09.000
in avidemux I get 00:51.833

---

### Post by FakeOutdoorsman on 2013-07-16
Using this command in a recently compiled ffmpeg to create a 60 second output:
```
ffmpeg -f x11grab -r 30 -s 1680x1026 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 60 output.mkv
```

I can not duplicate this issue using Avidemux 2.5.6 (Arch Linux) or 2.5.4 (Ubuntu 13.04). ffmpeg and SMPlayer 0.8.3 in Ubuntu also show 00:01:00.

When using the fake "ffmpeg" from the repository Avidemux 2.5.4 claims the file is 59.833 seconds in duration, but both ffmpeg versions and SMPlayer still show 00:01:00.

So maybe you can try [compiling ffmpeg](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) instead of using the trash from the repository.

---

### Post by Akovia on 2013-07-16
> **FakeOutdoorsman said:**
> Using this command in a recently compiled ffmpeg to create a 60 second output:
```
ffmpeg -f x11grab -r 30 -s 1680x1026 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 60 output.mkv
```

I can not duplicate this issue using Avidemux 2.5.6 (Arch Linux) or 2.5.4 (Ubuntu 13.04). ffmpeg and SMPlayer 0.8.3 in Ubuntu also show 00:01:00.

When using the fake "ffmpeg" from the repository Avidemux 2.5.4 claims the file is 59.833 seconds in duration, but both ffmpeg versions and SMPlayer still show 00:01:00.

So maybe you can try [compiling ffmpeg]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide") instead of using the trash from the repository.
Ouch! I wasn't trying to offend anyone. 
In any case, I am very thankful you took the time to test it out with my programs.

I followed your outstanding guide like I did ages ago, but of course this time there were problems and it took me three times to get what I hope is right. First, when I paste the commands into my terminal, for some reason the last command never executes, and I didn't notice the first time around. I had to hit enter after each paste ended and before the next paste. Then I noticed another error when pilling GIT.
```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-OWZOd8/pkcs11
``` Apparently this is a long standing [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177") in xubuntu (among other non gnome desktops).

When I got to the end of the third try, I tried your command to check the version.```
$ ffmpeg 2>&1 | head -n1
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-OWZOd8/pkcs11: No such file or directory

```*sigh*
I then tried with **ffmpeg --version** and got the following.```
ffmpeg --version
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-OWZOd8/pkcs11: No such file or directory
ffmpeg version 0.10.7-6:0.10.7-0jon1~precise Copyright (c) 2000-2013 the FFmpeg developers
  built on Jul 15 2013 21:25:07 with gcc 4.6.3
  configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu --enable-shared --disable-static
  avutil      configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avcodec     configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-aacenc --enable-libvo-amrwbenc
  avformat    configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avdevice    configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avfilter    configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  swscale     configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  swresample  configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  postproc    configuration: --arch=i386 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.7-0jon1~precise' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Missing argument for option '-version'

```Since it did seem to be the right version, I tried another test and unfortunately I still get the same results.

Avidemux 2.5.6 - 00:29.933
SMPlayer0.8.5 - 00:42

I am a moderator over at fanart.tv and am trying to make tutorials. The first few I posted never raised any flags. Then while making a few small tuts for some individuals that needed help, they kept saying they couldn't play them back. (windows users) I directed them to either VLC or MPC-HC for playback and have heard mixed results. I'm not certain if this time discrepancy is to blame or not, but when i was trying to find the root of the problem, this stood out. I do like repositories that auto-update because otherwise I'll forget to keep things updated myself, so I apologize for taking the lazy way out. At this point I'm willing to try anything as I really do need this functionality. I tried all the other programs when I started doing this, but none met my needs like this does.

I hacked together a script until I ran upon a nice one I [found ]("http://crunchbang.org/forums/viewtopic.php?id=22772")and have been using ever since. It's actually a couple of scripts for both audio and non audio captures, but I've only ever used the non audio and the terminate ones tied to some hotkeys. Here it is in case you find anything fishy.```
#!/bin/bash

    # SCREENCAST = LOSSLESS SCREENCAST

    # =============
    # USER SETTINGS
    # =============
    input=$(zenity --text "Name of Video?" --entry)
    OUTPUT="/home/akovia/Videos/Screencasts"
    KEYBOARDSTART="[ Super + F5 ] keys pressed"
    KEYBOARDSTOP="[ Super + F7 ] keys pressed"
    # =============

    # =========
    # VARIABLES
    # =========
    SIZE="1680x1026"
    RATE="30"
    VCODEC="libx264"

    PIXELS="yuv420p"
    PRESET="ultrafast"
    # =========

      # ===========
      # INFORMATION
      # ===========
      
      # ==========================================
      # keyboard bindings for chosen keys [rc.xml]
      # ==========================================
      # <keybind key="A-F1"><action name="Execute"><command>screencast</command></action></keybind>
      # <keybind key="A-F3"><action name="Execute"><command>screencast-stop</command></action></keybind>
      # ==========================================

      # ==============================
      # terminal conversion MKV >> MP4
      # ==============================
      # ffmpeg -i screencast.mkv -c:v libx264 -preset fast -crf 18 -y screencast.mp4
      # ==============================

      # ===============================
      # thunar custom action MKV >> MP4
      # ===============================
      # terminal --title="Screencast MKV Conversion to MP4" --geometry="200x35" --icon="$HOME/.icons/ffmpeg/convert.png" -e " ffmpeg -i %f -c:v libx264 -preset fast -crf 18 -y `basename %f .mkv`.mp4"
      # ===============================

    # ============
    # SCRIPT BELOW
    # ============
    
    # notification - starting
    notify-send -t 6000 "$KEYBOARDSTART : screencast will begin in 6 seconds"
    
    key-mon &
    
    # pause!
    sleep 6
 

    # start screencasting losslessly without audio
    ffmpeg -f x11grab -s $SIZE -r $RATE -i :0.0 -vcodec $VCODEC -preset $PRESET -crf 0 -threads 0 -y "$OUTPUT"/"$input".mkv

    ## screencast-stop ## << script (assigned to keyboard shortcut) silently brings the ffmpeg process to a halt here! >>

    # notification - completion
    notify-send -t 3000  "$KEYBOARDSTOP : Screencast finished   :-)"

    # pause
    sleep 3

    # open thunar to show video
    thunar "$OUTPUT"

```

Thanks again for taking your time to try and reproduce. I understand if you don't want to take it any further, but I'm open to try any suggestions short of a new OS install.
Cheers

---

### Post by tikky2 on 2013-10-19
Is this possible...
Lets say i want to screen capture 2 videos which are on separate monitors. Could i capture both video and sound from these 2 videos at the same time?

---

### Post by FakeOutdoorsman on 2013-10-20
Should be possible. From the [FFmpeg x11grab docs](http://ffmpeg.org/ffmpeg-devices.html#x11grab):

> ```
[hostname]:display_number.screen_number[+x_offset,y_offset]
```

*hostname:display_number.screen_number* specifies the X11 display name of the screen to grab from. hostname can be omitted, and defaults to "localhost". The environment variable DISPLAY contains the default display name.

x_offset and y_offset specify the offsets of the grabbed area with respect to the top-left border of the X11 screen. They default to 0.

Check the X11 documentation (e.g. man X) for more detailed information.

Use the dpyinfo program for getting basic information about the properties of your X11 display (e.g. grep for "name" or "dimensions"). 


From "man x":
```
       displaynumber
               The  phrase  "display" is usually used to refer to a collection
               of monitors that share a common set of input devices (keyboard,
               mouse,  tablet, etc.).  Most workstations tend to only have one
               display.  Larger, multi-user systems, however, frequently  have
               several  displays  so  that  more  than one person can be doing
               graphics work at once.  To avoid confusion, each display  on  a
               machine  is assigned a display number (beginning at 0) when the
               X server for that display is started.  The display number  must
               always be given in a display name.

       screennumber
               Some displays share their input devices among two or more moni&#8208;
               tors.  These may be configured  as  a  single  logical  screen,
               which  allows  windows to move across screens, or as individual
               screens, each with their own set  of  windows.   If  configured
               such  that each monitor has its own set of windows, each screen
               is assigned a screen number (beginning at 0) when the X  server
               for  that  display  is  started.   If  the screen number is not
               given, screen 0 will be used.

```

I only have one screen, but I guess you would try something like:
```
ffmpeg -f x11grab -framerate 25 -video_size 1680x1050 -i :0.0 -f x11grab -framerate 25 -video_size 1680x1050 -i :0.1 -c:v libx264 -crf 0 -preset ultrafast output.mkv
```

I assume this will create two separate video streams (one per screen) into one output file. You didn't mention if you wanted them combined (side-by-side for example) or anything.

---

### Post by artti on 2013-10-31
Tutorial is great! But like user arcmorrison, I also have fps 3. Tips to improve this?

---

### Post by FakeOutdoorsman on 2013-10-31
Please show your ffmpeg command and the complete console output.

---

### Post by dannyboy79 on 2013-11-18
im using avconv not to screencast but to livestream to twitch. I found a script and am attempting to use it but it appears like the video codec min and max bitrate and buffsize are missing, where or how exactly would I edit this script so that my video bitrate has different bitrate settings from the audio which is how this script is currently limited based on my testing

```
INRES="1680x1050"                                            # input resolution
OUTRES="1280x720"                                           # Output resolution
FPS="30"                                                    # target 
FPSQUAL="fast"                                               # one of the many FFMPEG preset on (k)ubuntu found in /usr/share/ffmpeg
# If you have low bandwidth, put the qual preset on 'fast' (upload bandwidth)
# If you have medium bandwitch put it on normal to medium # Write your key in a file named .twitch_key in your home directory

STREAM_KEY=$(cat ~/.twitch_key)  
# This is your streamkey generated by jtv/twitch found at: http://www.justin.tv/broadcast/adv_other

avconv \   
-f x11grab -s $INRES  -r "$FPS" -i :0.0 \   
-f alsa -ac 2 -i pulse  \    
-vcodec libx264 -s $OUTRES -preset $QUAL \   
-acodec libmp3lame -ar 44100 -threads 4 -qscale 3 -b 712000  -bufsize 512k \    
-f flv "rtmp://live.justin.tv/app/$STREAM_KEY" 

```

---

### Post by FakeOutdoorsman on 2013-11-18
This howto is specifically for ffmpeg from FFmpeg.

---

### Post by dannyboy79 on 2013-11-18
i didn't think they were that different, i understand preset names are different and some options are named or abbreviated differently but I just need to know where I would insert the min, max, and buffer for my video bitrate. Any help would be appreciated. and actually this thread is titled "Howto: Proper Screencasting in Linux" and doesn't state its for ffmpeg only.

---

### Post by millerthegorilla on 2013-11-21
I was having problems recording sound with ffmpeg screencast as I don't use the pulseaudio sound server.  I found this page : 

[http://stefan.boxbox.org/2011/09/26/creating-a-screencast-in-linux/](http://stefan.boxbox.org/2011/09/26/creating-a-screencast-in-linux/)

There is a little script that starts ffmep for screenrecording and jack_capture for audio.

When finished, there is also some info about transcoding and interweaving the separate video and audio so that you are left with one file.

The only problem that I now have is that my screen is 1440x900 and even with the ffmpeg parameter video_size set (I have also tried -s) the recorded screen is too short, possibly due to 720p set.

---

### Post by FakeOutdoorsman on 2013-11-21
> **millerthegorilla said:**
> The only problem that I now have is that my screen is 1440x900 and even with the ffmpeg parameter video_size set (I have also tried -s) the recorded screen is too short, possibly due to 720p set.

Please show your actual ffmpeg command and the complete ffmpeg console output.

---

### Post by thesleash on 2013-11-21
this is command I use for decent quality at low bit-rate.

avconv -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -i :0.0 -r 7 -s 680x384 output.mkv

---

### Post by willard2 on 2013-12-13
First of all, i'm not an Ubuntu user. I've used Mandrake/Mandriva since 1997 and i'm currently running Mageia :P

But this guide was really helpful and i wanted to share one problem that i had. I had the issue that the sound was out of sync everytime, and i googled like a maniac. Tried -vsync and -itsoffset. This thread came up several times and i read and tested but could not come up with a solution until i nearly gave up.

I thought to hell with this and deleted the output file. An hour later... Ok, one last try and it worked :)

Apparently when i pressed enter to start recording, ffmpeg asked me if i wanted to overwrite the already existing output.mkv. Ffmpeg had already started recording at this point. The time it took me to press y to overwrite was the offset time in the audio.

Most people try out a few times then do the final recording. Remeber to delete the old, or save to a new file :)

Don't know about everyone else but i'm a systems administrator and configure servers and write firewalls for a living, i live in a bash script. I was totally unaware and unfamiliar about this as i've never done it before.

This might not apply for everyone. I just thought i'd share this experience in good Linux Spirit and hope it might be of use to someone else. I'd also like to thank the OP for an excellent tutorial.

Merry Christmas everyone :)

---

### Post by alanpotteiger on 2013-12-26
Hello! I'm not a very experienced person with this type of thing. I have followed the tutorial and have successfully recorded my screen with audio from my microphone, with one problem. For some reason the audio from my microphone is not synced with the video, Is this a common ocurrence? Any fixes or ideas? Thanks!

---

### Post by alanpotteiger on 2013-12-26
> **alanpotteiger said:**
> Hello! I'm not a very experienced person with this type of thing. I have followed the tutorial and have successfully recorded my screen with audio from my microphone, with one problem. For some reason the audio from my microphone is not synced with the video, Is this a common ocurrence? Any fixes or ideas? Thanks!

Sorry for the double post.
I have partially fixed the problem. I have the audio in sync but only by decreasing the frame rate from 30 to 24. This will work but is there a reason it didn't work at 30?

---

### Post by FakeOutdoorsman on 2013-12-26
Please show your ffmpeg command and the complete ffmpeg console output. Does it make a difference if you replace "-r" with "-framerate"?

---

### Post by alanpotteiger on 2013-12-27
> **FakeOutdoorsman said:**
> Please show your ffmpeg command and the complete ffmpeg console output. Does it make a difference if you replace "-r" with "-framerate"?

Thanks for the response! My command:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 24 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
```
Also it should be noted that decreasing the fps to 24 did not completely fix the problem... It's 50/50 sometimes it's in sync and sometimes it's not, very odd.
Output:
```
ffmpeg version git-2013-12-27-42b6805 Copyright (c) 2000-2013 the FFmpeg developers
  built on Dec 26 2013 20:44:39 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --prefix=/home/apott/ffmpeg_build --extra-cflags=-I/home/apott/ffmpeg_build/include --extra-ldflags=-L/home/apott/ffmpeg_build/lib --bindir=/home/apott/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 59.100 / 52. 59.100
  libavcodec     55. 46.100 / 55. 46.100
  libavformat    55. 22.100 / 55. 22.100
  libavdevice    55.  5.102 / 55.  5.102
  libavfilter     4.  0.103 /  4.  0.103
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1388124885.639449, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
[x11grab @ 0x1bf2c20] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1920 height: 1080
[x11grab @ 0x1bf2c20] shared memory extension found
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1388124885.695288, bitrate: 1592524 kb/s
    Stream #1:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1920x1080, 1592524 kb/s, 24 tbr, 1000k tbn, 24 tbc
No pixel format specified, yuv444p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x1c09680] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x1c09680] profile High 4:4:4 Predictive, level 4.0, 4:4:4 8-bit
[libx264 @ 0x1c09680] 264 - core 140 r2 1ca7bb9 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=24 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf55.22.100
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv444p, 1920x1080, q=-1--1, 1k tbn, 24 tbc
    Stream #0:1: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #0:1 (pcm_s16le -> pcm_s16le)
Press [q] to stop, [?] for help
frame=  129 fps= 24 q=-1.0 Lsize=    2749kB time=00:00:05.37 bitrate=4189.9kbits/s    
video:1717kB audio:1003kB subtitle:0 global headers:0kB muxing overhead 1.082968%
[libx264 @ 0x1c09680] frame I:1     Avg QP: 0.00  size:426614
[libx264 @ 0x1c09680] frame P:128   Avg QP: 0.00  size: 10396
[libx264 @ 0x1c09680] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0x1c09680] mb P  I16..4: 63.8%  0.0%  0.0%  P16..4:  0.0%  0.0%  0.0%  0.0%  0.0%    skip:36.1%
[libx264 @ 0x1c09680] coded y,u,v intra: 0.3% 0.3% 0.3% inter: 0.0% 0.0% 0.0%
[libx264 @ 0x1c09680] i16 v,h,dc,p: 100%  0%  0%  0%
[libx264 @ 0x1c09680] kb/s:2615.57


```

---

### Post by FakeOutdoorsman on 2013-12-27
It's good you're using a recent and real build of ffmpeg.

1. Have you tried using -framerate instead of -r?

2. What if you capture video and audio as separate processes and remux? (The following is untested)
```
ffmpeg -f x11grab -framerate 24 -video_size 1920x1080 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -t 60 v.mkv & \
ffmpeg -f alsa -ac 2 -i pulse -acodec copy -t 60 a.wav && fg; \
ffmpeg -i v.mkv -i a.wav -c copy -shortest muxed.mkv
```

3. What player are you using so you know it is not in sync?

4. Is it better if you re-encode the original, out-of-sync output?
```
ffmpeg -i output.mkv -vf scale=640:-1 -crf 18 -preset medium -pix_fmt yuv420p -c:a copy output.mkv
```

---

### Post by alanpotteiger on 2013-12-27
> **FakeOutdoorsman said:**
> 1. Have you tried using -framerate instead of -r?

Turns out that right there fixed it! Thanks for the help.
And if you're curious I upload the clips to Youtube to verify it's not my viewer making it out of sync.
Thanks again!

---

### Post by maxi.sbrocca on 2014-01-07
Hello all, 

First of all, sorry if the information I'm sharing is not related with the topic.
With some coworkers we are developing a tool to replace Jing for ubuntu. Is free and the source code is in bitbucket [https://bitbucket.org/msbrocca/screen-capturer](https://bitbucket.org/msbrocca/screen-capturer)

So far we are just capturing screen parts to save or share. We have an open branch to work on video capturing.

Feel free to take a look and use it.
Regards,
Maxi

---

