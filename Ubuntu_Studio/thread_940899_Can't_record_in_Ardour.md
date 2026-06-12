---
title: "Can't record in Ardour"
date: 2008-10-07
forum: Ubuntu Studio
---

### Post by yelserpdog on 2008-10-07
I'm trying to record some guitar with Ardour but I can't seem to get it to receive any sound. My interface is a Tapco USB device. I can hear sound through the device, can play guitar through it and can record in Audacity but I can't seem to get anything into Ardour. Can anyone help?

thanks
Yd

---

### Post by paulg on 2008-10-07
Sorry if this seems obvious, but are you starting [JACK]("https://help.ubuntu.com/community/HowToJACKConfiguration") before you start ardour?

---

### Post by yelserpdog on 2008-10-07
yes, I'm starting Jack, then going into Ardour. When I try to create a new project though I get a message saying that i'm near the limit of memory and that Ardour may stop because of it (I didn't get chance to write it down). Once I choose OK the system locks up. I don't get this when I open an existing project though.
cheers

---

### Post by paulg on 2008-10-07
The message you are describing is typical if your memory is locked. In a terminal, 'ulimits -l' will tell you how much of the system memory is available. You probably don't want to set it all and I haven't seen any hard and fast rules about how much to set but if your system starts writing to swap then you're probably going to get xruns anyway. See the [Getting Started]("https://help.ubuntu.com/community/UbuntuStudio/GettingStarted") guide to set your limit higher. 

If that doesn't help what messages are you getting from JACK when Ardour exits (open 'messages' in qjackctl)? Are you running your latency too low and piling up xruns in JACK? Are you running the linux-rt (real-time) kernel?

---

### Post by yelserpdog on 2008-10-08
I've found somewhere on here that I may need to run the following commands

:-$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf

When I do so though I get a message saying "permission denied" How do I get round that (sorry, noob alert!)

I am running the realtime Kernel, that much I do know

cheers

---

### Post by DARKAD on 2008-10-08
The memory lock could not be your real problem;
I hope you use qjackctl to run jackd.
If you use it you can watch at the connection window and see if the system capture(output) is directed into the track name(input) that's from left to right, elsewhere you can draw a line from an output sound source to input recording track.

On ardour you can select the track and clicking on View, "show editor mixer", you can therefore click on the input selector high on the left and on the output selector down in the same panel.
You now have the way to select your input and output audio of the track you've just selected.

Good recording!
 Darkad

---

### Post by paulg on 2008-10-10
> **yelserpdog said:**
> I've found somewhere on here that I may need to run the following commands

:-$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf


Sorry for the late response.

You might try just editing the limits.conf file directly if the above isn't work for you.

```
~/ gksudo gedit /etc/security/limits.conf
```

Then add the following lines to the 
```
audio - memlock 250000
audio - nice -10
audio - rtprio 99
```

If I recall correctly (if anyone knows better than my layman's understanding please correct me):
[LIST]
[*]The 'memlock' line will give users in the audio group (or the user audio) more memory by increasing the user memory lock. Current value in the example is about 250MB. You can safely increase this if you have a gigabyte or more memory. You want to leave some for the system though.

[*]The 'nice' line, has to do with how long the processor will wait for processes queued from the audio group (or user audio).

[*]The 'rtprio' line assigns an extremely high priority to the group to ensure the audio group processes go to the front of the line.
[/LIST]

You'll need to log out/in for the changes to take effect. Typle 'ulimit -l' in a terminal to see if the changes were made.

> **yelserpdog said:**
> 
I am running the realtime Kernel, that much I do know


I think you can type 'urname -r' to determine which kernel is running. If you had installed the generic kernel at any point it may still be installed and may be the first option in the GRUB list so you may still not be getting the correct kernel if you haven't checked. 

If the 'urname -r' command doesn't work (away from my computer, sorry) you can install the 'linuxinfo' package which is run from the terminal and gives the same info in a pretty[ier?] format. It's also easier to remember :) If your rt kernel is not first in the list and you're running the wrong kernel you'll need to reboot to select the rt kernel from the grub menu. See the [howto page]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") to change your grub menu too load linux-rt by default. 

Let us know if you get it working. I've subscribed to the thread by email so I'll get back again.

---

### Post by yelserpdog on 2008-10-11
I'm making progress!!

I made the changes in Jack suggested by Darkad and I can now record audio, wooooohhhooooo :guitar: 
THe memory lock is still causing a problem though. When I open up Ardour I get te message and every time I try to create a new session in Ardour the system locks up and I have to turn off the power.

~/ gksudo /etc/security/limits.conf Running this command doesn't do anything. It asks me for my password but then nothing happens. I found the limits.conf file and tried to change it but it won't let me save the changes.
urname -r didn't work but I downloaded linuxinfo and that confirmed I am running the RT kernal.

I'm getting there slowly (thanks to your expertise!). Just the memory lock problem to sort out now.
THanks
YD

---

### Post by thorgal on 2008-10-11
put unlimited instead of 250000 in /etc/security/limits.conf, log out and log in again

PS: the gksudo command requires another command after, here a text editor command, like vi or emacs or nedit, whatever text editor you are comfortable with. gksudo means that you need to edit the text file as a superuser because this file is a system configuration file and only superusers can edit it (the admin of the PC, you I guess :) )

PPS: its not 'urname' but 'uname'

---

### Post by yelserpdog on 2008-10-12
Hey presto, problem solved, thanks. I managed to edit the file no have unlimited memory lock and all seems well. 
I can now record and don't get the memory message. Thanks for everyone's help here.
I'm learning......slowly!!!!

---

### Post by paulg on 2008-10-16
Sorry 'bout that. The command should have been 'gksudo gedit...' as pointed out. Fixed in my post.

Glad you got it working.

---

