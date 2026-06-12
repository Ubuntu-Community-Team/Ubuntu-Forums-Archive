---
title: "Ubuntu studio questions"
date: 2007-05-18
forum: The Cafe
---

### Post by falkenberg_cph on 2007-05-18
Hi
I have a couple of question i was hoping somebody might be able to answer:

1. Since i dont have a DVD-burner i decided to make a new install of feisty and then install UbuntuStudio via Synaptic. Worked like a charm. Then i had some Xrun problems, and i read in another thread that i should add something from terminal, so i did.
So this first question is: Do i need to do anything else? should i follow the dapper preparation in the wiki? (actually thats to questions)

2. Not directly UbuntuStudio, but still: I have not been able to create an input to ardour2, i have gotten an output, when i imported a wave-file.
Is there a Qjackctl tutorial anywhere that might work for me? (i'm using a 4 input USB interface, but lets keep it general)

3. What is the future of UbuntuStudio website. Will there be tutorials and other kinds of introductions?

Anyway. Great job so far, you have managed to gather a lot of great programs - oh, especially the low-latency kernel, whoopie.

Thanks
Carsten

---

### Post by jariku on 2007-05-18
> **falkenberg_cph said:**
> 
1. Since i dont have a DVD-burner i decided to make a new install of feisty and then install UbuntuStudio via Synaptic. Worked like a charm. Then i had some Xrun problems, and i read in another thread that i should add something from terminal, so i did.
What precisely did you do in the terminal? Did you add the necessary repositories? Like so:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Or, did you run this command to enable JACK to be run as a normal user?

```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
```

Or something else?

EDIT: The second command (the JACK stuff) might help with the Ardour problems if you haven't already done so.

---

### Post by falkenberg_cph on 2007-05-18
i did both. i just couldnt find that second quote of yours. Thats why my explanation got a little vague.

The second command did help a little with xruns. And xruns is not my main problem atm.
My main problem is probably: now what? Ardours documentation is really speaking generally (so does JACK documentation). I did however find this: [http://quicktoots.linuxaudio.org/toots/Jack_Ardour/](http://quicktoots.linuxaudio.org/toots/Jack_Ardour/) - but i havent had the time to look at it this morning.

Carsten

---

### Post by ReiKn on 2007-05-18
> **falkenberg_cph said:**
> Hi
I have a couple of question i was hoping somebody might be able to answer:

2. Not directly UbuntuStudio, but still: I have not been able to create an input to ardour2, i have gotten an output, when i imported a wave-file.
Is there a Qjackctl tutorial anywhere that might work for me? (i'm using a 4 input USB interface, but lets keep it general)


First create a new track in ardour from the session menu (or by right-clicking the track-part of the GUI). This should add a Audio1/in1 Audio1/in 2 pair to writable clients / input ports. It should also connect them to your capture devise (on the readable clients/output ports section of qjackctl) . 

You can manage the connections by choosing the pair which you want to connect and pressing 'connect' or simply by dragging the output to the desired input. 

As attachments are two screenshots how this looks like on my system. 

I don't know if I was clear enough or if I understood your problem correctly so ask again if this was no help :)

---

### Post by falkenberg_cph on 2007-05-18
I think i did exactly that. guess not. I'll have to try it again tonite.

thanks
Carsten

---

### Post by ReiKn on 2007-05-18
If the connections are ok in jack you could also check your volume control settings (double-click the loudspeaker tray-icon) and choose your recording device and adjust levels.

---

### Post by falkenberg_cph on 2007-05-20
Hmmm. I did with jack as ReiKn told me, also looking at [this page](https://help.ubuntu.com/community/HowToJACKConfiguration). But it is still not working. However i dont think its my jack/ardour setup - i think the problem is with alsa and the general setup. I have posted 2 screenshots: one showing the sound setup, one showing alsamixer in terminal (just type alsamixer in terminal ):

What puzzles me is:
1. in the sound setup, what should i use in the audio conferencing part?
2. look at alsamixer, it apparently is connected to my onboard realtek crap sound card. Why is that, and how on earth do i change it?

Thanks
Carsten

---

