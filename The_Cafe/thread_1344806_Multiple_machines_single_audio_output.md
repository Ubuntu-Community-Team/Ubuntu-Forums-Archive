---
title: "Multiple machines single audio output"
date: 2009-12-03
forum: The Cafe
---

### Post by hwttdz on 2009-12-03
I think it would be clever to be able to sync multiple machines to play the same audio at the same time.  The idea was sparked by this thread.  

[http://ubuntuforums.org/showthread.php?t=1328338](http://ubuntuforums.org/showthread.php?t=1328338)

After reading I think it should be possible to do roughly the same with the audio out, such that two machines play the same audio at the same time (possibly with network delay, which should be minimal over a LAN).  This would allow one to have the same music playing on two different machines synced up.  Of course it would be better if one could limit it to only say rhythmbox.  Any ideas?

---

### Post by NoaHall on 2009-12-03
Why would you want to? Too much network traffic, and one will become out of sync.

---

### Post by hwttdz on 2009-12-03
On a local network I think one might be able to avoid both these problems.  And how will I ever know if I'm not able to test?

---

### Post by Xbehave on 2009-12-03
Pulseaudio is the tool your looking for, it's network transparent so what you want shouldn't be too hard.

---

### Post by Grenage on 2009-12-03
You can't limit it to rythmbox, but you could easily do it in the same way as that poster.  I don't know why you'd want to, but you could.

---

### Post by hwttdz on 2009-12-03
Ok, given I can open an ssh connection and I have root access on both machines, how could I do this? i.e. what would the command be, would I necessarily need to clobber the audio on the receiving machine?

I would want to so that I could have the same music playing on two machines in sync, of course the real reason I would want to is because I'm curious.

---

### Post by Dougie187 on 2009-12-03
> **Grenage said:**
> You can't limit it to rythmbox, but you could easily do it in the same way as that poster.  I don't know why you'd want to, but you could.

Maybe you dont have a home sound system, and you want to listen to music all over the house while you are cleaning. Also, you don't have a portable music player, or a sound system that is capable of being heard throughout the house.

This way you could seamlessly play your music all over the house at the same time, and as you clean you don't have to mess with multiple computers or any issues from the songs begin out of sync.

---

### Post by Xbehave on 2009-12-03
> **NoaHall said:**
> Why would you want to? Too much network traffic, and one will become out of sync.
you can stream audio of the internet so over lan shouldn't be a problem. A typical lan latency is 1ms that is virtually unoticable.

> **Grenage said:**
> You can't limit it to rythmbox, but you could easily do it in the same way as that poster.  I don't know why you'd want to, but you could.
I'm not pulseaudio expert but limiting it to a single app is exactly what PA **can** do!

---

### Post by hwttdz on 2009-12-03
remove

---

### Post by Grenage on 2009-12-03
You'd simply do what the other poster did. He/she is simply taking all audio from one machine to the other.

---

### Post by Dougie187 on 2009-12-03
> **hwttdz said:**
> Ok, given I can open an ssh connection and I have root access on both machines, how could I do this? i.e. what would the command be, would I necessarily need to clobber the audio on the receiving machine?

I would want to so that I could have the same music playing on two machines in sync, of course the real reason I would want to is because I'm curious.

Well, assuming it works. You could go to the machine that you want to play the synced music. So imagine you have your laptop that has music on it, and a desktop that you want to hear the music from.

First, you need to make sure openssh-server is installed on your laptop.

So, on your desktop you would type this
```
ssh <username on laptop>@<ip to laptop> 'dd bs=1k if=/dev/audio' > /dev/audio
```

that should work as he said before, though you might have to play with either /dev/audio if it's in a different location, or the bs=1k if the block size needs to be larger.

---

### Post by Grenage on 2009-12-03
> **Xbehave said:**
> I'm not pulseaudio expert but limiting it to a single app is exactly what PA **can** do!

That is quite possible, but I've never used it for that purpose, so I cannot comment.  It does sound like a better way to go, probably get better sound quality.

---

### Post by hwttdz on 2009-12-03
Just discovering paprefs, pulseaudio is getting to be pretty clever. Of course it would probably be moreso if I had any idea how to use it. 

I think I've got the first possible solution of copying all audio using dd figured.  It seems to me that there is in all likelyhood a pulseaudio solution that forwards all sound, and then further a solution that forwards only rhythmbox.

---

### Post by Dougie187 on 2009-12-03
I'm not sure about this, but I think the biggest obstacle in these situations is the synchronization between the machines.

Did it work well with the ssh solution?

---

### Post by Xbehave on 2009-12-03
I never quite got the PA terminology, but you should be able to define a sink on all the clients (sound from these) that is the server (machine with speakers). On the server there will need to be a source (representin the netwrok) that goes to the real sink (the speakers)
Each of the clients can be set up to use the network sink as the output for just rythembox

[http://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network](http://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network)
is a guide to setup PA to network all sound, it avoids using the words sink/source tho so i'm not sure how it relates to my description.

> **Dougie187 said:**
> I'm not sure about this, but I think the biggest obstacle in these situations is the synchronization between the machines.
That is exactly what PA sorts out, beside a latency of 1ms is unnoticable and as it's simply sound to server, ther is no need for syncronisation.

---

### Post by Dougie187 on 2009-12-03
> **Xbehave said:**
> I never quite got the PA terminology, but you should be able to define a sink on all the clients (sound from these) that is the server (machine with speakers). On the server there will need to be a source (representin the netwrok) that goes to the real sink (the speakers)
Each of the clients can be set up to use the network sink as the output for just rythembox

[http://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network](http://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network)
is a guide to setup PA to network all sound, it avoids using the words sink/source tho so i'm not sure how it relates to my description.

I think it would be the other way in your description. Sink would be on the server (with the music you want to hear), and Source would be on all the clients (machines you want synced with the server).

But I may have just misunderstood what you meant.

> **Xbehave said:**
> That is exactly what PA sorts out, beside a latency of 1ms is unnoticable and as it's simply sound to server, ther is no need for syncronisation.

That's good to know. But yeah, 1ms is not going to be noticeable.

---

### Post by Xbehave on 2009-12-03
> **Dougie187 said:**
> I think it would be the other way in your description. Sink would be on the server (with the music you want to hear), and Source would be on all the clients (machines you want synced with the server).

Client
Source=Rythembox
Sink=Network

Server
Source=Network
Sink=Speakers

but I may be wrong

---

### Post by Dougie187 on 2009-12-03
> **Xbehave said:**
> Client
Source=Rythembox
Sink=Network

Server
Source=Network
Sink=Speakers

but I may be wrong

I think your Sources and Sinks are right, but Client and server are wrong. You want the server to be the rhythmbox feed, and the clients to have the speakers. At least from what I understand.

Just because you only want one computer to be the one playing music, and we could call that the server. And then multiple computers will be playing that music through their speakers so you could hear it anywhere, and you could call these the clients.

---

### Post by Xbehave on 2009-12-03
> **Dougie187 said:**
> I think your Sources and Sinks are right, but Client and server are wrong. You want the server to be the rhythmbox feed, and the clients to have the speakers. At least from what I understand.

Just because you only want one computer to be the one playing music, and we could call that the server. And then multiple computers will be playing that music through their speakers so you could hear it anywhere, and you could call these the clients.
Ah i think i misunderstood what OP wanted.

---

### Post by Dragonbite on 2009-12-03
Wouldn't setting up a machine, like a server, as a shoutbox server do the same thing?

Otherwise making a shortcut that runs the ssh .. command mentioned might work. Again, if it is a machine acting like a server then any desktops on the network can access it whenever they want.

---

### Post by gnomeuser on 2009-12-03
Ironically given all the misdirected hatred it is the subject of, this is one of the situations PulseAudio handles extremely easily.

---

### Post by hwttdz on 2009-12-03
gnomeuser, you don't happen to know how to do it using pulseaudio, i.e. what files I need to edit and which commands I need to run?

---

### Post by gnomeuser on 2009-12-03
> **hwttdz said:**
> gnomeuser, you don't happen to know how to do it using pulseaudio, i.e. what files I need to edit and which commands I need to run?

Something akin to this would work.

[http://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network](http://wiki.archlinux.org/index.php/PulseAudio#PulseAudio_over_network)

---

### Post by hwttdz on 2009-12-03
Of course ubuntu defaults to per user pulseaudio sessions, so it would instead be in the user file instead of the system file.  I can't even manage to get started with that because I can't get even the first steps of pulseaudio going from the command line.

```
user 14:59:48 @ texian ~> pulseaudio -C
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
```

When pulseaudio isn't running, due to stale locks.  I've tried deleting /temp/pulse-*, but to no avail.  This is a reported bug, and will probably be ironed out in time.

I realize that theoretically this is easy especially with the design of pulseaudio, but there doesn't seem to be much useful documentation, and that which exists seems to run into the reality not working the same as the documentation.

Edit: pulseaudio 0.9.19

---

### Post by hwttdz on 2009-12-03
A first step:
killall pulseaudio && sudo rm -rf /tmp/pulse-* && pulseaudio -nC
# -n means don't read the startup file
# -C gets you a pulseaudio command prompt

And to play around without screwing up pulse audio for everyone (and to have a convenient backup):
cp /etc/pulse/daemon.conf ~/.pulse/daemon.conf 
cp /etc/pulse/default.pa ~/.pulse/default.pa  
cp /etc/pulse/client.conf ~/.pulse/client.conf

---

### Post by Dougie187 on 2009-12-04
I was just curious if you got this to work, and if you did how well it works. With either of the two methods.

---

### Post by hwttdz on 2009-12-04
Nope, not yet, and it may be some time.  I'm a little confused as to how the gui interacts with the configuration files.  And if the gui makes changes to the user config files or the /etc/ config files.

---

### Post by Dougie187 on 2009-12-04
Well, I would assume that the gui made user specific changes, but I'm also not really sure that it matters for your test cases.

I think everything you want to do has to be done in the configuration files. As that's where you would define new sinks and sources. But I am not completely sure, because I have never done it myself.

---

### Post by hwttdz on 2009-12-04
But it gets tricky because there are a few ways to configure pulseaudio
1) system wide config (not recommended)
2) per user config, reading files from /etc/pulse (ubuntu default)
3) per user config reading files from ~

I'm guessing the gui makes changes to the file processed in 2.

---

