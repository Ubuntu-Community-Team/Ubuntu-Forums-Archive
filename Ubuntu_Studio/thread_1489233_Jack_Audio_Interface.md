---
title: "Jack Audio Interface"
date: 2010-05-20
forum: Ubuntu Studio
---

### Post by oleink on 2010-05-20
Hey.  I'm not sure this is a reocurring question or not as I have found very little about it.  Could someone point me to a decent tutorial that describes Jack Audio controller for noobs and more about Jack so that I know how to use it and maybe give me some advice about how to get my mic input to work on my laptop.  In either case I really want to learn Jack because I would like to record with linux but don't know what I'm doing with jack cause I've only used windows and mac for recording b4

Thanks in advance!:popcorn:

---

### Post by trulan on 2010-05-21
It's a very commonly occurring question - jack confuses a lot of people when they first encounter it.  Here's a good place to start:
[https://help.ubuntu.com/community/What%20is%20JACK]("https://help.ubuntu.com/community/What%20is%20JACK")

---

### Post by oleink on 2010-05-21
> **trulan said:**
> It's a very commonly occurring question - jack confuses a lot of people when they first encounter it.  Here's a good place to start:
[https://help.ubuntu.com/community/What%20is%20JACK]("https://help.ubuntu.com/community/What%20is%20JACK")

Thanks thats got some stuff I didn't know already

---

### Post by sgx on 2010-05-21
> **oleink said:**
> Thanks thats got some stuff I didn't know already
youtube videos on ardour, hydrogen and other linux audio apps often begin with info on jackd, and its qjackctl gui.
Cheers

---

### Post by psidrum on 2010-05-21
Jack is the audio cabling system for Linux 

its like pluging in VCRs DVD Bluray LCD and stereo systems to your htpc

---

### Post by Scott L on 2010-05-21
> **trulan said:**
> It's a very commonly occurring question - jack confuses a lot of people when they first encounter it.  Here's a good place to start:
[https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

Trulan,

Thanks for pointing people to that page!

I spent time and passion to make it and I'm glad people are using it :)

---

### Post by oleink on 2010-05-21
> **Scott L said:**
> Trulan,

Thanks for pointing people to that page!

I spent time and passion to make it and I'm glad people are using it :)

Hey I agree thank the person for posting it cause it was helpful and also thank you very much for making it!

---

### Post by no2498 on 2010-05-22
i installed pitivi

it uninstalled  jack

just a heads up for you all

---

### Post by oleink on 2010-05-23
I got a quick Q.  How does jack compare to other operating systems and how you can just plug stuff in and record etc with the software

---

### Post by sgx on 2010-05-23
> **oleink said:**
> Hey.  I'm not sure this is a reocurring question or not as I have found very little about it.  Could someone point me to a decent tutorial that describes Jack Audio controller for noobs and more about Jack so that I know how to use it and maybe give me some advice about how to get my mic input to work on my laptop.  In either case I really want to learn Jack because I would like to record with linux but don't know what I'm doing with jack cause I've only used windows and mac for recording b4

Thanks in advance!:popcorn:

A preamp and suitable mic will be needed. A laptop mic will be
poor quality, and a headache to maintain/configure. There is a
quality package deal here:

[http://pro-audio.musiciansfriend.com/product/ART-V63MART-Tube-MP-Studio-Package?sku=581915&src=3WWRWXGB&ZYXSEM=0&gclid=CNGrv7Gr6aECFRmfnAodiigaJg](http://pro-audio.musiciansfriend.com/product/ART-V63MART-Tube-MP-Studio-Package?sku=581915&src=3WWRWXGB&ZYXSEM=0&gclid=CNGrv7Gr6aECFRmfnAodiigaJg)

The parts are available separately, if desired.

The preamp goes in you line-in. Qjackctl is a jackd gui, and will show this port in its Audio tab, which opens when you press connect on the main screen. Items are input on one side, output on the other, select the
items you want to connect, and press the connect button(the one on this
tabbed page, not the one on main page.

Cheers.

---

### Post by sgx on 2010-05-23
> **oleink said:**
> I got a quick Q.  How does jack compare to other operating systems and how you can just plug stuff in and record etc with the software
It is very flexible, limited only by the number and quality of apps that support it. There are enough to do professional recording, and create
amazing soundscapes, bread-n-butter covertunes, and what lies in between.
Using wine/wineasio to integrate world-class vst plugins, (using a few vst host applications), means windows setups can be relegated to storage, or testing new products, or utilizing some high-end expensive apps that
use dongles, and unsupported copy-protection schemes.
Cheers
(youtube videos of ardour, hydrogen, rakarrack, and zynaddsubfx, lmms,
rosegarden, etc will sometimes include jackd/qjackctl, since it is the first step)

---

### Post by oleink on 2010-05-24
> **sgx said:**
> A preamp and suitable mic will be needed. A laptop mic will be
poor quality, and a headache to maintain/configure. There is a
quality package deal here:

[http://pro-audio.musiciansfriend.com/product/ART-V63MART-Tube-MP-Studio-Package?sku=581915&src=3WWRWXGB&ZYXSEM=0&gclid=CNGrv7Gr6aECFRmfnAodiigaJg](http://pro-audio.musiciansfriend.com/product/ART-V63MART-Tube-MP-Studio-Package?sku=581915&src=3WWRWXGB&ZYXSEM=0&gclid=CNGrv7Gr6aECFRmfnAodiigaJg)

The parts are available separately, if desired.

The preamp goes in you line-in. Qjackctl is a jackd gui, and will show this port in its Audio tab, which opens when you press connect on the main screen. Items are input on one side, output on the other, select the
items you want to connect, and press the connect button(the one on this
tabbed page, not the one on main page.

Cheers.

Thanks but the mic isnt for recording its just for things like skype.  I will be purchasing an interface for recording music etc

---

### Post by oleink on 2010-05-24
> **sgx said:**
> It is very flexible, limited only by the number and quality of apps that support it. There are enough to do professional recording, and create
amazing soundscapes, bread-n-butter covertunes, and what lies in between.
Using wine/wineasio to integrate world-class vst plugins, (using a few vst host applications), means windows setups can be relegated to storage, or testing new products, or utilizing some high-end expensive apps that
use dongles, and unsupported copy-protection schemes.
Cheers
(youtube videos of ardour, hydrogen, rakarrack, and zynaddsubfx, lmms,
rosegarden, etc will sometimes include jackd/qjackctl, since it is the first step)

Thanks that makes sense

---

### Post by jangal on 2010-05-25
Scott - yes indeed that is some amazing work. changed my view on audio computing and also made it accessible for the first time after many years. thank you very much.

---

### Post by oleink on 2010-07-28
ok i want to bring this post back to life.  I cannot get jack audio to work with any of my recording, or editing software

---

### Post by oleink on 2010-07-28
ok i got most of it to work but stuff like my synths don't have outputs to plug into my recording software..?

---

### Post by AutoStatic on 2010-07-29
Which synths are you using?

---

### Post by oleink on 2010-07-29
zynaddsubfx and amsynth.  I'm hoping I'll be able to use at least the guitar effects software (Rakarrak) with my guitar when recording on ardour and stuff.

---

### Post by AutoStatic on 2010-07-29
amSynth and ZASFX should output to JACK when JACK is running. amSynth's preferred audio driver is set to auto by default and ZASFX should detect a running JACK server too. You could try starting amsynth in a terminal and force it to use JACK with **amsynth -a jack** .

---

### Post by oleink on 2010-07-29
> **AutoStatic said:**
> amSynth and ZASFX should output to JACK when JACK is running. amSynth's preferred audio driver is set to auto by default and ZASFX should detect a running JACK server too. You could try starting amsynth in a terminal and force it to use JACK with **amsynth -a jack** .

thanks you've been a big help on most of my jack questions i've posted here

---

### Post by AutoStatic on 2010-07-30
You're welcome. But do the synths work with JACK now? The JACK Connections window should look like the screenshot I attached.

---

### Post by oleink on 2010-07-30
> **AutoStatic said:**
> You're welcome. But do the synths work with JACK now? The JACK Connections window should look like the screenshot I attached.

Yeah.  Sorry i realized afterword that i started qjackctl after starting the keyboard and synth.  If is start it first they are recognized

---

### Post by oleink on 2010-07-30
> **AutoStatic said:**
> You're welcome. But do the synths work with JACK now? The JACK Connections window should look like the screenshot I attached.

btw if i use an external sound card (an interface) will i be able to get rid of the crackling i get?  I reduced down to 44100hz and 128 frames/period.  If i were to get the interface (behringer uca222) would i be able to put those back to normal without the crackling?

PS crackling is GREATLY reduced when i lowered those settings

---

### Post by AutoStatic on 2010-07-30
The crackling you hear are probably [xruns]("http://alsa.opensrc.org/index.php/Xruns"). No idea how the UCA222 performs, don't expect too much of it though.

---

### Post by oleink on 2010-07-30
> **AutoStatic said:**
> The crackling you hear are probably [xruns]("http://alsa.opensrc.org/index.php/Xruns"). No idea how the UCA222 performs, don't expect too much of it though.

I just found out i don't have a real time kernel so i just installed linux-rt package but idk what it does or how it works.  The other thing is that if I make more adjustments I won't be able to record because it will lead to major lag in jack because of the large frames/period ratio not to mention lower quality at lower hz

---

### Post by oleink on 2010-07-30
> **AutoStatic said:**
> The crackling you hear are probably [xruns]("http://alsa.opensrc.org/index.php/Xruns"). No idea how the UCA222 performs, don't expect too much of it though.

also the packages linux-lowlatency are gone

---

### Post by DouglasAWh on 2010-12-08
> **oleink said:**
> Thanks but the mic isnt for recording its just for things like skype.  I will be purchasing an interface for recording music etc

So, does that mean you are recording Skype but don't care about the quality or just aren't recording at all?  I'd like to record Skype, but from what I can tell, this isn't really possible because Skype just doesn't work with pulse as far as recording.

For example: [http://superuser.com/questions/104631/linux-record-all-the-audio-in-out-of-a-programme](http://superuser.com/questions/104631/linux-record-all-the-audio-in-out-of-a-programme)

---

