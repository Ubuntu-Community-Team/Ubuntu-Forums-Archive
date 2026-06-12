---
title: "Portable Ubuntu USB Virus scanner"
date: 2008-05-28
forum: Security
---

### Post by AndyCee on 2008-05-28
Heya,
I'm currently working at a Uni where some of the windows machines are infected with a nasty virus which spreads via the students USB disks. I'd like to mention that I don't have authority over these machines.

Anywayz, I now have a queue of students and lecturers who can't log into windows (and have non-updated crapware antivirus installed). I am considering the possibility of creating a bootable Ubuntu USB, installing a virus-scanner (AVG, antivir or something) and scan machines I can't boot into.

Has this been implemented before? Any problems or suggestions? Would Xubuntu/Ubuntu/Kubuntu be better?

---

### Post by akiratheoni on 2008-05-28
I haven't actually done it before but I have read guides on how Knoppix does the trick where you pop in the live cd and install f-prot and update the virus definitions then scan for viruses. Hope this helps.

[http://www.extremetech.com/article2/0,1697,1918391,00.asp](http://www.extremetech.com/article2/0,1697,1918391,00.asp)

I think that might help.

The only issue that I would need someone to confirm is that since the only guides I can find are from 2004 they all say that you can't scan NTFS filesystems. I think though that you can.

---

### Post by Biochem on 2008-05-28
I don't want to spoil your fun,

But at my university the bios are lock with password and set NOT to boot from USB or CD.

I would expect any serious university to have those basic security measures.

Other than that I did use clamav with a live cd to clean a computer so it is feasible.

good luck

---

### Post by AndyCee on 2008-05-29
> **Biochem said:**
> I don't want to spoil your fun,

But at my university the bios are lock with password and set NOT to boot from USB or CD.

I would expect any serious university to have those basic security measures.

Other than that I did use clamav with a live cd to clean a computer so it is feasible.

good luck
Cool, I wasn't sure if I could scan a machine like that.

Yeah, the bios's on the machines I manage is locked too. I work at the helpdesk for the IT department, so while I have administrator access to our 'student use' machines, the infected ones are in another department.

I mean to use the scanner on student/teacher laptops until the department with the infected machines gets their act together, or until the students boycott those machines. I'll post a progress report when I've had time to put something together.

---

### Post by MaindotC on 2008-05-29
Guys what lappers do you use?  We are issued Thinkpad T60's/T61's and there's a way to get the BIOS password.  It's electrical but easy to do - solder some resistors to a chip and then hook them to a 7-segment display.

I just googled "T60 recover bios password".  Also, typically the password is going to be the same for all machines, and it will typically be something easy to remember and transferrable to other employees in case someone who knows it is sick or on vacation.  If you want to brute-force it, it may be something like the name of your school, a helpdesk employee name, or "helpdesk" or even "password".

---

### Post by AndyCee on 2008-05-30
Nah, sorry - I didn't explain very well.

I supervise 'student use' computers which are managed by the ITS department of the Uni. While we manage many of the machines on all of our campuses, some departments manage their own machines. One of these departments have machines infected with a virus. These infected machines are locked down well enough to prevent the virus from causing THEM any direct damage, but USB disks carry the virus to student/staff personal machines.
The ITS machines are nearly bullet-proof when it comes to viruses (even with xp installed). Executables are locked, the hard-disks are write-protected and hidden, files are wiped when a user logs off etc.

As I work at a desk physically at the front of the ITS computer labs, staff and students assume it's our job to deal with every IT question/problem.

The portable virus-scanner I'm looking to make is for privately owned & bought laptops which get brought to me. It's not the only solution, but it may be a very convenient one. It has a lot of potential for my work. A large percentage of students & staff own their own laptop AND use the infected machines regularly, so I'm surprised it hasn't reached the local newspaper yet...

Anyway, assignments are done (or at least, no longer due) so this is my new project. Thanks for all posts so far. Any suggestions or thoughts still welcome.
-AndyCee

---

### Post by MaindotC on 2008-05-30
Backtrack has some sort of virus scanner on it. Someone at our helpdesk keeps a bootable image of Backtrack on his usb drive.

---

### Post by AndyCee on 2008-06-02
Right. I have things working now.

_What I want:_
[LIST]
[*] A persistent, bootable linux distribution installed on a USB - preferably an *buntu.
[*] A free antivirus package to run and scan the HD of the machine that the USB is plugged into.
[/LIST]

_What have done:_
[LIST]
[*] I decided to go with Xubuntu (somewhat lightweight,customizable [Gee I'm making up words today] and familiar).
[*] After several attempts using several different methods (direct install, pendrivelinux.com, ubuntugeek.com) and damaging my laptop's pre-existing GRUB bootloader I managed to get a persistent install using the guide at [http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/](http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/) and by installing lilo on the USB disk (not in the guide).
[*] Downloaded Avast! .deb file and installed on the disk.
[/LIST]

_What I now have:_
[LIST]
[*] A portable, persistant version of the Xubuntu livecd on my 2 Gig USB disk.
[*] A small problem that the hard drive of the machine booting from the disk doesn't auotomount, so I will have to make a script for the staff to double-click or something.
[*] The Avast! antivirus installed.
[/LIST]

_What I have yet to do:_
[LIST]
[*]Test the virus-scanner on an ntfs hard drive - not at work(I'm not going to run a program I've never used before with root privileges on a machine I'm not supposed to have admin rights on...)
[*]Investigate the automount issue and possibly fix it myself with a script.
[/LIST]

Thoughts & criticisms always welcome...Maybe it's just attention I crave ;)
-AndyCee

---

