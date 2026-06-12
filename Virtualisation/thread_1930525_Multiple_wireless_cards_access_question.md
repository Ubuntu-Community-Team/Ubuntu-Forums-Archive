---
title: "Multiple wireless cards access question"
date: 2012-02-23
forum: Virtualisation
---

### Post by nchewgum on 2012-02-23
Hi, total noob here and im having some trouble using virtualbox on ubuntu 10.04 host with winxp guest.

basically i have 2 wireless cards, 1. broadcom bcm14313 and 2. rtl8187, i have them both working fine as wlan0 and wlan1.

what i would like to do is use wlan1 in the virtual machine at the same time i am using wlan0 on host.
my only problem is that when i do this, the guest os (win xp) connecst only to wlan1 which is what i want it to do, but my host (ubuntu 10.04) connects to both wlan0 and wlan1.

to get to the question now, is it possible to keep one connection active (wlan1) but block the host from using it somehow so only the virtual machine can use it?

ANY help would be much appreciated, and sry if my question is long winded lol.

thanx in advance

---

### Post by matt_symes on 2012-02-23
Hi

You could drop the interface in 10.04 in the virtual machine.

```
sudo ifconfig wlan1 down
```

Ubuntu would not be able to use wlan1. Only XP would use it. This would not persist after shutting down the VM so you may want to save its state (or edit the config files in Ubuntu).

That is one way to achieve what you want - i think ;).

Kind regards

---

### Post by sffvba[e0rt on 2012-02-23
*Thread moved to **Virtualization**.*


Title edited too.



404

---

### Post by nchewgum on 2012-02-23
> **matt_symes said:**
> Hi

You could drop the interface in 10.04 in the virtual machine.

```
sudo ifconfig wlan1 down
```

Ubuntu would not be able to use wlan1. Only XP would use it. This would not persist after shutting down the VM so you may want to save its state (or edit the config files in Ubuntu).

That is one way to achieve what you want - i think ;).

Kind regards
thanks for the reply,

10.04 is the host so the vm is running xp (my bad, didnt make that clear)

however after running ifconfig wlan1 down i have no connectivity when using wlan0, weird bcause wlan1 is the one that's down.

is there any way i can stop ubuntu from trying to connect to wlan1 while keeping it active (connected) so the vm can use it?

i know its a bit confusing lol, appreciate the help though.

---

### Post by nchewgum on 2012-02-24
Anyone?

im sure someone can answer this, right? lol

---

### Post by matt_symes on 2012-02-24
Hi

I have never tried to do what you are trying to do so this is a total shot in the dark.

Does it help if you disable the interface from network manager ?

Edit connections->(select interface)->ipv4->Method->Disable.

Like i said, a total shot in the dark.

Kind regards

---

### Post by nchewgum on 2012-02-24
im using wicd manager and cant find "edit connectins"

---

### Post by matt_symes on 2012-02-24
Hi

I need to create an XP VM on my laptop for some testing i want to do.

I will try to recreate your situation (as i have a spare wireless dongle as well as my built in card) and see if i can achieve what you are trying to do.

I will post back in the next day or so if no one else jumps in with the solution.

If you find the solution then please post it.

Kind regards

---

### Post by nchewgum on 2012-02-24
thanks alot for your help, 
.Reminder: it is the built in card that i want to use on the vm,

doing it the other way around ie. using the usb card in vm would be much easier as the vm cannot share the device, but i need to have packet injection capabilities wich my built in broadcom card does not have.

cheers!

---

### Post by nchewgum on 2012-02-26
I had to opt out for the easier setup, use the built in card in host os and the usb one in the vm. im trying to use metasploit and I realized that i dont really need injection (at all lol).
using the usb card is a piece of cake, just went to devices and imported the device.

if anyone does find a solution to the above setup however i would be interested in trying it out.
thanx

---

