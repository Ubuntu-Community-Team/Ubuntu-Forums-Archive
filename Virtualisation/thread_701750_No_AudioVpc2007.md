---
title: "No Audio/Vpc2007"
date: 2008-02-19
forum: Virtualisation
---

### Post by Michel Camire on 2008-02-19
No Audio 

--------------------------------------------------------------------------------

Hello,,

I have installed Ubuntu latest version as a Virtual Machine in Vista Ultimate (Virtual (PC 2007)
Everything work fine except for the sound card wich isn't producing any sounds.
At start up Ubuntu sends the following message;

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

If i look in the "SysInfo applet , there is no sound card repertoried; if i look in System>Preferences >Hardware Info, the Sound Blaster sound card is indeed repertoried.

I'm completely new to Ubuntu Linux and would like to know what is it i must do to have 
audio working in Ubuntu . Does it have anyhting to do with the Gnome module?

Many thanks!

---

### Post by Zimmer on 2008-02-20
Have you tried The Volume control (Alsa Mixer).? The Master Mono may be muted.
Applications >Sound and Video>Volume Control.  
This used to be a common problem with Dapper 6.06.
and
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) 
Because you are running a VM within Windows there may be other conflicts which I have no experience with.

---

