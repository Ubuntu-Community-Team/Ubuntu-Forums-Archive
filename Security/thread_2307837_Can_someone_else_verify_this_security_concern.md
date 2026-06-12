---
title: "Can someone else verify this security concern"
date: 2015-12-28
forum: Security
---

### Post by dokumentamarble on 2015-12-28
I have Ubuntu 15.10 installed on my laptop. I noticed that if I have a terminal window open when I close the lid, I can execute commands in that terminal window before the login screen comes up after opening the screen. I have not fully explored all the possibilities of this login screen bypass but I have been able to replicate the terminal window typing every time. 

Steps to reproduce:
- Open a terminal window (Optionally raise your privilege level)
- With the terminal window actively selected close the laptop lid (To enter a suspended state)
- Wait for the laptop to suspend
- Open the laptop lid and start typing
- Login once the prompt appears
- You should see some of your typed letters in the terminal window. 
- I am sure the timing changes for different laptops but with mine I can manually type fast enough to execute rudimentary commands. An automated attack would likely allow for more complex commands to be executed. 

Just curious if this is unique to me or if others can reproduce it. I have searched the forums and known bugs for Ubuntu 15.04 and I can't find anything related to this. 

.dok

---

### Post by matt_symes on 2015-12-28
Hi

I *cannot* replicate this on Xubuntu 16.04 using Light Locker.

My setup is different than yours is but it's your first metric :)

Kind regards

---

### Post by dokumentamarble on 2015-12-28
Thanks, that might/should help in determine the culprit here. 

I am running a Vanilla 15.10 Ubuntu installation with full disk encryption.

---

### Post by bashiergui on 2015-12-30
Submit it as a bug on launchpad. That way if it's truly a bug it can get fixed by the developers.

---

### Post by maglin2 on 2015-12-31
I have 15.10 with full disk encryption and it doesn't happen here.

---

