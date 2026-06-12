---
title: "Is this normal?  Root with no pass on recovery console."
date: 2010-09-20
forum: Security
---

### Post by Fibercoax on 2010-09-20
Hello , 

Was wondering if this is normal . I installed ubuntu-10.04-desktop-amd64.iso and when i boot into recovery console and select drop into root shell it dont ask for anny password.
I know i can change this pass but new users (maybey) dont know this , It feel weird to me.
What they point if this..  small security issue?

thx

** deffault install

---

### Post by movieman on 2010-09-20
> **Fibercoax said:**
> What they point if this..  small security issue?

If someone is sitting at the console of your PC, they can boot from a LiveCD or USB stick and then own your system.

If you want security against local attacks by someone with access to the hardware, you need to encrypt your files. Then they could install a rootkit to grab the password next time you boot, but they can't read the files unless they do something like that.

---

### Post by movieman on 2010-09-20
BTW, I'm sure there is a setting to require the root password at the recovery console, but since Ubuntu blocks root logins I'm guessing it won't work even if you enable it?

---

### Post by Fibercoax on 2010-09-20
This not gonna happen because boot of external devices is locked in my bios like usb/cd/dvd !

---

### Post by Fibercoax on 2010-09-20
> **movieman said:**
> If someone is sitting at the console of your PC, they can boot from a LiveCD or USB stick and then own your system.

If you want security against local attacks by someone with access to the hardware, you need to encrypt your files. Then they could install a rootkit to grab the password next time you boot, but they can't read the files unless they do something like that.


I dont think that is possbile because boot from external devices is disabled in bios like usb/dvd/cd

---

### Post by aysiu on 2010-09-20
It's normal.

Physical access is root access.

If you think it's not possible for someone to get root access since you disabled booting other devices in the BIOS, you'd better hope no one has a screwdriver and doesn't just remove your CMOS battery... or the internal hard drive altogether.

---

### Post by Fibercoax on 2010-09-20
> **movieman said:**
> BTW, I'm sure there is a setting to require the root password at the recovery console, but since Ubuntu blocks root logins I'm guessing it won't work even if you enable it?

I didnt see it , you should install it and test your self you would be surprised.

What they need to do when installing ubuntu , FORCE TO SET ROOT PASS in the setup procedure. (look at the fedora 13 installer )
I dont see ubuntu block root logins.

---

### Post by aysiu on 2010-09-20
> **Fibercoax said:**
> I didnt see it , you should install it and test your self you would be surprised.

What they need to do when installing ubuntu , FORCE TO SET ROOT PASS in the setup procedure. (look at the fedora 13 installer )
I dont see ubuntu block root logins.
Ubuntu disables root password logins. You can get to a root shell by booting into recovery mode. You can also simulate a root shell by typing ```
sudo -i
``` into a terminal. Unless you explicitly set a root password, though, you cannot log into the root account in the traditional sense. More importantly, there is no need to.

---

### Post by Fibercoax on 2010-09-20
Oke understand ,, but in other words when i leave my ubunutu desktop open on my office desk and somone boot recovery console (when i get my coffee break ) he got root in 4 seconds . The idea dont make me happy !!

---

### Post by BkkBonanza on 2010-09-20
You can remove the recovery console boot option if you don't feel it's needed. An advanced user can still boot in the right mode but at least it isn't on the menu. The only real way to secure a machine from physical access is with encryption. Ubuntu does make it easy to set that up.

---

### Post by bodhi.zazen on 2010-09-20
> **Fibercoax said:**
> Hello , 

Was wondering if this is normal . I installed ubuntu-10.04-desktop-amd64.iso and when i boot into recovery console and select drop into root shell it dont ask for anny password.
I know i can change this pass but new users (maybey) dont know this , It feel weird to me.
What they point if this..  small security issue?

thx

** deffault install

Yes

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue%20Mode](https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue%20Mode)

---

### Post by Fibercoax on 2010-09-20
> **BkkBonanza said:**
> You can remove the recovery console boot option if you don't feel it's needed. An advanced user can still boot in the right mode but at least it isn't on the menu. The only real way to secure a machine from physical access is with encryption. Ubuntu does make it easy to set that up.

Yeah i could uninstall os and change to something else or remove hd :D but its not the point of solving it but i ask my self why its on deffault like this.   from this moment i start thinking if i wil use ubuntu or not.

---

### Post by Fibercoax on 2010-09-20
> **bodhi.zazen said:**
> Yes

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue%20Mode]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue%20Mode")


So weird .. some ppl i talk to say its crazy.. sorry if im wrong .

annyway thanks for anwsers

My point is root pass always on from install, most ppl dont know this

---

### Post by bodhi.zazen on 2010-09-20
> **Fibercoax said:**
> So weird .. some ppl i talk to say its crazy.. sorry if im wrong .

annyway thanks for anwsers

My point is root pass always on from install, most ppl dont know this

If you have physical access to the machine you have root access, regardless of OS.

The only potential option for protection would be encryption , and even encryption has limits.

---

### Post by drs305 on 2010-09-20
In Grub2 you can add a user/password to any grub menu item. While I consider Grub passwords more a "childproof" password (since anyone knowledgeable could edit the grub files by various methods), you could add a password to the recovery mode menuentry (or all linux entries, Windows recovery partition, etc) to prevent others from selecting it. You could also not list the recovery mode option if you know how to edit the menuentry during boot to get into the recovery mode.

While preparing this response, I noticed that the way Grub2 creates the menu.cfg has changed a bit. I have a thread on creating passwords but I'll have to update the exact lines to modify in /etc/grub.d/10_linux. I'll have it done by the end of the day and when I get time I'll add an item specifically for the Recovery Mode option.

The thread is located here:
[Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019")


**EDIT:** Updated for GNU GRUB 1.98-1ubuntu5 and Recovery Mode password protection added.

---

### Post by Fibercoax on 2010-09-21
> **BkkBonanza said:**
> You can remove the recovery console boot option if you don't feel it's needed. An advanced user can still boot in the right mode but at least it isn't on the menu. The only real way to secure a machine from physical access is with encryption. Ubuntu does make it easy to set that up.

i wish this tasks where not nessacery after insatll , they say its linux for human beings but its not realy... human beings boot messenger+email .. and rest dont care 
My idea is to setup root pass and user pass from begin install to keep the basics :))

Respect for ubuntu but fedora 13 is olso realy nice , nice kernel too and feel more save..


*its all between the ears* :)[COLOR=#000000][FONT=sans-serif][/FONT][/COLOR]

---

### Post by LinuxPhreak on 2010-09-21
I setup laptop in such  manner to be more secure then my desktop. First what I do is I change the BIOS settings so it request for password before it will access any drive. This is then followed by the GRUB2 which ask for another password. Once again this is then followed by another password once your at the login screen of Ubuntu. 

You could also just remove GRUB2 from the Hard Drive and have password protected GRUB2 backup disk. This will mean that the person will need the backup disk of GRUB2 and the password to the backup disk to boot the computer.

Of course the user could always use the beast known as Super Grub Disk which pretty much null and voids your backup disk. Because of this I would recommend just keeping GRUB2 on your computers main hard drive.

---

### Post by BkkBonanza on 2010-09-21
These all mean little when someone can just take the laptop and/or hard drive. The only reasonable protection is an encrypted home or full drive encryption. 

Encrypted home has been an install option on Ubuntu for a year now and I don't see why anyone wanting to secure their data wouldn't just choose that. It has very little overhead, only uses the normal login password and when someone gets your laptop or drive they cannot get into the files. 

These other things are just road bumps for any advanced user wanting access to your data.

---

### Post by psusi on 2010-09-21
Removing the boot option won't stop someone from doing the same thing given physical access to the machine, but having it there makes administration easier.  If you don't keep your servers physically secure, then they aren't secure, period.

---

### Post by cariboo on 2010-09-22
The new Maverick desktop installer now allows you to create an encrypted home directory, instead of having to use the alternate install CD. You can do this at the same time you create your user name and password.

---

### Post by aysiu on 2010-09-22
> **cariboo907 said:**
> The new Maverick desktop installer now allows you to create an encrypted home directory, instead of having to use the alternate install CD. You can do this at the same time you create your user name and password.
This was in Lucid, too, actually.

---

### Post by bodhi.zazen on 2010-09-22
> **aysiu said:**
> This was in Lucid, too, actually.

Karmic actually, but in karmic you needed to pass a boot option.

The alternate CD is to encrypt the whole tamale.

---

