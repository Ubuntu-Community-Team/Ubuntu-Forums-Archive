---
title: "vlc on Ubuntu could not connect to Streaming server in windows it did"
date: 2010-07-30
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-30
I am having a strange issue probably some expert here can help me to debug.
I am having a media server Red5 Running on LAN on a CentOS 5.5 64 bit server.
The version of Red5 is 0.9.1
 Checked from Linux that was Ubuntu 9.04 
in VLC ,vlc could not get the stream of video.
 Checked from VLC on Mac OS X 10.5.8 PPC G5 machine

there also it did not got the stream of video.
Checked from a Windows XP machine on which vlc 1.0.5
 In Windows VLC was able to connect to Red5 on OCW and I am able to see
 the streamed video.


If some one wants to know how I installed Red5 to be able to understand any problem 
here is a link
[http://mightydreams.blogspot.com/2010/06/installing-red5-on-centos-55-64-bit.html](http://mightydreams.blogspot.com/2010/06/installing-red5-on-centos-55-64-bit.html)

Following is the link
[http://www.praggo.com/2009/12/media-streaming-with-red5.html](http://www.praggo.com/2009/12/media-streaming-with-red5.html)
on which accessing a file in VLC from a Red5 server is described.

Currently in Windows VLC I go to
Media--->Open Network Stream--->Network

Set the protocol to rtmp and the URL as rtmp://(IP of Red5 server):1935/olfaDemo/avatar.flv

and I am able to see the video but the same steps on a Linux or other machine is not working.

Here is the message from VLC log
```

main info: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
access_rtmp error: body handshake received corrupt
access_rtmp error: handshake active failed
main error: open of `rtmp://192.168.1.5:1935/oflaDemo/avatar.flv' failed: could not create access

```

What should I do to be able to debug this thing ?

---

