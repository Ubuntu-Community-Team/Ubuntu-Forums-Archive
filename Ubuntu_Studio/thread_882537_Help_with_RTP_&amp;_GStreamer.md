---
title: "Help with RTP &amp; GStreamer"
date: 2008-08-07
forum: Ubuntu Studio
---

### Post by darkweaver87 on 2008-08-07
Hi everyone,

I have some troubles streaming video file over the network.

First of all, I tired this :

server:
gst-launch filesrc location=../partage/Videos/superman_originale.avi ! 
decodebin ! x264enc ! video/x-h264 ! rtph264pay pt=96 ! udpsink 
host=192.168.1.2 port=5000 sync=false

client:
gst-launch udpsrc port=5000 ! rtph264depay  ! decodebin ! xvimagesink

It works but I can't read it with vlc : vlc udp://@:5000 : is it normal ?

Now I would like to do the same thing with an RTP pipeline :

server:
gst-launch filesrc location=../partage/Videos/superman_originale.avi ! 
decodebin ! x264enc ! rtph264pay ! rtpbin localport=5001 
destinations=127.0.0.1:5000

client:
gst-launch udpsrc port=5000 ! rtph264depay ! decodebin ! xvimagesink --> 
this works
gst-launch rtpbin localport=5000 ! rtph264depay ! decodebin ! 
xvimagesink --> this doesn't work

How can I receive my stream ? with vlc ?

Thanks in advance !

---

### Post by darkweaver87 on 2008-09-09
Found:

server:
gst-launch -v gstrtpbin name=rtpbin \
    filesrc location=filesrc location=../../../partage/Videos/superman_originale.avi ! decodebin name=dec \
    dec. ! queue ! x264enc byte-stream=false bitrate=300 ! rtph264pay ! rtpbin.send_rtp_sink_0 \
    rtpbin.send_rtp_src_0 ! udpsink port=5000 host=127.0.0.1 ts-offset=0 name=vrtpsink \
    rtpbin.send_rtcp_src_0 ! udpsink port=5001 host=127.0.0.1 sync=false async=false name=vrtcpsink \
    udpsrc port=5005 name=vrtpsrc ! rtpbin.recv_rtcp_sink_0 \
    dec. ! queue ! audioresample ! audioconvert ! alawenc ! rtppcmapay ! rtpbin.send_rtp_sink_1 \
    rtpbin.send_rtp_src_1 ! udpsink port=5002 host=127.0.0.1 ts-offset=0 name=artpsink \
    rtpbin.send_rtcp_src_1 ! udpsink port=5003 host=127.0.0.1 sync=false async=false name=artcpsink \
    udpsrc port=5007 name=artpsrc ! rtpbin.recv_rtcp_sink_1


client:

gst-launch -v gstrtpbin name=rtpbin latency=200 \
     udpsrc caps="application/x-rtp,media=(string)video,clock-rate=(int)90000,encoding-name=(string)H264" port=5000 ! rtpbin.recv_rtp_sink_0 \
       rtpbin. ! rtph264depay ! decodebin ! xvimagesink \
     udpsrc port=5001 ! rtpbin.recv_rtcp_sink_0 \
         rtpbin.send_rtcp_src_0 ! udpsink port=5005 host=127.0.0.1 sync=false async=false \
     udpsrc caps="application/x-rtp,media=(string)audio,clock-rate=(int)8000,encoding-name=(string)PCMA" port=5002 ! rtpbin.recv_rtp_sink_1 \
       rtpbin. ! rtppcmadepay ! decodebin ! audioconvert ! audioresample ! alsasink \
     udpsrc port=5003 ! rtpbin.recv_rtcp_sink_1 \
         rtpbin.send_rtcp_src_1 ! udpsink port=5007 host=127.0.0.1 sync=false async=false

or :

gst-launch -vvv playbin uri=file:///home/user/test/gstreamer/client.sdp

with client.sdp:
v=0
o=- 1188340656180883 1 IN IP4 127.0.0.1
s=Session streamed by GStreamer
i=server.sh
t=0 0
a=tool:GStreamer
a=type:broadcast
m=video 5000 RTP/AVP 96
c=IN IP4 127.0.0.1
a=rtpmap:96 H264/90000
m=audio 5002 RTP/AVP 8
c=IN IP4 127.0.0.1

---

### Post by uverma on 2009-03-17
Hey darkweaver87,

I am trying to do a similar thing and your solution works great.  However, I am having trouble transferring data over the network (it works great locally).  I changed the IP addresses etc for remote data transfer.  But I keep getting the following error on the client side:

ERROR: from element /GstPipeline:pipeline0/GstUDPSrc:udpsrc0: Internal data flow error.
Additional debug info:
gstbasesrc.c(2234): gst_base_src_loop (): /GstPipeline:pipeline0/GstUDPSrc:udpsrc0:
streaming task paused, reason not-negotiated (-4)


Do you have any ideas on what could be wrong? or if there's something similar you've seen before?

Thanks!

---

### Post by darkweaver87 on 2009-03-17
Sorry but I don't know where the error is.

I've worked on it in an internship and it's not very fresh anymore in my mind.

After I posted this thread, I tried, like you, to make it work over a network because I retieved an other PC. And it didn't work because of a bug in the SDP parser.

But the other solution :
```
gst-launch -v gstrtpbin name=rtpbin latency=200 ...
```
has always worked.

---

### Post by uverma on 2009-03-17
hmm .. weird.  Well, I will dig deeper into this and see if I can get it to work.

Thanks for your reply.

---

### Post by uverma on 2009-03-17
It worked for me now, with some help from #gstreamer and [http://cgit.freedesktop.org/gstreamer/gst-plugins-good/tree/tests/examples/rtp](http://cgit.freedesktop.org/gstreamer/gst-plugins-good/tree/tests/examples/rtp)

Thanks,

---

### Post by guodehua on 2010-11-09
hi,uverma:
    I have a same problem you have solved, when I use gstreamer plugin transmit the video and audio, hanppen an error, error message as below:
ERROR: from element /GstPipeline:pipeline0/GstUDPSrc:udpsrc0: Internal data flow error.
Additional debug info:
gstbasesrc.c(2550): gst_base_src_loop (): /GstPipeline:pipeline0/GstUDPSrc:udpsrc0:
streaming task paused, reason not-negotiated (-4)
 
my test example
Server:
gst-launch -v gstrtpbin name=rtpbin filesrc location=filesrc location=robot.avi ! decodebin name=dec dec. ! queue ! x264enc byte-stream=false bitrate=300 ! rtph264pay ! rtpbin.send_rtp_sink_0 rtpbin.send_rtp_src_0 ! udpsink port=5000 host=127.0.0.1 ts-offset=0 name=vrtpsink rtpbin.send_rtcp_src_0 ! udpsink port=5001 host=127.0.0.1 sync=false async=false name=vrtcpsink udpsrc port=5005 name=vrtpsrc ! rtpbin.recv_rtcp_sink_0 dec. ! queue ! audioresample ! audioconvert ! alawenc ! rtppcmapay ! rtpbin.send_rtp_sink_1 rtpbin.send_rtp_src_1 ! udpsink port=5002 host=127.0.0.1 ts-offset=0 name=artpsink rtpbin.send_rtcp_src_1 ! udpsink port=5003 host=127.0.0.1 sync=false async=false name=artcpsink udpsrc port=5007 name=artpsrc ! rtpbin.recv_rtcp_sink_1
 
client:
gst-launch -v gstrtpbin name=rtpbin latency=200 udpsrc caps="application/x-rtp,media=(string)video,clock-rate=(int)90000,encoding-name=(string)H264" port=5000 ! rtpbin.recv_rtp_sink_0 rtpbin. ! rtph264depay ! decodebin ! xvimagesink udpsrc port=5001 ! rtpbin.recv_rtcp_sink_0 rtpbin.send_rtcp_src_0 ! udpsink port=5005 host=127.0.0.1 sync=false async=false udpsrc caps="application/x-rtp,media=(string)audio,clock-rate=(int)8000,encoding-name=(string)PCMA" port=5002 ! rtpbin.recv_rtp_sink_1 rtpbin. ! rtppcmadepay ! decodebin ! audioconvert ! audioresample ! alsasink udpsrc port=5003 ! rtpbin.recv_rtcp_sink_1 rtpbin.send_rtcp_src_1 ! udpsink port=5007 host=127.0.0.1 sync=false async=false
 
can you give me some advice, thanks.

---

### Post by guodehua on 2010-11-09
uverma,
    could you tell me how do you solve the problem? I have the same problem, and have not solved until now.

---

