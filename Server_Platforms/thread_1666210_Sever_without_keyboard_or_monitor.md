---
title: "Sever without keyboard or monitor?"
date: 2011-01-13
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-13
Hello everyone,
I've recently decided to make a foray into the world of servers without any knowledge or experience. Yesterday, I ordered a Dell t110. I understand this is a really low-end server but I think it will work for home use.

Anyway... I am on a budget and literally just ordered the box. No keyboard. No mouse. No monitor. Not even an additional hard drive! With the exception of SLIGHTLY upgrading the processor, the thing is basically stock.

My question is this:
Can I control and operate this server with my laptop somehow? Will that allow me to install Ubuntu Server as well as perform systems administration tasks?

Ultimately, I'd like to get a new flat screen for the living room and have that be the monitor, with a wireless keyboard and mouse. However, like I said... I'm on a budget. I don't think I can sell my wife on that one right away. So... in the meantime, I need a way to actually USE my server.

Am I doomed to buying an old monitor and keyboard off of Craigslist?

---

### Post by chrislynch8 on 2011-01-13
Hi,

Obviously you will need a monitor and keyboard to configure the basic install and get things running. Once this is done you can configure ssh and manage everything from your lattop the with a SSH Client like putty.

Rgds
Chris

---

### Post by arrrghhh on 2011-01-13
Indeed.  Inital setup you'll need a keyboard and monitor.  Just get something temporary until you can get the rig up - then once it's up, no need for the kbd/monitor.  My server has been happily chugging along for 2 years now without a keyboard or monitor :D

---

### Post by Ranger_Joe on 2011-01-13
Sweet! That's awesome! Luckily, I work somewhere that has several unused computers and no one is there at night. I'll just install Ubuntu Server there, using one of their monitors and keyboards. Then I'll bring it home and use SSH. 

One more question...

If I can run everything from my laptop... would it be possible to run things remotely? Say, when I'm not at home?

---

### Post by chrislynch8 on 2011-01-13
Depends on how you configure it. If it will sit behind a standard router/firewall you can configure port forwarding to ssh into from outside the home office over the Internet.

In my office my server is my router so it is connected directly to the Internet so I can ssh in using the IP address.

Rgds
Chris

---

### Post by Ranger_Joe on 2011-01-13
Ok, cool. That makes sense. Thanks!

---

### Post by Sulcalibur on 2011-04-11
I tried this with a new setup the other day (I'm new to this) and was happily controlling the server from my MacBook but if I need to restart it I can't start it up with the username and password unless a monitor and keyboard is attached. Is it possible to restart or boot up the server and log in from a laptop screen?

Thank you

---

### Post by rbishop on 2011-04-11
@Sulcalibur it sounds like you have installed the Desktop version and are trying to get graphical I/O.

All editions (once SSH is setup) allow you to remotely control them even if no user is graphically signed in.

---

### Post by Sulcalibur on 2011-04-11
> **rbishop said:**
> @Sulcalibur it sounds like you have installed the Desktop version and are trying to get graphical I/O.

All editions (once SSH is setup) allow you to remotely control them even if no user is graphically signed in.

I'm 110% it's the server version. What I mean is I can connect wireless via ssh username@ipaddress but if I type sudo reboot it reboots but I then loose the connection.

---

### Post by arrrghhh on 2011-04-11
> **Sulcalibur said:**
> I'm 110% it's the server version. What I mean is I can connect wireless via ssh username@ipaddress but if I type sudo reboot it reboots but I then loose the connection.

Well if you reboot, the network connection will obviously drop.

You'd need a DRAC or some other piece of hardware to see the entire boot process - SSH only works when the SSH service (and therefore the server itself) is up and running...

---

### Post by 1clue on 2011-04-11
@original poster.

Make sure you install the server version of Ubuntu, and don't bother trying for any window managers.

I haven't tried this for years, but some distributions of Linux set their installer up so that you could log in via a serial cable with a terminal program on your laptop.  Not sure if Ubuntu comes set up like that or not, but it's something you might consider trying.

The reason I say that is because if your system goes down for some reason and won't boot cleanly (for example a corrupted filesystem) it won't bring the network up anyway, and you have to use some form of physical terminal to get it going again, or even just find out what's going on.

Chances are the console could be set up on a USB port as well, so you might just need the usb-to-usb cable.

Good luck and have fun.

---

### Post by Sulcalibur on 2011-04-11
> **arrrghhh said:**
> Well if you reboot, the network connection will obviously drop.

You'd need a DRAC or some other piece of hardware to see the entire boot process - SSH only works when the SSH service (and therefore the server itself) is up and running...

Thats my point, so basically it will always need a keyboard and monitor at hand :(

---

### Post by 1clue on 2011-04-11
> **Sulcalibur said:**
> Thats my point, so basically it will always need a keyboard and monitor at hand :(

Or a serial cable and terminal app on the laptop.

**Edit:** [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

### Post by arrrghhh on 2011-04-11
> **Sulcalibur said:**
> Thats my point, so basically it will always need a keyboard and monitor at hand :(

Why do you need to see/mess with the boot process?  I've only needed to do that once - the initial setup.

Well, there was a second time... lost the keys to the server, needed to setup password auth temporarily :p.

I just snag the monitor/keyboard from my desktop, figure out the issue, and put it back... I guess if you don't own any you could borrow them from a friend until you get the issue sorted?

My point is, you should very rarely ever need to connect a monitor or a keyboard.

---

### Post by 1clue on 2011-04-11
> **arrrghhh said:**
> Why do you need to see/mess with the boot process?  I've only needed to do that once - the initial setup.

Well, there was a second time... lost the keys to the server, needed to setup password auth temporarily :p.

I just snag the monitor/keyboard from my desktop, figure out the issue, and put it back... I guess if you don't own any you could borrow them from a friend until you get the issue sorted?

My point is, you should very rarely ever need to connect a monitor or a keyboard.

Wow.

You and I are from two different worlds.  I'm addicted to at least being able to have a root console.

But that said, you CAN do it through a serial cable which hangs on the wall or sits in a drawer taking up zero space until you need it, as long as there's another computer somewhere which can run a terminal app.

---

### Post by arrrghhh on 2011-04-11
> **1clue said:**
> Wow.

You and I are from two different worlds.  I'm addicted to at least being able to have a root console.

But that said, you CAN do it through a serial cable which hangs on the wall or sits in a drawer taking up zero space until you need it, as long as there's another computer somewhere which can run a terminal app.

I guess I don't see the need for it.  My server sits in the corner, and does its job... The thing hardly reboots, and is always available... so I don't see the need to have console access.  If something blows up, I can drag a monitor/keyboard over to sort out the issue, then put it away when I'm done.

Why do you need to always have console access?  Are you constantly changing BIOS options?  lol.

---

### Post by 1clue on 2011-04-11
> **arrrghhh said:**
> I guess I don't see the need for it.  My server sits in the corner, and does its job... The thing hardly reboots, and is always available... so I don't see the need to have console access.  If something blows up, I can drag a monitor/keyboard over to sort out the issue, then put it away when I'm done.

Why do you need to always have console access?  Are you constantly changing BIOS options?  lol.

I don't need *continual* console access, but rather *continually available* access.  I've had three machines which didn't even have video cards, and several for which I didn't have a spare keyboard or monitor.  The OP seems to be in the same situation, and if it were me I would much rather have a serial cable than a keyboard and monitor.

At one of my prior jobs, we maintained a room full of commercial UNIX systems (between 43 and 78 systems depending on when) with just two VT220's and two 50 foot serial cables.

I haven't tried it recently enough that I had to try the USB route though, so I don't know if it complicated things much.

---

### Post by arrrghhh on 2011-04-11
> **1clue said:**
> I don't need *continual* console access, but rather *continually available* access.  I've had three machines which didn't even have video cards, and several for which I didn't have a spare keyboard or monitor.  The OP seems to be in the same situation, and if it were me I would much rather have a serial cable than a keyboard and monitor.

At one of my prior jobs, we maintained a room full of commercial UNIX systems (between 43 and 78 systems depending on when) with just two VT220's and two 50 foot serial cables.

I haven't tried it recently enough that I had to try the USB route though, so I don't know if it complicated things much.

Ah.  Well yes, I guess I do kinda have tunnel vision in a sense - I forget there's rigs out there without any video card whatsoever :p.

I use serial cables every day, but with routers and switches, not servers ;).  Hopefully Sulcalibur can use a serial cable - a lot of new computers come without the port at all!  Not sure how USB works in this respect either.

---

### Post by 1clue on 2011-04-11
There are usb-to-serial port converters, but the device maps to a different location so you need to change that.  Not sure if you need 2 converters or if you can just go straight USB to USB.  Someday I will find out.

If it can be simply a USB to USB cable then it will be super cheap and handy.

---

