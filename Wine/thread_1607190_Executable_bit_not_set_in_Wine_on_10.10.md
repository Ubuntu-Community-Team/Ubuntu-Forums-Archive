---
title: "Executable bit not set in Wine on 10.10"
date: 2010-10-27
forum: Wine
---

### Post by dmtparker on 2010-10-27
[LIST]
[*]I just upgraded to 10.10 and now none of my windows programs that used to work under Wine will work. I get the error message that they do not have the executable bit set, so I go into the program's Properties and click on "allow execute", the check mark appears and then immediately disappears!:confused:
[/LIST]
 This happens with ALL windows programs that I have (well, I really only have 3)
What can I do to get back my programs? (I do have a dual boot still set up, but it is such a pain, I'd rather just stay in Linux and use Wine.

---

### Post by BuddyThirteen on 2010-10-27
I'm having this same problem.

[edit]: I figured it out. For some reason you can't mark it as executable if it's on an external drive (mine was on an external hard drive). I copied the *.exe file onto the desktop and right-clicked and marking the box works fine there. Then I ran it and it worked dandy. Give that a try.

---

### Post by dmtparker on 2010-10-29
Mine are on the internal hard drive, so no luck. I do\ note that a Windows program I downloaded since installing 10.10 does work after resetting the execute bit. I suppose I may need to download the programs again, but that is certainly a pain.

---

### Post by guythatsits on 2010-10-29
> **BuddyThirteen said:**
> I'm having this same problem.

[edit]: I figured it out. For some reason you can't mark it as executable if it's on an external drive (mine was on an external hard drive). I copied the *.exe file onto the desktop and right-clicked and marking the box works fine there. Then I ran it and it worked dandy. Give that a try.

You are probably not the owner of the external drive... I would look at the permissions of how it is mounted.

Just a guess though, I don't know too much. Just trying to be helpful.

---

### Post by BuddyThirteen on 2010-10-29
> **guythatsits said:**
> You are probably not the owner of the external drive... I would look at the permissions of how it is mounted.

Just a guess though, I don't know too much. Just trying to be helpful.
I'm the only user. I don't know how to change ownership of the drive. Under the "Properties" of the drive, it just says "The permissions of [drivename] could not be determined." and nothing else.

---

### Post by dmtparker on 2010-10-29
It clearly has something to do with permissions and ownership. The program in question exists in a Windows (XP) partition. If I move the executable to my desktop, I can change the execute bit and in fact the program will run, but crashes because it cannot find any of the other files it needs. When I put the altered program back in its original position, the execute bit goes away and cannot be changed. I have tried changeing properties of both the parent directory and the "Programs" directory without success in affecting this program.

---

### Post by dmtparker on 2010-10-29
More info: I tried a totally fresh install. Downloaded the installer from the web, ran the install under Wine (source page notes that is DOES run under Wine), installed it in a Linux partition, and again could not reset the execute bit.
What's up with this? Is there a console command I can execute to do this?

---

### Post by dmtparker on 2010-10-29
This is getting really weird.
I tried su in terminal, entered my password and "authentication failed". 
This is a single installation on my laptop. There is only one password as far as I know. In previous versions of Linux (Fedora, Mandriva, openSuse) I had a "root" password and a "mark" password, but Ubuntu only set up Mark and in the past when asked for a password to authenticate root privilege jobs, that always worked. Even now, it works if I go through a GUI program (e.g. to install new software), but under terminal, it doesn't????:(

---

### Post by annoyingrob on 2010-10-29
By default, the root account on Ubuntu doesn't have a password (which prevents direct login to root), everything is done through sudo. run "sudo su" to get into it, or "sudo passwd root" if you want to set the root password.

It's also VERY possible that your XP partition is being mounted with the "noexec" option, which prevents anything on it from being executed.

---

### Post by BuddyThirteen on 2010-10-29
> **annoyingrob said:**
> It's also VERY possible that your XP partition is being mounted with the "noexec" option, which prevents anything on it from being executed.
This might be my problem, too. The external drive was formatted and created by Windows before I switched over to Ubuntu (all of two days ago). But there's too much on the drive to move anywhere else for a fresh reformat. Is there anything I can do to fix this?

---

### Post by dmtparker on 2010-11-04
> **annoyingrob said:**
> It's also VERY possible that your XP partition is being mounted with the "noexec" option, which prevents anything on it from being executed.
That appears to be the case and I suppose there is a command line way of changing that (hopefully someone out there will give me a script). I tried doing it from the GUI, before mounting, permissions cannot be determined. After mounting the execute permission is not checked, I can check it and it does not disappear they way the program (.exe) files check does, but if I click Apply to all files..., then it disappears and does not get applied to files. Also if I just close Properties with it checked, it is uncheck next time I open Properties and I still cannot execute any files on that drive.
This is REALLY aggravating as everything was working so well under 10.04!

---

### Post by annoyingrob on 2010-11-05
you can set up a permanent mount in /etc/fstab for the drive so that it always mounts without noexec

example:

/dev/sdx /mountpoint ntfs defaults 0 0

where /dev/sdx is the partition you want to mount (it could be sdb1 for example), and /mountpoint is where you want to put it. This could be /home/username/win or something. Then, the partition will be mounted with "default" options every time the system is turned on. By default, you can execute files.

---

### Post by dmtparker on 2010-11-05
> **annoyingrob said:**
> By default, the root account on Ubuntu doesn't have a password (which prevents direct login to root), everything is done through sudo. run "sudo su" to get into it, or "sudo passwd root" if you want to set the root password.
I suppose this is abit off topic, but I am trying to edit /etc/fstab as suggested to automatically mount my windows partition and I cannot edit it as it is owned by root and I cannot log in as root as it ??doesn't exist?? 
I even tried sudu gedit /etc/fstab and that didn't work.
How do I get to be root and edit fstab?

Here is the output:
root@mark-laptop:/home/mark# gedit

(gedit:8834): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted

---

### Post by annoyingrob on 2010-11-06
sudo SHOULD work to allow you to edit the file. eg, "sudo gedit /etc/fstab" just like you were doing. What sort of errors are coming up when you try to run "sudo gedit /etc/fstab"? can you simply type "sudo su", which will get you into a root prompt, and then run "gedit /etc/fstab" from there?

---

### Post by fslezak on 2010-11-06
> This is REALLY aggravating as everything was working so well under 10.04!

Yeah right...

I use 10.04, and I am trying to run a software that is on DVD. As you all know, computers have limited space. Isn't there a way to override the executable bit for one "session*"?

* By session a mean from when you log in to when you turn the computer off.

---

### Post by fslezak on 2010-11-06
> This is REALLY aggravating as everything was working so well under 10.04!

Yeah right...

I use 10.04, and I am trying to run a software that is on DVD. As you all know, computers have limited space. Isn't there a way to override the executable bit for one "session*"?

[SIZE="2"]* By session a mean from when you log in to when you turn the computer off.[/SIZE]

---

### Post by annoyingrob on 2010-11-06
> **fslezak said:**
> Yeah right...

I use 10.04, and I am trying to run a software that is on DVD. As you all know, computers have limited space. Isn't there a way to override the executable bit for one "session*"?

[SIZE="2"]* By session a mean from when you log in to when you turn the computer off.[/SIZE]

You can re-mount the drive with the options you want.

For example "sudo mount -o remount,defaults /dev/sdx" should remount the drive with "default" settings.

noexec=off might work well too.

---

### Post by Dannyk on 2010-11-07
an easy solution:
instal ntfs configuration tool and set both internal and external drives to write

---

### Post by peter@iologic.co.uk on 2010-11-11
> **dmtparker said:**
> 
[LIST]
[*]I just upgraded to 10.10 and now none of my windows programs that used to work under Wine will work. I get the error message that they do not have the executable bit set, so I go into the program's Properties and click on "allow execute", the check mark appears and then immediately disappears!:confused:
[/LIST]
 This happens with ALL windows programs that I have (well, I really only have 3)
What can I do to get back my programs? (I do have a dual boot still set up, but it is such a pain, I'd rather just stay in Linux and use Wine.

I'm having the same problem when I try to run the setup.exe installer to install some Windows software from CD-ROM. Since the CD-ROM has a read-only filesystem I can't alter the executable status of the file. Is there any way around this?

---

### Post by BuddyThirteen on 2010-11-11
> **peter@iologic.co.uk said:**
> I'm having the same problem when I try to run the setup.exe installer to install some Windows software from CD-ROM. Since the CD-ROM has a read-only filesystem I can't alter the executable status of the file. Is there any way around this?
^ This! I can't install anything.

I understand why they'd make this change (average users are of below average intelligence), but is there a way to permanently change this stupid executable bit default setting? I'm a smart user, I never install or run anything that I don't trust or know the origin of, and it seems like I'm being punished for the few people that just run everything that comes from an email attachment willy-nilly. This is annoying and stupid.

---

### Post by mojo636 on 2010-11-11
I have 2 internal drives. 120GB & 1TB. 120gb has just had Ubuntu 10.10 installed. 1TB has 2 partitions, 1 with windows 7 and the other is ntfs partition where I store all my data. I have tried installing NTFS Config tool and setting internal and external drives with write support etc this did not work. Same issue is occurring under permissions tab where cannot select option to allow files to execute. When selected it just stays for a second then goes back to not selected. Owner of the drive \ mount point in Ubuntu is root which is why it is all locked down I presume. Normally I install everything on 1 drive and partition it all. This time I have used separate drive for Ubuntu which I believe is why this is happening. Cant change ownership \ permissions in linux as it is an ntfs drive. Not sure where to go from here.

---

### Post by ricey155 on 2011-02-16
has anyone fount a way around this yet ??

im trying to install pokerstars and gives me the error but this is the only program it gives the error 

its and exe file 

ive come back to ubuntu today after issues with gutsy gibbon, unistalled win7 and 10.10 is on all good except for this :)

---

### Post by YokoZar on 2011-02-18
As indicated in the stickies, the easy way to workaround this executable bit nonsense is to enable the Wine PPA.

---

### Post by Binayak on 2011-02-19
Another way to get around it is to 
open terminal, navigate to the folder where the '.exe' file is and write
"wine <exe_file_name>" without quotes.

---

### Post by yanosk on 2011-02-24
don't know if this problem has been solved some other way but I had to do a clean install of of 10.04 then install my windows apps which were on an external drive, after that, however, I couldn't upgrade back to 10.10 because of some dependency issues which I'm still trying to track down ... I'm also getting an unrelated message at boot about an 'ASIC bug' which I'm told isn't serious and is quite widespread, has to do with radeon graphics ... 10.04 is working fine for me and wine does what it's supposed to do so I think I'll just sit tight till the next LTS version

---

