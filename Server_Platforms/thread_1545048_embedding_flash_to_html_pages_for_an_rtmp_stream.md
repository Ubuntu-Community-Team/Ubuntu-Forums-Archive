---
title: "embedding flash to html pages for an rtmp stream"
date: 2010-08-03
forum: Server Platforms
---

### Post by tapas_mishra on 2010-08-03
Hi,
I am having a streaming server Red5 running on localhost.
Which is Ubuntu 9.04

I have a few HTML pages which should be serving those streams.

I read documentation given here
[http://www.longtailvideo.com/support/jw-player/13/embedding-flash](http://www.longtailvideo.com/support/jw-player/13/embedding-flash)

[http://builddocs.com/server_os_builds/streaming-video-with-red5-oflademo-app/](http://builddocs.com/server_os_builds/streaming-video-with-red5-oflademo-app/)


and

[http://www.longtailvideo.com/support/jw-player/13/embedding-flash](http://www.longtailvideo.com/support/jw-player/13/embedding-flash)
and the swfobject.js and player.swf are on same directory where the test.html page I created is present.

Following is the HTML code
Red5 is working on localhost.
Please see if some one can point out the error in it.
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>

<title>JW Player for Flash</title>

<style type="text/css">
  
  body { background-color: #fff; padding: 0 20px;
       color:#000; font: 13px/18px Arial, sans-serif; }
   a { color: #360; }
  h3 { padding-top: 20px; }
  ol { margin:5px 0 15px 16px; padding:0; list-style-type:square; }

</style>
<script type='text/javascript' src='swfobject.js'></script>

</head>
<body>

<div id='mediaspace'>This text will be replaced</div>
 
<script type='text/javascript'>
  var so = new SWFObject('player.swf','mpl','470','290','9');
  so.addParam('allowfullscreen','true');
  so.addParam('allowscriptaccess','always');
  so.addParam('wmode','opaque');
  so.addVariable('file','avatar.flv');
  so.addVariable('streamer','rtmp://localhost/oflaDemo');
  so.write('mediaspace');
</script>


</body>
</html>

```On [this]("http://developer.longtailvideo.com/trac/wiki/Player5FlashVars") link they explained you need to have file and avatar.flv is a file which I have to stream.
Also a flashvar streamer which should point to the rtmp stream.

I have avatar.flv in my streams folder of application oflaDemo

(where all the videos are kept to stream)

Also on following link
[http://www.longtailvideo.com/support/jw-player-setup-wizard](http://www.longtailvideo.com/support/jw-player-setup-wizard)
there is a sample code generator.

That website was able to play the flv on my Red5 installation on localmachine.
You can also try if you do not have a installation of Red5 then on the second link for setup wizard they have given a dummy flv which is as an example and streams very well.
At the bottom you will get a code snippet that is what I had tried.

---

