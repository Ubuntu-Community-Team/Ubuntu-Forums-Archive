---
title: "Problem with monobristol GUI"
date: 2016-05-31
forum: Ubuntu Studio
---

### Post by oscalypso on 2016-05-31
Hi

after install **Monobristol** (GUI to launch bristol synths)

when i launch it in terminal, I get the message :
"Cannot open assembly '@expanded_libdir@/monobristol/monoBristol.exe':File not found"

I can launch each of the synth by typing** startBristol -nameOfTheSynth** (startBristol -b3 , for example)
but not the GUI.

I have seen in Synaptic package manager that some package used by monoBristol are broken, and they don't repair when i click "repair broken package"

Any Ideas ?

---

### Post by oscalypso on 2016-05-31
Thanks to the #ubuntustudio channel on irc.freenode.net

Here's the fix:

after installing monobristol,
launch it with

**mono /usr/lib/monobristol/monoBristol.exe**

---

