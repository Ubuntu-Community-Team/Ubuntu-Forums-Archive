---
title: "some one worked with Zope read this thread"
date: 2010-08-19
forum: Server Platforms
---

### Post by tapas_mishra on 2010-08-19
I am using a Content Management Systen known as [eduCommons.]("http://educommons.com/")
 
It runs on Zope2.
 
I have a javascript 
```

<object classid='clsid:D27CDB6E-AE6D-11cf-96B8-444553540000' width='470' height='290' id='single1' name='single1'>
<param name='movie' value='http://localhost:8080/eduCommons/player.swf'>
<param name='allowfullscreen' value='true'>
<param name='allowscriptaccess' value='always'>
<param name='wmode' value='transparent'>
<param name='flashvars' value='file=/Courses/video1.flv&streamer=rtmp://_internal_stream_on_lan'>
<embedtype='application/x-shockwave-flash'id='single2'name='single2' 
src='http://localhost:8080/eduCommons/player.swf'
width='470' height='290' bgcolor='undefined' allowscriptaccess='always' allowfullscreen='true'
wmode='transparent'
flashvars='file=/Courses/video1.flv&streamer=rtmp://_internal_stream_on_lan'/>
</object>
```
 
 
The script does work when I create a static html page and view it from Apache Document 
Root but the same script fails to play any video when I see embed it in eduCommons.
I have latest flash player installed on my laptop. 
What can be the problem and what can I do to debug it ?

---

