---
title: "Skype Video on Darter"
date: 2009-01-15
forum: System76 Support
---

### Post by pseudotheist on 2009-01-15
Hey, I'm looking at getting a System 76 Darter, but kinda new to the whole linux PC thing (only ever a user on pre-configured boxes).  I assume that since it's pre-configured for Ubuntu I'll skip most of the installation pitfalls, and I'm given to understand that Open Office, WinE, and GIMP will address most of my computing needs, but I really wanted to be sure about this one before committing to purchase:
Will I be able to make and receive video-phone calls over Skype on this box?  Are there any complications I will have to address to make this possible?

---

### Post by thomasaaron on 2009-01-15
Yes, you will.

You will have to set up the audio on Skype (which we can help you with), and you will have to turn on your camera before starting Skype. That should be about it.

---

### Post by Spr0k3t on 2009-01-15
Just chiming in to say the Daru3 works fantastic with skype.

---

### Post by pseudotheist on 2009-01-28
Got it today.  Don't see any indication of how to turn on or use the camera...

---

### Post by thomasaaron on 2009-01-29
Fn-F10 turns on the camera. You can use it in Ekiga Softphone or Skype, but you should turn it on before starting the app.

---

### Post by pseudotheist on 2009-01-29
> **thomasaaron said:**
> Fn-F10 turns on the camera.
That was gonna be my next guess...


Should I have Camorama or anything to use the camera for standard picture and video taking, or will the fn-F10 open an app for that? 


I'll be installing Skype when I get home this afternoon.  You mentioned something about setting up the sound?  I currently only have the embedded microphone...

---

### Post by thomasaaron on 2009-01-29
Camorama won't work. Only applications that support the v4l2 format will work. 

You might try Cheese (but it was broken in Intepid, and I'm not sure if it is fixed yet).

Your cam will definitely work with Skype and Ekiga Softphone, though.

---

### Post by pseudotheist on 2009-01-29
When I try to install the Skype package it gives me: "Error: Wrong architecture 'i386'"

---

### Post by pseudotheist on 2009-01-29
O.k.  So I got Skype installed via mediabuntu, but can't get it to recognize the camera.  I don't see any visual response when I press Fn-F10.  How can I verify the camera is on?

---

### Post by Spr0k3t on 2009-01-30
Open up a terminal.  You should see something like this when you type lsusb:

```
Bus 004 Device 002: ID 5986:0303 Acer, Inc
```

It may not be all warm and fuzzy type of "your camera is on" but at least it's a way of verifying.  I haven't had any problems using Ekiga, Cheese, or Skype on my DARU3 (8.10 64bit installed).

---

### Post by pseudotheist on 2009-01-30
At least it's something.  As far as I can tell, the camera state is persistent through reloads, right?

From the available Skype tests it looks like I've got everything working.  Hopefully I can make an actual call this afternoon to verify.  I'll probably eventually need to get a better microphone, if the test call volume is any indication.  Is there a list of compatible products somewhere?

Thank you both very much for your help.

---

### Post by thomasaaron on 2009-01-30
Pretty much any external mic will do. I kind of like the headphone/mic combo that my wife has.

But, from your above response, I'm not clear on whether or not you got the cam working. 

If not, you have to go into Skype's options, select "Video Device" and then select your cam.

If that doesn't work, please provide more info on what you're trying and what you are seeing.

---

### Post by pseudotheist on 2009-01-30
The camera appears to work fine in the Skype camera test box.  Of course if I turn off the camera it stops (shocking), and it doesn't seem that I can get it working again without rebooting.  I'll come back to let you know when I get to make an actual call.

---

### Post by thomasaaron on 2009-01-30
OK, good. Then we know it's not hardware. Do you have to reboot, or can you just shut Skype all the way down and re-start it?

---

### Post by pseudotheist on 2009-01-30
Skype officially works fine.  People even said the audio was perfectly adequate (which surprises me, based on the "test call" volume).  Of course my wife hates the computer now anyway, because she brought home some random proprietary software called "SigmaPlot", that she absolutely has to have all of the sudden, and the WINE install isn't instantly flawless...



P.S. For you I did test, and if I turn off the camera while Skype is running, restarting Skype will not fix it.

---

### Post by jdb on 2009-01-31
> **pseudotheist said:**
> Skype officially works fine.  People even said the audio was perfectly adequate (which surprises me, based on the "test call" volume).  Of course my wife hates the computer now anyway, because she brought home some random proprietary software called "SigmaPlot", that she absolutely has to have all of the sudden, and the WINE install isn't instantly flawless...



P.S. For you I did test, and if I turn off the camera while Skype is running, restarting Skype will not fix it.

You might try Virtualbox if you have a copy of windows you can load.
Just about anything that will run on a windows box with basic integrated video will run in Virtualbox.
The downside is that it doesn't support native access to the graphics card so it's not very good for a lot of games.

jdb

---

### Post by pseudotheist on 2009-01-31
O.k. So, NOW it's time to get in over my head...

Is there a shell command to turn on the camera?  If so, can't I write some sort of script to issue that command before launching Skype?  At which point, all I'd have to do is assign it a goofy icon and add a panel link to it, right?  I'm sure there's a flaw in this plan somewhere...

---

### Post by thomasaaron on 2009-02-02
> I'm sure there's a flaw in this plan somewhere... 

Bingo. :popcorn:

I've spent a fair amount of time trying to come up with such a script. However, the actual *switching* mechanism (that is, getting power to the cam) seems to be at the BIOS level, not at the OS level. I'm not saying it's impossible, but I've not found any way to script the starting of the camera, and it is always turned off when the computer comes on.

Now, once you *initially* turn the camera on, you might be able to enable/disable it by inserting and removing the uvcvideo module, but that would be a) of very limited value, and b) one heck of a nasty hack.

---

### Post by pseudotheist on 2009-03-04
Well, it doesn't automate turning the camera on, but I ended up developing a script anyway,to kill any zombie Skype processes, verify the camera is on (and prompt the user to turn the camera on if it isn't), and launch Skype.

> ps aux | grep skype.real | grep -v grep | awk '{ system("kill " $2) }'
until [ "`lsusb | grep Acer`" ]
do
        echo "Camera not recognized; please press Fn-F10 to turn on camera.\nPress enter to continue."
        read x
done
skype

I have it mapped to the top panel.  I don't know if anyone else will find it useful, but this will probably save me a lot of grief from my wife...

---

### Post by 3Miro on 2009-03-04
I am using the camera on Pangolin, everything worked out of the box. (Sound was picky, but solved that one too). I wish my Mom has a camera too so I could see her as well.

---

