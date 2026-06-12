---
title: "Can other distros read my /home?"
date: 2006-04-22
forum: The Cafe
---

### Post by openmind on 2006-04-22
I have /home on a seperate partition from my / folder, if I desert Ubuntu and jump ship to another distribution will it read my /home including any conf files that I currently have set up under Ubuntu?

---

### Post by bscbrit on 2006-04-22
Yes.  Go ahead.

The only problems that you might experience are:

1.  if you use SELinux under Fedora, and then change to another distro that does not understand the SELinux extras.  This should not happen in this case.

2.  if the next distro is using older versions of your favourite applications, there might be an occasional glitch if it does not understand part of a config file.  This is unusual but does occur from time to time.

---

### Post by aysiu on 2006-04-22
[QUOTE=openmind]I have /home on a seperate partition from my / folder, if I desert Ubuntu and jump ship to another distribution will it read my /home including any conf files that I currently have set up under Ubuntu?[/QUOTE] It might--but you could end up with some breakage, as different distros use different config files and may structure them differently.

I would create a new username with the new distro (same /home partition) and then copy over a couple of config files (one by one) to see which ones work (you might have to *chown*--change ownership--of those folders once they've been copied).

---

### Post by openmind on 2006-04-22
Thanks for the quick replies people. I just might give it a go.

Hey bscbrit, do they still "run the rock?" I participated long ago (wow, 20+ years!) ran through the rock too. Never figured out how they got cars to park on that large car park on the other side. ;)

[SIZE=1]*(sigh, a lifetime ago.........)*[/SIZE]

---

### Post by bscbrit on 2006-04-22
Yes, running the Rock still takes place when the Grey Funnel Line is in port, or the brown jobs fancy something physical to do!  The Crabs, on the other hand, usually have more sense or less energy.  And the Rock is no smaller now than when you last ran it!

[For those that don't understand, this post refers to the British armed forces stationed in Gibraltar. Grey Funnel Line - Royal Navy,  Brown Jobs (or Pongoes) - Army.  Crabs - Royal Air Force.  'Running the Rock' is a race from the bottom of the Rock to the Top - although participants tend to be competing as much with their own determination to succeed than with each other.]

---

