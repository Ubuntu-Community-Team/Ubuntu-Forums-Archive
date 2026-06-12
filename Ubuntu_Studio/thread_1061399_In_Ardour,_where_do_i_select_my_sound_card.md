---
title: "In Ardour, where do i select my sound card?"
date: 2009-02-05
forum: Ubuntu Studio
---

### Post by Macfunky on 2009-02-05
I'm not getting any sound in or out of it. I am using the computers built in sound card (I know, i know. I'd say don't use it either but i just want to try out the program first). 

Also for if i get more drawn in by it and consider switching over to it what sound cards/interfaces are known to be compatible with Linux/Ardour? I wouldn't be looking for an amazing/expensive sound card/interface but something of descent quality and value. Any ideas or suggestions?

---

### Post by neu2buntu on 2009-02-06
you would be best to install qjackctl (frontend for jack) and this should allow your inbuilt soundcard to work with ardour. and set jack up for real time!!    heres a good tutorial on getting the most from your sound...........   [http://ubuntuforums.org/showthread.php?t=843012 ]("http://ubuntuforums.org/showthread.php?t=843012")


..

---

### Post by sgx on 2009-02-10
> **Macfunky said:**
> I'm not getting any sound in or out of it. I am using the computers built in sound card (I know, i know. I'd say don't use it either but i just want to try out the program first). 

Also for if i get more drawn in by it and consider switching over to it what sound cards/interfaces are known to be compatible with Linux/Ardour? I wouldn't be looking for an amazing/expensive sound card/interface but something of descent quality and value. Any ideas or suggestions?

m-audio 24/96 PCI is analog/digital/midi, works great in linux, around
$80. Soundcard selection and config in system menu choices, connection of
various apps using qjackctl (called 'jackconnect'  sometimes)
Ardour requires a touch more to start than expected, but google has some tutorial pages
Cheers

---

### Post by Stochastic on 2009-02-11
In Intrepid, just as Ardour starts, the window that requests you to create a new project should have a tab called 'Audio Setup'.  You could also use an external jack control application such as qjackctl (this is most common for people who use many jack applications).

After ardour is started, press Alt+m to bring up the mixer window, and on the output button of the tracks you want to play, double click to bring up the output editor.  Send all your outs through main 1 & 2 for now until you get more comfortable with the program.  Oh, and you may bump into the import audio bug in Intrepid, for some reason you either need to drag/drop audio files into Ardour, or recompile it from scratch to get import functionality.

---

### Post by pgmer6809 on 2009-02-11
> **Macfunky said:**
> I'm not getting any sound in or out of it. I am using the computers built in sound card (I know, i know. I'd say don't use it either but i just want to try out the program first). 

Also for if i get more drawn in by it and consider switching over to it what sound cards/interfaces are known to be compatible with Linux/Ardour? I wouldn't be looking for an amazing/expensive sound card/interface but something of descent quality and value. Any ideas or suggestions?

You might try going to System=>Preferences=>Default Sound Card.
and set your non built in sound card to be the preferred one. Then Ardour may select that one automatically at start up. 
Dont have Ardour installed so I cant say.

---

