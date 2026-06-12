---
title: "Is there a good apparmor profile for virtualbox?"
date: 2012-08-26
forum: Security
---

### Post by WhiteHatGuy on 2012-08-26
Any? That works in normal account and in guesst account for Ubuntu 12.04

Where can I get it? Or maybe the code?

Or any way to protect my virtualbox from the bad guys (Black Hat Crackers), hacking through malware, trojan, etc, forcing to drop my internet connection inside my virutalbox OS XP installed. (Infected with virus)

Outside its ok, no problems, in host, cause I use Ubuntu 12.04, and malware cant harm to it. Cause is a windows virus.

Thanks

---

### Post by cariboo on 2012-08-26
> **WhiteHatGuy said:**
> Any? That works in normal account and in guesst account for Ubuntu 12.04

Where can I get it? Or maybe the code?

Or any way to protect my virtualbox from the bad guys (Black Hat Crackers), hacking through malware, trojan, etc, forcing to drop my internet connection inside my virutalbox OS XP installed. (Infected with virus)

Outside its ok, no problems, in host, cause I use Ubuntu 12.04, and malware cant harm to it. Cause is a windows virus.

Thanks

There is no magic bullet, Windows works the same way in virtualbox, as it does on bare metal. Install the same tools you would on a normal Windows install.

---

### Post by WhiteHatGuy on 2012-08-26
> **cariboo907 said:**
> There is no magic bullet, Windows works the same way in virtualbox, as it does on bare metal. Install the same tools you would on a normal Windows install.

Sorry for my english spelling mistakes, english is not my native language

Well, usually I use on XP, comodo firewall, with highest tight security settings in firewall and in HIPS +defense and sandbox untrusted level, with vulnerability fixed commands included, sandboxie (drop administrators rights). VPNs: trustconnect, proxpn, anchorfree. 

Antiviruses, well basically all, Emsisoft,comodo,essentials,panda cloud,avg,avast,clamtk, etc etc etc.

Browsers, Commodo Dragon, FireFox, Google Chrome, Chromium.

Close all ports IN and OUT, and using only this ports: (In Comodo Firewall and gufw)

TCP OUT:  53,80,443
UDP OUT: 53

Also I tried running the hole thing from very secure Ubuntu guestt accont, and the blackhat hacker bad guy, fails on disconnecting XP internet connection on the first tries, but at the end, he made it, his attack goes through, and XP gets compromised.  LOL and is kinda funny cause you can actually see how the bad guy is trying to disconnect your xp connection but fails the first tries hahahahaha.



Disable almost all windows services, left only:

1) DCOM Server Process
2) Plug and Play
3) Network connections 
4) DHCP client
5) Remote procedure call (RPC)

Netbios attacks config, blocked, internet connections.

Running from restricted prvileges users account.

To name a few....

And so on, you name it, etc,etc,etc.

And yes somehow the blackhat cracker bad guy thief burgler crook always get away with it. LOL hahahahaha

No matter what security messuares I take on XP, at the end system gets compromised. XP is an easy target for blackhat crackers with tons of skill.

Unfurtantly, I need to run my business from XP or windows, cause the application I use is only for windows not linux (wine dont do the trick in my case) and yes of course there is tons of money involve. So scenario of black Hat crackers bad guys with tons of skill in security attacks and intrusions is going to be expected.


Now on Ubuntu or Lubuntu the story is different, if my business aplication will run in linux and be compatible, I am %100 shure linux would do the trick. But like I said before, the application I use, its only supported by windows not linux. By default linux its a more secure OS, and you can make it very secure if you hardened and tight up security settings. Right now I thinking on running the hole thing from a ubuntu custom live dvd, cause probably the virus is not going to be able to write on hard drive, and virus probably not capable of droping my internet in my XP.

Wish me luck. I am gonna need it. Cause windows security s u c k s. LOL hahahahah. Period, end of story.

My advice and from my experience:

If you are going to run a business from internet with tons of money involved, for christ sake dont use windows hahahahahaa lol.


Windows its ok for games LOL :lolflag:

---

### Post by Hungry Man on 2012-08-26
I used to use this one. It may require a bit of tweaking for your setup and I made it a long time ago so I can't vouch for how tight I made it. I think I gave it a lot more read access than I should have. Not awful though.

As you'll see I had a "VirtualBox VMs" folder in my /Documents/ so you can remove that line and replace it with whatever folder you like to keep them in.

> # Last Modified: Sat Mar 31 15:33:21 2012
#include <tunables/global>

/usr/share/virtualbox/VBox.sh {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>
  #include <abstractions/nvidia>

  capability net_raw,
  capability sys_ptrace,

  network inet raw,
  network inet stream,
  network inet6 stream,

  /bin/bash rix,
  /bin/dash rix,
  /bin/which rix,
  /dev/ati/* rw,
  /dev/vboxdrv rw,
  /etc/xdg/Trolltech.conf rk,
  /home/*/.ICEauthority r,
  /home/*/.VirtualBox/ r,
  /home/*/.VirtualBox/* rw,
  /home/*/.Xauthority r,
  /home/*/.cache/dconf/user rw,
  /home/*/.config/Trolltech.conf rk,
  /home/*/.config/dconf/user r,
  /home/*/.icons/ r,
  /home/*/.local/share/* r,
  "/home/*/Documents/OS Images/*" r,
  "/home/*/VirtualBox VMs/**" rw,
  /lib/** r,
  /lib32/** r,
  /lib64/** r,
  /proc/ r,
  /proc/*/cmdline r,
  /proc/*/io r,
  /proc/*/oom_score_adj rw,
  /proc/*/stat r,
  /proc/*/statm r,
  /proc/*/status r,
  /proc/*/task/** r,
  /proc/ati/* r,
  /proc/meminfo r,
  /proc/modules r,
  /proc/sys/kernel/** r,
  /proc/tty/drivers r,
  /proc/uptime r,
  /proc/version r,
  /run/resolvconf/* r,
  /sys/block/ r,
  /sys/class/*/ r,
  /sys/devices/** r,
  /tmp/** wk,
  /usr/lib/virtualbox/VBoxSVC rix,
  /usr/lib/virtualbox/VBoxTestOGL rix,
  /usr/lib/virtualbox/VBoxXPCOMIPCD rix,
  /usr/lib/virtualbox/VirtualBox rix,
  /usr/lib{,32,64}/** mr,
  /usr/share/glib-2.0/** r,
  /usr/share/icons/ r,
  /usr/share/icons/** rk,
  /usr/share/mime/* r,
  /usr/share/pixmaps/ r,
  /usr/share/themes/** r,
  /usr/share/virtualbox/** r,
  owner /{run,dev}/shm/* rk,
  /{run,dev}/shm/* w,

}

---

### Post by WhiteHatGuy on 2012-08-29
> **Hungry Man said:**
> I used to use this one. It may require a bit of tweaking for your setup and I made it a long time ago so I can't vouch for how tight I made it. I think I gave it a lot more read access than I should have. Not awful though.

As you'll see I had a "VirtualBox VMs" folder in my /Documents/ so you can remove that line and replace it with whatever folder you like to keep them in.




Thing is I put my "VirtualBox VMs" folder in my /Documents/.

I put this command in terminal:

cat /etc/apparmor.d/virtualbox | sudo apparmor_parser -a



It shows the profile is in enforce mode and its loaded to the kernel. So far so good.

But when I try to start my virtual machine with XP inside.

VirtualBox gives me an error permision denied, same thing If I try to create a new virtual machine, I know that the profile is blocking and causing the error. Cause If I disable the profile it works again fine.

But I dont get it. 

The profile should be allow me, to be able to start at least the virtual machine.

I mean I cant start the hole thing, and I cant login to XP. VM appears on the list but I cant start it, it sais inaccessible. 

This is insane locked up aplication profile dude. I like it. LOL!!!:lolflag:


Maybe I am so freaking noob on apparmor that I cant see the obvious answer in order to get this working lol hahahaha :lolflag:


Thanks for giving me a hand on this. ):P

---

### Post by Hungry Man on 2012-08-29
Change this line

"/home/*/Documents/OS Images/*" r,


To

"/home/*/Documents/**" r,

---

### Post by WhiteHatGuy on 2012-08-29
> **Hungry Man said:**
> Change this line

"/home/*/Documents/OS Images/*" r,


To

"/home/*/Documents/**" r,







Now its ok, but is going to boot xp and and then suddenly:

VirtualBox - Error

Failed to open a session for the virtual machine XP.

Failed to open release log (could not open file '/home/alex/Documents/VirtualBox VMs/XP/Logs/VBox.log' (fOpen=0x322), VERR_ACCESS_DENIED).

Details


Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

---

### Post by WhiteHatGuy on 2012-08-29
> **Hungry Man said:**
> Change this line

"/home/*/Documents/OS Images/*" r,


To

"/home/*/Documents/**" r,




OMG LOL I think I fix it after messing around with the profile for 2 hours, I am just start learning apparmor. So for me this is huge hahahaha.



I change 

"/home/*/Documents/**" r,

for 

"/home/*/Documents/ r, 

and now is working


Thanks guys for the help. Now its time to test my new toy  :guitar:

---

### Post by WhiteHatGuy on 2012-08-29
[QUOTE=WhiteHatGuy;12204280]OMG LOL I think I fix it after messing around with the profile for 2 hours, I am just start learning apparmor. So for me this is huge hahahaha.



I change 

"/home/*/Documents/**" r,

for 

"/home/*/Documents/ r, 

and now is working



Thanks guys for the help. Now its time to test my new toy  :guitar:[/QUOTE








Nope, I was wrong, is not working, I thought I fixed but I didnt.
:mad:


Now I am trying to disable virtualbox log, so I can avoid the error, but this stuff is hard for noobs like me ;)


Thanks guys for the help. Now its time to test my new toy  :guitar:[/QUOTE

If some one knows how to disable log on virtualbox or fix the apparmor profile, dont be afraid to explain thing for noobs lol :lolflag:

---

### Post by WhiteHatGuy on 2012-08-29
Wow after around 4 or 5 hours and I finally did it.

But now I get a new error, all the errors I am getting is because the profile dont allow to write, just allow to read. Thats awesome in terms of security, but for this errors cases, I think I dont have other option to allow them to write, otherwise I cant start the hole thing.

The next error is related to my cd rom.

Does someone knows which line in the profile belongs to the cd rom , so I can add a W at the end and allow write mode, so I dont get error?

I am trying to figure it out this one. Damn apparmor is defenetly not for noobs it takes time to learn it. But I suppose is the same hard to hacked lol :D

---

### Post by Hungry Man on 2012-08-29
You can put the profile into complain mode and then run the program. Afterwards you can run 'aa-logprof' to audit it automatically. I suggest you try that.

---

### Post by WhiteHatGuy on 2012-08-30
> **Hungry Man said:**
> You can put the profile into complain mode and then run the program. Afterwards you can run 'aa-logprof' to audit it automatically. I suggest you try that.






I found a temporary fix, I disconnect my cd rom. :lolflag:

And now is working, no more errors, now it boots XP without problems.

I am going to try what you said Hungry Man, for some reason when I use commands with aa- used by apparmor, in terminal gives me errors that the command do no exists. 

Now its time to go full sandbox vpn host, and full sandbox guest, multiple layers of sandbox :D, and see how it goes. I hope this black hat hackers crackers get a freaking nightmare if they try to disconnect my internet connection.

Thanks for helping me.

Everybody wish me Luck.

---

### Post by Hungry Man on 2012-08-30
Install apparmor-utils if it says the commands can't be foudn.

---

### Post by WhiteHatGuy on 2012-08-30
> **Hungry Man said:**
> Install apparmor-utils if it says the commands can't be foudn.

I already install apparmor utils, cause some one advice the same thing for my case of aa- commands, but unfourntanly for me it didnt fix the problem. I dont know if is caused because I am using lubuntu and apparmor utils is not compatible, or maybe I didnt install it properly. I would have to check on that one, more carefully.


The good news is that virtualbox sandboxed apparmor profile, have a very good effect on making life miserable to this blackhat crackers, I just tested against them, hahahah lol, what a surprise, they got really really upset. One of them put in chat OMFG lol :lolflag:. And it was so obvious. They tried again to do the disconnection internet trick, and it kinda work but not like before, it disconnect me, but I just had to refresh my window (wich is very simple) of my buisness and connection was back hahahaha. And also after several seconds if I dont do anything connection goes back to normal. They end it up leaving. ;)

Awesome!!!

---

### Post by WhiteHatGuy on 2012-09-01
> **Hungry Man said:**
> Install apparmor-utils if it says the commands can't be foudn.


I was  able to install apparmor-utils. I think the last time I didnt intall it correctly. But it works now.


Ubuntu + apparmor makes a very good shield of protection from what I tested so far. It would be nice a friendly user interface for apparmor, like sandboxie, for noobs and begginers. But for intermidiate and advanced users its a perfect tool.

I recommended to everyone out there that is looking to tigh up security

:p

---

