---
title: "Audacity not recording"
date: 2009-10-22
forum: Ubuntu Studio
---

### Post by th1bill on 2009-10-22
I click the record button and it does for 1/2 to one second and althugh the sweep continues across the screen, it just stops accepting iput from the microphone.  Any help will be appreciated.

---

### Post by sdpiowa on 2009-10-22
My recommendation - check the obvious:
Make sure that your microphone works consistently with other programs
Make sure that you have the newest version of Audacity

---

### Post by th1bill on 2009-10-22
> **sdpiowa said:**
> My recommendation - check the obvious:
Make sure that your microphone works consistently with other programs
Make sure that you have the newest version of Audacity

Those were the first two things I did and the mike works with Audacity... for 1/2 to one second.

---

### Post by sgx on 2009-10-23
Hi, I'm assuming audacity is not connected to jackd, so I would start audacity and jackd from the commandline, then start qjackctl, and try to choose your mic as one of the connections. Then choose your mic as the recording device in audacity, press record, then press pause. Now audacity should show up in qjackctl, but will be labelled portaudio. (how intuitive) Now connect the mic in qjackctl to the portaudio, and press pause in audacity again, which resumes recording. 
If there is still a problem, look in the commandline windows for jackd and audacity for clues.
Cheers

---

### Post by th1bill on 2009-10-23
> **sgx said:**
> Hi, I'm assuming audacity is not connected to jackd, so I would start audacity and jackd from the commandline, then start qjackctl, and try to choose your mic as one of the connections. Then choose your mic as the recording device in audacity, press record, then press pause. Now audacity should show up in qjackctl, but will be labelled portaudio. (how intuitive) Now connect the mic in qjackctl to the portaudio, and press pause in audacity again, which resumes recording. 
If there is still a problem, look in the commandline windows for jackd and audacity for clues.
Cheers

I'll need to admit that all of that just blew over my head.  What is happening; the Mic is recording for exactly 4/10 of a second and then Audacity cuts it off.  If I begin as soon as I click record I get 4/10 f a second f my vice ad no more.

---

### Post by sgx on 2009-10-23
Hi, qjackctl is just a visual patchbay to connect your various audio
software and hardware, it uses the jackd audio server, and the command

sudo apt-get install qjackctl

should install it, and the required jackd in one go.

qjackctl has a setup button, press it to open a preferences panel, and explore the options. The input-device/output-device  icons >  are on the middle far-right, and can be pressed to reveal the soundcards your system detects. Select the desired device, save the setup, and press the start button on the main gui.

If everything is working, you'll see the info in the lcd window  at the top of the qjackctl window. Now the earlier info about starting audacity
in the jackd audio environment can be used.


Press the connect button at the bottom-left of the qjackctl main screen. A three-tabbed panel appears, each with left and right sides. 

In the audio tab, the left side is system-capture, and the right side is sytem playback.

In the alsa tab, the left side is for inputs, the right side is for outputs.


This command

jackd -d alsa -r 44100

 can safely start the jackd audio server. It is pretty standard, so you can run it, and then start qjackctl (some menus list it as jack-connect, or similar) Refer back to the earlier post to use audacity in this environment. 
Cheers

---

### Post by AutoStatic on 2009-10-24
You don't need JACK to use Audacity. Besides, Audacity uses PortAudio to connect to JACK and in my experience this is a bit buggy. You're complicating things a bit sgx ;)
th1bill, what is the outcome in a terminal of:
- **aplay -l**
- **lspci | grep -i audio**
- **cat /proc/asound/card*/codec#* | grep -i codec**

And what are your settings in Audacity (Edit - Preferences - Audio I/O)?

---

### Post by sgx on 2009-10-25
> **AutoStatic said:**
> You don't need JACK to use Audacity. Besides, Audacity uses PortAudio to connect to JACK and in my experience this is a bit buggy. You're complicating things a bit sgx ;)
th1bill, what is the outcome in a terminal of:
- **aplay -l**
- **lspci | grep -i audio**
- **cat /proc/asound/card*/codec#* | grep -i codec**

And what are your settings in Audacity (Edit - Preferences - Audio I/O)?
it IS complicated, its a freakin'
RATS NEST :)
portaudio
oss
alsa
jackd
pulseaudio
esound
gstreamer
dbus
hal
modprobe
kernel xyz
compile this
edit that :P

But a little basic i/o information never hurts anyone...
:popcorn:

---

### Post by AutoStatic on 2009-10-25
It becomes a complicated rat's nest when:
- People are being advised to ditch PulseAudio and install esound
- People are being advised to use OSS
- People are advised to upgrade Alsa
- People are advised to use a real time sound server like JACK just to record something with Audacity

THAT is what is complicating things in my opinion. I agree, sound implementations galore, but when someone is unable to make use of the basic functionality of a program like Audacity you should start troubleshooting from there and not advise to start using a different sound server like JACK and then hoping the problem will disappear. Next thing you know is that the forumite who asked the initial question runs into new problems because he can't get JACK to work properly and then ditches Ubuntu alltogether because Ubuntu does not allow him to make a simple recording.

Jeremy

Edit: I'm also aware that having Ubuntu users dive into the terminal and entering all kinds of commands does complicate stuff also for the user. But I'm the one who's troubleshooting here, and for me it's the fastest way to get results ;) And of course, you don't have to work in a terminal if you don't like it.

---

### Post by sgx on 2009-10-27
Although the question about the short recording span in audacity
is narrowly focussed, my reply was intended to expand the users opportunities for success. The process of learning and utilizing
qjackctl often opens the eyes of users to see how their hardware and software are recognized and connected efficiently by linux, and the jackd sound server is without a doubt the one software that holds the interest of serious linux based musicians, such interest also strong in the Mac community, and growing among winxxxx users.
A side effect for this user would be quickly choosing a different
audio hardware and mic, if indeed it turned out there was insuffient support for his particular setup, which I suspect includes usb mic/device, those being problematic in particular, on many computers, linux or not. New linux users need to choose from a small subset of hardware that is known to work with linux, or suffer the inconsistancies of hoping what they have 'will just work', and a few resulting dissapointments. But that sticker is conveniently left off the box. 

@ th1Bill Hi, hope you are getting better results, keep posting! :)

---

### Post by buddah1620 on 2009-10-28
poor th 1 bill.... im sorry people can "nuke" things. I wish I had a simple solution to give you. But unfortunately i am having the same problem.

---

### Post by EbanC on 2009-10-30
I have seen others with this, or a similar, problem. Try going to edit-preferences-recording- and uncheck the software playthrough. I know that was causing a similar problem with a friend's system.

It is worth a shot.

---

