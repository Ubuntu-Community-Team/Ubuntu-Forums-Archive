---
title: "I think I was hacked"
date: 2008-10-10
forum: Security
---

### Post by tuddy24 on 2008-10-10
Hi all,

The title says it all. I think there might be a hole somewhere in Pidgin or somewhere. Let me explain the chain of events.

I wake up to find my screensaver frozen. Nothing let's me get out of it, three finger salute, CTL-ALT-BACKSPACE, nothing. 

I physically reset the pc, jump in the shower, and come back to find that the pc is at some command prompt for some sound config. I wish I would've jotted it down but didn't.

Three finger salute works here and I watch the boot process to see what's going on. I boot ok into gnome and everythings ok. I open Pidgin which I always leave running and see someone on my buddy list that I did not invite. I delete him immediately and quit Pidgin. I've had people trying to buddy me before but I was able to deny them. Is it possible that somehow this person took over my system in some way? I never log in as root or anything, I sudo whenever I install something and that's it.

Concerned,

Pete

---

### Post by hyper_ch on 2008-10-10
I don't think you were hacked - it rather sounds a problem with pidgin

---

### Post by Dr Small on 2008-10-10
I agree with hyper_ch.

---

### Post by Therion on 2008-10-10
YES!  You are undoubtedly the victim of a malicious UB3R L337 |-|4><0R3R.  Possibly even one of several known, dreaded, *Ninja* |-|4><0R3R$,  known to specialize in system-wide penetration via Pidgin!!!  

Lets review the evidence!!  

What else could it possibly be *except* **Malicious Ninja Pidgin Hackers**???!!!!  

Congrats...  You're doomed.






Warning: Above post contains humor.

---

### Post by tuddy24 on 2008-10-10
I must say that I am a bit insulted by the responses here. I came home to find my computer locked up again with no idea why. In my line of work I try to gather as much information as possible prior to presenting an issue before I say anything to back up what it is that I'm trying to say. This is exactly what I did here. I had an issue and a sign of something that didn't look right and noted it because I think it might be related. Now I can see where the elitism I hear so often from others about certain Linux distros but am surprised to see it coming from the, advertised at least, community driven Ubuntu. If anyone can help me figure out why my PC is now rendered useless under Ubuntu, not MS Windows as this is how I'm able to even write this message, I'd appreciate your help very much. If you feel like being a smart-*** don't bother to reply. Thanks.

---

### Post by patrickballeux on 2008-10-10
Hi tuddy24,

You lock-up could be caused by several things (last update could have changed something in your graphic card driver...).

I would suspect your 3d card and your screensaver to be the cause.  But to be on the safe side, stop your pidgin, and let the computer opened for a whole day.  

If it locks again, the you know it is not pidgin. 

Also, have a look at your log files in /var/log/".  I was hacked one day on my ftp server (I had forgot to change the password to something more complex than "admin/admin"...)  These logs can be useful to detect unwanted login (of sudo retry...)

Do you have an ATI card?  I have a glitch with OpenGL screesavers with my ATI x1200, so I simply select the "blank" screensaver to avoid any problem.

Let me know!

---

### Post by Drezard on 2008-10-10
Sounds like you should wipe the computer! Put it back in the box! and send it back to the manufacturer!

---

### Post by tuddy24 on 2008-10-12
Hi patrickballeux,

The problem seemed to be my graphics card. While doing stuff inside windows the PC locked up in a similar way that happened in Ubuntu. I pulled the card out and cleaned a ton of dust off of it and put it back in. Who knows maybe there was a bad connection or something. I do know that my idle GPU temp dropped form 50 to 42C just from cleaning it. The only problem was all the lockups tore up my Ubuntu install and I had to reinstall it. I kept getting an error when booting that said my ext3 partition had errors that were not fixable. Once I got it reinstalled however it's worked without a hitch. I have heard that it's a good idea to seperate the ext3 partitions for this reason but am not sure which folders should have their own partition. I split my ext3 up into / and /home this time. Thanks for your help I appreciate it.

Pete

---

### Post by patrickballeux on 2008-10-14
Yep, overheating can cause this kind of trouble.  And the fact that you saw a temperature drop indicated that while doing some screensaver opengl activity, you was probably burning hot.

And when it's hot, it freezes... it's a known fact in computer land :)

Make sure also that there is a good ventilation in your PC (Have a look at your power supply also...)

Have a nice day!

---

### Post by airtonix on 2008-10-15
you would be surprised at how well a millimetre of dust can prevent heat from disipating from your chips.

---

### Post by daleus on 2008-10-17
> **Drezard said:**
> Sounds like you should wipe the computer! Put it back in the box! and send it back to the manufacturer!

Ding Ding, here comes the ban-mobile.

---

### Post by pmlxuser on 2008-10-17
> **drezard said:**
> sounds like you should wipe the computer! Put it back in the box! And send it back to the manufacturer!

bad advise!!!!

---

### Post by emecas on 2008-10-17
HI all...

i don't know in what way ***"see someone on my buddy list that I did not invite"*** can be related with the graphic card or the chip set

I have experimented a similar situation some time ago in my accounts that i have used with pidgin ... I received messages from a unauthorized contact and I saw a contact that I did not accept in my contacts list.

if someone have a idea, i would like retake this part of tuddy24's post


thanks

---

### Post by Dr Small on 2008-10-17
> **emecas said:**
> HI all...

i don't know in what way ***"see someone on my buddy list that I did not invite"*** can be related with the graphic card or the chip set

I have experimented a similar situation some time ago in my accounts that i have used with pidgin ... I received messages from a unauthorized contact and I saw a contact that I did not accept in my contacts list.

if someone have a idea, i would like retake this part of tuddy24's post


thanks
That sounds like Instant Message Spam:
[http://ubuntuforums.org/showthread.php?t=943616](http://ubuntuforums.org/showthread.php?t=943616)

---

### Post by Kevbert on 2008-10-17
Regarding dust - as well as overheating components, it can cause fan wear and can even be conductive. It's worth carefully giving the computer an internal clean once in a while with a vacuum cleaner.

---

