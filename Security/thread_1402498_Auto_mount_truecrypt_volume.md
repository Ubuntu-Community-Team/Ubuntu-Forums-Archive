---
title: "Auto mount truecrypt volume??"
date: 2010-02-09
forum: Security
---

### Post by NertSkull on 2010-02-09
So I don't think this would be a bad idea, but it might.

I have a 2nd hard drive that I have encrypted using true crypt.  Is it possible to set this up with key files (or some other way) to auto mount when linux boots.

I need it in true crypt because there are some work programs I dual boot to use in windows, and need to have access to the drive in XP from time to time, and true crypt can mount there as well.  

But 90+% of my time is in linux and I would like to have it auto mount through fstab (or whatever way it needs to be).

My entire linux setup has been set up with encryption through dm crypt and LUKS (except for /boot).  So I would think having a key file stored on the computer and an auto mount fstab would be just as secure as however secure my LUKS setup is.  

So any way to auto mount a true crypt 2nd drive volume?

Thanks everyone!!

---

### Post by pascal91 on 2010-02-09
You should write a script that runs a truecrypt command and look to [udev rules]("http://reactivated.net/writing_udev_rules.html") to run this script automatically when your usb drive is plugged.
Truecrypt command line arguments are available in truecrypt user guide.

---

### Post by NertSkull on 2010-02-09
excellent idea, i will look into that and post if I have more questions (i'm sure I will, I'm pretty new to all this)

---

### Post by NertSkull on 2010-02-10
So I have looked at 20+ threads and tried a ton of combinations and I cannot get this to mount by itself.  I have a script that works on its own.  If I execute it by itself on the command line I can get it to mount the drive.

But I can't figure out how to get the script to automatically run on startup.

First, this is the guts of the script that I run

truecrypt --password='xxxxmypassxxxx' /dev/sda4 /media/Data

pretty simple, but it mounts the drive.

TWO problems I run into.

(1) First, in order for the script to run, it needs root access to mount the drive.  How do I get around this.  I figured out how to put my password into the script and make it work

echo 'my_root_pass' | sudo -S truecrypt --password='xxxxxmypasssxxxx' /dev/sda4/media/Data

but i'm not sure thats the best to store my password like that.  I'm not too concerned since i'm the only one with access to this machine, and me entire file-system is encrypted, but still seems like there should be a better way.

(2) I can't get it to run.  From what I've read the way to do this is using rc.d stuff.  So I copied my script into /etc, made it executable.

Then I ran

sudo update-rc.d myscript start 51 S .
But when I restarted, nothing.  No script.

Then I tried just adding the truecrypt command to mount my drive directly to the rc.local file.  Again, nothing happened.

Another option I toyed with is putting the script into the program launcher found in the preferences menu ("startup applications") but again I feel that there should be a better way.  Maybe not.

I've searched and read a ton, but can't find anything that is helping me understand this rc.d stuff?  Any thoughts/help.

Thanks all!!!!!!!

---

### Post by tcamdg on 2011-12-27
Sorry I don't have any solutions here, but I would also like to know how to accomplish this.

---

