---
title: "Web Server Won't Serve MP4 Files"
date: 2015-02-20
forum: Server Platforms
---

### Post by Luft on 2015-02-20
I'm playing around with HTML5 and the video tag but my Apache 2 web server is giving an error 203 (Forbidden) rather than serve the file.

My OS is Ubuntu 14.04. 

Can someone help me out?  Thanks

---

### Post by lisati on 2015-02-20
If you're getting [403]("http://en.wikipedia.org/wiki/HTTP_403") (forbidden) it could mean that there are permissions issues with the folder where you are storing the files. ([203]("http://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_Success") means something else....)

If memory serves correctly, a web server needs at least read access to folders and files that you intend to make available for download.

---

### Post by Luft on 2015-02-20
> **lisati said:**
> If you're getting [403]("http://en.wikipedia.org/wiki/HTTP_403") (forbidden) it could mean that there are permissions issues with the folder where you are storing the files. ([203]("http://en.wikipedia.org/wiki/List_of_HTTP_status_codes#2xx_Success") means something else....)

If memory serves correctly, a web server needs at least read access to folders and files that you intend to make available for download.

Yes, the error was 403 not 203 :oops:
I checked and all of the permissions are okay.
The server is choosing to to allow the file to be served or downloaded.  I have been reading and it might have something to do with .htaccess or the lack there of and something to do with mimes??  I'm so confused! :p

---

### Post by Doug S on 2015-02-20
> **Luft said:**
> Yes, the error was 403 not 203 :oops:
I checked and all of the permissions are okay.
The server is choosing to to allow the file to be served or downloaded.  I have been reading and it might have something to do with .htaccess or the lack there of and something to do with mimes??  I'm so confused! :pmp4 is defined in the /etc/mime.types file. You shouldn't need an .htaccess file. It works fine on both my 12.04 and 14.04 servers. Here is my html 5 mp4 test source file:```
<!DOCTYPE HTML>
<html>
<head>
 <META http-equiv="Content-Type" content="text/html;charset=utf-8" >
 <META NAME="ROBOTS" CONTENT="NOINDEX, NOFOLLOW">
 <TITLE> WWW.Smythies.com - Doug Test HTML 5 video clip. 2014.01.21</TITLE>
 <STYLE type="text/css">
    <!--
    @import url(/includes/smythies.css);
    -->
 </STYLE>
</head>
<BODY>
<P>
Example will use HTML 5 to show .mp4 (H.264) video clip:<BR>
The flash stuff is annoying, and what used to work doesn't anymore.<BR>
<BR>

<video width="640" height="480" controls autoplay>
   <source src="./Flash_test.mp4" type="video/mp4">
   Your browser does not support the video tag.
</video>

</P>
<ADDRESS>
WWW.Smythies.com - Doug Test HTML 5 video clip.
emaildoesnotwork@smythies.com 2014.01.21 Updated 2014.01.21
</ADDRESS>
</body>
</html>
```

---

### Post by Luft on 2015-02-21
Thanks Doug.

I don't see anything in your html 5  that is missing from my code.  If you want to check out my test page it's at [http://www.stellar-portal.net/onlinegaming/teamfortress2/thebulldog.html](http://www.stellar-portal.net/onlinegaming/teamfortress2/thebulldog.html).  I have put two links in the side bar.  One is for a Team Fortress 2 demo and the other for a mp4 file that was created from the demo.  The demo file can be downloaded easily by right mouse clicking on the link and selecting "Save Link As" but the mp4 file won't get served.  Both have the same permissions and both are in the same directory.

Are you running anything else like Mod Security?  Maybe I should disable mod security as a test.  I wouldn't want to leave it disabled for long, however, with all of the malicious hits it has been getting.  Unbelievable that hackers want control of my little home server.

---

### Post by Doug S on 2015-02-21
Try changing this:```
    <video width="320" height="240" controls>
        <source src="../movies/bulldog.mp4" type="video/mp4">
    Your browser does not support the video tag.
    </video>
```to this:```
    <video width="320" height="240" controls>
        <source src="./movies/bulldog.mp4" type="video/mp4">
    Your browser does not support the video tag.
    </video>
```I think your problem is merely that you are pointing to [http://www.stellar-portal.net/onlinegaming/movies/](http://www.stellar-portal.net/onlinegaming/movies/) instead of [http://www.stellar-portal.net/onlinegaming/teamfortress2/movies/](http://www.stellar-portal.net/onlinegaming/teamfortress2/movies/)

---

### Post by Luft on 2015-02-21
That was definitely an error but changing it didn't fix the problem.  The links in the side bar are correct.  The demo file downloads but the mp4 does not.:?

---

### Post by SeijiSensei on 2015-02-21
I didn't see any thumbnail on the page, but clicking on the MP4 video displays it in Firefox.  I have the "Cisco OpenH.264 codec" installed as an add-on to Firefox.  If you don't (look in Tools > Addons > Plugins), update Firefox and see if that solves the problem.

---

### Post by Luft on 2015-02-21
I was using chrome but you are correct that in Firefox, clicking on the mp4 link plays the video.  Progress!

So it looks like the video tag is not being handled correctly but my server is serving the mp4 file if referenced from a link.

hmmm... I'll have to think about this...

Edit:

The mp4 link plays in firefox on my Linux laptop but not on my windows 7 PC.  Windows says that the file is corrupt.  Now I wonder if the TF2 created the mp4 in some non-standard way.

---

### Post by Doug S on 2015-02-22
> **Luft said:**
> Windows says that the file is corrupt.For me also. Firefox, without any special add-ons on a windows 8.1 computer. My own page works fine. I'll try a Ubuntu desktop VM tomorrow, as it is late in my time zone.

Edit: I cannot get anywhere with Ubuntu desktops either. Tried 14.04 and 15.04 (dev) desktop VMs.

---

### Post by SeijiSensei on 2015-02-23
> **Luft said:**
>  Windows says that the file is corrupt.
If you download the file and try playing it with Windows Media Player or a third-party player like VLC or SMPlayer, what happens?

HTML5 video implementations require that the browser have a matching codec to display the streamed content.  That's now available for Firefox with the [arrival of the Cisco OpenH264 codec]("http://andreasgal.com/2014/10/14/openh264-now-in-firefox/").  I'm running Firefox 35.01 on Kubuntu 14.04 and have the codec installed as a Firefox add-on. I don't have any player add-ins other than Flash and Silverlight via pipelight either; in particular, I don't have gecko-mediaplayer installed.

There's a limitation to the OpenH264 implementation that the linked article points out:
> Note: Firefox currently uses OpenH264 only for WebRTC and not for the <video> tag, because OpenH264 does not yet support the high profile format frequently used for streaming video. We will reconsider this once support has been added.

The video comes up initially with a message that it cannot be played, but I could right-click on it and choose View Video to open it in a separate browser window.

---

### Post by Luft on 2015-02-23
If I download the file (link) I can play it.  However, Chrome on Windows 7 will not download the file.  I get a "Failed - Server problem" message in the download bar. I can download the file using Firefox even in Windows 7.

This all appears to be browser / plugin related on the client side.

What I'm really interested in is getting the Video tag working rather than spend much time with the link.  If I can get the Video to stream then I can remove all of the links anyway.

I though that HTML5 and the video tag was suppose to free us from all of the dependencies on 3rd party plugins?

[Edit] Thanks to all who have replied.  Any help is greatly appreciated.

---

### Post by Doug S on 2015-02-24
> **Luft said:**
> I though that HTML5 and the video tag was suppose to free us from all of the dependencies on 3rd party plugins?Exactly, and that is what I thought also. As far as I know my test stuff works without any third party stuff. Also some of my older HTML4 versions, that use the same .mp4 h264 file, that used to work on most browsers now doesn't work on most browsers.

---

### Post by Luft on 2015-02-25
I found an explanation of why Quicktime doesn't like some of my mp4 files.  I wish I had bookmarked the page.  I'll have to find it again but as I remember it has something to due with the encoding of either the video or audio.  Quicktime just doesn't think it is valid in an mp4 file but if you change the extension to m4v Quicktime will play it fine.

Also I read that mp4 is not as standard as we might like.  Some mp4 files have an index that is placed at the back of the file and some have the index at the front of the file.  We want the indexes to be at the front so that they are read first rather than forcing a browser to read the entire file.

I guess the upshot of the whole thing is that I have a lot to learn.  I did manage to get the thumbnail to show if I viewed my page using Firefox.  I have to right mouse click and select "view video" then mouse click on the progress bar to bring the video to the end of the file.  This forces my browser to read the entire file.  Then use the back arrow to return to my web page and finally click on the refresh page button.

Wow, what a pain but doing all that does allow the page to look as I want it to every time.  Now I need to figure out why and from there how to fix it.  I think it has something to do with the fact that the video has to load all the way first.  Maybe it's that index thing?

---

### Post by Doug S on 2015-02-25
> **Luft said:**
> Also I read that mp4 is not as standard as we might like.  Some mp4 files have an index that is placed at the back of the file and some have the index at the front of the file.  We want the indexes to be at the front so that they are read first rather than forcing a browser to read the entire file.Oh ya!!! I remember now. I went through a huge saga so that autostart would work. I had to place the stuff at the start of the file, but it defaulted to the end of the file. So I had to re-process the files. I was so "Grrrr" by the end of it.

Edit: I found my notes (although they are a little old now, having been done in 2009):

"Now, autostart does not quarantee that the video clip will play while downloading, also known as progressive download. It turns out that one can not make a .mp4 highly compressed file from iMovie or Quicktime that will play while downloading or do progressive download. It is easy with the 9 times worse compression stuff, but that kind of defeats what I wanted to be able to do. No matter what options one selects, the MOOV Atom (new lingo to me. The "chunk" or "Block" that is needed to be able index into and play or jump ahead or whatever.) is output at the end of the file, so the entire download is required before it can be played. However, there is a tool called qt-faststart that will move the MOOV Atom to the start of the file. One can find qt-faststart.c on internet and compile it and get a problematic program that will crash and not work. qt-faststart.c is also included as a tool in ffmpeg. Even though the qt-faststart.c code is still called version 0.1 it has differences from the crash type version. If one compiles ffmpeg first (took hours on my linux box and had zillions of warnings), then compiles qt-faststart it seems to work properly. Once one post processes their .mp4 file with qtfaststart.c, it will play while downloading, or will progressive download."

---

### Post by Luft on 2015-02-26
I use Handbrake and I noticed that there is a "web optimize" checkbox.  I wonder if that ensures that the index for mp4 files will be in the front?

---

### Post by FakeOutdoorsman on 2015-02-26
> **Luft said:**
> I use Handbrake and I noticed that there is a "web optimize" checkbox.  I wonder if that ensures that the index for mp4 files will be in the front?

Yes, I believe it does.

Alternatively you can use ffmpeg:
```

ffmpeg -i input.mp4 -c copy -movflags +faststart output.mp4
```
[list]
[*]This will [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy), so no re-encoding is occurring.
[*]Since Ubuntu does not provide ffmpeg (the real one) until 15.04 (IIRC) you can simply download, extract, and run a [static build](http://johnvansickle.com/ffmpeg/). I'm unsure if the old Libav flotsam in the repo supports this option.
[/list]

---

