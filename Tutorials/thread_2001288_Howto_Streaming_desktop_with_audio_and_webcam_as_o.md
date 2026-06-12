---
title: "Howto: Streaming desktop with audio and webcam as overlay in a browser."
date: 2012-06-10
forum: Tutorials
---

### Post by snusmusa on 2012-06-10
First off, this guide is done on ubuntu 10.04. Most likely you could adapt it to other distro.

My work needed a solution to broadcast presentations to other regional offices. 
I started looking into how to do this using open source applications. It needed to be easy to start the streaming and also easily automated.

These are the tools I'm using:

**FFMPEG** 

The stream feeder. It grabs the desktop, audio from pulse and the webcam, encodes it and sends it to the rtmp server

**CRTMPSERVER**

The c++ implementation of rtmp server. It takes my livestream from ffmpeg and does rtmp flvplayback.

**Apache**

It's a web server, there are several guide's on how to set it up so i won't go into it here

**Flowplayer**

The flashplayer of choice. JW Player is also an option, but it had issues with playing my recorded events, so i stuck with flowplayer.

**The Setup.**

I use three different hosts in this scenario. The desktop that will be streaming, the rtmp server and the Apache webserver.

[SIZE="3"]**Configuration:**[/SIZE]

**FFMPEG:**

This is what took me the most time, and there might still be ways to improve on the configuration.
First we need to compile ffmpeg. Use this compilation guide on the ffmpeg site: [[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideLucid](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideLucid)]("http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideLucid")

With that done i'll explain the ffmpeg command i'm using in detail. I feel understanding what ffmpeg actually does will make it a lot easier for you to adapt it to your own need


ffmpeg syntax goes like this: <input1 options> <input1> <input2 options> <input2> <output1 options> <output1> <output2 options> <output2>

This is my complete configuration:

```
ffmpeg -f alsa -itsoffset 1.3 -i pulse -f x11grab -s 1680x1050 -r 30 -i :0.0+0,0 -vf "movie=/dev/video0:f=video4linux2, scale=240:180, setpts=PTS-STARTPTS [movie]; [in][movie] overlay=main_w-overlay_w-2:main_h-overlay_h-2 [out]" -vcodec libx264 -s 960x540 -acodec libmp3lame -ar 22050 -ab 96000 -threads 0 -f flv - | tee desktop.flv | ffmpeg -i - -codec copy -f flv -metadata streamName=livestream tcp://dev-vm221:1234
```

I'll go over the input options, inputs, output options and outputs.

**Input 1:**

```
-f alsa -itsoffset 1.3 -i pulse
```

*-f alsa:* 
This means it will use the alsa format [http://ffmpeg.org/ffmpeg.html#alsa-1](http://ffmpeg.org/ffmpeg.html#alsa-1)

*-itsoffset 1.3:* 
Will delay the input 1.3 seconds, i will explain why i do this later. [http://ffmpeg.org/ffmpeg.html#toc-Main-options]("http://ffmpeg.org/ffmpeg.html#toc-Main-options")

*-i pulse:* 
Use pulse as input.

**Input 2:**

```
-f x11grab -s 1680x1050 -r 30 -i :0.0+0,0
```

*-f x11grab:* 
Tells ffmpeg to use x11grab as the format [http://ffmpeg.org/ffmpeg.html#X11-grabbing](http://ffmpeg.org/ffmpeg.html#X11-grabbing)

*-s 1680x1050:*
This is the portion of the desktop it will capture (if this is larger than the actuall desktop it will not work)

*-r 30:*
This tells it the force 30 frames per second on the input

*-i :0.0+0,0:*
The actual input, this is display 0.0 starting at posision 0,0 (top left corner)

But wait, we are not finished yet. We still need to put the webcam as an overlay onto the desktop. We'll use avfilter to do this:

```
-vf "movie=/dev/video0:f=video4linux2, scale=240:-1, fps, setpts=PTS-STARTPTS [movie]; [in][movie] overlay=main_w-overlay_w-2:main_h-overlay_h-2 [out]"
```

I'm not gonna go into to much detail into how this works but this is the short version:

*-vf:*
The libavfilter option. Configuration of -vf happens within the double quotes. [http://ffmpeg.org/ffmpeg.html#Filtering](http://ffmpeg.org/ffmpeg.html#Filtering)

*movie=/dev/video0:f=video4linux2:*
This tells us that video4linux is out input.

*scale=240:-1:*
This tells us that it will scale the input to 240 pixel in height and -1 means it will keep the original aspect ratio.

*fps:*
It will attempt to use a constant frames per second, this is quite important because without it the webcam might not sync up with the desktop

*setpts=PTS-STARTPTS:*
This tells it to start the presentation timestamp on 0

*overlay=main_w-overlay_w-2:main_h-overlay_h-2: *
his will overlay the input on the previous input in the bottom right corner 2 pixels from the right and 2 pixels from the bottom

Rememer the itsoffset option i put on the first input? This is because this -vf stuff takes some time to encode making the audio come a short time before the video.

Ok, done with inputs, now we need to encode it and send it to out rtmp server.

**Encoding:**

I use h.264 as video codec and mp3 as the audio codec.

*-vcodec libx264 -s 960x540:* 
Quite simply use libx264 as the codec and resize it down to 960x540 resolution. Increasing this will improve the quality, but also increase the bandwidth and cpu usage.

*-acodec libmp3lame -ar 22050 -ab 96000:*

Use the libmp3lame codec with a frequency of 22050 and a bitrate of 96kbit.
One thing important to note is to put this in a flv container we need to specify a supported frequency. 44100 is also accepted.

*-threads 0:*
This tells ffmpeg to support multiple cores when encoding. It should be there if you have dual or quad core CPU's

*-f flv:*
The last part is to place all this encoded stuff into an encoder. Since i'm gonne use flvplayback on my rtmp server i'm placing it into a flv container

*-metadata streamName=livestream tcp://x.x.x.x:1234:*
the metadata option sets the name for the stream, this is so we dont get a random name from the rtmp server.
tcp://x.x.x.x:1234 is the final output. replace x.x.x.x with your rtmp server ip address. 1234 is the port number we use, this can be changed to whatever you want to use on your rtmp server.

That's it :)

Almost.. For me this was not enough as I also needed to record the livestream so people can watch it as VOD. When trying to just add an file as another output, the webcam overlay is not there. 
This is because it sees the -vf part as the first output, and needs to be added to the second part as well. That doesn't work since /dev/video0 gets taken by the first output (device busy).

I managed to do a workaround on this. It might be dirty, but it works for me :)

instead of outputing to the server i first output it to stdout. this is done by a hyphen like this:

```
-f flv - |
```
I then use tee to record everything that comes from stdout

```
tee desktop.flv
```
Then pipe to another ffmpeg instance:

```
| ffmpeg -i - -codec copy -f flv -metadata streamName=livestream tcp://dev-vm221:1234
```
The input here is stdout and i dont encode anything, just copy the previous encoding and output it to the rtmpserver.

There is a catch to this, when you stop ffmpeg it will interupt everything that is being placed in desktop.flv making it unseekable. You can fix it by doing:

```
ffmpeg -i desktop.flv -codec copy fixed.flv
```

Please let me know if you know about a more elegant solution to this. I've tried skipping tee and just use it as a second output in the second ffmpeg instance, but for some reason the quality gets very poor.

**CRTMPSERVER**

I chose this as my rtmp server, there are other server out there that probably work fine as well, but this is what i stuck with.

I grabbed the binaries from here: [http://www.rtmpd.com/downloads/]("http://www.rtmpd.com/downloads/")

Download it with wget in your folder of preference

```
sudo wget http://www.rtmpd.com/assets/binaries/Ubuntu/10.10/i386/crtmpserver-716-Ubuntu-10.10-i386.tar.gz
tar xvzf crtmpserver-717.tar.gz
cd crtmpserver-717
```

Now edit the crtmpserver.lua file. Look for "description="FLV Playback Sample"
Under it you have the acceptors. you need to set the port number to what you are sending with in ffmpeg

```
{
	ip="0.0.0.0",
	port=1234,
	protocol="inboundLiveFlv",
	waitForMetadata=true,
},
```

Then run crtmpserver with this command:

```
./crtmpserver crtmpserver.lua
```

When you start the ffmpeg stream you should see a message that it found the stream "livestream"

This should be all you need on the crtmpserver.

**Flowplayer:**

This can also be tricky, but luckily there are good documentation on the flowplayer site.
I'll only explain how to embedd the player and use the rtmp plugin.

First off you need to add the path to flowplayer in the head:

```
<head>
<script src="http://releases.flowplayer.org/js/flowplayer-3.2.10.min.js"></script
</head>
```

I also use jquery so i have this in the body:

```
<body>
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7/jquery.js" type="text/javascript" charset="utf-8"></script>
```

I have a class called player with some fancy option to make it look a bit cooler.

```
<style>
a.player {
    display:block;
    width:900px;
    height:500px;
    text-align:center;
    color:#fff;
    text-decoration:none;
    cursor:pointer;
    background:#000 url(/media/img/global/gradient/h500.png) repeat-x 0 0;
    background:-moz-linear-gradient(top,
                                    rgba(55, 102, 152, 0.9),
                                    rgba(6, 6, 6, 0.9));
    -moz-box-shadow:0 0 40px rgba(100, 118, 173, 0.5);
}
</style>
```

This also tells it what height and width to use, which is important as flowplayer use the class parameters as default, and if you dont set any it wont show up.

Now for the actual flowplayer configuration:

```
<script>
$(function() {
    $f("stream", "flowplayer/flowplayer-3.2.11.swf", {
	 play:
		{		
		    opacity: 0.0,
		    label: null, // label text; by default there is no text
		    replayLabel: null, // label text at end of video clip
		},

		clip: {url: 'livestream',
			live: true,
			autoPlay: true,
              		provider: 'influxis',
               	},
		canvas: {
        		backgroundImage: 'url(image/offline.png)'
    		},

         	plugins: {
               		influxis: {
                      		url: "flowplayer/flowplayer.rtmp-3.2.10.swf",
                      		netConnectionUrl: 'rtmp://x.x.x.x/flvplayback'
                         	}
                  	}
    
    	});	
 });
</script>
```

Notice i use "stream" as the class id, this must match later on when i decide where to put it. Again, replace x.x.x.x with your rtmp server. Also notice i use livestream on the clip url option, this must match the streamname we use in ffmpeg.

Now embedd this in a div some place, or just in body like this:

```
<div class="player" id="stream" style=float:left"></div>
```

This will put the "stream" into this div and use the class "player" as the style

Now you should be able to start your ffmpeg command and watch the stream in your browser.

That's it. I hope this helps someone. This was all pretty new to me, and still is. If you have suggestions on how to improve on this setup please let me know!

---

