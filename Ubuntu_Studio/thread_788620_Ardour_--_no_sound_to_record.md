---
title: "Ardour -- no sound to record"
date: 2008-05-09
forum: Ubuntu Studio
---

### Post by le_vainqueur on 2008-05-09
I am presently having trouble getting Ardour (and Audacity for that matter) to recognize any sort of input.  I previously had Audacity working in 7.04 but have had problems since I installed 7.10.  

The problem I am having is that none of the available input selections will record anything.  I tried plugging my guitar into both the mic and the line in channels.  According to the Ardour manual, I opened up the alsa mixer, but mic was the only option for capture.  The same problems exist when I try to use Audacity.

I have no clue what to do here.  Any advice?

---

### Post by le_vainqueur on 2008-05-10
From my reading, it appears that these sort of problems are solved out of the box when installing ubuntu studio.  I also see that there are many ubuntu studio packages in the repos.  I was wondering if there was a chance that uninstalling Ardour, and installing some/all of the studio packages might be a way to fix these issues.  Any thoughts?

I am open to any other ideas as well.  I'd really like to get this recording business working.  I have a vinyl collection I'm itching to ripping to mp3, and my guitar is just sitting here...


LV

---

### Post by kayosiii on 2008-05-11
What model of soundcard are you using....

Typically you want to make sure that both the capture and mic or line channels levels are set high in the mixer. Record is is on for the right channel and the right microphone channel is selected (a lot of cards have more than one of these)... If you are bringing a mic directly into the soundcard you might also want to locate the microphone booster and put it up.

Second thing to check is that you don't have anything else plugged in that could be detected as a soundcard (eg usb headset, webcam) as it may be defaulting to these....

third thing - with ardour - install and open patchage and make sure you have connections between your input and ardour.

---

### Post by le_vainqueur on 2008-05-21
I am using the chipset that is built into my board.  I'm not sure of a model number.

I don't have anything else plugged in that would be confusing the system.  Also, I have tried both the "line in" and "mic" for all of the available input selections in Audacity (I figured I would go back to the program I originally had working back in the day).  I have my guitar plugged into a preamp so that the volume should be adequate.  In fact, I used this setup to record a quick lick on some software in XP without any complications.  

As to your third comment.  How would I make sure I have connections between my input and ardour?

---

### Post by le_vainqueur on 2008-05-21
I tried running patchage, and this is what I got:

> lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Loading configuration file /home/brandon/.patchagerc
Unable to load file /home/brandon/.patchagerc!
Connecting to Jack... could not connect to jack server.
terminate called without an active exception
Aborted


---

### Post by nalmeth on 2008-05-22
Are you pretty familiar with JACK and Ardour? I don't rule out that you have a more complicated issue, but its possible that you are just missing something small.

Have you created a new track in Ardour? When you do this, JACK should route your first available input source to that track. When you arm the track (clicking the little 'r' on the track), does this do anything? 

Does the connections window in qjackctl show that everything is properly connected when you've done all this?

What 'input selections' are available? 

(Sorry if you've been through this already, but its best to start at the basics)

---

