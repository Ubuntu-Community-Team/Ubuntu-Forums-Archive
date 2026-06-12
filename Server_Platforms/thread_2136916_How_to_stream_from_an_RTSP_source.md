---
title: "How to stream from an RTSP source?"
date: 2013-04-19
forum: Server Platforms
---

### Post by lluuuuuK on 2013-04-19
I didnt know where to put it so I put it here :P.

I recently did an streaming service for an enterprise and I've done a tutorial for all of you out there who want to stream.

So here we go:

 [B][I][I][I][I][I][I][I][FONT=Arial]
[/FONT][/I][/I][/I][/I][/I][/I][/I][/B]**[SIZE=5][B][FONT=Verdana]Requirements:[/FONT]**[/SIZE]

[I]
[LIST]
[*]RTSP source (source that provides an [[COLOR=#0F1399]_RTSP_[/COLOR]]("http://es.wikipedia.org/wiki/Real_Time_Streaming_Protocol") link)
[*]2 computers (A server and a client, in our example we used: **For the client: Ubuntu 13.04 and for the Server: Ubuntu Server 12.10**)
[*]RTMP server ([[COLOR=#0F1399]_crtmpserver_[/COLOR]]("http://www.rtmpd.com/"))
[*][[COLOR=#0F1399]_JW Player_[/COLOR]]("http://www.longtailvideo.com/jw-player/download/") (By using JW Player we will be able to watch the stream on our own website)
[*][[COLOR=#0F1399]_Apache2_[/COLOR]]("http://en.wikipedia.org/wiki/Apache_HTTP_Server") (we need this to run our website, we can download it, on the server, by using the command: sudo apt-get install apache2)
[*][[COLOR=#0F1399]_VLC_[/COLOR]]("http://www.videolan.org/vlc/") (Installed on the client, remember that you cant use VLC if you are as the user “***root***“) (We will also need this to do an [[COLOR=#0F1399]_HLS_[/COLOR]]("http://en.wikipedia.org/wiki/HTTP_Live_Streaming"))
[/LIST]
[SIZE=5]**[FONT=Verdana]How to do an RTSP source?[/FONT]**[/SIZE]

[FONT=Arial]We have two ways to do it:
[/FONT][B][FONT=Verdana]
[SIZE=4]Long Way[/SIZE][/FONT][/B]

[FONT=Arial]For this one you will only need:[/FONT][I]
[LIST]
[*]An Ubuntu client, such as ours: **Ubuntu 13.04**
[*]VLC Installed on the client (remember the annotations above)
[/LIST]
[SIZE=4]**[FONT=Verdana]Steps[/FONT]**[/SIZE]

[I]
[LIST]
[*]Open to VLC
[*]Press **Shift + Ctrl + O**
[*]Press ADD
[*]Add a file
[*]Go to show more options (It is located at the bottom part)
[*]Go to the Play button and click the arrow button (Located right next to it)
[*]Go to Stream (**Alt + S**)
[*]Go to “Destination setup”
[*]Uncheck “Activate Transcoding”
[*]Go to “New Destination” and select **RTSP**
[*]Go to ADD
[*]Replace the path for: /stream
[*]Click next
[*]Check “Stream all elementary streams” and modify “Time-To-Live” to 128
[*]Start streaming
[/LIST]
[FONT=Arial][SIZE=1]Annotation: The RTSP will be something like this: rtsp://our_ip:8554/stream[/SIZE]
[/FONT][B][FONT=Verdana]
[SIZE=4]Short Way[/SIZE][/FONT][/B]

[FONT=Arial]For this one you will only need:[/FONT][I]
[LIST]
[*]VLC installed (remember not to run it as “**root**“).
[*]A file that you want to stream
[/LIST]
[SIZE=4]**[FONT=Verdana]Steps[/FONT]**[/SIZE]

[FONT=Arial]Open a new terminal and copy paste this (remember to change whatever is necessary):[/FONT][FONT=Arial]cvlc file.format :sout=#rtp{sdp=rtsp://:8554/stream} :sout-all :ttl=128sout-keep
[/FONT][B][FONT=Verdana]
[SIZE=5]Steps to stream the RTSP source[/SIZE][/FONT][/B]

[FONT=Arial]First of all, you will need an [/FONT][FONT=Arial]**RTSP source**[/FONT][FONT=Arial], for this example, we will be using this one:[/FONT][COLOR=#0F1399][FONT=Arial]rtsp://apasfwl.apa.at:80/orf1_q6a/orf.sdp[/FONT][/COLOR][FONT=Arial] (German Television)
[/FONT][FONT=Arial]
Next step is to install on the Server an RTMP server, for this example we will be using [/FONT][FONT=Arial]**crtmpserver**[/FONT][FONT=Arial].
[/FONT][B][FONT=Verdana]
[SIZE=5]How to install crtmpserver?[/SIZE][/FONT][/B]

[FONT=Arial]As every software on linux we will install CRTMPServer by using the command:[/FONT][FONT=Arial]sudo apt-get install crtmpserver[/FONT]**[FONT=Verdana]Configuration steps[/FONT]**

[FONT=Arial]When the installation is over, we will check the status of the server by doing:[/FONT][FONT=Arial]sudo service crtmpserver status[/FONT][FONT=Arial]If the server is not started you can start it by doing.[/FONT][FONT=Arial]sudo service crtmpserver start[/FONT][FONT=Arial]Once we have the service started, we will be heading towards the file by using:[/FONT][FONT=Arial]nano /etc/crtmpserver/crtmpserver.lua[/FONT][FONT=Arial]When you get inside of it you will see this line:
[/FONT][FONT=Arial]
externalStreams =
        {
                --[[
                {
                        uri="rtsp://fms20.mediadirect.ro/live2/realitatea/realitatea",
                        localStreamName="rtsp_test",
                        forceTcp=true
                },
                {
                        uri="rtmp://edge01.fms.dutchview.nl/botr/bunny",
                        localStreamName="rtmp_test",
                        swfUrl="http://www.example.com/example.swf";
                        pageUrl="http://www.example.com/";
                        emulateUserAgent="MAC 10,1,82,76",
                }]]--
[/FONT][FONT=Arial]
You can either remove the annotations or create a new uri as we will do:[/FONT][FONT=Arial]On our example we are using [/FONT][COLOR=#0F1399][FONT=Arial]rtsp://apasfwl.apa.at:80/orf1_q6a/orf.sdp[/FONT][/COLOR][FONT=Arial] so we will create a new uri like this:

[/FONT][FONT=Arial]             {
                      uri="rtsp://apasfwl.apa.at:80/orf1_q6a/orf.sdp",
                      localStreamName="stream"
              },
[/FONT][FONT=Arial]
[SIZE=4]Lets explain the fields
[/SIZE][/FONT][I]
[LIST]
[*]Uri = The RTSP that we provided at the beginning, in our example: [COLOR=#0F1399]rtsp://apasfwl.apa.at:80/orf1_q6a/orf.sdp[/COLOR]
[*]localStreamName = The link that we will provide to the viewers, for example: [[COLOR=#0F1399][/COLOR]]("http://our_ip/live/")[COLOR=#0F1399]_[http://our_ip/live/](http://our_ip/live/)_[/COLOR]**stream**
[/LIST]
[FONT=Arial]
After that you must restart the server and check if everything is alright by using the command:[/FONT][FONT=Arial] sudo service crtmpserver restart[/FONT][FONT=Arial]And checking if it is started by using:[/FONT][FONT=Arial]sudo service crtmpserver status
[/FONT][B][FONT=Verdana]

[SIZE=5]Installing Apache and testing JW Player[/SIZE][/FONT][/B]

[FONT=Arial]Once you have Apache installed on your server, which will be installed at /var/www, we will dowload JW Player by doing:
[/FONT][B][FONT=Verdana]
[SIZE=4]On the client[/SIZE][/FONT][/B]

[I]
[LIST]
[*]Go to [[COLOR=#0F1399][/COLOR]]("http://www.longtailvideo.com/jw-player/download/")[COLOR=#0F1399]_[http://www.longtailvideo.com/jw-player/download/](http://www.longtailvideo.com/jw-player/download/)_[/COLOR] and download JW Player
[*]cd /home/**youruser**/Downloads/
[*]scp jwplayer-3242.zip root@130.206.32.145:/var/www
[/LIST]
[SIZE=4]**[FONT=Verdana]On the server[/FONT]**[/SIZE]

[I]
[LIST]
[*]cd /var/www
[*]sudo unzip jwplayer-3242.zip
[*]nano index.html (This is our website) (You will find something like, It works!) Erase all the content and copy paste this:
[/LIST]
[FONT=Arial]<html>

<head>
<script src="http://jwpsrv.com/library/mAx4MKWXEeKuhCIACpYGxA.js"></script>




</head>


<body><h1>It works!!!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>



<div id='my-video'>
<script type='text/javascript'>
    jwplayer('my-video').setup({
        file: 'rtmp://our_ip/live/stream',
    image: 'img',
        width: '480',
        height: '270',

    });
</script>
</div>




</body>



</html>

[/FONT][SIZE=5]**[FONT=Verdana]Explanation[/FONT]**[/SIZE]

[FONT=Arial]Pay attention to the line:[/FONT][FONT=Arial]file: 'rtmp://our_ip/live/stream'[/FONT][FONT=Arial]As you must use replace “our_ip” by the ip of your server.[/FONT][FONT=Arial]By following this steps you should be able to watch your stream on the following path: 10.34.2.125 [/FONT][[COLOR=#0F1399][FONT=Arial][/FONT][/COLOR]]("http://yourip/index.html")[COLOR=#0F1399]_[http://yourip/index.html](http://yourip/index.html)_[/COLOR][FONT=Arial]After testing our stream we will do it compatible with mobile devices.[/FONT]**[FONT=Verdana]Steps for doing an HLS[/FONT]**

[I]
[LIST]
[*]Add to your index.html file the following line (before </body>):
[/LIST]
[FONT=Arial]<video autoplay loop controls>
  <source src="http://our_ip/stream.m3u8" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'/>
</video>[/FONT][I]
[LIST]
[*]Open a new terminal and use the following command (pay attention about what you must replace):
[/LIST]
[FONT=Arial]vlc -v -I "dummy" rtmp://our_ip/live/stream :sout="#transcode{vcodec=h264,vb=100, venc=x264{aud,profile=baseline,level=30,keyint=30,ref=1}, aenc=ffmpeg{aac-profile=low},acodec=mp4a,ab=32,channels=1,samplerate=8000} :std{access=livehttp{seglen=2,delsegs=true,numsegs=2, index=/var/www/stream.m3u8, index-url=http://our_ip/stream-########.ts}, mux=ts{use-key-frames}, dst=/var/www/stream-########.ts}"
[/FONT][FONT=Arial]
After that you will be able to watch your stream via mobile devices, such as:[/FONT][I]
[LIST]
[*]iOS Devices
[*]Android Devices (This functionality only worked on Google Chrome).
[/LIST]
[/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/B]

---

