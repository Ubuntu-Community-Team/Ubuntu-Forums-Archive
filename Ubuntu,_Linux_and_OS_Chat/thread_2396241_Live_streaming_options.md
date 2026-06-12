---
title: "Live streaming options"
date: 2018-07-12
forum: Ubuntu, Linux and OS Chat
---

### Post by paulturn2k on 2018-07-12
Hi guys.

I would like to pick peoples brains.

Im looking for a FREE solution to the following requirments 

I am planning on broadcasting a LIVE stream of FPV racing. With a group of 5 pilots fpv feeds presented in OBS software on a windows machine. This will broadcast it to a server and then people will view it on our website.

Is that possible? 

Or should i just use youtube livestream?

Is there a free solution that is lite enough to run on our dedicated ubuntu server that i can put a webpage on so people can login and view the feed.

Hope this makes sense

Thanks
Paul

---

### Post by TheFu on 2018-07-12
Anything is possible, but the answer is "it depends."

You need to run some numbers.  CPU needed for transcoding.  Uplink bandwidth for the streams.  Bitrate per stream. Number of clients.

And you'll need to find a streaming server.  A webserver probably isn't what you want.  There's a reason people use commercial services like Livestream.

---

### Post by nik.charles on 2018-08-26
OBS runs on Linux

---

### Post by TheFu on 2018-08-26
> **nik.charles said:**
> OBS runs on Linux

OBS is a great solution for many things, but may not be the best choice for gaming. It has overhead and will impact FPS. 

It runs on Linux. I use it for recording presentations and a talking head with 2 HD inputs and 3 audio inputs. The recording system has a Core i3 and 4G of RAM. I also use OSB to mux those inputs and others into a final "published" recording after the fact.  It is an easy way to have a talking head in a corner while the slides are huge, full-screen.

I have an external hardware device that sits between the computer and the monitor. It has zero impact on game playback.  My device is a recorder (HDMI input --> recorded h.264/aac/mp4 output), but there are devices designed to stream to different services in 1080 resolutions rather than create mp4 files. Those devices run $120-$3000 depending on your needs.

Do others have more detailed tips?

---

