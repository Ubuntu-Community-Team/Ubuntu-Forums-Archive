---
title: "Apache as front end for rtmp stream"
date: 2010-08-06
forum: Server Platforms
---

### Post by tapas_mishra on 2010-08-06
I am having a website which is running on Zope.
I am using Apache as a front end to that Zope website.

On the same server where Zope is running I am having a streaming server Red5 running on it.
My communication to the Zope website from outside world is via front end Apache only.

To be able to reach the streaming server I 
embed a javascript in HTML pages of Zope website which is running Plone 
as follows
<embed .....
var="rtmp://my_domain.com"
>

My problem is a request for mydomain.com is handled via front end Apache on which I have redirected this to Zope.
Now in case of rtmp streams which are coming in form of rtmp://my_domain.com
is it possible to do some thing in Apache so that
request to video streams  coming from outside to be redirected
to Red5 on internal server on LAN.

So our communication with world is via Apache only.
In this situation how can apache redirect to a Red5 application or say
a stream on rtmp.
If  some one has  some clue on this then let me know.

---

