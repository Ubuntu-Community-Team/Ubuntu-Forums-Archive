---
title: "Will Skype work on Serp2?"
date: 2008-11-23
forum: System76 Support
---

### Post by hkarl629 on 2008-11-23
Got my webcam working on Serp2. It shows up in "Cheese" and "Ekiga". Among friends and relatives I think I have greater possibilities of communicating with Skype on their Windows machines. Tough converting them to Linux/Ubuntu.

I see there is a Linux version available for download.

If you are using Skype as I've suggested I woould like to hear from you with your experiences and suggestions.

Thank you.

---

### Post by korvus81 on 2008-11-24
Skype works fine for video chat with Windows users -- I used it this weekend (not on S76 hardware, however, but on Ubuntu 8.4).

I will say that it doesn't have the best video quality (the Windows side had an HD webcam, but Skype stuck to postage-stamp sized video), but it's peer-to-peer infrastructure means that it will figure out how to get around just about any firewall.  That's a big plus.

I'm just starting to play with getting Ekiga to talk to Windows users, so if anyone has any tips, let me know...

---

### Post by thomasaaron on 2008-11-24
Hi, Karl. 

Skype should work fine. I use it daily on my GazV5, but I use Skype-in and Skype-out, which allows you to call, and receive calls from, telephones.

I'd recommend following the instructions here for installing Skype...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Take it from the top. You want to install the mediabuntu repositories, and then install skype from them.

---

### Post by hkarl629 on 2008-11-24
Tom, hello

I've been trying to puzzle some things out and with the help of this forum I got the web cam working. Now I want to use it with Skype. Thank you for responding to my call for help.

My setup is Serp2, Hardy Heron. 32 bit Ubuntu.

If I follow your instruction in the link - I would go down to the Ubuntu 8.04 Hardy Heron section, input the commands in the first box, then input the command in the box under 32 Bit Ubuntu Users. Then input the command in the box under Skype.

MY QUESTION - Do I do these all at once. In other words, is this a series of commands where I don't hit enter or whatever command is neccesary, until I have entered all commands?

Seems like I'm telling the computer to do a lot.

I await your answer.

Sincerely,

Thank you,
Karl

---

### Post by thomasaaron on 2008-11-25
Hi, Karl. Yes, you copy and paste the commands in one at a time, hitting enter after each one. Here are the commands you will need to run (so don't worry about the tutorial...).

First:
Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Select Other in the left panel and then select the Ubuntu restricted extras package. Click Apply Changes. 

Then, open a terminal, and here are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs

```
```
sudo apt-get install skype
```

---

### Post by hkarl629 on 2008-11-25
Tom,

Thanks! Once again you are right there. I followed your instructions, carefully copying and pasting the codes into the terminal. Skype loaded. Now the problem is to get the microphone to work.

I know this Serp 2 has a microphone right up there next to the camera. How do I get it to turn on?

This version of Skype does not have a menu bar as does ver. 3.8.0.188 on my Vista laptop. It seems to be very'streamlined'.

Karl

---

### Post by thomasaaron on 2008-11-25
First, you need to get your mic working in Sound Recorder. Once you do that, it should more-or-less work in Skype.

In skype, you should be able to click the left icon at the bottom and then select "options". In the resulting window, you can pick "Sound Devices" and set it up like the screenshot I'm attaching.

If you're using Hardy, you will use ALSA instead of Pulse.

---

### Post by hkarl629 on 2008-11-25
Tom,

Screenshot didn't make it.

Karl

---

### Post by hkarl629 on 2008-11-25
Tom,

Got the screen shot.  Went to that options window and the Sound devices.  Problem is there is no "pulse" choice for "Sound Out"
there is no "pulse" choice for "Ringing".

I've also lost "Sound Recorder" clicking now tells me to Correct audio settings in Multi-Media Settings - which I can't find!

Help.  I'm making a mess of this.

Karl

---

### Post by thomasaaron on 2008-11-25
To get the clicking to quit, lower the PCM some in Sound Control.
Since you are using Hardy, you need to set skype to alsa, not pulse.

If that doesn't do it, I will image a machine with Hardy, set up Skype and post screenshots. However, I probably can't get to it until tomorrow or Monday.

---

### Post by hkarl629 on 2008-11-25
Tom,

The clicking I refer to above is me on the mouse. I'm trying to select Sound Recorder and I get this error message: "Your audio settings are invalid. Please correct them in the Multimedia settings."

I can't find "Multimedia settings".

I've screwed things up.

Karl

P.S. will be gone for a few days. Home probably Saturday.

---

### Post by thomasaaron on 2008-11-26
That most likely means that you have things set up wrong in your sound control panel.

First make sure that all of the dropdowns are in System > Prefs > Sound are set to ALSA.

Then double-click your speaker control icon. This pulls up your sound control panel. That panel should look something like mine (attached), but your options may be a little different.

(I'm working from home today and don't have a SerP2 here.)

---

