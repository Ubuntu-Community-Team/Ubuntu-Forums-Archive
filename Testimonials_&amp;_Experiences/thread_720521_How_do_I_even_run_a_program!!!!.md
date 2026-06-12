---
title: "How do I even run a program!!!!?????"
date: 2008-03-10
forum: Testimonials &amp; Experiences
---

### Post by etothepi on 2008-03-10
Ok, I'm getting seriously sick of this.  I've been "using" Linux for a week, and cannot do even the most basic of ******** commands.

I've not been able to even install anything!  I have no idea what is going on with so many stupid things, and I am getting progressively less convinced of Linux's "superiority."

Why can't I just install some stupid nVidia drivers without a ******* hassle?  Why do I try to install Envy, and Ubuntu asks for my installation disk and when I insert it, it STILL tells me "not all files could be found, installation not complete????"

I can't install a simple VPN client - why???  

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/blue/Desktop/vpnclient/linuxcniapi.o
/home/blue/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/blue/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/blue/Desktop/vpnclient/linuxcniapi.c:297: warning: implicit declaration of function ‘skb_set_timestamp’
/home/blue/Desktop/vpnclient/linuxcniapi.c:331: error: ‘struct sk_buff’ has no member named ‘nh’
/home/blue/Desktop/vpnclient/linuxcniapi.c:332: error: ‘struct sk_buff’ has no member named ‘mac’
/home/blue/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/blue/Desktop/vpnclient/linuxcniapi.c:454: error: ‘struct sk_buff’ has no member named ‘mac’
/home/blue/Desktop/vpnclient/linuxcniapi.c:455: error: ‘struct sk_buff’ has no member named ‘nh’
/home/blue/Desktop/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘h’
/home/blue/Desktop/vpnclient/linuxcniapi.c:458: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/blue/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/blue/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

Of course, there's some stock VPN client, but my university doesn't say what the gateway address is, you have to install the Cisco client to get it (as far as I can tell).

This is ridiculous, and no one responding is giving straight answers.

What I would LOVE to see:

A step-by-step guide to getting started in Linux.  How things are really running - if this "Restricted Drivers" **** is actually installing the latest drivers that I downloaded and are sitting on my desktop, or just whatever latest version might have been sitting in some default directory of Ubuntu.

How this Package manager is working.  If I download something and it's sitting on my desktop, does the Package manager recognize it, or again, does it just have some stock **** and shows me these things?

I also can't seem to connect to my wireless connection for some unknown reason - when I change my wireless connection settings (exactly the same as the settings I used in Windows), it doesn't work.  Luckily, it's easy for me to connect via wire, but I don't want to rely on this.


There.  Sorry for the tirade, but it's a weeks' worth of frustration and NOTHING working.

---

### Post by ukripper on 2008-03-10
This thread should be in testimonials. Problem is not with linux, it is with understanding how to use it.

Might help [https://help.ubuntu.com/7.10/](https://help.ubuntu.com/7.10/)

---

### Post by kesman on 2008-03-10
Also, removing CD from system -> administration -> software sources is a good idea if you have a working internet connection in the linux machine.

---

### Post by billgoldberg on 2008-03-10
Don't blame linux because you don't know how to use it.

Your using ubuntu as you would windows.

Take a look at this:

[https://wiki.ubuntu.com/Training](https://wiki.ubuntu.com/Training) for beginners.

---

### Post by Ardrias on 2008-03-10
"Your eyes are full of hate, forty-one. That's good. Hate keeps a man alive."

Well you can get a CISCO compatible vpn-client by installing the 'vpnc' package. Obviously you DO need the information to connect....

As for it asking for the CD, you can turn that off in /etc/apt/sources.list

What kind of wireless card do you have? Broadcom are a bit of a bitch.

Also, if it's YOU not understanding something, it really doesnt make Linux, or any other OS for that matter, worthless...

---

### Post by Barrucadu on 2008-03-10
You're obviously not willing to try and learn how to use Linux. In two days I had learned all of the basic terminal commands and had my system set up exactly as I wanted it. I've barely had to install anything since then.

---

### Post by ukripper on 2008-03-10
First go through above posts and understand how linux works and then you would be able  to configure your cisco VPN client using this HowTo - [http://ubuntuforums.org/showthread.php?t=298181](http://ubuntuforums.org/showthread.php?t=298181)

For easy installtion - [http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

---

### Post by NightwishFan on 2008-03-10
Please all, do not be mad at op. He just needs to understand. It all depends on what you need. If windows has all you need, then use it. I assume you aren't using Linux out of pure curiosity because you would not become frustrated so fast. When something is different it is by no means worse but possibly inefficient for you. If you take the steps to understand than you will enjoy the process a lot more. Please remember we are always here to help, respectfully.

---

### Post by etothepi on 2008-03-10
> **Barrucadu said:**
> You're obviously not willing to try and learn how to use Linux. In two days I had learned all of the basic terminal commands and had my system set up exactly as I wanted it. I've barely had to install anything since then.

Well aren't we smug.

I know all the terminal commands for these things.  Perhaps I'm just getting frustrated with the lack of control I'm feeling over certain things, coupled with a few "I don't know x specific thing" circumstances.  Probably I'd feel more comfortable in a pure command-line interface (although I'd be too scared to touch anything!).

I feel like all the documentation I've been finding hasn't helped, for anything I've tried to use.  They all refer vaguely to things I cannot find, and when I do find them, the documentation on them is also bad and again refers vaguely to things I cannot find.

The training page looks to be a great help - thanks!

Also, yeah, be defensive about Linux as though I am a personal threat.  Jump on me for calling its savior-like regard into question.  I'm not really serious about it sucking, again, just part of the venting.

As for the Cisco VPN, the error code I pasted is the output I get when I run the command as directed in the Cisco documentation.

I'm sure it will get better, and I'm *certainly* not giving up.  I really need the VPN for university stuff.  If I can get that working, I'll ignore the rest of the problems I'm having with Linux for a while and let it soak in more comfortably.

---

### Post by kwacka on 2008-03-10
Ensure you have an internet connection.

Click on System --> Administration --> Synaptic Package Manager.

Click on 'Settings' and click on all the boxes. Do the same with third party software. Remove the tick from the CD box. Click on close.

Now click on the blue 'reload' button.

Next, click on  'search'  and enter the name of the application you wish to install or a description e.g. 'vpn' ot 'cisco'. Choose the one you want and click apply.

Packages can be installed in several ways, two possible ways are using apt (either from the command line (sudo apt-get install xxxx) or via its graphic front end) as described above or by compiling from source code; there is geneally no need to do this, it is recommended that you use synaptic/apt.

See the wiki: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by aysiu on 2008-03-10
This rant belongs in Ubuntu Testimonials and Experiences (and that's where I've moved it). If you want to help out etothepi, then click on etothepi's username, go to the user profile, and find the support threads she or he has started.

---

