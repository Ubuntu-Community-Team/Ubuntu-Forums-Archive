---
title: "SSH connections to Server, making it act identical to working at the host"
date: 2011-08-14
forum: Server Platforms
---

### Post by asomad on 2011-08-14
Hi, I'm a Linux Noob, but not a computer noob. I'm running lucid server on one of my machines. I like using a command line program called mp3blaster, to listen to music, it works great. When I'm at the server's terminal to run it.

I primarily tinker with my server via SSH connection from my laptop, both from Ubuntu-gnome terminal, and Win7 with PuTTY.

I would like to use my command line music player, via an SSH connection, and have it work as if I'm at the server's terminal, with the sound coming from the server. However due to some differences between SSH and Local logon, (and this is what im trying to learn in order to solve my problem), When I run mp3blaster locally at the host, it's great. When I try to run mp3blaster, through ANY ssh connection, it opens fine but displays a "failed to load audio device" error upon initiating a file playback. I know this is because I'm trying to run the program through an SSH connection. 

My question is What can I do run applications via SSH, and have those applications run EXACTLY the same as if I was logged in locally.

 I.e. perhaps my sound device isn't active when I'm not logged in locally? I'm a noob, but not helpless, a little idea of what my problems exact cause could be, or just some direction, will go a long way. thanks in advance. 

I'd rather be taught to fish, than given a fish...

---

### Post by asomad on 2011-08-14
I think this issue can be solved by adding an environmental variable to "/.ssh/environment" or "/etc/ssh/sshd_config", am I correct? and if so, how can I find out which variable and value "VAR=VALUE" to set to get audio to work on the host while i'm operating via SSH connection? 

how could I even find out which audio device(s)(?) are being used by the app when Im running it at the host machine... Ive been reading everything I can find for about twenty four out of the last 48 hours. Im learning, but i'm still missing something here.

---

### Post by papibe on 2011-08-15
Have you tried using the -x option (to stop forwarding)?
```
$ ssh -x youruser@yourserver
```
Regards.

---

### Post by asomad on 2011-08-15
That sounded like a really worthwhile idea. I thought that could be the trick. Unfortunately it made no difference, at least for sound, lol. but thanks for the idea! 

Ive also tried it with X11  forwarded. I am a noob however, I thought X11 was for GUI based components? either way that made no difference either.. 

I know when you open a console via SSH its "XTERM" and when you login at the host directly, the terminal is "LINUX"... been pondering that as well...

---

### Post by robgr85 on 2011-08-16
> **asomad said:**
> That sounded like a really worthwhile idea. I thought that could be the trick. Unfortunately it made no difference, at least for sound, lol. but thanks for the idea! 

Ive also tried it with X11  forwarded. I am a noob however, I thought X11 was for GUI based components? either way that made no difference either.. 

I know when you open a console via SSH its "XTERM" and when you login at the host directly, the terminal is "LINUX"... been pondering that as well...

If You will manage to find solution to Your problem, please post it here :)

---

### Post by YesWeCan on 2011-08-17
Can you get any program to play sound on the sever, for example, 'play something.wav'?

---

### Post by papibe on 2011-08-17
I gave this a try, but I couldn't even get mp3blaster running locally.

On the other hand, I had success with cmus (it required some tweaking). Now, cmus works locally on the server, and remotely over a ssh connection. There's no special settings for the last one.

Any way, I'm going to give mp3blaster another chance and I'll get back to you.

Regards.

---

### Post by papibe on 2011-08-17
My results:
[LIST]
[*][mp3blaster]("http://mp3blaster.sourceforge.net/") doesn't seem to be a very "live" project (check their site and forums).
[*]Although it should support alsa, apparently the version in the repos does not (see this couple of bugs: [Bug #752091]("https://bugs.launchpad.net/ubuntu/+source/mp3blaster/+bug/752091") and [Bug #686260]("https://bugs.launchpad.net/ubuntu/+source/mp3blaster/+bug/686260")).

[*]To make it work I found 2 alternatives:
[LIST]
[*]Compile it from source (enabling support for sdl), or
[*]Install, setup and use OSS instead of ALSA.
[/LIST]
[/LIST]
At this point, I would recommend using a different player from a 'active' project like [cmus]("http://cmus.sourceforge.net/") or [moc]("http://moc.daper.net/").

Regards.

---

### Post by asomad on 2011-08-18
> **YesWeCan said:**
> Can you get any program to play sound on the sever, for example, 'play something.wav'?

If I'm at the servers keyboard and monitor, yes I have sound. No problems with sound....
Can I get any sound out of the servers audio, through a SSH connected terminal? Good question, Ill try to "play something.wav" but I'll put my money on NO, because its SSH. lol

My issue is that the program does not work the same when i'm running it through a SSH remote terminal. Via ssh, the program will just simply say "failed to load audio device" when you attempt to play a track.

Also for me, mp3blaster works, lol (and might I add, nice rich sound) which doesnt seem to be the case for most people..

I feel that there should be a way to "trick" either the program, or the server itself, into treating the SSH terminal as if it were a true local login, and thus ANY program would run the same through an SSH connection, as if I were local or "at the server". 

Maybe Openssh does not allow a terminal being run though it access to sound? or allow the same permissions available locally to SSH?

Either way, I guess it'l be simpler to find a program that will run through SSH, and still spit sound out of the server's minijack.

thanks for the replies and ideas!

---

### Post by asomad on 2011-08-18
> **papibe said:**
> My results:
[LIST]
[*][mp3blaster]("http://mp3blaster.sourceforge.net/") doesn't seem to be a very "live" project (check their site and forums).
[*]Although it should support alsa, apparently the version in the repos does not (see this couple of bugs: [Bug #752091]("https://bugs.launchpad.net/ubuntu/+source/mp3blaster/+bug/752091") and [Bug #686260]("https://bugs.launchpad.net/ubuntu/+source/mp3blaster/+bug/686260")).
[*]To make it work I found 2 alternatives:
[LIST]
[*]Compile it from source (enabling support for sdl), or
[*]Install, setup and use OSS instead of ALSA.
[/LIST]
 
[/LIST]
At this point, I would recommend using a different player from a 'active' project like [cmus]("http://cmus.sourceforge.net/") or [moc]("http://moc.daper.net/").

Regards.

makes sense.

---

### Post by asomad on 2011-08-18
whats the fun in doing things the easy way. lol. It doesn't seem right if there's not 3-4 computers being used, 

(share servers, ubuntu servers, laptop(s), and of course network media players, that's how we roll, see why I dove into linux?)  :-)

---

### Post by YesWeCan on 2011-08-18
> **asomad said:**
> Good question, Ill try to "play something.wav" but I'll put my money on NO, because its SSH. lol

My issue is that the program does not work the same when i'm running it through a SSH remote terminal. Via ssh, the program will just simply say "failed to load audio device" when you attempt to play a track.
So I installed sox and SSH'ed to a remote server from which I SSH'ed back again and played a .ogg file. The sound emerged here. So I am wondering whether it is a problem specific to mp3blaster or not. I've downloaded mp3blaster and I can't make it play locally! It says it failed to open sound device. Website not helpful.

---

### Post by asomad on 2011-08-18
> **YesWeCan said:**
> So I installed sox and SSH'ed to a remote server from which I SSH'ed back again and played a .ogg file. The sound emerged here. So I am wondering whether it is a problem specific to mp3blaster or not. I've downloaded mp3blaster and I can't make it play locally! It says it failed to open sound device. Website not helpful.

Well that's good news, if I read right, you got your sound to emerge from the host and not the client... 

I expected when I do get something working through an SSH terminal, It will "want" to play the audio at the clients terminal... I'm glad there's hope it will work how I want, and act the same as if I were at the hosts terminal...

---

### Post by asomad on 2011-08-23
so, Ive installed sox, now im just trying to get it to work with MP3.... blah. Ive added both the libmad0 package AND libmp3lame0 packages, which should be whats needed for it to play an mp3. But it still says "no handler for file extension".... Any's I guess im gonna find a wav file and go put it in my music folder, so I have something to test the sound output with

---

### Post by asomad on 2011-08-23
Ok, so using sox, AND mp3blaster. (the issue wasnt the software, the issue was something missing when I log in via ssh, that gets loaded when I log in locally.) I can get sound out of my sever, from an SSH connection. BUT, I have to be LOGGED in to a session at the server, in addition to the SSH terminal.....

How can I get audio to work through SSH without being logged into the server locally as well.... There's something im missing here..

'cause once i'm logged into a local terminal, my ssh connection does what I wanted all along. I just dont want to have to go to the server and log in there also, when I want to use a SSH connection...

---

### Post by asomad on 2011-08-23
OK, so I have verified my problems are in fact due to something with the sound not being enabled on the server, unless i'm logged in locally, AS I SUSPECTED FROM THE GET GO. 

as long as im logged in to the server locally, my ssh login can play sound. But I dont want to have to go log into the server everytime i turn it on, Id like my SSH log in to do everything a local log in does...

so those of you blaming my software, are missing the issue entirely. it has to do with something not being loaded when you log in SSH, but is loaded once you log in to the server locally.

If im not logged into a session at the server, the software cannot access the sound on the server. How can i get around this?

---

### Post by asomad on 2011-08-23
Or alternatively, maybe I can setup the server to Auto-login when it's started? Id rather leave the local terminal locked and not logged in to. But if I have to, we could do it this way....

---

### Post by volkswagner on 2011-08-23
This is beyond my skill set.  But I'm real good at mentioning the obvious.

Have you checked the ssh man pages? There is an enormous number of switches you can use.  In particular -t or -T looked somewhat promising.

I'm also curious how the mp3 player behaves when using screen.  If you can't get any native ssh switches to give you the outcome, perhaps using [screen]("https://help.ubuntu.com/community/Screen") may be a better workaround than having auto login.

Try logging in locally, run your mp3 player in a screen session, detach the screen session and log out.  If your mp3 keeps playing perhaps you can just remote ssh and reattach your screen session.

:guitar:

---

### Post by asomad on 2011-08-23
> **volkswagner said:**
> This is beyond my skill set.  But I'm real good at mentioning the obvious.



The obvious NEVER hurt a n00b! I appreciate any input, because YES I think this lil problem of mine should be absolutely solvable with something like a switch.....((((if it is, how can I apply a "switch" when I connect from putty in widows, I have ubuntu and ssh from that through gnome terminal primarily, but I also use putty in windows.... lol))))
Anyways, I have read extensive amounts of text in the man files for not just ssh but everything else I could think of.

I believe it wil be something as simple as a switch, or maybe edit my .bashrc to force the server to load whatever isn't being loaded, that does load once I log in locally. blah get all that? i'm tongue twisted here lol

Im sure when I log in locally, some or maybe "THE" sound device is loaded.? (noob)
Need to force that to load, when I log in via ssh.....

 It would be a nifty and simple solution, to add one line of code to the .bashrc to do this. hmmm. It's hard knowing so little about something (linux) and knowing so much about how "everything" works. (except that would be forcing "whatever it is" to load twice when I log in locally..?..) 

So maybe not .bashrc.... **what else is loaded upon log in to terminal locally, or remotely, i**.e. when bash fires up. a local bash session enables the sound. a remote bash session doesn't do that by itself. what gives.

---

### Post by asomad on 2011-08-23
[B]Lets simply this whole thing.....

An edit to sshd_config should absolutely be the answer.[/B]

I don't want to cross post... but this this thread is a messy mess of thoughts. maybe i should start a thread called editing ssh(d)_config to load sound..... I'm going to read more, and learn. That's half the fun.

---

### Post by awi on 2011-08-23
I use mplayer to do exactly what you are trying to acomplish. I log into my server with big speakers, and play shuffle files with these command line:

```
find /media/usb-drive/Music/mp3 -print0 | xargs -0 mplayer -shuffle
```

O just simply

```
mplayer file1.mp3 file2.mp3 
```

Install mplayer package and that should be enough.

---

### Post by asomad on 2011-08-23
> **awi said:**
> I use mplayer to do exactly what you are trying to acomplish. I log into my server with big speakers, and play shuffle files with these command line:

```
find /media/usb-drive/Music/mp3 -print0 | xargs -0 mplayer -shuffle
```O just simply

```
mplayer file1.mp3 file2.mp3 
```Install mplayer package and that should be enough.


The software being used is not the issue in my case. It's something with the setup Ubuntu or SSHD itself, where the audio device is UNavailabe to ANY software via ssh UNTIL there is a local login at the server. No sound from anything through SSH until I'm at least logged in, at the server.

It doesn't matter if the makers of linux themselves came down from above and gave me a magic music player.... If there's no access to the sound device, it wont work. I have working audio programs, lots of em now. LOL. That's how I know, I dont have sound through an SSH connection, UNLESS the server has a LOCAL bash session active.

---

### Post by asomad on 2011-08-25
I can elaborate further here.. SSH connection cannot load sound, until the server has a local bash login active. 

With a local login active at the server, I can then use ssh to play audio at the server.(regardless of program used)

Even in the middle of playing a track, If the local login at the server is logged out, the audio ceases, STOPS, quits. (various errors or no error depending on program being used for playback). 

So. It's simple. No audio via SSH, unless a local login is active simultaniously

I guess I have to make the server auto-login, to avoid this issue, but that is not the route I wanted to go... I really wanted to have audio work through SSH, without the server being logged into locally... (I'd like to ditch it's monitor entirely eventually)

---

### Post by volkswagner on 2011-08-25
Did you try the screen approach?

There are also alternatives to using a command line player.  Have you considered running an mpd server?  It is fairly simple to setup and you can use clients on your iPod, MS Windows, Mac, and of course Linux.  MPD is also lightweight so it should not impact server performance.

Obviously it would be nice to figure out how to get sound working without a login.  Perhaps just running an mpd daemon would help.

---

### Post by asomad on 2011-08-25
> **volkswagner said:**
> Did you try the screen approach?

There are also alternatives to using a command line player.  Have you considered running an mpd server?  It is fairly simple to setup and you can use clients on your iPod, MS Windows, Mac, and of course Linux.  MPD is also lightweight so it should not impact server performance.m

Obviously it would be nice to figure out how to get sound working without a login.  Perhaps just running an mpd daemon would help.

Even damonizing pulseaudio did nothing to allow the sound on the server to function before a local login was active.....

Im wondering if it's maybe something with upstart or even gdm. Which are part of my ubunu install, however gdm is set to not start until runlevel [3] so that X is not loaded by default.... Im wondering if maybe I get rid of the front end altogether, i.e. apt-get remove gdm, maybe then whatever is happening here will stop, and I can have access to the sound with ONLY the remote login to the server.

---

### Post by asomad on 2011-08-25
> **volkswagner said:**
> Did you try the screen approach?


ummmmm....... "Screen" is for switching between OPEN terminals...correct?.. If I log into the server via SSH, that login is the only active terminal.... So there's no screen to switch to.....

Now if I log into a local session at the server, Then yes I can use screen and access THAT terminal.

But That does nothing for me, because as soon as a local login is active at the server, I have access to sound from my SSH'ed terminal anyways. 

I need to have sound work, with ONLY the SSH session logged in. The server needs to sit at it's login, I do NOT want to have to login to a session at the server to have access to the server's sound from my ssh terminal.

---

### Post by asomad on 2011-08-25
> **volkswagner said:**
> There are also alternatives to using a command line player.  Have you considered running an mpd server?  It is fairly simple to setup and you can use clients on your iPod, MS Windows, Mac, and of course Linux.  MPD is also lightweight so it should not impact server performance.



Um, if there is no access to audio without the server being logged into at a local session, what does it matter what programs i use? NO PROGRAMS HAVE ANY ACCESS TO AUDIO.

 UNLESS THE SERVER HAS A LOCAL LOGIN ACTIVE (AT IT"S MONITOR AND KEYBOARD)


Im not going to spend another month trying a hundred more programs, just to keep finding out, that my server wont allow ANY program access to it's audio unless there is a LOCAL login active.

---

### Post by volkswagner on 2011-08-25
Don't get excited...:lolflag:

I was so interested in this topic I tried to get it working on my setup.  Things like this make for a better linux user.


I understand about not wanting/needing a local login, especially since you mention eventually ditching your screen and keyboard at the server.

As far as I can tell it is not a GDM issue.  

You are incorrect about using MPD.

My setup is 10.04 server running headless, even ditched the AGP video card!  I have both MPD and Mediatomb running without issue.  I can play songs at the server using my iPod, Ubuntu laptop, and Windows clients.  I have an old ez-stream wireless device that can connect to any UPnP/DLNA server, so that was the main reason for Mediatomb.

I did install mp3blaster on my server.  I was not able to successfully play sound.  The error I get is "Failed to open sound device".  I did notice needing to run mp3blaster as root for it to see the mixer in bottom right of screen.  Once adding myself to the audio group I no longer needed to run it as root to see the mixer settings.  However after many attempts to get the sound device loaded, I gave up.

I do believe you will have great joy installing a server type media player.  The list is exhaustive.  Here are a few suggestions.

MPD, MediaTomb, Ampache, Jinzora, I believe even VLC has a server/client setup.

If your library is on the large side, or your server is lacking resources, I suggest a solution using a real database backend, as both mediatomb and MPD can be cludgy for updating and initiating the library/database since it is just a flat file.


*************** Hold The Phone ****************

I think I got it.  I tried so many combinations after adding myself to the audio group.  The one thing I did not try is running mp3blaster with no arguments (I was always specifying the audio device). 

I'm not sure if you will need to restart or log out login after adding yourself to the audio group.  A simple test before adding yourself to the audio group is run mp3blaster as root.

If your not sure how to add yourself to a group.

one way:
```
sudo usermod -a -G audio yourusername
```

Again simply log out then log back in.  Check to see if you are part of the group.

```
groups
```

Hope it works for you.

PS: The only groups MPD was part of were 'audio' and 'myusername'!

:guitar:

:guitar:

---

### Post by asomad on 2011-08-25
let me start with "I like media tomb"....... :-)
we run a rather large server thats not mine, but is the reason I started moving on to linux....

anyways. im wondering if you have tried another audio player besides mp3blaster. because no one has been able to get that one to work, not even locally in most cases lol. so its a horrible example of how to re-create this issue....

Anyways. Ill try adding myself to the audio group.. but last night I tried adding myself to "pulseaudio" groups when i tried running pulseaudio daemonized.. with no difference in end result. audio with local login, no audio without a local login.

well see what happens Ill update shortly, going to try a couple things

---

### Post by asomad on 2011-08-25
NOW ITS TIME TO GET EXCITED!!!!!

cause you sir, I OWE you one!

adding my username to group "audio" was all it took!

Now I can access the servers sound, via SSH, without a local login active.

thats it. no fancy configuration, no adding to pulseaudio.... I had my nose on it last night, looked at pulseaudio, but not audio. always overlook the obvious huh.... lol.     it was THAT SIMPLE.

THANKS SIR

[SOLVED]

---

