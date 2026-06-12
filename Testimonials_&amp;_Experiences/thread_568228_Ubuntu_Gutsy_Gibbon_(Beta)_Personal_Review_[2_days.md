---
title: "Ubuntu Gutsy Gibbon (Beta) Personal Review [2 days using thus far.]"
date: 2007-10-05
forum: Testimonials &amp; Experiences
---

### Post by Mellowdrone on 2007-10-05
I'm using:

A Gigabyte GA-P965-S3 Motherboard
Intel Dual Core, E6400
1gb DDR2
Nvidia 7900GS
Samsung 193P LCD [Digital]
M-Audio Audiophile 24/96

I've not touched Ubuntu for a long while. As a matter of fact, I haven't touched it at all since 6.06, Dapper Drake. Over the course of that time, I've been using Sabayon Linux 3.3 and Sabayon 3.4a, both of which I've been extremely happy with. Per a bug with the (now) outdated, trial version of Gnome (before the 2.20 release), Sabayon 3.4a ran extremely well minus one issue regarding jpegs failing to load after a reboot. I'd reboot, and oddly the jpegs would disappear never to be seen again by any program except Gimp. I've no clue why this is, but I hope it's found/fixed in the later versions.

Regardless, Ubuntu Gutsy Gibbon, the recently released beta, I've found to be a joy to use. If initial trials are any indication, I might actually use this as my primary operating system. I've updated several packages via Synaptic, although it wasn't a painful upgrade. For me, being a 56k user, the download of Ubuntu took roughly two days of my time. The packages I've upgraded to since the install took roughly 100mb, so around 800mb of files (including the CD) I was forced to grab over the course of three or so days.

The only issue I've had thus far was one that did freak me out a bit. After the initial boot of Ubuntu, I'd upgraded several packages overnight (including some Compiz additions, etc.), and found that, on a reboot, Ubuntu's monitor settings failed and I was forced to enter the screen modifier new with this version of Ubuntu (I believe). I reset things as they were. When I rebooted, my system displayed normally, however Compiz simply refused to load as a result. Ultimately, the fix was to save the old (after-install) xorg.conf over the newly created xorg.conf by the program. (????) The system is running normally and rebooting normally, now. I've no clue what the issue was.

The system is operating normally, and things are setup as they were in Sabayon. Overall, the stability of the system is the same as Sabayon, however, in retrospect, Ubuntu seems 'snappier' than Sabayon on this system. I am completely unsure why. Don't mistake me, however - this is a dual core system. Not a single program I've tried feels "lagged" on either OS.

If there are any other issues, I'll post them here, but for now I'm upgrading with Synaptic as I see newer packages fitting for me to grab. After two days, she's running well. Thanks, Ubuntu crew. If the primary release of Gutsy proves to be solid, I'll definitely try to throw a donation your way.

---

### Post by por100pre1 on 2007-10-05
Good review, thanks for posting. :)

---

### Post by Mellowdrone on 2007-10-05
Absolutely, por100pre1.

I also wanted to add another note in regards to the issue posted within the overall positive review above. I have figured out why the system rebooted a graphic error per the X configuration, and was able to duplicate the error. I downloaded Wine 0.9.45 (available on the Ubuntu repos) and installed a program I typically use. Avant Window Navigator (AWN) was operational at the time I loaded the program. As a result of the two mingling, I've found AWN nearly completely hangs upon loading the program in Wine. After a few minutes of lag time, AWN comes back to be "somewhat" responsive, though it acts as if it's quite laggy in the loading of programs. When I'd rebooted, the problem occured. I'd done this once again, and the problem occured once again. Some issue exists here that causes the system to panic on reboot (but the system loads with no error upon simply pressing 'reset' when said error occurs).

FYI: This problem did not exist on Sabayon, nor did I expect it to exist on Ubuntu. The only difference between the two that I have installed is on the Sabayon system I'd used the ./configure, make, make install method, while on Ubuntu I allowed Synaptic to install Wine.

I'll try to ./configure, make, make install the latest source package later, but for now I'm working off a tightrope.

EDIT: I can now verify Wine via ./configure, make, sudo make install did not solve the issue. Also, I emerged Wine on Sabayon and it worked very well. The program I'm using via Wine is not a graphical entity to stress the machine - in fact, it's far from it. Voodoo [ [http://www.voodoochat.com](http://www.voodoochat.com) ], a multi-user chat system with user photos, works flawlessly on Sabayon 3.3 and 3.4a while using a -x parameter built for Voodoo's usage ( wine voodoo.exe -x ) with little system strain at all. Unfortunately, on Ubuntu, the system strain is quite noticeable. I've no clue what is the cause of this.

EDIT [1 day later]: The Voodoo client is working successfully under Wine (as it does under Sabayon), but as stated before the AWN issue (where the system slows down dramatically) does not exist in Sabayon. Regardless, when Wine loads Voodoo entirely, the system goes back to normal after the AWN icon representing a Wine window appears. It's a bit of a pain to watch, but the program works without issue otherwise. I'm unsure if this happens with other Wine programs as I don't use Wine for anything else. As of now, I feel this needs to be reported simply for eyeful purposes if nothing else. However, I'm unsure as to who to report the problem to - Wine works, AWN works, Ubuntu works.. it works, just presents a problem within the OS temporarily, a problem with Wine temporarily, and a problem with AWN temporarily..

---

