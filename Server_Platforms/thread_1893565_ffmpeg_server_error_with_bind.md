---
title: "ffmpeg server error with bind"
date: 2011-12-10
forum: Server Platforms
---

### Post by sirgad on 2011-12-10
Hi,

I've installed ffmpeg using apt-get on my 11.10 3.0.0-13-server laptop.  The server is running BIND9 as a caching DNS for my LAN, and privoxy.  The localhost is set up to ignore privoxy, though, it 's only serving it for the rest of the LAN.  

I'm running the following command as the first step in streaming a webcam over my LAN:

```
ffserver -f ~/ffserver.conf

```
It always fails to run however, with the following error message:

```
bind(): Address family not supported by protocol

```
I've been a good boy and Googled it, and it shows up in a variety of situations on a variety of platforms, but none of the threads I've looked at offer fixes.  I've confirmed in various places that my *ffserver.conf* file is correctly formatted and contains valid options (in truth, it varies very, very little from the example conf file).

Does anyone have any clue what this error means and how it might be avoided?

I've appended the ffserver.conf file for completeness:

```
Port 8090 
# bind to all IPs aliased or not 
BindAddress 0.0.0.0 
# Number of simultaneous HTTP connections that can be handled. It has
# to be defined *before* the MaxClients parameter, since it defines the
# MaxClients maximum limit.
MaxHTTPConnections 2000
# max number of simultaneous clients 
MaxClients 4
# max bandwidth per-client (kb/s) 
MaxBandwidth 10000 
# Suppress that if you want to launch ffserver as a daemon. 
NoDaemon 

<Feed webcam.ffm> 
File /tmp/webcam.ffm 
FileMaxSize 5M
ACL allow 127.0.0.1
</Feed>

<Stream webcam.mjpg>
Feed webcam.ffm
Format mpjpeg
VideoSize qvga
VideoFrameRate 2
VideoIntraOnly
Noaudio
Strict -1
</Stream>

```

Cheers all,

S.

---

