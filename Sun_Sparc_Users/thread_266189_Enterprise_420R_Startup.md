---
title: "Enterprise 420R Startup"
date: 2006-09-26
forum: Sun Sparc Users
---

### Post by tuxtax on 2006-09-26
Hi all,

I have recently bought a Sun Enterprise 420R that was in working condition. However, I have no keyboard, mouse, nor graphics card. This is ok, according to Sun's documentation -- output would be sent to the serial port A.

See page 58 (Page #30 internally)
[http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-1078-10.pdf](http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-1078-10.pdf)

[I]"If your server is configured without a local graphics console, you need to attach an alphanumeric (ASCII) terminal (or establish a tip connection) to the server in order to install the system software and to run diagnostic tests. For background information, see 'About Communicating With the Server” on page 28.' "
[/I]

When I turn on the system, all of the fans come on, the power LED is ok, the fault LED is clear, and each power supply light is on. According to the LED documentation, everthing is golden.

Well, I have two serial ports on my x86 box. I have brand new DB25->DB9 cable currently plugged in, DB25 on the 420R, DB9 on my computer. I have attached a brand new null modem to it as well. On my x86 box, I run these commands, each one in a different console in case for some reason my serial port marked as "1" on the motherboard isn't really #1 as far as Linux is concerned.

$ tail -f /dev/ttyS0

$ tail -f /dev/ttyS1

Then I turn on the power, and to my surprise, no output what so ever. So, I tried removing the null modem. No different -- no output whatsoever. Then I repeated these steps using the other serial port on my x86 box. Nothing, null modem or not.

I then read that it might be the actual format of the serial port's pins. The motherboard ships with default RS-432 mode. One person said that it should be switched to RS-232D (which makes some sense). This idea was posted at:

[https://lists.dulug.duke.edu/pipermail/aurora-sparc-user/2002-December/007947.html](https://lists.dulug.duke.edu/pipermail/aurora-sparc-user/2002-December/007947.html)
[I]"Other interesting information that may be helpful to others...

Sun 420r and 450 Enterprise machines serial interfaces (ttya and ttyb) come configured DEFAULT for EIA/RS 422!!!!  You have to look up the jumper settings and change to EIA/RS 232D for minicom or hyperterm to communicate well with them.  

If you have trouble talking to the serial port as a console, this is most likely the problem."
[/I]
 So I consulted the manual on how to change the jumper on the motherboard to change this:

See page 121 (Page #92 internally)
[http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-1080-10.pdf](http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-1080-10.pdf)

[I]"The serial port jumpers on the main logic board (J2804 and J2805) permit the configuration of the system’s two serial ports for either EIA-432 or EIA-232D signal levels. EIA-432 levels are the default standard for North American users. EIA-232D levels are required for digital telecomunication in nations of the European Economic Community."
[/I]

And again, I powered on the system. Totally silent. I tried removing the null modem once more. Nothing. I tried using serial port 2 on my system with and without a null modem. Still nothing.

By this time, I was quite baffled. I removed 3 of the 4 CPU boards, all but the minimum RAM, and I got the same thing: no output at all.

Surely someone has solved this problem before? What am I doing wrong/not doing at all?

---

### Post by tuxtax on 2006-09-27
I connected a Sun keyboard/mouse with a Sun framebuffer card, and I get no video or POST information (i.e. keyboard lights representing an error code). When I turn on the machine, the keyboard beeps, and all of the lights blink once, indicating some sort of a power up. After that, I get nothing. How long should I wait before the POST starts? Is there anyone who has had a problem similar to this?

---

### Post by netztier on 2006-09-28
> **tuxtax said:**
> I connected a Sun keyboard/mouse with a Sun framebuffer card, and I get no video or POST information (i.e. keyboard lights representing an error code). When I turn on the machine, the keyboard beeps, and all of the lights blink once, indicating some sort of a power up. After that, I get nothing. How long should I wait before the POST starts? Is there anyone who has had a problem similar to this?

As far as I know, a Sun will keep quiet on it's serial ports once it detects that a keyboard is connected. I'd suggest to leave the keyboard disconnected and work with the framebuffer & screen and the nullmodem.

Are you positive that the framebuffer works correctly an the screen you connected to it can cope with the signals it gets from the card?

regards

Marc

---

### Post by tuxtax on 2006-09-28
I am sure that the card (PGX64 I believe) is in working condition, and it has a standard VGA output which I have connected to a regular monitor that also works. Does the PGX64 not output normal signals? I thought they did, which is why they had the normal VGA connectors rather than the Sun monitor connectors.

I'm not worried about getting info from the serial port if I have a keyboard/mouse/framebuffer, but even when I have these three, I get no video output, and *no keyboard LEDs that would show the status of an unsuccessful POST*. I don't even know if the POST is running...no output at all.

---

### Post by netztier on 2006-09-28
> **tuxtax said:**
> Does the PGX64 not output normal signals? I thought they did, which is why they had the normal VGA connectors rather than the Sun monitor connectors.

I was asking this question because I've seen it happen that a monitor was believed dead (or even a graphics card) just because the signal delivered to it was beyond the monitors capabilites and it remained "dark".

With the sun machines, it is possible to configure screen resolutions and refresh rates already for the OBP phase of boot. I believe the command was something like 

```
setenv output-device screen:r1024x768x60
```

for a 1024x768 screen at 60Hz. 

Oh.. the speed settings on the null modem were correct, 9600, 8-N-1, right?

Does the 420R have an equivalent to a PC's "clear CMOS" jumper, so you could set the OBP and all it's settings to default? Might be worth a try.

[Downloading the Service Manual...]

Hm.. at a first glance, there's only information about serial port and flash PROM Jumpers. I don't know what the "ROMBO" Jumper does, and Google search for it hasn't brought me any further.

Sorry, this is my wit's end.


kind regards

Marc

---

### Post by civic_si on 2006-09-29
[QUOTE=tuxtax;1554811]I am sure that the card (PGX64 I believe) is in working condition, and it has a standard VGA output which I have connected to a regular monitor that also works. Does the PGX64 not output normal signals? I thought they did, which is why they had the normal VGA connectors rather than the Sun monitor connectors.


i have a enterprise 450 server. when i first got it i hooked up a regular vga monitor to it and i got nothing. I then got a sun monitor from a friend to try it and it works fine i then got video. so i am thinking that they have the same connector but different signals.

---

### Post by jon_k on 2006-11-20
Hi,

Yeah, you'll need to get a PCI card with VGA output. So far I've got a keyboard, VGA video card and etc, hopefully my install can work today.. just got to SCSI drives.

Wish me luck!
I've got a 420R too. Beast of a machine, isnt it?

---

### Post by sovs on 2006-11-30
Hi I just built up a 420r.

I connect to mine with a 'null modem cable' (this is male to female cable) plus a gender changer.  baud settings as in the sun manual.

I have a gfx raptor (pgx32 clone i think) which is hooked upto a sgi monitor (same as sun, different badge) with a hd15 cable.

my 420r came with a broken cdrom drive, so I had to a network install (running rarpd,tftp & a http proxy..).

the screen res is 1280x1024 16bpp, no joy with anything else, and had to add fbset to the rc.local too ](*,) 

is anyone using multiple graphics cards with their e420? i think the gfx raptor cost me 4quid from ebay, so might try to pick up some more :-k

---

### Post by yonderway on 2006-12-20
Try using minicom to talk to your serial port.  I've got a bunch of suns at home, all headless, and this is how I talk to them (with a null modem of course)

---

### Post by netztier on 2006-12-20
> **yonderway said:**
> Try using minicom

agreed. 

**gtkterm** from the universe repositories is also a good choice for the console-inclined users out there ;-)

regards

Marc

---

### Post by sandpiper on 2006-12-20
Not sure if this will help....Had a similar problem with an Ultra 2 .  

Check the diag-level switch? and diag-level flag settings accessed during POST boot. Found in the Service Manual that Serial port output is enabled "only" when diag-level setting is Max or Min and diag-switch? setting is true
Chris

---

### Post by unixfudotnet on 2007-03-26
Any update on this subject? I'm having the same issue.

---

### Post by HiFiJive on 2007-04-25
I just struggled with this problem all day. I read about changing motherboard jumpers, setting the diag-mode, all kinds of wild goose chases. It turned out to be the cable for me. Yes, the cable. I googled for hours and read many posts about using a null modem cable. This did not work for me. I followed these directions with my breakout box and got it working. 
Once you have the correct cable, make sure you boot up w/NO KEYBOARD plugged in. It will default back to ttya (DB25 Port A) on the backplane. Hope this helps.

[IMG]http://conserver.com/consoles/Tracers/tracer-howto.gif[/IMG]

[http://www.conserver.com/consoles/msock.html](http://www.conserver.com/consoles/msock.html)

---

### Post by mattosdf on 2008-07-23
> **netztier said:**
> I was asking this question because I've seen it happen that a monitor was believed dead (or even a graphics card) just because the signal delivered to it was beyond the monitors capabilites and it remained "dark".

With the sun machines, it is possible to configure screen resolutions and refresh rates already for the OBP phase of boot. I believe the command was something like 

```
setenv output-device screen:r1024x768x60
```

for a 1024x768 screen at 60Hz. 

Oh.. the speed settings on the null modem were correct, 9600, 8-N-1, right?

Does the 420R have an equivalent to a PC's "clear CMOS" jumper, so you could set the OBP and all it's settings to default? Might be worth a try.

[Downloading the Service Manual...]

Hm.. at a first glance, there's only information about serial port and flash PROM Jumpers. I don't know what the "ROMBO" Jumper does, and Google search for it hasn't brought me any further.

Sorry, this is my wit's end.


kind regards

Marc
about Downloading the Service Manual.

does anyone knows where can i find a sun enterprise 450 Service Manual/owner guide for download? I cant find in sun´s site.
thanks

Ps: i read in this post, that e450 with original pc card db15 wont work in vga monitor, onlu sun db15 monitor? is it true?
keyboard type 5 i know its ok, but type 6 will work too?

---

