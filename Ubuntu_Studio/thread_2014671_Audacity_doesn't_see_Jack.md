---
title: "Audacity doesn't see Jack"
date: 2012-07-02
forum: Ubuntu Studio
---

### Post by Gaaargh on 2012-07-02
Hi all,
Trying to get a Firepod working in Ubuntu 12.04. I've installed Jack and it seems to detect my Firepod. The light is blue and I can see the inputs and outputs in the connections window. However, I cannot see Audacity in the connections and I cannot see the  "Jack Audio Connection Kit" in Audacity's device toolbar either. One other thing worth noting is that I am connected through a firewire expresscard adapter (Startech 13942). Audacity version is 2.0.0 and Jack version is 0.3.8. 

Can anyone suggest where I need to go from here to get Audacity to detect my Firepod?

---

### Post by CrocoDuck on 2012-07-04
Hi, make some experiment in order to know if your device is properly working (you may use meterbridge to view and route to output the input signals). If the device is ok you'll be sure that we have an Audacity issue. Have a look at here:

[http://wiki.audacityteam.org/wiki/Mixer_Toolbar_Issues](http://wiki.audacityteam.org/wiki/Mixer_Toolbar_Issues) 

I guess you are using FFADO under jack, I never used it. Have a look at related guides and utilities: as Audacity can run with ALSA without needing jack running, maybe it can work with FFADO without needing jack running too.

---

### Post by sgx on 2012-07-04
> **Gaaargh said:**
> Hi all,
Trying to get a Firepod working in Ubuntu 12.04. I've installed Jack and it seems to detect my Firepod. The light is blue and I can see the inputs and outputs in the connections window. However, I cannot see Audacity in the connections and I cannot see the  "Jack Audio Connection Kit" in Audacity's device toolbar either. One other thing worth noting is that I am connected through a firewire expresscard adapter (Startech 13942). Audacity version is 2.0.0 and Jack version is 0.3.8. 

Can anyone suggest where I need to go from here to get Audacity to detect my Firepod?
Hi, for audacity to appear in qjackctl, press record, then
press pause, go to qjackctl and 'portaudio' will be the audacity connection.

You also need to choose jackd in audacity i/o preferences first.

I like to record single tracks in timemachine, then import them
into audacity for edits and conversions. Saves a lot of screen
real estate, and records nice 24 bit .w64, or .wav files.

Cheers

---

### Post by Gaaargh on 2012-07-05
> **CrocoDuck said:**
> Hi, make some experiment in order to know if  your device is properly working (you may use meterbridge to view and  route to output the input signals). If the device is ok you'll be sure  that we have an Audacity issue. Have a look at here:

Thanks for that. Tried to install meterbridge there, but it wouldn't compile, it couldn't find Jack. Now I'm confused. I assume it looked in  /usr/lib/, where from what I can see, qjackctl is installed. Is there  some difference between jack, jackd and qjackctl? Maybe I installed qjackctl, but not Jack? Is that even possible?


> **sgx said:**
> Hi, for audacity to appear in qjackctl, press record, then
press pause, go to qjackctl and 'portaudio' will be the audacity connection.

You also need to choose jackd in audacity i/o preferences first.
Thanks for that. Unfortunately, currently jackd doesn't show up in Audacity at all, so I can't get to that next step. But hopefully it will work like that eventually when I figure out why Audacity doesn't display Jack as an option.

---

### Post by CrocoDuck on 2012-07-05
> **Gaaargh said:**
> Thanks for that. Tried to install meterbridge there, but it wouldn't compile, it couldn't find Jack. Now I'm confused. I assume it looked in  /usr/lib/, where from what I can see, qjackctl is installed. Is there  some difference between jack, jackd and qjackctl? Maybe I installed qjackctl, but not Jack? Is that even possible?

What distro are you using? And how did you installed jack? You should be able to install all of these packages with apt, synaptic or software center (if you are under Ubuntu or other debian-based distro). Basically, jackd is the jack audio server daemon ([http://en.wikipedia.org/wiki/Daemon_(computing](http://en.wikipedia.org/wiki/Daemon_(computing))). You use it to launch jack with the needed options. Qjackctl is an user GUI for the jack configuration. It depends on jack, so it can't work without it. If you install Qjackctl with some kind of package manager the dependencies are automatically solved (and jackd is a dependence). You must have build dependencies in order to build Qjackctl. So you should have jack.

Repost the output of this:

```
cat .jackdrc 
```

---

### Post by Gaaargh on 2012-07-05
> **CrocoDuck said:**
> What distro are you using? And how did you installed jack? You should be able to install all of these packages with apt, synaptic or software center (if you are under Ubuntu or other debian-based distro). Basically, jackd is the jack audio server daemon ([http://en.wikipedia.org/wiki/Daemon_(computing]("http://en.wikipedia.org/wiki/Daemon_%28computing"))). You use it to launch jack with the needed options. Qjackctl is an user GUI for the jack configuration. It depends on jack, so it can't work without it. If you install Qjackctl with some kind of package manager the dependencies are automatically solved (and jackd is a dependence). You must have build dependencies in order to build Qjackctl. So you should have jack.

Repost the output of this:

```
cat .jackdrc 
```

Thanks CrocoDuck. I'm on ubuntu 12.04. I installed Jack with "sudo apt-get install qjackctl". I figured that, as you say, it would solve the dependencies itself. That said, the only way I seem to be able to get it to run with the firepod is with "sudo qjackctl". 

Here's the output of "cat .jackdrc":
```
/usr/bin/jackd -dfirewire -dhw:0 -r44100 -p128 -n3
```I was trying to install meterbridge 0.9.2, got from [launchpad.net]("https://launchpad.net/ubuntu/+source/meterbridge/0.9.2-9"). I went with the first tarball. Got as far as "sudo make install", that's where it failed, saying it couldn't find Jack in the packages.

---

### Post by CrocoDuck on 2012-07-05
Output comes as expected, but the needing for sudo when launching Qjackctl makes me wondering about permissions... Lets check jackd permissions: 

```
ls -l /usr/bin/jackd
```

and repost the output. Did you followed some guide for your firewire-jack setup? If so, repost it.

---

### Post by Gaaargh on 2012-07-05
> **CrocoDuck said:**
> Output comes as expected, but the needing for sudo when launching Qjackctl makes me wondering about permissions... Lets check jackd permissions: 

```
ls -l /usr/bin/jackd
```and repost the output. Did you followed some guide for your firewire-jack setup? If so, repost it.

Yeah, if I don't use sudo, I get " [COLOR=#ff0000]D-BUS: JACK server could not be started. Sorry[/COLOR]". 
Here's the output of "ls -l /usr/bin/jackd":

```
-rwxr-xr-x 1 root root 26404 Feb 10 15:04 /usr/bin/jackd
```I followed the [community guide for firewire]("https://help.ubuntu.com/community/FireWire"), to set up Jack. I'm on 12.04, so it recommended skipping some steps.

---

### Post by CrocoDuck on 2012-07-06
Jackd priorities comes as they should be. The seed of evils is somewhere else... Maybe some other command can help us to see better:

```
groups
```

```
lsmod | grep 'firewire\|1394'
```

```
grep 'firewire\|1394' /proc/interrupts
```

As always, repost the outputs. Hope someone will correct me if I'm wrong, but I feel smells of permission issue somewhere... It could be the explanation for both audacity issues and building issues. Usual configuration should make you able to run jackd (and Qjackctl) without sudo (in my experience, but I never used firewire devices). If you need sudo probably you need sudo for run other applications that needs jack too. I tried "sudo audacity" but it looks like you have to do some setting in order to make him properly working and I really don't know if it is a good idea.

---

### Post by Gaaargh on 2012-07-06
Ok, here's the output of "groups":
```
eoin adm dialout cdrom plugdev lpadmin admin sambashare
```
Here's the output of "lsmod | grep 'firewire\|1394'":
```
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
```
And here's the output of "grep 'firewire\|1394' /proc/interrupts":
```
17:          0          1          2          0   IO-APIC-fasteoi   mmc0, firewire_ohci
```

Does it make any difference that I ran these commands without the firepod plugged into my expresscard adapter?

---

### Post by CrocoDuck on 2012-07-07
> **Gaaargh said:**
> Ok, here's the output of "groups":
```
eoin adm dialout cdrom plugdev lpadmin admin sambashare
```
Here's the output of "lsmod | grep 'firewire\|1394'":
```
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
```
And here's the output of "grep 'firewire\|1394' /proc/interrupts":
```
17:          0          1          2          0   IO-APIC-fasteoi   mmc0, firewire_ohci
```

Does it make any difference that I ran these commands without the firepod plugged into my expresscard adapter?

Perhaps we could see a difference for the last command, but I think that the core of the issue was pointed out by the first one command:

```
eoin adm dialout cdrom plugdev lpadmin admin sambashare
```

we cleary see that your user is not in the audio group. That's why you can't launch jackd without sudo and (probably) why any application launched by your user can't see jack. You have to add your user to the audio group:

First of all make sure that audio group exists:

```
grep -w audio  /etc/group |cut -d: -f1
```

Then, if the output is "audio" (should be it):

```
useradd -G audio eoin
```

Reboot and test.

---

### Post by Gaaargh on 2012-07-07
Ok, here's the output of "grep -w audio /etc/group |cut -d: -f1":
```
audio
```
And here's the output of "useradd -G audio eoin":
```
useradd: user 'eoin' already exists
```
I found that output strange, but I decided to reboot and test anyway. Unfortunately, nothing changed. However, I did try running audacity from terminal (without sudo). I noticed that one of the messages it posts on startup is 

```
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```
Which is exactly the same as one of the messages Jack posts on startup, regardless of whether I use sudo or not. Could this be part of the problem?

---

### Post by CrocoDuck on 2012-07-07
](*,)...So sorry, useradd is to create new users... let's try this way:

```
groups
```

As useradd did'nt worked like I expected (oups:oops:) you should view this:

```
eoin adm dialout cdrom plugdev lpadmin admin sambashare
```

still without audio. If so, this one should make the trick:

```
sudo adduser eoin audio
```


Dunno for the last question, if your user isn't set in audio group.

---

### Post by Gaaargh on 2012-07-07
CrocoDuck, you are a gentleman and a scholar. I used "sudo adduser eoin audio", it worked, I rebooted, started qjackctl from the dash (not from terminal!), it worked, I opened Audacity, there was "Jack Audio Connection Kit", and finally I recorded some flawless input from my Firepod! Thank you so much for spending the time on this. You rock! :guitar:. Hopefully all the inputs are working (I'll check that now), but it seems to be working perfectly at the moment. I'll mess around with it for a while now and make sure everything's in order.
EDIT: Yep, all inputs working great!

---

### Post by sgx on 2012-07-07
In case you or a passer-by wonder, the audacity fx menu is greyed out until you select some or all of the audio, click in the audio, then ctrl a or click-n-drag a portion. Use the zoom functions for precise edit/fx. Then, any installed ladspa plugins can be applied

amb, caps, fil, mcp, omins, rev, swh, tap, vco are names in synaptic, to install, among many at this list

[http://linux-sound.org/plugins.html](http://linux-sound.org/plugins.html)

Using timemachine to record, LV2 and ladspa fx can be inserted
in the signal chain like plugins, for live use, and recording.

Cheers

---

### Post by CrocoDuck on 2012-07-08
> **Gaaargh said:**
> CrocoDuck, you are a gentleman and a scholar. I used "sudo adduser eoin audio", it worked, I rebooted, started qjackctl from the dash (not from terminal!), it worked, I opened Audacity, there was "Jack Audio Connection Kit", and finally I recorded some flawless input from my Firepod! Thank you so much for spending the time on this. You rock! :guitar:. Hopefully all the inputs are working (I'll check that now), but it seems to be working perfectly at the moment. I'll mess around with it for a while now and make sure everything's in order.
EDIT: Yep, all inputs working great!

Glad everything is working\\:D/! If everything is ok (YO!!!) mark the thread as solved. Have fun with your linux studio (we know, the best kind of studio ever!).

---

