---
title: "Howto: Mustek 1200 UB Plus USB Scanner Install / Setup"
date: 2006-04-03
forum: Tutorials
---

### Post by williamts99 on 2006-04-03
An easy, cut and paste way to get The Mustek 1200 UB Plus USB Scanner or one of it's clones working in Ubuntu Breezy through Ubuntu Maverick and beyond.

Open the Terminal(Applications>Accessories>Terminal), copy and paste the following one at a time.

To get to the proper directory:
```
cd /usr/share/sane/gt68xx
```
To download the driver firmware file sbfw.usb from the [SANE gt68xx-backend site]("http://www.meier-geinitz.de/sane/gt68xx-backend/"):
```
sudo wget http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/sbfw.usb
```
Then open the gt68xx.conf file for editing:
```
sudo gedit /etc/sane.d/gt68xx.conf
```
Replace / Uncomment:  hint: use ctrl+f to find
```
#override "mustek-scanexpress-1200-ub-plus"
```
With:
```
override "mustek-scanexpress-1200-ub-plus"
```

That's all there is to it, now you can go to Applications>Graphics>XSane Image Scanner(or SimpleScan) to scan your images.
Enjoy!!

The only thing better would be a script to do it for you :-)
Edit: A mirror location just in case the sbfw.usb host goes down. [http://www.multiupload.com/4LNXQQKTC6](http://www.multiupload.com/4LNXQQKTC6)

---

### Post by zarazooo on 2006-10-12
:D thx

---

### Post by williamts99 on 2006-10-23
No problem, glad it helped someone :-)

---

### Post by visible on 2007-01-27
I don't know how you folks figure this stuff out bot, I am so glad you do! thanks for the great info! works 100%  Even better than in windows!
:guitar:

---

### Post by wolfsandwich on 2007-02-06
i tried but it didn't work for me, i keep getting the "no devices available" message.  i have the MUSTEK PLUG-N-SCAN 1200 USB.  it was still in the box (and wrapped in plastic) when i bought it last week and i've got the cd's that came with it, but i can't seem to figure out how to make the thing work with my ubuntu 6.06.  just to see if it works i tried it on my old windows98 laptop and it installed and scanned well. 

any help would be greatly appreciated.

thanks.

---

### Post by alienexplorers on 2007-02-07
Try loading sane and xsane, then add the libsane and libsane-extras files.  I needed these to get my Mustek model 4800 running.

---

### Post by kimo_2020 on 2007-04-18
merciiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii

---

### Post by wolfsandwich on 2007-07-27
my solution:  buy another scanner for five dollars,  give the other scanner to a friend.

---

### Post by naught101 on 2007-10-08
that's a nice howto ;) thanks.

---

### Post by robc02 on 2007-11-26
I am trying to get my Mustek Scanmagic 1200USB working.

lsusb gives:

     Bus 004 Device 003: ID 055f:0003 Mustek Systems, Inc. ScanExpress 1200 USB

I have followed the above instructions but Xsane reports "no devices available"

sane-find-scanner gives:

      found USB scanner (vendor=0x055f, product=0x0003, chip=MA-1017) at libusb:004:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

scanimage-L gives:

   No scanners were identified. If you were expecting something different,
   check that the scanner is plugged in, turned on and detected by the
   sane-find-scanner tool (if appropriate). Please read the documentation
   which came with this software (README, FAQ, manpages)

I am not sure what to do next - any ideas?

---

### Post by williamts99 on 2007-12-10
The 1200USB models are not the same as the 1200UB models, they use different hardware and are not supported by this method.  Though if someone has an extra they might want to donate, you can see if Martin is interested. [http://lists.alioth.debian.org/pipermail/sane-devel/2004-August/011685.html](http://lists.alioth.debian.org/pipermail/sane-devel/2004-August/011685.html)

---

### Post by dregoroid on 2007-12-20
thanks for this howto. success with my 1200ub plus

---

### Post by gps_ on 2008-01-06
Thank you for this - very straight forward!

---

### Post by TomGar on 2008-03-22
perfect howto - thanks

---

### Post by EndorphinE on 2008-07-04
Scanner is working, thanks a lot :)

---

### Post by daevyd on 2008-07-22
Many, many thanks for this thread.  This particular scanner really stinks to install in Windows and after having a terrible time getting my Lexmark printer to work, I was a tad bit worried about my scanner but NOOOO it was a snap!  Awesome!!  (I can't find the thanks button for some reason).

---

### Post by amado738 on 2008-08-12
xsane closes each time i try to scan

any ideas?

I have a mustek 1200ub plus running ubuntu hardy heron!

---

### Post by williamts99 on 2009-01-21
> **amado738 said:**
> xsane closes each time i try to scan

any ideas?

I have a mustek 1200ub plus running ubuntu hardy heron!

If you haven't done so already, you should start a new thread for your issue, and run it from the terminal, that way you can see any error messages.

---

### Post by mmck on 2009-02-25
working fine, thanks...

---

### Post by trukker on 2009-03-10
Thanks for the help... scanner worked but output is terrible...

I have a mustek 1248 usb

email is [email]truckdriver737@hotmail.com[/email] if anyone has any ideas

:popcorn:

---

### Post by tzepu on 2009-04-12
thanks, it worked like a charm with a  Mustek 1200 UB Plus on Jaunty

---

### Post by DominicWatson on 2009-06-26
Thank you! Still working in 2009 :)

---

### Post by &quot;franceschini&quot; on 2009-07-10
I thank you very much for your help about
my Mustek 1200UB plus.....MERCI et encore MERCI !!!
I' m a new Jaunty Jackalope biginer 'sand  a fan now.:D
Bye Bye Vista !

---

### Post by Peopleunit on 2009-07-17
Now that was easy!

Note: In the conf file there were about four sections that had the same text for the scanner name... commented out. I just uncommented the second line of the first section it showed up in by removing the first character of that line.

Thank you :KS

---

### Post by pmetcher on 2009-09-01
Great post, clear instructions, got my scanner working first time, thanks very much :)

---

### Post by rosario.scumaci on 2009-10-26
Grazie = THANKS

---

### Post by mmck on 2010-03-08
thank you very much, works with karmic...

---

### Post by ronlevett on 2010-04-11
Am I in the wrong forum? I am trying to get a Mustek scanner 2448TA to work on my XP computer. It seizes up.

---

### Post by Mspirit on 2010-06-06
Thanks...after all these years I got to use this scanner with such an ease XD

---

### Post by J@n on 2010-08-10
Thanks to williamts99!

Simple How-to that worked like a charm :D

In my particular case I needed to reboot the machine before the scanner was detected. No prob.;)

Greetz,

J@n

---

### Post by Flos Headford on 2010-08-22
Thank you very much, williamts99!
Three years after it was written, it is still an object lesson in How To write a How To.
My scanner works, and it was easier than Windoze.
Phil

---

### Post by Borodiychuk on 2010-11-01
Tested with Maverick 10.10: Works well, thanks a lot! :)

---

### Post by mmck on 2010-11-03
Tested on 10.04 Lucid, works, thank you very much... 
(even though written 3 years ago thanks again)

---

### Post by bach42t on 2010-12-03
> **Borodiychuk said:**
> Tested with Maverick 10.10: Works well, thanks a lot! :)

Hi,
I'm on Maverik 10.10 too but does'nt work: with xsane I've this error:

"Non è possibile aprire il dispositivo 'gt68xx:libusb:002:003': l'argomento non è valido"

That in english is something like:

"Impossibile open the device 'gt68xx:libusb:002:003': invalid argument"

And, with lsusb, i see that 002:003 is the scanner:


federico@federico-F5SL:~$ lsusb
Bus 003 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385/ScanMagic 1200 UB Plus Scanner
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 006: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC Webcam
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any idea?


Missing permission:

federico@federico-F5SL:/usr/share/sane/gt68xx$ sudo chmod a+r *

Now works

---

### Post by alchimisto on 2010-12-06
Thanks ;)

---

### Post by williamts99 on 2010-12-06
Nice to see it's still working! :)

---

### Post by frozonecom on 2011-05-25
WOOOOW!! Thanks for this! I finally got my scanner to work! You know that they're hard to get to work with vista? WOW. with linux, I only needed 5 minutes to make it work! Thank you very much for this!

**EDIT:** Can someone help me? The scanner is detected and it works but, the output is really terrible. The problem is the the image(output) is really blurry. I tried different DPI's from 75-2400 and the blurry-ness is  still there. Please help!

---

### Post by mmck on 2011-06-14
nice, thanks...

---

### Post by Amirosperros on 2011-08-17
Hi every1,

have Mustek BearPaw 1200TA that is detected by "SimpleScan" bu after clicking scan it shouts: " unable to connect to scanner". The scanner is powered on and connected by USB cable. The lsusb gives:

Bus 002 Device 003: ID 055f:021e Mustek Systems, Inc. BearPaw 1200 TA/CS

so what is wrong, please help

---

### Post by J@n on 2011-11-06
Hi williamts99,

Tx a lot. After 5,5  years this how-to is still working great. Took me 2 minutes to find your post and get my Mustek 1200 UB Plus working:)

Greetz,

J@n

---

### Post by williamts99 on 2011-11-07
> **frozonecom said:**
> WOOOOW!! Thanks for this! I finally got my scanner to work! You know that they're hard to get to work with vista? WOW. with linux, I only needed 5 minutes to make it work! Thank you very much for this!

**EDIT:** Can someone help me? The scanner is detected and it works but, the output is really terrible. The problem is the the image(output) is really blurry. I tried different DPI's from 75-2400 and the blurry-ness is  still there. Please help!

What is the your output from the command:
lsusb

---

### Post by williamts99 on 2011-11-07
> **Amirosperros said:**
> Hi every1,

have Mustek BearPaw 1200TA that is detected by "SimpleScan" bu after clicking scan it shouts: " unable to connect to scanner". The scanner is powered on and connected by USB cable. The lsusb gives:

Bus 002 Device 003: ID 055f:021e Mustek Systems, Inc. BearPaw 1200 TA/CS

so what is wrong, please help

Wrong device for this thread, you should post a new thread concerning your issues.

---

### Post by reddleman79 on 2012-03-15
And another happy scanner! Thanks

---

### Post by berlinick on 2012-04-09
Just followed the instructions on my Maverick. Worked perfectly. Thank you so much!

---

### Post by MarkX on 2012-10-16
Yipppeee it worked!

Now WTF doesn't Ubuntu do this automatically?
Next job: get it to detect a 4gb sd card, and my monitor..... :-(

---

### Post by williamts99 on 2012-11-30
> **MarkX said:**
> Yipppeee it worked!

Now WTF doesn't Ubuntu do this automatically?
Next job: get it to detect a 4gb sd card, and my monitor..... :-(

Glad it worked, the reason is that the scanner driver for this model isn't freely available, and it could get Ubuntu into hot water if it were to distribute it.  So you have to do it manually, just like stuff from [http://www.medibuntu.org/](http://www.medibuntu.org/)

As far as your 4GB SD card, might want to check hardware compatability as some readers don't support 4GB plus cards, or SDHC(there is a difference between 4GB SD card and a 4GB SDHC card).  Good luck!

---

