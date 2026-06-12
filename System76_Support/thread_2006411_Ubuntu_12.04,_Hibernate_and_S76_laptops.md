---
title: "Ubuntu 12.04, Hibernate and S76 laptops"
date: 2012-06-19
forum: System76 Support
---

### Post by Newbunto on 2012-06-19
I just upgraded from 11.10 to 12.04 and one change is that Hibernate is disabled by default. (The procedure to enable it again is easy to find but difficult to understand i.e. opaque but works if you just do it without understanding it.)

I may have got the wrong end of the stick but ...

It seems like this is a somewhat controversial reaction to unreliable hibernation in some hardware.

It seems as if System 76 is supposed to certify hibernation on each of its platforms (in order to avoid being disabled by default). Is that right? If so, any comments?

I find the design decision to disable hibernation by default a bit odd. I never had a problem hibernating on 11.10 and perhaps Ubuntu would be able to tell that. Or maybe it should have asked me at some point e.g. during the upgrade.

Since hibernation is really just a complete shutdown and then a special boot to wake up again, I am a bit surprised that hibernation is so problematic. Sure I know that network connections aren't really going to come back 'as is' and I know that things always get more complicated when you dig into the details but is hibernation really a problem?

---

### Post by 3Miro on 2012-06-19
Hibernation came about long time ago when systems took forever to boot. Today, save-session and shutdown is pretty much the same thing. Also, suspended laptops can last a very long time. Hibernation no longer has an edge in either speed or energy consumption

There is no special certification for enabling hibernation, you do with your hardware whatever you want.

I don't know how problematic hibernation is in general, however, it is a problem for encrypted systems. I had some issues with having to write several passwords to get in as opposed to just one master password. I did full HDD encryption, but I think you will have the same problem if you are using encryption for your home folder (i.e. you need encrypted swap partition which is used to hibernate).

---

### Post by Newbunto on 2012-06-19
> **3Miro said:**
> it is a problem for encrypted systems

Good point about encryption. "Fortunately" I don't encrypt either my home folder or the swap partition so that isn't a problem for me.

It seems I may have spoken too soon about hibernation working in 12.04.

I normally hibernate my laptop every night, rather than shutting down. It seems that worked in Ubuntu 11.10. I hibernated hundreds of times without a problem.

Now with 12.04 ... I think it worked the first time after I upgraded (after I re-enabled it!) but yesterday I tried three times to hibernate and it didn't work. I just had to shutdown. "Didn't work" means: It appeared to be making the right changes to go into hibernation but then suddenly didn't and just put up the lock screen.

This morning as a test I tried to hibernate after booting up and it worked correctly.

Anyone else having a problem with hibernation in 12.04?

---

### Post by Newbunto on 2012-06-19
> **3Miro said:**
> Today, save-session and shutdown

Please tell me more about "save-session".

For me hibernation is not about boot time and not really even about energy consumption. It's about the time to get everything "just so" - establishing network connections (file servers etc.) and entering passwords, sorting out external display, starting Thunderbird and entering passwords, starting FireFox and entering more passwords, ...

As a relatively new Linux user, yes, maybe some of this can be done "smarter".

> Also, suspended laptops can last a very long time. Hibernation no longer has an edge in either speed or energy consumption

??? Hibernation must surely have the edge in energy consumption.

Hibernating laptop draws 0 W
My laptop "suspended" draws about 5 W. (Actual readings 4.8 W .. 5.2 W)

5 W isn't a whole lot but it all adds up and if you care at all about CO2 emissions then hibernate is better than suspend and hibernate must be available as an option.

I have no doubt that the gap in power between these two is less than it was some years ago.

As far as speed goes, while I didn't time it, unsuspending would be *much* faster than resuming from hibernation. (A normal boot for me is 40 seconds and I think resuming from hibernation is about the same.)

---

### Post by 3Miro on 2012-06-19
I am not trying to argue whether or not hibernation has any use, all I am saying is that very few people use it. I mostly use XFCE, which has the option "save session on logout". If I reboot my machine, it brings up my browsers/file managers or other opened documents. I am sure Unity has some option like that, probably automatic and I am assuming this is what most people use nowadays.

Actually, I think most people just don't reboot or very rarely if ever.

Having said that, there is no reason why you shouldn't be able to have hibernation enabled. If you post detailed specs (i.e. laptop model) you can wait for isantop to give official help, or you can go to the System76 web-page and start a support request.

---

### Post by isantop on 2012-06-20
> **Newbunto said:**
> Please tell me more about "save-session".

For me hibernation is not about boot time and not really even about energy consumption. It's about the time to get everything "just so" - establishing network connections (file servers etc.) and entering passwords, sorting out external display, starting Thunderbird and entering passwords, starting FireFox and entering more passwords, ...

As a relatively new Linux user, yes, maybe some of this can be done "smarter".



??? Hibernation must surely have the edge in energy consumption.

Hibernating laptop draws 0 W
My laptop "suspended" draws about 5 W. (Actual readings 4.8 W .. 5.2 W)

5 W isn't a whole lot but it all adds up and if you care at all about CO2 emissions then hibernate is better than suspend and hibernate must be available as an option.

I have no doubt that the gap in power between these two is less than it was some years ago.

As far as speed goes, while I didn't time it, unsuspending would be *much* faster than resuming from hibernation. (A normal boot for me is 40 seconds and I think resuming from hibernation is about the same.)

A resume from hibernate will be slower since it has to boot *and* load the contents of RAM from swap. Additionally, if the CO2 emissions are concerning, then the better course of action is to lobby for adoption of clean power generation.

Hibernate is a hackish solution to a problem. Even on our systems multiple hibernates tend to cause issues and become unreliable. However, suspend is much cleaner, and we have seen hundreds of consecutive suspends without issue. 

Hibernate also requires grossly oversized swap partitions. Imagine ordering a laptop with 32 GB of RAM and a 60 GB SSD. The user will have less than half of their original storage available, since the rest will be taken up by swap. And if the swap is less than that, the hibernate *will* fail. Those are the big reasons driving the deprecation of hibernate.

---

### Post by brdmn on 2012-06-21
Just my two cents...  I'm on Xubuntu 12.04 on a lemu4.  I just shut down the machine after I'm done.  Rebooting takes literally less than 10 seconds, and the machine is actually ready to use.  I can't imagine that hibernate+resume could be much better.

As an aside, my Windows 7 based Thinkpad takes about 30 seconds to resume from hibernate, after which there's a good 2-3 minutes of hard drive thrashing before the laptop is remotely usable.  Amazing.  No wonder the default setting is to hibernate after some ungodly number of hours, and to avoid it entirely if the laptop is plugged in.

---

### Post by Newbunto on 2012-06-22
> **3Miro said:**
> I am sure Unity has some option like that

Maybe not. I saw some net chatter that it had been dropped.

I can't see how saving the session is really going to work in the general case. At that level the system simply doesn't know all the state of every application. That's what's good about hibernation.

OK, I see everybody wants to argue that I shouldn't be using hibernation so it doesn't matter that it doesn't work. But can we leave those arguments to one side.

Fortunately the next time I tried it, it did work. So at this stage I don't know whether the few times that it didn't work were an irreproducible glitch. Or the few times that it did work are the glitch. Too soon since upgrade to 12.04.

I will have to do more testing.

@brdmn

> Rebooting takes literally less than 10 seconds,

Hmmm. Mine takes 40 seconds to do a normal boot and that's just to the login screen. (I thought I had a decent spec laptop but ?) The real pain is after that - which is why I am interested in hibernation.

@isantop

> Hibernate also requires grossly oversized swap partitions. Imagine ordering a laptop with 32 GB of RAM and a 60 GB SSD.


Yeah, that's why I have an SSD for the files and a HDD that is supposed to contain the swap partition (among other things). Yes, it would make hibernate and resume a bit slower but it solves the specific problem that you are identifying.

The swap partition right now is on the SSD.

---

### Post by isantop on 2012-06-22
> **Newbunto said:**
> @isantop



Yeah, that's why I have an SSD for the files and a HDD that is supposed to contain the swap partition (among other things). Yes, it would make hibernate and resume a bit slower but it solves the specific problem that you are identifying.

The swap partition right now is on the SSD.

It would allow for more storage, but A. most computer (especially laptops) only have {space for} one hard drive. On top of that, with that configuration, if the swap is ever utilized the system will grind to a slow crawl.

---

### Post by brdmn on 2012-06-22
> **Newbunto said:**
> 
Hmmm. Mine takes 40 seconds to do a normal boot and that's just to the login screen. (I thought I had a decent spec laptop but ?) The real pain is after that - which is why I am interested in hibernation.


To tell you the truth, the first time I booted up with Xubuntu, I thought something was wrong... :p  I've never had an SSD before, maybe that's the reason?  I also configured my system without swap (8GB of RAM, most of which is hardly used in my case.)   The only other thing I can think of is that Xubuntu might enjoy some advantages over Ubuntu in boot time, especially after the login screen.

---

### Post by kend650 on 2012-06-24
I think it would be great if System 76 DEFINED what hibernation and suspend are and then specify how they should work on their products.

I am currently unable to get back to 'normal' after closing the lid (hibernating?) my Bonobo 12.04.

Any suggestions?

---

### Post by Carborundum on 2012-06-24
> **kend650 said:**
> I think it would be great if System 76 DEFINED what hibernation and suspend are and then specify how they should work on their products.

I am currently unable to get back to 'normal' after closing the lid (hibernating?) my Bonobo 12.04.

Any suggestions?
[Hibernate]("http://en.wikipedia.org/wiki/Hibernation_%28computing%29")
[Suspend]("http://en.wikipedia.org/wiki/Sleep_mode#Sleep")

Can you provide more details on what happens when you re-open the lid of your Bonobo? Is the system completely unresponsive, or are you able to switch to another tty? Do you see anything at all (e.g. a mouse cursor), or is the screen completely black?

There are a number of bug reports on Launchpad reporting behavior similar to what you are describing, for example [#982299]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/982299"). If you have a Launchpad account, you can try to see if you can find one that matches what you are observing and mark it as affecting you.

---

### Post by kend650 on 2012-06-24
When I lift the lid back up, there is no response from keyboard, mouse, touchpad.  The power-on light is still lit, and no combination of keyboard clicks (at least, none that I have found) powers the laptop back up.  

I have to hold down the power button till it shuts off then restart.

---

### Post by Carborundum on 2012-06-24
> **kend650 said:**
> When I lift the lid back up, there is no response from keyboard, mouse, touchpad.  The power-on light is still lit, and no combination of keyboard clicks (at least, none that I have found) powers the laptop back up.  

I have to hold down the power button till it shuts off then restart.
Is this reliably reproducible (e.i. it happens every time you suspend your computer)?

Next time it happens, could you try pressing Ctrl + Alt + f1 simultaneously? This should bring up tty1, from which you would be able to control your system from the terminal.

If that doesn't work, press and hold Alt + SysRq and then press the following keys in order: 'R', 'E', 'I', 'S', 'U', 'B'. That should reboot your system gracefully.

If neither of those work... That's a pretty serious problem.

---

### Post by brdmn on 2012-06-24
> **kend650 said:**
> When I lift the lid back up, there is no response from keyboard, mouse, touchpad.  The power-on light is still lit, and no combination of keyboard clicks (at least, none that I have found) powers the laptop back up.  

I have to hold down the power button till it shuts off then restart.

I don't know about your specific machine, but I had an Aopen DE 945FX with the exact same symptoms.  I ended up changing my power manager settings to NEVER hibernate OR sleep.  Never had any other issues with the hardware though, so hopefully, that will be the case for you as well.

---

### Post by kend650 on 2012-06-24
First of all thanks for the Wiki defs of Hibernation and suspend.

Now for the strange part, I closed my lid a couple of hours ago, and when I came back and opened the lid, the system started back up.  I did do one thing from Todd in another thread:

"I just got this advice in another thread: while your laptop is in a happy state, go to Keyboard Layout --> Options --> Key Sequence to Kill X-Server, and enable the Ctrl-Alt-Backspace sequence by clicking the radio button next to Ctrl-Alt-Backspace in the popup. 

Then when your computer is in this "mouse cursor only" state after a resume from the suspended state, try Ctrl-Alt-Backspace. I haven't had to do it yet, but it's reputed to work. 

Todd"

I did do this and it appears to work.  I'll have to let it percolate for awhile and see if this fix works long term.

Thanks again for all the suggestions and help...

Kend650

---

### Post by isantop on 2012-06-25
> **brdmn said:**
> To tell you the truth, the first time I booted up with Xubuntu, I thought something was wrong... :p  I've never had an SSD before, maybe that's the reason?  I also configured my system without swap (8GB of RAM, most of which is hardly used in my case.)   The only other thing I can think of is that Xubuntu might enjoy some advantages over Ubuntu in boot time, especially after the login screen.

Just a side note: an 8GB swap partition is definitely a bit excessive, but I would recommend keeping a small swap partition of around 2 GB available. You never know when a process will go crazy and eat up RAM, and you want to be able to catch that before the system crashes.

---

### Post by Newbunto on 2012-07-06
> **Newbunto said:**
> 
It seems I may have spoken too soon about hibernation working in 12.04.

Well, after 2 weeks of testing, failure to hibernate has re-occurred once. So I guess it works about 90% of the time and fails about 10% of the time - in my configuration.

Does anyone have any suggestions? e.g. things to check / look at when it's refusing to hibernate? things to change?

---

### Post by amoxicillin on 2012-07-06
I am having the "cursor only" problem with my Lemu4 as well. Todd's ctrl+alt+backspace trick has worked for me.  I also found that suspending my computer with the fn+(f4? I don't have my Lemu4 in front of me at the moment) before closing the lid seemed to help as well.  I am thinking this may have to do with the kernel bug problem they mentioned in the sticky notes.  A number of people seem to be having this problem which makes it less likely a hardware issue.

---

### Post by isantop on 2012-07-09
> **amoxicillin said:**
> I am having the "cursor only" problem with my Lemu4 as well. Todd's ctrl+alt+backspace trick has worked for me.  I also found that suspending my computer with the fn+(f4? I don't have my Lemu4 in front of me at the moment) before closing the lid seemed to help as well.  I am thinking this may have to do with the kernel bug problem they mentioned in the sticky notes.  A number of people seem to be having this problem which makes it less likely a hardware issue.

We've just released the instructions for installing the new kernel. Please see the updated sticky thread at the top of this Forum.

---

