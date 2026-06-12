---
title: "delta 66 card and Audacity"
date: 2011-04-24
forum: Ubuntu Studio
---

### Post by serfcx on 2011-04-24
Have looked through the posts but cant find anything that answers my very basic question.
I have a second hand M-Audio delta 66 sound card with a break out box and its revision b so I think it should work with Ubuntu studio 10.4
Have I assumed wrongly that you just plug in a source to the "ins" on the breakout box and Audacity should pick it up ?
Do I have to link through Jack as I know that Audacity does not play well with Jack ?

Any help please, keep it simple idiot on the loose !

---

### Post by sgx on 2011-04-25
Hi, audacity prefs for my maudio  24/96 are set to Host = alsa, and the maudio soundcard in recording/playback device.

lsmod   the output of that lsmod command should have snd_ice1712
(the module supporting most maudio chipsets) somewhere in the list of kernel modules. If not, try this command

sudo modprobe snd_ice1712

If there is no feedback, it is successful, reboot, and try
to find your card in qjackctl, press the Setup button in the setup page,

Input Device  >
Output Device >

click the  >  widgets for a list of detected soundcards/chips.

And then in audacity menu Edit -->Preferences

There is a good page with screenshots:

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

. You may have your motherboard soundchip getting used first,
put some headphones in to check. There should be a Ubuntu hardware config utility to choose each available card.

For jackd, audacity shows up in qjackctl as 'portaudio', and only
after pressing audacitys record button, so you must then press pause, make the desired connections, and press pause again, to begin recording in your audacity. A little street theater, but it works.

Timemachine is a great little
recording app for jackd, saving w64, or wav files, which can be
imported to audacity.
the w64 files  look like this:
 tm-2011-04-01T01:12:05.w64
and should be renamed if used in windows, without the : :

Cheers

---

### Post by serfcx on 2011-04-25
Thankyou sgx for your help.

I can start qjackctl and can find my Maudio sound card and the snd_ice1712 driver - so far so good.

When I start Jack I have 12 captures in the readable clients column (LHS) and playback 1 and 2 in the writable clients which represent my on board sound as setup in output.

When I start Audacity and record and pause as you suggest I do not have port audio showing up in jack connect and also the maudio card is not available as an option in "record" options I assume because Jack has it connected and as such it is not available to audacity.

How does envy24 tie into all this ?

By the way I do not have pulse audio installed as I heard it gave problems.

Any ideas ?

---

### Post by cchhrriiss121212 on 2011-04-25
Audacity does not work well with jack, and I think the newest versions have dropped jack support altogether. If you want to use audacity, then just use ALSA. Also jack does not work well with more than one card, I'd recommend changing the settings to ignore your onboard audio if you want good performance. 

> How does envy24 tie into all this ?
Envy24control is the software for controlling your card, you can use it to set volume level, sample rates and other things. It is not involved in the recording chain.

---

### Post by tgalati4 on 2011-04-25
envy24control is needed to set the patches--the connections between your 6 inputs and your 6 outputs.  You need to make the correct patches before audacity will see any signals on the inputs.  The Delta66 card is pretty sweet for older sound hardware.

---

### Post by serfcx on 2011-04-25
> **tgalati4 said:**
> envy24control is needed to set the patches--the connections between your 6 inputs and your 6 outputs.  You need to make the correct patches before audacity will see any signals on the inputs.  The Delta66 card is pretty sweet for older sound hardware.

Thanks for that info but remember you are talking to an idiot. How do I make these connections - I can find no information !

---

### Post by sgx on 2011-04-26
> **serfcx said:**
> Thanks for that info but remember you are talking to an idiot. How do I make these connections - I can find no information !
OK, I led you down the wrong path temporarily ](*,)
Correct steps:
I logged out, and logged in (or fresh boot)
I open  qjackctl, and start jackd
I started audacity
Now, audacity menu Edit -->Device -->Host will show the option for
Jack Connection Kit, Alsa, and Oss, choose the Jack option.

Now in audacity, press record, and then pause, press the Connect button in qjackctl, and you should see PortAudio on the right panel, likely auto-connected to System Capture, on the left (Audacity 3.12 here) Manually connect if needed, and press the pause button in Audacity when ready to record.

By not starting jackd >before< audacity, Audacity could not see its existence, and therefore decided not to load it as an option in its Device preferences. I had forgotten this 'feature'. Sorry! You can't claim to be the stupid one :wink:

I also recommend using Jack Timemachine for recording, a brilliant
and simple app that can receive and record all your jackd outputs.
It saves .w64 files in high quality by default, which can be imported into audacity, or normal .wav, if desired.

Cheers

---

### Post by sgx on 2011-04-26
screenshots of envy24control Mudita version

[http://code.google.com/p/mudita24/](http://code.google.com/p/mudita24/) with delta 66

---

### Post by serfcx on 2012-02-17
> **sgx said:**
> OK, I led you down the wrong path temporarily ](*,)
Correct steps:
I logged out, and logged in (or fresh boot)
I open  qjackctl, and start jackd
I started audacity
Now, audacity menu Edit -->Device -->Host will show the option for
Jack Connection Kit, Alsa, and Oss, choose the Jack option.

Now in audacity, press record, and then pause, press the Connect button in qjackctl, and you should see PortAudio on the right panel, likely auto-connected to System Capture, on the left (Audacity 3.12 here) Manually connect if needed, and press the pause button in Audacity when ready to record.

By not starting jackd >before< audacity, Audacity could not see its existence, and therefore decided not to load it as an option in its Device preferences. I had forgotten this 'feature'. Sorry! You can't claim to be the stupid one :wink:

I also recommend using Jack Timemachine for recording, a brilliant
and simple app that can receive and record all your jackd outputs.
It saves .w64 files in high quality by default, which can be imported into audacity, or normal .wav, if desired.

Cheers

Quite a time since I looked at this problem, have been occupied.
Have followed instructions above but Audacity remains on "pause" and will not start recording. No apparent error messages

---

### Post by CivilizationII on 2012-02-17
> **serfcx said:**
> Have looked through the posts but cant find anything that answers my very basic question.
I have a second hand M-Audio delta 66 sound card with a break out box and its revision b so I think it should work with Ubuntu studio 10.4
Have I assumed wrongly that you just plug in a source to the "ins" on the breakout box and Audacity should pick it up ?
Do I have to link through Jack as I know that Audacity does not play well with Jack ?

Any help please, keep it simple idiot on the loose !


Probably not a great help, but the m-audio 66 and ubuntu standard 10.04 are working out of the box

---

