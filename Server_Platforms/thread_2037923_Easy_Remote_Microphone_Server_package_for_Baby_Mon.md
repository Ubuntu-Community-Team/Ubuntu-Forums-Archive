---
title: "Easy Remote Microphone Server package for Baby Monitor Project"
date: 2012-08-05
forum: Server Platforms
---

### Post by bakegoodz on 2012-08-05
When I found a Quickcam Pro 9000 packed away, I got the idea to use it as a baby monitor for my baby girl due next month. I found an easy to setup remote webcam package called Motion that throws the video into a web page. [http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)

I almost forgot about sound, what would you recommend for remote sound? It is just going to be used in my home LAN

---

### Post by HermanAB on 2012-08-06
Howdy,

You can use 'mumble' for sound: 
[http://mumble.sourceforge.net/](http://mumble.sourceforge.net/)

Alternatively, you could just pipe '/dev/audio' over the LAN using 'netcat'.

---

### Post by bakegoodz on 2012-08-06
Thanks for answering, but It looks like it designed for gamers that want a talk service. I don't think it is a right fit for me, because I can't figure out how to make so the microphone is on the murmur server. (no gui)

---

### Post by HermanAB on 2012-08-07
OK, here are some ideas - though instead of sending music streams, you can simply send /dev/audio over nc.

--

Piping Audio Around the House

Playing audio over a pair of dinky little speakers is not all that satisfying. So how can you get it playing over a proper sound system? The kind that can rattle the walls and break crystal glasses?

Say, all your music resides on a large disk drive on a noisy server machine in the basement, while another silent PC is relatively close to your HiFi system, then you can run a cable from the sound adaptor line out to the auxiliary input of the amplifier, but you then still need a convenient way to send audio from the server over a LAN. This can be done using a combination of Sound Exchange (sox) and Netcat (nc).

On the HiFi connected PC, sox can play a file like this:

sox file.mp3 -t ossdsp /dev/dsp

However, you want sox to play music coming from the LAN, so it needs to be hooked to a server, that will listen for incoming data. Netcat can do that very conveniently.

To make sox and netcat work together, you need to tell sox the incoming file type (-t mp3, or -t vorbis) and you need to tell sox to grab the data from standard input (the empty '-'):

| sox -t mp3 - -t ossdsp /dev/dsp

Then you need to add a netcat listener before the pipe, to listen on a specific IP address and port:

nc -l -w 10 192.168.1.10 -p 12345

To be really good, you need to put an infinite loop around it, so that if netcat or sox exits, that they will start again:

while [ 1 ]
do
nc -l -w 10 192.168.1.10 -p 12345 | sox -t mp3 - -t ossdsp /dev/dsp
done

Put the above at the end of file /etc/rc.d/rc.local and it will always run when the PC is restarted and the PC will play whatever comes over the LAN - so make sure the volume is turned down a bit...

Now, on the server with the music repository, you can use netcat to send the music to the HiFi like this:

cat *.mp3 | nc 192.168.1.10 12345

That will cause netcat to pipe the music from the basement to the HiFi. Some more scripting can make the system run a playlist, or simply play everything at random.

---

