---
title: "Going to infect Virtual Machine any Ubuntu precautions I should take?"
date: 2009-03-19
forum: Security
---

### Post by marco123 on 2009-03-19
Hi.  I was bored yesterday and came up with the idea of setting up an XP virtual machine, not patching it, running only the Windows Firewall, then going to dodgy sites like crackz.russia et cetera to see how long it takes before I get owned.

My entire /home directory is backed up on 2 separate external hard drives and I'll unmount my secondary internal HD.

Are there any changes I should make to permissions? Especially Virtualbox permissions, to maybe isolate Virtualbox?  Will it effect my /home directory or just the .virtualbox folder/XP virtual drive?

Cheers, Marco.

---

### Post by albandy on 2009-03-19
simply don't add shared folders to virtualbox

---

### Post by marco123 on 2009-03-19
> **albandy said:**
> simply don't add shared folders to virtualbox

Seriously?  That's all?  I'm gonna have some fun then.:D  I'll post some screenshots after.:D

Cheers, Marco.

---

### Post by albandy on 2009-03-19
try to not have any windows system exposed on your network because some viruses can infect windows sytem throught windows open ports.

---

### Post by marco123 on 2009-03-19
> **albandy said:**
> try to not have any windows system exposed on your network because some viruses can infect windows sytem throught windows open ports.

It's alright we've only got 2 PC's here my desktop and my daughters laptop (wirelessly connected) and they're both Ubuntu 8.10.:D

Cheers, Marco.

Edit:  That's a thought, I wonder if the firewall in my Router is going to scupper my plans.:(

---

### Post by albandy on 2009-03-19
> **marco123 said:**
> It's alright we've only got 2 PC's here my desktop and my daughters laptop (wirelessly connected) and they're both Ubuntu 8.10.:D

Cheers, Marco.

Edit:  That's a thought, I wonder if the firewall in my Router is going to scupper my plans.:(

it could, do a port scan in the virtual machine and redirect these ports in the router to your virtual machine.

Also you need to configure the virtual machine networking interface to use eth0 or wlan0 directly without nat.

---

### Post by marco123 on 2009-03-19
> **albandy said:**
> it could, do a port scan in the virtual machine and redirect these ports in the router to your virtual machine.

Also you need to configure the virtual machine networking interface to use eth0 or wlan0 directly without nat.

I'll try that.  If all else fails I'm just going to install CoolWebSearch. lol

Cheers, Marco

---

### Post by Therion on 2009-03-19
> **marco123 said:**
> Hi.  I was bored yesterday and came up with the idea of setting up an XP virtual machine, not patching it, running only the Windows Firewall, then going to dodgy sites like crackz.russia et cetera to see how long it takes before I get owned.
Dude, serioulsy?  LOL...  

Please micro-blog everything and report back with details.  I'm curious how many seconds it takes.





/weBcrackZorZ.ru for the win!!!

---

### Post by marco123 on 2009-03-19
This is actually harder than it sounds!

Every keygen I've downloaded so far has been genuine!:lolflag:

Edit: All I seem to be able to find are websites explaining how to remove things like CoolWebSearch.  Trying torrent sites now.

---

### Post by lovinglinux on 2009-03-19
> **marco123 said:**
> Hi.  I was bored yesterday and came up with the idea of setting up an XP virtual machine, not patching it, running only the Windows Firewall, then going to dodgy sites like crackz.russia et cetera to see how long it takes before I get owned.

Rofl, I thought I was bored recently, but you won. I was thinking about asking in the forums for cool programs to install, just to waste some time, but this is a top notch idea.

Please report back with your findings.

---

### Post by marco123 on 2009-03-19
Story so far:  Couldn't do it with crack sites as soon as I hit the pr0n sites though... boom, I got owned. :D

Pics so far attached more coming.:D  (Safe for work, don't worry.)

Cheers, Marco.

---

### Post by marco123 on 2009-03-19
It wants me to register to remove all the threats that are on my PC.  Oh noes what am I gonna do.;)

Cheers, Marco.

Edit: All websites are now being re-directed, and hidden services and processes are running.

---

### Post by lovinglinux on 2009-03-19
Did you get all those just visiting pr0n sites or did you installed something they asked for?

---

### Post by marco123 on 2009-03-19
> **lovinglinux said:**
> Did you get all those just visiting pr0n sites or did you installed something they asked for?

I clicked on every popup and install dialog I saw.:D

Cheers, Marco.

---

### Post by marco123 on 2009-03-19
Oh well, I've deleted the virtual machine now, didn't touch my /home partition or Ubuntu in any way.  Not quite as fun as I thought it would be, satisfying though; better than being stuck outside in the sun. 8-[

Cheers, Marco.

---

### Post by inuit-joe on 2009-03-23
Nice atempt, im farming windows based viruses myself could be fun.
exept im just using wine.
ive actuly heard bad things if u run them in wine so im not going to run them at all.
but i just like the idea of having viruses sitting there like trophies...
man i have no life :(

---

### Post by philsson on 2009-04-08
:popcorn:.....



But you did have a really nice OSX skin there. I run a MacBook with Ubuntu on it, would be nice to have that skin so I can yoke even more with my friends.. Would you mind telling me where to get it? ;)

---

### Post by marco123 on 2010-01-08
> **philsson said:**
> :popcorn:.....



But you did have a really nice OSX skin there. I run a MacBook with Ubuntu on it, would be nice to have that skin so I can yoke even more with my friends.. Would you mind telling me where to get it? ;)

Oops, sorry about the super-late reply, I didn't realise anyone had added to this thread until now.

Theme: [http://www.gnome-look.org/content/show.php/Cybertron+Leopard?content=69672](http://www.gnome-look.org/content/show.php/Cybertron+Leopard?content=69672)

Icons: [http://www.gnome-look.org/content/show.php/MacUltimate+Leopard?content=82844](http://www.gnome-look.org/content/show.php/MacUltimate+Leopard?content=82844)

Sorry again.:oops:

---

### Post by dogdo on 2010-01-09
> **marco123 said:**
> Oops, sorry about the super-late reply, I didn't realise anyone had added to this thread until now.

Theme: [http://www.gnome-look.org/content/show.php/Cybertron+Leopard?content=69672](http://www.gnome-look.org/content/show.php/Cybertron+Leopard?content=69672)

Icons: [http://www.gnome-look.org/content/show.php/MacUltimate+Leopard?content=82844](http://www.gnome-look.org/content/show.php/MacUltimate+Leopard?content=82844)

Sorry again.:oops:

Correct me if im wrong but wasn't there a story recently of ubuntu getting infected by gnome screensavers-are the above links safe?

---

### Post by cariboo on 2010-01-09
The screensaver in question was a .deb, which came from an untrusted source, if you are unsure where the .deb came from don't install it. That being said, you can always open up the archive, including debs, to check out the contents, if you aren't completely sure if it is safe or not.

---

### Post by Blue Dolphins on 2010-01-09
*******, Are you serious?  Go out and get some fresh air, it'd do you some good.

---

