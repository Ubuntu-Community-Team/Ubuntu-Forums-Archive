---
title: "jackd on a remote host ?"
date: 2009-09-15
forum: Ubuntu Studio
---

### Post by MisterBark on 2009-09-15
Hi ! ;)
 
My question is very simple :
 
**Is there a way to control a jackd server running on a remote host ?**
 
 
I'm working on a multi computer configuration like this :
 
- 4 PCs running LinuxSampler (which can be controlled remotely)
  there will be jackd on each computer
 
- A main PC running midi sequencer with midi data sent to the 4 others PCs (via external soundcards)
  by running 4 qsampler process, I can control each LinuxSampler remotely, from the main PC
  but I also would like to control the jackd process of each PC, i.e. with 4 qjackctl
 
NOTE: I'm not talking about midi or audio through the net, just controlling the remote jackd processes.
 
If I can't do that, I will be forced to open 4 ssh connections, and use jackd in command line... not really handy when creating connections...
(because I won't use any graphic on these 4 PCs, no need to use precious memory for nothing...)
 
Anyone heard talking about this for jackd ?
Or, if it doesn't exist, another way could be to create a sort of tunneling between the main PC, and each 4 samplers, then, i.e., I could configure qjackctl to use the binary "jackd-remote1", etc. but is there a way to make it working like this ?
 
Thanks a lot in advance ! :)

**SOLVED: solution given page 2**

---

### Post by Stochastic on 2009-09-15
Hmm, at first I thought you were looking for something similar to netjack (which might still be useful to you, so you may want to take a look at [http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack](http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack) ).

But I think all you're asking for is a means to adjust connections on a remote computer.  Since you mentioned GUI is only going to be run on the controlling computer, you probably want to run an ssh terminal and do ```
jack_lsp
``` to list all jack ports, then ```
jack_connect sourceport destinationport
``` to connect an output sourceport to an input destinationport, then ```
jack_disconnect sourceport destinationport
``` to undo the connection.

If that's the gold you were looking for, then this e-mail might be some extra platinum rims for you command line endeavours: [http://lalists.stanford.edu/lau/2007/10/0203.html](http://lalists.stanford.edu/lau/2007/10/0203.html)

Edit: This page has lots of useful features of the jack server [http://orford.org/assets/jack.php](http://orford.org/assets/jack.php)

Hope that helps.

---

### Post by MisterBark on 2009-09-15
Thanks a lot for your answer ! :)
Your links are very interesting, especially the last one :D

You're right, netjack is not what I'm looking for.
In fact, what I want is :

**Controlling jackd remotely with qjackctl exactly as I can control linuxsampler with qsampler.**

But linuxsampler has its own net protocol to do that.
I would like to have on my main PC:

**qsampler 1** : controlling the linuxsampler process running on the remote PC 1 to load soundbanks etc. Easy to do with the linuxsampler protocol, it's a feature of qsampler: enter the ip:port of the computer running linuxsampler. In fact, it's more than a feature, it's just how the linuxsampler daemon is controled. By default, the configuration in qsampler is "127.0.0.1:8888".
**qjackctl 1** : controlling the PC 1 jackd

**qsampler 2** .... on PC 2
**qjackctl 2** ....

 **qsampler 3** ....
 **qjackctl 3** ....
 
etc.

Then, the data transmitted over the net is just a protocol data to control the remote processes.

So, ok, jack_lsp + jack_connect and jack_disconnect is a solution, but not really handy because I can't use qjackctl i.e. to easyly see if there was a xrun, or create a connection by a simple mouse click. I have to open a lot of terminals and check them every 5 minutes...

Then, have you got an idea to do it with qjackctl ?

THANKS :D

---

### Post by Stochastic on 2009-09-17
> **MisterBark said:**
> So, ok, jack_lsp + jack_connect and jack_disconnect is a solution, but not really handy because I can't use qjackctl i.e. to easyly see if there was a xrun, or create a connection by a simple mouse click. I have to open a lot of terminals and check them every 5 minutes...

Then, have you got an idea to do it with qjackctl ?

Doing it with qjackctl, jack-panel, or any other GUI jack interface that I've heard of would most likely require a major rewrite of the GUI's code.  It probably could be done (modifying them to allow ssh connections for a remote underlying host), but it's probably not about to get done anytime soon.

Really what's so hard about opening four short terminals (for watching xruns on your jackd launch), and one terminal with four tabs (for connecting/disconnecting jack aware apps).  I've attached a screenshot of how I would run this.  Then just put that on one workspace.  You could even script up some bash to trigger an event if any lines beginning in XRUN come across your terminals...

But your setup has me intrigued.  What exactly are you building, or how is it you're using this system of synths?

---

### Post by madeinfamous on 2009-09-17
allo MisterBark, Stochastic

*"But your setup has me intrigued. What exactly are you building, or how is it you're using this system of synths"*

moi aussi j'aimerais savoir :)

---

### Post by MisterBark on 2009-09-17
haha lol
[Stochastic]("http://ubuntuforums.org/member.php?u=87541"): thanks for your screenshot and your answer

[madeinfamous]("http://ubuntuforums.org/member.php?u=741709"): d'accord je vais vous expliquer ;)
(ok, I'm gonna explain you)

So, first, finnaly it's gonna by 8 pc, then it means 16 terminals...
I'm working on doing a big LinuxSampler configuration because I'm preparing a film music album for the next year.
It's really orchestral, with many instruments and I really want an amazing beautiful sound, then I use a lot of huge gig soundbanks.
Each PC will have 4GB of ram.
I could do 2 PCs of 16GB but after thinking a lot about that, I think it's more safe to have 8 small PCs than 2 big ones, for many reasons. (and only 33% more expensive)
Each PC will have 2 midi input ports (midisport 2x2), and 1 ADAT output (RME)
So, the main PC running a midi sequencer (i.e. ardour 3), has 2 midisport 8x8 (so 16 midi output ports, 256 channels), send each 16 ports to each 8 LinuxSampler PC (2 ports each, 32 channels each) - i.e. the PC1 could be the violons, the PC2 Cellos and Contrabasses, etc.
After that, all the 8 ADAT from the 8 LinuxSampler PCs goes into a mixing console (Tascam DM-4800)
The DM-4800 makes the automation, with MTC (MidiTimeCode) from the ardour, and sends FX-sends to a Reverb PC (1 ADAT, then 4 stereo reverbs)
Finnaly, 8 buses (4 stereo) are going out from the DM-4800 without reverb in to a Soundcraft M12, and also 8 channels from the reverb PC (the 4 stereo reverbs) => this is where the DA convertion takes place (Apogee DA16, to convert the 2 ADAT ports)
Then, I can insert here extra analog racks (tube compressors, etc) and bounce it on the mix bus of the SoundCraft analog console with a Rosetta 200.
Here we are, you know alsmot everything about what I plan to do ;)
 
[B]So, I've got a question:
How to connect midi using jack_connect ? ....[/B]
because, that's right, if there's absolutely no solution to use qjackctl remotely, I'm gonna use 16 erminals...
.... and I know how to connect audio ports in jack in console mode, but what about the 2 midi ports ? (I have to connect them from midisport 2x2 inputs, to LinuxSampler)...

THANKS ! :D

---

### Post by madeinfamous on 2009-09-17
thx for the explanations,

i wish you luck, sorry i cant provide you with help,

hope to see your project around,

i'll put you in my friend list, so in time it will be more easy to find more about your project,

merci encore, et je te souhaite le mot de Cambronne :)

---

### Post by Stochastic on 2009-09-17
Tabernac!  Sorry to be a damper on Québécois culture (Gilles Duceppe would be proud of you both), but I need to give you both a friendly heads up that English is the only language allowed in the main sections of these forums.  Québécois is allowed to be spoken/typed in the [Quebec LoCo section]("http://ubuntuforums.org/forumdisplay.php?f=375"). In any case, the project sounds very impressive and I'd love to hear the final result.

Back to the issue at hand, it depends on which MIDI protocol you're using.  The newer Jack MIDI protocol (which hasn't yet been widely adopted) will be listed in jack_lsp and can be connected/disconnected using jack_connect/disconnect.  The older ALSA-sequencer MIDI protocol (which is the most commonly used) requires the use of aconnect.  To list the input ports do ```
aconnect -i -l
``` to list the output ports do ```
aconnect -o -l
``` and to quote from it's man page >        aconnect  is  a utility to connect and disconnect two existing ports on
       ALSA sequencer system.  The ports with the arbitrary subscription  per&#8208;
       mission, such as created by aseqview(1), can be connected to any (MIDI)
       device ports using aconnect.  For example, to connect from port 64:0 to
       65:0, run as follows:

           % aconnect 64:0 65:0

       The connection is one-way, and the whole data to the sender port (64:0)
       is redirected to the receiver port (65:0).   When  another  port  (e.g.
       65:1)  is  attached  to  the same sender port, the data is sent to both
       receiver ports.  For disconnection, use -d option.

       % aconnect -d 64:0 65:0

       The address can be given using the client's name.

       % aconnect External:0 Emu8000:1

       Then the port 0 of the client matching with the  string  "External"  is
       connected to the port 1 of the client matching with the "Emu8000".


Oh, and to remove all alsa midi connections do: aconnect -x

---

### Post by MisterBark on 2009-09-17
OMG ! :) it's great !
thanks a lot for your answer :D
I'll try it right now :)

PS: hope you won't take it as a spam... but if you're interested by the result, visit this website in a few months / 1 year: [http://www.ObjectiveBeauty.com](http://www.ObjectiveBeauty.com)
for now it's a temp page just to explain quickly, but the final website of the album will be really big, with a preview section to listen extracts, and also games to win the album in free download (1 winner a day: the one who brings the most visitors in 24h ;) lol)
there will be also a making of video, including computer & hardware demos/explainations... (with a promo for linux by the way lol)

---

### Post by MisterBark on 2009-09-19
Hi,

I've created a diagram to show the configuration that I plan to do.
I insert the image below, which is here : [http://images.mrbark.fr/mrbark-studio-diagram.jpg](http://images.mrbark.fr/mrbark-studio-diagram.jpg)
 
Any ideas are welcome !
*EDIT: I've updated the graphic around the Presonus Central Station*

[IMG]http://images.mrbark.fr/mrbark-studio-diagram.jpg[/IMG]

---

### Post by raboofje on 2009-09-20
Wow, that is an impressive-looking setup. So you're recording everything at once?

Wouldn't it be easier to just record one track at a time, then combine the tracks finally? Or am I being simplistic? :)

> **Stochastic said:**
> Doing it with qjackctl, jack-panel, or any other GUI jack interface that I've heard of would most likely require a major rewrite of the GUI's code.

Uh, doesn't X allow you to do just that?

```
raboof@mainpc$ ssh -X samplerpc1
Password: 
raboof@samplerpc1$ qjackctl

```

This should start qjackctl on samplerpc1, but show its GUI on mainpc.

---

### Post by MisterBark on 2009-09-20
> **raboofje said:**
> Wow, that is an impressive-looking setup. So you're recording everything at once?

Wouldn't it be easier to just record one track at a time, then combine the tracks finally? Or am I being simplistic? :)

Yes, everything in real time, in only one chain.
I can't do it track by track because you have absolutely no idea of the final result, and also because you add more and more conversions...
What I plan to do for the violins i.e. is mixing something like 4 or 5 different banks to have a really FULL sound.
You really can't do it track by track ! (and what about the buses ?)

> **raboofje said:**
> 
```
raboof@mainpc$ ssh -X samplerpc1
Password: 
raboof@samplerpc1$ qjackctl

```This should start qjackctl on samplerpc1, but show its GUI on mainpc.

OMG ? really ???
I'm gonna try it now !

---

### Post by MisterBark on 2009-09-20
OMG ! yes it works !!! :)

(I forgot the -X lol then I edited this post)

WAH fantastic ! that's exactly what I want !!!!
THANK YOU SO MUCH !!!! :D

**########## SOLVED ##########**
**########## SOLVED ##########**
[B]
the solution is running [ssh -X] on the remote computer,
then, start qjackctl and the X GUI will be forwarded to the remote pc :)
[/B]
**########## SOLVED ##########**
**########## SOLVED ##########**

---

### Post by Stochastic on 2009-09-21
> **raboofje said:**
> Uh, doesn't X allow you to do just that?

```
raboof@mainpc$ ssh -X samplerpc1
Password: 
raboof@samplerpc1$ qjackctl

```

This should start qjackctl on samplerpc1, but show its GUI on mainpc.

But this method does require the host PC to have X running (or it will start X running when it executes).  The original post didn't want the excess overhead of X on the host machines IIRC.

Yeah, > **MisterBark said:**
> (because I won't use any graphic on these 4 PCs, no need to use precious memory for nothing...)

---

### Post by MisterBark on 2009-09-21
> **Stochastic said:**
> But this method does require the host PC to have X running (or it will start X running when it executes).  The original post didn't want the excess overhead of X on the host machines IIRC.

Oh no !!!!!! :(
really ???

---

### Post by thorgal on 2009-09-21
the remote host does not need X, only the machine from where you 'ssh -X'. I have a non-X mythtv-backend server that I sometimes access remotely in the same way from my laptop (which runs X).

---

### Post by raboofje on 2009-09-21
> **Stochastic said:**
> But this method does require the host PC to have X running (or it will start X running when it executes).  The original post didn't want the excess overhead of X on the host machines IIRC.

Well, it will of course load a couple of X-related libraries, so there's *some* overhead, but it won't need to start all of X.

---

### Post by MisterBark on 2009-09-21
Ok, great, so I just have to install X, but not running it ? :)

---

