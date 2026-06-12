---
title: "Windows 7 guest now aborts on activation of full-screen"
date: 2013-07-06
forum: Virtualisation
---

### Post by imbjr on 2013-07-06
Pretty much as the title says. Some update no doubt, but where to start? The logs don't indicate much:

```

...
00:00:52.546492 AIOMgr: Flush failed with VINF_SUCCESS, disabling async flushes
00:00:53.237851 Guest Log: VBoxMP::VBoxDrvFindAdapter: using HGSMI
00:00:53.243335 OHCI: Software reset
00:00:53.243436 OHCI: USB Reset
00:00:53.316772 OHCI: USB Operational
00:00:54.035724 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f266c000000 w=1920 h=958 bpp=32 cbLine=0x1E00, flags=0x1
00:00:54.036776 Guest Log: VBoxDisp[0]: VBVA enabled
00:00:54.036798 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f266c000000 w=1920 h=958 bpp=32 cbLine=0x1E00, flags=0x1
00:00:54.036814 Display::handleDisplayResize(): Warning: resize postponed.
00:00:54.055684 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f266c000000 w=1920 h=958 bpp=32 cbLine=0x1E00, flags=0x1
00:00:56.723362 Starting host clipboard service
00:00:56.723387 Initializing X11 clipboard backend
00:00:56.724009 Guest Additions capability report: (0x4) seamless: no, hostWindowMapping: no, graphics: yes
00:00:56.724741 Shared clipboard: starting shared clipboard thread
00:00:56.733219 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
00:01:50.626595 AIOMgr: Flush failed with VINF_SUCCESS, disabling async flushes
00:02:47.535365 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f266c000000 w=1920 h=958 bpp=32 cbLine=0x1E00, flags=0x1
00:02:47.535775 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f266c000000 w=1920 h=958 bpp=32 cbLine=0x1E00, flags=0x1
00:02:47.558603 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f266c000000 w=1920 h=958 bpp=32 cbLine=0x1E00, flags=0x1

```

Running in a terminal sees no output at the point of abort. The only extra thing of note is a tiny glitch in whatever music I'm listening to.

I've tried greating a new VM with the hard drives the guest uses, but the problem remains. I have Debian guest that does the same thing, but a Mint guest with Mate does not.

---

### Post by imbjr on 2013-07-06
Well, older kernels don't fix the problem. Mint 14 has no problem with the guest, so if I really need full-screen I can use that.

---

### Post by imbjr on 2013-07-08
I decided to try and force the VM to run full-screen at start up. This revealed some extra information:

> 
imbjr@pc:~$ VirtualBox --startvm "Windows 7" --fullscreen
The program 'VirtualBox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 63 error_code 2 request_code 12 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


The --sync command line option did not appear to be part of VirtualBox.

---

### Post by gwm on 2013-07-08
Suddenly, during the last few days, my guest Windows7 has behaved in a similar way. Behavior is not always the same. At various stages I was blaming the geust OS so I unistalled things that seemed to be hogging the cpu but that wasn't the problem. Next I tried reverting to a backup version of the vdi file but the problem remained. Therefore the problem lies with vbox.

It feels like certain interrupts aren't getting through to the guest OS and the process simply hangs. I tried to shut down Windows from the start button in the usual way but the guest OS just seemed to hang. I left it in that state overnight and in the morning it had finally shut down. Whenever I try to close a window in the guest OS a similar state of hang occurs.

How does vbox get involved with close events for windows?

When it hung I would press the right control key together with F and the guest OS would abort instantly. After many attempts, I managed to reinstall the Guest Additions and that seemed to help a bit for a while. At least it fixed the problem of switching to full screen and back. However, the hanging behavior remains. Sometimes it is worse than others. It appers to be worse when accessing a folder shared with Ubuntu's file system through the share machanism.

---

### Post by twipley on 2013-07-08
Hello. Does it look like being related to this: [https://forums.virtualbox.org/viewtopic.php?f=7&t=56338&p=261004](https://forums.virtualbox.org/viewtopic.php?f=7&t=56338&p=261004) ?

---

### Post by gwm on 2013-07-08
I have read twipley's other link and it seems to me that my symptoms seem to be a little different because I turned off 3D by coincidence when trying to find out why the guest OS crashed when changing to or from full screen.

Mine was starting in full screen because of last time and would crash when trying to come out of it.

In the guest, I would run a program that opened multiple Windows and when I tried to close a window the whole guest OS would hang. However, it didn't hang permanently. If I left it and went away to do something else, I would find the window closed when I came back later. Hence I was blaming the guest OS. Then when I tried to move the hanging guest OS out of full screen mode it would abort instantly.

Still, I have found something else that may help.

When I execute a **Wine application** from within Ubuntu, all is well until I attempt to close the application.
I click on the close button in the command box and nothing happens other than some changes in coloring. The color change means to me that the application has been informed of the mouse click event via Wine. Yet the action to close the program down has not worked. Just to spoil my theory, Alt-F4 terminates the Wine application correctly.
Something about the propagation of events up and down the chain has gone wrong.

I take it that both VBox and Wine intercept events by inserting themselves into the interrupt chain or whatever terminology modern programmers use for such things. Perhaps some of these chains have been modified by recent kernel updates and now the return to the kernel interrupt handler is somehow failing, leaving the interrupt disabled until a return from some other, unrelated interrupt resets the PIC.

Windows 7 nolonger aborts on switching to full-screen mode for me. In the last 24h, I have received a whole bunch of Windows and Ubuntu updates. I am now running with 3D turned on and the guest OS nolonger crashes.

    The windows updates seemed to clear my problem with individual windows taking exeptionally long times to close. However, the guest OS, Windows7, still takes half an hour (not exagerating) to close. I started a shut down before coming on line to the forum and it has still not shut down. This is a fast PC and it normally takes less than 10s to close the guest OS.

---

### Post by imbjr on 2013-07-16
Looking good here. Only Ubuntu updates though. Something seems to have been resolved and I can go full-screen and back without any trouble - at least far more than than I could. Only time will tell if this is a solid resolution.

---

