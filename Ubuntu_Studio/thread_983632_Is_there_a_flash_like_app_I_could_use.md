---
title: "Is there a flash like app I could use?"
date: 2008-11-15
forum: Ubuntu Studio
---

### Post by Darkade on 2008-11-15
I mean an app with something like a time line, and layers. I don't want something really fancy but usable.

I tried to use Synfig Studio but Couldn't even add a key frame.

If this is my best option do you know of any good tutorial for it .

Thanks a lot :D

---

### Post by Izek on 2008-11-16
There's flash 4 linux, but it's missing lots of features I believe.

[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by HuaiDan on 2009-02-12
To add a key frame in Synfig File/Panels/Horizontal Dock:layers, children....

You should be able to figure out how to add a keyframe in there. The only experience I've eve had with it I had to go into animation editing mode by clickingon the green round icon on the canvas. That's not to say that's the only way.

I was looking for a thread to voice this about SYnfig. Currently, Synfig does not support scripting and embedded web content, as there is no browser plugin that will play it, nor does it export to SWF TTBOMK.

I'm no coder, and I really wish I knew some people who could jump right on this, I'd help them in every way.

---

### Post by subverted on 2009-03-25
This a tutorial for making flash animations with only Open Source Software (especially on Linux).

First you will need a few programs: [http://synfig.org/Main_Page](http://synfig.org/Main_Page), [http://ffmpeg.mplayerhq.hu](http://ffmpeg.mplayerhq.hu), [http://www.avidemux.org](http://www.avidemux.org), and [http://www.gimp.org/](http://www.gimp.org/).

Skipping right to post-animation stage (using synfig to animate covered later): So you have an animation you made in Synfig. You used layers, png or gif or something that has transparency, and you moved them around on the timeline at keyframes you created while in record mode that you entered by pressing the green checkbox at the bottom right-hand corner of the synfig stage. Just pretend you did that or actually do it.

Now, you have to render the animation. This can be crucial so I want to skip right to this. I like to render the animation with a .yuv [http://www.fileinfo.com/extension/yuv](http://www.fileinfo.com/extension/yuv) filename. This stores your animation information. Go a ahead and render your file. So far you've used GIMP to makea background and layers that you eventually animated in Synfig Studio. Now you have a yuv file of your animation that can be converted to a flv [http://www.fileinfo.com/extension/flv](http://www.fileinfo.com/extension/flv) using ffmpeg! Note, you can also use ffmpeg to make other kinds of files like avi [http://www.fileinfo.com/extension/avi](http://www.fileinfo.com/extension/avi). Ffmpeg is a command-line program so you have to enter some basic commands. In Linux, I store these as bash aliases that look like this:

alias flvto='ffmpeg -i *.flv -ar 44100 -r 25 -qmin 1 -qmax 6' #ex: mymov.mov
alias movto='ffmpeg -i *.mov -ar 44100 -r 25 -qmin 1 -qmax 6' #ex: mymov.mpg 
alias mpgto='ffmpeg -i *.mpg -ar 44100 -r 25 -qmin 1 -qmax 6' #ex: mymov.swf
alias swfto='ffmpeg -i *.swf -ar 44100 -r 25 -qmin 1 -qmax 6' #ex: mymov.flv
alias avito='ffmpeg -i *.avi -ar 44100 -r 25 -qmin 1 -qmax 6' #ex: mymov.flv
alias vobto='ffmpeg -i *.vob' #ex: mymov.mov 
alias yuvto='ffmpeg -i *.yuv -sameq' #ex: mymov.avi (for synfig studio, render as yuv convert to avi)

Those are bash aliases. Aliases are very common in all kinds of programming but are NOT necessary to use FFMPEG. I was just showing an example of an easy way to access these commands on the fly. All you have to do is type the alias: "yuvto", for instance; and then type a newfilename and extension: "mymovie.flv", for instance.

yuvto mymovie.flv

The other way is to actually type it all out:

ffmpeg -i mymovie.yuv -sameq mymovie.flv

FFMPEG is like a swiss-army-knife for audio/visual work. Its minimalistic and fairly easy to use. Now, you have a flash video of your animation using only open-source free software. Going further, you can make several flv videos and append them to each other to make one movie with an audio soundtrack using Avidemux.

Open Avidemux. Go to file>open and open your beginning flv file. Now go to file>append and select the second flv. You can then continue to select one after the other. This is good because making short videos in Synfig is easier than making one long one. Shorter videos render faster and are less likely to crash Synfig. In Avidemux is stacks them all up and saves them quick and simple from file>save>save-video and viola! Add sound, go to Audio>main track, and enter your sound file.

---

