---
title: "How do you use RPX400 in Ubuntu?"
date: 2012-01-19
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-01-19
I have a Digitech RPx400.   It is supposed to have digital USB out for recording.
When I hook it up,  I see MIDI channel outs on Patchage, which won't hook up to Playback (so I can hear it).

Shouldn't there be two or four digital audio outputs on the screen too?
Why can't I hook up the output of the RPx400 to say the Rackarack, and add more effects?

What am I doing wrong?

Why can't I record the output of the RPx400?
It is supposed to have digital output.

---

### Post by jejeman on 2012-01-19
Connect Digitech RPx400, and give us output from
```
arecord -l
```
```
aplay -l
```
```
amidi -l
```

---

### Post by nazaroo2 on 2012-01-19
> **jejeman said:**
> Connect Digitech RPx400, and give us output from
```
arecord -l
``````
aplay -l
``````
amidi -l
```

umm...
Do I type that into a terminal?

---

### Post by nazaroo2 on 2012-01-19
```
root@unknown-desktop:~# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@unknown-desktop:~# 

```> oot@unknown-desktop:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@unknown-desktop:~# 


```
root@unknown-desktop:~# amidi -l
Dir Device    Name
IO  hw:1,0,0  RPx400 MIDI 1
IO  hw:1,1,0  RPx400 MIDI 1
root@unknown-desktop:~# 

```

---

### Post by nazaroo2 on 2012-01-19
I have little idea what that means.
I guess it seems to say that at least part of the RPx400 is working and connected.

I can post a pic  

[IMG]http://2.bp.blogspot.com/-bkiRnBaiztI/Txip-0WzklI/AAAAAAAAAvU/wYmP5G-qq6g/s1600/Screenshot.png[/IMG]

I can connect the Hydrogen drum machine to the System playback and hear the sound.
But I can't connect the RPx400 to either the rakarrack, or the System playback, so I can't hear the sound.
I would like to record the sound eventually, but would settle for just hearing it in the computer monitor speakers for now.

---

### Post by jejeman on 2012-01-19
Digitech RPx400 is recognized as usb audio device.
Now, give us output from
```
cat ~/.jackdrc
```

---

### Post by nazaroo2 on 2012-01-19
okay here's an updated screenshot:

[IMG]http://3.bp.blogspot.com/-BHUJpePx0T4/TxisG6ynsiI/AAAAAAAAAvc/Hw8BTi-BR8M/s1600/Screenshot-2.png[/IMG]

Here the Drum machine has no problem going into a sound effects unit, then to meters and finally output to speaker. 

But the RPx400 just sits there like an expensive paperweight.

I should be able to take output from RPx400 and either listen to it, or record it to disk.
What am I doing wrong here?

---

### Post by nazaroo2 on 2012-01-19
root@unknown-desktop:~# cat ~/.jackdrc
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
root@unknown-desktop:~#

---

### Post by jejeman on 2012-01-19
You are using only HDA intel card.
You can't use two cards for capture or playback. Only one. If you want to use Digitech, you need to select it in Qjackctl, if you are useing that jack frontend.

---

### Post by nazaroo2 on 2012-01-19
okay. 
So I just need to shut off one D/A converter, the one built into my DELL?
Is QjackCntl  is that the JACK program?

I don't have a program actually called Qjackctl.  Is that part of another piece of software?

---

### Post by jejeman on 2012-01-19
You don't need to turn off, disable or pullout any cards. Just set jack to use the cards the way you want.
Qjackctl is jackd frontend. You are probably using it, if you didn't mannualy enter the jackd command.

---

### Post by nazaroo2 on 2012-01-19
> **jejeman said:**
> You don't need to turn off, disable or pullout any cards. Just set jack to use the cards the way you want.
Qjackctl is jackd frontend. You are probably using it, if you didn't mannualy enter the jackd command.

Thank you for your time. 
I know this is probably frustrating for you dealing with a newb.

So:  lets assume I'm using Qjackctl, since I didn't enter any jackd command.
I just ran Jack from the pulldown menu, then started to run other music software.
What exactly should I do next?  
If I go to the JACK program, it has all kinds of bewildering crap on each page.

I was under the impression that I just run "JACK" and then leave it alone.
But should I do something else to either configure it, or select the RPx400 each time I want to hear it?

---

### Post by jejeman on 2012-01-19
Look here [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
if you have this than you are using Qtjackctl.
Here you need to setup folowing fields
- interface
- input device
- output device

How do you want to setup your sound routing?

---

### Post by nazaroo2 on 2012-01-19
Here's an extra side-question. 
Since Digitech has basically abandoned the RPx400 for newer products,
but they have a bunch of newer sound patches online.
but again, I don't have the xedit software, since I got my pedal used, 
and run Ubuntu, not Windoze.
Is there a way to download patches into the RPx400 from Ubuntu?
i.e, with or without "xedit" program?

---

### Post by jejeman on 2012-01-19
If xedit is editor librarian for this RPx400, than you probably need to use it. Run it thru wine, it maybe works.

---

### Post by nazaroo2 on 2012-01-19
> **jejeman said:**
> Look here [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
if you have this than you are using Qtjackctl.
Here you need to setup folowing fields
- interface
- input device
- output device

How do you want to setup your sound routing?

Okay I'll check this out.

What I wanted to do was have a convenient way to input my guitar into computer for recording,
and also add vocals, since the RPx400 actually has a mic input too.
I have a mic preamp, but it has not D/A converter. 

So I was hoping to record guitar (and maybe bass) and vocals to computer.

I wanted to listen back and monitor using my computer's playback soundcard (built in).
This is a really low budget attempt to record music practice.
I can't afford expensive digital input cards etc.
I even priced something called an 'mbox' and it was like $200.
But I already have a mic input and supposedly a D/A USB output on the RPx400.
So I was hoping to just use what I have.

I was also hoping there was some free recording software on Ubuntu (next part of problem).

---

### Post by jejeman on 2012-01-19
So, you want to capture sound with RPx400, and to playback it with HDA Intel.
Than you can try to setup for
- input device HW:1
- output device HW:0

---

### Post by nazaroo2 on 2012-01-19
okay I set hw:1 input, hw:0 output.
I saved and rebooted, and it showed up as set.
I presume the change worked. 
Now the screen in Patchage still looks about the same:
also, there is no RPx400 in the Audio section of Connections in JACK.

[IMG]http://1.bp.blogspot.com/-ntMK74cvBs4/Txi423ZNtQI/AAAAAAAAAvk/uyTdaU0cR3s/s1600/Screenshot-3.png[/IMG]

Was I hoping to see extra outputs on the RPx400 for hooking up to a mixer, recorder, or playback?

hmmm... just noticed error msg? on Patchage at bottom of window...what is that?

---

### Post by nazaroo2 on 2012-01-19
> **jejeman said:**
> If xedit is editor librarian for this RPx400, than you probably need to use it. Run it thru wine, it maybe works.


Oops.  xedit for RPx400 installed under Wine but then immediately crashed.
THere is nothing under Digitech at the Wine HQ AppDB.

I will try to get son to run xedit 2.4  (downloadable here:  [http://www.digitech.com/en/software](http://www.digitech.com/en/software) )
on his pirated Vista box. ...

---

### Post by jejeman on 2012-01-19
Capture and Playback port labels never change no matter which card you are using. It's not like midi ports.
Just connect and see if it works.
You have choosed advanced setup to start with. I suggest you first try to set just one card, to see how it goes. And you need first to see if that Digitech will work anyway. Also, you need to run alsamixer to choose inputs if the are more than one.
I realy don't know about RPx400, I've had never use it.

---

### Post by nazaroo2 on 2012-01-19
> **jejeman said:**
> Capture and Playback port labels never change no matter which card you are using. It's not like midi ports.
Just connect and see if it works.
You have choosed advanced setup to start with. I suggest you first try to set just one card, to see how it goes. And you need first to see if that Digitech will work anyway. Also, you need to run alsamixer to choose inputs if the are more than one.
I realy don't know about RPx400, I've had never use it.

Hey!  that worked!  Capture1 and Capture2 are now actually the RPx400.

Looks like guitar input is good to go!
Now I just have to figure out how to record it to disk.

Thanks!

---

### Post by jejeman on 2012-01-20
There are many ways to record audio via jack server, it depends what are you doing. You can use
- jack time machine (quick record to a file)
- Ardour 2 (only audio DAW)
- Muse (audio & midi DAW)

---

