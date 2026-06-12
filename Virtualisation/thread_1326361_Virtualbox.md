---
title: "Virtualbox"
date: 2009-11-14
forum: Virtualisation
---

### Post by AmpersUK on 2009-11-14
As I couldn't use my cdrom drives with Virtualbox OSE and nobody seemed to have a solution here, I decided to delete Virtualbox OSE and go to the VirtualBox website and download the full version.

Naturally I deleted the OSE version first.

Everytime I try to load the 32-bit 9.10 version (that's the flavour of Ubuntu I own) I get an error message stating that I cannot load this when there is already a copy of the OSE version on my machine.

As I have already deleted it using Applications/Ubuntu Software Centre, I am at a loss of what to do next if I want Virtualbox installed.

The only other alternative is to purchase a copy of Canonical's Parallels virtual machine software unless someone here can suggest a remedy.

Please bear in mind that I am seventy and a bit of a novice where Linux is concerned.

Microsoft have just sent me a free copy of a Windows 7 32-bit DVD as well as a free copy of their 64-bit version, also on a dvd. I must admit, I am tempted to remove Linux and stick with something I am completely familiar with.

Ampers
[]("http://www.finchleyarrow.co.uk/admincentre.php")

---

### Post by gdonwallace on 2009-11-14
First thing I would do is check for virtualbox OSE  in synaptic.

From System  --> administration --> Synaptic package Manager.  Enter your login password and synaptic will start.  There are three buttons at the top left side of synaptic.  Click the first one to "reload" the repo information for Synaptic to make sure everything is up to date.  Next, in the box next to 'quick search' type <b>virtualbox</d>  This will list quite a bit of stuff.  While looking through this, look for anything that has a green box next to it and is labled virtualbox,  Synaptic has a better way of uninstalling most program from Ubuntu.

Next you will want to remove your profile information.  From applications --> accesories --> terminal.  This will launch a terminal session for you and put You in your home directory.  Next type <b> sudo rm -r .virtualbox*</b?  This will remove any profile information left from Virtualbox OSE.  (This can also be done through the nautilus file manager.  Places --> Home.  Although depending on the permissions of the directory, you may not be able to delete through nautilus; hence the terminal option to delete.)

Hope this works for you.

---

### Post by AmpersUK on 2009-11-14
Thank you for this. The first part worked straight away, but the second part didn't achieve anything. However, I marked all the hidden files visible, and when I clicked on .virtualbox and deleted it, it did delete without a problem and all is well.

There is a sudo code to use before nautiolus that begins with a g which I have forgotten. This allows you to put in your password and use Nautilus as root. Do you remember these three or four letters beginning with G, I think the second letter is a K.

---

### Post by Jose Catre-Vandis on 2009-11-14
> **AmpersUK said:**
> Thank you for this. The first part worked straight away, but the second part didn't achieve anything. However, I marked all the hidden files visible, and when I clicked on .virtualbox and deleted it, it did delete without a problem and all is well.

There is a sudo code to use before nautiolus that begins with a g which I have forgotten. This allows you to put in your password and use Nautilus as root. Do you remember these three or four letters beginning with G, I think the second letter is a K.

```
gksudo nautilus
```

Only use gksudo when running graphical apps as root, otherwise just use sudo.

---

### Post by AmpersUK on 2009-11-14
Thanks for that, I had completely forgotten it.

---

