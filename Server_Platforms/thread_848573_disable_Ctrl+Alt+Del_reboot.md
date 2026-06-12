---
title: "disable Ctrl+Alt+Del reboot"
date: 2008-07-03
forum: Server Platforms
---

### Post by LRT on 2008-07-03
how can i disable Ctrl+Alt+Del reboot. when i press these keys, my ubuntu server automatically reboots without any prompt. i don't even have to be logged in (which is kind of scary). is there a way to disable this???

---

### Post by unixbills on 2008-07-03
You can pound out the exec of shutdown in /etc/event.d/control-alt-delete or change it to run something else or whatever.

I just put in an exit 0 so it runs clean like rc.local

---

### Post by ixus_123 on 2008-07-03
Just out of curiosity, why would you want to disable this?

I find the key stroke be be a life saver when the computer locks up, yet the keys are far enough apart that you can't really push them by accident.

---

### Post by LRT on 2008-07-04
> **ixus_123 said:**
> Just out of curiosity, why would you want to disable this?

I find the key stroke be be a life saver when the computer locks up, yet the keys are far enough apart that you can't really push them by accident.

anyone who gets access to my server can easily do a Ctrl+Alt+Del and reboot. i don't like this because there are no credentials needed to do this. you just simply hit the keys and the computer reboots, no questions asked. Ctrl+Alt+Del are famous hot keys that can be guessed by anyone. thats why i want to disable this or be able to choose different keys.

> You can pound out the exec of shutdown in /etc/event.d/control-alt-delete or change it to run something else or whatever.

I just put in an exit 0 so it runs clean like rc.local

i will try this, thanks!

---

### Post by spike_strip on 2008-07-04
This Ctrl+Alt+Del adds no security risk!

 If someone is sitting at your PC and wishes to do harm, the least of your worries are  Ctrl+Alt+Del!

---

### Post by LRT on 2008-07-04
> **spike_strip said:**
> This Ctrl+Alt+Del adds no security risk!

 If someone is sitting at your PC and wishes to do harm, the least of your worries are  Ctrl+Alt+Del!

what i'm saying is if someone who knows NOTHING about hacking or linux manages to get into my server room and looks at the monitor and sees my login prompt he really won't be able to do anything EXCEPT hit Ctrl+Alt+Del and reboot the server because Ctrl+Alt+Del does not require a login. therefore i do consider Ctrl+Alt+Del to be a security risk because rebooting a server is a BIG deal.

---

### Post by spike_strip on 2008-07-04
I know my server has a power button that if held down will shutdown my running system. And then it is easy to push it again and restart the server. 

I agree with you, that being able to shut down a server is a risk—however, when someone has access to your server room; all bets are off!  

Ctrl+Alt+Del it's self is not an issue; the issue is physical access to your server!

---

### Post by spike_strip on 2008-07-04
I am not attempting to change your mind... only offering a different point of view!

---

### Post by Dr Small on 2008-07-04
Why do you have a monitor and keyboard hooked up to the server anyhow? But if someone has bypassed all of your other security and is able to get into your server room, then there is really no point in disabling the keypress.

---

### Post by sjwk on 2008-07-04
I agree with all the replies about physical security meaning all bets are off, but I guess the intention isn't to prevent deliberate damage, but someone with enough knowledge to be dangerous wandering in, seeing it isn't showing a pretty windows desktop and helpfully trying to reset it with C-A-D since that's what he's used to doing to fix broken machines...

At least with linux, C-A-D does do a proper clean shutdown and restart, compared to pressing the reset button on the case because C-A-D didn't fix the 'problem' :)

The first reply is the best answer.  I have a sneaky feeling that having X running also blocks it, unless the window manager catches it and triggers a reboot...  But I've not tried it for a long time, and I'm not about to test that now... :)

Steve.

---

### Post by LRT on 2008-07-04
if someone does gain access to my server room, yes, they will have gained great advantage, but i don't like to think that all bets are off. security must be layered. i agree having a physically secure server room should be one of those layers. but i think additional security can be in place through a number of ways, one of which is either disabling Ctrl+Alt+Del hotkey or assigning other keys instead of the traditional Ctrl+Alt+Del that everybody knows.

another layer of security is to have servers locked in individual closets that require keys to be opened. this would prevent someone from simply being able to hit the power or reset button or even unplugging the power cord.

> Why do you have a monitor and keyboard hooked up to the server anyhow? 

sometimes direct terminal access is required to troubleshoot particular problems where an ssh connection is not the best choice. direct terminal access also allows for a non-networked connection that is in my opinion much more secure than a networked connection no matter how secure.

i think relying on only one layer of security (and ignoring a potential security risk like Ctrl+Alt+Del) is putting all your eggs in one basket.

other comments are welcome, but i really don't want to beat this to death.

---

### Post by ixus_123 on 2008-07-04
Oh I wasn't trying to start ant trouble :)


I know I have accidentally rebooted a linux server for a client that had a dual OS setup.

One server running windows 2003 and the other RHES4.  The windows server was crashing lots (due to 2 anti virus being installed and fighting) and needed constant attention.

Out of habit, I went to the cabinet, plugged tme monitor in the windows server and the keyboard into the linux box.

ctrl alt del to get a password prompt and I suddenly realised my mistake :/

I can see the value in maping it to another set of keys if that is possible but like others have said, it's a good way to bounce a server gently rather than power-cycling.

Failing that, the sysreq key and REISUB works on some linux distros.

I guess what it really comes down to is the techs that will be looking after your server.

---

### Post by LRT on 2008-07-07
> **unixbills said:**
> You can pound out the exec of shutdown in /etc/event.d/control-alt-delete or change it to run something else or whatever.

I just put in an exit 0 so it runs clean like rc.local

is there a way to change the keys?

---

### Post by unixbills on 2008-07-07
I guess this is a matter of opinion.  I disable this on production servers.  I also unplug/disable the system reset button if it has one.  My thought is that people will think before pulling the power cord but often try ALT-CTL-Delete.  I also would find it hard to explain to managegent that we had an instant crash button and someone pushed it trying to "reset" the system.  "reset" even sounds kind of friendly.

Just my $.02

Bill

---

### Post by mrat on 2008-08-02
As I can be a bit of a plonker, I would like to disable this because I kept rebooting my VM server a number of times yesterday... DOH.

Was working with a few keyboards to close to one another LOL.

I know a few people at work will end up doing the same.

---

