---
title: "KVM+Qemu Networking Questions"
date: 2008-10-31
forum: Virtualisation
---

### Post by Weissbier on 2008-10-31
Hi there, i hope someone can answer me this.
I have read the whole day about KVM+Qemu and its Networking issues, but somehow i can't get through it - means i need your help.

I am using Ubuntu 8.04.1 LTS with Gnome and this "Host-System" is included in a larger network of Windows PC with many file-sharings.

I have successfully installed KVM&QEMU as well as created a virtual Win-XP image(Guest System) to launch from inside Ubuntu.
[I]
The Internet access was working out of the box, and the Processor Speed (based on benchmarks with Super-PI + SiSoft Sandra) are equal to a native installation on the same system.[/I] 

So far so good, and really thanks to all the people which have written those great tutorials out there :guitar:

Problem: I would like to be able to use the Virtual WIN-XP "Guest-System" for the following two things:

1. Running a Software on it which is using 4UDP Ports in a row for sending+receiving data,
2. Be able to connect to all the Windows File Sharing's in our larger Local-Area-Network.
3. Be able to get reached by Pings over the Network.

I have tried it with the "redirect" command when starting the Virtual XP System, but it hasn't worked and furthermore its odd to have like 10 redirects in the line.

Can someone help me?

Thanks very much 
- Weissbier-

---

