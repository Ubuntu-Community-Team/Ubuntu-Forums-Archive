---
title: "Gnome keyring fails after request for my wifi password. BT-FON shadows my router pas"
date: 2014-10-19
forum: Security
---

### Post by mat125 on 2014-10-19
Hi i have had this problem in the past last week when Ian weisser was helping out. After setting a new password in my router and re-connecting to the internet i get another request for my wifi password then my keyring striaght after that which i then enter. But the strangest thing happens when i monitor my attempt to link up to my wifi, bt-fon shows up shadowing my connection at every switch on and off, and this happens when accessing different devices. Later on a suspect virgin wifi link follows on showing up available. I have never used bt services for tens of years nor would i want to. Later on i went to change my Gnome keyring in my administrators account and i no longer have access to it, ??!! Can a request for the keyring or password be a scam without me knowing it ?? Normally after a password change i now get two or three asking prompts asking for both my wifi password and keyring why ?
Can anyone help i'm locked out of my keyring again strangely ?
I'm using UBUNTU 14.04 LTS ON X86 64 
Thanks.

---

### Post by CitadelUniversal on 2014-10-19
Do you still have access to your root section on Ubuntu 14.04? - if yes then try editing the gnome-keyring via root itself and as a precaution change your root password and user password - also as a side-note go into the "Edit Connection" on network-manager delete the wifi listed as "Example 1, 2,3" the example should be your wifi network and start over from square one again.

Edit:Note: Root password should be the same as your login password.

---

### Post by mat125 on 2014-10-19
Hi Citadel i have not yet changed the keyring because i had the crash notice --- Ubuntu has experienced an internal error 14.04
/usr/bin/gnome-keyring-daemon      
package gnome-keyring 3.10.1-1 ubuntu 4     
problem type crash 
    Title gnome-keyring-daemon crashed with SIGSEGV in dbus message

Since that i have reinstalled the keyring and anything else related in synaptic and completed a few updates. 
Gnome keyring now suggests it is unlocked and accessed on login into Admin.

Will try your suggestion later but i'm thinking about the internal crash at the moment.

Will close this post as i have just run out of time and will leave the problem as unsolved for this PC.
Would like to add do NOT press the software upgrade button do a clean install ONLY !!! p.s 14.04 LTS is not problem free !

---

