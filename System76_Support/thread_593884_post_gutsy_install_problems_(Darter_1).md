---
title: "post gutsy install problems (Darter 1)"
date: 2007-10-27
forum: System76 Support
---

### Post by dnarnold on 2007-10-27
I just completed the upgrade to gutsy on my white Darter 1.
For some reason the standard upgrade procedure hung in
the middle leaving my machine in a bad state and I ended
up doing a full install from CD.

The system is mostly working well now, but there are
some things that still need fixing for which I would
appreciate help:

 1) I can suspend from the logout menu or using Fn-F1,
    and it seems to suspend fine in that everything shuts
    down except for the flashing blue power light and
    on/off button, but I cannot resume.  If I hit a key
    to resume, the power light goes on solid, the disk
    busy light goes on solid, but nothing happens.

 2) Hibernate and resume from hibernate seem to work OK,
    except that the wireless, which was on at time of
    hibernation, is off after resume.  To get it back,
    I have to toggle the switch.

 3) Independent of suspend/resume, the Fn-F5 screen dim,
    Fn-F6 screen brighten, Fn-F8 LCD/monitor toggle,
    and Fn-F9 touchpad toggle keys don't do anything.
    The sound control keys Fn-F10, Fn-F11, and Fn-F12
    work fine.

I have tried purging the system76-driver package, removing
/opt/system76, and then reinstalling the package and
re-installing the drivers, but it didn't have any effect.

Thanks for any help!  -- Doug

---

### Post by perce on 2007-10-27
> **dnarnold said:**
> 
    Independent of suspend/resume, the Fn-F5 screen dim,
    Fn-F6 screen brighten, Fn-F8 LCD/monitor toggle,
    and Fn-F9 touchpad toggle keys don't do anything.
    The sound control keys Fn-F10, Fn-F11, and Fn-F12
    work fine.


In order to make the touchpad key work you have to locate the following entry in /etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

and add the line:

Option          "SHMConfig"             "true"

to the list of options.

For the brightness keys you can try to press Ctrl-Alt-F1 followed by Ctl-Alt-F7.

---

### Post by dnarnold on 2007-10-27
> In order to make the touchpad key work you have to locate the following entry in /etc/X11/xorg.conf:
> 
> Section "InputDevice"
> Identifier "Synaptics Touchpad"
> Driver "synaptics"
> Option "SendCoreEvents" "true"
> Option "Device" "/dev/psaux"
> Option "Protocol" "auto-dev"
> Option "HorizEdgeScroll" "0"
> EndSection
> 
> and add the line:
> 
> Option "SHMConfig" "true"
> 
> to the list of options.

Thanks, this fixed the Fn-F9 problem.

 
> For the brightness keys you can try to press Ctrl-Alt-F1 followed by Ctl-Alt-F7.

This didn't help.  I did a little more study on this, and I see that when I push
Fn-F5 I get these messages in /var/log/acpid:

  [Sat Oct 27 20:31:30 2007] received event "video LCDD 00000087 00000000"
  [Sat Oct 27 20:31:30 2007] notifying client 5193[107:116]
  [Sat Oct 27 20:31:30 2007] notifying client 6878[0:0]
  [Sat Oct 27 20:31:30 2007] executing action "/etc/acpi/video_brightnessdown.sh"
  [Sat Oct 27 20:31:30 2007] BEGIN HANDLER MESSAGES
  [Sat Oct 27 20:31:30 2007] END HANDLER MESSAGES
  [Sat Oct 27 20:31:30 2007] action exited with status 0
  [Sat Oct 27 20:31:30 2007] completed event "video LCDD 00000087 00000000"
  [Sat Oct 27 20:31:30 2007] received event "video LCDD 00000087 00000000"
  [Sat Oct 27 20:31:30 2007] notifying client 5193[107:116]
  [Sat Oct 27 20:31:30 2007] notifying client 6878[0:0]
  [Sat Oct 27 20:31:30 2007] executing action "/etc/acpi/video_brightnessdown.sh"
  [Sat Oct 27 20:31:30 2007] BEGIN HANDLER MESSAGES
  [Sat Oct 27 20:31:30 2007] END HANDLER MESSAGES
  [Sat Oct 27 20:31:30 2007] action exited with status 0
  [Sat Oct 27 20:31:30 2007] completed event "video LCDD 00000087 00000000"

But the screen doesn't dim.  Following the script video_brightnessdown.sh, I see
it runs "acpi_fakekey 224".  If I run "sudo acpi_fakekey 224" nothing happens.
I can verify this with "cat /proc/acpi/asus/brn" which shows that the brightness
remains 15.

Note that I can change the screen brightness with "acpitool -z 14"
or with "echo 14 >! /proc/acpi/asus/brn".

So the question is really: why is "acpi_faketool 224" doing nothing?

(And the most important problem remains, resume from suspend is not working.)

Thanks -- Doug

---

### Post by perce on 2007-10-27
> **dnarnold said:**
> > 
 
(And the most important problem remains, resume from suspend is not working.)



How many times did you try? My Darter almost always comes fine from suspend. Only once in a while does what you describe. I also can  use the brightness keys, except after resume from suspend. That case I have to do the F1-F7 trick I describe.

---

### Post by dnarnold on 2007-10-28
> How many times did you try? My Darter almost always comes fine from
> suspend. Only once in a while does what you describe. I also can use the
> brightness keys, except after resume from suspend. That case I have to
> do the F1-F7 trick I describe.

I have tried now many times, and the result is always identical:

 I hit Fn-F1 and the machine suspends normally

 I hit a key to resume and the blinking blue power light goes solid blue,
 the hard drive activity light goes solid blue, and the blue tooth indicator
 goes solid blue, but the screen stays black and the machine is unresponsive.

This has been a problem since I upgraded to gutsy, was not a problem under
feisty.

---

### Post by thomasaaron on 2007-10-29
> I have tried purging the system76-driver package, removing
/opt/system76, and then reinstalling the package and
re-installing the drivers, but it didn't have any effect.

Did you run the "Restore" function of the driver? It dumps in settings to your xorg.conf and, I think, your acpi-support file, whereas the "Install Drivers" tab does not.

---

### Post by dnarnold on 2007-10-31
> Did you run the "Restore" function of the driver? It dumps in settings to your xorg.conf and, I think, your acpi-support file, whereas the "Install Drivers" tab does not.

I just ran the Restore.  It made no difference--still cannot resume from
suspend.

How can we go about debugging this?  Maybe you could send me a tar
file of the relevant acpi files from a working gutsy Darter 1 and
I could compare.

Thanks.

---

### Post by thomasaaron on 2007-10-31
I don't mean to be a pain, here, but are you sure you have the DarU1? 
The DarU1 is the white one.
The DarU2 is the one on our website now.

I just tested my DarU1 and it resumes fine (although the screen brightness seems to be turned way down. (I'll have to look into that.)

The DarU2 suspends into a state much like what you are describing. The power button light stays on solid, etc...  To resume from suspend with the DarU2, you must push the power switch.


If you indeed have a DarU1 with these symptoms, I guess my next questions would be:

1. Are you running 32 bit or 64 bit?
2. Ubuntu or Kubuntu?
3. What modifications (if any) have you made to the acpi-support file or any other acpi related files.

---

### Post by perce on 2007-10-31
[QUOTE=thomasaaron;3677035

If you indeed have a DarU1 with these symptoms, I guess my next questions would be:

1. Are you running 32 bit or 64 bit?
[/QUOTE]

Does Daru1 have a 64 bits processor?

---

### Post by thomasaaron on 2007-10-31
No.

---

### Post by perce on 2007-10-31
Today I suspended twice and I had the same symptoms: power ligght solid blue, bluestooth light solid blue, and the computer didn't wake up. This happened three times. 

Then I realised that the only difference with yesterday was that I had an audio CD in he CD drive; I removed it and suspend worked again (tested only once). In the logs I see a weird message when I insert or 
eject a CD:

  Oct 31 15:13:49 Bach NetworkManager: <debug> [1193868829.082479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_608202752'). 

Oct 31 15:14:55 Bach NetworkManager: <debug> [1193868895.212685] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_608202752'). 

What has Network Manager to do with the CD drive??

---

### Post by perce on 2007-11-01
Today I tried again to suspend with an audio CD in the drive: it crashed again. Then I shut down Network Manager and suspended, still with the CD in the drive, and it worked. Moving the script in /etc/acpi/suspend.d stopping Network Manager from position 99 to position 01 seems to have fixed the problem.

What's wrong with Network Manager now? it worked fine in feisty.

---

### Post by dnarnold on 2007-11-03
Yes, I have the white DarU1.  I run Kubuntu 32 bit.  I haven't made any
acpi mods.

Again, suspend/resume worked fine under feisty.  Under gutsy, suspend
seems to work fine, leaving the machine with the blinking power button
and blinking blue power led, but everything else off.  If I attempt to resume
by hitting any key, including the power button, the power button
and power led stop blinking, the disk activity comes on solid, the
bluetooth led comes on solid, and the machine freezes.  100%
repeatable and a major pain. 

> I don't mean to be a pain, here, but are you sure you have the DarU1?
The DarU1 is the white one.
The DarU2 is the one on our website now.

I just tested my DarU1 and it resumes fine (although the screen brightness seems to be turned way down. (I'll have to look into that.)

The DarU2 suspends into a state much like what you are describing. The power button light stays on solid, etc... To resume from suspend with the DarU2, you must push the power switch.


If you indeed have a DarU1 with these symptoms, I guess my next questions would be:

1. Are you running 32 bit or 64 bit?
2. Ubuntu or Kubuntu?
3. What modifications (if any) have you made to the acpi-support file or any other acpi related files.

---

### Post by perce on 2007-11-03
> **dnarnold said:**
> 
Again, suspend/resume worked fine under feisty.  Under gutsy, suspend
seems to work fine, leaving the machine with the blinking power button
and blinking blue power led, but everything else off.  If I attempt to resume
by hitting any key, including the power button, the power button
and power led stop blinking, the disk activity comes on solid, the
bluetooth led comes on solid, and the machine freezes.  100%
repeatable and a major pain.

Do you have a CD in the drive when you try to suspend by any chance?
Have you tried to shut NetworkManager down before suspending?
I mean manually before hitting the button, not with a script.

---

### Post by dnarnold on 2007-11-04
> Today I suspended twice and I had the same symptoms: power ligght solid blue, bluestooth light solid blue, and the computer didn't wake up. This happened three times.

I also have the disk activity light solid blue when this happens (which is every time I try to resume from suspend).   How about you?

> Do you have a CD in the drive when you try to suspend by any chance?

No, no CD in the drive.

> Have you tried to shut NetworkManager down before suspending?
I mean manually before hitting the button, not with a script.

I hadn't tried before, but I just did. I killed NetworkManager, NetworkManagerDispatcher, and knetworkmanager, and then suspended.  Same problem on resume.  :(

I am completely at a loss.  Anyone have any ideas for debugging this.

---

### Post by perce on 2007-11-04
> **dnarnold said:**
> I also have the disk activity light solid blue when this happens (which is every time I try to resume from suspend).   How about you?



Yes, when it happens to me it has the exact same symptoms. However usually I can resume correctly; only today it's doing crazy things, I'll post if they go on.

Another thing which doesn't work 100% at suspend for me is the intel driver for the graphic card: I see a patchwork of coloured squares at suspend/hibernate, and I loose the possibility to change the screen brightness at resume. You could try either to shut X down and suspend manually (the command should be echo mem > /sys/power/state) or to change i810 with a generic driver and see what happens. I don't want to do these tests on my computer because things sort of work, and I don't want to risk to brake them.

---

### Post by dnarnold on 2007-11-20
This is to report the resolution of a problem I reported earlier,
namely that after upgrading my Darter 1 from feisty to gutsy,
resume from suspend was not working.  When I would attempt
to resume, the power light and disk activity light would go on
solid blue, and nothing more would happen.

It turned out that the problem was due to my booting
a 386 kernel, rather than a generic kernel.  Specifically,
grub would confront me with the choice of 2.6.22-14-386
or 2.6.22-14-generic, and would boot the former by default.
When I selected the generic kernel to boot, suspend/resume
worked fine.  Something I did or the install scripts did
during the gutsy install must have led to the wrong
default being set for the kernel.
This can be fixed either by changing the default
in /etc/grub/menu.lst and running update-grub,
or by removing the 386 kernel packages.

Thanks for everyone who gave suggestions or help.  Everything
is working pretty much perfectly for me with my Darter 1 under
gutsy.  Great machine!

---

