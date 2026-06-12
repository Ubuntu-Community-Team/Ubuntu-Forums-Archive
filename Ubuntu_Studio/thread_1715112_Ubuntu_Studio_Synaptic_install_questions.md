---
title: "Ubuntu Studio Synaptic install questions?"
date: 2011-03-26
forum: Ubuntu Studio
---

### Post by SirBartholomew on 2011-03-26
I'm going to install the ubuntu studio packages from the synaptic package manager on a desktop and laptop which are both running ubuntu 10.10 64 right now when I do this I was wondering if it came with a low latency kernel or will I have to install that seperately?

I also noticed there was a new low latency kernel on allesso's website will ubuntu studio automaticly update these kernels?

---

### Post by ailo.at on 2011-03-26
There's no low latency kernel for 10.10, and the Alessio Aboganis PPA is not included by default.
It is possible to use the -lowlatency kernel for 11.04. I've seen a guide somewhere that explains something about it.
Other than that, I would rather recommend 10.04 at this time, if there is no particular reason why you want to use 10.10 instead.

When installing Ubuntu Studio packages, you really only need to install the audio packages you want to use. Installing jackd is a good first step. Just make sure to enable realtime during installation. Also, add yourself to audio group. Changes take effect after loggin out and in again.

---

### Post by SirBartholomew on 2011-03-26
How would I add myself to audio gorup? Sorry new to ubuntu.

---

### Post by ailo.at on 2011-03-26
> **SirBartholomew said:**
> How would I add myself to audio gorup? Sorry new to ubuntu.

You can use, from the menu: System -> Administration -> Users and Groups.
I'm on a different system, but you should find your way to manage groups. Among the groups, find "audio" and make sure you are checked as a member. If it doesn't exist, add it.

The quick way to do add yourself to audio group in a terminal:

To check what groups you are member of, do 
 ```

  groups
```If you're not a member, do (be careful to use those exact flags)

```
sudo usermod -a -G audio <username>

```If the group doesn't exist, do:

```
sudo addgroup audio
```

The reason you need to be in audio group is to be able to run jackd in realtime.

---

### Post by SirBartholomew on 2011-03-26
The second command line you gave me worked but is said "the group audio already exists so I'm guessing I'm good to go?

---

### Post by ailo.at on 2011-03-26
> **SirBartholomew said:**
> The second command line you gave me worked but is said "the group audio already exists so I'm guessing I'm good to go?

Just remembered that doing 

```
groups
```Will only show you what groups you are member of during that login session, so "audio" will only show after you logged in and out again. If you want to inspect the changes directly, you can view the file:

```
gedit /etc/group

```If you're a member of audio group, and you installed jackd choosing "yes" to realtime, you should be good to go.

To make sure the jackd installation went fine, you can check 

```
gedit /etc/security/limits.d/audio.conf
```which should include these two lines:

```
@audio   -  rtprio     95
@audio   -  memlock    unlimited
```That's all you need to run jackd in realtime.
But, on Ubuntu 10.10 you won't achieve very low latencies, without a low-latency kernel.

---

### Post by SirBartholomew on 2011-03-27
it said command not founf for the last command you gave me.

```

bart@Mr-Fantastic-Axess-Terminal1:~$ etc security linits.d dfaudio.conf
No command 'etc' found, did you mean:
 Command 'rtc' from package 'nvram-wakeup' (universe)
 Command 'vtc' from package 'lipsia' (universe)
 Command 'tc' from package 'iproute' (main)
 Command 'htc' from package 'httptunnel' (universe)
 Command 'atc' from package 'bsdgames' (universe)
 Command 'etw' from package 'etw' (universe)
 Command 'dtc' from package 'device-tree-compiler' (main)
etc: command not found
bart@Mr-Fantastic-Axess-Terminal1:~$ 


```
should I of used the gedit command or sudo gedit?

Also I was using vitual keyboard and aconnectgui when I was testing out some of the new programs and the niext time I logged on I lost the timidity in whick in aconnectgui. I was connecting the virtual keyboard  to the timidity in aconnectgui so the keyboard would make sound.

---

### Post by ailo.at on 2011-03-27
/etc/security/limits.d/audio.conf is the path to the file audio.conf. You can use nautilus to navigate to that file and use gedit to view it.
If you need to edit it, you would need to do that as superuser, so

```
gksudo gedit /etc/security/limits.d/audio.conf
```

Haven't used timidity, so can't help there. These configurations will only allow you to have realtime privilege, so the applications would not be affected in any other way.

---

### Post by SirBartholomew on 2011-03-27
There was nothing in the dfaudio file should I just type those lines in there?

---

### Post by ailo.at on 2011-03-27
> **SirBartholomew said:**
> There was nothing in the dfaudio file should I just type those lines in there?

If you installed jackd and chose "yes" for adding realtime privilege, you should have that file in place already. 
If not, yes, you can add it manually.

First try this this in the terminal:

```
sudo dpkg-reconfigure -p high jackd
```That should let you enable realtime and you can check again to see if you have the two "@audio" lines in:

```
gksudo gedit /etc/security/limits.d/audio.conf
```

These are the lines you need. If they are not there, just copy and paste them:

```
@audio   -  rtprio     95
@audio   -  memlock    unlimited
```After that, you'll need to logout/login for changes to take effect.

---

### Post by SirBartholomew on 2011-03-27
They were in there thanks. Now just figuring out how to use jack.

---

