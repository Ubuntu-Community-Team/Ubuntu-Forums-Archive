---
title: "help &quot;E: Couldn't find package linux-headers-2.6.31-21-server&quot;"
date: 2010-07-29
forum: Server Platforms
---

### Post by captainentropy on 2010-07-29
Hi, I'm trying to install some nvidia drivers but I need to install the correct headers. 
 
uname -r says: 2.6.31-21-server
 
but I can't find the headers anywhere to install. 2.6.31-21 and 2.6.31-21-generic are installed but not the server version. It's not showing up in synaptic and using apt-get I get the error message in the title.
 
I have 2.6.31-22-server headers but for some reason when I boot into 2.6.31-22 the OS can't see my 3ware cards and, obviously, the arrays they control. So, I can't use 2.6.31-22 yet.
 
Any ideas?

---

### Post by arrrghhh on 2010-07-29
Synaptic?  Are you running ubuntu-server... or not?

Typically the command ```
sudo apt-get install linux-headers-`uname -r`
``` is all you need.

---

### Post by captainentropy on 2010-07-29
yes, Ubuntu 9.10 Server. 
 
And as I said, when I use *apt-get install linux-headers-2.6.31-21-server* I get the error in the title (E: Couldn't find package linux-headers-2.6.31-21-server).

---

### Post by arrrghhh on 2010-07-30
> **captainentropy said:**
> yes, Ubuntu 9.10 Server. 
 
And as I said, when I use *apt-get install linux-headers-2.6.31-21-server* I get the error in the title (E: Couldn't find package linux-headers-2.6.31-21-server).

I'm not calling you a liar, but can you post the output of everything?  The command you submit, and all output until you get a prompt?

---

### Post by captainentropy on 2010-07-30
I suppose there was no way of you knowing but I did paste all the output. Here's the verbatim:
 
>  
> genuser@megatron:~$ uname -r
2.6.31-21-server
genuser@megatron:~$ sudo apt-get install linux-headers-2.6.31-21-server
[sudo] password for genuser: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package linux-headers-2.6.31-21-server
genuser@megatron:~$ 

 
If I were to try to install the headers for 2.6.31-21 (without "-server") it says they are already installed. 
 
I guess this begs the question, do the headers ever reflect the "server" release? This is all for an attempt to install some nvidia drivers. It seems I can't proceed without fixing this.

---

### Post by arrrghhh on 2010-07-30
> **captainentropy said:**
> I guess this begs the question, do the headers ever reflect the "server" release? This is all for an attempt to install some nvidia drivers. It seems I can't proceed without fixing this.

Odd, any reason why you're trying to install nvidia drivers on a server rig?

I had this issue before... I can't remember what the resolution was.  I'll see if I can dig it up.

Der, do you have build-essential installed?  Per [this](http://ubuntuforums.org/showthread.php?t=204181) thread.

---

### Post by brettg on 2010-07-30
Have you tried doing an apt-get update?

---

### Post by captainentropy on 2010-07-30
ok, before I read the last two replies I applied some other updates and restarted the server. I forgot to select the 2.6.31-21 release so it booted the 2.6.31-22 release and it magically recognized my two arrays, which it had never done before. So, I installed the headers for 2.6.31-22-server and then tried to install the nvidia divers (ctrl-alt F1, etc.) and it installed them no problem. Yah!
 
BUT. The remote desktop is now broken. I can connect to the server, I can see the desktop, but I can only move the cursor, nothing else. When I access the server directly it behaves as it should, nice and smooth. GRRRRRR! I tell ya, I hate linux sometimes.
 
I was installing the nvidia drivers because I thought the old video card (integrated Matrox) or default drivers for nvidia support were behind this OTHER problem I'm having [http://ubuntuforums.org/showthread.php?p=9654916](http://ubuntuforums.org/showthread.php?p=9654916)
 
Now it's even worse. I'm going to attemp to install x11vnc thinking vino might be the problem.
 
And to answer arrrghhh's laast question, I installed the desktop on the server because I use Matlab a lot for image analysis. If it wasn't for that I might not have installed it, but frankly, having a desktop is so much nicer to work with.
 
If I can't resolve these problems, I may just ditch ubuntu and install Redhat or CentOS or some other server optimized distro.
 
 
Thanks for all your comments, it was helpful.

---

### Post by CharlesA on 2010-07-30
If you've got a GUI installed, turn off desktop effects, as they don't really play nice with VNC.

---

### Post by captainentropy on 2010-08-02
thanks CharlesA, turning off the desktop effects did the trick. Vino is still a little sluggish but it's better than before with the integrated Matrox chip.

---

### Post by arrrghhh on 2010-08-03
Desktop effects?  Server?  Really?

I... I just don't get it.

---

### Post by captainentropy on 2010-08-03
Yes. Server. Belch. Apparently. How the &*!# am I supposed to know desktop effects are turned on by default? I didn't design the damn OS.
 
I'm not sure what part of "First Cup of Ubuntu" says "I'm an Ubuntu/Linux" guru but apparently smugness shades everything that way.

---

### Post by arrrghhh on 2010-08-03
> **captainentropy said:**
> Yes. Server. Belch. Apparently. How the &*!# am I supposed to know desktop effects are turned on by default? I didn't design the damn OS.
 
I'm not sure what part of "First Cup of Ubuntu" says "I'm an Ubuntu/Linux" guru but apparently smugness shades everything that way.

I don't think anyone is trying to be smug here... I'm just confused as to why you had desktop effects enabled on the server edition.  The server edition doesn't have a GUI... so therefore no desktop effects.

If, however, you do install the ubuntu-desktop package then you'll basically get everything that's included in the desktop distro... and you might as well just install that.  No point in installing a server OS if you're going to put a GUI on top of it really.

---

### Post by captainentropy on 2010-08-04
I'm trying to be clear when I write responses, perhaps I haven't been.
 
The desktop effects were on by default, *I did not turn them on. *Actually, I didn't know there were "desktop effects" and I'm not sure what those are on linux.
 
As for the server OS, well, it is a file and application server (dual Xeon 2.4GHz CPUs, 24GB RAM, X-25 SSD OS drives, and two 12TB arrays) and since Ubuntu Server's kernel is supposed to be optimized for a server environment, whatever that is (it isn't just a "headless" desktop Ubuntu), I chose that. As I said, I use it to run MATLAB for image and data analysis. Not very convenient to do that on a machine with no desktop. I tried setting up vino-server on the "headless" Ubuntu Server but I couldn't get it to work. I couldn't keep wasting time going that route so I run the Gnome desktop and use VNC on my workstation (Windows 7) to connect to it through vino. It's still a little slow but way better with the nvidia card installed. It'll do for now.

---

### Post by arrrghhh on 2010-08-04
Sounds like you should just install ubuntu-desktop.  As I said before, if you want a GUI, just do that.  Don't use the server install if you need a GUI, it causes more headache than it's worth (as you've found).

---

