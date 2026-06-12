---
title: "Ubuntu Studio 14.04 Jack/Firewire: D-BUS: JACK server could not be started."
date: 2015-07-14
forum: Ubuntu Studio
---

### Post by mjones1949 on 2015-07-14
Running Ubuntu Studio 14.04 on Dell optiplex 330. Have Belkin F5u508 Firewire card, and TI firewire card (only one installed at a time). both work fine under windows 7. I am trying to use a Presonus FP10. This set up worked fine on other computers up to about Ubuntu 12.04. I recently bought the Dell and installed Ubuntu Studio 14.04. Previous versions have taken a bit of setting up, but once set up they have been rock-solid perfect. At the outset I will state that I don't care about Pulseaudio etc, all I want is my FP10 working through Jack to Ardour this is a purely DAW - no frills!

The message I get when starting the GUI Jackctl is as follows:[INDENT=2]
22:32:29.440 Patchbay deactivated.
22:32:29.505 Statistics reset.
22:32:29.524 ALSA connection change.
22:32:29.696 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
22:32:29.707 ALSA connection graph change.
(qjackctl:2777): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2777): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
22:32:40.082 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:2777): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2777): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
Mon Jul 13 22:32:39 2015: Starting jack server...
Mon Jul 13 22:32:39 2015: JACK server starting in realtime mode with priority 10
Mon Jul 13 22:32:40 2015: ERROR: firewire ERR: FFADO: Error creating virtual device
Mon Jul 13 22:32:40 2015: ERROR: Cannot attach audio driver
Mon Jul 13 22:32:40 2015: ERROR: JackServer::Open failed with -1
Mon Jul 13 22:32:40 2015: ERROR: Failed to open server
Mon Jul 13 22:32:41 2015: Saving settings to "/home/michael/.config/jack/conf.xml" ...
[/INDENT]

There is more, but its already fallen over by this point. I have trawled the internet until I'm blue in the face, I've tried all sorts of suggestions but I can get nowhere with this, I've re-installed, messed it all up and reinstalled again, but no joy. At one point, after much thrashing about, I did get it to link to the FP10 for about 20 seconds then it dropped out. Could not re-create the conditions again. Is as simple as neither of my Firewire cards is supported by Linux? In earlier versions of Linus there were groups, to be set up, raw1394 to be enabled, priorities to be set, but as far as I can see, these are not options for 14.04 - it should just work straight out of the box.

I can't believe that there is not a known answer to this issue as the forums are littered with this same question, but there is never a definitive answer, its always, try this, and try that and the thread trails off either without arriving at a solution or it all miraculously strats towork for no apparent reason.

Sorry about the rant, but I can't see why this is so hard and I'm really at my wits end trying to resolve this. If I don't get a solution soon, I shall probably remove 14.04 and go back to something like 9.10 or try AVLinux.

Anybody any ideas ? Please?

Thanks - Michael

---

### Post by jejeman on 2015-07-17
I gave up on my firewire audio card, since JACK won't work for kernel >3.2. (NEC & MSI chipsets), and there are no more laptops with firewire port. I went for USB card.
I think I got it working on VIA chipset on kernel 3.5 (12.10), but I need to confirm that. There are no TI chipsets in my country.

I don't have time to troubleshoot the issue, and with whom (kernel, FFADO, JACK devs)? In my brief test FFADO works (test signals), but JACK does not.
AVLinux won't help, or any distro with >3.2 kernel. I still have AVLinux6 with 3.0 kernel installed on my laptop and it works, all latter versions does not work.
My guess, something changed in kernel since 3.2 version.

---

### Post by mjones1949 on 2015-07-22
Hi, thanks for the comments. I have long supported Linux and Studio in particular. Earlier versions were always rock solid once the initial settings had been sorted out. USB is not really an option as I shelled out a lot of money for the FP10 which is an excellent piece of equipment for my purposes so for the time being I need Firewire. I did load up AVLinux which actually impressed me. Overall it seems more responsive and makes fewer demands on resources, but, predictably enough Firewire still fails and in this respect I note your comments about using a kernel <=3.2. I might be tempted to give that a whirl. However, we specialise in recording classical music so the demands for low latency are not very stringent, but reliability is, given that one movement of a concerto might be 20 minutes long, a system crash is disasterous. This was one of the main motivating factors for the move to Linux some years ago. I have to say that in recent years, apart from an odd virus, Windows XP on our computers has not suffered a system crash ( it has been crashed by faulty software), so I decided to see what was available for Windows. I was pleased to find that Ardour, my favourite DAW, and Jack can now be run on windows. You can only get Ardour 4 for windows as an unsupported Beta from nightly downloads. Once I had Jack and Jack Portaudio cracked it all worked very well in Windows 7 64 bit. My intention now is to make the PC dual boot windows 7 and XP: configure the XP partition purely for DAW, strip out unnecessary stuff, network, but no internet and see how that goes. I'm sorry to ditch Ubuntu Studio, but its just too hard and no solutions to my issue.
(I still have two laptops and another desktop running older versions of Ubuntu Studio (9.04 and 9.10) so these are still available as reliable recording PCs.)

---

### Post by jejeman on 2015-08-08
I confirm that with VIA chipset firewire controller JACK works on UbuntuStudio 14.04 (kernel 3.13.0-57-lowlatency).
Maybe you can try to find some old VIA card.

---

### Post by mjones1949 on 2015-08-12
Thanks for the tip, I'll see what I can find - shouldn't be too hard to find.

---

