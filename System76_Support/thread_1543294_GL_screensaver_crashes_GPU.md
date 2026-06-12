---
title: "GL screensaver crashes GPU"
date: 2010-07-31
forum: System76 Support
---

### Post by robgwin on 2010-07-31
Brand new Ratel Ultra showed up yesterday, with Ubuntu 10.04, Kernel 2.6.32-24-generic, and GNOME 2.30.2. The GPU took to crashing after an hour of inactivity. Luckily, I eventually figured out that this was apparently caused by setting the screensaver to GLCells. The screensaver was set to start after 5 minutes, so it doesn't happen right away. It also works fine in the preview (else I wouldn't have chose it in the first place!)

Obviously, I don't have to use that screensaver, but it's still a little surprising (?) for a completely new install of the latest default Ubuntu on the latest hardware, with (at least) one of the default screensavers listed in preferences.

Here's what I see in the syslog when the hang occurs (at 11:24.. first 3 lines just shown for context)

Jul 31 10:28:30 monkeyjr AptDaemon: INFO: Quiting due to inactivity
Jul 31 10:28:30 monkeyjr AptDaemon: INFO: Shutdown was requested
Jul 31 11:17:01 monkeyjr CRON[1820]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 31 11:24:24 monkeyjr kernel: [ 3726.356842] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul 31 11:24:24 monkeyjr kernel: [ 3726.356852] render error detected, EIR: 0x00000000
Jul 31 11:24:24 monkeyjr kernel: [ 3726.356907] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 408693 at 408692)
Jul 31 11:24:27 monkeyjr kernel: [ 3728.619852] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul 31 11:24:27 monkeyjr kernel: [ 3728.619858] render error detected, EIR: 0x00000000
Jul 31 11:24:27 monkeyjr kernel: [ 3728.619879] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 408699 at 408692)
Jul 31 11:24:27 monkeyjr kernel: [ 3729.367527] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul 31 11:24:27 monkeyjr kernel: [ 3729.367533] render error detected, EIR: 0x00000000

... and repeats over and over until I attempt to wake the computer up, at which point I get this:

GLIB_WARNING **: getpwuid_r(): failed due to unknown user id (0)

at which point my only recourse is to switch to another console and reboot the box.

---

### Post by marshmallow1304 on 2010-08-01
Looks similar to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/528467").  [s]Comment [#34]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/528467/comments/34") says that installing kernel 2.6.35 (which can be had [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/") (get linux-headers*<your-architecture>.deb, linux-headers*all.deb, and linux-image*<your-architecture>.deb)) fixes the problem.[/s]

Nevermind:
[quote=Craig73]And in the very next comment he said he spoke too quickly... (not fixed)[/quote]

---

### Post by Craig73 on 2010-08-02
And in the very next comment he said he spoke too quickly... (not fixed)

Out of curiosity... if you create a new test profile, log out of your profile, log into 'test'... are you able to reproduce the problem?  (I'm curious as when I log into a test profile, my setup is considerably more stable... I can run gl desktop, world of goo, try a few gl screen savers... all without a crash / haven't played with it for a long time to see if it eventually dies)

---

### Post by robgwin on 2010-08-11
whoops, think I wasn't subscribed properly to this thread, just noticed the last comment today. Tried creating a test profile, and.. things got even more confusing. Let me try to relate this...

I switched to the test profile, set the screensaver to GLCells, switched back to my own user, continued to work for a while (didn't have a chance yet to leave it alone for an hour). Then, in an attempt to [diagnose this other problem]("http://ubuntuforums.org/showthread.php?p=9703733"), I tried a reboot, forgetting that the "test" profile was still active. So I got a warning popup saying it couldn't shut down with another profile active. I hit cancel and... gnome crashed, or X or whatever. Got a black screen with "GLIB_WARNING **: getpwuid_r(): failed due to unknown user id (0)" and about 6 other lines that look like boot messages (e.g. "Starting Common Unix Printing System: cupsd [OK]", etc).

I hit ctrl-alt-F1 to switch terminals, logged in, and I think that's where I got a message about gnome-server hanging. So I did a kill -9 on the gnome-server process, and that caused a new X/gnome session to start in terminal 8, with GLIB_WARNING still sitting in terminal 7. By this time I gotta head out the door, so I might as well try the GCells test. I log out of my regular profile, log in as "test", confirm GLCells is the active screensaver, and leave for a few hours. When I come back, the test profile is still up and running fine.

So the problem is avoided by either (a) switching to the test profile, or (b) crashing GLIB some other way, or (c) running the desktop in terminal 8 instead of terminal 7. Basically, I still know nothing. Gonna reboot and try again with the test profile overnight...

---

### Post by robgwin on 2010-08-11
Geez, okay, this may not have anything to do with GLcells after all? I can now trigger a version of the problem without it, just by logging out of my default profile:

1. Power down the computer and boot it fresh. I am automatically logged into my main account.
2. Switch between vterminals to verify that the desktop is running in term7 as expected.
3. Select Log Out... and confirm. I am brought to the login screen to choose an account to log into.
4. Switch between vterminals to discover that the desktop is now running in term8, and term7 is crashed with the following messages:

(process: 337): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
mountall: Disconnected from Plymouth
* Starting Common Unix Printing System: cupsd    [ OK ]
* PulseAudio configured for per-user sessions
* Enabling Additional Executable binary formats binfmt-support    [ OK ]
* Checking battery state...    [ OK ]

---

