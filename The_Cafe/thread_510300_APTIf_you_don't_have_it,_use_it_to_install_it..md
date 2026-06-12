---
title: "APT:If you don't have it, use it to install it."
date: 2007-07-26
forum: The Cafe
---

### Post by init1 on 2007-07-26
Today, I was dumped into maintenance mode, and it said 
> The program 'apt-get' is currently not installed.  You can install it by typing:
sudo apt-get install apt
 
:lolflag:

---

### Post by koenn on 2007-07-26
and did that work ?

---

### Post by KIAaze on 2007-07-26
Reminds me of Windows...:lolflag:
That's a bug to be fixed I say!

---

### Post by Jussi01 on 2007-07-26
lol... do you have aptitude still? could use that...

---

### Post by srt4play on 2007-07-26
I've seen that before.  I lol at it.

---

### Post by @trophy on 2007-07-26
> **init1 said:**
> Today, I was dumped into maintenance mode, and it said 
 
:lolflag:

Just another example of the smart-***, elitist attitude that *nix guys sometimes have... I imagine someone put this in there while saying "MWUHAHAHAHA!"

---

### Post by init1 on 2007-07-26
> **Jussi01 said:**
> lol... do you have aptitude still? could use that...
No, it's fine now. I was just in a limited shell. A partition on my HD is messed up, and fschk always freaks out about it and asks me if I want to go into maintenance mode. So I tried it. I'm in normal mode now.

---

### Post by forrestcupp on 2007-07-26
The funny thing is that that is really how you install apt.  I've had to do that before and it works.

---

### Post by m0eman on 2007-07-26
lol, I used to get that quite often before I figured out to change a 1 to 0 in my fstab file (something about scanning a partition type that wasn't supposed to be scanned)

---

### Post by aktiwers on 2007-07-26
Hehe I just typed:
```
aktiwers@HAL:~$ sudo apt-get remove apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apport apport-gtk apt apt-utils aptitude gdebi gdebi-core gnome-app-install
  language-selector python-apport python-apt python-launchpad-bugs
  python-software-properties restricted-manager software-properties-gtk
  synaptic tasksel tasksel-data ubuntu-desktop ubuntu-minimal
  unattended-upgrades update-manager update-manager-core update-notifier wajig
  xubuntu-desktop
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt
0 upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 33,6MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

```
Look what I need to type to confirm! LOL

---

### Post by KIAaze on 2007-07-26
> **aktiwers said:**
> Look what I need to type to confirm! LOL
...and that's where the stupid Windows user just copy/pastes the answer...

---

### Post by ironfistchamp on 2007-07-26
I just typed "Yes, do as I say!"

That was a ****ing stupid thing to do wasn't it?

Ironfistchamp

---

### Post by forrestcupp on 2007-07-26
> **ironfistchamp said:**
> I just typed "Yes, do as I say!"

That was a ****ing stupid thing to do wasn't it?

Ironfistchamp

Now try
```
sudo apt-get install apt
```
and see what happens

---

### Post by ironfistchamp on 2007-07-26
Couldn't find apt. All I did was use dpkg and install a downloaded deb of apt. Then I apt-get installed synaptic and went about reinstalling things and looking for other call software. Ended up installing 70 packages when I only removed a few lol.

---

### Post by guitarmaniac on 2007-07-28
I had that happen to me a day or two ago as well.
Don't know why, I think it was a bad install of ubuntu.

---

### Post by Polygon on 2007-07-28
i get the "could not find the command apt. Type sudo apt-get install apt to install it" when i get a fsck error on startup and it dumps me to a recovery console. I think its a bug thats not major but should be fixed eventually :D

---

### Post by Spike-X on 2007-07-28
> **KIAaze said:**
> Reminds me of Windows...

"Keyboard not detected. Press f8 to continue."

---

### Post by Stone123 on 2007-07-28
> **init1 said:**
> Today, I was dumped into maintenance mode, and it said 
 
:lolflag:

You lost PATH or you have corrupted system. Nothing new. If it happends after more recoveries you have a foulty processor or memory.

I got that from missing last line in apt. And after restart dpkg was broken too. Try dpkg even funnier errors

---

### Post by init1 on 2007-07-30
> **Stone123 said:**
> You lost PATH or you have corrupted system. Nothing new. If it happends after more recoveries you have a foulty processor or memory.

I got that from missing last line in apt. And after restart dpkg was broken too. Try dpkg even funnier errors
No, it was just a limited shell trying to act like the real shell but failing. This came from a bad partition on my HD that fstab was handling.

---

