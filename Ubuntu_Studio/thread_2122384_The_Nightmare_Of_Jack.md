---
title: "The Nightmare Of Jack"
date: 2013-03-05
forum: Ubuntu Studio
---

### Post by martylux on 2013-03-05
Please help me to use Studio. I just bought a nice new machine with the hopes of recording music and now all I will have time for is wrestling with JACK.
How can a piece of software be so temperamental and still be included in an OS that is supposed to be user-friendly?!?
I get Audacity working and then I get Guitarix working and then Audacity is broken; or I get Rakarrack working and then use Ardor and then Rakarrack won't work anymore...
It's just one headache after another.

Can anyone please let me know if there's a way past this horrible minefield of waiting for the right phase of the moon and standing on one foot and holding my mouth just so in hopes that at least ONE app will deliver SOME audio???
I'm at my wit' end (or half-way) :)

---

### Post by jejeman on 2013-03-05
>  How can a piece of software be so temperamental and still be included in an OS that is supposed to be user-friendly?!?There is no such thing as "user friendly". You need to learn to use the software. "User firendly" is a marketing term. "User frendlines" is highly and completly individual.

I really don't know how to help with JACK issues. You need to be patient, read and search a lot. I took me couple of years to have almost rock steady audio producion workflow.

Audacity is tricky to use with JACK.

I don't know what is your level of audio/software knowledge, maybe you need to start from the begining
[http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)

Sorry for not being of much help, just hang in there.
If you can give more detailed description of your problems, maybe I can help more. It is not clear are applications crashing or what. Also you didn't give us your JACK settings, or any real input for solving the problem.
Also, what is your PC specification: CPU RAM.

---

### Post by falskmyntarn on 2013-03-05
+1 for jejeman's post - i agree that it's confusing and frustrating and noone really likes to read manuals, right? I had the same issues with Jack and still haven't solved them all, but for me it's a matter of trying - reading - trying. also, if it's any comfort, audio configuration on Windows with external soundcard and Logic is no walk in the park either :)
hang in there!

---

### Post by Splashmania on 2013-03-11
> How can a piece of software be so temperamental and still be included in an OS that is supposed to be user-friendly?!?
I think he have reason the sistem to make music in linux is unusable in a production set.
no way to make music comfortable.
the system is powerfull but is not practic
and the expression is correct. is not user-friendly

---

### Post by CraigPid on 2013-03-11
I'm sorry but I don't think using Jack is that hard.Once you understand what it actually is.When I 1st got a pc I was trying to use cakewalk pro audio 9.I didn't even realize I could plug a guitar in & record it.I was writing notes on a midi staff with the mouse to make music.It took quite a long time to realize the full depth of the program.If you're coming from a different OS then Linux is really like learning to use a computer all over again.It's no more user unfriendly than any system.If you've been working with something for 10 years of course it's going to seem more user friendly.
  Craig

---

### Post by Splashmania on 2013-03-12
> I'm sorry but I don't think using Jack is that hard
Yes it is. 
To  make music i dont care wich sound server is working, i just want it running,  why we have two sound servers?? one less powerfull?? choose the better  one and remove the other, and then build the rest of the sound arround.

> Once you understand what it actually is
Yes, because I understand

> When I 1st got a pc I was trying to use cakewalk pro audio 9.I didn't  even realize I could plug a guitar in & record it.I was writing  notes on a midi staff with the mouse to make music.It took quite a long  time to realize the full depth of the program.If you're coming from a  different OS then Linux is really like learning to use a computer all  over again.It's no more user unfriendly than any system.If you've been  working with something for 10 years of course it's going to seem more  user friendly.
  Craig
Sorry but no. 
I am trying it with linux for a long time and i know how it works, but thats not practice to make music with. i' m telling you 
i want all my plugins working inside my host (what must be sincroniced with my gear by midi of course). Its a point have them outside of the host easy but must be in the other way and easy!!
that will be easy

---

### Post by CraigPid on 2013-03-12
I'd be willing to concede that music production in Linux is not really feasible in a professional environment at this time.I think most people here though are hobbyists.We are doing important work towards breaking the stranglehold that corporate monoliths have over our computers.We've convinced ourselves that we have to have the best software even though something that comes at little or no cost would accomplish what we need.So therefore we pirate Photoshop,Pro Tools etc. My father-in-law is going to be teaching Adobe CS6 Suite & Pro Tools among other stuff in a high school course.He admits that those kids will just pirate the software.So if the get a job in a related industry they will have a leg up but if there's no education in open source alternatives then the industries will be forever beholden to the Adobes & Apples of the software world.As for the kids who just use the software for personal use ,they will have to pay hundreds or thousands of dollars or hope that they will be able to continue pirating photoshop or pro tools because it's the only thing that they know & it's "too hard" to learn something new.
I can understand if you are doing music production in tv or movies or a pro studio you need a very steamlined workflow . What I gather from your post is that you want to use a soft synth or effect that you can't use as an inline plugin so you have to start the syntn & open the jack connections window & make the cable connections.So you're saying that it's easy to right click in the patch point in the mixer strip,browse for a plugin,select it & the double click on it to open the interface but it's too hard to click a synth to start it, open the jack connections window & make a few clicks in there to connect the cables.So it seems to me that you're saying that moving your index finger 1 millimetre 4 times is easy but doing it 6 times is too hard.
Craig

---

### Post by Splashmania on 2013-03-12
nope what i am saying is if i want use a sinth inside a project and there is a button to add a synth it should work, not turn around all the system (what you must know how) to use it.
I think is clear
and i think that programs are to make music not to make history, maybe if they can make music they can make history
Splash

---

### Post by CraigPid on 2013-03-12
I think there's a bit of a lack of communication here because of a language barrier. I'm sorry if I come across as disrespecting you.I tend to get riled up about the lack of freedom in software.Everyone has their own reasons for the way they do things. So keep on making the music.
  Craig

---

### Post by Splashmania on 2013-03-12
a bit of order and simply then get all the free what you want

---

### Post by jnbek on 2013-03-19
JACK is a bit temperamental there's no denying this, but if you use qjackctl; which comes with Ubu Studio, then most of your problems go away... Sure you might have to connect a system plug to an effects rack then plug the effects rack into Ardour what not... with QJackCtl all of this is sooooo much easier, if your App is JACK aware, it becomes listed as soon as you start it... End of story...

---

### Post by Sylos on 2013-03-20
> **jnbek said:**
> JACK is a bit temperamental there's no denying this, but if you use qjackctl; which comes with Ubu Studio, then most of your problems go away... Sure you might have to connect a system plug to an effects rack then plug the effects rack into Ardour what not... with QJackCtl all of this is sooooo much easier, if your App is JACK aware, it becomes listed as soon as you start it... End of story...

True enough as long as Jack is working properly - I still get issues with some progs not appearing in Jack everytime I start them. A couple of attempts normally gets it working properly though. And as for connecting system plugs to effects - well .... to me thats just reminiscent of a pro studio 10 years ago - when people still had rack mount compressors, reverbs etc and you used a thing called a patch bay with little patch leads that connected everything.

For my part - I dont see Jack as being that hard to use. It can be a pig to get running when you first start (although when I first used it I just started Qjackctl and it worked fine from the off) but I have made peace with that on the basis that it is trying to work with the widest possible selection of hardware etc etc. Using it once you get it running is pretty easy once you get the principles of how it works (basically, at the user level, - its a virtual patchbay that connects everything). It gives you a lot of control over what you want to do. Anything with an output can be connected to anything with an input if you know how (and have a2jmidid).

As for the comments above about having only 1 sound server - well, sadly the audio options have become a bit of a joke in the linux world. Whether its OSS, ESD, Pulseaudio yada yada yada. That is pretty annoying. But then Jack sits in a different league and for different purposes than the other options. I dont think you could do low latency recording with ESD or Pulse. The pulseaudio/jack conflict narks me greatly but I just remove pulseaudio and go straight into alsa/jack usage when I install my Studio OS, so it doesnt really affect me.

I've said it many times before, but Im gonna sya it again: I still like the music I listened to 10 years ago - it doesnt sound poorly recorded or badly prodcued. SO if linux can offer me a free option that is 10 years behind the curve of the commercial products then I can still make music that doesnt sound bad. A good engineer does not need the latest software to create a good sound (which is all the more annoying when I hear how poor my own creations are), and having the latest software wont make a bad engineer sound good.

In the end Jack is a good sound server for music production and should be supported as the standard for it on linux. If you find a problem, file a bug report, contact the devs or whatever will help make it better. Frustrating though it may be at times, its the best option we have. 


TO THE OP: If you can give some more details on your hardware and software configuration, along with the steps you are taking then someone may be able to help you get Jack working how you want.

Cheers

---

### Post by user333 on 2013-04-07
I'm coming to this thread a bit late, but maybe I can help :) I struggled with jack a lot before I understood how it works, but now I love it. It is very important to understand that pulseaudio and jack don't play nice. You have to disable pulse in order to use jack. To do this use the "puseaudio --kill" command, and then start jack using qjackctl. Once this is done, new applications that start may disconnect old ones, so keep an eye on this and make sure they stay connected to your speakers. As far as the apps themselves go, make sure Audacity is in jack mode when you want to use jack. Also, you can't really run pulseaudio apps at the same time, so don't try. I'm not sure if this helps at all but I can give a more detailed explanation if you need it.

---

### Post by CraigPid on 2013-04-09
> **Sylos said:**
> I've said it many times before, but Im gonna sya it again: I still like the music I listened to 10 years ago - it doesnt sound poorly recorded or badly prodcued. SO if linux can offer me a free option that is 10 years behind the curve of the commercial products then I can still make music that doesnt sound bad. A good engineer does not need the latest software to create a good sound (which is all the more annoying when I hear how poor my own creations are), and having the latest software wont make a bad engineer sound good.



Well said.

---

