---
title: "Keyboard freezes when switching from host/guest and back"
date: 2011-11-21
forum: Virtualisation
---

### Post by r_avital on 2011-11-21
Hi, all, 

Here's the problem:

Two machines running Lucid 64-bit 2.6.32-35-generic, both running VMWare  Player 4.0.1.  Both have WinXP SP3 as a guest under VMWare Player.

One functions perfectly.
The other displays this behavior:

1. Switch into the Guest (WinXP) and launch Notepad.  Type some characters.

2. Switch back to the host (Lucid), launch a terminal or gedit -  keyboard doesn't type at all.  I need to unplug/replug the keyboard to  fix this, then it types nice and pretty.

3. Switch back to the guest, try to type in notepad - doesn't type.  I unplug/replug the keyboard, types nice and easy.

4. Switch back to the host - same behavior as before, won't type.  Same remedy, back and forth between guest and host.

Again, the other machine does not display this behavior.

Both have a USB port with a splitter on it, to which I connect keyboard/mouse PS/2 cables from a KVM.

Any ideas?  Any keyboard related entries in any of the guest VM configuration files that may need tweeking?

Thanks in advance

---

### Post by r_avital on 2011-11-22
Well, no responses, but believe it or not, the solution was a very specific PS/2 to USB Y-cable adapter, available from adesso.com.  Specifically, the ADP-PU21 "Adesso® PS/2 to USB Adapter for Keyboard and Mouse"

Unbelievable, right? It won't turn on the Num-Lock or Caps-Lock lights, but the keyboard reacts correctly.  Small inconvenience.

---

