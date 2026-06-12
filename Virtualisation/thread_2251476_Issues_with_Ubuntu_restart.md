---
title: "Issues with Ubuntu restart"
date: 2014-11-04
forum: Virtualisation
---

### Post by sudsid on 2014-11-04
Recently I installed the Nvidia-CUDA package. It asked me for a restart.  After restart, my pc starts but doesn't load the desktop (after logging  in)
Note: I have ubuntu x86-64 installed in vmware player.

---

### Post by sudsid on 2014-11-04
I Solved the issue.
Steps:

[LIST=1]
[*]Remove any drivers that may be causing the issue,
[*]open the terminal and type ( open it from the dash, using the ubuntu icon on the left corner); In case you get a blank screen, press ctrl+alt+f1  and login.
sudo apt-get --purge remove nvidia
or
sudo apt-get --purge remove nvidia-current
(Depending on which one you have installed) or deactivate them from the restricted driver settings.

[*]reboot.
The pc should have recovered from the error by now. If not then,

[*]then on a terminal type this:
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

[*]reboot.
[/LIST]

---

