---
title: "Wineasio problems"
date: 2011-02-27
forum: Ubuntu Studio
---

### Post by rev_G on 2011-02-27
I am trying to get the wineasio drivers installed but I keep running into problems. I followed the instructions here:
[http://www.sandgreen.dk/index.php?side=linux_wineasio](http://www.sandgreen.dk/index.php?side=linux_wineasio)

When I type "sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential" I get this message:

Package libjack0.100.0-dev is a virtual package provided by:
  libjack-jackd2-dev 1.9.5~dfsg-19ubuntu1
  libjack-dev 1:0.118+svn3796-7ubuntu1
You should explicitly select one to install.

E: Package 'libjack0.100.0-dev' has no installation candidate

Also, when I type "regsvr32 wineasio.dll" into terminal I get this message: err:module:load_builtin_dll failed to load .so lib for builtin L"wineasio.dll": libjack-0.100.0.so.0: cannot open shared object file: No such file or directory
Failed to load DLL wineasio.dll

---

### Post by Pablo_F on 2011-02-28
Hi, 

Those instructions are obsolete. There have been some changes with regards to jackd. Please, tell us what version of ubuntu you are using. 

EDIT: I see... 10.10

Cheers, Pablo

---

### Post by Pablo_F on 2011-02-28
There are deb packages thanks to falktx :) No need to compile.

Just do a:

**sudo apt-get install wine**

Then follow this link:

[http://sourceforge.net/projects/kxstudio/files/DEBs/](http://sourceforge.net/projects/kxstudio/files/DEBs/)

And open the deb package corresponding to your system (32 or 64 bits). 
Install it.

(I am not sure which is "better" beta0.9 or 0.8.1)

Then:

**regsvr32 wineasio.dll**

And I think that you are done. Otherwise, report the error messages.

Cheers, Pablo

---

### Post by rev_G on 2011-02-28
I am running 10.10 on an Alienware laptop from 2002. So I know not to expect perfect results. I am trying to get the ASIO drivers to run in FL Studio. I found this thread.
[http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057)

I followed the instructions and and got the ASIO driver to show up on FL Studio, but I get an error when I select it. I will have to check what the error is when I get home from work. I made the changes to the Jack settings suggested by the post. When I click start in Jack it says it cannot start. I am guessing that might be my problem.

I apologize if I am not explaining things clearly. I am new to Ubuntu and I am thrilled I can get some use out of my ancient laptop.

---

### Post by Pablo_F on 2011-02-28
> When I click start in Jack it says it cannot start. I am guessing that might be my problem.

Yes, you need jack up and running. That step is crucial. Post the contents of the message window and also, post the output of the terminal command:

cat /proc/asound/cards 

Or are you using a firewire card?

jack configuration depends a lot on the hardware used.

If the laptop is going to be dedicated to music work only, then I recommend a more specialized distro, and, by the time being, based on ubuntu 10.04 rather than on 10.10. I find Tango Studio very good and easy, but there are others aswell.

---

### Post by rev_G on 2011-02-28
Thanks for being so helpful, Pablo!

This is what I get when I click Start on Jack.

21:08:55.394 Patchbay deactivated.
21:08:55.396 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:08:55.509 ALSA connection graph change.
21:08:55.686 ALSA connection change.
21:09:24.775 Startup script...
21:09:24.777 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
21:09:25.180 Startup script terminated with exit status=32512.
21:09:25.181 JACK is starting...
21:09:25.181 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n4 -s -S
21:09:25.196 Could not start JACK. Sorry.
21:09:26.790 JACK was stopped successfully.
21:09:26.791 Post-shutdown script...
21:09:26.792 killall jackd
jackd: no process found
21:09:27.204 Post-shutdown script terminated with exit status=256.

And when I run "cat /proc/asound/cards" this is what I get.


0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with ALC200,200P at irq 11

---

### Post by Pablo_F on 2011-03-01
Hi, 

An onboard card, isn't it. There are so many different ones. 

Anyway:

server path: /usr/bin/jackd -S
options in the left colum: realtime (normally, nothing else is needed).
sample rate: Try 48000
frames/period: 1024
period/buffer: 2

The remainder options look good, driver alsa and interface hw:0 seems OK. What is the output of:

arecord -l && aplay -l 

?

Note that, in order to run jackd in realtime mode, you need rtprio and memlock privileges. What are the output of 

ulimit -r -l

groups

? 

Cheers, Pablo

---

### Post by rev_G on 2011-03-01
arecord -l && aplay -l

**** List of CAPTURE Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 1: Intel ICH - MIC ADC [Intel 82801CA-ICH3 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ulimit -r -l

real-time priority              (-r) 0
max locked memory       (kbytes, -l) 64

---

### Post by Pablo_F on 2011-03-02
Hi,

Please, run this command:

**sudo dpkg-reconfigure -p high jackd2**

Yes, you want rtprio and memlock privileges.

Your user must belong to the audio group, so now do a:

**sudo adduser your_user_name audio**

And restart the computer. Then you will be able to run jackd in realtime mode.

Cheers, Pablo

---

### Post by rev_G on 2011-03-02
When I run **sudo dpkg-reconfigure -p high jackd2** it says jackd2 is not installed. I thought I installed it. Where did I go wrong?

Package `jackd2' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: jackd2 is not installed

---

### Post by Pablo_F on 2011-03-03
I thought you had jackd2 installed, but it could be that you have jackd1. I am trying to guess too much, sorry. Try jackd1 instead of jackd2, and if it does not work either, simply, jackd.  

Cheers, Pablo

---

### Post by rev_G on 2011-03-03
Sorry, I thought I did too. When I go to the audio tab in the Wine Configuration, ALSA and Jack are checked. When I click Test Sound, it says "Audio Test Failed". Could this be part of the problem? Should I uninstall whatever version of Jack I have? And how do I do that?

---

### Post by rev_G on 2011-03-03
I don't think I have any Jack installed. I type "sudo apt-get install qjackctl" and this is what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
qjackctl is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Am I doing something wrong or is there a step after this I am missing?

---

### Post by Pablo_F on 2011-03-03
Hi, 

Surprisingly, in wine configuration enabling alsa only is OK. Sound test does not work for me either, don't worry about that.

By the time being, you need jack up and running in realtime mode. 

Does it start? If not, what are the error messages?

Cheers, Pablo

> qjackctl is already the newest version.
So, you have qjackctl installed, and jackd too, almost certainly sure. I don't know if you have jackd1 or jackd2, but that doesn't matter too much.


So do a:

sudo dpkg-reconfigure -o high jackd1 

or

sudo dpkg-reconfigure -p high jackd2

or 

sudo dpkg-reconfigure -p high jackd

One of those will make a window pop up, and you have to answer yes, then add your user to the audio group and then reboot.

---

### Post by rev_G on 2011-03-03
How do I start it? I downloaded Jack CONTROL, but I am guessing there is something I am not doing.

---

### Post by Pablo_F on 2011-03-03
Hi, 

You will see Jack Control in Applications -> Sound and Video menu (In gnome at least). You launch it, then you set up the jack server (Setup button) as I told you above, accept and close the setup window. Then you start the jack server by means of the Start button.

If it does not start, post the content of the message window, please.

Cheers, Pablo

---

### Post by rev_G on 2011-03-03
Here is what I get when I click start.

19:34:10.853 Patchbay deactivated.
19:34:10.985 Statistics reset.
19:34:11.008 Startup script...
19:34:11.009 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
19:34:11.020 ALSA connection graph change.
sh: artsshell: not found
19:34:11.492 Startup script terminated with exit status=32512.
19:34:11.493 JACK is starting...
19:34:11.495 /usr/bin/jackd1 -dalsa -dhw:0 -r44100 -p1024 -n4 -s -S
19:34:11.505 Could not start JACK. Sorry.
19:34:11.714 ALSA connection change.
19:34:13.434 JACK was stopped with exit status=255.
19:34:13.435 Post-shutdown script...
19:34:13.436 killall jackd
jackd: no process found
19:34:13.850 Post-shutdown script terminated with exit status=256.

---

### Post by Pablo_F on 2011-03-04
Hi, 


In the server path field, you need /*usr/bin/jackd*, not jackd1 or jackd2. 

See you version of jackd by typing in the terminal: *jackd -V*

Refer to my comment #7 and:

If you have jackd1 installed (jackd -V: 0.xxxx.x) leave out *-S* off the "server path"). If you have jackd2 (jackd -V: 1.9.x) append -S to */usr/bin/jackd*

Cheers, Pablo

---

### Post by rev_G on 2011-03-06
Hey! Jack is now running but now no audio drivers are selectable in FL Studio. WineASIO is no longer on the list.

---

### Post by sgx on 2011-03-06
Might be a good time to reinstall a fresh wine, and wineasio, from the repositories, and do the

regsvr32 wineasio.dll

and copy your relevant jackd settings for future reference.
Cheers

---

