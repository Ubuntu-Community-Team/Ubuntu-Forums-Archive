---
title: "PulseAudio and qpaeq loading troubles"
date: 2014-10-23
forum: Ubuntu Studio
---

### Post by Charles_Bishop on 2014-10-23
[FONT=Arial]I have Ubuntu Studio 14.04 LTS. PulseAudio has been running without incident for 3+ months. I read about qpaeq which would allow me to do a 1/3 octave job on my stereo system. I have a friend who has an I-Phone with a calibrated mic and an RTA app. He cleaned up our church PA in an impressive manner.[/FONT]
 
 
 [FONT=Arial]I loaded qpaeq following the instructions in [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html). Pactl looks like everything should work. However, this is what happens.[/FONT]
 
 
  [FONT=Arial]jnyreb@INDEDEN:~$ pactl load-module module-equalizer-sink[/FONT]
 [FONT=Arial]25[/FONT]
 [FONT=Arial]jnyreb@INDEDEN:~$ pactl load-module module-dbus-protocol[/FONT]
 [FONT=Arial]26[/FONT]
 [FONT=Arial]jnyreb@INDEDEN:~$ qpaeq[/FONT]
 
 
 [FONT=Arial]If I click on any of the controls on the EQ, I get:[/FONT]
 
 
 [FONT=Arial](python:2772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/FONT]
 
 
 [FONT=Arial](python:2772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/FONT]
 
 
 [FONT=Arial]If I use sudo to load the modules and the EQ, I get :[/FONT]
 
 
 [FONT=Arial]jnyreb@INDEDEN:~$ sudo pactl load-module module-equalizer-sink[/FONT]
 [FONT=Arial][sudo] password for jnyreb: [/FONT] 
 [FONT=Arial]25[/FONT]
 [FONT=Arial]jnyreb@INDEDEN:~$ pactl load-module module-dbus-protocol[/FONT]
 [FONT=Arial]26[/FONT]
 [FONT=Arial]jnyreb@INDEDEN:~$ sudo qpaeq[/FONT]
 [FONT=Arial]There was an error connecting to pulseaudio, please make sure you have the pulseaudio dbus module loaded, exiting...[/FONT]
 [FONT=Arial]jnyreb@INDEDEN:~$ [/FONT] 
 
 
 [FONT=Arial]I have searched all of the above ad nauseum and the more I read the confuseder I get. So if anybody has a clue, I could sure use a hint.[/FONT]
 
 
 [FONT=Arial]Thanks[/FONT]
 [FONT=Arial]Charlie Bishop[/FONT]

---

### Post by Mathsterk on 2015-01-01
You should not load the modules as root, that's just a bad idea.

Did you restart pulseaudio as the article mentioned? I've had the exact same problem with qpaeq before, and restarting pulseaudio fixed it.

(in case of laziness)
```
pulseaudio -k
pulseaudio &
```

---

### Post by Redsandro on 2015-02-23
Did you ever find a solution @**Charles_Bishop**?

I have the exact same problem, and all google comes up with is this page and mirrors of this page.

Or if there is a more current way of implementing an equalizer? I find it hard to believe that something as obvious as a mixer is not implemented by default. Especially in 2015.

*[edit]*

Oops. It does not work on digital audio. It works for analog headphones when you select this:

[img]http://i.imgur.com/tJTmAzl.png[/img]

Now it works regarding of the error messages.

---

