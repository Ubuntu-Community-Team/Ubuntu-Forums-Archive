---
title: "Jack wont start."
date: 2012-10-21
forum: Ubuntu Studio
---

### Post by mjhouska on 2012-10-21
fresh install of studio12.10 jack wont start. dbus yadda yadda. please help.

---

### Post by mjhouska on 2012-10-21
heres the output. again this is a pristine install.

 p, li { white-space: pre-wrap; }  [COLOR=#999999]0:27:12.934 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:27:13.061 Statistics reset.[/COLOR]
 [COLOR=#cccc99]10:27:13.066 ALSA connection change.[/COLOR]
 [COLOR=#999999]10:27:13.073 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]10:27:13.079 ALSA connection graph change.[/COLOR]
 (qjackctl.real:7550): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:7550): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed


just a biostar A780L3G mobo  nothing else

---

### Post by mjhouska on 2012-10-21
yeah i know. stupid idea to move  away from 12.04 LTS  but i was feeling adventurous.  any help is apreciated

---

### Post by mjhouska on 2012-10-21
p, li { white-space: pre-wrap; }  [COLOR=#999999]11:47:45.775 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:47:45.778 Statistics reset.[/COLOR]
 [COLOR=#cccc99]11:47:45.789 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:47:45.803 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]11:47:45.811 ALSA connection graph change.[/COLOR]
 (qjackctl.real:7772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:7772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]11:47:54.827 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Sun Oct 21 11:47:54 2012: Starting jack server...
 Sun Oct 21 11:47:54 2012: JACK server starting in realtime mode with priority 10
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:7772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:7772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Sun Oct 21 11:47:54 2012: control device hw:0
 Sun Oct 21 11:47:54 2012: control device hw:0
 Sun Oct 21 11:47:54 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Sun Oct 21 11:47:54 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sun Oct 21 11:47:54 2012: [1m[31mERROR: Cannot initialize driver[0m
 Sun Oct 21 11:47:54 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
 Sun Oct 21 11:47:54 2012: [1m[31mERROR: Failed to open server[0m
 Sun Oct 21 11:47:56 2012: Saving settings to "/home/mjhouska/.config/jack/conf.xml" ...
 [COLOR=#ff0000]11:48:02.340 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:7772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:7772): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by mjhouska on 2012-10-21
mjhouska@mjhouska-A780L3G:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mjhouska@mjhouska-A780L3G:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe8f4000 irq 16

---

### Post by sgx on 2012-10-21
Solved? What was the solution?
Cheers

---

### Post by Precipitous on 2012-10-24
> **sgx said:**
> Solved? What was the solution?
Cheers
I would like to know how this was solved as well. I had to purchase a new hard drive, so I now have a fresh install of 12.10 and am having the same problems with jack/qjackctl.  I need to get up and running properly as soon as possible as that I am right in the middle of two different album projects and am currently dead in the water.

---

### Post by sgx on 2012-10-24
> **Precipitous said:**
> am currently dead in the water.

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

A link is in the first post, to a 330 meg linux audio distro,
a fore-runner of Studio1337, based on Puppy Linux, includes
qjackctl, ardour, and many common linux audio apps ready to go.

Use k3b, or other app to burn the iso, use computers early-boot
menu, or modify the bios boot order, to launch the studio.

There is a disk mounting gui (pmount) so you can record to any
system hard-disk. I have used this from version 3, to the current
commercial system, and they all do the job, with minimal
user angst.

At first shutdown, you can choose to have a savefile created,
which can be utilized in future sessions. Web browser and basic
utilities are also available.
Cheers

[http://www.getstudio1337.com/](http://www.getstudio1337.com/)  (this is the current commercial
product, but gives you some clues as to the earlier version)

---

### Post by sgx on 2012-10-24
also, did you try launching all the audio apps with sudo,
to remove possible permissions problems?

---

### Post by Precipitous on 2012-10-25
@sgx:  Thank you for your concern and suggestions! Fortunately, I was able to resolve the issue and am now back up and running as per normal...  I am a little embarrassed as to the source of the problems, but in a a nutshell, I had failed to reboot after adding my user account to the audio group, so the change had not yet registered. I figured this out because I decided to try using Cadence (from the KXStudio repositories) to connect to jack instead of qjackctl. It listed on its main window that I was a member of the audio group, but a re-start was necessary! 

In a way I am realy happy everything happened the way it did because it gave me a great excuse to check out Cadence. If you have never used it you should check it out. I am very impressed with it. In fact over time my setup has started to become a real hybrid of KX and Ubuntu Studios. I have found that the KX builds of jack, qjackctl and wineasio are a "must", and play very nicely with UbuntuStudio.

---

### Post by sgx on 2012-10-26
> **Precipitous said:**
> I figured this out because I decided to try using Cadence (from the KXStudio repositories) to connect to jack instead of qjackctl. It listed on its main window that I was a member of the audio group, but a re-start was necessary! 

That is an excellent attention to detail, from a developer
who has tirelessly worked on his project, over many years,
to address both serious issues, and pesky annoyances,
in the linux audio world.
Cheers

---

### Post by architectadrian on 2012-10-27
I am sorry, but I have the same problem. Can anyone help? I didn't changed the user,... I simply installed Ubuntu Studio and I am not able to start Jack. In the QJackctl I get the following message:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]20:06:49.362 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:06:49.363 Statistics reset.[/COLOR]
 [COLOR=#cccc99]20:06:49.376 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:06:49.384 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#ff0000]20:06:49.588 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]20:06:49.642 ALSA connection graph change.[/COLOR]
 Sat Oct 27 20:06:49 2012: Starting jack server...
 Sat Oct 27 20:06:49 2012: JACK server starting in realtime mode with priority 10
 Sat Oct 27 20:06:49 2012: control device hw:0
 Sat Oct 27 20:06:49 2012: control device hw:0
 Sat Oct 27 20:06:49 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Sat Oct 27 20:06:49 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Sat Oct 27 20:06:49 2012: [1m[31mERROR: Cannot initialize driver[0m
 Sat Oct 27 20:06:49 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
 Sat Oct 27 20:06:49 2012: [1m[31mERROR: Failed to open server[0m
 Sat Oct 27 20:06:50 2012: Saving settings to "/home/adrian/.config/jack/conf.xml" ...
 [COLOR=#ff0000]20:06:53.684 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started

---

