---
title: "Advice about &lt;video&gt; tag. . . ?"
date: 2009-11-05
forum: The Cafe
---

### Post by pi.boy.travis on 2009-11-05
Hi!

I've just begun learning html after deciding against using any wysiwyg editors, and I am looking to put some videos on my pages, however, I am not sure about the best way to go about it. . .   Should I:

-Use the <object> tag and then pick some common video format.  What video format would likely be the most compatible?

-Use Flash, and face using a proprietary format, finding some player software to run on my server, and yet more coding. . . 

-or use this new <video> tag I keep hearing about.  It seems to work well at first, but what browsers support it?

Just looking for some advice from the Ubuntu community, and I thought I would as here, as this doesn't really have much to do with Ubuntu.

Thanks!

---

### Post by doorknob60 on 2009-11-05
HTML5 with Backup Java applet for non-supported browsers: [http://www.theora.org/cortado/](http://www.theora.org/cortado/)

Example code:
```
<video src="MyVideo.ogv" width="352" height="288">
  <applet code="com.fluendo.player.Cortado.class" archive="http://theora.org/cortado.jar" width="352" height="288">
    <param name="url" value="MyVideo.ogv"/> 
  </applet>
</video>
```

Example site (for the Java applet, doesn't use HTML5): [http://people.xiph.org/~maikmerten/demos/bigbuckbunny-applet.html](http://people.xiph.org/~maikmerten/demos/bigbuckbunny-applet.html)

---

### Post by Frak on 2009-11-06
If you're wanting to support the mass market, skip the <video> tag and go straight into Flash or Silverlight. Both of which penetrate the market way more than HTML5 does. Flash is readily available on around 97% of computers, and Silverlight is readily available for the 83% of computers out there that run Windows and (roughly) 8% that run Mac OS X.

Firefox will play ogg, but will not play H.264
Safari will not play ogg, but will play H.264
Chrome will play ogg, and will play H.264, but the legal issues are iffy.
Internet Explorer won't play either.

Remember to look at your target audience. If you aim for everybody, go for the platform that is
1. Easiest to develop for
2. Most widely supported for in that audience
3. Provides the most fool-proof methods to accomplish your goal

<video> is great because browsers provide a native interface for playing video, but a common format isn't supported. Flash is great, but it is a real performance hog on OS X and Linux systems. It also doesn't show the best consistency between browsers. Silverlight has amazing support on OS X and Windows. It also has a native movie player that only needs stop-placements added to the timeline (via expression media encoder), and some skinning, though the default widgets can be added, but has semi-ok support on Linux. <video> uses an XML method of writing handles, along with Javascript. Flash and Silverlight use XAML for markup, though Flash uses Actionscript for logic and Silverlight is able to use C#, F#, Visual Basic or a combination thereof. Flash is heavily proprietary, while Silverlight and <video> are based on open standards. Flash files cannot be built on Linux (within reason), but Silverlight can. <video> is interpreted, so doesn't need to be built. Flash and Silverlight provide consistent platforms, <video> doesn't. Finally, in terms of streaming media, <video> is the cheapest, followed by Silverlight, since the Media Streaming Server comes stock with Server 2003 and Server 2008 (and R2), while Flash wants (note wants, media streaming servers aren't required, but they can help in a lot of cases and are a great way to protect your media. One such way it benefits is by only sending the parts the client wants, instead of wasting bandwidth sending the entire file. If a client can only play a certain bitrate and quality, the server dynamically creates a copy of the file at that bitrate and stores it for a certain amount of time and increases effeciency by lowering the amount of bandwidth wasted in the transaction and limiting the overall resource hit on the client end, creating a much more happy atmosphere for both parties) Flash wants a media streaming server from Adobe. <video> media streaming includes CDN's and Amazon S3 buckets, Silverlight includes the Windows Media Streaming Server included with Server 2003 and Server 2008 and also open source alternatives. Flash uses the Adobe Flash Media Streaming Server which runs about $995.

Hope that helps some! Oh, and by Flash, I mostly meant Flex, since that's mainly what professional studios use nowadays. The Flex IDE is a modified Eclipse interface. For a good flash media player, [http://flowplayer.org/](http://flowplayer.org/) and [http://www.longtailvideo.com/players/jw-flv-player/](http://www.longtailvideo.com/players/jw-flv-player/). Silverlight comes with a stock media plyer.

---

### Post by pi.boy.travis on 2009-11-06
Wow, thanks for the advice, and for pointing me to that java applet!

---

### Post by Frak on 2009-11-06
> **pi.boy.travis said:**
> Wow, thanks for the advice, and for pointing me to that java applet!
Did my wall-o-text help any? ;)

---

