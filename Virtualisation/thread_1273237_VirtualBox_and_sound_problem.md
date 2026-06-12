---
title: "VirtualBox and sound problem"
date: 2009-09-23
forum: Virtualisation
---

### Post by Pengwyn44 on 2009-09-23
VirtualBox and sound problem
I am running XP in a virtual computer based on Ubuntu Jaunty and Sun Virtual Box 3.0.6. When XP starts up I hear the normal Windows sound.
The sound Host Driver is set to PulseAudio as recommended by Sun.
The Controller is set to ICH AC97.
My problem is that XP will not recognize an Audio CD but will recognize a data CD.
Any suggestions please?

---

### Post by etnlIcarus on 2009-09-23
I'm not certain but that probably has something to do with the way linux handles audio CDs and the limited way in which virtualbox emulates the CD/DVD drive.

Just a quick google turned up [this bug](http://www.virtualbox.de/ticket/3494). I wouldn't be surprised if it also affects linux.

Do you need help playing back audio CDs in Ubuntu, itself?

---

### Post by Pengwyn44 on 2009-09-23
Thanks for your comments and the link URL. My experience is the same as some of the contributers on the link. With "Enable pass through" ticked XP then recognizes the CD as audio and Windows Media plays the video part but not the audio. It looks as if we will have to wait for VirtualBox to fix it.


This problem is for me a stepping stone to my vital problem. I need to run one Windows program only, namely IBM ViaVoice which is a dictation program.
Currently XP reports that my voice input is nil!
I have a windows machine solely for this purpose but was hoping that VirtualBox would enable me to do away with Windows entirely.
Thanks again for you help.

---

