---
title: "Cortado with flumotion 0.6.1"
date: 2010-02-06
forum: Ubuntu Studio
---

### Post by redxine on 2010-02-06
I'm setting up a streaming server for my church with flumotion and am trying to test it with the cortado java applet. I can successfully connect to a stream on [http://localhost:8800/ogg-audio-video/](http://localhost:8800/ogg-audio-video/) with firefox, but need to be able to read it with the java client for deployment. I'm serving the applet from apache on port 80 on the same machine, so the java security limitation shouldn't be a problem (right?). Here's my index.html:

```

<applet code="com.fluendo.player.Cortado.class"
        archive="cortado.jar"
        width="320" height="240">

   <param name="url" value="http://localhost:8800/ogg-audio-video/"/>
   <param name="keepAspect" value="true"/>
   <param name="video" value="true"/>
   <param name="audio" value="true"/>
<param name="bufferSize" value="200"/>
<param name="keepaspect" value="true"/>
    <param name="local" value="false"/>

</applet>
```

I'm using the ovt version of the jar file but keep getting "Unknown stream http://localhost:8800/ogg-audio-video/" every time. Any suggestions?

---

