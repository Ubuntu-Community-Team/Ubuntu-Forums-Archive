---
title: "[SOLVED] Can't turn off &amp;quot;Background Snapshots&amp;quot; in VMWare Server"
date: 2008-01-21
forum: Virtualisation
---

### Post by A-dogg on 2008-01-21
I have both virtualbox and vmware installed. virtualbox runs fast, but try as i may i can't get it to recognize usb drives. so I installed vmware, which runs incredibly slow. i read some posts that recommend unchecking "background snapshots" and setting it to allocate all drivespace at once, rather than as an expanding disk. Problem is when I go to uncheck background snapshots, it tells me I don't have the permissions required to do this....

Any thoughts? i may reinstall from scratch to see if that solves it for some reason.

---

### Post by fjgaude on 2008-01-21
Once you have set the hard drive space, it is fixed in VMware. You have to create a new vm guest, and set it drive space as desired.

Also for speed, use only one core, or CPU, at setup time of the guest.

---

### Post by A-dogg on 2008-01-21
thanks for the reply, except my real problem was that I can change anything in the "Host settings." When I try to turn off background snapshots or limit the amount of host RAM for all running virtualizations, and click OK, the program tells me "You don't have the permission to execute this operation."

How do I get around that? I uninstalled vmware server and reinstalled and have the same problem...

:confused:

---

### Post by fjgaude on 2008-01-21
I don't know... mine does the same thing but I guess I don't see a need to change from the default. Perhaps starting the program from a terminal as root. I've never done that, but you might wish to try.

Likely this is one price we pay for the free version of VMware.

---

### Post by A-dogg on 2008-01-22
Figured it out. You need to run vmware from the command line as sudo. only then will it let me change the host settings...

---

### Post by fjgaude on 2008-01-22
Okay, I won't forget that... someone else will likely wish to do the same thing.

---

### Post by pellgarlic on 2008-02-10
> **A-dogg said:**
> Figured it out. You need to run vmware from the command line as sudo. only then will it let me change the host settings...

just fyi - it's advisable to use "gksudo" rather than just "sudo" when launching a "gui" program (as opposed to a command-line prog), to avoid messing up your .ICEauthority file...

see [this link]("http://www.psychocats.net/ubuntu/graphicalsudo") for details

it happened to me once, and i always use gksudo now :)

(i'm still looking for a proper fix for this vmware issue - i don't like having to run a prog as root just to change a setting...)

---

