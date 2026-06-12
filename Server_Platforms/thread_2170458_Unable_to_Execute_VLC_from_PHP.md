---
title: "Unable to Execute VLC from PHP"
date: 2013-08-26
forum: Server Platforms
---

### Post by Seemant_Shankar on 2013-08-26
I am running uBuntu 12.04.3, 32 bit OS on a 8 CPU, 8GB RAM 64-bit Intel Xeon machine. I have installed all backports as well.

I have this problem which is eating my head for the last 3 days. I created a play.sh file with the following code...

```
[COLOR=#262626][FONT=arial]#! /bin/sh[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]vlc -vvv sasural.ts[/FONT][/COLOR]
```

Where sasural.ts is a video file that resides [COLOR=#262626][FONT=arial]under home and in the same level as Apache. I am invoking the .sh file by using the following PHP code...

[/FONT][/COLOR]```
[COLOR=#262626][FONT=arial]shell_exec('play.sh');[/FONT][/COLOR]
```[COLOR=#262626][FONT=arial] I also tried both the [/FONT][/COLOR][COLOR=#262626][FONT=arial]exec() / system() methods to invoke the .sh file.[/FONT][/COLOR][COLOR=#262626][FONT=arial]

Whenever I do so, I get the following message...

[/FONT][/COLOR][COLOR=#b22222][FONT=arial]*VLC media player 2.2.0-git Weatherwax Command Line Interface initialized. Type `help' for help. > Shutting down.*[/FONT][/COLOR][COLOR=#262626][FONT=arial]
[/FONT][/COLOR][COLOR=#262626][FONT=arial]
play.sh works if I execute it from the terminal command prompt outside of  the PHP code. I guess I am doing something wrong when I invoke it from within PHP.

I have linked all directories in Apache, etc. tried every trick in the book but to no avail! I am losing my brains and my nuts over this issue! Is there anybody out there who knows what is going on?


[/FONT][/COLOR]

---

### Post by Azdour on 2013-08-26
Have you tried with the full path to sasural.ts in your play.sh script?

---

### Post by Seemant_Shankar on 2013-08-26
Thanks Azdour. Unfortunately, yes, I have tried doing that. It still did not pick it up. What concerns me is the fact that VLC tells me that its shutting down. This ONLY happens when I run if from the PHP script and not when I run the .sh file from the command prompt.

---

### Post by Azdour on 2013-08-26
Since VLC is a graphical application maybe VLC is having problems finding the correct X DISPLAY to open on.  I wonder what user your PHP shell_exec is being run under.  Could it be trying to run as www-data the Apache2 user?  Since www-data is not logged in there is no X Display running.

How about adding the following to your play script before you call vlc:

export DISPLAY=:0.0

or

export DISPLAY=:1.0

UPDATE: after having Googled for similar questions I have also found the following -

> you need to add the user apache runs as (maybe www-data or apache) to the group 'video' in your /etc/groups file

---

### Post by Seemant_Shankar on 2013-08-28
VLC has a non GUI version as well known as noX. Since the server is a headless kind I have installed that on my machine. Therefore there is no need to run it with a Display parameter. 

The solution should be pretty straightforward. I don't know where I am going wrong.

---

### Post by Azdour on 2013-08-29
Hi,

I do not know much about what you are trying to do but you are trying to play a video via VLC.  So at some point that video needs to be displayed on a display.  Where are you aiming to view this video, I'm guessing not on the headless server but are you trying to stream it to the computer viewing the php page?

---

### Post by Seemant_Shankar on 2013-08-31
Yes Azdour, I am planning to stream the file out of the headless server to a set top box on the network. The server just needs to stream the video out using a command line shell file that I am trying to call via a PHP page.

---

### Post by Azdour on 2013-09-09
Hi,

Sorry I'm not sure what to suggest next.

---

### Post by Habitual on 2013-09-09
try ```
 [COLOR=#262626][FONT=arial]#!/bin/bash[/FONT][/COLOR] 
```instead of ```
#! /bin/sh
``` ?
does a space in #! /bin/sh matter? I've never utilized sh but it looks "funny"

---

