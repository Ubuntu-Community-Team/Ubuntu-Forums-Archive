---
title: "[HowTo]: Fix suspend and hibernate on laptops"
date: 2007-06-12
forum: Tutorials
---

### Post by Bluecircle on 2007-06-12
If the normal suspend and hibernate buttons don't work, you can try this little hack.

First get uswsusp:

```

sudo apt-get install uswsusp

```

Now, test out suspend to see if it works:

```

sudo s2ram

```

If this does not work, you can use

```

sudo s2ram --force

```

Next, try out hibernate:

```

sudo s2disk

```

Now, if one or both of these commands work and you would like to use them, we need to change the command on the shutdown menu to this.

**Note: This part is for [COLOR="Red"]FEISTY AND GUTSY ONLY!!![/COLOR] The scripts in Edgy are stored in "/usr/share/hal/scripts" and have different names AFAIK. If someone running Edgy could tell me what the files names are I will add it here.**

First, backup your original files:

```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak

```

Now, edit these two files and replace all the code with this:

**hal-system-power-suspend-linux**

```

sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

```

```

#!/bin/sh

/sbin/s2ram --force

```

**hal-system-power-hibernate-linux**

```

sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

```

```

#!/bin/sh

/sbin/s2disk

```

if this breaks stuff, just restore the backup files you made.

Good luck! ;)

---

### Post by ukripper on 2007-06-13
I know few people having this problem in feisty I will ask them to try this.

On my laptops there are no problems either on Edgy or Feisty.

Good work though.

---

### Post by Unnicknamed on 2007-06-15
Excellent!

This works on my HP Pavilion DV5215us, with xgl and beryl enabled on Feisty :)

But, after I hibernate or suspend, my Hibernate and Suspend buttons from the Log off menu are gone!

UPDATE: Sound didn't work, I have to reboot to get it back.

---

### Post by slartoff on 2007-06-19
Thanks, Bluecircle.  The kernalspace (?) suspend/resume stuff (what comes by default) never worked properly on my Toshiba A105.  I spent some time long ago trying to figure it out, and eventually because satisfied with only hibernate.

A couple weeks ago, after some update undoubtedly, fan control started to be flaky on resume---the laptop would sometimes get VERY hot!  But following your guide, now suspend and hibernate both seem to work fine.

The only strange thing I get is that upon resume, Gnome Power Manager reports that there was a problem suspending.  So I have to click a checkbox to make that disappear.

---

### Post by vanadium on 2007-06-19
See also this thread

[http://ubuntuforums.org/showthread.php?t=417964&page=2](http://ubuntuforums.org/showthread.php?t=417964&page=2)

Probably, the permanent installation of the alternative hibernate routine is safer the way described in the link. I have applied it with success (Dell Latitude D810) under Feisty

---

### Post by grahams on 2007-06-20
Many thanks Bluecircle, I will give a try and report back.

---

### Post by kushelmex on 2007-06-20
tnx!! works fine here

---

### Post by Teamgeist on 2007-06-21
Seems to work fine here too. I have an Asus M2400N Centrino Laptop. It's like 4 years old now.
I will have to play around with it a little more, but the test run I just did went fine.
Thank you very much!

---

### Post by grahams on 2007-06-21
Thanks for the post. 

I tried s2disk and found it resumes much faster (50 secs v 84 secs), than the default hibernate on my Compaq n610c. So far s2ram does work on this system as i can not resume. I think the ATI graphics controller is not recovering correctly and I will try this again when the later uswsusp0.6 gets release as this adds more options such as -v (save the PCI config space for the VGA card).

If anyone has a Compaq n610c and has s2ram working, please let me know what settings you are using and also report the s2ram -i output to the developers, thanks.

I will try s2disk and s2ram on my work HP nw8440 laptop soon.

---

### Post by teasum on 2007-06-22
No luck on my Dell inspiron 8600--suspend and hibernate both worked for me in Dapper, but not in Feisty.  I've tried several solutions listed here in the forums, but no dice.  Everything seems to go down nicely, even with the commands listed in this thread, but when I power up, I get nothing after grub.  Does anybody know why the solution listed in this thread works?  I'd really like to track down this problem and get it working.  Otherwise, I'll have to try and install Dapper again or Edgy.  Thanks.  Here's my sudo s2ram -i output, if it means anything...

> This machine can be identified by:
    sys_vendor   = "Dell Computer Corporation"
    sys_product  = "Inspiron 8600                   "
    sys_version  = ""
    bios_version = "A14"

---

### Post by grahams on 2007-06-22
s2disk works well on my work nw8440 and the system no longer hangs after resume. 

So far s2ram does not work, but I haven't tried all the settings yet (-a 1, -p etc.)

---

### Post by teasum on 2007-06-24
> **Bluecircle said:**
> 
First, backup your original files:

```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak

```

I think there's an important error in the second 'cp' command.  It should be 

```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-**hibernate**-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak
```

I noticed this because I wanted to restore my files, but both backup files have the suspend script in them.  So, now I can't restore the original hibernate script.  All in all, it's cool, because I finally got s2disk to work (blacklisting the 'intel_agp' module did it, I believe), so I guess I wont be needing the original hibernate script after all.  Still, perhaps the original post could be changed.

Thanks!

---

### Post by Bluecircle on 2007-06-24
Oops, I'll fix that.

---

### Post by thrillhouse on 2007-06-25
Ok so my Thinkpad T41 under feisty goes to sleep and hibernates using s2ram and s2disk but waking it up is another story.  With s2ram, I get a bunch of I/O disk errors (I think its talking about not being able to mount the disk again) and with s2disk, it just boots normally and doesn't restore my session.  Any ideas?

---

### Post by Bluecircle on 2007-06-25
> **thrillhouse said:**
> Ok so my Thinkpad T41 under feisty goes to sleep and hibernates using s2ram and s2disk but waking it up is another story.  With s2ram, I get a bunch of I/O disk errors (I think its talking about not being able to mount the disk again) and with s2disk, it just boots normally and doesn't restore my session.  Any ideas?

There's a file somewhere with a bunch of system options configuring this stuff, but I can't find it right now. I'll try to find it.

---

### Post by wastedfluid on 2007-06-25
Confirming this DOES work on Fiesty 7.04 and an Acer 5100.

---

### Post by angel12 on 2007-06-28
i tried this on my hp dv2315nr, and it seems to work great, until i wake up the computer, and it goes to a completely black screen with a mouse cursor. i have tried typing my name/ password to get it back to a workable condition, but nothing works.

---

### Post by angel12 on 2007-06-28
i switched to a VT and i get the same errors i would get if i tried the kernel method: rejecting I/O to dead device. Im running this on an nforce 430 sata notebook, could that be part of the problem?

---

### Post by HeavyAl on 2007-06-29
Neato - I've had problems with suspend/resume on every Ubuntu install I've tried on my Thinkpad T40. This seems to make it work but it throws this error on resume:

kernel: [ 4282.952000] journal commit I/O error

Note that even though the error appears it doesn't seem to affect the functionality of the system in any way .. just keeps piping along happy as can be. Also, this is with the 2.6.20-16-lowlatency kernel thats part of Ubuntu Studio. 

Thanks for the tip!

---

### Post by HeavyAl on 2007-06-29
> **HeavyAl said:**
> 
Note that even though the error appears it doesn't seem to affect the functionality of the system in any way .. 

D'oh!!! I take that part back - all my icon's suddenly started freaking out and I had to do a hard reboot. Ok .. hrmm .. there must be some options that need tweaking ...

---

### Post by crazedgremlin on 2007-07-07
thanks - very nice - I've been having problems with suspending on a dell inspiron e1505n (yes, the one that _came_ with ubuntu).

It works fine, except that when I resume from suspend I see my session there for 2 or 3 seconds and then it goes back to suspend.  the second time I try to wake it up it will work.

it goes:
   -Ok, I'm using the computer
   -I hit stand-by key
   -the computer goes to sleep
   -I hit the power button to wake it up
   -the screen turns on - I can see the previous session
   -BLOOP! it's gone- the computer went to sleep again
   -I hit the power button to wake up
   -it works!

not really important, but can anyone shed any light on this?

---

### Post by crazedgremlin on 2007-07-08
ok when I hit fn+standby, I encounter the previously mentioned problem.
when I do K menu -> logout -> suspend, it works the way it should.

I guess I'll just use the K menu from now on.

---

### Post by crazedgremlin on 2007-07-09
Will I have to redo this when it's time to upgrade to Gutsy Gibbon?
Triple post ftw!

---

### Post by crazedgremlin on 2007-07-10
ok I fixed my problem! yay!
I did
```
sudo -i
cp /etc/acpi/sleep.sh /etc/acpi/sleep.sh.bak
```
apparently it ran through two different sleep scripts when I hit the suspend key

---

### Post by Bluecircle on 2007-07-10
If you have errors there are a bunch of settings to mess around with:

man s2ram:
```

OPTIONS
       -h, --help
              Short help text.

       -n, --test
              test if the machine is in the database. returns 0 if  known  and
              supported

       -i, --identify
              prints a string that identifies the machine.

       -f, --force
              force  suspending,  even on unknown machines.  the following op&#8208;
              tions are only available with --force.

       -s, --vbe_save
              save VBE state before suspending and restore after resume.

       -p, --vbe_post
              VBE POST the graphics card after resume

       -r, --radeontool
              turn off the backlight on radeons before suspending.

       -a, --acpi_sleep
              set  the  acpi_sleep  parameter  before   suspend.    1=s3_bios,
              2=s3_mode, 3=both

       -v, --pci_save
              Save the PCI config space of the VGA card before suspend and re&#8208;
              store it after resume.


```

Also, it is recommended to use s2both instead of s2ram in case the system loses power.

```

       s2both will do precisly the same as s2disk except that it will not pow&#8208;
       er off the system, but will suspend it to ram (put  the  system  in  S3
       mode). This has the advantage that resume will be faster, with the dis&#8208;
       advantage that you still use batteries. If they batteries  do  deplete,
       you  still  have  the system state saved to disk and can resume without
       data loss.

       You will need to set up an initramfs which calls the resume program for
       this  to  work. If you use an debian kernel package which was made with
       the --initrd option and you use mkinitramfs-tools, this package  should
       include the necessary parts on your initramfs.


```

---

### Post by Paul S on 2007-07-13
> **crazedgremlin said:**
> ok I fixed my problem! yay!
I did
```
sudo -i
cp /etc/acpi/sleep.sh /etc/acpi/sleep.sh.bak
```
apparently it ran through two different sleep scripts when I hit the suspend key

That doesn't make sense.  Did you move (mv) it instead of copy (cp)?  Or did you enter some code in the original file after copying it, or make it non-executable?  Otherwise, the old script ought to still run.

I have the same laptop and same problem with the "start" button bringing it back but only to go back to suspend again.  But, the laptop lid switch works better .. just close and reopen the lid and it will resume from suspend.

regards,

---

### Post by crazedgremlin on 2007-07-13
haha you're right,
I did mv instead of cp

I really need to proofread before I post

---

### Post by Paul S on 2007-07-13
OK, so now I have a working suspend / resume and hibernate / resume.  Suspend / resume worked before, but hibernate never did.  I have a dell e1505 with nvidia card.

But, still there is a problem when I use compiz/compiz-fusion/beryl.  After one or two successful suspend / resume cycles, the computer locks up and I have to power off and reboot.  This happened before and even now with uswsusp.  I know about unchecking "sync to  vblank" with compiz, but still have the problem.  I also know that if I disable compiz before suspend / hibernate, resume will work.  Of course, turning off compiz causes all open windows to bunch together, so it makes a lot of work after resuming.  Anyone have a solution to this?

regards,

---

### Post by fflarex on 2007-07-13
My computer will lock up like that too, whenever the display goes to sleep for too long without expliciting suspending or hibernating the system. If I have Compiz or Beryl installed (or maybe even if I'm just running Xgl, who knows?), then my computer will freeze up *much* more often it seems. And when my computer does this, I've learned to make sure there is no external hard drive mounted or else.

What is the "sync to vblank" option?

Anyways, I actually came to this thread because it solved my suspend/hibernate problems, but I just now noticed that my computer still locks up when the display goes to sleep and I don't know how to get it to resume.

---

### Post by Paul S on 2007-07-13
> **fflarex said:**
> 

What is the "sync to vblank" option?



I think it's discussed on the beryl troubleshooting page:

[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

It applies only to nvidia video cards.

regards,

---

### Post by drplix on 2007-07-14
This works great.  But after installing uswsusp the power button reverts to an immediate shutdown.

If you want to get the nice menu of options do the following:

First backup the power button acpi script
```

sudo cp /etc/acpi/powerbtn.sh /etc/acpi/powerbtn.sh.bak

```

Then edit powerbtn.sh to the following:

```

#!/bin/bash
/usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0

```

*Note this works for KDE.  I don't know about Gnome.

---

### Post by Paul S on 2007-07-14
> **drplix said:**
> This works great.  But after installing uswsusp the power button reverts to an immediate shutdown.

On KDE, the power button menu did not disappear.  All the options are still there.

But, on my laptop, the hibernate key combo (Fn-F1) does not activate hibernate.  Hibernate works great from the menu.  Also, the standby key combo (Fn-Esc) works fine .. so, why not hibernate?  Do you have any magic to make the hibernate button work?

TIA,

---

### Post by crazedgremlin on 2007-07-14
Thanks, drplix, that worked perfectly for me.:)

Paul S, I have the same problem as you, but hibernate isn't necessary for me.  It would be nice to make all the buttons perform their supposed functions, though.

---

### Post by crazedgremlin on 2007-07-14
OK, I go to /etc/acpi/hibernatebtn.sh
It ends up executing
```
#acpi_fakekey 205
```
If I run acpi_fakekey 205 it doesn't hibernate.

Any more clues?

---

### Post by Paul S on 2007-07-14
Yes, I tried all the combinations of Fn with another key, but nothing happens.  I also tried xev and found out that Fn-Esc is keycode 223, and that's not what's listed for suspend in /usr/share/acpi-support/key_constants (205).  I'm not sure how this works as it does.

regards,

---

### Post by dadde on 2007-07-15
I don't know why it works when I type on terminal
sudo s2ram --force         or
sudo s2disk

but then, when I modify the files 
hal-system-power-suspend-linux   and
hal-system-power-hibernate-linux

I've got the problem of the white screen after either suspending or hibernate

Any suggestion?

---

### Post by Paul S on 2007-07-15
> **dadde said:**
> I don't know why it works when I type on terminal
sudo s2ram --force         or
sudo s2disk

but then, when I modify the files 
hal-system-power-suspend-linux   and
hal-system-power-hibernate-linux

I've got the problem of the white screen after either suspending or hibernate

Any suggestion?

It sounds like you didn't correctly move the original files and create the new ones .. which means the original scripts are still running when you use the menus to hibernate / suspend. Open a terminal and check with these commands (see how you compare to mine):

paul :~$ ls -la /usr/lib/hal/scripts/linux/
total 64
drwxr-xr-x 2 root root 4096 2007-07-13 09:16 .
drwxr-xr-x 3 root root 4096 2007-05-18 21:53 ..
-rwxr-xr-x 1 root root 1283 2007-05-11 03:29 hal-luks-remove-linux
-rwxr-xr-x 1 root root 1093 2007-05-11 03:29 hal-luks-setup-linux
-rwxr-xr-x 1 root root  813 2007-05-11 03:29 hal-luks-teardown-linux
-rwxr-xr-x 1 root root 1965 2007-05-11 03:29 hal-system-killswitch-get-power-linux
-rwxr-xr-x 1 root root 2121 2007-05-11 03:29 hal-system-killswitch-set-power-linux
-rwxr-xr-x 1 root root 2393 2007-05-11 03:29 hal-system-lcd-get-brightness-linux
-rwxr-xr-x 1 root root 2447 2007-05-11 03:29 hal-system-lcd-set-brightness-linux
-rwxr-xr-x 1 root root   78 2007-07-13 20:57 hal-system-power-hibernate-linux
-rw-r--r-- 1 root root 3124 2007-07-13 09:16 hal-system-power-hibernate-linux.bak
-rwxr-xr-x 1 root root  333 2007-05-11 03:29 hal-system-power-reboot-linux
-rwxr-xr-x 1 root root  897 2007-05-11 03:29 hal-system-power-set-power-save-linux
-rwxr-xr-x 1 root root  335 2007-05-11 03:29 hal-system-power-shutdown-linux
-rwxr-xr-x 1 root root  112 2007-07-13 20:57 hal-system-power-suspend-linux
-rw-r--r-- 1 root root 4092 2007-07-13 09:15 hal-system-power-suspend-linux.bak

paul :~$ cat /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
#!/bin/sh

/sbin/s2ram

paul :~$ cat /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
#!/bin/sh

/sbin/s2disk

HTH

---

### Post by Paul S on 2007-07-22
I don't know what's happened here.  Initially this s2ram and s2disk seemed to work, but after using it for a week, now I'm getting the same problem I had with the other system, namely, that it won't resume.  I have to hit the power off and restart.  I've checked all the files, and they are the same, so nothing seems to have changed on my system.  Disppointing ..

regards,

---

### Post by ugm6hr on 2007-07-23
The suspend function works with Acer Aspire 5051AWXMi (5050 derivative) as described in post 1.

Easy :) Thanks.

---

### Post by tarek on 2007-07-23
Thanks. The suspend works but when it wakes up the sound doesn't work so I ran:
```
sudo /etc/init.d/alsa-utils restart
```
and fixed it.

There's one problem, tty1,2.. are not working. The font is so big I can't see anything. Any ideas?

Thanks again,
TK

---

### Post by Paul S on 2007-07-26
> **Paul S said:**
> I don't know what's happened here.  Initially this s2ram and s2disk seemed to work, but after using it for a week, now I'm getting the same problem I had with the other system, namely, that it won't resume.  I have to hit the power off and restart.  I've checked all the files, and they are the same, so nothing seems to have changed on my system.  Disppointing ..

regards,

OK, I found this command in another thread:

sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

After doing this, I have had no more problems with s2ram or s2disk.  So, for some reason, I suspect that the old scripts that use pmi are still getting executed somehow on my system.  That's strange.  Anyway, with pmi out of the way, s2ram and s2disk seem great.

---

### Post by CalvinK on 2007-07-26
It doesn't work on my Toshiba A200. s2disk crashes. No luck.

---

### Post by st33med on 2007-07-26
Hi, I'm having problems with when I resume from a hibernation. I have not yet made the files permanent. The screen is all stretched out, I can't see everything. The only way to go to the thing I want to get is move the mouse to the edge of the screen and the screen moves. I think this might be because my graphics card (Intel 950GM) relies on the memory since it is integrated and it gets mixed up somehow. I'll see if I can update my 915resolution package, but that might not help. I even disabled Compiz, still did it.

Any solution?

---

### Post by JProgrammer on 2007-07-26
I have actually found a way to use the exisiting hibernate.sh script on fiesty so that suspend to disk works as well as the nice menu on power button etc and lock screen etc.

In /etc/acpi/hibernate.sh

Replace

```

if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
    . /etc/usplash.conf
    /sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
    /sbin/s2disk $DEVICE
    fi
else

```with

```

if [ -x /sbin/s2disk ]; then
     /sbin/s2disk
else

```This is because uswsusp uses a config now and the hibernate script has not been modified.

I raised a [bug]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/107377") but no one seems to care :P

---

### Post by dadde on 2007-07-29
> **Paul S said:**
> It sounds like you didn't correctly move the original files and create the new ones .. which means the original scripts are still running when you use the menus to hibernate / suspend. Open a terminal and check with these commands (see how you compare to mine):

paul :~$ ls -la /usr/lib/hal/scripts/linux/
total 64
drwxr-xr-x 2 root root 4096 2007-07-13 09:16 .
drwxr-xr-x 3 root root 4096 2007-05-18 21:53 ..
-rwxr-xr-x 1 root root 1283 2007-05-11 03:29 hal-luks-remove-linux
-rwxr-xr-x 1 root root 1093 2007-05-11 03:29 hal-luks-setup-linux
-rwxr-xr-x 1 root root  813 2007-05-11 03:29 hal-luks-teardown-linux
-rwxr-xr-x 1 root root 1965 2007-05-11 03:29 hal-system-killswitch-get-power-linux
-rwxr-xr-x 1 root root 2121 2007-05-11 03:29 hal-system-killswitch-set-power-linux
-rwxr-xr-x 1 root root 2393 2007-05-11 03:29 hal-system-lcd-get-brightness-linux
-rwxr-xr-x 1 root root 2447 2007-05-11 03:29 hal-system-lcd-set-brightness-linux
-rwxr-xr-x 1 root root   78 2007-07-13 20:57 hal-system-power-hibernate-linux
-rw-r--r-- 1 root root 3124 2007-07-13 09:16 hal-system-power-hibernate-linux.bak
-rwxr-xr-x 1 root root  333 2007-05-11 03:29 hal-system-power-reboot-linux
-rwxr-xr-x 1 root root  897 2007-05-11 03:29 hal-system-power-set-power-save-linux
-rwxr-xr-x 1 root root  335 2007-05-11 03:29 hal-system-power-shutdown-linux
-rwxr-xr-x 1 root root  112 2007-07-13 20:57 hal-system-power-suspend-linux
-rw-r--r-- 1 root root 4092 2007-07-13 09:15 hal-system-power-suspend-linux.bak

paul :~$ cat /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
#!/bin/sh

/sbin/s2ram

paul :~$ cat /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
#!/bin/sh

/sbin/s2disk

HTH

Ok..I followed the instrunction of Paul S
..not just the files had to be owned by the root, but I had to do a: chmod 755  on the files so as to have the same kind of permissions (-rwxr-xr-x). 

Then I had to run the command: 
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
and now both hibernate and suspend work ..except for the network: 

I tried to follow this thread [http://ubuntuforums.org/showthread.php?t=402616](http://ubuntuforums.org/showthread.php?t=402616) but I have still problems..

Anyway..thanks Paul!

---

### Post by maestrobwh1 on 2007-07-31
Nope... this still doesn't work on my **desktop**.  s2disk --force makes the computer suspend, but on waking... well, there is no screen until I wiggle the mouse... and I get just flickering (still mostly black with random horizontal bands) when I do this... and it goes back to blank when I stop moving the mouse.  If I do a ctrl-alt F1 then a ctrl-alt-del, the computer obviously goes through a proper shutdown script and no harm is done on reboot.  I tried this on my Feisty and Gutsy installs with same results.  Ditto all the way back to Dapper and Edgy.

Here is my hal-system-power-suspend **before **the modifications (I bolded where there might be a problem?).  The bios is set to use si and s3, and suspend/hibernate works flawlessly in XP.  

#!/bin/sh

POWERSAVED_SUSPEND2RAM="dbus-send --system --dest=com.novell.powersave \
                        --print-reply /com/novell/powersave \
                        com.novell.powersave.action.SuspendToRam"

alarm_not_supported() {
	echo org.freedesktop.Hal.Device.SystemPowerManagement.AlarmNotSupported >&2
	echo Waking the system up is not supported >&2
	exit 1
}

unsupported() {
	echo org.freedesktop.Hal.Device.SystemPowerManagement.NotSupported >&2
	echo **No suspend method found** >&2
	exit 1
}

read seconds_to_sleep

# Make a suitable command line argument so that the tools can do the correct
# quirks for video resume.
# Passing the quirks to the tool allows the tool to not depend on HAL for data.
QUIRKS=""
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-bios"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-mode"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-suspend"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-on"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBESTATE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbestate-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBEMODE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbemode-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VGA_MODE_3" = "true" ] && QUIRKS="$QUIRKS --quirk-vga-mode3"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBE_POST" = "true" ] && QUIRKS="$QUIRKS --quirk-vbe-post"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_RADEON_OFF" = "true" ] && QUIRKS="$QUIRKS --quirk-radeon-off"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_NONE" = "true" ] && QUIRKS=" --quirk-none"

#PMU systems cannot use /sys/power/state yet, so use a helper to issue an ioctl
if [ "$HAL_PROP_POWER_MANAGEMENT_TYPE" = "pmu" ]; then
	hal-system-power-pmu sleep
	if [ $? -ne 0 ]; then
		echo "org.freedesktop.Hal.Device.SystemPowerManagement.NotSupported" >&2
		exit 1
	fi
	exit 0
fi

#ALTLinux only supports powersave
if [ -f "/etc/altlinux-release" ]; then
	if [ -x /usr/bin/powersave ] ; then
	        $POWERSAVED_SUSPEND2RAM
		RET=$?
	else
		# TODO: add support
		unsupported
	fi

#Mandriva supports suspend-scripts 
elif [ -f "/etc/mandriva-release" ] ; then 
    # TODO: fix pmsuspend to take a --wakeup-alarm argument 
    if [ $seconds_to_sleep != "0" ] ; then 
	alarm_not_supported 
    fi 
    
    if [ -x "/usr/sbin/pmsuspend" ] ; then 
	/usr/sbin/pmsuspend memory
	RET=$? 
    else 
        # TODO: add support 
	unsupported 
    fi 

#RedHat/Fedora and SUSE support pm-utils
elif [ -f "/etc/redhat-release" ] || [ -f "/etc/fedora-release" ] \
		|| [ -f "/etc/SuSE-release" ] ; then
	# TODO: fix pm-suspend to take a --wakeup-alarm argument
	if [ $seconds_to_sleep != "0" ] ; then
		alarm_not_supported
	fi
	# TODO: fixup pm-suspend to define erroc code (see alarm above) and throw
	#	   the appropriate exception
	if [ -x "/usr/sbin/pm-suspend" ] ; then
		/usr/sbin/pm-suspend $QUIRKS
		RET=$?
	else
		# TODO: add support
		unsupported
	fi

#Other distros just need to have *any* tools installed
else
	if [ -x "/usr/sbin/pm-suspend" ] ; then
		/usr/sbin/pm-suspend $QUIRKS
		RET=$?
	elif [ -x "/usr/bin/powersave" ] ; then
		$POWERSAVED_SUSPEND2RAM
		RET=$?
	elif [ -x "/usr/sbin/hibernate" ] ; then
		# Use hibernate configured for suspend-to-ram
		/usr/sbin/hibernate -F/etc/hibernate/ram.conf
		RET=$?
	elif [ -x "/etc/acpi/sleep.sh" ] ; then
		# Use acpi-support for suspend to ram 
		/etc/acpi/sleep.sh force
		RET=$?
	elif [ -x "/usr/sbin/s2ram" ] ; then
		# uswsusp tools installed
		/usr/sbin/s2ram
		RET=$?
	elif [ -x "/usr/sbin/pmi" ] ; then
		/usr/sbin/pmi action suspend force
		RET=$?
	elif [ -w "/sys/power/state" ] ; then
		# Use the raw kernel sysfs interface
		echo "mem" > /sys/power/state
		RET=$?
	else
		# TODO: add other scripts support
		unsupported
	fi
fi

#Refresh devices as a resume can do funny things
for type in button battery ac_adapter
do
	devices=`hal-find-by-capability --capability $type`
	for device in $devices
	do
		dbus-send --system --print-reply --dest=org.freedesktop.Hal \
			  $device org.freedesktop.Hal.Device.Rescan
	done
done

exit $RET

---

### Post by zasq on 2007-08-03
Hi everybody!

This Howto helped me a lot! Thank you. It was the only way to get my Dell Inspiron 1501 with ATI Radeon Xpress 1100 to hibernate!!! Even the newest  ATI-linux driver (8.39.4) wouldn't do. I couldn't find a similar Howto in the german Forums - so thank you!

But I still have a question: Could it be, that frequent hibernation fills the swap up? I have the feeling that my programs like OpenOffice don't get enough memory to run!

I'm an absolute newbie with both linux and ubuntu so a hint would be great.

Thanks again,

zasq

---

### Post by Paul S on 2007-08-03
> **zasq said:**
> Hi everybody!

This Howto helped me a lot! Thank you. It was the only way to get my Dell Inspiron 1501 with ATI Radeon Xpress 1100 to hibernate!!! Even the newest  ATI-linux driver (8.39.4) wouldn't do. I couldn't find a similar Howto in the german Forums - so thank you!

But I still have a question: Could it be, that frequent hibernation fills the swap up? I have the feeling that my programs like OpenOffice don't get enough memory to run!

I'm an absolute newbie with both linux and ubuntu so a hint would be great.

Thanks again,

zasq

Just type "top" in a terminal to see your process usage and swap usage.  I don't think the image saved to swap remains, but don't know for sure.

regards,

---

### Post by Paul S on 2007-08-03
> **dadde said:**
> 
and now both hibernate and suspend work ..except for the network: 


For me, some of the things take a while (maybe minute or more) to come back .. network is among them.  If you just sit and do nothing, perhaps it will restart itself eventually.

regards,

---

### Post by scholzilla on 2007-08-07
I have the same problem as unnicknamed does: hibernate runs with the proposed edit of hal-system-power-hibernate-linux, but now hiberating disables the sound. Sound can be restored by rebooting, which sort of defeats the purpose of hibernating. I'm using a Gateway MT-something laptop and feisty is my only OS. I've restored my old version of hal-system-power-hibernate-linux and the sound works fine, but of course, the hibernate doesn't, Any advice is appreciated.


UPDATE: [This]("http://ubuntuforums.org/showthread.php?p=3151492#post3151492") fix, on the other hand, DID work without disabling my sound.

---

### Post by Mach1US on 2007-08-09
Many Thanks :lolflag:
Works without any modifications on DELL Inspiron 6000 with integrated graphics .
Fantastic Fix !!!

---

### Post by shadowhywind on 2007-08-14
This seams to work on a dv6000 as well, but only if i remove icqfixup from the boot *icqfixup fixes ubuntu from slowing down when i go idle for 5+ mins*. Does anyone have any ideas on why icqfixup would cause s2disk to freeze?

I fixed my issue and changed icqfixup to icqpoll instead. Hibernate works, and ubuntu doesn't freeze. Incase anyone ever has the same problem again.

---

### Post by FrancoNero on 2007-08-15
short question: does the S2RAM/S2DISK method at the beginning of this thread fix issues where HP laptops "lose" mouse/touchpad and keyboard upon resuming from suspend/hibernate?

edit: no it doesn't....
s2ram "works" on my HP compaq nx7400, but what good is it if I can't do anything after I wake it up again ;-)

---

### Post by st33med on 2007-08-20
This is wierd. Sometimes the s2ram 'breaks' the process of suspending, and displays flickering boxes...
And sometimes the shutdown or hibernation does the same. Not always, though.

Suspend worked before the script, so I'll restore that script.

---

### Post by SeanBlader on 2007-08-20
s2ram works, but resume hangs, love to hear any tips for my Inspiron 8500 with nVidia graphics.

Exactly the same effect with s2disk, seems to hibernate perfectly but doesn't start back up.

---

### Post by mufflon on 2007-08-21
> **FrancoNero said:**
> short question: does the S2RAM/S2DISK method at the beginning of this thread fix issues where HP laptops "lose" mouse/touchpad and keyboard upon resuming from suspend/hibernate?

Found this thread when looking for a solution.
s2ram works like a charm on my HP nc6320, except the tiny drawback of not having any keyboard or mouse after resuming. ;)

Now I did find a solution. After resume these two lines wakes up my keyboard and mouse:
```
sudo sh -c 'echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind'
sudo sh -c 'echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind'
```
I found it here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/23497/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/23497/comments/17)


Since I do not have the time to go diggin' for scripts now I just wonder:
Is there any script called when resuming where I can put those two lines of code? When I'm on the bus I cannot use ssh to do this...

edit: Created a new script /etc/acpi/resume.d/99-reinit-i8042.sh
```

#!/bin/sh  

# Force re-init of the i8042 PS/2 keyboard/mouse controller
echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind

```

Now I have another question: It works just fine but should it be run as the last script (99-*)
or should it run earlier in the resume-process?!?

---

### Post by Dark Star on 2007-08-21
Thanks a ton.. Just fixed this in my frnds lappy :D

---

### Post by owhno on 2007-08-22
Hi,

Since a few days i have got Gutsy Gibbon on 2.6.22-10 kernel. In Gutsy the uswsusp packages has been altered. s2ram has been renamed to s2both. 

But it works fantastic only a little bit slower on making the image and no password  on resume. how to enable this?

---

### Post by qfwills on 2007-08-25
That has fixed a long-standing susp/hib problem of mine thanks. HOWEVER, if anybody has advice on how NOT to have (k)ubuntu make crackling sounds and distorted screens on coming out of suspension/hibernation I'd be enormously grateful. I have an HP nx8220, but seem to remember the same issue with a DELL I have. It looks aweful and very unprofessional. I won't be taking my HP into a boardroom any time soon until it boots up 'pretty' :)

---

### Post by qfwills on 2007-08-25
That has fixed a long-standing susp/hib problem of mine thanks. HOWEVER, if anybody has advice on how NOT to have (k)ubuntu make crackling sounds and distorted screens on coming out of suspension/hibernation I'd be enormously grateful. I have an HP nx8220, but seem to remember the same issue with a DELL I have. It looks aweful and very unprofessional. I won't be taking my HP into a boardroom any time soon until it boots up 'pretty'

---

### Post by Mateo on 2007-08-26
Anyone had success getting resume to work on the Toshiba Satellite?  thanks.

---

### Post by Xomphos on 2007-08-27
Hi,

I have a Dell Inspiron 4150, and although the hibernate was working, sleep mode isn't. I did as directed for the sleep mode and found out the sleep --force command worked. However, when I modified the file, it didn't work still.

Any ideas?

Thanks! :D

---

### Post by -SpaZ on 2007-08-27
Thank you. This has been bugging a bunch of people for a while.

---

### Post by EXCiD3 on 2007-08-27
Hopefully Gutsy will have much better support out ofthe box *crosses fingers*

---

### Post by FrancoNero on 2007-08-27
ok i'm running the latest gutsy available. as i'm postin gthis, aptitude won't offer any new updates.

so i finally got SUSPEND working for the FIRST TIME EVER. And I am not only talking putting my HP Laptpo to sleep, it also woke up fine and I had touchpad and keyboard. I will try to repeat it a few more times tomorrow to see if it really works now (FINALLY!! kernel x....11.10 or something) or if it was an exception.

HIBERNATE still doesn't work at all, it just refuses and gives me an error and a link to Quirk....

any ideas? I am seriously not interested in any fixes or scripts or kernel patches, because a) if it doesnt work out of the box, what good is it on a laptop and b) i am not using ubunu on a production partition yet so i can wait..... I want to see all this work out of the box, which is my main stopper from switching to ubuntu (aside from TINY fonts here in firefox that give me eye cancer, haha)

---

### Post by Jeremy23 on 2007-08-29
Cool, this fixes hibernate on my N610c. Hibernate worked fine on Edgy, and on Feisty sometime in Feb/Mar, but broke around April, near Feisty's release. Thanks, it's working awesomely now!

However, you don't need to replace that HAL script. An easier solution for me was:

```
$ sudo mv /etc/acpi/hibernate.sh /etc/acpi/hibernate.sh.disabled
$ sudo vi /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```

Then, I change all instances of this:

```
/usr/sbin/s2disk
```

to this:

```
/sbin/s2disk
```

(a vim command for that is...)

```
:%s/\/usr\/sbin\/s2disk/\/sbin\/s2disk/
```

---

### Post by twrock on 2007-08-29
Dell 700m will suspend if the lid is closed or if it is plugged into power. It will not suspend if it is running on batteries. It will not hibernate in any circumstance. So the really important situation to have it work (on batteries) doesn't. Frustrating. Maybe I'll revert to a previous version too.

---

### Post by korser on 2007-09-02
[QUOTE=mufflon;3227039]
edit: Created a new script /etc/acpi/resume.d/99-reinit-i8042.sh
```

#!/bin/sh  

# Force re-init of the i8042 PS/2 keyboard/mouse controller
echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind

```

Thanks this work perfectly with my HP nw9440. I don't even need to use s2ram and s2disk. I works with the regular suspend/hibernate from feisty.

---

### Post by sureinlux on 2007-09-04
Hi, 
 I have a AMD Turion 64 X2 processor and 2 GB RAM. After installing the above mentioned application, my s2disk works perfectly fine, except for two problems. After resuming for hibernation:
[LIST]
[*]only one of the processors work
[*]sound does not work
[/LIST]

Thank you for any help, especially for the first problem. My laptop is Compaq Presario 3029

---

### Post by rzrgenesys187 on 2007-09-11
When i try to install uswsusp i get this screen (attached file).  I know it says to run the dpkg-reconfigure but i've done it before and always manage to mess something up.  is there any better way to solve this?

Found this thread and worked perfect for me [http://ubuntuforums.org/showthread.php?t=503587](http://ubuntuforums.org/showthread.php?t=503587) on my toshiba satellite for the person who mentioned they had one

---

### Post by Albireo on 2007-09-16
Hello:

I've followed the howto and finally and after a lot of tries i've successfully activate hibernate and suspend on my laptop. I have also change the contents of hal files to point to /sbin/s2ram or /sbin/s2disk. When I try to hibernate or suspend pressing the buttons of the log out menu of KDE, all seems to work perfectly. But I try to use the power button of my laptop to hibernate (changing the contents of /etc/acpi/powerbtn.sh) the computer hang up.

That' not a serious issue but I'd like to solve it to be sure that when I try to hibernate anyway, the computer is going to do that.

Thanks.

Albireo

---

### Post by rscarriere on 2007-09-16
I was having difficulty getting my wifi  (intel 3945 chip in thinkpad r60e) back after I resumed (s2ram).  I figured out that if I reload the driver that would fix things.   To have this done automatically my /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux script looks like this:
```

/sbin/modprobe -r ipw3945
/sbin/s2ram --force
/sbin/modprobe ipw3945

```

I'm no expert on uswsusp but it seems to work for me.

---

### Post by jarich on 2007-09-18
> **Jeremy23 said:**
> 
However, you don't need to replace that HAL script. An easier solution for me was:

```
$ sudo mv /etc/acpi/hibernate.sh /etc/acpi/hibernate.sh.disabled
$ sudo vi /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```
...


Thanks for this advice Jeremy.  When I looked inside

```
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```

I found that it did point to ```
/sbin/s2disk
``` so that wasn't my problem.  However I didn't want to move the hibernate.sh script away without understanding what I was doing, so I looked a little closer.  What I found was that in hal-system-power-hibernate-linux, it checks to see if:

```
/etc/acpi/hibernate.sh
``` 

exists before it checks for: 

```
/sbin/s2disk
```  

So merely installing uswsusp couldn't solve the problem.  In order to have /sbin/s2disk be called, I'd need to change something and your suggestion of moving away the troublesome files seemed the least dangerous to me.

I have a Dell Inspiron 8600, with bios_version "A13" running Feisty Fawn and this works perfectly for me.  So to summarise, in order to fix this problem I did the following:

```
sudo apt-get install uswsusp
sudo mv /etc/acpi/hibernate.sh /etc/acpi/hibernate.sh.disabled
sudo mv /etc/acpi/sleep.sh /etc/acpi/sleep.sh.disabled
```

and the rest just worked.  :)

---

### Post by jarich on 2007-09-18
I just walked through this with a friend of mine who also has a Dell Inspiron (different model) and this didn't work for them.  Apparently they had both /usr/sbin/pmi/ and /etc/acpi/sleep.sh installed somehow.

So when we looked at /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux both were checked before /sbin/s2ram.

Our solution was to make the following edits:

```

# /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
# From line 81 change else block to look as follows:

#Other distros just need to have *any* tools installed
else
        if [ -x "/usr/bin/powersave" ] ; then
            $POWERSAVED_SUSPEND2RAM
            RET=$?
        # moved the next three lines up to here
        elif [ -x "/sbin/s2ram" ] ; then
            /sbin/s2ram
           RET=$?
        elif [ -x "/usr/sbin/pmi" ] ; then
            /usr/sbin/pmi action suspend force
            RET=$?
        elif [ -x "/usr/sbin/hibernate" ] ; then
            # Use hibernate configured for suspend-to-ram
            /usr/sbin/hibernate -F/etc/hibernate/ram.conf
            RET=$?
        elif [ -x "/etc/acpi/sleep.sh" ] ; then
            # Use acpi-support for suspend to ram
            /etc/acpi/sleep.sh force
            RET=$?
        elif [ -w "/sys/power/state" ] ; then
            # Use the raw kernel sysfs interface
            echo "mem" > /sys/power/state
            RET=$?
        else
            # TODO: add other scripts support
            unsupported
            fi
        fi

```

```

# /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
# From line 40 change else block to look as follows:

#Other distros just need to have *any* tools installed
else
        if [ -x "/usr/bin/powersave" ] ; then
                $POWERSAVED_SUSPEND2DISK
                RET=$?
       # moved the next three lines up to here
        elif [ -x "/sbin/s2disk" ] ; then
                /sbin/s2disk
                RET=$?
        elif [ -x "/usr/sbin/pmi" ] ; then
                /usr/sbin/pmi action hibernate force
                RET=$?
        elif [ -x "/usr/sbin/pm-hibernate" ] ; then
                /usr/sbin/pm-hibernate
                RET=$?
        elif [ -x "/usr/sbin/hibernate" ] ; then
                # Suspend2 tools installed
                /usr/sbin/hibernate --force
                RET=$?
        elif [ -x "/etc/acpi/hibernate.sh" ] ; then
                # acpi-support installed
                /etc/acpi/hibernate.sh force
                RET=$?
        elif [ -w "/sys/power/state" ] ; then
                # Use the raw kernel sysfs interface
                echo "disk" > /sys/power/state
                RET=$?
        else
                unsupported
                fi
        fi

```

This forces the script to call /sbin/s2ram and /sbin/s2disk first, however if for some reason in an upgrade or some other reason you lose these scripts, it'll try other options.  All things considered, if we're changing this file anyway, it might be worthwhile just replacing as per the suggestion of the original poster.

---

### Post by st33med on 2007-09-22
Thank you for this! Compiz Fusion somehow was screwing up my standby. This, however, fixed everything and make suspend faster and shutdowns as well because it was saving data to the hard disk on suspend.

---

### Post by ddumanis on 2007-09-24
Confirming that this fixed Compiz-Fusion screwing up MY standby too (on Dell Latitude D600).

**Why isn't this the default suspend in the kernel?** Any way to make that happen?

EDIT: On upgrading to Gutsy, the command s2ram (or s2ram --force) is no longer recognized. s2disk still works fine.

---

### Post by Spazztastic on 2007-09-26
> **ukripper said:**
> I know few people having this problem in feisty I will ask them to try this.

On my laptops there are no problems either on Edgy or Feisty.

Good work though.

Fixed my problem on Feisty with my Inspiron 1501

---

### Post by peabody on 2007-10-09
[B]Note: Nevermind the below post...I think my problems were related to the fact that I was running an encrypted swap which was initialized with a random key.  I since removed encryption and discovered that s2disk does seem to work for me.  A comment in this blog post ([http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)) however, suggested using dpkg-divert to move the pmi binary out of the way so the suspend/hibernate scripts default to the s2ram and s2disk scripts.  This will make it so that system updates don't clobber your changes.  The command was:

 sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

Then if you need to switch back to the old style, you can use this command:

sudo dpkg-divert --rename --remove /usr/sbin/pmi

[/B]



Contrary to the vast majority of success stories I've read here, this caused nothing but problems for me.  I was having intermittent suspend problems (crashing X, freezes) on my compaq presario c571nr.  Suspend worked about 90% of the time, but would fail the rest of the time.  Hibernate, however, was working flawlessly.  However, after having tried s2disk, hibernate has been permanently broken for me!!!  Even after a '--purge remove' and replacing all scripts involved from backup, hibernate does not work anymore!

I would like to know if there's anything I can try to get hibernate working again.  And as a favor to the community, I think the OP should place a warning of the dangers of trying s2disk when hibernate is already working.

---

### Post by xlr8ed on 2007-10-09
Works fine on my Dell 6400 with no problems

---

### Post by disembodied on 2007-10-12
I have used this fix a few different times to solve my suspend issues on my ASUS S96J laptop (AKA ASUS Z96js). 
It always solves the issue, BUT seemingly causes ubuntu to boot up a lot slower then it does by default. If I look at the POST info it seems to  hang on the search for a disk to reload data from. (ie the search for data from a hibernation).

Does anyone else have this problem? If so is there a way to fix it? or am I just crazy?

---

### Post by samuraiche on 2007-10-12
Hi guys,

is there anyway to fix this susped/hibernate issue for Gutsy Gibbon?
After a recent update suspend/hibernate just stopped working.
And the tips given above are all for Feisty,so i cannot use them.

any ideas?

---

### Post by peabody on 2007-10-12
> **samuraiche said:**
> Hi guys,

is there anyway to fix this susped/hibernate issue for Gutsy Gibbon?
After a recent update suspend/hibernate just stopped working.
And the tips given above are all for Feisty,so i cannot use them.

any ideas?

Are you sure you can't use them just because they're for feisty?  Are you sure that the suspend/hibernate setup has changed so dramatically between feisty and gutsy?  Not saying it hasn't, but I'd be surprised if there was nothing you could use from this thread.

---

### Post by samuraiche on 2007-10-12
> **peabody said:**
> Are you sure you can't use them just because they're for feisty?  Are you sure that the suspend/hibernate setup has changed so dramatically between feisty and gutsy?  Not saying it hasn't, but I'd be surprised if there was nothing you could use from this thread.

Hi,

well, ive tried to install uswsusp and after installation i got a windows with a checkbox in it and that was something about the swap partition.....after that I removed that package and installed it from console:sudo apt-get install uswsusp. I could install it but after installation commands like s2ram were not recognized. That 's the first issue.And I noticed that after previously upgrade to kernel 2.6.22-14 my suspend fails...but if i load to kernel 2.6.20-16...then it works fine...so yeah...that's it :)

cheers

---

### Post by michael37 on 2007-10-12
About s2ram and Gutsy: a simple check 
```

dpkg -L uswsusp

```
on Gutsy confirms that /sbin/s2disk and /sbin/s2both exist, but /sbin/s2ram does not.  

Does anyone know what is going on?  Was there a bug filed?

---

### Post by jw5801 on 2007-10-12
Didn't "s2both" wind up replacing "s2ram"? I seem to remember reading that somewhere. What happens if you run s2both? Does it hibernate or suspend? If it suspends and you really wanna use s2ram, then create a link!

---

### Post by samuraiche on 2007-10-13
With this command dpkg -L uswsusp i get this output:
/.
/etc
/usr
/usr/sbin
/usr/lib
/usr/lib/uswsusp
/usr/lib/uswsusp/resume
/usr/share
/usr/share/initramfs-tools
/usr/share/initramfs-tools/hooks
/usr/share/initramfs-tools/hooks/uswsusp
/usr/share/initramfs-tools/scripts
/usr/share/initramfs-tools/scripts/local-premount
/usr/share/initramfs-tools/scripts/local-premount/uswsusp
/usr/share/initramfs-tools/conf.d
/usr/share/initramfs-tools/conf.d/uswsusp
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/doc
/usr/share/doc/uswsusp
/usr/share/doc/uswsusp/changelog.gz
/usr/share/doc/uswsusp/HOWTO.gz
/usr/share/doc/uswsusp/README
/usr/share/doc/uswsusp/TODO
/usr/share/doc/uswsusp/README.Debian-source
/usr/share/doc/uswsusp/README.Debian
/usr/share/doc/uswsusp/copyright
/usr/share/doc/uswsusp/changelog.Debian.gz
/usr/share/doc/uswsusp/README.s2ram-whitelist.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/suspend-keygen.8.gz
/usr/share/man/man8/swap-offset.8.gz
/usr/share/man/man8/s2disk.8.gz
/usr/share/man/man8/uswsusp.conf.8.gz
/sbin
[B]/sbin/s2disk
/sbin/s2both[/B]
/sbin/swap-offset
/sbin/suspend-keygen
/usr/share/man/man8/resume.8.gz
/usr/share/man/man8/s2both.8.gz
 

so s2disk and s2both are there but if i try
$ sudo s2both or s2disk i get this message:
*s2both: Could not stat the resume device file. Reason: No such file or directory*

I thougt that is has smthg to do with my swap partion which is 2GB,coz I have 2gb ram..
I've also tried swapoff and swapon but it doesn't change anything :)

thnx :)

---

### Post by namgar on 2007-10-15
> **samuraiche said:**
> With this command dpkg -L uswsusp i get this output:
/.
/etc
/usr
/usr/sbin
/usr/lib
/usr/lib/uswsusp
/usr/lib/uswsusp/resume
/usr/share
/usr/share/initramfs-tools
/usr/share/initramfs-tools/hooks
/usr/share/initramfs-tools/hooks/uswsusp
/usr/share/initramfs-tools/scripts
/usr/share/initramfs-tools/scripts/local-premount
/usr/share/initramfs-tools/scripts/local-premount/uswsusp
/usr/share/initramfs-tools/conf.d
/usr/share/initramfs-tools/conf.d/uswsusp
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/doc
/usr/share/doc/uswsusp
/usr/share/doc/uswsusp/changelog.gz
/usr/share/doc/uswsusp/HOWTO.gz
/usr/share/doc/uswsusp/README
/usr/share/doc/uswsusp/TODO
/usr/share/doc/uswsusp/README.Debian-source
/usr/share/doc/uswsusp/README.Debian
/usr/share/doc/uswsusp/copyright
/usr/share/doc/uswsusp/changelog.Debian.gz
/usr/share/doc/uswsusp/README.s2ram-whitelist.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/suspend-keygen.8.gz
/usr/share/man/man8/swap-offset.8.gz
/usr/share/man/man8/s2disk.8.gz
/usr/share/man/man8/uswsusp.conf.8.gz
/sbin
[B]/sbin/s2disk
/sbin/s2both[/B]
/sbin/swap-offset
/sbin/suspend-keygen
/usr/share/man/man8/resume.8.gz
/usr/share/man/man8/s2both.8.gz
 

so s2disk and s2both are there but if i try
$ sudo s2both or s2disk i get this message:
*s2both: Could not stat the resume device file. Reason: No such file or directory*

I thougt that is has smthg to do with my swap partion which is 2GB,coz I have 2gb ram..
I've also tried swapoff and swapon but it doesn't change anything :)

thnx :)

I know this isn't very helpful but you are not alone ... I have all of the problems you have been having.  Hibernate worked with 2.6.20-16, but doesn't with 2.6.22-?? (anything up to and including 14).

I have also had the same errors trying to get uswsusp working ... I'll let you know if I figure it out.

I'm using an Inspiron 9400...

---

### Post by zorkerz on 2007-10-16
Im running gutsy and am also having the problem where s2ram is not a recognized command giving terminal output "command not found"

s2disk works great and i have set it as the default with this howto.

does anyone know what happened in gutsy to make the s2ram command disappear?

cheers

---

### Post by ddumanis on 2007-10-16
On machines with ATI cards, neither suspend nor hibernate (out of the box or S2Disk/S2Both) work with the current version of gutsy. An incompatibility with the ATI driver is rumored to be the culprit, and it's theoretically ATI's responsibility to fix it.

So, we with ATI cards are stuck without any working suspend for now.

---

### Post by Paul S on 2007-10-16
I've just installed gutsy (7.10RC) and have not yet added uswsusp.  After just 2 days, my suspend has worked about 8 times, but 2 other times, it rebooted.  So far, hibernate has worked ok.  I'm not sure if I need uswsusp yet.  I want to try to see I can tweek suspend to get it to work all the time.

> does anyone know what happened in gutsy to make the s2ram command disappear?

If you check the /usr/share/doc/uswsusp/changelog.Debian.gz, you'll see this:

```
uswsusp (0.6~cvs20070618-1ubuntu2) gutsy; urgency=low

  * Don't build s2ram. It's not sensible on Ubuntu. 

 -- Matthew Garrett <mjg59@srcf.ucam.org>  Mon, 20 Aug 2007 15:47:18 +0100
```

I think s2ram was removed because s2both was designed to replace it.  s2both copies the program info into your swap space, just like s2disk, and then is supposed to suspend to RAM (like the old s2ram).  The idea is that if your laptop battery goes dead in a suspend to RAM period, you could still recover when you next plug in and boot up, because the s2both saved the image in your swap space too.

What does "man s2both" show.  If it's the replacement for s2ram, then you should be able to experiment with it and get it going.

---

### Post by zorkerz on 2007-10-16
I was not pleased with the way the s2both command worked. It appeared to suspend to ram as expected but when I tried to open again it was like starting the computer from an off state. the bios went and the grub and it took nearly as long as resuming from hibernate the s2disk command
elias

---

### Post by Paul S on 2007-10-16
For the gutsy version, if you read the /usr/share/doc/uswsusp/README.Debian.gz, you will see:

```
Ubuntu specific notes
---------------------

The s2ram binary is not included in the Ubuntu package. Equivalent
functionality is provided by acpi-support.

-- Matthew Garrett <mj59@srcf.ucam.org>

```

So, I think Garrett must have incorporated s2ram into acpi-support in gutsy.

But, apparently, s2disk (hibernate) is not incorporated.  However, in my specific Dell E1505 with nvidia 7300, I do have the ability to hibernate in gutsy, but it did not in feisty.  s2disk helped in feisty for me.

FWIW ..

---

### Post by Permafrost91 on 2007-10-17
latest Gutsy on an IBM X60 ... neither the default suspend/hibernate of uswsusp work. Not having suspend/hibernate work is a major turn-off for Gutsy laptop users, if you ask me. So how can we get this to work?

---

### Post by Paul S on 2007-10-17
> So how can we get this to work?

Try playing around with the options in /etc/default/acpi-support.  I had to set SAVE_VBE_STATE=false and POST_VIDEO=false .. but not an IBM.  Try each one on and off.  I must confess that my suspend is not much better than Feisty.  It'll work 4 or 5 times, but then something strange happens (i.e. won't resume at all, keyboard repeat stops working, reboots instead of resume, localhost is unreachable for some programs, etc.)  In all fairness though, I've seen strange things happen when running M$ and resuming from "sleep", so it's not all just a linux problem.

regards,

---

### Post by samuraiche on 2007-10-19
As I mentioned before my suspend/hibernate doesn't work if I boot to kernels above 2.6.20-16.So if we could see what has been changed in the kernel(? or acpi?) sinds 2.6.20-16 we could determine the problem.

So, where can we see all this?

thanx

---

### Post by dadde on 2007-10-19
Even for me the s2disk in Gutsy doesn't work fine. It hibernates the PC (hp dv2000) but when I resume I've got several "disturbances" (I just can see several lines shaking) on the screen.

Any idea, suggestion or what else?

dadde

---

### Post by zorkerz on 2007-10-19
This looks promising if you are looking for a changelog to the linux kernel though I think there will be alot of stuff to go through. [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

there could be better stuff out there im sure google knows

---

### Post by samuraiche on 2007-10-19
Here I want to describe what i get when trying to suspend on kernel 2.6.22-14.
When I do suspend I get a black screen on my laptop then it just hangs...and neither keyboard nor mouse work. It seems that it suspends but not "fully"...leds on my laptop are still on..but as i said it becomes irresponible....

I have also tried to change in /etc/default/acpi-support SAVE_VBE_STATE and POST_VIDEO but still nothing :)

---

### Post by Ingenium on 2007-10-20
I'm having the exact same problem. Suspend (via the logout/Quit menu) looks like it suspends my computer, but then it just hangs with the LEDs all on rather than actually suspending.

Suspend to disk wasn't working for me either, but this was because my swap partition was smaller than my RAM. When I run s2disk it hibernates fine, but when I run s2both it also hibernates (ie powers off completely) rather than S3 suspend. 

For some reason, the hibernate function on the logout menu looks like it tries to hibernate and the screen flickers and goes blank, but then loads again and gives me a login type screen to unlock the computer. I thought this used s2disk?

---

### Post by Diabolis on 2007-10-20
I installed uswsusp. Now I can suspend through the GUI or by typing the appropriate command in the terminal, but not by closing the lid. Also, I used to be able to awake my laptop by pressing any key on the keyboard, but now it will work only by pressing the power button.

Acer Travelmate 2420

---

### Post by brk3 on 2007-10-22
The s2disk is working which is a linux first for me ever!  Just really gets me wondering if the s2ram would work too though which is what I really want, any ideas how to get this command back seen as it was taken out of the package?

---

### Post by Sunnz on 2007-10-22
Anyone here happens to be running 64-bit OS with 4 GB of RAM?

Suspend worked out of the box on Gutsy BEFORE I enabled 4 GB of RAM in the BIOS. Now I have enabled 4 GB in the BIOS to let Gutsy to access all 4 GB of RAM and Suspend just fails to work anymore, it just "suspends", but REBOOTS when I try to wake it up.

---

### Post by peabody on 2007-10-22
> **Sunnz said:**
> Anyone here happens to be running 64-bit OS with 4 GB of RAM?

Suspend worked out of the box on Gutsy BEFORE I enabled 4 GB of RAM in the BIOS. Now I have enabled 4 GB in the BIOS to let Gutsy to access all 4 GB of RAM and Suspend just fails to work anymore, it just "suspends", but REBOOTS when I try to wake it up.

This may or may not be relevant, but how big is your swap partition?

---

### Post by Sunnz on 2007-10-22
> **peabody said:**
> This may or may not be relevant, but how big is your swap partition?
5 GB.

---

### Post by Sunnz on 2007-10-22
I just disabled 4 GB support in the BIOS, and now I only have access to 3.2 GB of my 4 GB RAM... but Suspend now works again... so perhaps I have a totally different problem here, anyone know where can I get help with this?

---

### Post by ecoxmit on 2007-10-22
this just works for me
Gutsy, Thinkpad x61t

---

### Post by bbqsandwich on 2007-10-22
This worked for my Acer Aspire 3680 laptop.

However, first I had to change the swap space that uswsusp uses by following the directions here:

[http://ubuntuforums.org/showpost.php?p=3573566&postcount=12](http://ubuntuforums.org/showpost.php?p=3573566&postcount=12)

Now my hibernate works great!

I still can't suspend, and am currently trying different acpi_support options. Like others, I wish s2ram was still around so I could at least give it a try.

---

### Post by EXCiD3 on 2007-10-22
> **Sunnz said:**
> I just disabled 4 GB support in the BIOS, and now I only have access to 3.2 GB of my 4 GB RAM... but Suspend now works again... so perhaps I have a totally different problem here, anyone know where can I get help with this?

Are you running 64bit? I'm not sure but that might make a difference.

---

### Post by Permafrost91 on 2007-10-22
thank you bbqsandwich!! I can now hibernate my ThinkPad ... I still can't suspend though

---

### Post by Permafrost91 on 2007-10-22
I guess I spoke too soon ... I set up the two HAL scripts as outlined in the first post and Gutsy now suspends/hibernates (well, it really only hibernates) after a few minutes of idle time, as set in the preferences ... BUT! when resuming, it immediately suspends/hibernates again. After the second resume in a row, I get back to Gnome and an error message in the systray informs me that suspend didn't quite work and that there would be more info in the help system. This does not happen when I call s2disk/s2both from the CLI. Is anyone else having these problems?

---

### Post by yexin218 on 2007-10-22
Hello, it is necessary to configure something about uswsusp when installing it.
The notice is:
```
 The swap file or partition that was found in uswsusp's configuration      &#9474;  
 &#9474; file is not active. In most cases this means userspace software suspend   &#9474;  
 &#9474; will not work for you and you will need to choose (or let uswsusp         &#9474;  
 &#9474; choose) another swap space. In some corner cases however, this can be     &#9474;  
 &#9474; what you want.                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Continue without a valid swap space? 
```
does it mean that if the usrspace's configuration file is active, and then i could suspend my laptop?,right? and how?
I choose "NO" to continue the installation. and it shows 
```
liceven@liceven-laptop:~$ sudo s2ram
sudo: s2ram: command not found
liceven@liceven-laptop:~$ sudo s2ram --force
sudo: s2ram: command not found
```
the same result with "YES"
so, what can i do?
thanks very much.

---

### Post by Sunnz on 2007-10-22
> **EXCiD3 said:**
> Are you running 64bit? I'm not sure but that might make a difference.

Yes, 64-bit all the way here, CPU and OS and all my application software.

---

### Post by Sunnz on 2007-10-22
> **yexin218 said:**
> Hello, it is necessary to configure something about uswsusp when installing it.
The notice is:
```
 The swap file or partition that was found in uswsusp's configuration      &#9474;  
 &#9474; file is not active. In most cases this means userspace software suspend   &#9474;  
 &#9474; will not work for you and you will need to choose (or let uswsusp         &#9474;  
 &#9474; choose) another swap space. In some corner cases however, this can be     &#9474;  
 &#9474; what you want.                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Continue without a valid swap space? 
```
does it mean that if the usrspace's configuration file is active, and then i could suspend my laptop?,right? and how?
I choose "NO" to continue the installation. and it shows 
```
liceven@liceven-laptop:~$ sudo s2ram
sudo: s2ram: command not found
liceven@liceven-laptop:~$ sudo s2ram --force
sudo: s2ram: command not found
```
the same result with "YES"
so, what can i do?
thanks very much.

What is your /etc/uswsusp.conf like?

And I believe that there's no s2ram, but s2both, which does s2ram AND s2disk... it resumes from RAM but should your laptop runs out of juice and has no more power for RAM, it would resume from disk.

---

### Post by yexin218 on 2007-10-23
/etc/uswsusp.conf 
```
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform
```
/dev/hda5           12031       12161     1052226   82  Linux swap / Solaris
and if i modify the resume device =/dev/hda5 (my swap)
the command sudo s2ram works, but my laptop still doesn't supspend well, the error message like: couldn't find ..... i forgot.

---

### Post by thrillhouse on 2007-10-23
Suspend works wonderfully now after upgrading to Gusty.  Haven't tried hib yet.

---

### Post by Permafrost91 on 2007-10-23
yexin218 ... the fix comes from bbqsandwich's instructions as posted on page 11 of this thread, here's the link he supplied:
[http://ubuntuforums.org/showpost.php?p=3573566&postcount=12](http://ubuntuforums.org/showpost.php?p=3573566&postcount=12)

This worked for me (hibernation but not suspending works now)

---

### Post by alina.bolero on 2007-10-23
I too, found that when I upgraded to Gutsy, the s2ram and s2disk executables vanished, and I was left with just an s2both.

If I try to run s2both at the command line, my system ends up hanging on a black screen that just says:

```
s2both: Snapshotting system
```

it never does anything, and I have to do a hard restart.

What happened to s2ram/s2disk?  and/or how do I fix this?

-Alina

---

### Post by dashnak on 2007-10-23
Yeah, I'm having the exact same issue, and have been unable to fix it.

---

### Post by radovan01 on 2007-10-24
> **alina.bolero said:**
> I too, found that when I upgraded to Gutsy, the s2ram and s2disk executables vanished, and I was left with just an s2both.

If I try to run s2both at the command line, my system ends up hanging on a black screen that just says:

```
s2both: Snapshotting system
```

it never does anything, and I have to do a hard restart.

What happened to s2ram/s2disk?  and/or how do I fix this?

-Alina

the same problem here :( tried everything from this thread, but nothing helps

---

### Post by yogarock on 2007-10-26
when i do s2ram it works but when i press the power button, the screen doesnt turn on my computer:hp nx 7400

---

### Post by jackdaw28 on 2007-10-28
I've managed to get s2ram and s2disk back working on Gutsy following the tip here: [URL="https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238"][COLOR="Blue"]https://b
ugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238[/COLOR][/URL]
It is essential to have uswsusp installed from the Gutsy repository first.
I downloaded and installed the debian version from here: [[COLOR="Blue"]http://packages.debian.org/unstable/admin/uswsusp[/COLOR]]("http://packages.debian.org/unstable/admin/uswsusp")
I'm running 64 bit but I don't see why the i386 version should cause any problems.
When editing the scripts bear in mind that s2ram, s2disk and s2both are now in /usr/sbin and not /sbin.
I'm doing this on an Averatec 6230 with a SIS M760. "s2ram -f -a 3" works for me - I went through the list at [[COLOR="Blue"]http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box[/COLOR]]("http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box") 
one by one.

---

### Post by nate on 2007-10-29
> **samuraiche said:**
> Here I want to describe what i get when trying to suspend on kernel 2.6.22-14.
When I do suspend I get a black screen on my laptop then it just hangs...and neither keyboard nor mouse work. It seems that it suspends but not "fully"...leds on my laptop are still on..but as i said it becomes irresponible....

I have also tried to change in /etc/default/acpi-support SAVE_VBE_STATE and POST_VIDEO but still nothing :)

I get the same behavior after updating to Gutsy. If I try to hibernate, the screen goes black but still has power. The power and wireless light also stay on. Nothing can be done except using the power button to shut down and then boot.

I also tried installing uswsusp, but it doesn't work. I may try the newer debian version.

---

### Post by Ingenium on 2007-10-29
> **nate said:**
> I get the same behavior after updating to Gutsy. If I try to hibernate, the screen goes black but still has power. The power and wireless light also stay on. Nothing can be done except using the power button to shut down and then boot.

I also tried installing uswsusp, but it doesn't work. I may try the newer debian version.

I have the exact same problem. Screen goes black, but the power (and fan) is still on and it never enters suspend. I also tried the newer debian version and have the same problem.

---

### Post by snoopmoose on 2007-10-30
HI,

somehow i managed to overwrite my suspend-to-ram-script-backup
:)
could anyone help me. Got Gutsy Kubuntu on my Laptop.
cheers

---

### Post by Paul S on 2007-10-30
[HTML]somehow i managed to overwrite my suspend-to-ram-script-backup[/HTML]

You can reinstall via

```
aptitude reinstall hal
```

In gutsy, s2disk is called by /etc/acpi/hibernate.sh directly, so you shouldn't be changing /usr/lib/hal/scripts/* anymore.  Take a look at it.

I've been doing a lot of experimenting and conclude that all my problems with suspend / hibernate have to do with compiz.  I have stopped running compiz and now suspend works fine (gutsy).  If I enable compiz, then the resume failures start occuring.  I have an nvidia laptop card 7300 Go, and have tried all the different nvidia drivers.  driver version 9639 works better than 100.14.19 .. but still fails to resume after a few suspends with compiz.  I also found a bug on lauchpad regarding the ATI driver with gutsy .. it says the fglrx driver prevents suspend from working on gutsy's kernel .. it's an AMD/ATI bug and who knows when they'll fix it.

So, now I suspect that those of us having success and failure are more related to whether we are using desktop effects (compiz) and which video card you have.

regards,

---

### Post by EXCiD3 on 2007-10-30
This is terrible to think that an OS that has been under development for this amount of time still cannot suspend/hibernate properly. I LOVE Linux, don't get me wrong, but I feel that with the amount of laptop users here these problems should be worked out **before** release. It sucks that we are left behind in something that LOTS of people use. I am unable to get suspend/hibernate working too. It works on and off in Feisty, and Gutsy doesnt work worth a crap. I understand that this has to do with the graphics drivers however I feel that the Developers should have spent more time trying to fix this. Hopefully the Developers will be able to change this in Hardy Heron since it is an LTS release. For now I am forced to tweak Feisty for fast booting/shutdown in order to replace suspend/hibernate.

---

### Post by zorkerz on 2007-10-30
I don't mean to start a battle here but this is a free operating system as in bear and freedom. I find it pretty hard to complain about anything when its given to us for free.

Is there any other operating system that can claim to be free in as in beer and freedom and provide an experience anywhere similar to this. 

Personally I would lump the whole linux and bsd community into this statement because of the large amount of shared code between them. I don't know maybe Solaris comes close. Vista and Leopard are for sure not free and often don't provide as good of an experience.

I have a question also. How long does my computer need to hibernate before it is more energy efficient than suspending. Is there any way to get numbers on the energy use during suspension.

Thanks

---

### Post by EXCiD3 on 2007-10-30
Yes, you have a point. A free OS is like a free day at the amusement park - unlimited fun! I totally agree that because it is free it deserves some slack, however don't you feel that suspend/hibernate should be slightly more usable by now? Yes its extremely complicated, but if you are going to market your OS to laptop users this can be one of the deciding factors. I am glad Ubuntu is free, and it is by far my favorite distro, mostly because I've been using it so much without anything else.

As for your hibernate vs suspend question: Hibernate should techincally ALWAYS be more effecient. Suspend is always using power to keep the data in RAM alive. Hibernate saves that to your hdd (swap parition to be exact) and does not require ANY power afterwards. Suspend is probably more efficient/useful in the 5 mins or less category. You can continue MUCH faster than hibernation. Hibernation will use a little more power to copy to/from the data from RAM to/from the hdd, but this will be unnoticable as you hdd is always spinning anyways. In summary, there is not much difference whatsoever, just use suspend if its going to be a short time, hibernate for a longer time.

---

### Post by Paul S on 2007-10-30
> **EXCiD3 said:**
> Hopefully the Developers will be able to change this in Hardy Heron since it is an LTS release.

This goes back to the upstream (kernel) developers and their inability to break the Nvidia and AMD/ATI driver code.  There's a project to create an Nvidia driver which will be called "nouveau".  Also, AMD has hired developers from Novell to write an open source driver for their hardware.  I doubt that either of these will be working well enough to handle compiz with suspend / hibernate by the time of Hardy .. but maybe for the next release after.

> **EXCiD3 said:**
> For now I am forced to tweak Feisty for fast booting/shutdown in order to replace suspend/hibernate.

Did you try shutting off compiz .. as I said, that fixes all the suspend problems here.

I also wonder if it's possible to revise the sleep and resume scripts to shut off compiz before suspending and  then restart it after resuming.  Anyone know a script expert?

regards,

---

### Post by EXCiD3 on 2007-10-30
Yes, it does work but I hate having to shutdown compiz every time...if we could get a modified script that would be perfect! You could probably get that added to Hardy too.

---

### Post by Ingenium on 2007-10-30
> **Paul S said:**
> This goes back to the upstream (kernel) developers and their inability to break the Nvidia and AMD/ATI driver code.  There's a project to create an Nvidia driver which will be called "nouveau".  Also, AMD has hired developers from Novell to write an open source driver for their hardware.  I doubt that either of these will be working well enough to handle compiz with suspend / hibernate by the time of Hardy .. but maybe for the next release after.



Did you try shutting off compiz .. as I said, that fixes all the suspend problems here.

I also wonder if it's possible to revise the sleep and resume scripts to shut off compiz before suspending and  then restart it after resuming.  Anyone know a script expert?

regards,

Shutting down compiz doesn't help. I tried in single user mode as well and got the same effect. No matter what options I try with s2ram, the system just turns off the screen but never finishes suspending. Hibernate however works only if I manually run s2disk from the console. Running it in a script (as root) or using the hibernate option in GNOME both just hang the computer or cause it to try to hibernate but it aborts and goes back to my desktop with no error message. I'm really puzzled why it works if I manually type it in but won't work in a script. This is a fresh install of Ubuntu btw.

---

### Post by jw5801 on 2007-10-30
> **EXCiD3 said:**
> Yes, it does work but I hate having to shutdown compiz every time...if we could get a modified script that would be perfect! You could probably get that added to Hardy too.

It's open source! Add it yourself! All you'd need to do would be add "metacity --replace" to the start of the hibernate script, and then "compiz --replace" to the end of the resume script.

Besides I wouldn't single the Linux kernel out for the whole hibernate/suspend thing not working. It never worked for me in XP either, dunno about OSX but I doubt it. uswsusp actually worked properly in Feisty (dunno about Gutsy, uni classes have finished for the year so I haven't needed to hibernate and I'm too busy with exam study to set it up for the fun of it), so Linux is one up on the alternatives for the moment.

---

### Post by peabody on 2007-10-31
Hmm, me thinks perhaps that this might fix suspend for some people here, but it's a long road, requires building a custom kernel:

[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)
[https://help.ubuntu.com/community/Suspend2Kernel?action=show&redirect=Suspend2ForFeisty](https://help.ubuntu.com/community/Suspend2Kernel?action=show&redirect=Suspend2ForFeisty)

I might be willing to build this kernel for somebody, but it'll take time, and the resultant package is likely to be huge so I'd probably have to distribute it via BitTorrent.

---

### Post by tdrusk on 2007-11-03
uswsusp says I have an invalid swap partition. It did this in Debian too. Any idea?

---

### Post by jboehm on 2007-11-04
> **jackdaw28 said:**
> I've managed to get s2ram and s2disk back working on Gutsy following the tip here: [URL="https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238"][COLOR="Blue"]https://b
ugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238[/COLOR][/URL]
It is essential to have uswsusp installed from the Gutsy repository first.
I downloaded and installed the debian version from here: [[COLOR="Blue"]http://packages.debian.org/unstable/admin/uswsusp[/COLOR]]("http://packages.debian.org/unstable/admin/uswsusp")
I'm running 64 bit but I don't see why the i386 version should cause any problems.
When editing the scripts bear in mind that s2ram, s2disk and s2both are now in /usr/sbin and not /sbin.
I'm doing this on an Averatec 6230 with a SIS M760. "s2ram -f -a 3" works for me - I went through the list at [[COLOR="Blue"]http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box[/COLOR]]("http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box") 
one by one.

For the record, this method worked for me.  I have not had a suspend problem since implementing this.

My  /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux script looks like
------------------
#!/bin/sh

/usr/sbin/s2ram -f
------------------
You may have to play with some of the command line parameters as mentioned in the link of the above post.

---

### Post by tdrusk on 2007-11-06
This was the only workaround for my Acer Aspire 3680
[http://techaspect.net/2007/11/06/make-ubuntu-shutdown-when-lid-is-closed/](http://techaspect.net/2007/11/06/make-ubuntu-shutdown-when-lid-is-closed/)

---

### Post by Copter on 2007-11-10
Hi! 

Thanks for this howto. On my laptop default sleep method does not work properly. s2ram works like a charm. I just needed to add one script to wake up manually my cardbus DWL-650+ wlan card. I didnt want to modify system's default hibernatre / sleep / suspend scripts so i did it this way:

First off all my mashine is unknown to s2ram
```

copter@xidgex:~$ sudo s2ram -n
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "LG Electronics"
    sys_product  = "GS50-5FY"
    sys_version  = "Not Applicable"
    bios_version = "MDEMSF13"

```
so I have to use -f (force) argument. Here is my script.
```

copter@xidgex:~$ cat /sbin/ctrsleep 
#! /bin/bash

testEth0=$(ifconfig eth0 | grep "inet addr")
testWlan0=$(ifconfig wlan0 | grep "inet addr")

eth0State="off"
wlan0State="off"

# network state check
function checkState
{
    if [ -n "$testEth0" ];
        then
            eth0State="on"
    fi
    if [ -n "$testWlan0" ];
        then
            wlan0State="on"
    fi
}
#---------------------

checkState
ifdown eth0
ifdown wlan0

# suspend to ram and lock the screen
## xscreensaver-command -lock && s2ram -f
## kdesktop_lock --forcelock && s2ram -f
/etc/acpi/screenblank.sh && s2ram -f
sleep 5

# wake up network
killall dhclient3
if [ $eth0State == 'on' ];
    then
        ifdown eth0
        ifup eth0
fi
if [ $wlan0State == 'on' ];
    then
        pccardctl eject
        sleep 1
        pccardctl insert 
        ifdown wlan0
        ifup wlan0
fi

```
Added also this line to sudoers
```

copter@xidgex:~$ sudo cat /etc/sudoers 
Password:
## CUT

copter xidgex = NOPASSWD: /sbin/ctrsleep

## CUT

```
Than added activator to my XFCE desktop with command
```

sudo /sbin/ctrsleep

```
Now it works just fine. Thanks for help!

[COLOR="Red"]**EDIT**[/COLOR]: done on Xubuntu 7.04 Feisty Fawn, 2.6.20-16-generic
[COLOR="Red"]**EDIT2**[/COLOR]: xscreensaver-command -lock didnt work properly. fixed

copter :]

---

### Post by Paul S on 2007-11-20
Since upgrading to gutsy, I've been having problems with resume not working.  After a lot of trial and error, I find that using "Alt-F2" to enter the command "sudo pmi action suspend" works all the time for me.  If your still having trouble, give it a try.

HTH

---

### Post by Human2.0 on 2007-11-21
Will this fix make Ubuntu darken the screen and put it into standby when I close the screen? Right now the screen stays on, which is not so great for the battery life. If there's another thread for this problem, please direct me there, cause i can't find it.

---

### Post by zorkerz on 2007-11-21
for gnome go to system->preference->power management
You can set the behavior for when your lid closes. This assumes your standby already works if not you could try some of the things mentioned here.
cheers

---

### Post by MozartlovesUbun2 on 2007-11-26
> **peabody said:**
> Hmm, me thinks perhaps that this might fix suspend for some people here, but it's a long road, requires building a custom kernel:

[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)
[https://help.ubuntu.com/community/Suspend2Kernel?action=show&redirect=Suspend2ForFeisty](https://help.ubuntu.com/community/Suspend2Kernel?action=show&redirect=Suspend2ForFeisty)

I might be willing to build this kernel for somebody, but it'll take time, and the resultant package is likely to be huge so I'd probably have to distribute it via BitTorrent.

would it work for a Dell Inspiron ATI X1400 / Gutsy?

I opened a thread at:
[http://ubuntuforums.org/showthread.php?p=3840722#post3840722](http://ubuntuforums.org/showthread.php?p=3840722#post3840722)

the guy at:
[http://www.mylittleubuntuguide.com/](http://www.mylittleubuntuguide.com/)

seems to be working on it (release fixed ISO soon)

---

### Post by InfinityCircuit on 2007-12-02
This is confirmed to work in Hardy Heron Tribe 1 on a Thinkpad X40 after /etc/uswsusp.conf is edited to use /dev/sda3 instead of the UUID system.

---

### Post by ukripper on 2007-12-04
> **InfinityCircuit said:**
> This is confirmed to work in Hardy Heron Tribe 1 on a Thinkpad X40 after /etc/uswsusp.conf is edited to use 

Interesting!

---

### Post by victorgreen on 2007-12-07
~$ sudo apt-get install uswsusp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
uswsusp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~$ sudo s2ram --force
sudo: s2ram: command not found


Grr it refuses to recognize the commands. gutsy 32, x61, 1gb swap, 2gb ram

---

### Post by nekr0z on 2007-12-08
Same here: s2disk command is available, s2ram is not.

---

### Post by InfinityCircuit on 2007-12-08
I was actually a bit off in my previous post.  This is actually how I got it working on my Thinkpad X40:

1) Two preliminary steps are necessary:
a. add the following to the device section of /etc/X11/xorg.conf:
```
Option          "VBERestore"           "true"
```

b. uncomment the line about saving the PCI video state in /etc/default/acpi-support

2) install uswsusp and edit /etc/uswsusp.conf to use the /dev/sda3 instead of UUID system.

3) Use s2both to suspend the computer and s2disk to hibernate.  You can fix hal by using the changes in the original post.

---

### Post by Farenheit on 2007-12-09
bash: s2ram: command not found

---

### Post by InfinityCircuit on 2007-12-09
> **Farenheit said:**
> bash: s2ram: command not found

That's why you use s2both instead.  Maybe someone should make a symlink in the package from s2ram to s2both.

---

### Post by nekr0z on 2007-12-09
Using s2both for me resulted in suspending to disk, not to ram.

---

### Post by mperry on 2007-12-10
I just installed the uswsusp from Debian Lenny which does have the s2ram package and changed the hal scripts.  I noticed that the s2both script produces the same result.  It snapshots the system but then hibernates it.  I don't think making a symbolic link would work.  We need a uswsusp package with s2ram in iit unless there are other switches that change things.

BTW, I just tried this on my thinkpad t40 which has the basic problem of not coming out of suspends reliably.  I added in the changes to /etc/X11/xorg.conf and /etc/default/acpi-support as well.  

I have noticed a rather interesting pattern to the laptop not waking up.  It seems that the longer suspends seem to cause the problem at a replicable rate.  Anyone else tried all these on a "T" model thinkpad.

---

### Post by zeekoe on 2007-12-13
For me, it worked using uswsusp right after updating to Gutsy. Now it's gone again. What I did to fix it:

* Did what was described here:
[http://knowledge76.com/index.php/Suspend_and_Hibernate](http://knowledge76.com/index.php/Suspend_and_Hibernate)
* Did some basic tests from here:
[http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt](http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt)
The reboot/disk test showed directly that mysql was a problem. I disabled mysql, did some tests again, and it worked fine! This is now my custom hibernate script:
#!/bin/bash
/etc/init.d/mysql stop
echo platform >/sys/power/disk
echo disk >/sys/power/state
/etc/init.d/mysql start

Don't think this is using swsusp, but it works... who cares :)
By the way, the Menu -> Shutdown -> Hibernate thing does still not work; it blanks the screen for a few minutes and then just returns.

---

### Post by msdark on 2007-12-29
(sorry for me english, but i don'ts speak that very well.. i speak spanish)

i try this in a laptop packard bell easynote mx36-u-2080

I'm running compiz fusion with the latest fglrx driver of ati propieatry, with a intel core duo 1.73ghz and 1gb ram... on ubuntu gutsy

when i try... it seems like to the resume image is done.. but when i reboot the sistem (s2disk) the screen freeze and i only see a message like that:

resume: Image loadding succesfull.

But the sistem don't start...
What can i do???

other thing the command s2ram doesn't exists... i see only a s2disk and s2both... i supose s2both = s2ram ...

---

### Post by chiefmanyrabbitguteat on 2008-01-22
For me, the fix worked only when I entered the command: ```
 s2ram --force 
``` from the terminal.  To fix this, I had to do the following:


```
sudo aptitude install uswsusp
```

After that, I pulled the 0.7 version off of 

[http://packages.debian.org/sid/i386/uswsusp/download](http://packages.debian.org/sid/i386/uswsusp/download)

and installed it.  I don't know if it is necessary to install the one from the Ubuntu repos, but that's how I did it.

Test it out:  Use
```
sudo s2ram --force
```

If that works, back up the following file:
```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak

```

Then, edit the original:
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

```

Replace all of the text with the following:
```

#!/bin/sh

/usr/sbin/s2ram --force

```


Now, it works like a charm!

P.S.  Sometimes I get a white screen after I suspend,  and all I need to do is enter my password and hit enter.

---

### Post by beercz on 2008-02-06
> **chiefmanyrabbitguteat said:**
> For me, the fix worked only when I entered the command: ```
 s2ram --force 
``` from the terminal.  To fix this, I had to do the following:


```
sudo aptitude install uswsusp
```After that, I pulled the 0.7 version off of 

[http://packages.debian.org/sid/i386/uswsusp/download](http://packages.debian.org/sid/i386/uswsusp/download)

and installed it.  I don't know if it is necessary to install the one from the Ubuntu repos, but that's how I did it.

Test it out:  Use
```
sudo s2ram --force
```If that works, back up the following file:
```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak

```Then, edit the original:
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

```Replace all of the text with the following:
```

#!/bin/sh

/usr/sbin/s2ram --force

```
Now, it works like a charm!

P.S.  Sometimes I get a white screen after I suspend,  and all I need to do is enter my password and hit enter.
Thanks chiefmanyrabbitguteat

Suspend works OK now on my HP Compaq nx7400 laptop.

Anyone been able to get hibernate to work as well?

---

### Post by Permafrost91 on 2008-02-06
both hibernate and suspend now work on my IBM X60

---

### Post by gobucks on 2008-02-17
On a Dell Inspiron 5160, I've managed to get s2both working properly from the command line using sudo s2both, which was a huge ordeal.  However, pressing the Fn-Esc (Suspend) does nothing at all.  After running "xev", no events are reported for this key event.  All of the other Fn keys report events.  Furthermore, pressing the power button does nothing as well.  Performing the suspend or hibernate from the Gnome menu appear t suspend and hibernate, but when powered on again, they screen is blank but the system appears to be running.

Does anyone know how to enable these events?

Running Gutsy, kernel version 2.6.22-14-generic.

Thanks!

---

### Post by warpjavier on 2008-02-21
Hi,
I have a compaq Evo n610c and I managed to get suspend to ram working. Not using s2ram.
I added to grub kernel line "acpi=off".
It just work pressing the suspend button, not with the suspend icon. Also hibernation does not work anymore. Maybe somebody with the same laptop can fix the hibernation and suspend with the icons.

warpjavier

PS.
Does anybody knows what script is executed when I press the suspend button and I have ACPI deactivaded?

thanks

---

### Post by gobucks on 2008-02-23
My suspicions were correct.  The problem is not Ubuntu, it is the BIOS.  It does not properly report all ACPI messages.  I found this link where they discussed how to patch it on the fly:

[http://bugzilla.kernel.org/show_bug.cgi?id=1752#c103](http://bugzilla.kernel.org/show_bug.cgi?id=1752#c103)

This made my power and suspend button start working, but after suspending, the resume does not work.  The system powers up again, but gets stuck before X starts.

Any recommendations?

---

### Post by gobucks on 2008-02-23
> **gobucks said:**
> My suspicions were correct.  The problem is not Ubuntu, it is the BIOS.  It does not properly report all ACPI messages.  I found this link where they discussed how to patch it on the fly:

[http://bugzilla.kernel.org/show_bug.cgi?id=1752#c103](http://bugzilla.kernel.org/show_bug.cgi?id=1752#c103)

This made my power and suspend button start working, but after suspending, the resume does not work.  The system powers up again, but gets stuck before X starts.

Any recommendations?

I got suspend working properly.  After following the above steps in the link, then the instructions in this link:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend?highlight=%28CategoryDocumentation%29](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend?highlight=%28CategoryDocumentation%29)

everything works fine.  Hope this helps someone else.

---

### Post by madmatrixz3000 on 2008-04-02
I get a weird message ```
s2disk: Could not stat the resume device file. Reason: No such file or directory
```

---

### Post by madmatrixz3000 on 2008-04-02
I figured out that this problem has to do with me having shrunk my swap file to almost nothing, so now it does not recogize the fact that I reset the swap size to 1.5Gb.  How do I set up my ubuntu to see my swap file.

---

### Post by mlapaglia on 2008-04-02
thanks for this fix!

when i was installing it told me my swap wasn't formatted correctly, and i selected "no" (i think this is because my swap is never used, i have 2gb of ram, but my swap max size is 3.83 gb)

my sound works also, after a standby.
thanks!

---

### Post by madmatrixz3000 on 2008-04-02
Fixed my swap file: [http://ubuntuforums.org/showthread.php?p=4639273#post4639273](http://ubuntuforums.org/showthread.php?p=4639273#post4639273)

I am reinstalling the uswsusp now how do I config it?

---

### Post by altonbr on 2008-06-28
s2ram is no longer in uswsusp in Hardy. You may want to update your tutorial.

---

### Post by smuggler on 2008-07-11
[https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238/comments/12](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238/comments/12)
so you can try powersave instead of s2ram

---

### Post by Deadalus on 2008-07-12
How can I make this work in hardy heron. Tried to follow the guide. Got the s2disk to work, but I can't get is to work default. I have searched the web and can't find anything on this issue on hardy heron.

---

### Post by gabbuntu on 2008-07-19
After I upgraded to Hardy from Feisty, my hibernate was fine after a few tweaks to my ACPI scripts but I was having trouble fixing the well-known problem of a white screen after resume from suspend. So I tried the uswsusp path and both s2disk and s2both seem to work fine on mine. Thanks to all you folks!!

---

### Post by antirem on 2008-07-19
Much thanks and appreciations!

---

### Post by pcolamar on 2008-07-19
> **madmatrixz3000 said:**
> I get a weird message ```
s2disk: Could not stat the resume device file. Reason: No such file or directory
```

I got the same msg but my swap is bigger than my RAM

laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075608    1587272     488336          0     195664     720468
-/+ buffers/cache:     671140    1404468
Swap:      2128572          0    2128572

Any idea ?

Palmer

PS -  s2ram is working though

---

### Post by ikkus42 on 2008-07-23
> **pcolamar said:**
> I got the same msg but my swap is bigger than my RAM

laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075608    1587272     488336          0     195664     720468
-/+ buffers/cache:     671140    1404468
Swap:      2128572          0    2128572

Any idea ?

Palmer

PS -  s2ram is working though

I had the same problem:  Even though I had enough swap, I got this:
```
s2disk: Could not stat the resume device file. Reason: No such file or directory
```
I fixed it by running this:
```
sudo dpkg-reconfigure uswsusp
```
I accepted all the defaults and it worked.  I suspect that it was a problem with the value of "resume device", which the util changed to "/dev/sda5" for me.  

PS I found this in the man page of uswsusp.conf which i found in the man page of s2disk.  It might be helpful to make this util or file more obvious to newbies like me.

Cheers!

---

### Post by pcolamar on 2008-07-26
ikkus42, no luck.
I tried your suggestion but still the "stat" problem comes back.

On the otherside , googleing about the uswsusp, I have learnt that pm-hibernate use the s2disk  an strage enough using pm-hibernate I succeed in hibernating but the resume does not work, my screen remains in text mode.

Ok , step by step !

I will follow the pm-hibernate path now.

Thanks

Palmer

---

### Post by PadreSol on 2008-07-30
I switched from metacity (broken focus and other annoying stuff) and started using fvwm-crystal but I can't figure out how to make suspend work.  Tried pm-suspend but and it suspends.  When I try to resume everything comes back (I can see the disk activity) but no graphics.  So I have to reboot.  Anyone know how to make suspend work again?  What does metacity do differently?

---

### Post by itmanvn on 2008-08-27
using sony vaio fz320e, tried many stuff with no luck, can not suspend or hibernate @@

---

### Post by gsuveg on 2008-09-01
someone know a solution for suspend nx7400 on hardy ? sometime its dont come back after supsend, i need power-off

---

### Post by NoSmokingBandit on 2008-09-10
i followed the instructions to the letter but when i run "s2ram" or "s2disk" it tells me the command is unrecognized...?

---

### Post by Duranxl on 2008-09-13
NVM!! 1st time i tried S2disk it hung on shutdown..but 2nd try and now it works!
I can't believe i have a working hibernation on ubuntu!!

---

### Post by flymw on 2008-10-19
Hello all, this is how I got it to work on my system. Hope that helps and looking forward to feedback!

My system: Sony Vaio VGN-TZ21VN and Ubuntu 8.04 Hardy

With me this is not an error of Ubuntu but as far as I understand a stupidity of the computer manufacturer (Sony with me) using a slacky Microsoft compiler for the power management implementation in the BIOS.

So all we have to do is recompile the DSDT-tables and correct any errors in them. Sounds complicated? It's not necessarily too difficult. At least it wasn't on my system. Just have a look at my “ez” tutorial...

For a good english tutorial and information on what to do if you have errors recompiling your DSDT you can have a look here: [http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html#post1819135](http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html#post1819135)

I used the following tutorial (GERMAN! but there are also some useful links in English on that site), all information given here originates from that site, thanks for the helpful wiki: [http://wiki.ubuntuusers.de/acpi-fix](http://wiki.ubuntuusers.de/acpi-fix) 

Just copy and paste the following commands in the Terminal:

```
sudo apt-get install iasl
sudo cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
iasl -sa dsdt.dsl
```	

(This step is the recompilation of the file, if you have any errors here, please refer to the internet. That's where things might get difficult since you need to change code to repair the errors. With me it had no errors but just automatically did some improvements and I guess that's all that was necessary. Otherwise have a look at the links above for more detailed tutorials)

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
```

(Caution: Up to now you did no changes to your system. The next step will activate the changes in your system.)

```
sudo update-initramfs -u
```

Reboot your system and everything should be OK. Thumbs up!

[I](If you should have any problems with the new DSDT you can probably undo the changes to the system by the following command:

```
sudo rm /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u
```
but this is just a guess of my own and I have not yet tested this...)[/I]

---

### Post by rathel on 2008-11-02
> **flymw said:**
> Hello all, this is how I got it to work on my system. Hope that helps and looking forward to feedback!

My system: Sony Vaio VGN-TZ21VN and Ubuntu 8.04 Hardy

With me this is not an error of Ubuntu but as far as I understand a stupidity of the computer manufacturer (Sony with me) using a slacky Microsoft compiler for the power management implementation in the BIOS.

So all we have to do is recompile the DSDT-tables and correct any errors in them. Sounds complicated? It's not necessarily too difficult. At least it wasn't on my system. Just have a look at my “ez” tutorial...

For a good english tutorial and information on what to do if you have errors recompiling your DSDT you can have a look here: [http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html#post1819135](http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html#post1819135)

I used the following tutorial (GERMAN! but there are also some useful links in English on that site), all information given here originates from that site, thanks for the helpful wiki: [http://wiki.ubuntuusers.de/acpi-fix](http://wiki.ubuntuusers.de/acpi-fix) 

Just copy and paste the following commands in the Terminal:

```
sudo apt-get install iasl
sudo cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
iasl -sa dsdt.dsl
```	

(This step is the recompilation of the file, if you have any errors here, please refer to the internet. That's where things might get difficult since you need to change code to repair the errors. With me it had no errors but just automatically did some improvements and I guess that's all that was necessary. Otherwise have a look at the links above for more detailed tutorials)

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
```

(Caution: Up to now you did no changes to your system. The next step will activate the changes in your system.)

```
sudo update-initramfs -u
```

Reboot your system and everything should be OK. Thumbs up!

[I](If you should have any problems with the new DSDT you can probably undo the changes to the system by the following command:

```
sudo rm /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u
```
but this is just a guess of my own and I have not yet tested this...)[/I]

Sadly this does NOT work with Sony Vaio PCG-K23. :(

---

### Post by m10 on 2008-11-07
i tried to fix my dsdt with no avail:

here is my dsdt.dsl:
```
/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20061109
 *
 * Disassembly of dsdt.dat, Fri Nov  7 17:55:02 2008
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x00006979 (27001)
 *     Revision         0x02
 *     OEM ID           "Sony"
 *     OEM Table ID     "VAIO"
 *     OEM Revision     0x20071221 (537334305)
 *     Creator ID       "PTL "
 *     Creator Revision 0x20050624 (537200164)
 */
DefinitionBlock ("dsdt.aml", "DSDT", 2, "Sony", "VAIO", 0x20071221)
{
    External (PDC1)
    External (PDC0)
    External (CFGD)
    External (^CPU0._PPC)

    OperationRegion (SMI0, SystemMemory, 0x7FEE2B38, 0x00000415)
    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
        BCMD,   8, 
        DID,    32, 
        INFO,   4096
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INFB,   8
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INFD,   32
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INDD,   64
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        SXBF,   8320
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INF1,   8, 
        INF2,   8
    }

    OperationRegion (SMI1, SystemIO, 0x0000FE00, 0x00000002)
    Field (SMI1, AnyAcc, NoLock, Preserve)
    {
        SMIC,   8
    }

    Mutex (MPHS, 0x00)
    Method (PHS0, 1, NotSerialized)
    {
        Store (Arg0, BCMD)
        Store (Zero, SMIC)
        While (LEqual (BCMD, Arg0)) {}
        Store (Zero, BCMD)
    }

    Method (PHS, 1, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Zero, DID)
        PHS0 (Arg0)
        Store (INFD, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHSD, 2, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Zero, DID)
        Store (Arg1, INFD)
        PHS0 (Arg0)
        Store (INFD, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHDD, 2, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Zero, DID)
        Store (Arg1, INDD)
        PHS0 (Arg0)
        Store (INDD, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHSW, 3, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Zero, DID)
        Store (Arg1, INF1)
        Store (Arg2, INF2)
        PHS0 (Arg0)
        Store (INFB, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHSB, 2, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Zero, DID)
        Store (Arg1, INFB)
        PHS0 (Arg0)
        Store (INFB, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Mutex (MUTX, 0x00)
    OperationRegion (PRT0, SystemIO, 0x80, 0x04)
    Field (PRT0, DWordAcc, Lock, Preserve)
    {
        P80H,   32
    }

    Method (P8XH, 2, Serialized)
    {
        If (LEqual (Arg0, Zero))
        {
            Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
        }

        If (LEqual (Arg0, One))
        {
            Store (Or (And (P80D, 0xFFFF00FF), ShiftLeft (Arg1, 0x08)
                ), P80D)
        }

        If (LEqual (Arg0, 0x02))
        {
            Store (Or (And (P80D, 0xFF00FFFF), ShiftLeft (Arg1, 0x10)
                ), P80D)
        }

        If (LEqual (Arg0, 0x03))
        {
            Store (Or (And (P80D, 0x00FFFFFF), ShiftLeft (Arg1, 0x18)
                ), P80D)
        }

        Store (P80D, P80H)
    }

    Method (_PIC, 1, NotSerialized)
    {
        Store (Arg0, GPIC)
    }

    Method (_PTS, 1, NotSerialized)
    {
        Add (Arg0, 0x4D, Local0)
        DBGC (Local0, 0x80, BCEN)
        Store (Zero, P80D)
        P8XH (Zero, Arg0)
        Store (Arg0, PRM0)
        Store (0x51, SMIF)
        Store (Zero, TRP0)
        TRAP (0x50)
        Add (Arg0, 0x4D, Local0)
        DBGC (Local0, 0x81, BCEN)
    }

    Method (_WAK, 1, NotSerialized)
    {
        Or (Arg0, 0x50, Local0)
        DBGC (Local0, 0x80, BCEN)
        P8XH (One, 0xAB)
        Store (Arg0, PRM0)
        Store (0x52, SMIF)
        Store (Zero, TRP0)
        If (LOr (LEqual (Arg0, 0x03), LEqual (Arg0, 0x04)))
        {
            If (And (CFGD, 0x01000000))
            {
                If (LAnd (And (CFGD, 0xF0), LEqual (OSYS, 0x07D1)))
                {
                    TRAP (0x3D)
                }
            }
        }

        If (LEqual (RP1D, Zero))
        {
            Notify (\_SB.PCI0.RP01, Zero)
        }

        If (LEqual (RP2D, Zero))
        {
            Notify (\_SB.PCI0.RP02, Zero)
        }

        If (LEqual (RP3D, Zero))
        {
            Notify (\_SB.PCI0.RP03, Zero)
        }

        If (LEqual (RP5D, Zero))
        {
            Notify (\_SB.PCI0.RP05, Zero)
        }

        If (LEqual (Arg0, 0x03))
        {
            If (LEqual (Zero, ACTT)) {}
        }

        If (_OSI ("Windows 2006"))
        {
            Store (DETC, Local0)
            PHSB (0xE1, Local0)
        }

        Store (\_SB.PCI0.LPCB.EC.RPWR, PWRS)
        Store (\_SB.PCI0.LPCB.EC.RSCL, B0SC)
        Store (\_SB.PCI0.LPCB.EC.BATP, BNUM)
        Notify (\_SB.BAT0, 0x80)
        Notify (\_SB.BAT0, 0x81)
        If (LEqual (Arg0, 0x04))
        {
            Store (CM72, Local0)
            Store (Zero, CM72)
            If (LNotEqual (And (Local0, 0x84, Local0), 0x84))
            {
                Notify (\_SB.PWRB, 0x02)
            }
        }
        Else
        {
            If (And (PMST, One))
            {
                Notify (\_SB.PWRB, 0x02)
            }
        }

        \_PR.RPPC ()
        P8XH (Zero, 0xCD)
        Or (Arg0, 0x50, Local0)
        DBGC (Local0, 0x81, BCEN)
        Return (Package (0x02)
        {
            Zero, 
            Zero
        })
    }

    Method (GETB, 3, Serialized)
    {
        Multiply (Arg0, 0x08, Local0)
        Multiply (Arg1, 0x08, Local1)
        CreateField (Arg2, Local0, Local1, TBF3)
        Return (TBF3)
    }

    Method (PNOT, 0, Serialized)
    {
        If (MPEN)
        {
            If (And (PDC0, 0x08))
            {
                Notify (\_PR.CPU0, 0x80)
                If (And (PDC0, 0x10))
                {
                    Sleep (0x64)
                    Notify (\_PR.CPU0, 0x81)
                }
            }

            If (And (PDC1, 0x08))
            {
                Notify (\_PR.CPU1, 0x80)
                If (And (PDC1, 0x10))
                {
                    Sleep (0x64)
                    Notify (\_PR.CPU1, 0x81)
                }
            }
        }
        Else
        {
            Notify (\_PR.CPU0, 0x80)
            Sleep (0x64)
            Notify (\_PR.CPU0, 0x81)
        }
    }

    Method (TRAP, 1, Serialized)
    {
        Store (Arg0, SMIF)
        Store (Zero, TRP0)
        Return (SMIF)
    }

    Scope (_SB)
    {
        Method (_INI, 0, NotSerialized)
        {
            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (One, LINX)
                }

                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }

            If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
            {
                TRAP (0x3D)
            }

            TRAP (0x2B)
            TRAP (0x32)
        }
    }

    OperationRegion (GNVS, SystemMemory, 0x7FEE2A37, 0x0100)
    Field (GNVS, AnyAcc, Lock, Preserve)
    {
        OSYS,   16, 
        SMIF,   8, 
        PRM0,   8, 
        PRM1,   8, 
        SCIF,   8, 
        PRM2,   16, 
        LCKF,   8, 
        PRM4,   16, 
        P80D,   32, 
        LIDS,   8, 
        PWRS,   8, 
        DBGS,   8, 
        LINX,   8, 
                Offset (0x14), 
        ACT1,   8, 
        ACTT,   8, 
        PSVT,   8, 
        TC1V,   8, 
        TC2V,   8, 
        TSPV,   8, 
        CRTT,   8, 
        DTSE,   8, 
        DTS1,   8, 
        DTS2,   8, 
        BNUM,   8, 
        B0SC,   8, 
        B1SC,   8, 
        B2SC,   8, 
        B0SS,   8, 
        B1SS,   8, 
        B2SS,   8, 
        LBST,   8, 
        TBST,   8, 
                Offset (0x28), 
        APIC,   8, 
        MPEN,   8, 
        PCP0,   8, 
        PCP1,   8, 
        PPCM,   8, 
                Offset (0x32), 
                Offset (0x3C), 
        IGDS,   8, 
        TLST,   8, 
        CADL,   8, 
        PADL,   8, 
        CSTE,   16, 
        NSTE,   16, 
        SSTE,   16, 
        NDID,   8, 
        DID1,   32, 
        DID2,   32, 
        DID3,   32, 
        DID4,   32, 
        DID5,   32, 
                Offset (0x64), 
        PNID,   8, 
                Offset (0x67), 
        BLCS,   8, 
        BRTL,   8, 
        ALSE,   8, 
        ALAF,   8, 
        LLOW,   8, 
        LHIH,   8, 
                Offset (0x6E), 
        EMAE,   8, 
        EMAP,   16, 
        EMAL,   16, 
                Offset (0x74), 
        MEFE,   8, 
                Offset (0x78), 
        TPMP,   8, 
        TPME,   8, 
                Offset (0x82), 
        GTF0,   112, 
        IDEM,   8, 
                Offset (0x96), 
        SYID,   8, 
        BCEN,   8, 
                Offset (0xAA), 
        ASLB,   32, 
        IBTT,   8, 
        IPAT,   8, 
        ITVF,   8, 
        ITVM,   8, 
        IPSC,   8, 
        IBLC,   8, 
        IBIA,   8, 
        ISSC,   8, 
        I409,   8, 
        I509,   8, 
        I609,   8, 
        I709,   8, 
        IDMM,   8, 
        IDMS,   8, 
        IF1E,   8, 
        HVCO,   8, 
        NXD1,   32, 
        NXD2,   32, 
        NXD3,   32, 
        NXD4,   32, 
        NXD5,   32, 
        NXD6,   32, 
        NXD7,   32, 
        NXD8,   32
    }

    Name (DSEN, One)
    Name (ECON, Zero)
    Name (GPIC, Zero)
    Name (CTYP, Zero)
    Name (L01C, Zero)
    Name (VFN0, Zero)
    Name (VFN1, Zero)
    Name (AODV, Zero)
    Name (CADD, Zero)
    Name (PADD, Zero)
    Scope (_GPE)
    {
        Method (_L01, 0, NotSerialized)
        {
            Add (L01C, One, L01C)
            P8XH (Zero, One)
            P8XH (One, L01C)
            If (LAnd (LEqual (RP1D, Zero), \_SB.PCI0.RP01.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP01.PDCX)
                {
                    Store (One, \_SB.PCI0.RP01.PDCX)
                    Store (One, \_SB.PCI0.RP01.HPSX)
                    Notify (\_SB.PCI0.RP01, Zero)
                }
                Else
                {
                    Store (One, \_SB.PCI0.RP01.HPSX)
                }
            }

            If (LAnd (LEqual (RP2D, Zero), \_SB.PCI0.RP02.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP02.PDCX)
                {
                    Store (One, \_SB.PCI0.RP02.PDCX)
                    Store (One, \_SB.PCI0.RP02.HPSX)
                    Notify (\_SB.PCI0.RP02, Zero)
                }
                Else
                {
                    Store (One, \_SB.PCI0.RP02.HPSX)
                }
            }

            If (LAnd (LEqual (RP3D, Zero), \_SB.PCI0.RP03.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP03.PDCX)
                {
                    Store (One, \_SB.PCI0.RP03.PDCX)
                    Store (One, \_SB.PCI0.RP03.HPSX)
                    Notify (\_SB.PCI0.RP03, Zero)
                }
                Else
                {
                    Store (One, \_SB.PCI0.RP03.HPSX)
                }
            }

            If (LAnd (LEqual (RP5D, Zero), \_SB.PCI0.RP05.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP05.PDCX)
                {
                    Store (One, \_SB.PCI0.RP05.PDCX)
                    Store (One, \_SB.PCI0.RP05.HPSX)
                    Notify (\_SB.PCI0.RP05, Zero)
                }
                Else
                {
                    Store (One, \_SB.PCI0.RP05.HPSX)
                }
            }
        }

        Method (_L02, 0, NotSerialized)
        {
            Store (Zero, GPEC)
        }

        Method (_L03, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB1, 0x02)
        }

        Method (_L04, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB2, 0x02)
        }

        Method (_L05, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB5, 0x02)
        }

        Method (_L06, 0, NotSerialized)
        {
            If (\_SB.PCI0.GFX0.GSSE)
            {
                \_SB.PCI0.GFX0.GSCI ()
            }
            Else
            {
                Store (One, SCIS)
            }
        }

        Method (_L09, 0, NotSerialized)
        {
            If (\_SB.PCI0.RP01.PSPX)
            {
                Store (One, \_SB.PCI0.RP01.PSPX)
                Store (One, \_SB.PCI0.RP01.PMSX)
                Notify (\_SB.PCI0.RP01, 0x02)
            }

            If (\_SB.PCI0.RP02.PSPX)
            {
                Store (One, \_SB.PCI0.RP02.PSPX)
                Store (One, \_SB.PCI0.RP02.PMSX)
                Notify (\_SB.PCI0.RP02, 0x02)
            }

            If (\_SB.PCI0.RP03.PSPX)
            {
                Store (One, \_SB.PCI0.RP03.PSPX)
                Store (One, \_SB.PCI0.RP03.PMSX)
                Notify (\_SB.PCI0.RP03, 0x02)
            }

            If (\_SB.PCI0.RP05.PSPX)
            {
                Store (One, \_SB.PCI0.RP05.PSPX)
                Store (One, \_SB.PCI0.RP05.PMSX)
                Notify (\_SB.PCI0.RP05, 0x02)
            }
        }

        Method (_L0B, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.PCIB, 0x02)
        }

        Method (_L0C, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB3, 0x02)
        }

        Method (_L0D, 0, NotSerialized)
        {
            If (\_SB.PCI0.EHC1.PMES)
            {
                Store (One, \_SB.PCI0.EHC1.PMES)
                Notify (\_SB.PCI0.EHC1, 0x02)
            }

            If (\_SB.PCI0.EHC2.PMES)
            {
                Store (One, \_SB.PCI0.EHC2.PMES)
                Notify (\_SB.PCI0.EHC2, 0x02)
            }

            If (\_SB.PCI0.HDEF.PMES)
            {
                Store (One, \_SB.PCI0.HDEF.PMES)
                Notify (\_SB.PCI0.HDEF, 0x02)
            }
        }

        Method (_L0E, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB4, 0x02)
        }

        Method (_L1E, 0, NotSerialized)
        {
            Notify (\_SB.PWRB, 0x02)
        }
    }

    Scope (_PR)
    {
        Processor (CPU0, 0x00, 0x00001010, 0x06) {}
        Processor (CPU1, 0x01, 0x00001010, 0x06) {}
        Method (RPPC, 0, NotSerialized)
        {
            If (LEqual (OSYS, 0x07D2))
            {
                If (And (CFGD, One))
                {
                    If (LGreater (^CPU0._PPC, Zero))
                    {
                        Subtract (^CPU0._PPC, One, ^CPU0._PPC)
                        PNOT ()
                        Add (^CPU0._PPC, One, ^CPU0._PPC)
                        PNOT ()
                    }
                    Else
                    {
                        Add (^CPU0._PPC, One, ^CPU0._PPC)
                        PNOT ()
                        Subtract (^CPU0._PPC, One, ^CPU0._PPC)
                        PNOT ()
                    }
                }
            }
        }
    }

    Scope (_TZ)
    {
        ThermalZone (TZ00)
        {
            Method (_CRT, 0, Serialized)
            {
                Return (0x0FA2)
            }

            Method (_TMP, 0, Serialized)
            {
                If (ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC.TS1R, Local0)
                    If (And (Local0, 0x80))
                    {
                        Subtract (Local0, 0x0100, Local0)
                    }

                    Return (Add (0x0AAC, Multiply (Local0, 0x0A)))
                }

                Return (0x0BB8)
            }
        }

        ThermalZone (TZ01)
        {
            Method (_AC0, 0, Serialized)
            {
                Return (Add (0x0AAC, Multiply (ACTT, 0x0A)))
            }

            Method (_AC1, 0, Serialized)
            {
                Return (Add (0x0AAC, Multiply (ACT1, 0x0A)))
            }

            Method (_CRT, 0, Serialized)
            {
                Return (Add (0x0AAC, Multiply (CRTT, 0x0A)))
            }

            Method (_SCP, 1, Serialized)
            {
                Store (Arg0, CTYP)
            }

            Method (_TMP, 0, Serialized)
            {
                If (DTSE)
                {
                    If (LGreaterEqual (DTS1, DTS2))
                    {
                        Return (Add (0x0AAC, Multiply (DTS1, 0x0A)))
                    }

                    Return (Add (0x0AAC, Multiply (DTS2, 0x0A)))
                }

                If (ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC.TS1R, Local0)
                    If (And (Local0, 0x80))
                    {
                        Subtract (Local0, 0x0100, Local0)
                    }

                    Return (Add (0x0AAC, Multiply (Local0, 0x0A)))
                }

                Return (0x0BB8)
            }

            Method (_PSL, 0, Serialized)
            {
                If (MPEN)
                {
                    Return (Package (0x02)
                    {
                        \_PR.CPU0, 
                        \_PR.CPU1
                    })
                }

                Return (Package (0x01)
                {
                    \_PR.CPU0
                })
            }

            Method (_PSV, 0, Serialized)
            {
                Return (Add (0x0AAC, Multiply (PSVT, 0x0A)))
            }

            Method (_TC1, 0, Serialized)
            {
                Return (TC1V)
            }

            Method (_TC2, 0, Serialized)
            {
                Return (TC2V)
            }

            Method (_TSP, 0, Serialized)
            {
                Return (TSPV)
            }
        }
    }

    Scope (_SB)
    {
        Device (ADP1)
        {
            Name (_HID, "ACPI0003")
            Method (_PSR, 0, NotSerialized)
            {
                If (LEqual (ECON, Zero))
                {
                    And (PHSB (0xD4, Zero), 0x80, Local0)
                }
                Else
                {
                    Store (^^PCI0.LPCB.EC.RPWR, Local0)
                }

                If (LEqual (Local0, Zero))
                {
                    Return (Zero)
                }
                Else
                {
                    Return (One)
                }
            }

            Method (_PCL, 0, NotSerialized)
            {
                Return (_SB)
            }
        }

        Device (BAT0)
        {
            Name (_HID, EisaId ("PNP0C0A"))
            Name (_UID, Zero)
            Method (_STA, 0, NotSerialized)
            {
                DBGC (0xB0, 0x80, BCEN)
                Sleep (0x05)
                If (LEqual (ECON, Zero))
                {
                    Store (Zero, Local1)
                }
                Else
                {
                    Store (^^PCI0.LPCB.EC.BATP, Local1)
                }

                If (LEqual (Local1, Zero))
                {
                    Store (0x0F, Local0)
                }
                Else
                {
                    Store (0x1F, Local0)
                }

                DBGC (0xB0, 0x81, BCEN)
                Return (Local0)
            }

            Method (_BIF, 0, NotSerialized)
            {
                Name (MULV, Zero)
                DBGC (0xB1, 0x80, BCEN)
                Name (BATI, Package (0x0D)
                {
                    Zero, 
                    0x2710, 
                    0x2710, 
                    Zero, 
                    0xFFFFFFFF, 
                    0x03E8, 
                    0x0190, 
                    0x64, 
                    0x64, 
                    "", 
                    "", 
                    "LiOn", 
                    "Sony Corp."
                })
                Store (One, MULV)
                Sleep (0x05)
                If (LEqual (ECON, Zero)) {}
                Else
                {
                    And (^^PCI0.LPCB.EC.OMFH, 0x80, Local0)
                    If (Local0)
                    {
                        Store (Zero, Index (BATI, Zero))
                        Store (0x0A, MULV)
                    }
                    Else
                    {
                        Store (One, Index (BATI, Zero))
                    }

                    Store (^^PCI0.LPCB.EC.BDCH, Local0)
                    Or (ShiftLeft (Local0, 0x08), ^^PCI0.LPCB.EC.BDCL, Local0)
                    Store (Multiply (Local0, MULV), Index (BATI, One))
                    Store (^^PCI0.LPCB.EC.FCCH, Local0)
                    Or (ShiftLeft (Local0, 0x08), ^^PCI0.LPCB.EC.FCCL, Local0)
                    Store (Multiply (Local0, MULV), Index (BATI, 0x02))
                    Store (^^PCI0.LPCB.EC.BAVH, Local0)
                    Or (ShiftLeft (Local0, 0x08), ^^PCI0.LPCB.EC.BAVL, Local0)
                    Store (Multiply (Local0, MULV), Index (BATI, 0x04))
                }

                DBGC (0xB1, 0x81, BCEN)
                Return (BATI)
            }

            Method (_BST, 0, NotSerialized)
            {
                DBGC (0xB2, 0x80, BCEN)
                Name (PKG0, Package (0x04)
                {
                    0x02, 
                    0xFFFFFFFF, 
                    0xFFFFFFFF, 
                    0xFFFFFFFF
                })
                Sleep (0x05)
                If (LEqual (ECON, Zero)) {}
                Else
                {
                    If (LEqual (^^PCI0.LPCB.EC.CHGE, One))
                    {
                        Store (^^PCI0.LPCB.EC.RSCL, Local0)
                        If (LEqual (Local0, 0x64))
                        {
                            Store (Zero, Index (PKG0, Zero))
                        }
                        Else
                        {
                            Store (0x02, Index (PKG0, Zero))
                        }
                    }
                    Else
                    {
                        Store (One, Index (PKG0, Zero))
                    }

                    Name (MULV, Zero)
                    And (^^PCI0.LPCB.EC.OMFH, 0x80, Local0)
                    If (Local0)
                    {
                        Store (0x0A, MULV)
                    }
                    Else
                    {
                        Store (One, MULV)
                    }

                    Store (^^PCI0.LPCB.EC.BRCH, Local0)
                    Or (ShiftLeft (Local0, 0x08), ^^PCI0.LPCB.EC.BRCL, Local0)
                    Store (Multiply (Local0, MULV), Index (PKG0, 0x02))
                    Store (^^PCI0.LPCB.EC.BACH, Local0)
                    Or (ShiftLeft (Local0, 0x08), ^^PCI0.LPCB.EC.BACL, Local0)
                    If (LAnd (Local0, 0x8000))
                    {
                        Add (Not (Local0), One, Local0)
                        And (Local0, 0xFFFF, Local0)
                    }

                    Store (^^PCI0.LPCB.EC.BAVH, Local1)
                    Or (ShiftLeft (Local1, 0x08), ^^PCI0.LPCB.EC.BAVL, Local1)
                    Divide (Local1, 0x03E8, , Local1)
                    Store (Multiply (Local0, Local1), Index (PKG0, One))
                }

                DBGC (0xB2, 0x81, BCEN)
                Return (PKG0)
            }

            Method (_PCL, 0, NotSerialized)
            {
                Return (_SB)
            }
        }

        Device (LID0)
        {
            Name (_HID, EisaId ("PNP0C0D"))
            Method (_LID, 0, NotSerialized)
            {
                If (ECON)
                {
                    Store (^^PCI0.LPCB.EC.LSTE, Local0)
                }
                Else
                {
                    And (PHSB (0xD4, Zero), 0x20, Local0)
                }

                If (Local0)
                {
                    Return (Zero)
                }
                Else
                {
                    Return (One)
                }
            }
        }

        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
            Name (_PRW, Package (0x02)
            {
                0x1E, 
                0x04
            })
        }

        Mutex (PLOK, 0x00)
        Method (NCPU, 0, NotSerialized)
        {
            Acquire (PLOK, 0xFFFF)
            Notify (\_PR.CPU0, 0x80)
            Sleep (0x64)
            Notify (\_PR.CPU0, 0x81)
            Release (PLOK)
        }

        Device (PCI0)
        {
            Method (_INI, 0, NotSerialized)
            {
                Store (Zero, ^LPCB.SNC.XECR)
                Store (Zero, ^LPCB.SNC.SNBF)
            }

            Method (_S3D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Method (_S4D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Name (_HID, EisaId ("PNP0A08"))
            Name (_CID, 0x030AD041)
            Name (SUPP, Zero)
            Name (CTRL, Zero)
            Device (MCHC)
            {
                Name (_ADR, Zero)
                OperationRegion (HBUS, PCI_Config, 0x40, 0xC0)
                Field (HBUS, DWordAcc, NoLock, Preserve)
                {
                    EPEN,   1, 
                        ,   11, 
                    EPBR,   20, 
                            Offset (0x08), 
                    MHEN,   1, 
                        ,   13, 
                    MHBR,   18, 
                            Offset (0x20), 
                    PXEN,   1, 
                    PXSZ,   2, 
                        ,   23, 
                    PXBR,   6, 
                            Offset (0x28), 
                    DIEN,   1, 
                        ,   11, 
                    DIBR,   20, 
                            Offset (0x30), 
                    IPEN,   1, 
                        ,   11, 
                    IPBR,   20, 
                            Offset (0x50), 
                        ,   4, 
                    PM0H,   2, 
                            Offset (0x51), 
                    PM1L,   2, 
                        ,   2, 
                    PM1H,   2, 
                            Offset (0x52), 
                    PM2L,   2, 
                        ,   2, 
                    PM2H,   2, 
                            Offset (0x53), 
                    PM3L,   2, 
                        ,   2, 
                    PM3H,   2, 
                            Offset (0x54), 
                    PM4L,   2, 
                        ,   2, 
                    PM4H,   2, 
                            Offset (0x55), 
                    PM5L,   2, 
                        ,   2, 
                    PM5H,   2, 
                            Offset (0x56), 
                    PM6L,   2, 
                        ,   2, 
                    PM6H,   2, 
                            Offset (0x57), 
                        ,   7, 
                    HENA,   1, 
                            Offset (0x62), 
                    TUUD,   16, 
                            Offset (0x70), 
                        ,   4, 
                    TLUD,   12
                }
            }

            Name (BUF0, ResourceTemplate ()
            {
                WordBusNumber (ResourceProducer, MinFixed, MaxFixed, PosDecode,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x00FF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0100,             // Length
                    ,, )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0x00000CF7,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000CF8,         // Length
                    ,, , TypeStatic)
                IO (Decode16,
                    0x0CF8,             // Range Minimum
                    0x0CF8,             // Range Maximum
                    0x01,               // Alignment
                    0x08,               // Length
                    )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000D00,         // Range Minimum
                    0x0000FFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x0000F300,         // Length
                    ,, , TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000A0000,         // Range Minimum
                    0x000BFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C0000,         // Range Minimum
                    0x000C3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y00, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C4000,         // Range Minimum
                    0x000C7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y01, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C8000,         // Range Minimum
                    0x000CBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y02, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000CC000,         // Range Minimum
                    0x000CFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y03, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D0000,         // Range Minimum
                    0x000D3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y04, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D4000,         // Range Minimum
                    0x000D7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y05, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D8000,         // Range Minimum
                    0x000DBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y06, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000DC000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y07, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E0000,         // Range Minimum
                    0x000E3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y08, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E4000,         // Range Minimum
                    0x000E7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y09, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E8000,         // Range Minimum
                    0x000EBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y0A, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000EC000,         // Range Minimum
                    0x000EFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y0B, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000F0000,         // Range Minimum
                    0x000FFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00010000,         // Length
                    ,, _Y0C, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xDFFFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y0D, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xF0000000,         // Range Minimum
                    0xFEBFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x0EC00000,         // Length
                    ,, _Y0E, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xFED40000,         // Range Minimum
                    0xFED44FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
            })
            Method (_CRS, 0, Serialized)
            {
                If (^MCHC.PM1L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y00._LEN, C0LN)
                    Store (Zero, C0LN)
                }

                If (LEqual (^MCHC.PM1L, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y00._RW, C0RW)
                    Store (Zero, C0RW)
                }

                If (^MCHC.PM1H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y01._LEN, C4LN)
                    Store (Zero, C4LN)
                }

                If (LEqual (^MCHC.PM1H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y01._RW, C4RW)
                    Store (Zero, C4RW)
                }

                If (^MCHC.PM2L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y02._LEN, C8LN)
                    Store (Zero, C8LN)
                }

                If (LEqual (^MCHC.PM2L, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y02._RW, C8RW)
                    Store (Zero, C8RW)
                }

                If (^MCHC.PM2H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y03._LEN, CCLN)
                    Store (Zero, CCLN)
                }

                If (LEqual (^MCHC.PM2H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y03._RW, CCRW)
                    Store (Zero, CCRW)
                }

                If (^MCHC.PM3L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y04._LEN, D0LN)
                    Store (Zero, D0LN)
                }

                If (LEqual (^MCHC.PM3L, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y04._RW, D0RW)
                    Store (Zero, D0RW)
                }

                If (^MCHC.PM3H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y05._LEN, D4LN)
                    Store (Zero, D4LN)
                }

                If (LEqual (^MCHC.PM3H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y05._RW, D4RW)
                    Store (Zero, D4RW)
                }

                If (^MCHC.PM4L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y06._LEN, D8LN)
                    Store (Zero, D8LN)
                }

                If (LEqual (^MCHC.PM4L, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y06._RW, D8RW)
                    Store (Zero, D8RW)
                }

                If (^MCHC.PM4H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y07._LEN, DCLN)
                    Store (Zero, DCLN)
                }

                If (LEqual (^MCHC.PM4H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y07._RW, DCRW)
                    Store (Zero, DCRW)
                }

                If (^MCHC.PM5L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y08._LEN, E0LN)
                    Store (Zero, E0LN)
                }

                If (LEqual (^MCHC.PM5L, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y08._RW, E0RW)
                    Store (Zero, E0RW)
                }

                If (^MCHC.PM5H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y09._LEN, E4LN)
                    Store (Zero, E4LN)
                }

                If (LEqual (^MCHC.PM5H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y09._RW, E4RW)
                    Store (Zero, E4RW)
                }

                If (^MCHC.PM6L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0A._LEN, E8LN)
                    Store (Zero, E8LN)
                }

                If (LEqual (^MCHC.PM6L, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0A._RW, E8RW)
                    Store (Zero, E8RW)
                }

                If (^MCHC.PM6H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0B._LEN, ECLN)
                    Store (Zero, ECLN)
                }

                If (LEqual (^MCHC.PM6H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0B._RW, ECRW)
                    Store (Zero, ECRW)
                }

                If (^MCHC.PM0H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0C._LEN, F0LN)
                    Store (Zero, F0LN)
                }

                If (LEqual (^MCHC.PM0H, One))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0C._RW, F0RW)
                    Store (Zero, F0RW)
                }

                CreateDWordField (BUF0, \_SB.PCI0._Y0D._MIN, M1MN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0D._MAX, M1MX)
                CreateDWordField (BUF0, \_SB.PCI0._Y0D._LEN, M1LN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._MIN, M2MN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._MAX, M2MX)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._LEN, M2LN)
                ShiftLeft (^MCHC.PXBR, 0x1A, M1MX)
                ShiftRight (0x10000000, ^MCHC.PXSZ, Local0)
                Add (M1MX, Local0, M2MN)
                Add (Subtract (M2MX, M2MN), One, M2LN)
                Subtract (M1MX, One, M1MX)
                ShiftLeft (^MCHC.TLUD, 0x14, M1MN)
                Add (Subtract (M1MX, M1MN), One, M1LN)
                Return (BUF0)
            }

            Method (_PRT, 0, NotSerialized)
            {
                If (GPIC)
                {
                    Return (Package (0x13)
                    {
                        Package (0x04)
                        {
                            0x0001FFFF, 
                            Zero, 
                            Zero, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0002FFFF, 
                            Zero, 
                            Zero, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            Zero, 
                            Zero, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0019FFFF, 
                            Zero, 
                            Zero, 
                            0x14
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            Zero, 
                            Zero, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            One, 
                            Zero, 
                            0x15
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x02, 
                            Zero, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            Zero, 
                            Zero, 
                            0x16
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            Zero, 
                            Zero, 
                            0x11
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            One, 
                            Zero, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            Zero, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            Zero, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            Zero, 
                            Zero, 
                            0x17
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            One, 
                            Zero, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            Zero, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            Zero, 
                            Zero, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            One, 
                            Zero, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x02, 
                            Zero, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x03, 
                            Zero, 
                            0x10
                        }
                    })
                }
                Else
                {
                    Return (Package (0x13)
                    {
                        Package (0x04)
                        {
                            0x0001FFFF, 
                            Zero, 
                            ^LPCB.LNKA, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x0002FFFF, 
                            Zero, 
                            ^LPCB.LNKA, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            Zero, 
                            ^LPCB.LNKA, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x0019FFFF, 
                            Zero, 
                            ^LPCB.LNKE, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            Zero, 
                            ^LPCB.LNKA, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            One, 
                            ^LPCB.LNKF, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x02, 
                            ^LPCB.LNKC, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            Zero, 
                            ^LPCB.LNKG, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            Zero, 
                            ^LPCB.LNKB, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            One, 
                            ^LPCB.LNKA, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            ^LPCB.LNKC, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            ^LPCB.LNKD, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            Zero, 
                            ^LPCB.LNKH, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            One, 
                            ^LPCB.LNKD, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            ^LPCB.LNKC, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            Zero, 
                            ^LPCB.LNKD, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            One, 
                            ^LPCB.LNKD, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x02, 
                            ^LPCB.LNKD, 
                            Zero
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x03, 
                            ^LPCB.LNKA, 
                            Zero
                        }
                    })
                }
            }

            Method (_OSC, 4, NotSerialized)
            {
                DBGC (0x6C, 0x80, BCEN)
                CreateDWordField (Arg3, Zero, PSTS)
                CreateDWordField (Arg3, 0x04, PSUP)
                CreateDWordField (Arg3, 0x08, PCNT)
                Store (PSUP, SUPP)
                Store (PCNT, CTRL)
                Name (UID1, Buffer (0x10)
                {
                    /* 0000 */    0x5B, 0x4D, 0xDB, 0x33, 0xF7, 0x1F, 0x1C, 0x40, 
                    /* 0008 */    0x96, 0x57, 0x74, 0x41, 0xC0, 0x3D, 0xD7, 0x66
                })
                If (LEqual (Arg0, Buffer (0x10)
                        {
                            /* 0000 */    0x5B, 0x4D, 0xDB, 0x33, 0xF7, 0x1F, 0x1C, 0x40, 
                            /* 0008 */    0x96, 0x57, 0x74, 0x41, 0xC0, 0x3D, 0xD7, 0x66
                        }))
                {
                    And (CTRL, 0x1D, CTRL)
                    If (LNotEqual (And (SUPP, 0x16), 0x16))
                    {
                        And (CTRL, 0x1E)
                    }

                    If (Not (And (PSTS, One)))
                    {
                        If (And (CTRL, One)) {}
                        If (And (CTRL, 0x04)) {}
                        If (And (CTRL, 0x10)) {}
                    }

                    If (LNotEqual (Arg1, One))
                    {
                        Or (PSTS, 0x08, PSTS)
                        DBGC (0x6C, 0x81, BCEN)
                        Return (Arg3)
                    }

                    If (LNotEqual (PCNT, CTRL))
                    {
                        Or (PSTS, 0x10, PSTS)
                    }

                    Store (Zero, PCNT)
                    DBGC (0x6C, 0x82, BCEN)
                    Return (Arg3)
                }
                Else
                {
                    Or (PSTS, 0x04, PSTS)
                    DBGC (0x6C, 0x83, BCEN)
                    Return (Arg3)
                }
            }

            Device (PDRC)
            {
                Name (_HID, EisaId ("PNP0C02"))
                Name (_UID, One)
                Name (BUF0, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00004000,         // Address Length
                        _Y0F)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00004000,         // Address Length
                        _Y10)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00001000,         // Address Length
                        _Y11)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00001000,         // Address Length
                        _Y12)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00000000,         // Address Length
                        _Y13)
                    Memory32Fixed (ReadWrite,
                        0xFED20000,         // Address Base
                        0x00020000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED40000,         // Address Base
                        0x00005000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED45000,         // Address Base
                        0x0004B000,         // Address Length
                        )
                })
                Method (_CRS, 0, Serialized)
                {
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y0F._BAS, RBR0)
                    ShiftLeft (^^LPCB.RCBA, 0x0E, RBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y10._BAS, MBR0)
                    ShiftLeft (^^MCHC.MHBR, 0x0E, MBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y11._BAS, DBR0)
                    ShiftLeft (^^MCHC.DIBR, 0x0C, DBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y12._BAS, EBR0)
                    ShiftLeft (^^MCHC.EPBR, 0x0C, EBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y13._BAS, XBR0)
                    ShiftLeft (^^MCHC.PXBR, 0x1A, XBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y13._LEN, XSZ0)
                    ShiftRight (0x10000000, ^^MCHC.PXSZ, XSZ0)
                    Return (BUF0)
                }
            }

            Device (PEGP)
            {
                Name (_ADR, 0x00010000)
                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                Zero, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                Zero, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                Zero, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                Zero, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                ^^LPCB.LNKA, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                ^^LPCB.LNKB, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                ^^LPCB.LNKC, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                ^^LPCB.LNKD, 
                                Zero
                            }
                        })
                    }
                }

                Device (NGFX)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        DBGC (0x62, Zero, BCEN)
                        Return (Zero)
                    }

                    OperationRegion (NVFX, PCI_Config, Zero, 0x10)
                    Field (NVFX, AnyAcc, NoLock, Preserve)
                    {
                        NVID,   16
                    }

                    Device (LCD)
                    {
                        Name (_ADR, 0x0118)
                    }

                    Name (ERR0, Buffer (0x04)
                    {
                        0x00, 0x00, 0x00, 0x00
                    })
                    Name (ERR1, Buffer (0x04)
                    {
                        0x01, 0x00, 0x00, 0x80
                    })
                    Name (VER1, Buffer (0x04)
                    {
                        0x01, 0x00, 0x00, 0x00
                    })
                    Name (BHW1, Buffer (0x0C)
                    {
                        /* 0000 */    0x00, 0x00, 0x64, 0x00, 0xC8, 0x00, 0x00, 0x00, 
                        /* 0008 */    0x00, 0x00, 0xE8, 0x03
                    })
                    Name (BCL1, Buffer (0x0B)
                    {
                        /* 0000 */    0x64, 0x64, 0x14, 0x18, 0x1D, 0x24, 0x2C, 0x35, 
                        /* 0008 */    0x3F, 0x4C, 0x64
                    })
                    Name (ODID, Buffer (0x10)
                    {
                        /* 0000 */    0x10, 0x01, 0x00, 0x00, 0x00, 0x01, 0x01, 0x00, 
                        /* 0008 */    0x00, 0x02, 0x01, 0x00, 0x20, 0x01, 0x00, 0x00
                    })
                    Method (NVIF, 3, NotSerialized)
                    {
                        DBGC (0x6F, Arg0, BCEN)
                        If (LEqual (Arg0, One))
                        {
                            Concatenate (ERR0, VER1, Local0)
                            Return (Local0)
                        }
                        Else
                        {
                            If (LEqual (Arg0, 0x09))
                            {
                                Name (_T_0, Zero)
                                Store (ToInteger (Arg1), _T_0)
                                If (LEqual (_T_0, Zero))
                                {
                                    Store (ERR0, Local1)
                                    Return (Local1)
                                }
                                Else
                                {
                                    If (LEqual (_T_0, One))
                                    {
                                        Name (_T_1, Zero)
                                        Store (ToInteger (PNID), _T_1)
                                        If (LEqual (_T_1, One))
                                        {
                                            Concatenate (ERR0, BHW1, Local1)
                                        }
                                        Else
                                        {
                                            If (LEqual (_T_1, 0x02))
                                            {
                                                Concatenate (ERR0, BHW1, Local1)
                                            }
                                            Else
                                            {
                                                If (LEqual (_T_1, 0x04))
                                                {
                                                    Concatenate (ERR0, BHW1, Local1)
                                                }
                                                Else
                                                {
                                                    If (LEqual (_T_1, 0x05))
                                                    {
                                                        Concatenate (ERR0, BHW1, Local1)
                                                    }
                                                    Else
                                                    {
                                                        Concatenate (ERR0, BHW1, Local1)
                                                    }
                                                }
                                            }
                                        }

                                        Return (Local1)
                                    }
                                    Else
                                    {
                                        If (LEqual (_T_0, 0x02))
                                        {
                                            Store (ERR0, Local1)
                                            Return (Local1)
                                        }
                                        Else
                                        {
                                            If (LEqual (_T_0, 0x03))
                                            {
                                                Name (_T_2, Zero)
                                                Store (ToInteger (PNID), _T_2)
                                                If (LEqual (_T_2, One))
                                                {
                                                    Concatenate (ERR0, BCL1, Local1)
                                                }
                                                Else
                                                {
                                                    If (LEqual (_T_2, 0x02))
                                                    {
                                                        Concatenate (ERR0, BCL1, Local1)
                                                    }
                                                    Else
                                                    {
                                                        If (LEqual (_T_2, 0x04))
                                                        {
                                                            Concatenate (ERR0, BCL1, Local1)
                                                        }
                                                        Else
                                                        {
                                                            If (LEqual (_T_2, 0x05))
                                                            {
                                                                Concatenate (ERR0, BCL1, Local1)
                                                            }
                                                            Else
                                                            {
                                                                Concatenate (ERR0, BCL1, Local1)
                                                            }
                                                        }
                                                    }
                                                }

                                                Return (Local1)
                                            }
                                        }
                                    }
                                }
                            }
                            Else
                            {
                                If (LEqual (Arg0, 0x0B))
                                {
                                    If (LEqual (Arg1, One))
                                    {
                                        Concatenate (ERR0, ODID, Local0)
                                        Return (Local0)
                                    }
                                    Else
                                    {
                                        Return (ERR1)
                                    }
                                }
                            }
                        }

                        Return (ERR1)
                    }
                }
            }

            Device (GFX0)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x63, Zero, BCEN)
                    Return (0x00020000)
                }

                OperationRegion (IGFX, PCI_Config, 0xF0, 0x10)
                Field (IGFX, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x04), 
                    BREG,   8
                }

                Method (_DOS, 1, NotSerialized)
                {
                    Store (And (Arg0, 0x03), DSEN)
                }

                Method (_DOD, 0, NotSerialized)
                {
                    If (LEqual (NDID, One))
                    {
                        Name (TMP1, Package (0x01)
                        {
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP1, Zero))
                        Return (TMP1)
                    }

                    If (LEqual (NDID, 0x02))
                    {
                        Name (TMP2, Package (0x02)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP2, Zero))
                        Store (Or (0x00010000, DID2), Index (TMP2, One))
                        Return (TMP2)
                    }

                    If (LEqual (NDID, 0x03))
                    {
                        Name (TMP3, Package (0x03)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP3, Zero))
                        Store (Or (0x00010000, DID2), Index (TMP3, One))
                        Store (Or (0x00010000, DID3), Index (TMP3, 0x02))
                        Return (TMP3)
                    }

                    If (LEqual (NDID, 0x04))
                    {
                        Name (TMP4, Package (0x04)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP4, Zero))
                        Store (Or (0x00010000, DID2), Index (TMP4, One))
                        Store (Or (0x00010000, DID3), Index (TMP4, 0x02))
                        Store (Or (0x00010000, DID4), Index (TMP4, 0x03))
                        Return (TMP4)
                    }

                    Name (TMP5, Package (0x05)
                    {
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF
                    })
                    Store (Or (0x00010000, DID1), Index (TMP5, Zero))
                    Store (Or (0x00010000, DID2), Index (TMP5, One))
                    Store (Or (0x00010000, DID3), Index (TMP5, 0x02))
                    Store (Or (0x00010000, DID4), Index (TMP5, 0x03))
                    Store (Or (0x00010000, DID5), Index (TMP5, 0x04))
                    Return (TMP5)
                }

                Device (DD01)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID1))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (One)
                        If (And (CSTE, One))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, One))
                        {
                            Return (One)
                        }

                        Return (Zero)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD02)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID2))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (One)
                        If (And (CSTE, 0x02))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x02))
                        {
                            Return (One)
                        }

                        Return (Zero)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD03)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID3))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (One)
                        If (And (CSTE, 0x04))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x04))
                        {
                            Return (One)
                        }

                        Return (Zero)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD04)
                {
                    Name (RTL1, Buffer (0x09)
                    {
                        /* 0000 */    0x14, 0x18, 0x1D, 0x24, 0x2C, 0x35, 0x3F, 0x4C, 
                        /* 0008 */    0x64
                    })
                    Name (ICL1, Package (0x0B)
                    {
                        0x64, 
                        0x64, 
                        0x04, 
                        0x10, 
                        0x1C, 
                        0x28, 
                        0x34, 
                        0x40, 
                        0x4C, 
                        0x58, 
                        0x64
                    })
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID4))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (One)
                        If (And (CSTE, 0x08))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x08))
                        {
                            Return (One)
                        }

                        Return (Zero)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }

                    Method (_BCL, 0, NotSerialized)
                    {
                        Return (ICL1)
                    }

                    Method (_BCM, 1, NotSerialized)
                    {
                        Divide (Subtract (Arg0, 0x04), 0x0C, , Local0)
                        Name (_T_0, Zero)
                        Store (ToInteger (PNID), _T_0)
                        If (LEqual (_T_0, One))
                        {
                            Store (DerefOf (Index (RTL1, Local0)), Local0)
                        }
                        Else
                        {
                            If (LEqual (_T_0, 0x02))
                            {
                                Store (DerefOf (Index (RTL1, Local0)), Local0)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x04))
                                {
                                    Store (DerefOf (Index (RTL1, Local0)), Local0)
                                }
                                Else
                                {
                                    If (LEqual (_T_0, 0x05))
                                    {
                                        Store (DerefOf (Index (RTL1, Local0)), Local0)
                                    }
                                    Else
                                    {
                                        Store (DerefOf (Index (RTL1, Local0)), Local0)
                                    }
                                }
                            }
                        }

                        Store (Local0, BRTL)
                        Store (Local0, CBLV)
                        AINT (One, BRTL)
                    }
                }

                Device (DD05)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID5))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (One)
                        If (And (CSTE, 0x10))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x10))
                        {
                            Return (One)
                        }

                        Return (Zero)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Scope (^^PCI0)
                {
                    OperationRegion (MCHP, PCI_Config, 0x40, 0xC0)
                    Field (MCHP, AnyAcc, NoLock, Preserve)
                    {
                                Offset (0x60), 
                        TASM,   10, 
                                Offset (0x62)
                    }
                }

                OperationRegion (IGDP, PCI_Config, 0x40, 0xC0)
                Field (IGDP, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x12), 
                        ,   1, 
                    GIVD,   1, 
                        ,   2, 
                    GUMA,   3, 
                            Offset (0x14), 
                        ,   4, 
                    GMFN,   1, 
                            Offset (0x18), 
                            Offset (0xA4), 
                    ASLE,   8, 
                            Offset (0xA8), 
                    GSSE,   1, 
                    GSSB,   14, 
                    GSES,   1, 
                            Offset (0xB0), 
                            Offset (0xB1), 
                    CDVL,   5, 
                            Offset (0xB2), 
                            Offset (0xB5), 
                    LBPC,   8, 
                            Offset (0xBC), 
                    ASLS,   32
                }

                OperationRegion (IGDM, SystemMemory, ASLB, 0x2000)
                Field (IGDM, AnyAcc, NoLock, Preserve)
                {
                    SIGN,   128, 
                    SIZE,   32, 
                    OVER,   32, 
                    SVER,   256, 
                    VVER,   128, 
                    GVER,   128, 
                    MBOX,   32, 
                            Offset (0x100), 
                    DRDY,   32, 
                    CSTS,   32, 
                    CEVT,   32, 
                            Offset (0x120), 
                    DIDL,   32, 
                    DDL2,   32, 
                    DDL3,   32, 
                    DDL4,   32, 
                    DDL5,   32, 
                    DDL6,   32, 
                    DDL7,   32, 
                    DDL8,   32, 
                    CPDL,   32, 
                    CPL2,   32, 
                    CPL3,   32, 
                    CPL4,   32, 
                    CPL5,   32, 
                    CPL6,   32, 
                    CPL7,   32, 
                    CPL8,   32, 
                    CADL,   32, 
                    CAL2,   32, 
                    CAL3,   32, 
                    CAL4,   32, 
                    CAL5,   32, 
                    CAL6,   32, 
                    CAL7,   32, 
                    CAL8,   32, 
                    NADL,   32, 
                    NDL2,   32, 
                    NDL3,   32, 
                    NDL4,   32, 
                    NDL5,   32, 
                    NDL6,   32, 
                    NDL7,   32, 
                    NDL8,   32, 
                    ASLP,   32, 
                    TIDX,   32, 
                    CHPD,   32, 
                    CLID,   32, 
                    CDCK,   32, 
                    SXSW,   32, 
                    EVTS,   32, 
                    CNOT,   32, 
                    NRDY,   32, 
                            Offset (0x200), 
                    SCIE,   1, 
                    GEFC,   4, 
                    GXFC,   3, 
                    GESF,   8, 
                            Offset (0x204), 
                    PARM,   32, 
                    DSLP,   32, 
                            Offset (0x300), 
                    ARDY,   32, 
                    ASLC,   32, 
                    TCHE,   32, 
                    ALSI,   32, 
                    BCLP,   32, 
                    PFIT,   32, 
                    CBLV,   32, 
                    BCLM,   320, 
                    CPFM,   32, 
                    EPFM,   32, 
                            Offset (0x400), 
                    GVD1,   57344
                }

                Name (DBTB, Package (0x15)
                {
                    Zero, 
                    0x07, 
                    0x38, 
                    0x01C0, 
                    0x0E00, 
                    0x3F, 
                    0x01C7, 
                    0x0E07, 
                    0x01F8, 
                    0x0E38, 
                    0x0FC0, 
                    Zero, 
                    Zero, 
                    Zero, 
                    Zero, 
                    Zero, 
                    0x7000, 
                    0x7007, 
                    0x7038, 
                    0x71C0, 
                    0x7E00
                })
                Name (CDCT, Package (0x03)
                {
                    Package (0x03)
                    {
                        0xC8, 
                        0x0140, 
                        0x0190
                    }, 

                    Package (0x03)
                    {
                        0xC8, 
                        0x014D, 
                        0x0190
                    }, 

                    Package (0x03)
                    {
                        0xDE, 
                        0x014D, 
                        0x017D
                    }
                })
                Name (SUCC, One)
                Name (NVLD, 0x02)
                Name (CRIT, 0x04)
                Name (NCRT, 0x06)
                Method (GSCI, 0, Serialized)
                {
                    Method (GBDA, 0, Serialized)
                    {
                        If (LEqual (GESF, Zero))
                        {
                            Store (0x0279, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, One))
                        {
                            Store (0x0240, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x04))
                        {
                            And (PARM, 0xEFFF0000, PARM)
                            And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
                                PARM)
                            Or (IBTT, PARM, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x05))
                        {
                            Store (IPSC, PARM)
                            Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
                            Add (PARM, 0x0100, PARM)
                            Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
                            Add (PARM, 0x00010000, PARM)
                            Or (PARM, ShiftLeft (IBLC, 0x12), PARM)
                            Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x06))
                        {
                            Store (ITVF, PARM)
                            Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x07))
                        {
                            Store (GIVD, PARM)
                            XOr (PARM, One, PARM)
                            Or (PARM, ShiftLeft (GMFN, One), PARM)
                            Or (PARM, 0x1000, PARM)
                            If (IDMM)
                            {
                                Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
                            }
                            Else
                            {
                                Or (PARM, ShiftLeft (IDMS, 0x0D), PARM)
                            }

                            Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), Subtract (
                                CDVL, One))), 0x15), PARM, PARM)
                            Store (One, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x0A))
                        {
                            Store (Zero, PARM)
                            If (ISSC)
                            {
                                Or (PARM, 0x03, PARM)
                            }

                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        Store (Zero, GESF)
                        Return (CRIT)
                    }

                    Method (SBCB, 0, Serialized)
                    {
                        If (LEqual (GESF, Zero))
                        {
                            Store (Zero, PARM)
                            Store (0xF7FD, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, One))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x03))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x04))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x05))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x06))
                        {
                            Store (And (PARM, 0x0F), ITVF)
                            Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x07))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x08))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x09))
                        {
                            And (PARM, 0xFF, IBTT)
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x0A))
                        {
                            And (PARM, 0xFF, IPSC)
                            If (And (ShiftRight (PARM, 0x08), 0xFF))
                            {
                                And (ShiftRight (PARM, 0x08), 0xFF, IPAT)
                                Decrement (IPAT)
                            }

                            And (ShiftRight (PARM, 0x14), 0x07, IBIA)
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x0B))
                        {
                            And (ShiftRight (PARM, One), One, IF1E)
                            If (And (PARM, 0x0001E000))
                            {
                                And (ShiftRight (PARM, 0x0D), 0x0F, IDMS)
                                Store (Zero, IDMM)
                            }
                            Else
                            {
                                And (ShiftRight (PARM, 0x11), 0x0F, IDMS)
                                Store (One, IDMM)
                            }

                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x10))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x11))
                        {
                            Store (ShiftLeft (LIDS, 0x08), PARM)
                            Add (PARM, 0x0100, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x12))
                        {
                            If (And (PARM, One))
                            {
                                If (LEqual (ShiftRight (PARM, One), One))
                                {
                                    Store (One, ISSC)
                                }
                                Else
                                {
                                    Store (Zero, GESF)
                                    Return (CRIT)
                                }
                            }
                            Else
                            {
                                Store (Zero, ISSC)
                            }

                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x13))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        Store (Zero, GESF)
                        Return (SUCC)
                    }

                    If (LEqual (GEFC, 0x04))
                    {
                        Store (GBDA (), GXFC)
                    }

                    If (LEqual (GEFC, 0x06))
                    {
                        Store (SBCB (), GXFC)
                    }

                    Store (Zero, GEFC)
                    Store (One, SCIS)
                    Store (Zero, GSSE)
                    Store (Zero, SCIE)
                    Return (Zero)
                }

                Method (PDRD, 0, NotSerialized)
                {
                    If (LNot (DRDY))
                    {
                        Sleep (ASLP)
                    }

                    Return (LNot (DRDY))
                }

                Method (PSTS, 0, NotSerialized)
                {
                    If (LGreater (CSTS, 0x02))
                    {
                        Sleep (ASLP)
                    }

                    Return (LEqual (CSTS, 0x03))
                }

                Method (GNOT, 2, NotSerialized)
                {
                    If (PDRD ())
                    {
                        Return (One)
                    }

                    If (PSTS ())
                    {
                        Return (One)
                    }

                    Store (Arg0, CEVT)
                    Store (0x03, CSTS)
                    If (LAnd (LEqual (CHPD, Zero), LEqual (Arg1, Zero)))
                    {
                        If (LOr (LGreater (OSYS, 0x07D0), LLess (OSYS, 0x07D6)))
                        {
                            Notify (PCI0, Arg1)
                        }
                        Else
                        {
                            Notify (GFX0, Arg1)
                        }
                    }

                    Notify (GFX0, 0x80)
                    If (LNot (PSTS ()))
                    {
                        Store (Zero, CEVT)
                    }

                    Return (Zero)
                }

                Method (GHDS, 1, NotSerialized)
                {
                    Store (Arg0, TIDX)
                    Return (GNOT (One, Zero))
                }

                Method (GLID, 1, NotSerialized)
                {
                    Store (Arg0, CLID)
                    Return (GNOT (0x02, Zero))
                }

                Method (GDCK, 1, NotSerialized)
                {
                    Store (Arg0, CDCK)
                    Return (GNOT (0x04, 0x80))
                }

                Method (PARD, 0, NotSerialized)
                {
                    If (LNot (ARDY))
                    {
                        Sleep (ASLP)
                    }

                    Return (LNot (ARDY))
                }

                Method (AINT, 2, NotSerialized)
                {
                    If (LNot (And (TCHE, ShiftLeft (One, Arg0))))
                    {
                        Return (One)
                    }

                    If (PARD ())
                    {
                        Return (One)
                    }

                    If (LEqual (Arg0, 0x02))
                    {
                        If (CPFM)
                        {
                            And (CPFM, 0x0F, Local0)
                            And (EPFM, 0x0F, Local1)
                            If (LEqual (Local0, One))
                            {
                                If (And (Local1, 0x06))
                                {
                                    Store (0x06, PFIT)
                                }
                                Else
                                {
                                    If (And (Local1, 0x08))
                                    {
                                        Store (0x08, PFIT)
                                    }
                                    Else
                                    {
                                        Store (One, PFIT)
                                    }
                                }
                            }

                            If (LEqual (Local0, 0x06))
                            {
                                If (And (Local1, 0x08))
                                {
                                    Store (0x08, PFIT)
                                }
                                Else
                                {
                                    If (And (Local1, One))
                                    {
                                        Store (One, PFIT)
                                    }
                                    Else
                                    {
                                        Store (0x06, PFIT)
                                    }
                                }
                            }

                            If (LEqual (Local0, 0x08))
                            {
                                If (And (Local1, One))
                                {
                                    Store (One, PFIT)
                                }
                                Else
                                {
                                    If (And (Local1, 0x06))
                                    {
                                        Store (0x06, PFIT)
                                    }
                                    Else
                                    {
                                        Store (0x08, PFIT)
                                    }
                                }
                            }
                        }
                        Else
                        {
                            XOr (PFIT, 0x07, PFIT)
                        }

                        Or (PFIT, 0x80000000, PFIT)
                        Store (0x04, ASLC)
                    }
                    Else
                    {
                        If (LEqual (Arg0, One))
                        {
                            Store (Divide (Multiply (Arg1, 0xFF), 0x64, ), BCLP)
                            Or (BCLP, 0x80000000, BCLP)
                            Store (0x02, ASLC)
                        }
                        Else
                        {
                            If (LEqual (Arg0, Zero))
                            {
                                Store (Arg1, ALSI)
                                Store (One, ASLC)
                            }
                            Else
                            {
                                Return (One)
                            }
                        }
                    }

                    Store (Zero, LBPC)
                    Return (Zero)
                }
            }

            Scope (\)
            {
                Method (BRTW, 1, Serialized)
                {
                    Store (Arg0, Local1)
                    If (LEqual (ALSE, 0x02))
                    {
                        Store (Divide (Multiply (ALAF, Arg0), 0x64, ), Local1)
                        If (LGreater (Local1, 0x64))
                        {
                            Store (0x64, Local1)
                        }
                    }

                    Store (Divide (Multiply (0xFF, Local1), 0x64, ), Local0)
                    Store (Local0, PRM0)
                    Store (Arg0, BRTL)
                    If (LEqual (TRAP (0x12), Zero))
                    {
                        P8XH (0x02, Local0)
                    }
                }

                Method (HKDS, 1, Serialized)
                {
                    If (LEqual (Zero, And (0x03, DSEN)))
                    {
                        If (LEqual (TRAP (Arg0), Zero))
                        {
                            If (LNotEqual (CADL, PADL))
                            {
                                Store (CADL, PADL)
                                If (LOr (LGreater (OSYS, 0x07D0), LLess (OSYS, 0x07D6)))
                                {
                                    Notify (\_SB.PCI0, Zero)
                                }
                                Else
                                {
                                    Notify (\_SB.PCI0.GFX0, Zero)
                                }

                                Sleep (0x02EE)
                            }

                            Notify (\_SB.PCI0.GFX0, 0x80)
                        }
                    }

                    If (LEqual (One, And (0x03, DSEN)))
                    {
                        If (LEqual (TRAP (Increment (Arg0)), Zero))
                        {
                            Notify (\_SB.PCI0.GFX0, 0x81)
                        }
                    }
                }

                Method (LSDS, 1, Serialized)
                {
                    If (Arg0)
                    {
                        HKDS (0x0C)
                    }
                    Else
                    {
                        HKDS (0x0E)
                    }

                    If (LNotEqual (And (0x03, DSEN), One))
                    {
                        Sleep (0x32)
                        While (LEqual (And (0x03, DSEN), 0x02))
                        {
                            Sleep (0x32)
                        }
                    }
                }

                Method (BRTN, 1, Serialized)
                {
                    If (LEqual (And (DID1, 0x0F00), 0x0400))
                    {
                        Notify (\_SB.PCI0.GFX0.DD01, Arg0)
                    }

                    If (LEqual (And (DID2, 0x0F00), 0x0400))
                    {
                        Notify (\_SB.PCI0.GFX0.DD02, Arg0)
                    }

                    If (LEqual (And (DID3, 0x0F00), 0x0400))
                    {
                        Notify (\_SB.PCI0.GFX0.DD03, Arg0)
                    }

                    If (LEqual (And (DID4, 0x0F00), 0x0400))
                    {
                        Notify (\_SB.PCI0.GFX0.DD04, Arg0)
                    }

                    If (LEqual (And (DID5, 0x0F00), 0x0400))
                    {
                        Notify (\_SB.PCI0.GFX0.DD05, Arg0)
                    }
                }
            }

            Scope (\)
            {
                OperationRegion (IO_T, SystemIO, 0x0800, 0x10)
                Field (IO_T, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x08), 
                    TRP0,   8
                }

                OperationRegion (PMIO, SystemIO, 0x1000, 0x80)
                Field (PMIO, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x01), 
                    PMST,   8, 
                            Offset (0x42), 
                        ,   1, 
                    GPEC,   1, 
                            Offset (0x64), 
                        ,   9, 
                    SCIS,   1, 
                            Offset (0x66)
                }

                OperationRegion (GPIO, SystemIO, 0x1180, 0x3C)
                Field (GPIO, ByteAcc, NoLock, Preserve)
                {
                    GU00,   8, 
                    GU01,   8, 
                    GU02,   8, 
                    GU03,   8, 
                    GIO0,   8, 
                    GIO1,   8, 
                    GIO2,   8, 
                    GIO3,   8, 
                            Offset (0x0C), 
                        ,   2, 
                    GP02,   1, 
                            Offset (0x0D), 
                        ,   4, 
                    GP12,   1, 
                            Offset (0x0E), 
                        ,   5, 
                    GP21,   1, 
                            Offset (0x0F), 
                        ,   3, 
                    GP27,   1, 
                    GP28,   1, 
                            Offset (0x10), 
                            Offset (0x18), 
                    GB00,   8, 
                    GB01,   8, 
                    GB02,   8, 
                    GB03,   8, 
                            Offset (0x2C), 
                    GIV0,   8, 
                    GIV1,   8, 
                    GIV2,   8, 
                    GIV3,   8, 
                    GU04,   8, 
                    GU05,   8, 
                    GU06,   8, 
                    GU07,   8, 
                    GIO4,   8, 
                    GIO5,   8, 
                    GIO6,   8, 
                    GIO7,   8, 
                        ,   5, 
                    GP37,   1, 
                            Offset (0x39), 
                    GL05,   8, 
                    GL06,   8, 
                    GL07,   8
                }

                OperationRegion (RCRB, SystemMemory, 0xFED1C000, 0x4000)
                Field (RCRB, DWordAcc, Lock, Preserve)
                {
                            Offset (0x1000), 
                            Offset (0x3000), 
                            Offset (0x3404), 
                    HPAS,   2, 
                        ,   5, 
                    HPAE,   1, 
                            Offset (0x3418), 
                        ,   1, 
                    PATD,   1, 
                    SATD,   1, 
                    SMBD,   1, 
                    HDAD,   1, 
                            Offset (0x341A), 
                    RP1D,   1, 
                    RP2D,   1, 
                    RP3D,   1, 
                    RP4D,   1, 
                    RP5D,   1, 
                    RP6D,   1
                }

                OperationRegion (XCMS, SystemIO, 0x72, 0x02)
                Field (XCMS, ByteAcc, NoLock, Preserve)
                {
                    XIND,   8, 
                    XDAT,   8
                }

                IndexField (XIND, XDAT, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x6C), 
                    CM6C,   8, 
                    CM6D,   8, 
                    CM6E,   8, 
                    CM6F,   8, 
                            Offset (0x72), 
                    CM72,   8, 
                            Offset (0x76), 
                    DETC,   8
                }

                Name (BFER, Zero)
                Mutex (RWCM, 0x00)
                Method (DBGC, 3, NotSerialized)
                {
                    Acquire (RWCM, 0xFFFF)
                    If (LEqual (Arg2, 0x02))
                    {
                        Store (CM6D, BFER)
                        If (LNotEqual (Arg0, BFER))
                        {
                            Store (BFER, CM6E)
                            Sleep (One)
                            Store (Arg0, CM6D)
                        }

                        Sleep (One)
                        Store (Arg1, CM6F)
                    }

                    Release (RWCM)
                }

                Name (_S0, Package (0x03)
                {
                    Zero, 
                    Zero, 
                    Zero
                })
                Name (_S3, Package (0x03)
                {
                    0x05, 
                    0x05, 
                    Zero
                })
                Name (_S4, Package (0x03)
                {
                    0x06, 
                    0x06, 
                    Zero
                })
                Name (_S5, Package (0x03)
                {
                    0x07, 
                    0x07, 
                    Zero
                })
                Method (GETP, 1, Serialized)
                {
                    If (LEqual (And (Arg0, 0x09), Zero))
                    {
                        Return (0xFFFFFFFF)
                    }

                    If (LEqual (And (Arg0, 0x09), 0x08))
                    {
                        Return (0x0384)
                    }

                    ShiftRight (And (Arg0, 0x0300), 0x08, Local0)
                    ShiftRight (And (Arg0, 0x3000), 0x0C, Local1)
                    Return (Multiply (0x1E, Subtract (0x09, Add (Local0, Local1))
                        ))
                }

                Method (GDMA, 5, Serialized)
                {
                    If (Arg0)
                    {
                        If (LAnd (Arg1, Arg4))
                        {
                            Return (0x14)
                        }

                        If (LAnd (Arg2, Arg4))
                        {
                            Return (Multiply (Subtract (0x04, Arg3), 0x0F))
                        }

                        Return (Multiply (Subtract (0x04, Arg3), 0x1E))
                    }

                    Return (0xFFFFFFFF)
                }

                Method (GETT, 1, Serialized)
                {
                    Return (Multiply (0x1E, Subtract (0x09, Add (And (ShiftRight (Arg0, 0x02
                        ), 0x03), And (Arg0, 0x03)))))
                }

                Method (GETF, 3, Serialized)
                {
                    Name (TMPF, Zero)
                    If (Arg0)
                    {
                        Or (TMPF, One, TMPF)
                    }

                    If (And (Arg2, 0x02))
                    {
                        Or (TMPF, 0x02, TMPF)
                    }

                    If (Arg1)
                    {
                        Or (TMPF, 0x04, TMPF)
                    }

                    If (And (Arg2, 0x20))
                    {
                        Or (TMPF, 0x08, TMPF)
                    }

                    If (And (Arg2, 0x4000))
                    {
                        Or (TMPF, 0x10, TMPF)
                    }

                    Return (TMPF)
                }

                Method (SETP, 3, Serialized)
                {
                    If (LGreater (Arg0, 0xF0))
                    {
                        Return (0x08)
                    }
                    Else
                    {
                        If (And (Arg1, 0x02))
                        {
                            If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
                            {
                                Return (0x2301)
                            }

                            If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, One)))
                            {
                                Return (0x2101)
                            }
                        }

                        Return (0x1001)
                    }
                }

                Method (SDMA, 1, Serialized)
                {
                    If (LLessEqual (Arg0, 0x14))
                    {
                        Return (One)
                    }

                    If (LLessEqual (Arg0, 0x1E))
                    {
                        Return (0x02)
                    }

                    If (LLessEqual (Arg0, 0x2D))
                    {
                        Return (One)
                    }

                    If (LLessEqual (Arg0, 0x3C))
                    {
                        Return (0x02)
                    }

                    If (LLessEqual (Arg0, 0x5A))
                    {
                        Return (One)
                    }

                    Return (Zero)
                }

                Method (SETT, 3, Serialized)
                {
                    If (And (Arg1, 0x02))
                    {
                        If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
                        {
                            Return (0x0B)
                        }

                        If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, One)))
                        {
                            Return (0x09)
                        }
                    }

                    Return (0x04)
                }
            }

            Device (HDEF)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x64, Zero, BCEN)
                    Return (0x001B0000)
                }

                OperationRegion (HDAR, PCI_Config, 0x4C, 0x10)
                Field (HDAR, WordAcc, NoLock, Preserve)
                {
                    DCKA,   1, 
                            Offset (0x01), 
                    DCKM,   1, 
                        ,   6, 
                    DCKS,   1, 
                            Offset (0x08), 
                        ,   15, 
                    PMES,   1
                }
            }

            Device (RP01)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x65, Zero, BCEN)
                    Return (0x001C0000)
                }

                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x9C), 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, Zero)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x03
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                Zero, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                Zero, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                Zero, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                Zero, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                ^^LPCB.LNKA, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                ^^LPCB.LNKB, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                ^^LPCB.LNKC, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                ^^LPCB.LNKD, 
                                Zero
                            }
                        })
                    }
                }
            }

            Device (RP02)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x65, One, BCEN)
                    Return (0x001C0001)
                }

                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x9C), 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, Zero)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x03
                    })
                }

                Method (_HPP, 0, NotSerialized)
                {
                    Return (Package (0x04)
                    {
                        0x10, 
                        0x40, 
                        One, 
                        Zero
                    })
                }

                Name (PXSX._RMV, One)
                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                Zero, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                Zero, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                Zero, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                Zero, 
                                0x10
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                ^^LPCB.LNKB, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                ^^LPCB.LNKC, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                ^^LPCB.LNKD, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                ^^LPCB.LNKA, 
                                Zero
                            }
                        })
                    }
                }
            }

            Device (RP03)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x65, 0x02, BCEN)
                    Return (0x001C0002)
                }

                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x9C), 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, Zero)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x03
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                Zero, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                Zero, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                Zero, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                Zero, 
                                0x11
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                ^^LPCB.LNKC, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                ^^LPCB.LNKD, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                ^^LPCB.LNKA, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                ^^LPCB.LNKB, 
                                Zero
                            }
                        })
                    }
                }
            }

            Device (RP05)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x65, 0x04, BCEN)
                    Return (0x001C0004)
                }

                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x9C), 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, Zero)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x03
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                Zero, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                Zero, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                Zero, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                Zero, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                Zero, 
                                ^^LPCB.LNKA, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                One, 
                                ^^LPCB.LNKB, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                ^^LPCB.LNKC, 
                                Zero
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                ^^LPCB.LNKD, 
                                Zero
                            }
                        })
                    }
                }
            }

            Device (USB1)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x66, One, BCEN)
                    Return (0x001D0000)
                }

                OperationRegion (U1CS, PCI_Config, 0xC4, 0x04)
                Field (U1CS, DWordAcc, NoLock, Preserve)
                {
                    U1EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x03, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U1EN)
                    }
                    Else
                    {
                        Store (Zero, U1EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB2)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x66, 0x02, BCEN)
                    Return (0x001D0001)
                }

                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U2EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x04, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U2EN)
                    }
                    Else
                    {
                        Store (Zero, U2EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB3)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x66, 0x03, BCEN)
                    Return (0x001D0002)
                }

                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U3EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x0C, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U3EN)
                    }
                    Else
                    {
                        Store (Zero, U3EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB4)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x66, 0x04, BCEN)
                    Return (0x001A0000)
                }

                OperationRegion (U4CS, PCI_Config, 0xC4, 0x04)
                Field (U4CS, DWordAcc, NoLock, Preserve)
                {
                    U4EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x0E, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U4EN)
                    }
                    Else
                    {
                        Store (Zero, U4EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB5)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x66, 0x05, BCEN)
                    Return (0x001A0001)
                }

                OperationRegion (U5CS, PCI_Config, 0xC4, 0x04)
                Field (U5CS, DWordAcc, NoLock, Preserve)
                {
                    U5EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x05, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U5EN)
                    }
                    Else
                    {
                        Store (Zero, U5EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (EHC1)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x67, One, BCEN)
                    Return (0x001D0007)
                }

                OperationRegion (U7CS, PCI_Config, 0x54, 0x04)
                Field (U7CS, DWordAcc, NoLock, Preserve)
                {
                        ,   15, 
                    PMES,   1
                }

                Device (HUB7)
                {
                    Name (_ADR, Zero)
                    Device (PRT1)
                    {
                        Name (_ADR, One)
                    }

                    Device (PRT2)
                    {
                        Name (_ADR, 0x02)
                    }

                    Device (PRT3)
                    {
                        Name (_ADR, 0x03)
                    }

                    Device (PRT4)
                    {
                        Name (_ADR, 0x04)
                    }

                    Device (PRT5)
                    {
                        Name (_ADR, 0x05)
                    }

                    Device (PRT6)
                    {
                        Name (_ADR, 0x06)
                    }
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (EHC2)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x67, 0x02, BCEN)
                    Return (0x001A0007)
                }

                OperationRegion (UFCS, PCI_Config, 0x54, 0x04)
                Field (UFCS, DWordAcc, NoLock, Preserve)
                {
                        ,   15, 
                    PMES,   1
                }

                Device (HUB7)
                {
                    Name (_ADR, Zero)
                    Device (PRT1)
                    {
                        Name (_ADR, One)
                    }

                    Device (PRT2)
                    {
                        Name (_ADR, 0x02)
                    }

                    Device (PRT3)
                    {
                        Name (_ADR, 0x03)
                    }

                    Device (PRT4)
                    {
                        Name (_ADR, 0x04)
                    }
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (PCIB)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x68, Zero, BCEN)
                    Return (0x001E0000)
                }

                Device (CARD)
                {
                    Name (_ADR, 0x00030000)
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0B)
                    }
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (Zero)
                    {
                        If (GPIC)
                        {
                            Return (Package (0x10)
                            {
                                Package (0x04)
                                {
                                    0xFFFF, 
                                    Zero, 
                                    Zero, 
                                    0x15
                                }, 

                                Package (0x04)
                                {
                                    0xFFFF, 
                                    One, 
                                    Zero, 
                                    0x16
                                }, 

                                Package (0x04)
                                {
                                    0xFFFF, 
                                    0x02, 
                                    Zero, 
                                    0x17
                                }, 

                                Package (0x04)
                                {
                                    0xFFFF, 
                                    0x03, 
                                    Zero, 
                                    0x14
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    Zero, 
                                    Zero, 
                                    0x16
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    One, 
                                    Zero, 
                                    0x15
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    0x02, 
                                    Zero, 
                                    0x14
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    0x03, 
                                    Zero, 
                                    0x17
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    Zero, 
                                    Zero, 
                                    0x12
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    One, 
                                    Zero, 
                                    0x13
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    0x02, 
                                    Zero, 
                                    0x11
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    0x03, 
                                    Zero, 
                                    0x10
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    Zero, 
                                    Zero, 
                                    0x11
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    One, 
                                    Zero, 
                                    0x14
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    0x02, 
                                    Zero, 
                                    0x16
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    0x03, 
                                    Zero, 
                                    0x15
                                }
                            })
                        }
                        Else
                        {
                            Return (Package (0x10)
                            {
                                Package (0x04)
                                {
                                    0xFFFF, 
                                    Zero, 
                                    ^^LPCB.LNKF, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0xFFFF, 
                                    One, 
                                    ^^LPCB.LNKG, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0xFFFF, 
                                    0x02, 
                                    ^^LPCB.LNKH, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0xFFFF, 
                                    0x03, 
                                    ^^LPCB.LNKE, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    Zero, 
                                    ^^LPCB.LNKG, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    One, 
                                    ^^LPCB.LNKF, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    0x02, 
                                    ^^LPCB.LNKE, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0001FFFF, 
                                    0x03, 
                                    ^^LPCB.LNKH, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    Zero, 
                                    ^^LPCB.LNKC, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    One, 
                                    ^^LPCB.LNKD, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    0x02, 
                                    ^^LPCB.LNKB, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0002FFFF, 
                                    0x03, 
                                    ^^LPCB.LNKA, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    Zero, 
                                    ^^LPCB.LNKB, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    One, 
                                    ^^LPCB.LNKE, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    0x02, 
                                    ^^LPCB.LNKG, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0005FFFF, 
                                    0x03, 
                                    ^^LPCB.LNKF, 
                                    Zero
                                }
                            })
                        }
                    }
                    Else
                    {
                        If (GPIC)
                        {
                            Return (Package (0x03)
                            {
                                Package (0x04)
                                {
                                    0x0003FFFF, 
                                    Zero, 
                                    Zero, 
                                    0x10
                                }, 

                                Package (0x04)
                                {
                                    0x0003FFFF, 
                                    One, 
                                    Zero, 
                                    0x11
                                }, 

                                Package (0x04)
                                {
                                    0x0003FFFF, 
                                    0x02, 
                                    Zero, 
                                    0x12
                                }
                            })
                        }
                        Else
                        {
                            Return (Package (0x03)
                            {
                                Package (0x04)
                                {
                                    0x0003FFFF, 
                                    Zero, 
                                    ^^LPCB.LNKA, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0003FFFF, 
                                    One, 
                                    ^^LPCB.LNKB, 
                                    Zero
                                }, 

                                Package (0x04)
                                {
                                    0x0003FFFF, 
                                    0x02, 
                                    ^^LPCB.LNKC, 
                                    Zero
                                }
                            })
                        }
                    }
                }
            }

            Device (LPCB)
            {
                Name (_ADR, 0x001F0000)
                OperationRegion (LPC0, PCI_Config, 0x40, 0xC0)
                Field (LPC0, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x20), 
                    PARC,   8, 
                    PBRC,   8, 
                    PCRC,   8, 
                    PDRC,   8, 
                            Offset (0x28), 
                    PERC,   8, 
                    PFRC,   8, 
                    PGRC,   8, 
                    PHRC,   8, 
                            Offset (0x40), 
                    IOD0,   8, 
                    IOD1,   8, 
                            Offset (0xB0), 
                    RAEN,   1, 
                        ,   13, 
                    RCBA,   18
                }

                Device (LNKA)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, One)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PARC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLA, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLA, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PARC, 0x0F), IRQ0)
                        Return (RTLA)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PARC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PARC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKB)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x02)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PBRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLB, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLB, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PBRC, 0x0F), IRQ0)
                        Return (RTLB)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PBRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PBRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKC)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x03)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PCRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLC, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLC, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PCRC, 0x0F), IRQ0)
                        Return (RTLC)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PCRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PCRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKD)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x04)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PDRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLD, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLD, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PDRC, 0x0F), IRQ0)
                        Return (RTLD)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PDRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PDRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKE)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x05)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PERC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLE, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLE, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PERC, 0x0F), IRQ0)
                        Return (RTLE)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PERC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PERC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKF)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x06)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PFRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLF, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLF, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PFRC, 0x0F), IRQ0)
                        Return (RTLF)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PFRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PFRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKG)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x07)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PGRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLG, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLG, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PGRC, 0x0F), IRQ0)
                        Return (RTLG)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PGRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PGRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKH)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x08)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PHRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLH, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {}
                        })
                        CreateWordField (RTLH, One, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (One, And (PHRC, 0x0F), IRQ0)
                        Return (RTLH)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, One, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PHRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PHRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (EC)
                {
                    Name (_HID, EisaId ("PNP0C09"))
                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BFFR, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0062,             // Range Minimum
                                0x0062,             // Range Maximum
                                0x00,               // Alignment
                                0x01,               // Length
                                )
                            IO (Decode16,
                                0x0066,             // Range Minimum
                                0x0066,             // Range Maximum
                                0x00,               // Alignment
                                0x01,               // Length
                                )
                        })
                        Return (BFFR)
                    }

                    OperationRegion (ECF2, EmbeddedControl, Zero, 0xFF)
                    Field (ECF2, ByteAcc, Lock, Preserve)
                    {
                            ,   3, 
                        PRCP,   1, 
                            ,   1, 
                        LSTE,   1, 
                        BATP,   1, 
                        RPWR,   1, 
                            ,   4, 
                        CHGE,   1, 
                        LVDS,   1, 
                            ,   1, 
                        AUAM,   1, 
                        ENR0,   8, 
                        ENR1,   8, 
                        ESR0,   8, 
                        ESR1,   8, 
                        BSTS,   8, 
                        WKSR,   8, 
                                Offset (0x19), 
                        ISID,   8, 
                                Offset (0x20), 
                        BTPL,   8, 
                        BTPH,   8, 
                        BSNL,   8, 
                        BSNH,   8, 
                        BDCL,   8, 
                        BDCH,   8, 
                        BDVL,   8, 
                        BDVH,   8, 
                        BAVL,   8, 
                        BAVH,   8, 
                        BACL,   8, 
                        BACH,   8, 
                        RSCL,   8, 
                        RSCH,   8, 
                        BRCL,   8, 
                        BRCH,   8, 
                        FCCL,   8, 
                        FCCH,   8, 
                            ,   4, 
                        FDCH,   1, 
                        FUCH,   1, 
                        DCHG,   1, 
                        BTIT,   1, 
                        BSTH,   8, 
                        OMFL,   8, 
                        OMFH,   8, 
                        IBMF,   8, 
                        ASSR,   8, 
                                Offset (0x40), 
                        TS1R,   8, 
                        TS1L,   8, 
                        TS2R,   8, 
                        TS2L,   8, 
                        TS3R,   8, 
                        TS3L,   8, 
                        F1FL,   8, 
                        F1FH,   8, 
                        F2FL,   8, 
                        F2FH,   8, 
                        T1U1,   8, 
                        T1U2,   8, 
                        T1U3,   8, 
                        T1U4,   8, 
                        T1U5,   8, 
                        T1U6,   8, 
                        T1U7,   8, 
                        T1D1,   8, 
                        T1D2,   8, 
                        T1D3,   8, 
                        T1L1,   8, 
                        T2R1,   8, 
                        T2U1,   8, 
                        T3L1,   8, 
                        T3L2,   8, 
                                Offset (0x60), 
                        SMBN,   8, 
                        SPTR,   8, 
                        SSTS,   8, 
                        SADR,   8, 
                        SCMD,   8, 
                        SBFR,   256, 
                        SCNT,   8
                    }

                    Method (_REG, 2, NotSerialized)
                    {
                        If (LAnd (LEqual (Arg0, 0x03), LEqual (Arg1, One)))
                        {
                            Store (BATP, BNUM)
                            Store (RSCL, B0SC)
                            Store (RPWR, PWRS)
                            Notify (BAT0, 0x81)
                            PNOT ()
                            Store (Arg1, ECON)
                        }
                    }

                    Name (_GPE, 0x17)
                    Method (_Q21, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x21)
                        Store (RPWR, PWRS)
                        Notify (ADP1, 0x81)
                        Notify (BAT0, 0x80)
                        PNOT ()
                    }

                    Method (_Q22, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x22)
                        Store (RPWR, PWRS)
                        Notify (ADP1, 0x81)
                        Notify (BAT0, 0x80)
                        PNOT ()
                    }

                    Method (_Q23, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x23)
                        Store (RSCL, B0SC)
                        Store (BATP, BNUM)
                        Notify (BAT0, 0x81)
                    }

                    Method (_Q24, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x24)
                        Store (RSCL, B0SC)
                        Store (BATP, BNUM)
                        Notify (BAT0, 0x81)
                    }

                    Method (_Q25, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x25)
                        Store (RSCL, B0SC)
                        Notify (BAT0, 0x80)
                    }

                    Method (_Q26, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x26)
                        Notify (SNC, 0x90)
                    }

                    Method (_Q27, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x27)
                        Notify (SNC, 0x90)
                    }

                    Method (_Q28, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x28)
                        If (_OSI ("Windows 2006"))
                        {
                            If (LEqual (^^^PEGP.NGFX.NVID, 0xFFFF))
                            {
                                Notify (GFX0, 0x81)
                            }
                            Else
                            {
                                Notify (^^^PEGP.NGFX, 0x81)
                            }
                        }
                        Else
                        {
                            Notify (SNC, 0x91)
                        }
                    }

                    Method (_Q29, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x29)
                        Notify (LID0, 0x80)
                    }

                    Method (_Q2A, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x2A)
                        Notify (LID0, 0x80)
                    }

                    Method (_Q2B, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x2B)
                        Notify (SNC, 0x94)
                    }

                    Method (_Q2C, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x2C)
                        Notify (SNC, 0x94)
                    }

                    Method (_Q32, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x32)
                        Notify (PWRB, 0x80)
                    }

                    Method (_Q34, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x34)
                        Notify (\_TZ.TZ00, 0x80)
                        If (MPEN)
                        {
                            Notify (\_TZ.TZ01, 0x80)
                        }
                    }

                    Name (HF1P, 0x81)
                    Name (HF1R, One)
                    Name (HF5P, 0x85)
                    Name (HF5R, 0x05)
                    Name (HF6P, 0x86)
                    Name (HF6R, 0x06)
                    Name (HF7P, 0x87)
                    Name (HF7R, 0x07)
                    Name (HF8P, 0x88)
                    Name (HF8R, 0x08)
                    Name (HF9P, 0x89)
                    Name (HF9R, 0x09)
                    Name (HFAP, 0x8A)
                    Name (HFAR, 0x0A)
                    Name (HFBP, 0x8B)
                    Name (HFBR, 0x0B)
                    Name (HFCP, 0x8C)
                    Name (HFCR, 0x0C)
                    Name (HFDP, 0x8D)
                    Name (HFDR, 0x0D)
                    Name (HS1P, 0x90)
                    Name (HS1R, 0x10)
                    Name (HS2P, 0x91)
                    Name (HS2R, 0x11)
                    Name (HUPP, 0x95)
                    Name (HUPR, 0x15)
                    Name (HDWP, 0x96)
                    Name (HDWR, 0x16)
                    Name (HMUP, 0x97)
                    Name (HMUR, 0x17)
                    Name (HTRP, 0x99)
                    Name (HTRR, 0x19)
                    Name (HCUP, 0x9A)
                    Name (HCUR, 0x1A)
                    Name (HCDP, 0x9B)
                    Name (HCDR, 0x1B)
                    Name (HEJP, 0x9F)
                    Name (HEJR, 0x1F)
                    Name (HAVP, 0xA1)
                    Name (HAVR, 0x21)
                    Method (_Q50, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x50)
                        SECR (HF1P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q51, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x51)
                        SECR (HF1R)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q58, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x58)
                        SECR (HF5P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q59, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x59)
                        SECR (HF5R)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q5A, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x5A)
                        SECR (HF6P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q5B, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x5B)
                        SECR (HF6R)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q5C, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x5C)
                        SECR (HF7P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q5D, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x5D)
                        SECR (HF7R)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q5E, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x5E)
                        SECR (HF8P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q5F, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x5F)
                        SECR (HF8R)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q60, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x60)
                        SECR (HF9P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q61, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x61)
                        SECR (HF9R)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q62, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x62)
                        SECR (HFAP)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q63, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x63)
                        SECR (HFAR)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q64, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x64)
                        SECR (HFBP)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q65, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x65)
                        SECR (HFBR)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q66, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x66)
                        SECR (HFCP)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q67, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x67)
                        SECR (HFCR)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q68, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x68)
                        SECR (HFDP)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q69, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x69)
                        SECR (HFDR)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q7E, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x7E)
                        SECR (HAVP)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q7F, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x7F)
                        SECR (HAVR)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q82, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x82)
                        SECR (HS1P)
                        Notify (SNC, 0x92)
                    }

                    Method (_Q83, 0, NotSerialized)
                    {
                        P8XH (Zero, 0x83)
                        SECR (HS1R)
                        Notify (SNC, 0x92)
                    }

                    Method (SECR, 1, NotSerialized)
                    {
                        Store (Arg0, ^^SNC.XECR)
                    }

                    Method (GECR, 0, NotSerialized)
                    {
                        Return (^^SNC.XECR)
                    }
                }

                Device (DMAC)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IO (Decode16,
                            0x0081,             // Range Minimum
                            0x0081,             // Range Maximum
                            0x01,               // Alignment
                            0x11,               // Length
                            )
                        IO (Decode16,
                            0x0093,             // Range Minimum
                            0x0093,             // Range Maximum
                            0x01,               // Alignment
                            0x0D,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        DMA (Compatibility, NotBusMaster, Transfer8_16, )
                            {4}
                    })
                }

                Device (FWHD)
                {
                    Name (_HID, EisaId ("INT0800"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFF000000,         // Address Base
                            0x01000000,         // Address Length
                            )
                    })
                }

                Device (HPET)
                {
                    Name (_HID, EisaId ("PNP0103"))
                    Name (_CID, 0x010CD041)
                    Name (BUF0, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFED00000,         // Address Base
                            0x00000400,         // Address Length
                            _Y14)
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSYS, 0x07D1))
                        {
                            If (HPAE)
                            {
                                Return (0x0F)
                            }
                        }
                        Else
                        {
                            If (HPAE)
                            {
                                Return (0x0B)
                            }
                        }

                        Return (Zero)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        If (HPAE)
                        {
                            CreateDWordField (BUF0, \_SB.PCI0.LPCB.HPET._Y14._BAS, HPT0)
                            If (LEqual (HPAS, One))
                            {
                                Store (0xFED01000, HPT0)
                            }

                            If (LEqual (HPAS, 0x02))
                            {
                                Store (0xFED02000, HPT0)
                            }

                            If (LEqual (HPAS, 0x03))
                            {
                                Store (0xFED03000, HPT0)
                            }
                        }

                        Return (BUF0)
                    }
                }

                Device (IPIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0024,             // Range Minimum
                            0x0024,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0028,             // Range Minimum
                            0x0028,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x002C,             // Range Minimum
                            0x002C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0030,             // Range Minimum
                            0x0030,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0034,             // Range Minimum
                            0x0034,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0038,             // Range Minimum
                            0x0038,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x003C,             // Range Minimum
                            0x003C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A4,             // Range Minimum
                            0x00A4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A8,             // Range Minimum
                            0x00A8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00AC,             // Range Minimum
                            0x00AC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B0,             // Range Minimum
                            0x00B0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B4,             // Range Minimum
                            0x00B4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B8,             // Range Minimum
                            0x00B8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00BC,             // Range Minimum
                            0x00BC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x04D0,             // Range Minimum
                            0x04D0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (MATH)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Device (LDRC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x02)
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x002E,             // Range Minimum
                            0x002E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x004E,             // Range Minimum
                            0x004E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0063,             // Range Minimum
                            0x0063,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0065,             // Range Minimum
                            0x0065,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0067,             // Range Minimum
                            0x0067,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0080,             // Range Minimum
                            0x0080,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0092,             // Range Minimum
                            0x0092,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x00B2,             // Range Minimum
                            0x00B2,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0680,             // Range Minimum
                            0x0680,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IO (Decode16,
                            0x0800,             // Range Minimum
                            0x0800,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x1000,             // Range Minimum
                            0x1000,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                        IO (Decode16,
                            0x1180,             // Range Minimum
                            0x1180,             // Range Maximum
                            0x01,               // Alignment
                            0x40,               // Length
                            )
                        IO (Decode16,
                            0x1640,             // Range Minimum
                            0x1640,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0xFE00,             // Range Minimum
                            0xFE00,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                        IO (Decode16,
                            0xFE80,             // Range Minimum
                            0xFE80,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                    })
                }

                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                }

                Device (TIMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x01,               // Alignment
                            0x04,               // Length
                            )
                        IO (Decode16,
                            0x0050,             // Range Minimum
                            0x0050,             // Range Maximum
                            0x10,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {0}
                    })
                }

                Device (SNC)
                {
                    Name (_HID, EisaId ("SNY5001"))
                    Method (_INI, 0, NotSerialized)
                    {
                        If (_OSI ("Windows 2006"))
                        {
                            And (ENMK, 0xFFBF, ENMK)
                            And (SNIA, 0xFFFD, SNIA)
                            Or (SNIA, 0x40, SNIA)
                            If (And (SYID, 0x80)) {}
                            Else
                            {
                                Store (0x374A0100, SNI4)
                            }

                            Store (DETC, Local0)
                            PHSB (0xE1, Local0)
                        }
                    }

                    Method (PWAK, 0, NotSerialized)
                    {
                        Acquire (PLOK, 0xFFFF)
                        DBGC (0xF3, 0x80, BCEN)
                        Sleep (0x64)
                        Notify (\_PR.CPU0, 0x80)
                        Sleep (0x64)
                        DBGC (0xF3, 0x81, BCEN)
                        Release (PLOK)
                        Return (Zero)
                    }

                    Method (GWDP, 0, NotSerialized)
                    {
                        DBGC (0xF2, 0x80, BCEN)
                        DBGC (0xF2, 0x81, BCEN)
                        Return (ShiftRight (And (PHS (0xDD), 0x40), 0x06))
                    }

                    Name (EVS0, 0x07)
                    Name (EVS1, Zero)
                    Name (EVS2, Zero)
                    Mutex (MSNE, 0x00)
                    Method (GSNE, 1, NotSerialized)
                    {
                        DBGC (0xF1, 0x80, BCEN)
                        Store (ShiftRight (And (Arg0, 0xFF000000), 0x18), Local1)
                        Store (ShiftRight (And (Arg0, 0x00FF0000), 0x10), Local2)
                        Store (And (Arg0, 0xFFFF), Local3)
                        Acquire (MSNE, 0xFFFF)
                        Store (Zero, Local0)
                        If (LEqual (Local1, Zero))
                        {
                            If (LEqual (Local2, Zero))
                            {
                                Store (And (Arg0, 0xFFFF0000), Local0)
                                Store (Or (Local0, 0x07), Local0)
                            }

                            If (LEqual (Local2, One))
                            {
                                Store (And (Arg0, 0xFFFF0000), Local0)
                                Store (Or (Local0, Zero), Local0)
                            }

                            If (LEqual (Local2, 0x02))
                            {
                                Store (And (Arg0, 0xFFFF0000), Local0)
                                Store (Or (Local0, Zero), Local0)
                            }
                        }
                        Else
                        {
                            If (LEqual (Local1, One))
                            {
                                If (LEqual (Local2, Zero))
                                {
                                    Store (And (Arg0, 0xFFFF0000), Local0)
                                    Store (Or (Local0, EVS0), Local0)
                                }

                                If (LEqual (Local2, One))
                                {
                                    Store (And (Arg0, 0xFFFF0000), Local0)
                                    Store (Or (Local0, EVS1), Local0)
                                }

                                If (LEqual (Local2, 0x02))
                                {
                                    Store (And (Arg0, 0xFFFF0000), Local0)
                                    Store (Or (Local0, EVS2), Local0)
                                }
                            }
                            Else
                            {
                                Store (Ones, Local0)
                            }
                        }

                        Release (MSNE)
                        DBGC (0xF1, 0x81, BCEN)
                        Return (Local0)
                    }

                    Method (SSNE, 1, NotSerialized)
                    {
                        DBGC (0xF4, 0x80, BCEN)
                        Store (ShiftRight (And (Arg0, 0xFF000000), 0x18), Local1)
                        Store (ShiftRight (And (Arg0, 0x00FF0000), 0x10), Local2)
                        Store (And (Arg0, 0xFFFF), Local3)
                        Acquire (MSNE, 0xFFFF)
                        Store (Zero, Local0)
                        If (LEqual (Local1, Zero))
                        {
                            If (LEqual (Local2, Zero))
                            {
                                Store (Or (Arg0, EVS0), EVS0)
                            }

                            If (LEqual (Local2, One))
                            {
                                Store (Or (Arg0, EVS1), EVS1)
                            }

                            If (LEqual (Local2, 0x02))
                            {
                                Store (Or (Arg0, EVS2), EVS2)
                            }
                        }
                        Else
                        {
                            If (LEqual (Local1, One))
                            {
                                If (LEqual (Local2, Zero))
                                {
                                    Store (And (EVS0, Not (Arg0)), EVS0)
                                }

                                If (LEqual (Local2, One))
                                {
                                    Store (And (EVS1, Not (Arg0)), EVS1)
                                }

                                If (LEqual (Local2, 0x02))
                                {
                                    Store (And (EVS2, Not (Arg0)), EVS2)
                                }
                            }
                        }

                        DBGC (0xF4, 0x81, BCEN)
                        Release (MSNE)
                    }

                    Method (CSXB, 1, NotSerialized)
                    {
                        Acquire (MPHS, 0xFFFF)
                        DBGC (0xF5, 0x80, BCEN)
                        Store (Arg0, SXBF)
                        PHS0 (0xCC)
                        Store (SXBF, Local0)
                        DBGC (0xF5, 0x81, BCEN)
                        Release (MPHS)
                        Return (Local0)
                    }

                    Method (SODV, 1, NotSerialized)
                    {
                        DBGC (0xF6, 0x80, BCEN)
                        If (LNotEqual (DSEN, Zero))
                        {
                            Return (Ones)
                        }

                        Store (Arg0, AODV)
                        If (LNot (And (AODV, CADD)))
                        {
                            Store (One, AODV)
                        }

                        If (LNotEqual (CADD, PADD))
                        {
                            Store (CADD, PADD)
                            Notify (PCI0, Zero)
                            Notify (PEGP, Zero)
                            Sleep (0x02EE)
                        }

                        Notify (GFX0, 0x80)
                        Notify (^^^PEGP.NGFX, 0x80)
                        DBGC (0xF6, 0x81, BCEN)
                        Return (Zero)
                    }

                    Method (GDDI, 0, NotSerialized)
                    {
                        Store (PHS (0xC5), Local0)
                        Store (And (Local0, 0x0F), CADD)
                        Return (Local0)
                    }

                    Method (STCS, 1, NotSerialized)
                    {
                        If (LEqual (Arg0, Zero)) {}
                        If (LEqual (Arg0, One)) {}
                    }

                    Mutex (MIDB, 0x00)
                    Method (RBMF, 1, Serialized)
                    {
                        Acquire (MIDB, 0xFFFF)
                        DBGC (0xF7, 0x80, BCEN)
                        And (Arg0, 0x00010000, Local0)
                        Store (PHSD (0xDC, Local0), Local0)
                        If (LEqual (Local0, 0x02))
                        {
                            Sleep (0x1388)
                        }

                        DBGC (0xF7, 0x81, BCEN)
                        Release (MIDB)
                        Return (Local0)
                    }

                    Method (RSBI, 1, Serialized)
                    {
                        Return (Zero)
                    }

                    Method (CBMF, 1, Serialized)
                    {
                        Acquire (MIDB, 0xFFFF)
                        Or (And (Arg0, 0x0001FFFF), 0x02000000, Local0)
                        Store (PHSD (0xDC, Local0), Local0)
                        Release (MIDB)
                        Return (Zero)
                    }

                    Method (EAWK, 1, Serialized)
                    {
                        Acquire (MIDB, 0xFFFF)
                        PHSB (0xD3, Zero)
                        Not (Arg0, Local0)
                        Release (MIDB)
                        Return (Local0)
                    }

                    Name (SNI0, 0x53636E53)
                    Name (SNI1, 0x6F707075)
                    Name (SNI2, 0x64657472)
                    Name (SNI3, 0x0100)
                    Name (SNI4, 0x374A0000)
                    Name (SNIA, 0x40B7)
                    Name (SNDK, 0x2000)
                    Name (SNN0, 0x0101)
                    Name (SNN1, 0x0102)
                    Name (SNN2, 0x0100)
                    Name (XECR, Zero)
                    Name (SNN4, 0x010F)
                    Name (SNN5, 0x0106)
                    Name (SNN6, 0x0113)
                    Name (SNN7, 0x010A)
                    Name (LBSR, Zero)
                    Name (SNND, 0x010D)
                    Name (SNNE, 0x0105)
                    Name (IIR, 0x02)
                    Name (ENMK, 0xFFE8)
                    Name (ENCR, Zero)
                    Name (ESR, Zero)
                    Method (SN00, 1, NotSerialized)
                    {
                        Store (And (Arg0, 0xFF), Local1)
                        If (LEqual (Local1, Zero))
                        {
                            Return (SNI0)
                        }
                        Else
                        {
                            If (LEqual (Local1, One))
                            {
                                Return (SNI1)
                            }
                            Else
                            {
                                If (LEqual (Local1, 0x02))
                                {
                                    Return (SNI2)
                                }
                                Else
                                {
                                    If (LEqual (Local1, 0x03))
                                    {
                                        Return (SNI3)
                                    }
                                    Else
                                    {
                                        If (LEqual (Local1, 0x04))
                                        {
                                            Return (SNI4)
                                        }
                                        Else
                                        {
                                            If (LEqual (Local1, 0x10))
                                            {
                                                Store (SNAV (), Local2)
                                                Return (Local2)
                                            }
                                            Else
                                            {
                                                If (LAnd (LGreaterEqual (Local1, 0x20), LLessEqual (Local1, 0x2F)))
                                                {
                                                    Store (SNGN (Local1), Local2)
                                                    Return (Local2)
                                                }
                                                Else
                                                {
                                                    Return (Zero)
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }

                    Method (SN01, 0, NotSerialized)
                    {
                        Store (PHS (0xD6), Local1)
                        And (Local1, Not (ENMK), Local1)
                        And (ENCR, ENMK, Local2)
                        Or (Local1, Local2, Local1)
                        Return (Local1)
                    }

                    Mutex (SNM0, 0x00)
                    Method (SN02, 1, NotSerialized)
                    {
                        Store (Arg0, Local1)
                        If (LNotEqual (Local1, Zero))
                        {
                            Acquire (SNM0, 0xFFFF)
                            And (Local1, Not (ENMK), Local2)
                            If (LNotEqual (Local2, Zero))
                            {
                                PHSD (0xD7, Local2)
                            }

                            And (Local1, ENMK, Local2)
                            If (LNotEqual (Local2, Zero))
                            {
                                And (ENCR, ENMK, Local3)
                                Or (Local3, Local2, ENCR)
                            }

                            Release (SNM0)
                        }
                    }

                    Method (SN03, 1, NotSerialized)
                    {
                        Store (Arg0, Local1)
                        If (LNotEqual (Local1, Zero))
                        {
                            Acquire (SNM0, 0xFFFF)
                            And (Local1, Not (ENMK), Local2)
                            If (LNotEqual (Local2, Zero))
                            {
                                PHSD (0xD8, Local1)
                            }

                            And (Local1, ENMK, Local2)
                            If (LNotEqual (Local2, Zero))
                            {
                                And (ENCR, ENMK, Local3)
                                And (Local3, Not (Local2), ENCR)
                            }

                            Release (SNM0)
                        }
                    }

                    Method (SN04, 0, NotSerialized)
                    {
                        Store (^^EC.ESR0, Local1)
                        And (Local1, Not (ENMK), Local1)
                        And (ESR, ENMK, Local2)
                        Or (Local1, Local2, Local1)
                        Return (Local1)
                    }

                    Method (SN05, 1, NotSerialized)
                    {
                        Store (Arg0, Local1)
                        If (LNotEqual (Local1, Zero))
                        {
                            And (Local1, Not (ENMK), Local2)
                            If (LNotEqual (Local2, Zero))
                            {
                                PHSD (0xDA, Local1)
                            }

                            And (Local1, ENMK, Local2)
                            If (LNotEqual (Local2, Zero))
                            {
                                And (ESR, ENMK, Local3)
                                And (Local3, Not (Local2), ESR)
                            }
                        }
                    }

                    Mutex (SNM1, 0x00)
                    Name (SNBF, Buffer (0x0410) {})
                    CreateField (SNBF, Zero, 0x20, SNBD)
                    CreateField (SNBF, 0x20, 0x20, SND1)
                    CreateField (SNBF, 0x40, 0x08, SNB8)
                    CreateField (SNBF, 0x10, 0x40, SND8)
                    Method (SN06, 1, NotSerialized)
                    {
                        Store (Arg0, SNBF)
                        Return (SNCM ())
                    }

                    Method (SNCM, 0, NotSerialized)
                    {
                        Acquire (SNM1, 0xFFFF)
                        Store (DerefOf (Index (SNBF, Zero)), Local0)
                        And (Local0, 0x0F, Local0)
                        DBGC (0xF0, Local0, BCEN)
                        If (LEqual (Local0, Zero))
                        {
                            SNF0 (SNBF)
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                If (_OSI ("Windows 2006")) {}
                                Else
                                {
                                    SNF1 (SNBF)
                                }
                            }
                            Else
                            {
                                If (LEqual (Local0, 0x02))
                                {
                                    SNF2 (SNBF)
                                }
                                Else
                                {
                                    If (LEqual (Local0, 0x03))
                                    {
                                        SNF3 (SNBF)
                                    }
                                    Else
                                    {
                                        If (LEqual (Local0, 0x04))
                                        {
                                            SNF4 (SNBF)
                                        }
                                        Else
                                        {
                                            If (LEqual (Local0, 0x05))
                                            {
                                                SNF5 (SNBF)
                                            }
                                            Else
                                            {
                                                If (LEqual (Local0, 0x06))
                                                {
                                                    If (_OSI ("Windows 2006"))
                                                    {
                                                        SNF6 (SNBF)
                                                    }
                                                }
                                                Else
                                                {
                                                    If (LEqual (Local0, 0x07))
                                                    {
                                                        SNF7 (SNBF)
                                                    }
                                                    Else
                                                    {
                                                        If (LEqual (Local0, 0x0C))
                                                        {
                                                            SNFC (SNBF)
                                                        }
                                                        Else
                                                        {
                                                            If (LEqual (Local0, 0x0E))
                                                            {
                                                                SNFE (SNBF)
                                                            }
                                                            Else
                                                            {
                                                            }
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }

                        Release (SNM1)
                        Return (SNBF)
                    }

                    Method (SN07, 1, NotSerialized)
                    {
                        Store (Arg0, Local0)
                        Store (Local0, SNBD)
                        SNCM ()
                        Return (SNBD)
                    }

                    Method (SNF0, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (One, Local1)
                            PHSB (0xD0, Local1)
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (One, Local1)
                                PHSB (0xD1, Local1)
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x70, 0x81, BCEN)
                        Return (SNBF)
                    }

                    Method (SNF1, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (0x02, Local1)
                            PHSB (0xD0, Local1)
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (0x02, Local1)
                                PHSB (0xD1, Local1)
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x71, 0x81, BCEN)
                        Return (SNBF)
                    }

                    Method (SNF2, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (0x04, Local1)
                            PHSB (0xD0, Local1)
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (0x04, Local1)
                                PHSB (0xD1, Local1)
                            }
                            Else
                            {
                                If (LEqual (Local0, 0x02))
                                {
                                    Store (^^EC.GECR (), Local1)
                                    Store (Local1, Index (SNBF, Zero))
                                }
                                Else
                                {
                                }
                            }
                        }

                        DBGC (0x72, 0x81, BCEN)
                    }

                    Method (SNF3, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (PHS (0xDB), Local1)
                            And (Local1, One, Local1)
                            XOr (Local1, One, Local1)
                            Store (Local1, Index (SNBF, Zero))
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (DerefOf (Index (SNBF, 0x02)), Local1)
                                And (Local1, One, Local1)
                                XOr (Local1, One, Local1)
                                PHSB (0xCE, Local1)
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x73, 0x81, BCEN)
                    }

                    Method (SNF4, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (PHS (0xDD), Local1)
                            Store (And (Local1, One), Index (SNBF, Zero))
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (PHS (0xDD), Local1)
                                ShiftRight (And (Local1, 0x06), One, Local1)
                                Store (Local1, Index (SNBF, Zero))
                            }
                            Else
                            {
                                If (LEqual (Local0, 0x02))
                                {
                                    Store (DerefOf (Index (SNBF, 0x02)), Local1)
                                    And (Local1, 0x03, Local1)
                                    PHSD (0xDE, Local1)
                                }
                                Else
                                {
                                    If (LEqual (Local0, 0x03))
                                    {
                                        Store (PHS (0xDD), Local1)
                                        ShiftRight (And (Local1, 0x30), 0x04, Local1)
                                        Store (Local1, Index (SNBF, Zero))
                                    }
                                    Else
                                    {
                                        If (LEqual (Local0, 0x04))
                                        {
                                            Store (DerefOf (Index (SNBF, 0x02)), Local1)
                                            And (Local1, 0x03, Local1)
                                            PHSD (0xDF, Local1)
                                        }
                                        Else
                                        {
                                            If (LEqual (Local0, 0x07))
                                            {
                                                ShiftRight (And (Store (SN04 (), Local1), 0x10), 0x04, Local1)
                                                Store (Local1, Index (SNBF, Zero))
                                            }
                                            Else
                                            {
                                            }
                                        }
                                    }
                                }
                            }
                        }

                        DBGC (0x74, 0x81, BCEN)
                        Return (SNBF)
                    }

                    Method (SNF5, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (^^EC.ISID, Local1)
                            If (LEqual (Local1, 0x02))
                            {
                                Store (0x04, Local1)
                            }
                            Else
                            {
                                Store (Zero, Local1)
                            }

                            Store (Local1, Index (SNBF, Zero))
                        }
                        Else
                        {
                        }

                        DBGC (0x75, 0x81, BCEN)
                    }

                    Method (SNF6, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (One, Index (SNBF, Zero))
                        }

                        If (LEqual (Local0, One))
                        {
                            Store (DETC, Index (SNBF, Zero))
                        }

                        If (LEqual (Local0, 0x02))
                        {
                            Store (DerefOf (Index (SNBF, 0x02)), Local0)
                            If (LNotEqual (DETC, Local0))
                            {
                                PHSB (0xE0, Local0)
                            }

                            Store (DETC, Local0)
                            PHSB (0xE1, Local0)
                        }

                        DBGC (0x76, 0x81, BCEN)
                        Return (SNBF)
                    }

                    Method (SNF7, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Acquire (MPHS, 0xFFFF)
                            Store (SND8, Local1)
                            Store (PHDD (0xE2, Local1), SND8)
                            DBGC (0x77, 0x81, BCEN)
                            Release (MPHS)
                        }
                    }

                    Method (SNFC, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Not (GP21, Local1)
                            And (Local1, One, Local1)
                            Store (Local1, LBSR)
                            Store (Local1, Index (SNBF, Zero))
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (DerefOf (Index (SNBF, 0x02)), Local2)
                                And (Local2, One, Local2)
                                Store (Local2, LBSR)
                                Not (Local2, Local1)
                                And (Local1, One, Local1)
                                Store (Local1, GP21)
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x7C, 0x81, BCEN)
                    }

                    Method (SNFD, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (GP02, Local1)
                            And (Local1, One, Local1)
                            Store (Local1, Index (SNBF, Zero))
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (DerefOf (Index (SNBF, 0x02)), Local2)
                                And (Local2, One, Local2)
                                Store (Local2, GP02)
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x7D, 0x81, BCEN)
                    }

                    Method (SNFE, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (PHS (0xC7), Local1)
                            And (Local1, 0xFF, Local1)
                            If (LEqual (Local1, 0xFE))
                            {
                                Store (One, Local1)
                            }
                            Else
                            {
                                Store (Zero, Local1)
                            }

                            Store (Local1, Index (SNBF, Zero))
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (DerefOf (Index (SNBF, 0x02)), Local2)
                                And (Local2, One, Local2)
                                If (LEqual (Local2, Zero))
                                {
                                    Store (0xA0, Local3)
                                }
                                Else
                                {
                                    Store (0xA1, Local3)
                                }

                                PHSB (0xC8, Local3)
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x7E, 0x81, BCEN)
                    }

                    Method (SNFF, 1, NotSerialized)
                    {
                        Store (DerefOf (Index (SNBF, One)), Local0)
                        If (LEqual (Local0, Zero))
                        {
                            Store (PHSD (0xC9, 0xFF), Local1)
                            If (LEqual (Local1, Zero))
                            {
                                Store (Zero, SNBD)
                            }
                            Else
                            {
                                Store (IIR, SNBD)
                            }
                        }
                        Else
                        {
                            If (LEqual (Local0, One))
                            {
                                Store (DerefOf (Index (SNBF, 0x02)), Local2)
                                If (LEqual (Local2, One))
                                {
                                    Acquire (MPHS, 0xFFFF)
                                    Store (PHSD (0xC9, Zero), Local1)
                                    Store (Local1, SNBD)
                                    Store (PHSD (0xC9, One), Local1)
                                    Store (Local1, SND1)
                                    Store (PHSD (0xC9, 0x02), Local1)
                                    Store (Local1, SNB8)
                                    Release (MPHS)
                                }
                            }
                            Else
                            {
                            }
                        }

                        DBGC (0x7F, 0x81, BCEN)
                    }

                    Method (SNAV, 0, NotSerialized)
                    {
                        Store (PHS (0xD2), Local0)
                        If (Local0)
                        {
                            Store (SNIA, Local1)
                        }
                        Else
                        {
                            And (SNIA, Not (SNDK), Local1)
                        }

                        Return (Local1)
                    }

                    Method (SNGN, 1, NotSerialized)
                    {
                        Store (And (Arg0, 0x0F), Local1)
                        If (LEqual (Local1, Zero))
                        {
                            Return (SNN0)
                        }
                        Else
                        {
                            If (LEqual (Local1, One))
                            {
                                If (_OSI ("Windows 2006"))
                                {
                                    Return (Zero)
                                }

                                Return (SNN1)
                            }
                            Else
                            {
                                If (LEqual (Local1, 0x02))
                                {
                                    Return (SNN2)
                                }
                                Else
                                {
                                    If (LEqual (Local1, 0x04))
                                    {
                                        Return (SNN4)
                                    }
                                    Else
                                    {
                                        If (LEqual (Local1, 0x05))
                                        {
                                            Return (SNN5)
                                        }
                                        Else
                                        {
                                            If (LEqual (Local1, 0x06))
                                            {
                                                If (_OSI ("Windows 2006"))
                                                {
                                                    Return (SNN6)
                                                }

                                                Return (Zero)
                                            }
                                            Else
                                            {
                                                If (LEqual (Local1, 0x07))
                                                {
                                                    Return (SNN7)
                                                }
                                                Else
                                                {
                                                    If (LEqual (Local1, 0x0E))
                                                    {
                                                        Return (SNNE)
                                                    }
                                                    Else
                                                    {
                                                        Return (Zero)
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }

                Device (PS2K)
                {
                    Name (_HID, EisaId ("PNP0303"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {1}
                    })
                }

                Device (PS2M)
                {
                    Name (_HID, EisaId ("SNY9001"))
                    Name (_CID, 0x130FD041)
                    Name (_CRS, ResourceTemplate ()
                    {
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {12}
                    })
                }
            }

            Device (PATA)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x69, One, BCEN)
                    Return (0x001F0001)
                }

                OperationRegion (PACS, PCI_Config, 0x40, 0xC0)
                Field (PACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                            Offset (0x04), 
                    PSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4
                }

                Device (PRID)
                {
                    Name (_ADR, Zero)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Name (PBUF, Buffer (0x14)
                        {
                            /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0008 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0010 */    0x00, 0x00, 0x00, 0x00
                        })
                        CreateDWordField (PBUF, Zero, PIO0)
                        CreateDWordField (PBUF, 0x04, DMA0)
                        CreateDWordField (PBUF, 0x08, PIO1)
                        CreateDWordField (PBUF, 0x0C, DMA1)
                        CreateDWordField (PBUF, 0x10, FLAG)
                        Store (GETP (PRIT), PIO0)
                        Store (GDMA (And (SYNC, One), And (ICR3, One), 
                            And (ICR0, One), SDT0, And (ICR1, One)), DMA0)
                        If (LEqual (DMA0, 0xFFFFFFFF))
                        {
                            Store (PIO0, DMA0)
                        }

                        If (And (PRIT, 0x4000))
                        {
                            If (LEqual (And (PRIT, 0x90), 0x80))
                            {
                                Store (0x0384, PIO1)
                            }
                            Else
                            {
                                Store (GETT (PSIT), PIO1)
                            }
                        }
                        Else
                        {
                            Store (0xFFFFFFFF, PIO1)
                        }

                        Store (GDMA (And (SYNC, 0x02), And (ICR3, 0x02), 
                            And (ICR0, 0x02), SDT1, And (ICR1, 0x02)), DMA1)
                        If (LEqual (DMA1, 0xFFFFFFFF))
                        {
                            Store (PIO1, DMA1)
                        }

                        Store (GETF (And (SYNC, One), And (SYNC, 0x02), 
                            PRIT), FLAG)
                        If (And (LEqual (PIO0, 0xFFFFFFFF), LEqual (DMA0, 0xFFFFFFFF)))
                        {
                            Store (0x78, PIO0)
                            Store (0x14, DMA0)
                            Store (0x03, FLAG)
                        }

                        Return (PBUF)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        CreateDWordField (Arg0, Zero, PIO0)
                        CreateDWordField (Arg0, 0x04, DMA0)
                        CreateDWordField (Arg0, 0x08, PIO1)
                        CreateDWordField (Arg0, 0x0C, DMA1)
                        CreateDWordField (Arg0, 0x10, FLAG)
                        If (LEqual (SizeOf (Arg1), 0x0200))
                        {
                            And (PRIT, 0xC0F0, PRIT)
                            And (SYNC, 0x02, SYNC)
                            Store (Zero, SDT0)
                            And (ICR0, 0x02, ICR0)
                            And (ICR1, 0x02, ICR1)
                            And (ICR3, 0x02, ICR3)
                            And (ICR5, 0x02, ICR5)
                            CreateWordField (Arg1, 0x62, W490)
                            CreateWordField (Arg1, 0x6A, W530)
                            CreateWordField (Arg1, 0x7E, W630)
                            CreateWordField (Arg1, 0x80, W640)
                            CreateWordField (Arg1, 0xB0, W880)
                            CreateWordField (Arg1, 0xBA, W930)
                            Or (PRIT, 0x8004, PRIT)
                            If (LAnd (And (FLAG, 0x02), And (W490, 0x0800)))
                            {
                                Or (PRIT, 0x02, PRIT)
                            }

                            Or (PRIT, SETP (PIO0, W530, W640), PRIT)
                            If (And (FLAG, One))
                            {
                                Or (SYNC, One, SYNC)
                                Store (SDMA (DMA0), SDT0)
                                If (LLess (DMA0, 0x1E))
                                {
                                    Or (ICR3, One, ICR3)
                                }

                                If (LLess (DMA0, 0x3C))
                                {
                                    Or (ICR0, One, ICR0)
                                }

                                If (And (W930, 0x2000))
                                {
                                    Or (ICR1, One, ICR1)
                                }
                            }
                        }

                        If (LEqual (SizeOf (Arg2), 0x0200))
                        {
                            And (PRIT, 0xBF0F, PRIT)
                            Store (Zero, PSIT)
                            And (SYNC, One, SYNC)
                            Store (Zero, SDT1)
                            And (ICR0, One, ICR0)
                            And (ICR1, One, ICR1)
                            And (ICR3, One, ICR3)
                            And (ICR5, One, ICR5)
                            CreateWordField (Arg2, 0x62, W491)
                            CreateWordField (Arg2, 0x6A, W531)
                            CreateWordField (Arg2, 0x7E, W631)
                            CreateWordField (Arg2, 0x80, W641)
                            CreateWordField (Arg2, 0xB0, W881)
                            CreateWordField (Arg2, 0xBA, W931)
                            Or (PRIT, 0x8040, PRIT)
                            If (LAnd (And (FLAG, 0x08), And (W491, 0x0800)))
                            {
                                Or (PRIT, 0x20, PRIT)
                            }

                            If (And (FLAG, 0x10))
                            {
                                Or (PRIT, 0x4000, PRIT)
                                If (LGreater (PIO1, 0xF0))
                                {
                                    Or (PRIT, 0x80, PRIT)
                                }
                                Else
                                {
                                    Or (PRIT, 0x10, PRIT)
                                    Store (SETT (PIO1, W531, W641), PSIT)
                                }
                            }

                            If (And (FLAG, 0x04))
                            {
                                Or (SYNC, 0x02, SYNC)
                                Store (SDMA (DMA1), SDT1)
                                If (LLess (DMA1, 0x1E))
                                {
                                    Or (ICR3, 0x02, ICR3)
                                }

                                If (LLess (DMA1, 0x3C))
                                {
                                    Or (ICR0, 0x02, ICR0)
                                }

                                If (And (W931, 0x2000))
                                {
                                    Or (ICR1, 0x02, ICR1)
                                }
                            }
                        }
                    }

                    Device (P_D0)
                    {
                        Name (_ADR, Zero)
                        Method (_RMV, 0, NotSerialized)
                        {
                            Return (Zero)
                        }

                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB0, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                            })
                            CreateByteField (PIB0, One, PMD0)
                            CreateByteField (PIB0, 0x08, DMD0)
                            If (And (PRIT, 0x02))
                            {
                                If (LEqual (And (PRIT, 0x09), 0x08))
                                {
                                    Store (0x08, PMD0)
                                }
                                Else
                                {
                                    Store (0x0A, PMD0)
                                    ShiftRight (And (PRIT, 0x0300), 0x08, Local0)
                                    ShiftRight (And (PRIT, 0x3000), 0x0C, Local1)
                                    Add (Local0, Local1, Local2)
                                    If (LEqual (0x03, Local2))
                                    {
                                        Store (0x0B, PMD0)
                                    }

                                    If (LEqual (0x05, Local2))
                                    {
                                        Store (0x0C, PMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Store (One, PMD0)
                            }

                            If (And (SYNC, One))
                            {
                                Store (Or (SDT0, 0x40), DMD0)
                                If (And (ICR1, One))
                                {
                                    If (And (ICR0, One))
                                    {
                                        Add (DMD0, 0x02, DMD0)
                                    }

                                    If (And (ICR3, One))
                                    {
                                        Store (0x45, DMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD0, 0x07), 0x02), 0x20, DMD0)
                            }

                            Return (PIB0)
                        }
                    }

                    Device (P_D1)
                    {
                        Name (_ADR, One)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB1, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                            })
                            CreateByteField (PIB1, One, PMD1)
                            CreateByteField (PIB1, 0x08, DMD1)
                            If (And (PRIT, 0x20))
                            {
                                If (LEqual (And (PRIT, 0x90), 0x80))
                                {
                                    Store (0x08, PMD1)
                                }
                                Else
                                {
                                    Add (And (PSIT, 0x03), ShiftRight (And (PSIT, 0x0C), 
                                        0x02), Local0)
                                    If (LEqual (0x05, Local0))
                                    {
                                        Store (0x0C, PMD1)
                                    }
                                    Else
                                    {
                                        If (LEqual (0x03, Local0))
                                        {
                                            Store (0x0B, PMD1)
                                        }
                                        Else
                                        {
                                            Store (0x0A, PMD1)
                                        }
                                    }
                                }
                            }
                            Else
                            {
                                Store (One, PMD1)
                            }

                            If (And (SYNC, 0x02))
                            {
                                Store (Or (SDT1, 0x40), DMD1)
                                If (And (ICR1, 0x02))
                                {
                                    If (And (ICR0, 0x02))
                                    {
                                        Add (DMD1, 0x02, DMD1)
                                    }

                                    If (And (ICR3, 0x02))
                                    {
                                        Store (0x45, DMD1)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD1, 0x07), 0x02), 0x20, DMD1)
                            }

                            Return (PIB1)
                        }
                    }
                }
            }

            Device (SATA)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x69, 0x02, BCEN)
                    Return (0x001F0002)
                }

                OperationRegion (SACS, PCI_Config, 0x40, 0xC0)
                Field (SACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                    SECT,   16, 
                    PSIT,   4, 
                    SSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x0B), 
                    SDT2,   2, 
                        ,   2, 
                    SDT3,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4, 
                            Offset (0x50), 
                    MAPV,   2
                }
            }

            Device (SBUS)
            {
                Method (_ADR, 0, Serialized)
                {
                    DBGC (0x69, 0x03, BCEN)
                    Return (0x001F0003)
                }
            }
        }
    }
}

```

and here are the errors i get when trying to recompile:
```

iasl -tc dsdt.dsl
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

ACPI Error (nsaccess-0531): ACPI path has too many parent prefixes (^) - reached beyond root node [20061109]

Maximum error count (200) exceeded
dsdt.dsl    23:     External (^CPU0._PPC)
Error    4014 -  From ACPI CA Subsystem ^  (AE_NOT_FOUND Failure from lookup %s
)

dsdt.dsl    25:     OperationRegion (SMI0, SystemMemory, 0x7FEE2B38, 0x00000415)
Error    4062 -   Object does not exist ^  (SMI0)

dsdt.dsl    26:     Field (SMI0, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI0)

dsdt.dsl    28:         BCMD,   8, 
Error    4062 -            ^ Object does not exist (BCMD)

dsdt.dsl    29:         DID,    32, 
Error    4062 -           ^ Object does not exist (DID_)

dsdt.dsl    30:         INFO,   4096
Error    4062 -            ^ Object does not exist (INFO)

dsdt.dsl    33:     Field (SMI0, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI0)

dsdt.dsl    36:         INFB,   8
Error    4062 -            ^ Object does not exist (INFB)

dsdt.dsl    39:     Field (SMI0, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI0)

dsdt.dsl    42:         INFD,   32
Error    4062 -            ^ Object does not exist (INFD)

dsdt.dsl    45:     Field (SMI0, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI0)

dsdt.dsl    48:         INDD,   64
Error    4062 -            ^ Object does not exist (INDD)

dsdt.dsl    51:     Field (SMI0, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI0)

dsdt.dsl    54:         SXBF,   8320
Error    4062 -            ^ Object does not exist (SXBF)

dsdt.dsl    57:     Field (SMI0, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI0)

dsdt.dsl    60:         INF1,   8, 
Error    4062 -            ^ Object does not exist (INF1)

dsdt.dsl    61:         INF2,   8
Error    4062 -            ^ Object does not exist (INF2)

dsdt.dsl    64:     OperationRegion (SMI1, SystemIO, 0x0000FE00, 0x00000002)
Error    4062 -   Object does not exist ^  (SMI1)

dsdt.dsl    65:     Field (SMI1, AnyAcc, NoLock, Preserve)
Error    4062 -               ^ Object does not exist (SMI1)

dsdt.dsl    67:         SMIC,   8
Error    4062 -            ^ Object does not exist (SMIC)

dsdt.dsl    70:     Mutex (MPHS, 0x00)
Error    4062 -               ^ Object does not exist (MPHS)

dsdt.dsl    71:     Method (PHS0, 1, NotSerialized)
Error    4062 -                ^ Object does not exist (PHS0)

dsdt.dsl    73:         Store (Arg0, BCMD)
Error    4062 -   Object does not exist ^  (BCMD)

dsdt.dsl    74:         Store (Zero, SMIC)
Error    4062 -   Object does not exist ^  (SMIC)

dsdt.dsl    75:         While (LEqual (BCMD, Arg0)) {}
Error    4062 -     Object does not exist ^  (BCMD)

dsdt.dsl    76:         Store (Zero, BCMD)
Error    4062 -   Object does not exist ^  (BCMD)

dsdt.dsl    79:     Method (PHS, 1, Serialized)
Error    4062 -               ^ Object does not exist (PHS_)

dsdt.dsl    81:         Acquire (MPHS, 0xFFFF)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl    82:         Store (Zero, DID)
Error    4062 -  Object does not exist ^  (DID_)

dsdt.dsl    83:         PHS0 (Arg0)
Error    4062 -            ^ Object does not exist (PHS0)

dsdt.dsl    84:         Store (INFD, Local0)
Error    4062 -                   ^ Object does not exist (INFD)

dsdt.dsl    85:         Release (MPHS)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl    89:     Method (PHSD, 2, Serialized)
Error    4062 -                ^ Object does not exist (PHSD)

dsdt.dsl    91:         Acquire (MPHS, 0xFFFF)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl    92:         Store (Zero, DID)
Error    4062 -  Object does not exist ^  (DID_)

dsdt.dsl    93:         Store (Arg1, INFD)
Error    4062 -   Object does not exist ^  (INFD)

dsdt.dsl    94:         PHS0 (Arg0)
Error    4062 -            ^ Object does not exist (PHS0)

dsdt.dsl    95:         Store (INFD, Local0)
Error    4062 -                   ^ Object does not exist (INFD)

dsdt.dsl    96:         Release (MPHS)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   100:     Method (PHDD, 2, Serialized)
Error    4062 -                ^ Object does not exist (PHDD)

dsdt.dsl   102:         Acquire (MPHS, 0xFFFF)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   103:         Store (Zero, DID)
Error    4062 -  Object does not exist ^  (DID_)

dsdt.dsl   104:         Store (Arg1, INDD)
Error    4062 -   Object does not exist ^  (INDD)

dsdt.dsl   105:         PHS0 (Arg0)
Error    4062 -            ^ Object does not exist (PHS0)

dsdt.dsl   106:         Store (INDD, Local0)
Error    4062 -                   ^ Object does not exist (INDD)

dsdt.dsl   107:         Release (MPHS)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   111:     Method (PHSW, 3, Serialized)
Error    4062 -                ^ Object does not exist (PHSW)

dsdt.dsl   113:         Acquire (MPHS, 0xFFFF)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   114:         Store (Zero, DID)
Error    4062 -  Object does not exist ^  (DID_)

dsdt.dsl   115:         Store (Arg1, INF1)
Error    4062 -   Object does not exist ^  (INF1)

dsdt.dsl   116:         Store (Arg2, INF2)
Error    4062 -   Object does not exist ^  (INF2)

dsdt.dsl   117:         PHS0 (Arg0)
Error    4062 -            ^ Object does not exist (PHS0)

dsdt.dsl   118:         Store (INFB, Local0)
Error    4062 -                   ^ Object does not exist (INFB)

dsdt.dsl   119:         Release (MPHS)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   123:     Method (PHSB, 2, Serialized)
Error    4062 -                ^ Object does not exist (PHSB)

dsdt.dsl   125:         Acquire (MPHS, 0xFFFF)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   126:         Store (Zero, DID)
Error    4062 -  Object does not exist ^  (DID_)

dsdt.dsl   127:         Store (Arg1, INFB)
Error    4062 -   Object does not exist ^  (INFB)

dsdt.dsl   128:         PHS0 (Arg0)
Error    4062 -            ^ Object does not exist (PHS0)

dsdt.dsl   129:         Store (INFB, Local0)
Error    4062 -                   ^ Object does not exist (INFB)

dsdt.dsl   130:         Release (MPHS)
Error    4062 -                     ^ Object does not exist (MPHS)

dsdt.dsl   134:     Mutex (MUTX, 0x00)
Error    4062 -               ^ Object does not exist (MUTX)

dsdt.dsl   135:     OperationRegion (PRT0, SystemIO, 0x80, 0x04)
Error    4062 -   Object does not exist ^  (PRT0)

dsdt.dsl   136:     Field (PRT0, DWordAcc, Lock, Preserve)
Error    4062 -               ^ Object does not exist (PRT0)

dsdt.dsl   138:         P80H,   32
Error    4062 -            ^ Object does not exist (P80H)

dsdt.dsl   141:     Method (P8XH, 2, Serialized)
Error    4062 -                ^ Object does not exist (P8XH)

dsdt.dsl   145:             Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
Error    4062 -          Object does not exist ^  (P80D)

dsdt.dsl   145:             Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
Error    4062 -                                    Object does not exist ^  (P80D)

dsdt.dsl   150:             Store (Or (And (P80D, 0xFFFF00FF), ShiftLeft (Arg1, 0x08)
Error    4062 -          Object does not exist ^  (P80D)

dsdt.dsl   151:                 ), P80D)
Error    4062 - Object does not exist ^  (P80D)

dsdt.dsl   156:             Store (Or (And (P80D, 0xFF00FFFF), ShiftLeft (Arg1, 0x10)
Error    4062 -          Object does not exist ^  (P80D)

dsdt.dsl   157:                 ), P80D)
Error    4062 - Object does not exist ^  (P80D)

dsdt.dsl   162:             Store (Or (And (P80D, 0x00FFFFFF), ShiftLeft (Arg1, 0x18)
Error    4062 -          Object does not exist ^  (P80D)

dsdt.dsl   163:                 ), P80D)
Error    4062 - Object does not exist ^  (P80D)

dsdt.dsl   166:         Store (P80D, P80H)
Error    4062 -                   ^ Object does not exist (P80D)

dsdt.dsl   166:         Store (P80D, P80H)
Error    4062 -   Object does not exist ^  (P80H)

dsdt.dsl   169:     Method (_PIC, 1, NotSerialized)
Error    4062 -                ^ Object does not exist (_PIC)

dsdt.dsl   171:         Store (Arg0, GPIC)
Error    4062 -   Object does not exist ^  (GPIC)

dsdt.dsl   174:     Method (_PTS, 1, NotSerialized)
Error    4062 -                ^ Object does not exist (_PTS)

dsdt.dsl   177:         DBGC (Local0, 0x80, BCEN)
Error    4062 -            ^ Object does not exist (DBGC)

dsdt.dsl   177:         DBGC (Local0, 0x80, BCEN)
Error    4062 -          Object does not exist ^  (BCEN)

dsdt.dsl   178:         Store (Zero, P80D)
Error    4062 -   Object does not exist ^  (P80D)

dsdt.dsl   179:         P8XH (Zero, Arg0)
Error    4062 -            ^ Object does not exist (P8XH)

dsdt.dsl   180:         Store (Arg0, PRM0)
Error    4062 -   Object does not exist ^  (PRM0)

dsdt.dsl   181:         Store (0x51, SMIF)
Error    4062 -   Object does not exist ^  (SMIF)

dsdt.dsl   182:         Store (Zero, TRP0)
Error    4062 -   Object does not exist ^  (TRP0)

dsdt.dsl   183:         TRAP (0x50)
Error    4062 -            ^ Object does not exist (TRAP)

dsdt.dsl   185:         DBGC (Local0, 0x81, BCEN)
Error    4062 -            ^ Object does not exist (DBGC)

dsdt.dsl   185:         DBGC (Local0, 0x81, BCEN)
Error    4062 -          Object does not exist ^  (BCEN)

dsdt.dsl   188:     Method (_WAK, 1, NotSerialized)
Error    4062 -                ^ Object does not exist (_WAK)

dsdt.dsl   191:         DBGC (Local0, 0x80, BCEN)
Error    4062 -            ^ Object does not exist (DBGC)

dsdt.dsl   191:         DBGC (Local0, 0x80, BCEN)
Error    4062 -          Object does not exist ^  (BCEN)

dsdt.dsl   192:         P8XH (One, 0xAB)
Error    4062 -            ^ Object does not exist (P8XH)

dsdt.dsl   193:         Store (Arg0, PRM0)
Error    4062 -   Object does not exist ^  (PRM0)

dsdt.dsl   194:         Store (0x52, SMIF)
Error    4062 -   Object does not exist ^  (SMIF)

dsdt.dsl   195:         Store (Zero, TRP0)
Error    4062 -   Object does not exist ^  (TRP0)

dsdt.dsl   200:                 If (LAnd (And (CFGD, 0xF0), LEqual (OSYS, 0x07D1)))
Error    4062 -                                  Object does not exist ^  (OSYS)

dsdt.dsl   202:                     TRAP (0x3D)
Error    4062 -  Object does not exist ^  (TRAP)

dsdt.dsl   207:         If (LEqual (RP1D, Zero))
Error    4062 -  Object does not exist ^  (RP1D)

dsdt.dsl   209:             Notify (\_SB.PCI0.RP01, Zero)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.RP01)

dsdt.dsl   212:         If (LEqual (RP2D, Zero))
Error    4062 -  Object does not exist ^  (RP2D)

dsdt.dsl   214:             Notify (\_SB.PCI0.RP02, Zero)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.RP02)

dsdt.dsl   217:         If (LEqual (RP3D, Zero))
Error    4062 -  Object does not exist ^  (RP3D)

dsdt.dsl   219:             Notify (\_SB.PCI0.RP03, Zero)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.RP03)

dsdt.dsl   222:         If (LEqual (RP5D, Zero))
Error    4062 -  Object does not exist ^  (RP5D)

dsdt.dsl   224:             Notify (\_SB.PCI0.RP05, Zero)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.RP05)

dsdt.dsl   229:             If (LEqual (Zero, ACTT)) {}
Error    4062 -            Object does not exist ^  (ACTT)

dsdt.dsl   234:             Store (DETC, Local0)
Error    4062 - Object does not exist ^  (DETC)

dsdt.dsl   235:             PHSB (0xE1, Local0)
Error    4062 -                ^ Object does not exist (PHSB)

dsdt.dsl   238:         Store (\_SB.PCI0.LPCB.EC.RPWR, PWRS)
Error    4062 -               Object does not exist ^  (\_SB.PCI0.LPCB.EC.RPWR)

dsdt.dsl   238:         Store (\_SB.PCI0.LPCB.EC.RPWR, PWRS)
Error    4062 -                     Object does not exist ^  (PWRS)

dsdt.dsl   239:         Store (\_SB.PCI0.LPCB.EC.RSCL, B0SC)
Error    4062 -               Object does not exist ^  (\_SB.PCI0.LPCB.EC.RSCL)

dsdt.dsl   239:         Store (\_SB.PCI0.LPCB.EC.RSCL, B0SC)
Error    4062 -                     Object does not exist ^  (B0SC)

dsdt.dsl   240:         Store (\_SB.PCI0.LPCB.EC.BATP, BNUM)
Error    4062 -               Object does not exist ^  (\_SB.PCI0.LPCB.EC.BATP)

dsdt.dsl   240:         Store (\_SB.PCI0.LPCB.EC.BATP, BNUM)
Error    4062 -                     Object does not exist ^  (BNUM)

dsdt.dsl   241:         Notify (\_SB.BAT0, 0x80)
Error    4062 -   Object does not exist ^  (\_SB.BAT0)

dsdt.dsl   242:         Notify (\_SB.BAT0, 0x81)
Error    4062 -   Object does not exist ^  (\_SB.BAT0)

dsdt.dsl   245:             Store (CM72, Local0)
Error    4062 - Object does not exist ^  (CM72)

dsdt.dsl   246:             Store (Zero, CM72)
Error    4062 -       Object does not exist ^  (CM72)

dsdt.dsl   249:                 Notify (\_SB.PWRB, 0x02)
Error    4062 -           Object does not exist ^  (\_SB.PWRB)

dsdt.dsl   254:             If (And (PMST, One))
Error    4062 -   Object does not exist ^  (PMST)

dsdt.dsl   256:                 Notify (\_SB.PWRB, 0x02)
Error    4062 -           Object does not exist ^  (\_SB.PWRB)

dsdt.dsl   260:         \_PR.RPPC ()
Error    4062 -                 ^ Object does not exist (\_PR.RPPC)

dsdt.dsl   261:         P8XH (Zero, 0xCD)
Error    4062 -            ^ Object does not exist (P8XH)

dsdt.dsl   263:         DBGC (Local0, 0x81, BCEN)
Error    4062 -            ^ Object does not exist (DBGC)

dsdt.dsl   263:         DBGC (Local0, 0x81, BCEN)
Error    4062 -          Object does not exist ^  (BCEN)

dsdt.dsl   271:     Method (GETB, 3, Serialized)
Error    4062 -                ^ Object does not exist (GETB)

dsdt.dsl   275:         CreateField (Arg2, Local0, Local1, TBF3)
Error    4062 -   Object does not exist ^  (TBF3)

dsdt.dsl   276:         Return (TBF3)
Error    4062 -                    ^ Object does not exist (TBF3)

dsdt.dsl   279:     Method (PNOT, 0, Serialized)
Error    4062 -                ^ Object does not exist (PNOT)

dsdt.dsl   281:         If (MPEN)
Error    4062 -                ^ Object does not exist (MPEN)

dsdt.dsl   285:                 Notify (\_PR.CPU0, 0x80)
Error    4062 -           Object does not exist ^  (\_PR.CPU0)

dsdt.dsl   289:                     Notify (\_PR.CPU0, 0x81)
Error    4062 -               Object does not exist ^  (\_PR.CPU0)

dsdt.dsl   295:                 Notify (\_PR.CPU1, 0x80)
Error    4062 -           Object does not exist ^  (\_PR.CPU1)

dsdt.dsl   299:                     Notify (\_PR.CPU1, 0x81)
Error    4062 -               Object does not exist ^  (\_PR.CPU1)

dsdt.dsl   305:             Notify (\_PR.CPU0, 0x80)
Error    4062 -       Object does not exist ^  (\_PR.CPU0)

dsdt.dsl   307:             Notify (\_PR.CPU0, 0x81)
Error    4062 -       Object does not exist ^  (\_PR.CPU0)

dsdt.dsl   311:     Method (TRAP, 1, Serialized)
Error    4062 -                ^ Object does not exist (TRAP)

dsdt.dsl   313:         Store (Arg0, SMIF)
Error    4062 -   Object does not exist ^  (SMIF)

dsdt.dsl   314:         Store (Zero, TRP0)
Error    4062 -   Object does not exist ^  (TRP0)

dsdt.dsl   315:         Return (SMIF)
Error    4062 -                    ^ Object does not exist (SMIF)

dsdt.dsl   320:         Method (_INI, 0, NotSerialized)
Error    4062 -                    ^ Object does not exist (_INI)

dsdt.dsl   322:             Store (0x07D0, OSYS)
Error    4062 -         Object does not exist ^  (OSYS)

dsdt.dsl   327:                     Store (One, LINX)
Error    4062 -              Object does not exist ^  (LINX)

dsdt.dsl   332:                     Store (0x07D1, OSYS)
Error    4062 -                 Object does not exist ^  (OSYS)

dsdt.dsl   337:                     Store (0x07D1, OSYS)
Error    4062 -                 Object does not exist ^  (OSYS)

dsdt.dsl   342:                     Store (0x07D2, OSYS)
Error    4062 -                 Object does not exist ^  (OSYS)

dsdt.dsl   347:                     Store (0x07D6, OSYS)
Error    4062 -                 Object does not exist ^  (OSYS)

dsdt.dsl   351:             If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
Error    4062 -    Object does not exist ^  (MPEN)

dsdt.dsl   351:             If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
Error    4062 -                  Object does not exist ^  (OSYS)

dsdt.dsl   353:                 TRAP (0x3D)
Error    4062 -                    ^ Object does not exist (TRAP)

dsdt.dsl   356:             TRAP (0x2B)
Error    4062 -                ^ Object does not exist (TRAP)

dsdt.dsl   357:             TRAP (0x32)
Error    4062 -                ^ Object does not exist (TRAP)

dsdt.dsl   361:     OperationRegion (GNVS, SystemMemory, 0x7FEE2A37, 0x0100)
Error    4062 -   Object does not exist ^  (GNVS)

dsdt.dsl   362:     Field (GNVS, AnyAcc, Lock, Preserve)
Error    4062 -               ^ Object does not exist (GNVS)

dsdt.dsl   364:         OSYS,   16, 
Error    4062 -            ^ Object does not exist (OSYS)

dsdt.dsl   365:         SMIF,   8, 
Error    4062 -            ^ Object does not exist (SMIF)

dsdt.dsl   366:         PRM0,   8, 
Error    4062 -            ^ Object does not exist (PRM0)

dsdt.dsl   367:         PRM1,   8, 
Error    4062 -            ^ Object does not exist (PRM1)

dsdt.dsl   368:         SCIF,   8, 
Error    4062 -            ^ Object does not exist (SCIF)

dsdt.dsl   369:         PRM2,   16, 
Error    4062 -            ^ Object does not exist (PRM2)

dsdt.dsl   370:         LCKF,   8, 
Error    4062 -            ^ Object does not exist (LCKF)

dsdt.dsl   371:         PRM4,   16, 
Error    4062 -            ^ Object does not exist (PRM4)

dsdt.dsl   372:         P80D,   32, 
Error    4062 -            ^ Object does not exist (P80D)

dsdt.dsl   373:         LIDS,   8, 
Error    4062 -            ^ Object does not exist (LIDS)

dsdt.dsl   374:         PWRS,   8, 
Error    4062 -            ^ Object does not exist (PWRS)

dsdt.dsl   375:         DBGS,   8, 
Error    4062 -            ^ Object does not exist (DBGS)

dsdt.dsl   376:         LINX,   8, 
Error    4062 -            ^ Object does not exist (LINX)

dsdt.dsl   378:         ACT1,   8, 
Error    4062 -            ^ Object does not exist (ACT1)

dsdt.dsl   379:         ACTT,   8, 
Error    4062 -            ^ Object does not exist (ACTT)

dsdt.dsl   380:         PSVT,   8, 
Error    4062 -            ^ Object does not exist (PSVT)

dsdt.dsl   381:         TC1V,   8, 
Error    4062 -            ^ Object does not exist (TC1V)

dsdt.dsl   382:         TC2V,   8, 
Error    4062 -            ^ Object does not exist (TC2V)

dsdt.dsl   383:         TSPV,   8, 
Error    4062 -            ^ Object does not exist (TSPV)

dsdt.dsl   384:         CRTT,   8, 
Error    4062 -            ^ Object does not exist (CRTT)

dsdt.dsl   385:         DTSE,   8, 
Error    4062 -            ^ Object does not exist (DTSE)

dsdt.dsl   386:         DTS1,   8, 
Error    4062 -            ^ Object does not exist (DTS1)

dsdt.dsl   387:         DTS2,   8, 
Error    4062 -            ^ Object does not exist (DTS2)

dsdt.dsl   388:         BNUM,   8, 
Error    4062 -            ^ Object does not exist (BNUM)

dsdt.dsl   389:         B0SC,   8, 
Error    4062 -            ^ Object does not exist (B0SC)

dsdt.dsl   390:         B1SC,   8, 
Error    4062 -            ^ Object does not exist (B1SC)

dsdt.dsl   391:         B2SC,   8, 
Error    4062 -            ^ Object does not exist (B2SC)

dsdt.dsl   392:         B0SS,   8, 
Error    4062 -            ^ Object does not exist (B0SS)

dsdt.dsl   393:         B1SS,   8, 
Error    4062 -            ^ Object does not exist (B1SS)

dsdt.dsl   394:         B2SS,   8, 
Error    4062 -            ^ Object does not exist (B2SS)

dsdt.dsl   395:         LBST,   8, 
Error    4062 -            ^ Object does not exist (LBST)

dsdt.dsl   396:         TBST,   8, 
Error    4062 -            ^ Object does not exist (TBST)

dsdt.dsl   398:         APIC,   8, 
Error    4062 -            ^ Object does not exist (APIC)

dsdt.dsl   399:         MPEN,   8, 
Error    4062 -            ^ Object does not exist (MPEN)

dsdt.dsl   400:         PCP0,   8, 
Error    4062 -            ^ Object does not exist (PCP0)

dsdt.dsl   401:         PCP1,   8, 
Error    4062 -            ^ Object does not exist (PCP1)

dsdt.dsl   402:         PPCM,   8, 
Error    4062 -            ^ Object does not exist (PPCM)

dsdt.dsl   405:         IGDS,   8, 
Error    4062 -            ^ Object does not exist (IGDS)

dsdt.dsl   406:         TLST,   8, 
Error    4062 -            ^ Object does not exist (TLST)

dsdt.dsl   407:         CADL,   8, 
Error    4062 -            ^ Object does not exist (CADL)

dsdt.dsl   408:         PADL,   8, 
Error    4062 -            ^ Object does not exist (PADL)

dsdt.dsl   409:         CSTE,   16, 
Error    4062 -            ^ Object does not exist (CSTE)

dsdt.dsl   410:         NSTE,   16, 
Error    4062 -            ^ Object does not exist (NSTE)

dsdt.dsl   411:         SSTE,   16, 
Error    4062 -            ^ Object does not exist (SSTE)

dsdt.dsl   412:         NDID,   8, 
Error    4062 -            ^ Object does not exist (NDID)

dsdt.dsl   413:         DID1,   32, 
Error    4062 -            ^ Object does not exist (DID1)


Maximum error count (200) exceeded
ASL Input:  dsdt.dsl - 7326 lines, 253841 bytes, 3040 keywords
Compilation complete. 201 Errors, 0 Warnings, 0 Remarks, 2 Optimizations
```

i hope somebody here has a clue on how to fix this because i don't :P
thx in advance..

---

### Post by penC on 2008-11-10
Thanks, works fine with Acer Aspire 5102 with 8.10.

All the best,

  pen

---

### Post by flymw on 2008-12-08
As it seams no need to change anything on the new Ubuntu 8.10 Intrepid.

Suspend and resume has been working out of the box for me!

---

### Post by falfam on 2009-03-03
Hi gang....this is my first post. I've been looking over the tips here and tried a few but so far nothing has helped. I've tried the first post in the forum and one somewhere else but, again, to no avail. I have a GATEWAY MX8734 Laptop running Ubuntu 8.10- the Intrepid Ibex - released in October 2008.

Everything works great. I just cannot suspend nor hibernate this machine. I've also tried other (forgive me) distros to no avail.

Any ideas at all.....? If i have missed something in this particular forum please forgive me...I'm trying.

Thanks for ANY help in this matter.

Jeff

---

### Post by falfam on 2009-03-04
):P Any help at all?

Thanks

---

### Post by nekr0z on 2009-03-04
falfam, I have never had any experience with Gateway laptops (they are not sold in my country, AFAIK), so I can only make guesses and general suggestions.

As defaults for various Linux distros are slightly different, I can easily suppose that your lack of luck shows that your laptop's ACPI doesn't play good with Linux kernel. There may be at least 2 reasons: either the laptop's power management is broken completely (have you tried MS Windows, BSD or any other OS?) or Linux kernel just doesn't support it (yet?). Anyway, the first thing to do is trying to update your BIOS, and the second thing to do is searching hard for some Gateway-specific (or even model-specific) forum or topic. The third step would be looking through the logs (starting from /var/log/syslog and /var/log/dmesg) and trying to interpret the messages you get there at the times you try to put the machine into suspend mode. There's a fair chance you'll find a hint about what exactly prevents your system from going to suspend mode in those logs.

I doubt you'll get any help in a general thread like this one: at the first sight, your issue seems to be extremely hardware-specific, so try searching for the place where owners of such hardware talk. But if you create a separate thread and post some logs, someone (even me) may try to help analyse.

---

### Post by falfam on 2009-03-04
Thanks nekr0z. I will further investigate, as you say, the hardware-specific section of these forums...and yes I will try to post some specific hardware details about by laptop to se if solutiopn is found.

Russia uh....THATS GREAT...what a small world for sure.

---

### Post by Rob-e on 2009-04-18
i just ran this on 8.10 and if fixed my problem

the problem was i installed another distro on another partition and it formatted my swap, thus changing my uuid and breaking my resume, but this did it, nice!

---

### Post by okan72 on 2009-04-29
Yes, it works!

---

### Post by WhiteHorse on 2009-04-30
Also confirmed the suspend to disk(hibernate) works for aspire 4720Z. The default suspend to ram(suspend) works so I didn't test it, just left it as is by default.

This is on Ubuntu 9.04 Jaunty Jackalopearoo.

Now I can focus on making games work :)

---

### Post by jodef on 2009-05-02
I have a Dell Inspiron 9400 I have never been able to get suspend to ram or hibernate to work.

Today read through this entire thread and did some googling after some prelim work got my swap space setup and recognized and s2disk works perfectly.:P

But s2ram is a bit problematic it suspends but on resume the system freezes I have to do a hard power off. 

My Inspiron uses an integrated Intel 945GM. Where can I locate the log that would have the errors encountered while resuming?

Thanks.

---

### Post by Watonga on 2009-05-04
I just upgraded to Jaunty, and as I normally do in upgrades, I made the changes outlined in this howto to make my system use s2ram and s2disk. Both commands would work when I ran them from the terminal, but when I selected "hibernate" or "suspend" from the logout menu, they didn't seem to be working.

I discovered that with this upgrade, Jaunty seems to have installed uswsusp into /usr/sbin/, and not /sbin. So, for those of you having the same problem, when you edit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux, instead of putting this:

```
#!/bin/sh

/sbin/s2disk

```
try this instead:

```
#!/bin/sh

/usr/sbin/s2disk
```

You also would need to make a similar change for suspend. This fixed the problem for me so that I could select hibernate or suspend from the menu, rather than having to run s2disk or s2ram from the terminal.

---

### Post by inspired on 2009-05-06
> **Watonga said:**
> 

I discovered that with this upgrade, Jaunty seems to have installed uswsusp into /usr/sbin/, and not /sbin. So, for those of you having the same problem, when you edit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux, instead of putting this:

```
#!/bin/sh

/sbin/s2disk

```
try this instead:

```
#!/bin/sh

/usr/sbin/s2disk
```


Thanks for posting this tip. I now have hibernation working again on my system... after the upgrade to 9.04 killed it. Nice...

---

### Post by Deadalus on 2009-05-07
Thank you Watonga. This make hibernate work for me. It has never worked for me.

---

### Post by nloewen on 2009-06-13
s2ram didn't work proporly on jaunty. It just did a lock screen. I replaced /usr/sbin/s2ram --force with just s2ram --force and it worked.

---

### Post by GNUbee40 on 2009-08-12
Hello there!

I have a different problem: Sleep worked fine initially. But now I get logged out every time I send my machine to sleep and thus loose all my opened windows. Not sure if this is related to some X-upgrades, but I suppose it is some kind of problem with X. I use an updated version of X to get better graphic performance.

Any comments or suggestions?
Regards

---

### Post by Sherlock19 on 2009-08-16
well for now it is working, but this has happened before, i am running 9.04 and sometimes it wokrs and sometimes it doesnt, working now so i will post later if i have any issues thanks!

---

### Post by lazyfirecloud on 2009-08-27
I've finally upgraded my laptop to Jaunty and hibernate does not work anymore. Under Intrepid I had to use s2both; I had changed some script to call it when I click the button and all was well.

Currently, When I click the hibernate button, it goes black for a second and goes to the unlock screen.

I can hibernate just fine by running ```
sudo s2disk
``` command-line.

I've changed /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux such that running ```
sudo /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
``` works fine, but it does not seem to be script called when I press the button.
I also tried running ```
sudo /etc/acpi/hibernate.sh
``` but it shuts down my computer (or at least it doesn't resume properly), so I'm guessing that's also not the script called when I press the button.
I'm debating whether to change the pm-hibernate but I'm very reluctant to try doing so.

So my question is: what does Jaunty call when I click hibernate in the menu? What script do I have to change so it runs s2disk?

If anyone has any ideas, I would be more than grateful.

---

### Post by lazyfirecloud on 2009-08-27
> **Paul S said:**
> It sounds like you didn't correctly move the original files and create the new ones .. which means the original scripts are still running when you use the menus to hibernate / suspend. Open a terminal and check with these commands (see how you compare to mine):

paul :~$ ls -la /usr/lib/hal/scripts/linux/
total 64
drwxr-xr-x 2 root root 4096 2007-07-13 09:16 .
drwxr-xr-x 3 root root 4096 2007-05-18 21:53 ..
-rwxr-xr-x 1 root root 1283 2007-05-11 03:29 hal-luks-remove-linux
-rwxr-xr-x 1 root root 1093 2007-05-11 03:29 hal-luks-setup-linux
-rwxr-xr-x 1 root root  813 2007-05-11 03:29 hal-luks-teardown-linux
-rwxr-xr-x 1 root root 1965 2007-05-11 03:29 hal-system-killswitch-get-power-linux
-rwxr-xr-x 1 root root 2121 2007-05-11 03:29 hal-system-killswitch-set-power-linux
-rwxr-xr-x 1 root root 2393 2007-05-11 03:29 hal-system-lcd-get-brightness-linux
-rwxr-xr-x 1 root root 2447 2007-05-11 03:29 hal-system-lcd-set-brightness-linux
-rwxr-xr-x 1 root root   78 2007-07-13 20:57 hal-system-power-hibernate-linux
-rw-r--r-- 1 root root 3124 2007-07-13 09:16 hal-system-power-hibernate-linux.bak
-rwxr-xr-x 1 root root  333 2007-05-11 03:29 hal-system-power-reboot-linux
-rwxr-xr-x 1 root root  897 2007-05-11 03:29 hal-system-power-set-power-save-linux
-rwxr-xr-x 1 root root  335 2007-05-11 03:29 hal-system-power-shutdown-linux
-rwxr-xr-x 1 root root  112 2007-07-13 20:57 hal-system-power-suspend-linux
-rw-r--r-- 1 root root 4092 2007-07-13 09:15 hal-system-power-suspend-linux.bak

paul :~$ cat /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
#!/bin/sh

/sbin/s2ram

paul :~$ cat /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
#!/bin/sh

/sbin/s2disk

HTH

Hi:
I have the exact same problem. I can actually hibernate just fine when I run 
```
sudo /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```
The script has the right permissions:
```

-rwxr-xr-x 1 root root   29 2009-08-26 16:27 hal-system-power-hibernate-linux
-rwxr-xr-x 1 root root 3651 2009-04-09 18:13 hal-system-power-hibernate-linux.bak

```
but when I press the hibernate button I only get a black screen for a second and it goes to the unlock screen.

---

### Post by Taintedlove on 2009-09-04
**I seem to have a different problem, s2disk doesn't work, neither does my hibernate script, this is the output I get:**
```
******@ubuntu:~$ ls -la /usr/lib/hal/scripts/linux

total 68
drwxr-xr-x 2 root root 4096 2009-09-03 12:39 .
drwxr-xr-x 3 root root 4096 2009-09-03 12:39 ..
-rwxr-xr-x 1 root root  252 2009-07-05 06:07 hal-dockstation-undock-linux
-rwxr-xr-x 1 root root 1662 2009-07-05 06:07 hal-luks-remove-linux
-rwxr-xr-x 1 root root 1093 2009-07-05 06:07 hal-luks-setup-linux
-rwxr-xr-x 1 root root  813 2009-07-05 06:07 hal-luks-teardown-linux
-rwxr-xr-x 1 root root 2703 2009-07-05 06:07 hal-system-killswitch-get-power-linux
-rwxr-xr-x 1 root root 2822 2009-07-05 06:07 hal-system-killswitch-set-power-linux
-rwxr-xr-x 1 root root 2654 2009-07-05 06:07 hal-system-lcd-get-brightness-linux
-rwxr-xr-x 1 root root 2710 2009-07-05 06:07 hal-system-lcd-set-brightness-linux
-rwxr-xr-x 1 root root 1855 2009-07-05 06:07 hal-system-power-hibernate-linux
-rwxr-xr-x 1 root root  333 2009-07-05 06:07 hal-system-power-reboot-linux
-rwxr-xr-x 1 root root  451 2009-07-05 06:07 hal-system-power-set-power-save-linux
-rwxr-xr-x 1 root root  335 2009-07-05 06:07 hal-system-power-shutdown-linux
-rwxr-xr-x 1 root root 2108 2009-07-05 06:07 hal-system-power-suspend-hybrid-linux
-rwxr-xr-x 1 root root 2197 2009-07-05 06:07 hal-system-power-suspend-linux
lrwxrwxrwx 1 root root   20 2009-09-03 12:39 hal-system-wol-enabled-linux -> hal-system-wol-linux
lrwxrwxrwx 1 root root   20 2009-09-03 12:39 hal-system-wol-enable-linux -> hal-system-wol-linux
-rwxr-xr-x 1 root root 1775 2009-07-05 06:07 hal-system-wol-linux
lrwxrwxrwx 1 root root   20 2009-09-03 12:39 hal-system-wol-supported-linux -> hal-system-wol-linux

```**And the hybernate scrypt:**```

#!/bin/sh

unsupported() {
    echo org.freedesktop.Hal.Device.SystemPowerManagement.NotSupported >&2
    echo No hibernate script found >&2
    exit 1
}

# Make a suitable command line argument so that the tools can do the correct
# quirks for video resume.
# Passing the quirks to the tool allows the tool to not depend on HAL for data.
QUIRKS=""
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-bios"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE" = "true" ] && QUIRKS="$QUIRKS --quirk-s3-mode"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-suspend"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_ON" = "true" ] && QUIRKS="$QUIRKS --quirk-dpms-on"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBESTATE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbestate-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBEMODE_RESTORE" = "true" ] && QUIRKS="$QUIRKS --quirk-vbemode-restore"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VGA_MODE_3" = "true" ] && QUIRKS="$QUIRKS --quirk-vga-mode3"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_VBE_POST" = "true" ] && QUIRKS="$QUIRKS --quirk-vbe-post"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_RADEON_OFF" = "true" ] && QUIRKS="$QUIRKS --quirk-radeon-off"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_RESET_BRIGHTNESS" = "true" ] && QUIRKS="$QUIRKS --quirk-reset-brightness"
[ "$HAL_PROP_POWER_MANAGEMENT_QUIRK_NONE" = "true" ] && QUIRKS="$QUIRKS --quirk-none"

# We only support pm-utils
if [ -x /usr/sbin/pm-hibernate ] ; then
    /usr/sbin/pm-hibernate $QUIRKS
    RET=$?
else
    unsupported
fi

#Refresh devices as a resume can do funny things
for type in button battery ac_adapter
do
    devices=`hal-find-by-capability --capability $type`
    for device in $devices
    do
        dbus-send --system --print-reply --dest=org.freedesktop.Hal \
              $device org.freedesktop.Hal.Device.Rescan
    done
done

exit $RET

```
**Any idea's/help would be greatly apreciated, I'm running a HP HDX 18 laptop, Jaunty 64bit. I got my suspend working by updating my bios, but hybernate still requires a hard reboot after attempting.**

---

### Post by James Keating on 2009-11-04
Before Karmic (9.10), I edited /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux and changed the quirks line to:
QUIRKS="--quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore" 
(This needed to be redone after each update, since the file got overwritten.)

Now that file has no effect. Instead, I must add two boot parameters and delete references to the quirks in a file that removes them instead of letting them take effect.

The first time I suspend, resume works for a moment and then goes into hibernation. After coming out of hibernation, resume works from the second time on. This may be peculiar to my machine.

Make backups of all files you change. All changes must be made as root.

My method:

1. In /boot/grub/menu.lst
add i915.modeset=0 nomodeset to the defoptions line. This disables the new kernel mode-setting (KMS):
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i915.modeset=0 nomodeset

If menu.lst doesn't exist, your installation uses a new GRUB method.
If so, edit /etc/defaults/grub
and add i915.modeset=0 nomodeset:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 nomodeset"

1b) Save and run the command update-grub.

2. In /usr/lib/pm-utils/sleep.d/98smart-kernel-video
delete all references to the quirks you need.
In my case (for an Intel driver), two quirks are in the section remove_all_video_quirks: 
     --quirk-s3-bios  --quirk-s3-mode
and three are in the section have_smart_intel: 
     --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore

3) Save and reboot.

To find the quirks you need, look at the manpage for pm-suspend, and run pm-suspend followed by quirk options. Try combining everything that looks likely, then removing some. Be thorough and patient. Make notes, because you may be rebooting a lot until something works. 

If no combination works, try installing uswsusp and running s2ram, or try TuxOnIce, though I had no luck with either.

##########

Update for Lucid:

Under Lucid, the instructions above do not work -- with those kernel parameters, I boot into a black screen.
i915.modeset needs to be on in order to boot.

If, like me, you can't boot after upgrading to Lucid, and can't boot off a Lucid CD, you need to

A) get a CD for a Ubuntu version before Lucid 10.04
B) change your boot parameters
C) optionally, install a newer kernel that fixes the Intel 8xx graphics problem 

I have tried everything in [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and a number of other suggestions. I have only had success with this method. 

A)
1. Go to the Ubuntu Releases site, [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
2. Choose Karmic or 9.10 and download one of the desktop CD .iso files.
3. Burn its contents to a 700 Mb CD.

B)
Boot from that CD.

You must edit a boot file as root. Nautilus has no options for editing files as root, so you must use commands. 

1. Open a terminal.

2. The easiest way to go from here is to start Nautilus as root with "sudo nautilus" and edit files the usual way, without running each editing command below.

You will need to edit the boot file on your hard drive, not on the CD. The CD makes this confusing, since directories will not be in their usual places.
From the command line, your hard drive will be under /media/(long-nonsensical-name)
From Nautilus, it will show under Places as "106 GB Filesystem" or something.
If you have multiple partitions and there is more than one such listing, find the one that contains your home directory.

3. Navigate to /etc/default on your hard drive

4. Edit the file called grub 
sudo gedit grub
On the line that begins GRUB_CMDLINE_LINUX_DEFAULT, add i915.modeset=1
GRUB_CMDLINE_LINUX_DEFAULT="splash i915.modeset=1"

If your /etc/default/grub doesn't exist, you are using the old Grub. 
In that case, go to /boot/grub/ on your hard drive
and edit the file called menu.lst
There is one line that begins with # defoptions. Add i915.modeset=1"
# defoptions=quiet splash i915.modeset=1

5. Save and run the command 
sudo update-grub

If gedit doesn't work, try another text editor. At the very least, nano should be present (control-o saves; control-x exits).

6. Reboot.

C)
1. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and find the newest directory (I used v2.6.34-rc7-lucid)
2. Download the kernel image and header files
3. Install them from a terminal with the command 
sudo dpkg -i (kernelfilename.deb) (headersfilename.deb)
or run sudo gdebi-gtk
3. reboot and choose that kernel.

---

### Post by altonbr on 2010-05-23
Is there an updated tutorial for Ubuntu 10.04 Lucid?

---

### Post by rlcanfield on 2010-06-14
I have never had any problems with my laptop with hibernate option.

---

### Post by Redsandro on 2010-07-01
lol that totally broke my computer. :o

Not advised for Asus P4C 800.

---

### Post by hellolife on 2010-09-11
> **altonbr said:**
> Is there an updated tutorial for Ubuntu 10.04 Lucid?

Hi, did you ever find an update for Lucid 10.04?

I am afraid to try anything because I don't want to have to restore :(.

---

### Post by Kixtosh on 2010-09-12
Everyone, I'm running Xubuntu 10.04 on an old Portégé ultra-light. I just use it for browsing and other stuff, as a handy very light 11.3" screen portable (under 3lbs, or about 1.Kg). With the LXDE desktop installed, it boots in just under one minute, and navigates reliably with Chromium. But ... suspend was not working.

Hibernation has always worked, but that doesn't really save much time compared to a normal boot (about 10-15 seconds faster). Thanks to this thread, and the openSUSE suspend 2 RAM project, I've got this working perfectly. Here's what happened.


**[COLOR="Red"]I - Before the Fix:[/COLOR]**

When I would attempt to suspend:

- Display would go blank, with blinking "_" in top left of screen.
- Green "On" LED never went out (it should blink orange in standby).
- Wireless PC card Link light went off, but Power light stayed on.
- I could only turn off from this state by pressing power button.


**[COLOR="Red"]II - Now The Fix:[/COLOR]**

I followed Bluecircle's instructions, after opening a Terminal window: ```
sudo apt-get install uswsusp
``` then my password, then: ```
sudo s2ram
```This returned the result: ```
Machine is unknown.
This machine can be identified by:
   sys_vendor   = "TOSHIBA"
   sys_product  = "Portable PC"
   sys_version  = "Version 1.0"
   bios_version = "Version 1.80"
See http://suspend.sf.net/s2ram-support.html for details.
If you report a problem, please include the complete output above.
```Well, that's an old link, but the infromation is there, and a newer one to the SUSE project is here: 

[http://en.opensuse.org/SDB:Suspend_to_RAM#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F](http://en.opensuse.org/SDB:Suspend_to_RAM#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F)

After some reading I tried: ```
s2ram -f -a 3
``` - Enabled suspend perfectly.
- Could not wake up from suspend properly.
- Everything wakes up, but screen remains blank.
- Screen gradually turns whiter and whiter.

So, I tried, ```
s2ram -f -a 2
```- Everything worked.
- Wake up worked perfectly.


**[COLOR="red"]III - Making it Permanent:[/COLOR]**

At the usual terminal prompt ~$, tried: ```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/hal-system-power-suspend-linux
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```Got the following message: ```
sudo: gedit: command not found
```I realized that Xubuntu with the LXDE desktop environment does not have the gedit text editor. It uses Mouse. Instead of trying to figure that one out (I'm not very familiar with Terminal commands as yet), I installed gedit from the Ubuntu Software Center, and tried again.

- A gedit text editor window appeared.
- I replaced the ENTIRE page of code with just:

```
#!/bin/sh

/sbin/s2ram -f -a2
```- Tried suspend again.
- Nothing happened.

Fortunately, I had read this whole thread, including **Watonga's** post on page 19:

[http://ubuntuforums.org/showpost.php...&postcount=190](http://ubuntuforums.org/showpost.php...&postcount=190)

So, I changed my Terminal command to: ```
#!/bin/sh

/usr/sbin/s2ram -f -a2
```

- Hibernation still works perfectly. No changes were made.
- Suspend now works perfectly!


[B]Thank you [COLOR="Red"]Bluecircle[/COLOR] and [COLOR="red"]Watonga[/COLOR], and thankyou [COLOR="red"]openSUSE s2ram project[/COLOR]!

Perhaps it's time to update the instructions on page one to reflect Watonga's correction on page nineteen?!

[COLOR="red"]OpenSUSE project here: [http://en.opensuse.org/SDB:Suspend_to_RAM#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F](http://en.opensuse.org/SDB:Suspend_to_RAM#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F)[/COLOR][/B]


_For reference purposes_, the rather old Portégé 3490CT uses:

- S3 Savage IX graphics controller, 
- 128-bit 3D GraphicsAccelerator,
- 128bit BitBLT engine, 33MHz PCI bus,
- 8MB internal video memory.

---

### Post by kooldino on 2010-12-16
Found this solution for my Dell Mini 1012.  Thank God it works:

[QUOTE="Petri K"]Hi!

This problem affects not just the Lenovo T400 but also for example the new Dell Latitude E4200, HP EliteBook 2530p, Sony Vaio VGN-TT1, Toshiba R600, or anything else with the "Mobile Intel® GM45 Express Chipset" or X4500. I have exactly the same symptoms on my E4200 running intrepid.

The bug most certainly resides in the xserver-xorg-video-intel code. The fact that is manifests itself only with gnome desktop and not with KDE or text mode gives some clue. It is not compiz related as disabling compiz has no effect. I would say that this is a classical multiprocessor concurrency control problem! Disabling all but one core makes the bug disappear.

Here is my suggestion for a workaround. Save in /etc/pm/sleep.d/00CPU with 755 permissions. Note that it has to be called 00CPU so that it gets executed before and after anything else.
```

Code:
#!/bin/sh
# Workaround for concurrency bug in xserver-xorg-video-intel 2:2.4.1-1ubuntu10.
# Save this as /etc/pm/sleep.d/00CPU

. "${PM_FUNCTIONS}"

case "$1" in
	hibernate|suspend)
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 0 >$i
		done
		;;
	thaw|resume) 
		sleep 10	# run with one core for 10 secs
		for i in /sys/devices/system/cpu/cpu*/online ; do
			echo 1 >$i
		done
		;;
	*)
		;;
esac

```
Please report if this works for you! The sleep period can easily be made longer if necessary.

Petri K[/QUOTE]

---

### Post by earlf on 2010-12-28
[INDENT]**[COLOR=Red]II - Now The Fix:[/COLOR]**
 
 I followed Bluecircle's instructions, after opening a Terminal window: [/INDENT]
I just tried this fix on a Sony VAIO A series laptop and it did not work. (The machine has 496.6 MB RAM and an Intel Pentium M processor 1.7 GHZ.


I am a rookie in these matters so I more than likely have done something wrong.

After I tried the fix I suspended my computer and then it froze up completely. It has done this when booting up so trying this fix may not be the only/direct issue.

---

### Post by readable on 2011-02-21
Thanks. This worked great on my Toshiba NB305 netbook with all the other hacks that people have used. The only thing is that I need to hit the power button to resume from a suspend.

---

### Post by Kixtosh on 2011-02-21
> **readable said:**
> Thanks. This worked great on my Toshiba NB305 netbook with all the other hacks that people have used. The only thing is that I need to hit the power button to resume from a suspend.That seems to be standard procedure: all three of my Toshiba Portégé laptops (3490CT, R205 and R500) require that the power button be pressed to resume from sleep. It doesn't bother me in the slightest however, so I have never tried to make it work any other way.

---

### Post by misterpotato on 2011-05-11
Hello,

I am running Ubuntu 11.04 Natty on an Acer Aspire 5630 (sad, I know...). With 10.04 I was able to suspend but not to hibernate. Now, I can hibernate (though with a messed up screen when I have to enter my password) but I can't suspend: the screen goes blank but the fan goes insane and the laptop never really goes to sleep. 

So I tried the s2ram thing and it works (sort of...) but my problem is that I can't follow those instructions to change the "hal-system-power-suspend-linux" because (from what I got) that file doesn't exist anymore.

So how, or more exactly where, can I change the suspend order permanently? Thanks

---

### Post by James Keating on 2011-05-11
Control over suspending is moving into the kernel, with uneven success. The hal files don't do anything anymore. I went half-mad trying to fix my suspend problem, and finally found I had to change multiple files in a specific way simultaneously. Yay! First in the world to work that out, and it might have helped a bunch of people except that the very next distribution introduced kernel modesetting, and I had to find an answer all over again. Fortunately, this time only a little research was required.

I only need one modified line in /etc/defaults/grub now:
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"

You can also try pm-suspend, and try combinations of options (keep notes) until something works. See the man page for the options. For me, the following command is still effective, and the chances are good that something similar will work for you:

pm-suspend --quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore

If it does, put it into a file (with #!/bin/sh as the first line), make it executable and run it to suspend.

---

### Post by misterpotato on 2011-05-11
Hey James,

Thanks for you answer. 

However, I kept looking for answers and found this today in omgubuntu:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

It worked for me in 11.04 perfectly. I just followed the instructions there.

---

### Post by Dabak on 2011-05-13
I enthusiastically installed Ubuntu for the first time on a Toshiba M100 last night and set it to hibernate when I had finished with it for the evening. After being met by an unresponsive system today and doing a quick search online I learnt that there seems to be an issue with hibernate. As I had nothing of any value on the system I did a re install. I had to use an additional monitor in order to proceed as the Toshiba display would not wake up. Now that the re install is complete the only way that I can use the laptop is by using the extra monitor.

---

### Post by James Keating on 2011-10-25
Update for 11/10 Oneiric:

Pressing the power button again failed to suspend my laptop. I have to something different with nearly every release.

I tried making panel launcher with 
gksudo "pm-suspend --quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore"
and that worked but I hated having to enter a password just to suspend.

The real solution is simpler:
In /etc/acpi/powerbtn.sh
comment out the last line:
#/sbin/shutdown -h now "Power button pressed"
and enter the suspend command, along with whatever quirks your machine requires:
/usr/sbin/pm-suspend --quirk-s3-bios --quirk-s3-mode --quirk-dpms-on --quirk-vbe-post --quirk-vbestate-restore

Finding the quirks is a matter of trial and error.

I think grub no longer needs modification, but my one line
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"
doesn't seem to hurt anything.

---

