---
title: "Cannot log in to Ubuntu Studio after crash"
date: 2015-01-21
forum: Ubuntu Studio
---

### Post by ATMarsden on 2015-01-21
I cannot log in to my account on this computer, after problems with qjackctl and Audacity caused a crash, and the session hanged, forcing me to perform an unsafe shutdown (i.e. holding the power button).

I can log in to the Guest account, and I have created a new account from the terminal, which also works fine. I can also log into the proper account from TTY.

When I try to log in, the following happens:

[LIST]
[*]Login screen appears.
[*]If incorrect password is typed:
[LIST]
[*]Notification of incorrect password, and return to login screen.
[*]Nothing is broken here.
[/LIST]

[*]If correct password is typed:
[LIST]
[*]Login box disappears
[*]Interface reloads.
[*]"Ubuntu Studio" loading bar appears
[*]"NVIDIA" splash appears
[*]Login screen returns
[/LIST]
[/LIST]

It doesn't matter whether I select XFCE or Ubuntu Studio in the "session selector", this happens.

Sequence of events prior to problem:

[LIST]
[*]I had Chrome and Spotify open.
[*]Opened QJackCtl, started JACK server
[*]Opened Audacity
[*]Recorded from microphone into Audacity.
[*]Playback wouldn't work, checked sound settings.
[*]Sound settings were normal
[*]Closed JACK server, closed qjackctl
[*]Inwardly cursed myself for forgetting to close Audacity before qjackctl
[*]Changed input on Audacity to ALSA instead of JACK
[*]Audacity hangs, force quit from System-Monitor
[*]Go to save open tabs on Chrome, ready to reboot. "Bookmark all tabs" hangs after clicking "Save".
[*]"Unresponsive" dialog comes up for Chrome, I click "close"
[*]Go to close Spotify, but it returns as unresponsive, I click "close"
[*]Wait a couple of minutes, neither Chrome nor Spotify is closing down as instructed.
[*]Try to shut down from user menu, but nothing happens after pressing button.
[*]Hold down physical power button for 5 seconds, forcing shut down.
[*]Restart computer, and above problem presents.
[*]Restart computer with NO peripherals except trackball, above problem still present.
[/LIST]

---

### Post by ibjsb4 on 2015-01-22
Can you log into your problem account from tty?  That would bypass your display manager.  Have you tried resetting the DM (lightdm or gdm)?

Can you update and upgrade without problems?

Anything in /var/crash/ that would help?

Can you boot using recovery mode?

Just fishing :)

---

### Post by ATMarsden on 2015-01-22
I can log in just fine through tty.

I don't know how to reset DM

Updating and upgrading worked without problem. I also uninstalled the programmes that I had installed since the previous reboot (2 DLNA server programmes and Celestia).

There is no output from JACK or Audacity in /var/crash/, and a Google Chrome report that was older than the problem.

I haven't tried recovery mode.

However, I've managed to copy my files and Chrome and Thunderbird profiles over to the new account, which was the only thing really stopping me from just giving up...

I'm going to call it quits on this, as the legwork to recover the old account isn't worth it now that I have all of my files back.

Thanks anyway, and sorry for suddenly closing the thread before it really started!

---

