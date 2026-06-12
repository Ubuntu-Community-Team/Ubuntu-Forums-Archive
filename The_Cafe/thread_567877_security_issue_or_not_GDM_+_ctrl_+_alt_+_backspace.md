---
title: "security issue or not GDM + ctrl + alt + backspace"
date: 2007-10-05
forum: The Cafe
---

### Post by nowshining on 2007-10-05
I have set that each time a password or username is incorrectly put that it will take 1 minute to re-allow logins, however this can be bypassed by pressing and reloading GDM by ctrl + alt + backspace which then allows one to try a re-login promptly.

I didn't know where to put this :)..by the way.

---

### Post by nowshining on 2007-10-05
oops now just thought I could of put it in the security forum.. :) my brain was fogged up at the time and that Thought didn't get thru until just now.. :P

---

### Post by n3tfury on 2007-10-05
why is that an issue.  you either know the password or you don't.

---

### Post by nowshining on 2007-10-05
i was talking about for tho multi users on one computer and passwords, makes it easier to quick guess as a local user than having to wait the time to re-try a login. Otherwise that should be removed if it can easily be bypassed.

---

### Post by Tomosaur on 2007-10-05
At the end of the day, local access to a machine means that machine is pretty much compromised already. You just can't defend from a physical attack - at the very least all they have to do is reboot the machine and enter recovery mode, or insert their own live CD, etc etc. If the person is physically typing away at your machine, then all passwords can hope to do is provide a little privacy (and even then it doesn't work very well anyway).

---

### Post by nowshining on 2007-10-05
disabling a restart of the server or gdm via that way while it is locked out would be a good solution in the end...I also meant just guessing passwords, and well Recovery mode is a HUGE issues if just entering that will enable the deleting of files, etc.. without a password.

Live CD which I think they would have hidden somewhere in the home or destroyed it just incase or put it somewhere other than at home would help. 

Passwords are great for protection and it's the best protection in the end considering no backdoors are secretly input into the OP.

---

### Post by Tomosaur on 2007-10-05
> **nowshining said:**
> disabling a restart of the server or gdm via that way while it is locked out would be a good solution in the end...I also meant just guessing passwords, and well Recovery mode is a HUGE issues if just entering that will enable the deleting of files, etc.. without a password.

Live CD which I think they would have hidden somewhere in the home or destroyed it just incase or put it somewhere other than at home would help. 

Passwords are great for protection and it's the best protection in the end considering no backdoors are secretly input into the OP.

But that's the point - no security system in the world can defend from a local physical attack, unless you mount auto-machine gun turrets around your computer or something. If somebody wants to mess up your machine, and has actual physical access to it, they will be able to do it. The simplest way is to just smash the machine to bits, for example. A more 'covert' way would be to reboot the machine and use the recovery option to gain automatic root access.

You can make it a little more difficult for the attacker - for example, you can remove the recovery mode option from the bootloader, then put a password on the bootloader to prevent someone re-adding it. This just means, however, that the person has to simply skip the bootloader. If they have a bootloader on a floppy disk, they can just use that - or they can just use a LiveCD, or indeed just use a normal install CD and wipe everything off your machine.

If you are REALLY paranoid, do the following:
1) Remove the recovery mode from the bootloader.
2) Put a password on the bootloader.
3) Enter your BIOS settings and put the hard drive to boot first.
4) Put a password on your BIOS so nobody can reset the boot order.

This will go a long way to delaying an attack on a physical machine, but a determined attacker will still get through by some other means, or may resort to just destroying your machine (hopefully you don't have anybody in your home / workplace so malicious!).

Somebody guessing your password is the least of your worries, and is actually incredibly unlikely. It is far quicker for an attacker to just use the recovery mode option. Just pick a good strong password and then never tell anybody it.

---

### Post by nowshining on 2007-10-05
then what's the point with timeout if it's not meant to keep and easily bypassed. I know what can happen and will however it's another Delay, so i'm guessing that all those encryption methods are just bogus eh! then?? right..

The question tho is give me some examples of bypassing the recovery mode because for maintance it asks for a password root that is, and it's disabled by default on Ubuntu, i'd like to know myself,

as for

2) Put a password on the bootloader. - haven't done that
3) Enter your BIOS settings and put the hard drive to boot first - haven't done that.
4) Put a password on your BIOS so nobody can reset the boot order.- done that however that CAN be bypassed by opening up the computer and removing the battery.


So in the end Windows makes a better protector when a machine is physically used for attack then Ubuntu right ?? i mean with Windows there is no ctrl + alt + backspace to reload after so many login attempts and the freeze and no live cd to easily mount a drive right.

So in the end

Linux Vs. Windows when attacked via internet

Linux = Very Strong
Windows - Weak

Linux vs. Windows when Physically attacked

Linux - Weak
Windows Strong.

---

### Post by Tomosaur on 2007-10-05
> **nowshining said:**
> then what's the point with timeout if it's not meant to keep and easily bypassed. I know what can happen and will however it's another Delay, so i'm guessing that all those encryption methods are just bogus eh! then?? right..

The question tho is give me some examples of bypassing the recovery mode because for maintance it asks for a password root that is, and it's disabled by default on Ubuntu, i'd like to know myself,

as for

2) Put a password on the bootloader. - haven't done that
3) Enter your BIOS settings and put the hard drive to boot first - haven't done that.
4) Put a password on your BIOS so nobody can reset the boot order.- done that however that CAN be bypassed by opening up the computer and removing the battery.


So in the end Windows makes a better protector when a machine is physically used for attack then Ubuntu right ?? i mean with Windows there is no ctrl + alt + backspace to reload after so many login attempts and the freeze and no live cd to easily mount a drive right.

So in the end

Linux Vs. Windows when attacked via internet

Linux = Very Strong
Windows - Weak

Linux vs. Windows when Physically attacked

Linux - Weak
Windows Strong.

Never heard of Safe Mode?

Select Windows when you're booting up, then keep hitting f8 - tell us how strong Windows is then, as Safe Mode is essentially free administrator access.

At the end of the day, locking the login screen is pointless. It is a mild inconvenience, but doesn't make your system any more secure. The attacker can just reboot, and then you're back to square one.

Logon passwords serve no purpose other than to give you some minimal privacy from other users on the same machine. This privacy is almost completely ineffective. They do **not** secure your machine from local attackers - and remote attackers do not need your user password, they only need to exploit a bug, or exploit the user's naivety.

You can argue this any way you want, but the fact remains. User passwords are primarily a psychological device to get **you** to be more vigilant. While it does have a small use regarding privacy (and by the way, Linux uses the password system much more effectively, as the concept of file ownership and permissions is much more prevalent on Linux than on Windows), the simple fact of the matter is that if someone is physically sitting at your machine and wants to be malicious, then your machine is effectively toast before they get to work.

The most effective way to safeguard your privacy is to pick a STRONG user password, then make sure the files in your home directory are set to be readable, writable, and executable only by you, THEN encrypt your hard drive, THEN do all of the steps I outlined earlier.

Then your local attacker may take another 10 minutes before they get into your machine.

---

### Post by nowshining on 2007-10-05
lolz never thought of safe mode, a reboot is actually a delay, however I still know that is a bit effective in stopping them or delaying them. A reboot vs. a restart of the GDM display - which is quicker.

But why does Encrypting protect if it can be hacked in the end. I am saying if that's true then WHAT IS THE POINT OF HAVING IT AS AN OPTION. Then is should be removed if it in ineffective.

---

### Post by kerry_s on 2007-10-05
try this->
[http://linux.about.com/od/ubuntu_doc/a/ubudg10t19.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t19.htm)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html)

google would have saved you a whole lot of waiting.

---

### Post by mridkash on 2007-10-05
> Put a password on your BIOS so nobody can reset the boot order.- done that however that CAN be bypassed by opening up the computer and removing the battery.

On my PC (Intel 915GAG board) the onboard cell died, so I removed it and put new one a day later and strangely, I found the BIOS password intact. 
For the whole day computer was switched off and battery removed.
 I wonder they now hard code the password somewhere.

---

### Post by Tomosaur on 2007-10-05
> **nowshining said:**
> lolz never thought of safe mode, a reboot is actually a delay, however I still know that is a bit effective in stopping them or delaying them. A reboot vs. a restart of the GDM display - which is quicker.

But why does Encrypting protect if it can be hacked in the end. I am saying if that's true then WHAT IS THE POINT OF HAVING IT AS AN OPTION. Then is should be removed if it in ineffective.

The point is for **convenience** and to stop scripts / viruses from brute-forcing your password. If you have a virus on your machine, for example, which continuously tries to guess your password, then having an erratic or unpredictable delay before the password is able to be input again means that many of those random passwords will be ignored by GDM and so the chances of the brute force attempt working are greatly reduced.

A **human** attacker will find another way around.

Once again - you cannot defend your computer from a **local, human attack**. All you can do is to inconvenience the attacker in as many ways as possible, but this means that you also inconvenience yourself, what with all the passwords and such you'll have to remember. It's just not worth worrying about. The only way you can be sure your machine is safe is to just not let anyone near it.

Much of the 'security' in systems is there to protect you from yourself, and remote attacks. With local malicious attacks, you just can't defend yourself. All you can do is take steps to improve your privacy, and Linux is much, much better at this than Windows, for reasons outlined earlier.

Encrypting your hard drive means people can't just use a LiveCD, for example, to look at the contents of your hard drive. It also means that you are inconvenienced yet again by having to remember yet another key to decrypt the hard drive when you need to.

Passwords will only deter people who don't know what they're doing - ie, your little brother or sister. Someone who actually wants to get at your information **will do so, if they have physical access to your computer and the right tools**.

---

### Post by FuturePilot on 2007-10-05
> **nowshining said:**
> 

Linux vs. Windows when Physically attacked

Linux - Weak
Windows Strong.
I'd have to disagree with that. There are ways to lock the computer down like others have said. Put a password on your BIOS and make sure that it's set to boot from the hard drive first so there's no way to boot a live CD. Put a password on Grub and remove the recovery options.
But like others have said, if a person has physical access to the computer, you're done anyways.

---

