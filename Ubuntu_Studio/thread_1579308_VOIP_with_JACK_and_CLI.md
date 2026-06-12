---
title: "VOIP with JACK and CLI?"
date: 2010-09-21
forum: Ubuntu Studio
---

### Post by Quirq on 2010-09-21
Hello

A friend and I would like to be able to use VOIP as we live in different countries and phone calls are cumbersome as well as expensive: besides just chatting, we collaborate musically and emails just aren't cutting it any more!

So far we haven't been able to find a solution as there are two prerequisites that must be met:
1. it must be usable from the command line, with *no gui whatsoever*
2. it must be usable with JACK

The reasons for this are that my friend is blind and runs a headless system -- it would be a major pain (and he doesn't really have the resources) to install a window manager, just to be able to run a VOIP app. He also has JACK running all the time and can't run without it. He's actually running Debian, but I run Ubuntu Studio.

There are a couple of other criteria which are by no means essential but it would be cool if they could be met as well. It would be nice if I could run something with a GUI at my end because I like my eye candy, so either we'd run different clients or it would be one with GUI and CLI versions. It would be nice if it had very good audio quality and low latency so we could play ideas to each other (I'm not talking about jamming simultaneously) and hear them reasonably well and also have a conversation without it being difficult. The sound quality isn't really that important, it'd just be nice to just have the V in VOIP and be able to chat.

It would be nice if there was a single app that would do it, but if there's a way of doing it that requires more than one, even that would be fine -- this evening he's managed to pipe audio to an Ogg stream and broadcast to me using Icecast, but the latency is of the order of seconds, so conversations wouldn't be easy although the sound quality was good.

So, is it possible to do what we want to do? So far, everything we've  found seems to either support JACK or is usable from the command line,  but not both. I wasn't entirely sure where to ask, but given that lack of JACK support is a deal-breaker, I thought here might be best.

Thanks in advance

Quirq

---

### Post by sheehanje on 2010-09-21
I believe what you are looking for is netjack...  It's not VoIP per say, but it would allow you to talk by simply having your friend connect a microphone to jack, and transport it to you...  
 
The concept is fairly straight forward, you would setup jack one your end with whatever driver you need (ALSA, Firewire, etc), a   This would assume he has either a straight IP address on the net, or something with proper PAT setup....
 
You would first start jackd anyway you needed to (through the GUI or command line, then with whatever driver you need, like alsa, firewire, etc.)
His command would be similar to:
 
jackd -r -d net -o 2 -i 2
 
That will give two outputs, two inputs...
 
Once his end is setup, you can then connect your system to his slave:
 
jack_netsource -H hostname 
 
Once the connection is made, you will view his device like any other instrument/device that shows up in jack...  Connect it how you need, I prefer patchage.
 
There is a decent guide [here]("http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack").  The man page for jack_netsource is fairly informative too.
 
I'm not sure if that is the latest and greatest documentation, but it worked for me...

---

### Post by Quirq on 2010-09-22
Many thanks for your response.

My friend had looked into netjack but had ruled it out for some reason, I'm not sure why. However, he now thinks netjack is going to be the way to go, so it's nice to know from someone's actual practical experience that it will work! 

Thanks for the link as well, it looks like it should be useful. I think it's going to take a little bit of getting used to (for me anyway :-) he's used to using JACK and stuff like that from the command line), but I'm sure that after a bit it will become second nature.

Thanks again :-)

---

### Post by kayosiii on 2010-09-24
Have a look at the recent editions of the open source musicians podcast they managed to hook something up using mumble I think.

---

### Post by Quirq on 2010-09-28
Thanks kayosiii. I found the podcast you referred to, I think it's number 43 IIRC.

I'd come across Mumble and Murmur before in my travels, but had written it off because of lack of JACK support, but now that it has it it'll be something else to look into.

We're still playing with netjack at the moment, trying to sort out problems with ports, but I don't think they're insurmountable.

Thanks again :)

---

