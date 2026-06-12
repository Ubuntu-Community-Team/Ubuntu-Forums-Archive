---
title: "Ubuntu 18.04"
date: 2018-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by gordie692 on 2018-05-17
Hey guys running the new 18.04 on my new Dell Inspiron 15 AMD had W10 but didn't like it so I put this on great so far how's that malware threat or was it nothing but one question I don't need an antivirus the reason why I ask you read so online just asking

---

### Post by kerry_s on 2018-05-17
it's just less likely, but there are threats out there, your just much more safer on linux.

i haven't, nor do i fell the need to use any malware/antivirus/firewall/etc... in the system.

i do use adblock in the browsers that do say they stop those things.

---

### Post by poorguy on 2018-05-18
As long as the*** UFW*** is ***enabled*** you should be good to go.

I use ***Firejail*** which is available in the*** link below*** for an extra layer of protection.

[https://sourceforge.net/projects/firejail/](https://sourceforge.net/projects/firejail/)


I also use ***Ublock Origin*** keep the ads down it available in your ***browser extensions***.



This is written for ***Linux Mint*** although still applies to ***Ubuntu***.

[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

---

### Post by gordie692 on 2018-05-18
Thanks guys

---

### Post by gordie692 on 2018-05-19
Thanks guys far as firewall goes isn't that built in the system or do I download it from software center I do my updates every morning

---

### Post by exploder on 2018-05-19
Yes, the firewall is present but you might want to get GUFU from the software center. GUFU is a GUI front end for it.

---

### Post by oldrocker99 on 2018-05-19
To enable UFW (Uncomplicated Firewall), type this in a terminal:
```
sudo ufw enable
```

The program is already installed; you just have to start it, and it will start running immediately, and on every reboot.

Windows, which is closed-source, is a malware magnet, while Linux programmers are constantly searching for security holes, and all the coders make up for a lot more eyes that check the code than the smaller by far number of Windows coders' eyes. In a decade, I have had zero instances of malware.

---

### Post by hrsetrdr on 2018-05-19
> **oldrocker99 said:**
> to enable ufw (uncomplicated firewall), type this in a terminal:
```
sudo ufw enable
```

the program is already installed; you just have to start it, and it will start running immediately, and on every reboot.

Windows, which is closed-source, is a malware magnet, while linux programmers are constantly searching for security holes, and all the coders make up for a lot more eyes that check the code than the smaller by far number of windows coders' eyes. In a decade, i have had zero instances of malware.

+1.  Qft.

---

### Post by poet1 on 2018-05-20
> **poorguy said:**
> I also use ***Ublock Origin*** keep the ads down it available in your ***browser extensions***.

You know the drill: seemingly innocent website turns into a whack-a-mole marathon. The window does not close.

I think Ublock origin may help with this.

---

### Post by grahammechanical on 2018-05-21
Hi

> how's that malware threat or was it nothing

Were you referring to this?

[https://blog.ubuntu.com/2018/05/15/trust-and-security-in-the-snap-store](https://blog.ubuntu.com/2018/05/15/trust-and-security-in-the-snap-store)

Ubuntu has an app store that provides applications in two types of packages. There are the traditional Debian or deb packaged applications and there are also some applications that are packaged in the Ubuntu snap package format.

Snap applications are very limited as to what parts of the system they can access. For example, I have Deepin Music snap installed. It will not access even music files on another partition. Music files have to be on in the Music folder in the system that Deepin Music is installed in. I doubt if Deepin Music can access any system files. 

The blog post that I link to discusses an application that got into the Ubuntu store as a snap package app and that used system resources the mine cryptocurrency. It did this without the computer user's knowledge or permission. 

Was it malware? Debate. Argue. Throw chocolate currency at each other. The blog post provides information about the intentions of Ubuntu developers as regards snap app security.

Regards

---

