---
title: "*shudder* XP Home question"
date: 2005-11-16
forum: The Cafe
---

### Post by hizaguchi on 2005-11-16
I'm running Windows XP Home edition on my laptop.  In order to register myself with the wireless network on my college campus, the IT department requires me to run a program they provide which makes sure I have antivirus software and the latest security updates.  An unadvertised side effect of this program running was that it changed my computer's password length and complexity requirements, and now I have a 7-mile, 3-handed password.  I'm sure for the security concious, this isn't a problem, but for a computer that is always in my possession and is not used to store any sensitive information, this is severely annoying.

Since this isn't XP Pro, I can't use group policy settings or anything else that I've found in the Microsoft knowledge base to fix it.  I have been able to reduce the length requirement by going to the command line and typing "net accounts /minpwlen:0", but I"m still stuck with the complexity requirements.  Anybody know how to fix this?

---

### Post by Kyral on 2005-11-16
Smack your Campus IT department over the head with a 50lb Unix Manual.

It sounds like proprietary stuff of the worse kind. I wouldn't know anything about it unless you could give me the name of the program.

~ UbuntuForums, we rock so hard that we help fix XP!

---

### Post by hizaguchi on 2005-11-16
It's just a little .exe file that the IT department put together to enforce their security policy on students.  It used to just be antivirus software, but they've evidently changed it.  Now it enforces password complexity, disables the guest account, renames the admin account, and probably more that I've not come across yet.  Had to run it to register with the network. :???:

---

### Post by TravisNewman on 2005-11-16
sounds like the Cisco Clean Access Agent

If it IS, you don't have to use that as long as you just want to go on the web.

Another good thing, if it's the Clean Access Agent, and it's set up the way I've seen it before, you can use Linux as well, but it will time out after a while.

If it's not the clean access agent then I'm not sure what you can do.

---

### Post by hizaguchi on 2005-11-16
Not sure if that's it or not.  My limited understanding is that the IT department keeps track of the hardware ID (MAC address, is that correct terminology?) of everyone's wireless card, and before you can do anything on the network you have to register your university ID and password with the hardware ID.  Once that is done, you're good, but for a student to do that you have to run IT's program that changes all these windows settings on your computer before it will register your hardware with the network.  So I could reinstall windows and fix the problem, and my hardware would still be registered.  But the annoyance isn't really worth that much trouble.

---

### Post by Brunellus on 2005-11-16
[QUOTE=hizaguchi]Not sure if that's it or not.  My limited understanding is that the IT department keeps track of the hardware ID (MAC address, is that correct terminology?) of everyone's wireless card, and before you can do anything on the network you have to register your university ID and password with the hardware ID.  Once that is done, you're good, but for a student to do that you have to run IT's program that changes all these windows settings on your computer before it will register your hardware with the network.  So I could reinstall windows and fix the problem, and my hardware would still be registered.  But the annoyance isn't really worth that much trouble.[/QUOTE]
well, now that your MAC address is registered, wipe XP, run ubuntu, and be happy.  If they challenge you ever again, note politely that since you're running ubuntu, you are a net *positive* to the network community, since your computer won't pass on their lousy Microsoft crapware.  

If they don't believe that, I'm sure there are enough eyeballs in the ubuntu community to help you circumvent.

---

### Post by ferentix on 2005-11-16
Wait, this is your own laptop? Or a uni leased one? Because if it's the former, then they can't really complain if you change your OS in any case.

Just interested- what would they do if you brought your own laptop to uni and it had Ubuntu installed rather than WinXP... what would they do?

---

### Post by hizaguchi on 2005-11-16
It is my own laptop, and they don't have a problem with people using different OSes (my wife has a Mac, my desktop that used to be on the network was Linux), but if you do use Windows on their network, the registration system requires you to run their little security program before you can enter your information.  My wife once asked a guy from the IT department why that was, and he basically told her that if all the Macs in the world got viruses, nobody would care because they are so rare compared to Windows machines.  So yeah, we're not dealing with brilliance here.

Anyhow, I'm stuck with Windows because my department has free student liscenses of Maple and Matlab for Windows, and because my books often come with useful little programs (like Working Model), that require Windows (or occasionally OS X).  I just wish I could get rid of this minor annoyance, and on a larger scale, I'm ticked off that the most malicious program any computer I have ever owned has ever seen came from my school's IT department.  What gives them the right to screw with my personal system's settings, without so much as a confirmation box?

---

### Post by Brunellus on 2005-11-16
[QUOTE=hizaguchi]It is my own laptop, and they don't have a problem with people using different OSes (my wife has a Mac, my desktop that used to be on the network was Linux), but if you do use Windows on their network, the registration system requires you to run their little security program before you can enter your information.  My wife once asked a guy from the IT department why that was, and he basically told her that if all the Macs in the world got viruses, nobody would care because they are so rare compared to Windows machines.  So yeah, we're not dealing with brilliance here.

Anyhow, I'm stuck with Windows because my department has free student liscenses of Maple and Matlab for Windows, and because my books often come with useful little programs (like Working Model), that require Windows (or occasionally OS X).  I just wish I could get rid of this minor annoyance, and on a larger scale, I'm ticked off that the most malicious program any computer I have ever owned has ever seen came from my school's IT department.  What gives them the right to screw with my personal system's settings, without so much as a confirmation box?[/QUOTE]
what gives them the right?  the fact that most windows users either abdicate their rights or are too clueless to exercise them.

---

### Post by blastus on 2005-11-16
This is probably the stupidest thing I've ever heard of. They obviously do not believe in the security and integrity of their network. If a compromised machine actually did try to compromise their network (i.e. send out spam, transmit viruses, scan other machines on the network etc...), they should suspend the account and deal with it then.

If an ISP were run like this University, they would go out of business as not many people would be willing to run some dumb-ass Windows program that does who knows what to verify that their machine is "safe" for their network. This approach is really stupid because there is nothing in it that prevents or addresses the fact that a machine that connects to their network can be compromised at a later date. And you don't need to install a special program to obtain the MAC address of your network card either--the OS can provide it--I forget what the command is.

---

### Post by Qrk on 2005-11-17
You can emulate a new MAC address. Then you might be able to go through the setup again and choose a new password for connecting in ubuntu only. Its easy enough to change a MAC address in Linux.

Just run 

```
ifconfig
```

and look for your hwaddr. Write it down, then you can change it...

```
sudo ifconfig #name of your connection# hw ether #MAC address#
```

I think you need to shut down your connection before doing this,

```
dhclient down
```

I've also never tried it with wireless connections (I have a desktop), but I think it should work.

---

### Post by hizaguchi on 2005-11-17
Well, I found some directions for screwing with the registry and forcing it to autologin the admin account.  So it's acceptable now.  I still wonder where they hid the complexity requirement though.  I'd kinda like to have it ask me for a password when I log in, but without it having to be ultra-complex.  I read through the whole registry last night and couldn't find anything.  This is crazy.

---

