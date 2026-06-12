---
title: "VMWare Workstation sound issues"
date: 2008-09-13
forum: Virtualisation
---

### Post by GeordieToddy on 2008-09-13
I keep getting the message:

> Cannot connect virtual device sound. No corresponding device is available on the host.


On every startup of VMware Workstation, and, needless to say, I don't get any sound.

Sound works fine in Ubuntu for most programs.

I'm using OSS not ALSA, with my onboard sound (got sick of trying to make my Creative X-fi work) on Ubuntu Studio (Hardy)

Had a look around google and these forums and can't find anything similar.
Any ideas would be great, even if they don't work, they may help me to figure out the problem.

Thanks,
Toddy.

---

### Post by GeordieToddy on 2008-09-15
*bump*

come on, somebody must have SOME ideas...

:-k

---

### Post by Geekboy on 2008-09-17
I am also having this issue.  The sound device fails as soon as I power up the Vmware session.

---

### Post by KnightOnline on 2008-09-29
Same situation, sound works perfectly in Ubuntu but VMWare doesn't recognize the sound card

---

### Post by articfox on 2008-10-09
I am having the same problem.  Any ideas?

---

### Post by Valok on 2008-10-16
I've also got this same problem.

---

### Post by ee19921 on 2008-10-28
I am using VMware server. Just now did the steps mentioned in this [thread]("http://ubuntuforums.org/showthread.php?t=331175") for VMware server. So far so good!

did you try it?

---

### Post by MarshallClan on 2008-12-29
Hola,
 Without following the above mentioned post, I have audio working in VMWare Server 2.0 installed from this: [http://ubuntuforums.org/showthread.php?t=973729](http://ubuntuforums.org/showthread.php?t=973729)  tutorial. (seemingly hit or miss from mixed results with XP guest). 
 From the "Inventory" pane with your VM highlighted> go to the "Summary" tab (make sure you see an audio device added- if not go to the "Commands" section and "Add Hardware" and choose "Sound Adapter") select "Audio" device drop down> go to "edit" check the box for "Connect at power on" and under "Connection" choose /dev/dsp.     Power on the VM - you should see a speaker icon in the status area and it will NOT show a red X when to actually "connected" to the server . Inside the VM (XP in my case) I went to "Control Panel"> "Sounds and Audio"> "Audio" tab> "Sound playback" section> "default device" drop down menu and RE-choose "Creative Sound blaster PCI" device. Sound was then heard. In Host machine "Intrepid" Sound Preferences are all set to "auto detect".  VMWare seems weak in the audio dept. and I have had much better luck with Virtualbox audio functions. Best of luck!
_-K-_

---

