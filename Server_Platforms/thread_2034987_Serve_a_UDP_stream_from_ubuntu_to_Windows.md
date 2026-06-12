---
title: "Serve a UDP stream from ubuntu to Windows"
date: 2012-07-29
forum: Server Platforms
---

### Post by uRock on 2012-07-29
What I want to do is be able to open movies on my Windows PC, which is connected to the TV. The movies are on another system running ubuntu within my LAN. 

I start having problems with the TCP transfer not keeping up ith the speed of screenplay and causing the movie to pause distort while the movie is playing, which is embarassing. Since the Windows machine is wireless, it will only download from the Desktop at 2MB/s, which is too slow for blueray quality. Smaller 720p videos seem to work flawlessly.

I have tried adjusting samba to speed up these connections with no improvement, so I think setting up a UDP stream will be more usefull, especially if I can set it up to have a buffer. 

How can I set up a UDP streaming server on the desktop machine?

Thanks,
uRock

---

### Post by SeijiSensei on 2012-07-31
See if you have the [Windows NFS client]("http://technet.microsoft.com/en-us/library/cc771698") and export the movies with NFS.  Use the "async" option in [/etc/exports]("http://linux.die.net/man/5/exports") on the Ubuntu box to improve performance over the wireless connection.

Apparently only some versions of Win7 have the NFS client.  I don't think you can add it either, though there may be third party options.

Another option might be an RTSP server.  VLC comes with one of those.  Most video clients support RTSP streams; in SMPlayer/mplayer you use an rtsp:// URL.

---

### Post by nbetham on 2012-07-31
If the problem is the 2Mb/s wireless connection then no change on the serving computer, whether it be a TCP or UDP stream, would change the amount of data you can cram through the wifi channel. Out of curiosity what standard of wifi are you running? And how many devices do you have running on the wifi? If you have a lot of devices on wifi it will slow down speeds quite a bit given that they all have to share the single wifi channel. One of the things you could do is to reduce the number of devices on wifi while watching a movie.

---

### Post by Cheesemill on 2012-07-31
> **nbetham said:**
> If the problem is the 2Mb/s wireless connection then no change on the serving computer, whether it be a TCP or UDP stream, would change the amount of data you can cram through the wifi channel.

You can't change the bandwidth of the link, but you could get more usable data down it by changing protocols. SAMBA is well known for having a high network overhead whereas a UDP stream would have almost none. This could well make all the difference between a stream being unwatchable or bearable.

---

### Post by SeijiSensei on 2012-07-31
TCP requires that the client acknowledge receipt of every single packet.  This adds a lot of overhead to the connection.  The UDP protocol simply blasts out the packets and is indifferent to whether the client received them all or received them in the correct order.  For something like streaming, that's by far the preferable approach.  Even if a packet or two gets dropped along the way, it will be pretty invisible from the perspective of someone watching a streamed video.

---

### Post by nbetham on 2012-07-31
> **SeijiSensei said:**
> TCP requires that the client acknowledge receipt of every single packet.  This adds a lot of overhead to the connection.  The UDP protocol simply blasts out the packets and is indifferent to whether the client received them all or received them in the correct order.  For something like streaming, that's by far the preferable approach.  Even if a packet or two gets dropped along the way, it will be pretty invisible from the perspective of someone watching a streamed video.

While I understand that there is overhead associated with different protocols that is minimal compared to the amount of data that is being sent. A video stream is a huge load on a network, especially a wireless one. And while UDP would mean no resending of packets that will still degrade the quality of the movie. To a certain extent no matter what system is used to transport the data it still has to be encapsulated in some form of transport protocol which encurrs overhead. The problem here is the limited bandwidth of the channel being used, not necessarily that of the transport protocol. I have a gigabit network that I have multiple computers backing up files to a server. Even with a computer sending about 900 Mb/s to the server the overhead for the ack packets being received was only about 70 Kb/s.

---

### Post by Cheesemill on 2012-07-31
> **nbetham said:**
> While I understand that there is overhead associated with different protocols that is minimal compared to the amount of data that is being sent. A video stream is a huge load on a network, especially a wireless one. And while UDP would mean no resending of packets that will still degrade the quality of the movie. To a certain extent no matter what system is used to transport the data it still has to be encapsulated in some form of transport protocol which encurrs overhead. The problem here is the limited bandwidth of the channel being used, not necessarily that of the transport protocol. I have a gigabit network that I have multiple computers backing up files to a server. Even with a computer sending about 900 Mb/s to the server the overhead for the ack packets being received was only about 70 Kb/s.
It's not just the ack packets, the SMB protocol has overheads in the order of around 30% of the usable bandwidth.

---

### Post by uRock on 2012-07-31
> **SeijiSensei said:**
> See if you have the [Windows NFS client]("http://technet.microsoft.com/en-us/library/cc771698") and export the movies with NFS.  Use the "async" option in [/etc/exports]("http://linux.die.net/man/5/exports") on the Ubuntu box to improve performance over the wireless connection.

Apparently only some versions of Win7 have the NFS client.  I don't think you can add it either, though there may be third party options.

Another option might be an RTSP server.  VLC comes with one of those.  Most video clients support RTSP streams; in SMPlayer/mplayer you use an rtsp:// URL.

I will look into those. Thanks! :)

---

### Post by uRock on 2012-07-31
> **nbetham said:**
> If the problem is the 2Mb/s wireless connection then no change on the serving computer, whether it be a TCP or UDP stream, would change the amount of data you can cram through the wifi channel. Out of curiosity what standard of wifi are you running? And how many devices do you have running on the wifi? If you have a lot of devices on wifi it will slow down speeds quite a bit given that they all have to share the single wifi channel. One of the things you could do is to reduce the number of devices on wifi while watching a movie.

My systems are all capable of 100MB/s connections. I have tried adjusting the SMB settings to no avail, which tells me that the routers is setting the speeds. UDP would be able to better utilize the bandwidth restrictions set by the router. Another reason I believe the router is limiting the connection is the fact I can download from outside sights while movies are in play.

---

### Post by nbetham on 2012-07-31
I would give Darwin Streaming Server a try: [http://dss.macosforge.org/](http://dss.macosforge.org/) I have used it before with pretty good success. Here's a tutorial on installing it to be a video streaming: server [http://code.google.com/p/streameverything/wiki/Instructions](http://code.google.com/p/streameverything/wiki/Instructions)

I would definitely try something other than samba to transport the video though.

---

### Post by uRock on 2012-07-31
I am looking at trying VLC's VLM for setting up videos on demand and I am lost when looking at the code [offered in the documentation]("http://wiki.videolan.org/Documentation:Streaming_HowTo/VLM") for setting up channels. I am looking at these conf commands and wondering how exactly they are to be written for ubuntu, the instructions on the page look to be for Windows.```
new channel1 broadcast enabled
setup channel1 input http://host.mydomain/movie.mpeg
setup channel1 output #rtp{mux=ts,dst=239.255.1.1,port=5004,sdp=sap://,name="Channel 1"}

new channel2 broadcast enabled
setup channel2 input udp://@239.255.12.42
setup channel2 output #rtp{mux=ts,dst=239.255.1.2,port=5004,sdp=sap://,name="Channel 2"}

control channel1 play
control channel2 play
```I am wondering if there is an easy way to use something like *.* so that all movies are available.

I was trying to set things up via the GUI, but the documentation on their site doesn't match the GUI in ubuntu's VLC.

Thanks.

---

