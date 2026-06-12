---
title: "LTSP - Where's the client filesystem?"
date: 2008-09-16
forum: Server Platforms
---

### Post by computer_freak_8 on 2008-09-16
I am trying to setup a Linux terminal server (LTSP) on Ubuntu. I do not want to use Edubuntu, especially not the pre-configured version. I want to get experience doing this myself, but I'm needing some help.

I installed the LTSP packages via apt-get, and am now trying to figure out where on my hard drive the client filesystem is. I was originally looking to install LTSP from source so I could customize it, but I did not see the option to do so for LTSP 5.

Can anyone point me in the right direction? I don't need help installing the base package; just configuring it now that it's installed.

Thanks,

computer _freak_8

---

### Post by UbuWu on 2008-09-16
Did you build the client already?

See also:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

If I remember correctly, the client gets installed in /opt/ltsp.

---

### Post by computer_freak_8 on 2008-09-16
> **UbuWu said:**
> Did you build the client already?

See also:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

If I remember correctly, the client gets installed in /opt/ltsp.

Crap, you beat me to it!

I was just finishing two other posts, this was going to be my third.

Yes, I ...err... did not run the command "sudo ltsp-build-client --arch i386" at the time of the start of this thread.
I now see my "client root" at "/opt/ltsp/i386". 

Now, is there any way to "install" a different distribution in this area?
Say, I want to run Ubuntu, but have the client computers using Kubuntu... is this possible? One way I can think of right now is to install the wanted distribution on another partition on my hard drive, and then copy over the filesystem from there. Three more things:

1. What is all this a hear about NFS? (NFS = Network File System???)
Is this what /opt/ltsp/i386/ is? 

2. How do I setup swap space for the clients?

3. How do I connect clients via Wi-Fi? Is this possible via PXE?


Thanks much,

computer_freak_8

---

### Post by cariboo on 2008-09-17
Have a look at the documentation for LTSP here:

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation)

For a nfs howto look here:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

You won't be able to connect using wifi as you have to have an operating systems with drivers for the wifi card to be able to use wifi. Defeating the purpose of LTSP.

Jim

---

### Post by UbuWu on 2008-09-17
To install kubuntu, chroot into your ltsp:

sudo chroot /opt/ltsp/i386

and then run apt-get install kubuntu-desktop

---

### Post by computer_freak_8 on 2008-09-17
@cariboo907
Thanks for the links.

Also, I know there's some way to do thin-client Wi-Fi, just maybe not with LTSP. 
Here's the link for what I'm referring to:

[http://www.thinclient.org/archives/2007/08/wifi_reaches_th.html]("http://www.thinclient.org/archives/2007/08/wifi_reaches_th.html")


@UbuWu

Thanks, I'll try that. 

Also, say later on down the road sometime I want to install an operating system that has to be installed via CD/DVD. (I'm thinking maybe some time in a year or two using Slackware.) Is there an easy way to do this? I mean manually, as in not just using a command like "apt-get slackware", but actually going through the whole install process.


One more thing I can think of right now: Do I need to setup swap space, or does it share the server's swap space? (Or should I just make sure I have lots of RAM?)

Thanks again for all your help; I really like Linux, and it's good to know there are excellent support communities for it.

computer_freak_8

---

