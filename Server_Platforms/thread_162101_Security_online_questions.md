---
title: "Security online questions"
date: 2006-04-18
forum: Server Platforms
---

### Post by imhdd on 2006-04-18
I'm about ready to make Ununtu 5.10 my primary system. One thing that's holding me back is questions about security. I understand the insecurity of Windows and I have many software devices that I use (which helps *some*).

I've been studying Linux and it's modular design and all the reasons that Linux is more secure than Win. But being new to Linux, I don't want to jump right in and mistakenly think my passwords and ID are safe. Here's what I've done trying to make my personal stuff stay personal on the Internet - this may all be in vain.

I'm a home user and security at home is not a problem. It's the Internet that worries me.

I use DSL with an electronic switch (like a hub but better) for home networking. GRC Port Authority reported my ports as Stealthed.

On my Primary User desktop I'm using Firestarter and Firefox. This is where I do all my browsing and admn.

I set up a second User desktop with permissions limited to modem and print,
using Mozilla with PSM. This account would be used only for banking and credit cards. Can it's security be compromised by someone breaking into my primary user account from the I'net? 

Will this help me secure my personal info? Should I set up another desktop for browsing and everyday use and leave the primary user for administration only? 

I appreciate any help from users who do online banking and have been down this road before.

---

### Post by jazzmuzik on 2006-04-18
Sounds like a good start, but once you are on the net, no matter what steps you take, you are vulnerable. For example, I doubt the powerful want a world full of people with unreachable computers. Unfortunately. That fact makes things more insecure by default! Do we have cars that cannot be broken into? Hardly. But they can be made more secure. Stolen cars are big business for criminals, police, lawyers and prisons. Every time you press that button to unlock your car doors, you send out a signal that can be picked up. My guess is it *is* picked up. Routinely. We've got a spacecraft on the edge of the solar system and we still receive it's paltry half a watt or so transmission. What are you transmitting via your computer? Sorry to wax philosophical but these are things to consider.

---

### Post by chettyk on 2006-04-18
I use my Ubuntu for online banking and Internet transactions. I am no expert, but I think you have taken sensible precautions. Like you, I too have created two user accounts, one of which I use solely for online banking and online financial transactions. In that account (the one I uses for online financial activities), I have set the Firefox preferences so that all cookies are deleted when I exit Firefox and I don't permit Firefox to store forms data or passwords.

Linux is inherently far more secure than Windows and in addition one can take commonsense precautions, which you have done. Don't worry excessively.

---

### Post by towsonu2003 on 2006-04-18
it seems you're good. But if you are really really really paranoid, you could look into running a lightweight liveCD distro (dsl, puppy, ...) using emulation (Qemu, Vmware, ...) only during your online banking actions. The advantage of an emulated livecd: close the emulator and everything gets erased, plus no need to log out-log in. Cons: overkill.

---

### Post by imhdd on 2006-04-18
Thanks for replies. I'm not familiar enough with Linux to try anything that isn't very simple. That's what scares me. Emulation sounds like something I want when I learn how to use it. But with Windows being under constant attack I have almost no confidence in it's security even with all my third party applications. I'm about ready to make the permanent switch to Ubuntu.

---

### Post by jinacio on 2006-04-18
As soon as you switch from windows to linux, it usually makes a HUGE difference in security.

Good networking and firewall helps too...

I say if you'r not paranoid about security then now it's just a matter of not having bad web browsing habbits (good passwords, decent sites...) and you'r all set.

and remember: the chain is as weak as it's weakest link - no point beeing paranoid about every security aspect and then (like i've seen) keep your passwords on a post-it ;)

---

### Post by towsonu2003 on 2006-04-18
[QUOTE=imhdd]Thanks for replies. I'm not familiar enough with Linux to try anything that isn't very simple. That's what scares me. [/QUOTE]
Emulation is very fun: you can break the emulated installation while experimenting and nothing happens to your computer. But point taken, it may look hard at first. 

oh, just remembered. Check out the forums about rootkit hunter (rkhunter) or chkrootkit (I'm just increasing your blood pressure, no worry :) ) I found this that might help: [http://tldp.org/HOWTO/Security-HOWTO/index.html](http://tldp.org/HOWTO/Security-HOWTO/index.html) be careful not to break your installation while experimenting with instructions. 

I also saw this [https://wiki.ubuntu.com/InstallingSecurityTools?highlight=%28rootkit%29](https://wiki.ubuntu.com/InstallingSecurityTools?highlight=%28rootkit%29) but that doesn't mean you need to install them. just check it out. 

also go to google.com/linux and search for "linux security" (no quotes) to see what there is out there worth reading -which is subjective- :)

and finally, regular precautions will help: don't install stuff you don't know, don't use your superuser (wiki.ubuntu.com/SudoRoot) password unless you know what you are doing etc. usually, from what I see from the forums, the worst vulnerability is the user him/herself in that, check your spelling carefully when you input commands using superuser (root) permissions.... a common mistake that trashes a user's data seems to be typing a command incorrectly, for linux newbies (anyone reading this, do NOT post example commands -just don't/thanks :) ).

---

### Post by imhdd on 2006-04-20
Thanks for all the information. I have to admit: I am a bit (a lot) paranoid. With so much ID thieft, bank accounts cleaned out, etc. I try to protect myself as much as is possible. It's a mean world.  I appreciate your help.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=imhdd]I am a bit (a lot) paranoid.[/QUOTE]
for trying virtualization (emulation), check out:
[http://www.ubuntuforums.org/showthread.php?t=39513&highlight=kqemu+compile+howto](http://www.ubuntuforums.org/showthread.php?t=39513&highlight=kqemu+compile+howto) (qemu)
[http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php) (vmware)

use these as your starting point of choosing qemu or vmware as your emulation software, choose a lightweight *liveCD* linux distro (I prefer DSL) to run under the emulation, and play around. 

qemu is open source, vmware player is not. both are free. I found qemu to be easier, but tastes are subjective. most ppl seem to prefer vmware. 

the pro is: imagine you browsed a malicious web site that installed malicious software to your livecd linux emulation (extremely low probability). close the emulation software, reopen it, and the mali. soft. is gone, along with any cookies, passwords that might have been stored, history etc. 

this will however not protect you against keyloggers installed to your host OS (ubuntu in this case). -etremely low probability-

---

### Post by jazzmuzik on 2006-04-21
[QUOTE=imhdd]Thanks for all the information. I have to admit: I am a bit (a lot) paranoid. With so much ID thieft, bank accounts cleaned out, etc. I try to protect myself as much as is possible. It's a mean world.  I appreciate your help.[/QUOTE]

The idea is probably analogous to door lock security. The police say you can't totally prevent a break-in, but they suggest you make your house harder to break into than the next one and then criminals will go to the easy house. A bit of paranoia can work in your favor, BTW.

---

