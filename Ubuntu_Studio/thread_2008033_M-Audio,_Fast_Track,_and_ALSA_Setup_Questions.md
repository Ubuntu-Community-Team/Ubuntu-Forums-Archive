---
title: "M-Audio, Fast Track, and ALSA Setup Questions"
date: 2012-06-21
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-06-21
Hi Everyone, 

So, I'm new to all this, both Linux AND music recording. Right now I have and M-Audio Fast Track. It's not a Fast Track Pro. Just a regular Fast Track. 

[http://www.americanmusical.com/Item--i-MII-FSTRKMK2-LIST?src=Y0802G00SRCHCAPN&utm_source=google&utm_medium=cpc&utm_campaign=PLA&gclid=CLzUrIzp4LACFUJo4AodnV9Ezw](http://www.americanmusical.com/Item--i-MII-FSTRKMK2-LIST?src=Y0802G00SRCHCAPN&utm_source=google&utm_medium=cpc&utm_campaign=PLA&gclid=CLzUrIzp4LACFUJo4AodnV9Ezw)

I wanted to verify just to make sure. I made this post, because I noticed that all the articles and threads similar to this are about different versions. I just have the standard.

Anyways, right now I'm just trying to do the basic thing and have the ability to record my bass right in to Ardour, so I can export them out as MP3's and share them. But first I need to set the configurations. What driver should I use? What latency?  I mentioned ALSA cause it's the driver I see on every article about subjects like this. It recognizes Fast Track as a USB device, but I don't get any sound or signs that it's recording.

Any help would be greatly appreciated. Like I said, I'm new to all this. I have a strongg knowledge of computers. I'm relatively new with Linux, definitely  new to Ubuntu Studio, ALSA, Ardour, and music production.

---

### Post by sgx on 2012-06-22
Hi, I have a regular FastTrack also, a nice kit. You'll
want to look at the qjackctl wiki, worry not about alsa.

The qjackctl wiki, links 4 and 8 will help set up jackd,
your high performance linux sound server, (like asio from
windows world) and its qjackctl gui, with screenshots, and info.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Run these two commands in a terminal, and look for the
FastTrack sound device to appear in brackets. snd-ice-1712 is the
maudio kernel module, so ice1712 in some form, will be output here.

aplay -l
cat /proc/asound/cards

My output looks like

bash-4.1$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bash-4.1$ cat /proc/asound/cards
 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xac00, irq 17

My pci soundcard has two listings in brackets, (yours will be
slightly different) M Audio Audiophile 24/96, and ICE1712 multi 

both are shown in qjackctl at the
setup page on the right side in the dropdown list of

Input Device >
Output Device  >

click the > widgets to see the dropdown list. If nothing that is
listed there now works, in the line where it says hw:0 or similar, substitute something listed in the brackets, without the brackets

qjackctl mimics the real cables of the 70's  so use that old
sensibility, to conquer the new environment.

The Periods/Buffer setting in qjackctl Setup page should be 3,
for any usb gear. The Frames/Period will be your choice,
try 256 or 128 for live recording, and higher for mastering
or rendering.

On the qjackctl Connect page, click to select an item, it highlights, then on the opposite side of that panel, click the item you want to connect to, it highlights, then click the connect button, and a line
is drawn between them.

There are three tabs on the Connection panel.
Your soundcard input is System, on the audio tab, on the left side.

the soundcard output is System on the right side of
the Audio tab.

Start rakarrack, for fx on your bass. It should connect
automatically in qjackctl, but might be connected mono by default,
so, if desired, redo the connections for stereo,
and change the setting in Rakarrack Preferences.
Like two mono rca cables, you select each pair of rakarrack destinations you want to terminate, and press the
Disconnect button.

Then reconnect it to the half of its stereo output that was not used by default. 

A big X will be drawn, when the In and Out of
rakarrack are connected.

Ardour connections will show up, and it has useful features to start and connect jackd upon starting ardour.

There is a little widget on the left side of the various items
in the qjackctl connection window. + or >  etc, click it to
expand the list, showing all possible i/o on that item 

The alsa tab holds midi connections for keyboards, synthesizers,
and software midi ports, and the middle Midi tab, connects jackd-aware midi items. That port is launched after jackd is running,
by

a2jmidid -j default

Search for hydrogen and ardour in youtube, many videos
will show qjackctl and the connections process,
since it is the first step for nearly everything.

:popcorn: cheers

---

### Post by MrBalloonHands on 2012-06-23
Hi sgx,

Thanks for the help thus far. I do however have a few questions. I have followed you steps up until the point of configuring the Connect page. I can't seem to find it.

 I attached a couple of screen shots. One of the terminal displaying the results of what you told me to do in the first few steps, and one of the qjacktl main page. Could you please look these over and point out anything I'm missing? I'm kinda stuck. 

[ATTACH]220093[/ATTACH]
[ATTACH]220094[/ATTACH]

Also, please take a look at the terminal screen shot. 

Thanks for your help,

-Nate

---

### Post by jejeman on 2012-06-23
Never use picture to show text. Outputs from terminal can be copyied as text. Just copy them here and format them with CODE tags.

In qjackctl there is button for connections. Press it and window will show.

---

### Post by MrBalloonHands on 2012-06-23
Ok, I did what I was told and it still doesn't. I pretty much need a step by step guide from the get go on how to plug my bass in my m-aduio fast track and record in the ardour. That's it! nothing more. Can some one please help me?

---

### Post by jejeman on 2012-06-23
I will asume that you configured jack corectly.

0. plug in bass to usb card
1. turn on usb card
2. start jack - with qjackctl
3. start adrour
4. make mono audio track - it will automaticly be named Audio1
5. in qjackctl connections window connect capture_1 to Audio1 - if you connected bass to capture_1 port, this means left channel on physicall stereo input on usb card

This is the general workflow, adjust it to your setup.

---

### Post by MrBalloonHands on 2012-06-23
I don't know how to configure Jacks. That's my first problem. I'm new to all this. I know nothing.

---

### Post by MrBalloonHands on 2012-06-23
I tried what the first person told me, but I barely get a signal, and I can't hear it back. I've been trying different combinations Input/output devices.

---

### Post by MrBalloonHands on 2012-06-23
Yeah, still doesn't work. I did check the connections like you asked, but nothing. There has been progress as far as output sound. I can hear the click track. What do you mean by " left channel on physicall stereo input on usb card"?

---

### Post by MrBalloonHands on 2012-06-23
[jejeman]("http://ubuntuforums.org/member.php?u=609757"),

I know you don't like screen shots, but it's the only way that I know of that will show how my connections are set up. If you see anything wrong, please let me know.

Thanks a lot for all your help thus far, it's greatly appreciated. 

[ATTACH]220127[/ATTACH]

---

### Post by jejeman on 2012-06-24
It's not that I don't like screenshots, it's about to be optimal. Using a picture to show the part of the GUI is normal, but using it to show text from terminal emulator is not. Because it can be easily selected and copied. Much more simpler action than takeing a screenshot, plus it saves bandwith, alows search etc.

Back to the matter.

I don't see anything wrong with connections in qjackctl, but I don't know your setup.
In the specification for that usb card it says it has 2 input and 2 output. In connections window there are 6 outputs, so I guess that you didn't seleceted the usb card to be used with jack. And that is why you don't have sound from your bass.

---

### Post by MrBalloonHands on 2012-06-24
I GOT IT!!!!!! It now works. Thanks for all your help guys. It's greatly appreciated.

---

### Post by boglode on 2013-01-12
I am struggling to figure out how to get sound into Rakarrack and Rosegarden since I can't figure out how my settings are supposed to look. Connecting M-audio Fast track I get:
```
bo@Ovelokale-Dell:/proc/asound$ aplay -l
**** Liste over PLAYBACK-hardwareenheder ****
lydkort 0: AudioPCI [Ensoniq AudioPCI], enhed 0: ES1371/1 [ES1371 DAC2/ADC]
  Underenheder: 1/1
  Underenhed #0: subdevice #0
lydkort 0: AudioPCI [Ensoniq AudioPCI], enhed 1: ES1371/2 [ES1371 DAC1]
  Underenheder: 1/1
  Underenhed #0: subdevice #0
lydkort 1: Track [Fast Track], enhed 0: USB Audio [USB Audio]
  Underenheder: 1/1
  Underenhed #0: subdevice #0
lydkort 3: ICH6 [Intel ICH6], enhed 0: Intel ICH [Intel ICH6]
  Underenheder: 1/1
  Underenhed #0: subdevice #0
lydkort 3: ICH6 [Intel ICH6], enhed 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Underenheder: 1/1
  Underenhed #0: subdevice #0
bo@Ovelokale-Dell:/proc/asound$ cat /proc/audio/cards
cat: /proc/audio/cards: Ingen sådan fil eller filkatalog
bo@Ovelokale-Dell:/proc/asound$ cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xccc0, irq 18
 1 [Track          ]: USB-Audio - Fast Track
                      M-Audio Fast Track at usb-0000:00:1d.0-1, full speed
 3 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1980 at irq 23
bo@Ovelokale-Dell:/proc/asound$ 

```
I can get recording in Audacity working using ALSA but when it comes to Jack - no sound. I can't figure out how the connections in Jack are supposed to look. Question:
When selecting hw1,0 as input device - should jack produce some additional input ports?
Is it correct that M-Audio fasttrack shows up as hv1 and hw1,0 (I expected to see hw:1,0 and hw:1,1). Please find attached images from Jack

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229953&stc=1&d=1358019476[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229954&stc=1&d=1358019476[/IMG]

One of many tests:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229955&stc=1&d=1358019944[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229956&stc=1&d=1358019944[/IMG]
Regards

Bo.

---

### Post by boglode on 2013-01-14
I got it to - finally some might say:

Following [http://ubuntuforums.org/showthread.php?t=447744](http://ubuntuforums.org/showthread.php?t=447744) I found out that I kept missing the interfaces part. I tested playback using Hydrogen and recording using Ardour.

I would like to playback on my soundcard while recording on the M-Audio Fasttrack - but so far i have been unsuccessfull. Since I like to play guitar rather than fiddling with output settings I am okay with this :-)

I have seen all my playback devices listed a few times but I cant seem to be able both to record and to see the onboard or pci soundcards....

Thank you all for the nice descriptions :-)

Below my Jack-settings:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230069&stc=1&d=1358201731[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230070&stc=1&d=1358202538[/IMG]

---

