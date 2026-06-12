---
title: "SERP2 built-in webcam and Hardy?"
date: 2008-04-29
forum: System76 Support
---

### Post by asmiller-ke6seh on 2008-04-29
This is addressed to the folks at System76, but if anyone has information regarding the impending functionality for the SERP2 webcam (there was hope that Hardy might give the System76 folks the toold they needed to get the built-in webcam up and running)

Is there an ETA for built-in webcam functionality under Hardy Heron? This has been on the hot list for more than a year ... and with each new release we have been told, "We're working on it." It reminds me of the old computer industry joke about "You said you'd have that feature ready in the 1st Quarter." To which the marketing guy replies under his breath, "Yeah. But we didn't say 1st Quarter of which year."

I just want to know if I should continue to wait, or just go out and purchase an Ubuntu compatible notebook webcam to clip on my Serval Performance SERP2.

And while we're on the subject, it would be nice to have the fingerprint reader up and running with password login functionality for at least logging in to Ubuntu, but that's just a nice to have, for me.

---

### Post by steveneddy on 2008-04-29
> **asmiller-ke6seh said:**
> 

I just want to know if I should continue to wait, or just go out and purchase an Ubuntu compatible notebook webcam to clip on my Serval Performance SERP2.



I'm saving my pennies for an off board camera, like one of the Logitech laptop clip on cams.

---

### Post by asmiller-ke6seh on 2008-04-30
Yeah. I probably will, too. But it's so clunky, having to clip it, run a wire, and plug into another USB port (I am already using one for my trackball). It's kind of contrary to the reason why I bought a laptop; if I wanted to deal with wires, I would have gotten one of those cute mini- units.

---

### Post by Luke has no name on 2008-05-02
> **asmiller-ke6seh said:**
> This is addressed to the folks at System76, but if anyone has information regarding the impending functionality for the SERP2 webcam (there was hope that Hardy might give the System76 folks the toold they needed to get the built-in webcam up and running)

Is there an ETA for built-in webcam functionality under Hardy Heron? This has been on the hot list for more than a year ... and with each new release we have been told, "We're working on it." 

Wait... you're telling me that System76 sells you a component in a laptop that is not supported in the operating system? the webcam is just dead there on the laptop?

---

### Post by asmiller-ke6seh on 2008-05-02
> **Luke has no name said:**
> Wait... you're telling me that System76 sells you a component in a laptop that is not supported in the operating system? the webcam is just dead there on the laptop?

No, that's not what I am saying. When I bought the SERP2, I was told that this would be enabled in the future. The chip used in this webcam is/was not supported by the available Open Source solutions for webcams. However, System76 has represented that they would get this working, and that there was some kind of priority to get this done.

Everytime there is a new Ubuntu release, I like to check in to see if they think there will be a solution made available. It's really no big deal ... just a nice to have. I spent about $1200 for the laptop, so what's another $50 to $100 for an external webcam.

However, as I stated, I would really like to see support for the internal webcam.

Also, I understand that the SERP3 and SERP4 have webcams with supported chips.

---

### Post by hkarl629 on 2008-05-07
I too am asking this same question re the SERP 2 webcam. As newer models come on stream with working web cams our SERP 2's are being left behind. I'm waiting.

H Karl Juelch
[email]juelch@davtv.com[/email]

---

### Post by thomasaaron on 2008-05-09
SUPPORT FOR THE SERP2 WEBCAM!

This information is courtesy of a System76 customer. I'll not list his name here for privacy reasons, but I will point him to this thread in case he wants to get involved in any discussing this issue further. 

Below are his instructions. We will be testing in the shop too, but I think he hit the nail on the head. So if anybody out there wants to try it...

Once we're finished testing in the shop, we will release the fix in the System76 driver.

The driver for the webcam is here:  [https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

Instructions on downloading and building the driver follow.  For more
thorough instructions, I'd recommend looking at
[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft).

GETTING THE SERVAL PERFORMANCE (SERP2) WEB CAM TO WORK

Since we'll be compiling a kernel driver, you'll need to install the
kernel source files:

$ sudo apt-get install kernel-package linux-source build-essential

Next you'll need to install 'git' so we can download the driver's source code:

$ sudo apt-get install git-core gitk git-gui git-doc curl

Now we'll download the webcam driver:

$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

Let's compile the kernel module (webcam driver):

$ cd microdia
$ make

Load our new kernel driver:

$ sudo insmod ./microdia.ko

Check to see that the driver loaded successfully:

$ dmesg

You should see something like this at the bottom of the output:

[107348.616179] microdia: Microdia USB2.0 webcam driver startup
[107348.616563] microdia: Microdia USB2.0 Webcam - Product ID 624F.
[107348.616570] microdia: Release: 0100
[107348.616574] microdia: Number of interfaces : 1
[107348.623570] microdia: Microdia USB2.0 Camera is now controlling
video device /dev/video0
[107348.623950] usbcore: registered new interface driver usb_microdia_driver

If you run into any problems, see
[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)
for more details.

Please note that I didn't write the driver; I just discovered it this
evening and got it running.  Also, using "insmod ./microdia.ko" only
loads the driver until you reboot your machine.  The driver won't be
loaded automatically unless you take further steps (see the link
above).  I haven't played with the webcam too much yet, but I did test
is briefly using VLC:

$ sudo apt-get install vlc
$ vlc

Once VLC is running, select File > Open Capture Device...  Set the
"Video device name" to /dev/video0 (or whatever appears in the dmesg
output above).  Click OK.  You should see a window displaying the
webcam video.

---

### Post by asmiller-ke6seh on 2008-05-10
smiles

applause

---

### Post by hkarl629 on 2008-05-23
You and I own Serval 2's and have been waiting for the web cam to be activated. I'm a complete novice at Linux/Ubuntu so the lingo is like a foreign language to me. In the posts above is Tom giving the instructions to make the web cam operational, or is there something more to come?

I would like to get this feature up and running.

Your response will be appreciated.

Sincerely

Karl Juelch

---

### Post by asmiller-ke6seh on 2008-05-26
> **hkarl629 said:**
> You and I own Serval 2's and have been waiting for the web cam to be activated. I'm a complete novice at Linux/Ubuntu so the lingo is like a foreign language to me. In the posts above is Tom giving the instructions to make the web cam operational, or is there something more to come?

I would like to get this feature up and running.

Your response will be appreciated.

Sincerely

Karl Juelch

Yes, and Yes. The fix will be in some future release of the System 76 driver, but you can use this formula to "roll your own."

---

### Post by hkarl629 on 2008-05-28
Thanks for the reply.  Considering my lack of knowledge, I think I'll wait for the System 76 release rather than try the "roll your own" approach.  I guess 'safe rather than sorry' would be a better course of action for me.

H Karl 

Bluffton, SC

---

### Post by steveneddy on 2008-05-29
What about the Serp 1 ?

---

### Post by asmiller-ke6seh on 2008-05-30
> **thomasaaron said:**
> SUPPORT FOR THE SERP2 WEBCAM!

This information is courtesy of a System76 customer. I'll not list his name here for privacy reasons, but I will point him to this thread in case he wants to get involved in any discussing this issue further. 

Below are his instructions. We will be testing in the shop too, but I think he hit the nail on the head. So if anybody out there wants to try it...

Once we're finished testing in the shop, we will release the fix in the System76 driver.

The driver for the webcam is here:  [https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

...


I followed the instructions (above, and in the google groups page, listed above) it's WORKING!!!

Thanks Thomas Aaron and the Mystery People who found this solution.

T.A. - you can tell your Development and Support people that this driver works and can be used as the basis of adding the Web Cam to the System76 Driver support. It's 640 x 480, full color. But most of all, IT WORKS.

---

### Post by steveneddy on 2008-05-30
I tried to get this to work last night, and at least **[COLOR="Blue"]lsusb[/COLOR]** lists it in the list now as a Microdia product.

I will have to do a little more experimenting to get it to be sucessful on my Serp 1.

So, this may come down as a System76 driver update?

---

### Post by thomasaaron on 2008-05-30
It will.

---

### Post by steveneddy on 2008-05-31
> **thomasaaron said:**
> It will.

Even for the Serp 1, Aaron?

EDIT:

It works perfectly now.

Amazing!

Even with Skype.

---

### Post by steveneddy on 2008-06-04
I wonder, gentlemen, what we could do to get this driver into the Linux kernel so we don't have to install it ourselves?

Maybe someone has already done it? Or is going to?

It does seem to work very well, though, with the cam in my Serval Performance Type 1.

---

### Post by steveneddy on 2008-06-06
OK - got the web cam working. Now if we can just get the dial up modem working, I will have a perfectly working laptop!

Any chance of a modem driver rattling around anywhere for the Serp type 1?

---

### Post by hkarl629 on 2008-06-10
Have you tried the "roll your own" approach to the wweb cam problem on your Serp 2?  If. "yes" ow did it turn out?

My unfamiliarity with the inner workings of ubuntu make me very hesitant to tackle the fix Tom posted.

Thank you.

H Karl Juelch

---

### Post by steveneddy on 2008-06-10
> **hkarl629 said:**
> Have you tried the "roll your own" approach to the wweb cam problem on your Serp 2?  If. "yes" ow did it turn out?

My unfamiliarity with the inner workings of ubuntu make me very hesitant to tackle the fix Tom posted.

Thank you.

H Karl Juelch

Dude, I got a Serp 1 and it works great.

If you can't do it, just come over and I'll do it for you.

---

### Post by steveneddy on 2008-06-21
If we have this module installed when the System76 driver with this patch in it comes down, would we need to uninstall the module we previously manually installed? 

Do you think that this camera module should become a permanent part of the Linux Kernel so others can benefit from this work?

---

### Post by thomasaaron on 2008-06-23
We're having a hard time getting this working on 64-bit Hardy. What are you guys using? 32-bit?

Has anyone got it working in 64-bit?

---

### Post by steveneddy on 2008-06-23
> **thomasaaron said:**
> We're having a hard time getting this working on 64-bit Hardy. What are you guys using? 32-bit?

Has anyone got it working in 64-bit?

I'm using 64 bit. Works fine here. But I'm on a Serp Type 1.

EDIT:

I used your instruction on the first page, Aaron.

And [look here]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft").

At the bottom of this page it talks about trouble shooting.

Try these commands after inserting the module into the kernel:

```

$sudo modprobe videodev

$sudo modprobe compat-ioctl32

```

These are things I had to do to get it working.

Works great with Skype. Guy on the other end Sunday morning was on Windows and said my cam looked better than his.

---

### Post by asmiller-ke6seh on 2008-06-24
> **thomasaaron said:**
> We're having a hard time getting this working on 64-bit Hardy. What are you guys using? 32-bit?

Has anyone got it working in 64-bit?

I got it working on a Serp2 in 32-bit Ubuntu. I know --- Serp2 --- Dual Core --- but I am waiting until 64-bit Ubuntu is just as smoothly functional as 32-bit.

---

### Post by steveneddy on 2008-06-24
> **asmiller-ke6seh said:**
> I got it working on a Serp2 in 32-bit Ubuntu. I know --- Serp2 --- Dual Core --- but I am waiting until 64-bit Ubuntu is just as smoothly functional as 32-bit.

That's funny because I moved to 64 bit in Feisty so my machine ran smoother.

It runs better on 64 than 32.

Hardy is smooth as butter on 64. Try it, you'll like it.

---

### Post by asmiller-ke6seh on 2008-06-24
"Hello? I believe we have a penguin on the tele. What? Size 9!"

It's 10 o'clock, and time for the penguin on the top of your television set to explode.

---

### Post by 982000971 on 2008-06-25
I got as far as "Make" in the instructions before it spit out the following error

root@ubuntu:~/microdia# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: ctags: Command not found
make: *** [ctags] Error 127
root@ubuntu:~/microdia#

Solutions? The instructions say Error 127 means that the module is not in the proper location, but it doesn't tell me how to solve it.

---

### Post by thomasaaron on 2008-06-25
you need to install ctags
```
sudo apt-get install ctags
```

---

### Post by 982000971 on 2008-06-26
Thanks! That got me one step further, but now...

root@ubuntu:~/microdia# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
root@ubuntu:~/microdia# insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module
root@ubuntu:~/microdia#

---

### Post by thomasaaron on 2008-06-26
Yep. That's where I'm stuck too. Working on it...

---

### Post by steveneddy on 2008-06-26
> **982000971 said:**
> Thanks! That got me one step further, but now...

root@ubuntu:~/microdia# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
root@ubuntu:~/microdia# insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module
root@ubuntu:~/microdia#

From the link that thomasaaron posted on the first page of this thread:

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

> 
Troubleshooting insmod errors

# insmod microdia.ko
[COLOR="Red"]**insmod: error inserting 'microdia.ko': -1 Unknown symbol in module**[/COLOR]
 

See the output of #dmesg

the last few lines would be complaints about missing symbols, depending upon whats missing 

you may not have loaded the modules that module depends on,
So it failed with those error messages. You would need to modprobe for that module's dependencies
 

[COLOR="Red"][B]Try

$sudo modprobe videodev

$sudo modprobe compat-ioctl32

then

$sudo insmod microdia.ko[/B][/COLOR]


This is what I suggested be done earlier.

This is what I had to do to get the module to be inserted into my kernel, and there were three kernel upgrades at this time and I had to do this all three times to put the module into each kernel.

---

### Post by godbyk on 2008-06-28
Hello, everyone.

I'll admit that I'm Thomas's "mystery person" who emailed him the original instructions.  I wanted to let everyone know that I've posted the instructions on my blog and that I've updated them to work around a couple of the problems people have been experiencing.  Additionally, I've added instructions for installing the kernel module and getting it to load automatically every time your boot your computer.

[http://kevin.godby.org/2008/05/09/howto-serval-performance-serp2-webcam/](http://kevin.godby.org/2008/05/09/howto-serval-performance-serp2-webcam/)

Please let me know if you run into any problems with these instructions and I'll try to keep them up to date.  (I've also subscribed to this thread, so I'll try to jump in and help where I can.  Please note, however, that I'm not involved in the development of the driver itself -- I'm just a System76 customer who took a little time to track it down.)

Also, for reference, I'm running this on a Serval Performance (SERP2) machine with Ubuntu Hardy (8.04), 32-bit.  I'm thrilled to see that the driver has been working for folks with earlier Servals and 64-bit Linux.

---

### Post by steveneddy on 2008-06-28
> **godbyk said:**
> Hello, everyone.

I'll admit that I'm Thomas's "mystery person" who emailed him the original instructions.  I wanted to let everyone know that I've posted the instructions on my blog and that I've updated them to work around a couple of the problems people have been experiencing.  Additionally, I've added instructions for installing the kernel module and getting it to load automatically every time your boot your computer.

[http://kevin.godby.org/2008/05/09/howto-serval-performance-serp2-webcam/](http://kevin.godby.org/2008/05/09/howto-serval-performance-serp2-webcam/)

Please let me know if you run into any problems with these instructions and I'll try to keep them up to date.  (I've also subscribed to this thread, so I'll try to jump in and help where I can.  Please note, however, that I'm not involved in the development of the driver itself -- I'm just a System76 customer who took a little time to track it down.)

Also, for reference, I'm running this on a Serval Performance (SERP2) machine with Ubuntu Hardy (8.04), 32-bit.  I'm thrilled to see that the driver has been working for folks with earlier Servals and 64-bit Linux.

Very nice. I see that you seem to have discovered that the order of loading modules is different than the original website states.

I will follow your instructions on the next kernel update.

I will confirm that after a fresh install that the kernel module loaded with no problems or issues.

Thank you for you post on this thread. This is going to help many people.

---

### Post by godbyk on 2008-06-28
Yeah, when I first wrote the instructions I left out the videodev module.  Either I simply forgot to add it to my notes or I had loaded it previously while I was testing out drivers.  But I've seen the same error message about missing symbols, and loading the videodev module has always solved that problem for me.  

One note: I've never had to load the compat-ioctl32 module.  The microdia and videodev modules are the only ones I've needed to load for the device to work.  Has anyone else needed to load compat-ioctl32 specifically?  If so, which laptop (version) and Ubuntu version are you using?  32-bit or 16-bit?

---

### Post by steveneddy on 2008-06-28
> **godbyk said:**
> Yeah, when I first wrote the instructions I left out the videodev module.  Either I simply forgot to add it to my notes or I had loaded it previously while I was testing out drivers.  But I've seen the same error message about missing symbols, and loading the videodev module has always solved that problem for me.  

One note: I've never had to load the compat-ioctl32 module.  The microdia and videodev modules are the only ones I've needed to load for the device to work.  Has anyone else needed to load compat-ioctl32 specifically?  If so, which laptop (version) and Ubuntu version are you using?  32-bit or 16-bit?

I did, but only because it was in the instruction on the original page for the device driver under the troubleshooting section. I don't really know if I needed that module or not, but it's done and the cam works.

The camera actually has a very clear picture and there is no delay when you call it. Very nice. Thanks for searching and finding this wonderful piece of software.

---

### Post by asmiller-ke6seh on 2009-02-19
The following quotations are from back in May of 2008:

> **steveneddy said:**
> I tried to get this to work last night, and at least **[COLOR="Blue"]lsusb[/COLOR]** lists it in the list now as a Microdia product.

I will have to do a little more experimenting to get it to be sucessful on my Serp 1.

So, this may come down as a System76 driver update?

> **thomasaaron said:**
> It will.

THAT IS A PLAIN COMMITMENT BY SYSTEM 76's TECHNICAL REPRESENTATIVE. IT WAS SAID WITHOUT EQUIVOCATION.

I bought my SERP2 way back about the time of Dapper Drake (maybe earlier). We have been promised the built-in web cam driver for the SERP2 would be integrated into the SYSTEM76 driver. Jaunty Jackalope is already in development and testing. How much longer must we wait.

At this point, I am disappointed in System 76's failure to deliver on their commitment.

Who else is still waiting in disappointment?

After all this time, and demonstration of extreme patience with, and loyalty to, System 76, I feel that it is reasonable for me to say that I am upset AND disappointed.

Please! Please! Please! It's time to make good on your obligation. Don't cause potential customers to doubt System 76's commitment; don't make it look like you are happy to take our money and then forget us long-term committed customers. Don't create bad feelings with your long-time customers or else when it comes time to purchase another Linux computer we will probably walk away -- especially as hardware support for Ubuntu continues to improve. I bought System 76 because I believed I could count on your company.

To help you understand how I feel with the wait for support for the SERP2, pick up and read Samuel Beckett's "Waiting for Godot".

---

### Post by val67 on 2009-02-20
I think this is the biggest problem with S76 and Ubuntu:

 Future updates might break working installs, and s76 drivers not capable of fixing'em. (see also daru2 and power mgmt, an 9 months unsolved issue)

 Unfortunately s76 focuses on the very last release (Ibex 64 bit, now) putting those with Hardy LTS on second place.

 I always thought the 6 months Ubuntu release cycle is to short; it merely allows for current bugs to be sorted out, by the time you have to upgrade again. Then the circle goes on and on.


 If s76 claims they support Hardy LTS (valid till 2011), why can't we buy laptops with hardy preinstalled?

---

### Post by thomasaaron on 2009-02-20
```
THAT IS A PLAIN COMMITMENT BY SYSTEM 76's TECHNICAL REPRESENTATIVE. IT WAS SAID WITHOUT EQUIVOCATION.
```

Unfortunately, I can't get the camera to work at all on our shop model. It won't install, and a few of us have banged our head against the wall substantially with it.

I will keep trying, though.

> If s76 claims they support Hardy LTS (valid till 2011), why can't we buy laptops with hardy preinstalled? 

This is a strategic and logistical decision made by those higher up in the company than I will ever be. 

The vast majority of our customers want the latest version of Ubuntu. Very very few have requested Hardy, and those who want Hardy generally are server customers. We do offer a Hardy installation option for Servers. 

Essentially, it takes a ton of time and effort to manage the imaging servers, updates and troubleshooting for any particular version -- and it seems to make the most sense to expend that time and effort on the versions that almost all of our customers want -- the latest one.

Also, Hardy lacks some support for ATI graphics,which we are starting to use on some of our newer desktop systems.

We do try to support our desktop and laptop customers who have Hardy installed, and we are happy to walk any of our customers through installing it.

---

### Post by hkarl629 on 2009-02-20
I have voiced my unhappiness with the state of the Serp2 webcam. My purchase date was June 25, 2007! That's a long wait for a promise to come true.

I did get it working and want it to make Skype live up to its capabilities. Whatever the various upgrades did to it, now it is useless. We bought it with the expectation that it would work or be made to work.

Maybe System 76 is understaffed.

H. Karl Juelch

---

### Post by thomasaaron on 2009-02-21
Is Henry the only one whose SerP2 webcam is broken due to updates?

Also, Henry, what version of Ubuntu are you currently running?

EDIT... I sent you an email with a request for some more information.

---

### Post by hkarl629 on 2009-02-21
Tom,

I'm running Hardy Heron on my Serp2.

As I've said in my response to your more info request, I'm really making an assumption that an upgrade 'hosed' the camera. I'm to inexperienced to really know. It did work for a while and now, for some time, it doesn't.

Henry

---

### Post by hkarl629 on 2009-02-25
I've been struggling to get the web cam in my Serp2 working. Using Hardy 32 bit.  The camera worked for a while then quit. Tom is working on getting my camera working again.

What did you do to get it to function? I know you were without the camera for a good while.  

I.m very new at Ubuntu. Think the Serp2 is a great computer but I want to be able to use Skype to its fullest.

Your comments?

Thank you.

Karl

---

### Post by asmiller-ke6seh on 2009-02-28
Anyone want to buy a SERP2? I think it might be time to find a fully-supported Ubuntu-compatible laptop, including webcam.

Then again, maybe my kids want a laptop and don't care that the webcam doesn't work.Or, maybe I can eBay it for use under Windows, where the webcam is supported. I still have the original packaging, including the Windows driver disk. All it would need is a Windows operating system, and with Windows 7 about to be released, Windows XP will be availble on the cheap.

---

### Post by brijohn on 2009-03-15
I'm one of the developers of said driver as well as an owner of my own SERP2, one of the reasons I got involved with this project to begin with :-)

The SERP2 webcam should work just fine with the driver in question. I've been using it for the last year since we first got it working with 624f webcam used in the this computer.

Since the original posting by Tom in this thread the driver has evolved and changed quite abit including having its named change from microdia to sn9c20x since we only really support the sn9c20x chipset. One thing thats has changed since then is we have gotten rid of in kernel format conversion after successfully implementing hardware format switching. This however means that many applications won't work with the limited formats supported by the camera and therefor you will need to use libv4l to do user space format conversion.

If you are having trouble getting this driver to work on a SERP2 let me know I'll be glad to try and help.


And tom what problem are you having getting it installed on your shop computer? I do all my development for this driver on my SERP2 and haven't had any issues installing the driver.

---

### Post by hkarl629 on 2009-03-15
Hello brijohn,
I'm an owner of A Serp2 also. I got the camera working when I was running Hardy. I want to use it with Skype primarily. Then it stopped working and I can't get it going. Tom has been on the case and so far has not had success. With Tom's help I have installed the 64 bit Ubuntu 8.10. Which works quite well. Now I would like to get the camera working with this OS. I am new to Linux/Ubuntu so detailed (step by step)and complete instructions that I can follow are what I need.

Can you help?

I would appreciate it.

Sincerely,

hkarl629

---

### Post by brijohn on 2009-03-16
hkarl629,

I do not know what you have tried so far but below is a set of
instructions for compiling both the sn9c20x driver and the necessary
userspace library libv4l. Since you are using a 64bit system and skype is
only available as 32bit application you will need to compile both 32bit
and 64bit versions of libv4l.

If you have any questions just let me know

Install SN9C20X Webcam driver on SERP2 from latest git HEAD

First make sure to install necessary build environment
# sudo make install linux-headers-`uname -r` git-core build-essential

Next grab a copy of the driver source from the git repository
# git clone git://repo.or.cz/microdia.git
# cd microdia

Build it using the following command
# make

To install the driver so that it loads every boot do the following
# sudo cp ./sn9c20x.ko /lib/modules/`uname -r`/kernel/ubuntu/misc/media/
# sudo depmod -a
# sudo modprobe sn9c20x

This should load the module and set it to load automatically on every boot.
To check that it has found your camera type the following
# dmesg
Expected Output:
> sn9c20x: SN9C20X USB 2.0 Webcam - 0C45:624F plugged-in.
> sn9c20x: Detected OV9650 Sensor.
> sn9c20x: Webcam device 0C45:624F is now controlling video device /dev/video0
> sn9c20x: Using yuv420 output format
> usbcore: registered new interface driver sn9c20x
> sn9c20x: SN9C20x USB 2.0 Webcam Driver v2009.01 loaded

Installing libv4l

libv4l is needed for two reasons. 1) using it you can use older applications that only support
the v4l1 API, sn9c20x only supports v4l2. 2) many applications such as skype do not natively 
support the video output formats that the sn9c20x driver uses. 

Note: intrepid and above have this library in their repositories. Its called libv4l-0.
      I still recommend getting and installing the latest version though.

Download the source from the following location: [http://people.atrpms.net/~hdegoede/libv4l-0.5.9.tar.gz](http://people.atrpms.net/~hdegoede/libv4l-0.5.9.tar.gz)

Extract the source archive
# tar xzvf libv4l-0.5.9.tar.gz

Compile and install libv4l
# cd libv4l-0.5.9
# make
# make install PREFIX=/usr/

If your camera was detected properly when installing the driver and you have successfully built
and installed libv4l the following commands should test the driver using mplayer
# export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
# mplayer tv:// -tv driver=v4l2:width=320:height=240:outfmt=bgr24:fps=30

If you need to compile the library as 32bits on 64bit system for use with 32bit applications (Skype).
Try the following

First make sure to install multilib support for 32bit compilation
# sudo aptitude install gcc-multilib libc6-i386 lib6-dev-i386

Next in the libv4l-0.5.9 directory type the following
# gedit libv4l2/Makefile libv4l1/Makefile libv4lconvert/Makefile

gedit should open with 3 tabs for each makefile. Next we will do the same thing for each Makefile
find the line near the top that looks like this CFLAGS := -g -O1, add the -m32 onto the end. 
Next hit enter to create a new line and add the following LDFLAGS := -m32
Thing should look like this when you are done

CFLAGS := -g -O1 -m32
LDFLAGS := -m32
CFLAGS += -Wall -Wno-unused -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes

Do that for all three Makefiles you opened and then save them.

Now close gedit and go back to the command line
# make
# make install PREFIX=/usr/ LIBDIR=/usr/lib32

This should give you a 32bit version of the library to use with 32bit applications

---

### Post by hkarl629 on 2009-03-16
brijohn,
WOW! For a nearly 80 year old Ubuntu neophyte this looks like more than I can bite off. There's no one in this area that can guide me through this process. Tom Aaron at System 76 has been great helping me with some of the things I have done, but nothing this extensive.  I've been waiting for Sys76 to get this problem worked out but so far they seem stymied. Maybe more pressing issues to resolve. Have been good to me though.

I will print out your instructions and ponder over them. This seems to require a "talking through" session to assure it will work.

In your instructions there is a line that tells about testing the driver using mplayer - there is a "Smiley" face obscuring the character directly after =240__ utfmt.   I know the need for accuracy and the wrong character(s) would negate the whole effort.

Sincerely, Thank you for your detailed answer. Your concern and willingness to help is very much appreciated.

hkarl629

---

### Post by jdb on 2009-03-17
> **hkarl629 said:**
> brijohn,
WOW! For a nearly 80 year old Ubuntu neophyte this looks like more than I can bite off. There's no one in this area that can guide me through this process. Tom Aaron at System 76 has been great helping me with some of the things I have done, but nothing this extensive.  I've been waiting for Sys76 to get this problem worked out but so far they seem stymied. Maybe more pressing issues to resolve. Have been good to me though.

I will print out your instructions and ponder over them. This seems to require a "talking through" session to assure it will work.

In your instructions there is a line that tells about testing the driver using mplayer - there is a "Smiley" face obscuring the character directly after =240__ utfmt.   I know the need for accuracy and the wrong character(s) would negate the whole effort.

Sincerely, Thank you for your detailed answer. Your concern and willingness to help is very much appreciated.

hkarl629

This is what that line should have looked like:

```
# mplayer tv:// -tv driver=v4l2:width=320:height=240:outfmt=bgr24:fps= 30
```

```
:o
``` becomes :o if it's not put in a code box.

Yeah, that's a couple notches above the average linux user's comfort level.

Maybe using brijohn's post, System76 can package something up in their custom drivers.

jdb

---

### Post by brijohn on 2009-03-17
Yes as jdb said this
```

mplayer tv:// -tv driver=v4l2:width=320:height=240:outfmt=bgr24:fps=30

```
is what i meant to say my original post has been updated and should fix the Smilely issue. Really who is genius idea was it have forum software decidide it knows what I meant better then me anyways (^-^)

Yeah I'm aware if you're really new to linux and ubuntu this may be abit much i did try to give a full step by step of each command needed though. If you are having trouble getting it to work with those instructions feel free to IM me sometime and I'll try and help walk you through things if you need it.

---

### Post by asmiller-ke6seh on 2009-03-27
> **brijohn said:**
> >snip<

Install SN9C20X Webcam driver on SERP2 from latest git HEAD

First make sure to install necessary build environment
# sudo make install linux-headers-`uname -r` git-core build-essential

-----------%<---cut---------%<---------------

Do that for all three Makefiles you opened and then save them.

Now close gedit and go back to the command line
# make
# make install PREFIX=/usr/ LIBDIR=/usr/lib32

This should give you a 32bit version of the library to use with 32bit applications

brijohn,

You have done all of us a great service. All of us with the Microdia webcam in our Serp2 laptops can now enjoy the use of this piece of included hardware if we can follow your recipe. Unfortunately, there are people who are still waiting for System76 to deliver on the promise of turnkey Ubuntu in our systems through the support that we believed we where purchasing along with the System76 hardware.

Could you add your information to the System76 Knowledge base at: [http://knowledge76.com/index.php/Main_Page](http://knowledge76.com/index.php/Main_Page) - this will make it easier for all System76 users to find the instruction than having to search the support board.

Again, you have our thanks.

---

### Post by brijohn on 2009-03-27
> **asmiller-ke6seh said:**
> brijohn,

Could you add your information to the System76 Knowledge base at: [http://knowledge76.com/index.php/Main_Page](http://knowledge76.com/index.php/Main_Page) - this will make it easier for all System76 users to find the instruction than having to search the support board.



Done. This information can now be found under the Desktop Howto's section of the Knowledge base.

---

### Post by thomasaaron on 2009-03-27
I will test this next week on our shop computers. If it works well, we will add it to the System76 Driver.

Does it work in 64-bit?

---

### Post by brijohn on 2009-03-27
Yes, it should work fine under 64bit

---

### Post by asmiller-ke6seh on 2010-02-21
I went away, in frustration, from this forum. However, recently I remembered having stomped away in disgust, BUT -

With the release of Ubuntu 9.10, I found that the webcam in my SERP2 (yes, I still have and am still using my SERP2 ... my kids didn't want my "old laptop") is now JUST WORKING - no need to roll my own driver. All I had to do was load Karmic Koala and there it was.

However, when my wife wanted a netbook for use in Grad school, we bought her an Acer Aspire One with Windows 7, and I just installed Ubuntu Netbook Remix over Windows 7 (we will never have any Microsoft product in our home ... not even a Microsoft keyboard or mouse).

That little netbook is really nice. For $300, it does anything she wants, and Ubuntu Netbook Remix make good use of the 600 pixel high display. It cost me less than $20 to buy an ativa 2GB USB memory device. The web camera in that little netbook is so bright in low light that I wish I had THAT web camera in my "old laptop" -- but at least my SERP2 web cam is now working without having to wait for, or employ, a System76 driver. In fact, I no longer use the System 76 driver on my SERP2 - seems that it is totally unnecessary since Karmic,

Ubuntu is certainly a ready for prime time operating system. When I recently bought a brand new, state of the art HP printer (HP Deskjet F4480), I brought it home, plugged it in, and Ubuntu saw it and installed it, completely plug and play. The only thing I needed to do manually was to install the HP graphic Device manager - and that I was able to find in the Ubuntu repository. It even makes it transparent to access and use the scanner in the HP printer/scanner.

---

