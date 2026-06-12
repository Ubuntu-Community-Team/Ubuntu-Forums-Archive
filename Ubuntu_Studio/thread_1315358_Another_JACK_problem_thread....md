---
title: "Another JACK problem thread..."
date: 2009-11-05
forum: Ubuntu Studio
---

### Post by eeter on 2009-11-05
So here I go again... Seems like there's no end with audio problems in Ubuntu.
Yesterday night I managed to finally install UbuntuStudio Karmic Koala. It's nice but still I cannot use JACK because of loads of xruns and huge CPU consumption by any application using JACK. Also the software I'm using for my production work is not running very well (only way I can do it is though wine :-?)
As I've been investigating these problems for a month already I've done everything I know that can be done and I have tested different settings for JACK. In most cases JACK produces at least one xrun already during startup and when there is no applications open and connected though it.

yes, I have followed the classical suggestion to add these two lines to */etc/security/limits.conf* file:
```
@audio          -       rtprio          99
@audio	 	- 	nice 		&#8722;10
```

Yes, I _am_ a member of group '_audio_':
```
urmo@urmuntu:~$ groups urmo
urmo : urmo adm dialout cdrom audio plugdev lpadmin admin sambashare
```


Of cause I _have real-time kernel_:
```
urmo@urmuntu:~$ uname -r
2.6.31-9-rt

```

What else is there to do to make things work smoothly?
I really need help because I'm already so depressed after several failed installations and attempts to configure Ubuntu to handle audio as it should be normal. I finally need to start working on my music again, but during one month I have had time to create only 2 tracks but I haven't had a chance to work like I want - using wine as a workaround is also painful, as it's buggy as well, but at least it runs much faster.

---

### Post by AutoStatic on 2009-11-05
You could try adding the following line to */etc/security/limits.conf*:
```
@audio - memlock unlimited  # maximum locked-in-memory address space (KB)
```

And you're using your onboard card right? With which sample rate? Those HDA Intel thingies like 48000 most.
There are some other options you could try, like modifying your fstab and */etc/sysctl.conf*. Did you look into that already? You can find more info here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

---

### Post by sgx on 2009-11-05
To narrow down the possible villains, try running a jackd setup totally
as root user, just jackd, qjackctl, and an instrument like hydrogen or zynaddsubfx, all started by root. Once that minimal setup works, (records pristine sound, regardless of some xruns) compare the exact same setup run by the normal user. Draw conclusions, make adjustments, keep notes.
I used this recently on a non-Ubuntu setup, while having a sudden rash of serious problems after some updates, that led me in the end to shut off SMP support in Reaper 3.13, as a temporary fix while using vsts, and using
a root environment when using wine based apps alongside native linux apps.

I downloaded Karmic 9.10, will install on a usb stick tonight for testing.

---

### Post by sgx on 2009-11-05
Just discovered libpulse (installed with mplayer as a dependancy) was
the source of my jackd thread getting zombified when using wine to run windows audio software. Consider removing all libpulse/pulseaudio software as a possible enhancement to your audio system.

---

### Post by AutoStatic on 2009-11-06
> **sgx said:**
> To narrow down the possible villains, try running a jackd setup totally
as root user, just jackd, qjackctl, and an instrument like hydrogen or zynaddsubfx, all started by root.Why would you do this? If stuff doesn't work well in a normal user account then you misconfigured something. You don't need to run everything as root to figure that out. But if it works for you that's good. I wouldn't advise it though, next thing you know is that everyone runs all kinds of apps with root priviliges because they think it runs better that way, undermining the whole security model of GNU/Linux.

---

### Post by sgx on 2009-11-07
> **AutoStatic said:**
> Why would you do this? If stuff doesn't work well in a normal user account then you misconfigured something. You don't need to run everything as root to figure that out. But if it works for you that's good. I wouldn't advise it though, next thing you know is that everyone runs all kinds of apps with root priviliges because they think it runs better that way, undermining the whole security model of GNU/Linux.
There is a lot of buggy, untested, uncompleted software in linuxland that is properly configured, and still fails. User/root priveledges are common to many realtime kernel linux audio probems. Software can be seriously flawed, and if it is, running it as root likely won't cure it. If software works when running in a simple root-only test, you quickly know you have hope to change some settings, likely the software is not at fault. 
A few guitar/keyboard players are not going to crush the linux security model with an occasional test. A lot of serious windows/Mac musicians don't allow internet connections on their DAW. A necessity for them, but good practice even in our relatively secure systems, rootkits making the rounds as they sometimes do...

---

### Post by AutoStatic on 2009-11-08
> **sgx said:**
> There is a lot of buggy, untested, uncompleted software in linuxland that is properly configured, and still fails. User/root priveledges are common to many realtime kernel linux audio probems.
Software can be seriously flawed, and if it is, running it as root likely won't cure it. If software works when running in a simple root-only test, you quickly know you have hope to change some settings, likely the software is not at fault.And what if it works with root privileges and you can't find the cause of the issue? Then you keep running it as root?
> **sgx said:**
> A few guitar/keyboard players are not going to crush the linux security model with an occasional test.I agree, but it's simply the beginning of the end.

But this doesn't help eeter, he probably threw his PC out of the window in the meantime.

---

### Post by paddedcell on 2009-11-08
just out of interest Eeter, what software are you trying to use? It seems that the other couple of posters here have an insight but the casual observer will not. 

I take it your system works ok under windows, but is unstable with the same settings in Linux?

I would like a little more info about your set up, just as a matter of info. It could be something as simple as running your audio in the 'red line' (I am a motor mechanic by day) all the time. 

iain

---

### Post by paddedcell on 2009-11-08
> **sgx said:**
> . A lot of serious windows/Mac musicians don't allow internet connections on their DAW. A necessity for them, but good practice even in our relatively secure systems, rootkits making the rounds as they sometimes do...

The computer in my studio has no internet connection, in fact the studio also has no phone line to ensure that the computer cant be connected that easily. As I am new to the linux experience I am worried about how hard it will be to upgrade the software when new patches come out. 

I am first a studio owner, computers are the medium I use to record. They are a tool so must either be very easy to use or extremely powerful. I hope that its the second as the first has yet to rear its head.

iain

---

