---
title: "pd-extended + Jack = nightmare!"
date: 2014-12-02
forum: Ubuntu Studio
---

### Post by prytolukster on 2014-12-02
Dear friends:

 
I'm opening this thread, after trying every single bit of information  i could find over the internet to solve my problem. Lost nights n'  nights trying to get better results, but i'm basically stuck on the same  spot.


 I'm trying to get my pure-data/jack setup on Ubuntu-Studio 14.04 RT kernel.
I've installed every package of KXStudio, and managed to get quite a good audio configuration:


 As i read in many forums that pulseaudio is a common source of issues, **I've got rid of pulseaudio, it isn't installed at synaptics, nor running at all**.

 I'm using qjackctl to configure my jack server, and i'm pretty sure  everything is fine, since i'm able to configure jack as the adudio  output in softwares such as mixxx and audacious, and i'm also able to  use non-configurable (at least for me) software such as Firefox with  alsa->jack configuration, all at the same time. Magic for my eyes n'  ears .

 
My problems start exactly when i try to use jack as the audio output  for pd-extended (same error for regular pd, as a matter of fact).

 To add a short background story, i'm trying (with quite sucess so  far) to use pd-extended to get the some analog sensors (so far, i'm  testing a potentiometer) plugged as analog inputs on my arduino-mega,  connect my Arduino-Mega via StandardFirmata+pduino to pd-extended and  use Jack to provide a Midi output to make "ctlout 1" object to connect  with midi-input-able softwares such as Mixxx, and use it as a midi  controller.

As of Pd-extended configuration, i'm doing quite nice, pd-extended is  able to read my potentiometer values, which are scalled from 0-127 and  are linked to a "ctlout 1" object.

 The problem is, i'm not able to select Jack as an Audio Output on pd-extended!

 
After my jackd server is running (with qjackctl) and it is veryfied  to work with the software/methods listed above, i open a terminal prompt  and try "sudo pdextended" (i need super-user privileges so i don't get  "Permission denied" errors):


 The results are as such:

 [B]
[1]On Pd-extended terminal:[/B]
[I]JACK: unable to connect to JACK server
JACK: server returned status 17[/I]

 [B]
[2]On the terminal screen i used to call "sudo pd extended":[/B]
[I]user@PC:~$ sudo pd-extended
priority 6 scheduling enabled.
priority 8 scheduling enabled.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
watchdog: signaling pd...
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
open: /etc/pd/gem.conf: No such file or directory
open: /home/pirata/.pd/gem.conf: No such file or directory
open: ./gem.conf: No such file or directory[/I]

 [B]
[3]On qjackctl "Messages" screen i get as follow:[/B]
[I]Tue Dec  2 16:55:15 2014: JACK server starting in non-realtime mode
Tue Dec  2 16:55:15 2014: self-connect-mode is "Don't restrict self connect requests"
Tue Dec  2 16:55:15 2014: ERROR: cannot register object path  "/org/freedesktop/ReserveDevice1/Audio0": A handler is already  registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Dec  2 16:55:15 2014: ERROR: Failed to acquire device name : Audio0  error : A handler is already registered for  /org/freedesktop/ReserveDevice1/Audio0
Tue Dec  2 16:55:15 2014: ERROR: Audio device hw:PCH cannot be acquired...
Tue Dec  2 16:55:15 2014: ERROR: Cannot initialize driver
Tue Dec  2 16:55:15 2014: ERROR: JackServer::Open failed with -1
Tue Dec  2 16:55:15 2014: ERROR: Failed to open server

[/I]It seems to me there it's something related to wrong qjackctl  settings, but if that's the case, why is it only related to pd-extended?

 
I'm adding Screenshots of my Qjack Settings:

 [[IMG]http://forum.pdpatchrepo.info/uploads/files/upload-63e70ee8-7e40-4b9c-8716-1d15623a73a6.jpg[/IMG]]("http://forum.pdpatchrepo.info/uploads/files/upload-63e70ee8-7e40-4b9c-8716-1d15623a73a6.jpg")

 [[IMG]http://forum.pdpatchrepo.info/uploads/files/upload-f0f3653b-258e-40c9-9b47-2a923fc8fcbb.jpg[/IMG]]("http://forum.pdpatchrepo.info/uploads/files/upload-f0f3653b-258e-40c9-9b47-2a923fc8fcbb.jpg")

 
Since i cannot take a print-screen of Input/Output devices, that's my list ATM:
[I]hw:PCH - HD Intel PCH (hw:0)
hw:PCH,0 - CX20590 Analog (hw:0.,0) #thats my mic
hw:Loopback - Loopback (hw:1)
hw:Loopback,0 - Loopback PCM (hw:1,0)
hw:Loopback,1 - Loopback PCM (hw:1,1)
(default)[/I]

 
If any useful info is missing, please ask me for it, i'm REALLY into fixing this.

 
Thank you very much,

 
Miguel.

---

### Post by jejeman on 2014-12-02
Why server prefix "jackdmp"?
Why periods = 3 ?
Why sudo to start pd?

As I see you don't use pd to process audio, so why use JACK backend?

And, yes, pd+JACK is nightmare.

---

