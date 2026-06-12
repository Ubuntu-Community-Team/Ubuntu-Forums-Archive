---
title: "An uncertain future awaits me in Linux..."
date: 2006-07-10
forum: The Cafe
---

### Post by Jucato on 2006-07-10
**Foreword**: Please allow me to rant a bit, as the results of my "investigations" for the past days have not been very inspiring, to say the least. This thread is both a rant and a plea for help, specially from people who are familiar with the Linux kernel.

**Short Summary**: It seems that the optical mouse that I am currently using right now will no longer work with kernel versions higher than 2.6.15-23. This incudes 2.6.16, 2.6.17, and even Ubuntu's own 2.6.15-25.

**Background Story**:
**May 2006**: SymphonyOS 2006-05 Beta was released. I was always curious about this little project so I decided to try it out, since it came in a Live CD. However, my mouse didn't work. Thinking that since this was a beta version, it might be due to some problems with the OS itself. I decided not to pursue the matter further.

**June 2006**: Dapper Drake was released. A few days after it's official release, a kernel update was made available in order to address some security issues with the default installed kernel. This update installs the 2.6.15-25 kernel. The upgrade was successful, but my mouse didn't work. I posted this problem several times, and even filed my first ever bug report. There were others who had problems with the upgrades as well, and I was hoping my problem would be similarly solved in a few days. I was not that fortunate. While almost everybody else's problems got solved little by little, mine began to gather dust.Defeated, I resigned myself to just use the 2.6.15-23 kernel for the meantime, hoping that a future kernel upgrade would be more promising.

**July 2006**: I began playing around with VMWare Server from the Ubuntu repositories. Out of a blue, I decided to give SymphonyOS one more try using VMWare. To my surprise, the mouse worked. Then, suddenly getting some inspiration from nowhere, I decided to type *uname -r* in the terminal. I then discovered that it was using the 2.6.16 kernel. I began to think that my mouse problems was, in some way, related to the kernel version that is being used by the distro. Prompted by this, I started looking for Live CD distros that were using the latest Linux kernels, in the hope of discovering whether this is really an Ubuntu only problem, a Debian only problem, or really a basic kernel problem. These were the distributions I tried and the kernel versions they were using:

> Ubuntu 6.06 LTS (Debian-based) kernel 2.6.15-23 and 2.6.15-25
SymphonyOS (Debian-based) kernel 2.6.16
KNOPPIX 5.0.1 (Debian-based) kernel 2.6.17
SimplyMEPIS 6 beta 3 (Ubuntu-based) kernel 2.6.15-22
Berry Linux (Fedora Core-based) kernel 2.6.16
GoblinX mini (Slackware-based) kernel 2.6.16.12

The results of my "investigations": Only SimplyMEPIS 6 and Ubuntu using the 2.6.15-23 kernel was able to make my mouse work, confirming that it was indeed a kernel issue. I took a further step by testing these distros again, using a previous but currently-not-working-properly mouse (non-optical, still used the mouse ball, or whatever it's called). It was a mouse from a company called UniTek (serial number UM 1018, I think). And it worked. All of them worked. So based on these, I concluded that the latest versions of the kernel, and possibly (but hopefully not) future versions of the kernel cannot detect my current mouse. It fails in this aspect of hardware detection.

So this is a problem with the kernel, the very heart and soul of a GNU/Linux OS. Then my problem begins on how I could probably "solve" this. 

**Possible solutions**:
1. Compile my own version of the kernel, again hoping that a customized kernel would solve the problem. But then, would that mean I would have to compile everytime there's a new kernel version that comes out or everytime a patch is released? I didn't pick Slackware for a reason...

2. Buy a new mouse. This optical mouse is a generic PS/2 mouse, which I was able to buy from a very respectable local dealer for just around US$ 3.00 (rough conversion for our local currency). The dealer is a respectable one, but it doesn't really specializes in computer hardware/peripherals. Branded mice, like those from Logictech or A4 or Genius cost 4 times as much as the one I'm using. For someone out of work, that's qutie a big cost. I was hoping to save some cash in order to upgrade my system's memory or buy a tablet (not a Tablet PC!), but of course a mouse takes priority. But my dilemma is this: even if I were to buy a new, branded, mouse, what assurance do I have that something like this would not happen in the future? I mean, I have a perfectly working mouse under the present and past versions of the kernel, and now there's a possibility that it will not/never work in future versions. How do I know that it won't happen again with another mouse?

3. Third option would just to switch to BSD... Or if worse comes to worst, even back to Windows...

This incident has left me very sad (to put it mildly), a bit disappointed, and confused. I was led to believe that Linux is supposed to be compatible with a large number of non-Windows specific devices. I also thought that newer kernel versions accomodated/supported more and more hardware and not actually remove already supported hardware.

Then again, this might be a bug, or might be a very, very personal bug, something that only I have the misfortune of experiencing, which makes my situation all the more depressing. If it's a bug that I and only I have experienced, then the possibility of it being fixed, just for me, would be nil. And I wouldn't really be able to know if it's a kernel bug unless I file a bug report, right? Which brings me to the problem of filing a bug report for the Linux kernel. In my 7 months of using Linux, I have filed only one bug report, and even that was a disaster, IMO. Filing a bug report on a very busy and professional place like the kernel might be a task that may be beyond me.

This is why my future is uncertain. I'm not sure how to proceed. I have big plans for my Linux experience, but now they're all put into a temporary hiatus because of this.

I'd appreciate any help, input, comments, criticism, whatever. This hasn't been a very good day for me... :(

P.S. I'm attaching dmesg outputs from the test runs I made (continued in a second post). There are two sets per distro, one with a working mouse using my old mouse, and one with a non-working mouse using my current mouse. The dmesg for Ubuntu with a working mouse is using kernel 2.6.15-23, while the one with no working mouse is 2.6.16-25. If anyone with the know-how in deciphering these cryptic lines could take the time to read some of them, I'd be truly, truly grateful.

Btw, it seems that a common line in all the dmesg with non-working mice is
> psmouse.c: Failed to enable mouse on isa0060/serio1

---

### Post by Jucato on 2006-07-10
Continuation of the dmesg files...

---

### Post by fuscia on 2006-07-10
i'm using a $5.00 GE optical mouse that i got from home depot, in dapper. it's a usb mouse.

---

### Post by Jucato on 2006-07-10
> **fuscia said:**
> i'm using a $5.00 GE optical mouse that i got from home depot, in dapper. it's a usb mouse.

You're lucky, I guess.
Still no response from the "knowledgeable ones"...
Maybe I'll try finding a way to file a bug report for the kernel, but I don't want to make a fool out of myself as much as possible.

Or just take my chances in buying a new mouse, and hope that something like this will never happen again... :(

---

### Post by RAV TUX on 2006-07-10
my Razer Diamondback mouse worked with all OS's listed.

---

### Post by Christmas on 2006-07-10
I had a Logitech MX310 which was detected correctly in Breezy and Dapper, now I have a 7$ Umax SuperFox 0700 and works fine. Maybe it was the model of your mouse not very common, otherwise every mouse should work I think.

---

### Post by Kimm on 2006-07-10
My USB Wireless mouse works flawlessly in Ubuntu (well... never botherd to configure buttons). And it wasnt to expensive.

Perhaps you should look into buying something new?
Otherwise its allways possible to downgrade the kernel (at least until you can buy something new) by compiling your own.

---

### Post by Jucato on 2006-07-10
Yeah I figured I would eventually have to buy a new mouse. I just can't shake the fear/uncertainty that it might happen again. Although buying a more expensive but more well-known branded mouse might give a sort of guarantee.

Better start saving up some more. 

Thanks for taking the time to read my long rant...

P.S. Is this enough material to file a bug report in the kernel mailing list? Or should I just leave it like that and get on with my life?

---

### Post by nalmeth on 2006-07-10
Go USB, seems to be the best for everyone. They've worked flawlessly for me too.

---

### Post by GuitarHero on 2006-07-11
Yes, my USB mouse works even though its made by microsoft

---

### Post by Jucato on 2006-07-11
So if I were to buy a new mouse, you'd recommend that I buy a USB mouse rather than a PS/2?

---

### Post by Sheinar on 2006-07-11
[QUOTE=Fenyx]P.S. Is this enough material to file a bug report in the kernel mailing list? Or should I just leave it like that and get on with my life?[/QUOTE]
File it. A bug is a bug. Unless the support for that device was taken out due to it being buggy. Even if you get a new mouse (definitely go USB), best to inform the kernel developers that a device that was working in previous versions isn't working anymore. At worse they'll say that it's already known...or perhaps throw a hissy fit like only a software developer can.

---

### Post by benplaut on 2006-07-11
I recommend a cheap USB mouse.  Microsoft ones are very nice, and have great support -- stop by your local bussiness IT room and see if they can give you one :)

---

### Post by tsb on 2006-07-11
I don't think supporting ancient hardware is the way to go.  That certainly won't attract hardware makers and therfore won't attract more Linux drivers and software.

I suggest a BT mouse personally.  Logitech and MS both make good ones AFAIK.

---

### Post by T700 on 2006-07-11
"An uncertain future awaits me in Linux..."
[I]
It's a mouse.[/I]  With the amount of time and effort you've put into making this one work, you could have earned enough to buy several new ones.  

Paul

---

### Post by Jucato on 2006-07-11
> **T700 said:**
> "An uncertain future awaits me in Linux..." 
I did say this thread was a rant, written in frustration and confusion. 
> *It's a mouse.*
Like I said, I know that the easiest solution would be to buy a new mouse. But I also said that there's a tiny (very tiny) question in my brain, asking whether this would happen again. Then I would have to buy another mouse again, even if the previous one was working.

Anyway, I might be buying a new one this weekend...

> With the amount of time and effort you've put into making this one work, you could have earned enough to buy several new ones.
I don't understand this statement. Making what work? I'm currently using the default Ubuntu install kernel (2.6.15-23), so there wasn't much work to be done. Downloading the ISO's just took at most less than 48 hours, burning them on a CD-RW so I could use the same CD over and over again, with a different distro.

Although it's not impossible, going out to buy a new mouse isn't the most convenient thing for me right now, because of my situation. My allowance (roughly $2/week) is only given to me on Sundays. The trip to the nearest store where I can buy a good mouse costs $2, back and forth. And I can only leave on weekends when someone else can take my place in watching over my grandma.

Anyway, like I said, I'm buying a new mouse this weekend. I'll just be keeping my fingers crossed...

---

### Post by shrimphead on 2006-07-11
> **T700 said:**
> "An uncertain future awaits me in Linux..."
[I]
It's a mouse.[/I]  With the amount of time and effort you've put into making this one work, you could have earned enough to buy several new ones.  

Paul

that's not really the point though is it? If this kind of mentality was commonplace then Linux would never be able to support the amount of hardware that is does now! 

I can just imagine the ACPI support team saying "oh i'll save my self some time by buying a different laptop that already works rather than fixing this one!"

---

### Post by Zimmer on 2006-07-11
> **Fenyx said:**
> 
...
This is why my future is uncertain. I'm not sure how to proceed. I have big plans for my Linux experience, but now they're all put into a temporary hiatus because of this.

I'd appreciate any help, input, comments, criticism, whatever. This hasn't been a very good day for me... :(
...


I can identify with your future concerns, but from a Windows perspective !
A few years ago (before I started using Linux) I bought a new scanner (£80.00 sterling ) and was using Win98. 6 months later I decided to buy a new computer which came with Win XP loaded. The scanner would not work with XP:no drivers. No drivers to this day. I had to buy a new scanner to work with the XP machine.(it won't work under Linux either..no SANE backend).
I have to wonder whether my current scanner will work under the new Win Vista when it is released...no guarantee it will.... 
Moral: you pays your money and you takes your chance. The manufacturers may support today's OS but there is no guarantee they will for the next version.. or that the new OS will provide backwards compatibility.

---

### Post by T700 on 2006-07-11
deleted because I can be a bit of an *******.  Sorry about that.

---

### Post by Jucato on 2006-07-11
> **Zimmer said:**
> I can identify with your future concerns, but from a Windows perspective !
A few years ago (before I started using Linux) I bought a new scanner (£80.00 sterling ) and was using Win98. 6 months later I decided to buy a new computer which came with Win XP loaded. The scanner would not work with XP:no drivers. No drivers to this day. I had to buy a new scanner to work with the XP machine.(it won't work under Linux either..no SANE backend).
I have to wonder whether my current scanner will work under the new Win Vista when it is released...no guarantee it will.... 
Moral: you pays your money and you takes your chance. The manufacturers may support today's OS but there is no guarantee they will for the next version.. or that the new OS will provide backwards compatibility.

I can totally relate to that. A few years ago, I also bought a scanner that worked up to Windows ME. No driver was available for Windows XP. But being Windows (or Windows-based), I'm not surprised (specially after they recently decided to stop providing patches for Windows 98). But I was thinking, this is Linux. My mouse is definitely not ancient, it's just half a year old.

Maybe underneat all these, my real question is "why?" Why does a device suddenly not work in new kernels? Why is a device suddenly not supported?

(Why am I even ranting on this... :()

---

### Post by Jucato on 2006-07-11
> **T700 said:**
> It's a bloody mouse!  US$10.  5 pounds.
Let me see. If I were to use the figures I gave, a US$10 mouse would, what, take me 5 weeks to save up for? Not to mention the traveling expenses? Luckily I have a bit more money saved up. But just around US$ 15. You have to understand. I'm unemployed, living at home and taking care of my grandma, with very limited means of going out and buying a mouse from the nearest computer store.

> If you want to maintain compatibility for every old, cheap, piece of hardware, be my guest. In the real world, no OS does that. Not Windows, not Mac, not Linux, not anything.
old - yes we should slowly start removing support for "legacy" hardware, regardless of the fact that Linux once prided itself on it's ability to run on these kinds of hardware.
cheap - of course. cheap stuff are low quality stuff. Anything you can get for a bargain price is bound to be defective in some way. How much did I pay again to get Ubuntu?

Btw, my mouse, like I said earlier, is not old. It is cheap, though. And therein probably lies the root of all my problems.

---

### Post by Miguel on 2006-07-11
OK, Fenyx. [list]
[*]You have a mouse that doesn't work under certain controlable and replicable situations.
[*]You know exactly the make and model of your mouse
[*]Your issues can be traced back to the kernel
[*]You have dmesg outputs from different kernels and different distros.
[/list]

This, for me, equates a great bug report. Send it. What's more, if you have bugzilla accounts in the other distro's (unlikely) also fill the bug report there. It doesn't get much better than what you did. IMHO, if your mouse doesn't need drivers in windows, if it uses a standard protocol on a standard PS2 connection, it should work. Today and tomorrow. Period. Come on, there is still pre-EISA hardware support on the kernel.

BTW: good luck with your grandma

---

### Post by Jucato on 2006-07-11
Thanks for the tips. I already filed a bug report in Launchpad/Malone last month when my mouse started behaving like that. After some time, however, an Ubuntu dev came by and commented that it was, in fact, an xorg bug and transferred it from "Affects: kernel" to "Affects: xorg". I just posted yesterday the additional details that I posted in this thread. I'm hoping that some Ubuntu dev would notice it again.

That was my first ever bug report in my whole life. And it, IMHO, was a disaster. I probably didn't get the words right, or didn't immediately include the needed information, or didn't even know what logs/files were needed to be attached. Let's just say that I developed a sort of bug-filing trauma. But I'm willing to learn how to file bug reports properly.

Here's the bug report I made: [https://launchpad.net/distros/ubuntu/+source/xorg/+bug/49996/+index](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/49996/+index)

In the mean time, a new kernel update is available. I'm going to sit this one out for a while... I'd rather have a stable system, than a perfectly secure but unusable system.

---

### Post by bruce89 on 2006-07-11
My mouse went haywire (had to double click all the time, and sometimes double clicked when I single clicked), so I replaced it temporarily with another one, which seems fine.

---

### Post by Miguel on 2006-07-11
> **Fenyx said:**
> After some time, however, an Ubuntu dev came by and commented that it was, in fact, an xorg bug and transferred it from "Affects: kernel" to "Affects: xorg".

Thanks again for posting your bug. This helps us all. It might be that your bug is simply a regression in Xorg. You can check this in your "beloved" logs (more info later ;))

> That was my first ever bug report in my whole life. And it, IMHO, was a disaster. I probably didn't get the words right, or didn't immediately include the needed information, or didn't even know what logs/files were needed to be attached. Let's just say that I developed a sort of bug-filing trauma. But I'm willing to learn how to file bug reports properly.


LOL, it gets better with practice. Just don't worry, not everybody knows how to recover crashes and errors. If they need specific info from you, don't be shy to ask the commands. My first bug report was for a flight sim (Falcon 4.0) and went something like "fighters further than 30nm don't appear in your radar screen".


> In the mean time, a new kernel update is available. I'm going to sit this one out for a while... I'd rather have a stable system, than a perfectly secure but unusable system.

This one will make a new entry in grub, if you wondered, so you should  be more or less safe testing it. Anyway, I would trust the developer about x.org.

_*X.org errors and warnings*_

Errors are usually (i.e. always) marked with EE in the corresponding line. Similarly, warnings use WW. So instead of looking through the whole log looking for errors and warnings, you can directly filter these lines. X.org's log file is /var/log/Xorg.0.log (note zero, not o).

```

grep EE /var/log/Xorg.0.log
grep WW /var/log/Xorg.0.log

```
will only show lines containing EE or WW respectively. Everybody loves grep. It only shows lines containing a certain string of a long long file. You could try these commands in your non working distros. They might be of help.

For the kernel messages you can look at either /var/log/messages (this one is longer than a day without bread, as we say in Spain) or dmesg. It's certainly better to use dmesg, but for that you need to use what's known as a pipeline:

```

dmesg | grep EE
dmesg | grep "the word you want to filter"

```

The "|" symbol is called a pipe. It is a way to give the next program data from the previous program. So you run "grep EE" on the output of dmesg, intead of a file.

---

### Post by DoctorMO on 2006-07-11
Thats just not true at all

a pipe is a way to give the next program data from the previous program: from stdout to stdin (standard out, standard in), it doesn't use files nor paramiters.

---

### Post by Miguel on 2006-07-11
> **DoctorMO said:**
> Thats just not true at all

OK, thanks for reading all that and noting my mistake. It's edited now. Is it alright now? I don't want to put those things wrong because I don't want to mislead others and because I also learn from these things.

---

### Post by Jucato on 2006-07-11
@Miguel thank you for your detailed instructions. I might try that out after I install/upgrade the new kernel. The reason I'm quite hesitant to immediately test the new kernel upgrade is because the batch of upgrades also includes upgrading linux-restricted-modules-common and nvidia-glx. If both kernel and nvidia fails to work, then I'm done for...

Btw, when should I grep the Xorg logs? After installing the new kernel or after something else?

Also, my dmesg logs don't have EE's and WW's...

---

### Post by kop316 on 2006-07-11
> **bruce89 said:**
> My mouse went haywire (had to double click all the time, and sometimes double clicked when I single clicked), so I replaced it temporarily with another one, which seems fine.

Mine did that too, but there has been an update that has fixed that.

---

### Post by Miguel on 2006-07-12
> **Fenyx said:**
> Also, my dmesg logs don't have EE's and WW's...

I've noticed that too... :confused:

> Btw, when should I grep the Xorg logs?

I would boot in a perfectly working kernel and then copy /var/log/Xorg.0.log to somewhere in my directory and mark it as working or whatever you prefer. Then, I would boot in a non-working kernel (if you have it installed) and then and get the new /var/log/Xorg.0.log. You gan grep WW or EE in this new log. If it isn't much of a hassle, you could submit those. 

Anyway, don't bother too much. It is not nice to break your system intentionally (especially when the way you know to fix it is a reinstall) just for an error log. Although there could be interesting info in a live CD.

Maybe you are interested in looking at the differences yourself. OK. Open a terminal and maximize it (you will need the extra space). Then type 
```

vimdiff file1 file2

```

You will then see half screen showing each document. If there are many lines equal, they are skipped. Lines that are different are marked purple (awful colour), and the specific different part is marked in red. To exit this program (no, I'm not joking) you must press :q (enter) and :q (enter) again.

The curious thing is that in your bug report, the only WW that appears is related to cyrilic fonts, and has nothing to do with the mouse.

---

### Post by Jucato on 2006-07-12
> **Miguel said:**
> I've noticed that too... :confused:



I would boot in a perfectly working kernel and then copy /var/log/Xorg.0.log to somewhere in my directory and mark it as working or whatever you prefer. Then, I would boot in a non-working kernel (if you have it installed) and then and get the new /var/log/Xorg.0.log. You gan grep WW or EE in this new log. If it isn't much of a hassle, you could submit those. 

Anyway, don't bother too much. It is not nice to break your system intentionally (especially when the way you know to fix it is a reinstall) just for an error log. Although there could be interesting info in a live CD.

Maybe you are interested in looking at the differences yourself. OK. Open a terminal and maximize it (you will need the extra space). Then type 
```

vimdiff file1 file2

``` 
You will then see half screen showing each document. If there are many lines equal, they are skipped. Lines that are different are marked purple (awful colour), and the specific different part is marked in red. To exit this program (no, I'm not joking) you must press :q (enter) and :q (enter) again.

The curious thing is that in your bug report, the only WW that appears is related to cyrilic fonts, and has nothing to do with the mouse.

Yeah I noticed that WW line, too. Thanks again for your guide. I'm now beginning to download the latest updates EXCEPT the new kernel. I'll do that a bit later. 

Btw, is there a "vimdiff" counterpart for nano? I've had very unpleasant experiences with vim, and I try to steer clear of it as much as I can. But then again, beggars can't be choosers, right? :D

---

### Post by Miguel on 2006-07-12
> **Fenyx said:**
> 
Btw, is there a "vimdiff" counterpart for nano? I've had very unpleasant experiences with vim, and I try to steer clear of it as much as I can. 

I've searched with no joy for "geditdiff" or "nanodiff", but no joy. :cool: :D (I did look for them). But don't worry. As long as you only press "colon" q enter, noting wrong will happen. You can also try the command diff, but it is less visual than vim.

---

### Post by Jucato on 2006-07-12
> **Miguel said:**
> I've searched with no joy for "geditdiff" or "nanodiff", but no joy. :cool: :D (I did look for them). But don't worry. As long as you only press "colon" q enter, noting wrong will happen. You can also try the command diff, but it is less visual than vim.

Thought so. I did a bit of research, too. :D
Doing a search for "diff" in [http://packages.ubuntu.com](http://packages.ubuntu.com) gave quite a few results. I do remember, though, that once I encountered a KDE frontend to diff, but I never really got to know how to use it. 
Anyway, thanks again.

If you don't mind, just one last question, a bit unrelated though.
I'm planning to buy a new mouse this weekend, probably a Logitech, since it seems more popular. From the previous posts, it seems that a USB mouse is what I should buy, rather than a PS/2. What's your recommendation? :D

---

### Post by raldz on 2006-07-12
I am impressed how far you were willing to go just to make your mouse work.. For me, I'm a little lazy, if I was in your place I'll just report the bug and buy another mouse.. mouse is cheap.. But if it were a little more expensive piece of hardware, I'll go through the troubles just to make it work.. about you mentioning MEPIS, yes, I am also amazed how MEPIS works.. it simply works out of the box.. currently my Kubuntu and Ubuntu is still in my experimental/play PCs (currently using now).. I use MEPIS for my work machine.. while my 3 yr old son uses Kubuntu..

---

### Post by Miguel on 2006-07-12
> **Fenyx said:**
> 
If you don't mind, just one last question, a bit unrelated though.
I'm planning to buy a new mouse this weekend, probably a Logitech, since it seems more popular. From the previous posts, it seems that a USB mouse is what I should buy, rather than a PS/2. What's your recommendation? :D

I'm not knowledgeable in mice. I personally have a USB optical mouse that came with my laptop. It's a no-frills mouse. Only two buttons and the wheel. It works OK. I don't need more.

On the PS/2 vs. USB camp, the decission boils down to two things: the price and the number and position of your USB ports. I don't think PS/2 support will be dropped from the kernel anytime soon. Too many mice and keyboards are still PS/2. I'd bet that even serial mice are still supported. 

If you only have two USB ports, a PS/2 looks a better option. If the USB ports are too close, maybe having the mouse will not allow the use of the port next to it (big plug or whatever). You know, I only have two USB ports on my laptop, but if I unplug the mouse I still have the touchpad.

---

### Post by Jucato on 2006-07-12
@raldz: hehehe! I have a bit of an obssesive-compulsive attitude from time to time. :D

@Miguel: I also thought that PS/2 mice were more of a "standard" and are always supported. But this experience has made me a bit doubtful. It seems that those who posted here opted more for USB mice. I might go for one, too. Anyway, I have 4 USB ports, 2 of which are quite unused (1 slot is for my smartphone, the other is for a USB extender). 

Now to ask my countrymen in these forums for advice on a good brand/model. :D

---

### Post by Miguel on 2006-07-12
OK, the cheapest Logitec I've found in spain is the Logitech Pilot wheelmouse. It's wired, has three buttons plus wheel and I suppose it uses a ball. It's PS/2. But it costs 9.99&#8364; in spain (16% VAT included, I guess). The optical version costs an amazing 19.99&#8364;. It is a theft.

It seems you are actually paying a lot of brand. "Trust" mice seem cheaper, though I don't have any experience with these. In comparison, on the store just outside my house, the simplest *optical* Trust mouse is 6.60&#8364;, less than a third of the logitech... well, this store sells an optical Logitech for 9.70&#8364;, which is more reasonable.

Anyway, I've seen some mice sport a usb connection... plus a USB-to-PS/2 adapter. One of these should solve all your doubts... as long as it falls in your budget.

*EDIT:* You are right, Spanish prices are hard to translate to prices in the Philippines

---

### Post by Jucato on 2006-07-12
The most famous mice brands here are Logitech, A4, and Genius. I really don't like to buy "branded" stuff too much. For me, not everything that's branded, or even famous, works well. Windows is a clear example of that. :D But in this case, I think I have no choice, as a well known brand might be better supported than my cheap generic mouse...

UPDATE: Installed the new kernel. Didn't work. Xorg didn't have any EE or WW lines except for that single font WW. dmesg displayed the same error. I guess it's really time to buy a new mouse... :(

[off-topic]I'm typing this around 14:00 UTC. And the forum layout was changed... and I don't like (bordering around being annoyed?) the format/layout. Hope they change it ASAP...

---

### Post by 3rdalbum on 2006-07-12
If you can buy a TDE Electronics mouse, buy it. They come with a PS2/USB adapter, and the company is kind-of Linux friendly. (the packet for their flash drives says that they work with Linux Kernel 2.4)

---

### Post by Miguel on 2006-07-12
Hi again Fenyx,

I couldn't find your Xorg.conf file, though I am a bit retarded today, and my reading comprehension is really low. Anyway, my interest lies in what protocol you are using for your mouse. You should have somewhere in /etc/X11/xorg.conf something like this:

```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"            "/dev/input/mice"
        Option      "Protocol"          "ExplorerPS/2"
        Option      "Emulate3Buttons"   "true"
EndSection

```

You could try swapping "Auto", "ExplorerPS/2" and "IMPS/2" as possible protocols. Just a quick and dirty suggestion. I don't know if this will work but you can try.

---

### Post by wislon on 2006-07-12
I have an A4Tech wireless mouse, with a receiver that plugs into the PS/2 port. Works perfectly here in Ubuntu 6.06, and every other distro/livecd I've tried. But notafsck will it work in Knoppix. Go figure :)

---

### Post by ubuntu_demon on 2006-07-14
I understand your frustration.

I recommend the logitech optical wheelmouse (USB) which is probably also the cheapest logitech optical usb mouse.

My girlfriend has a logitech optical wheelmouse and it's a great mouse if you want a good and relatively cheap (and simple) mouse. I have two (different) logitech mouses and never had any problems. AFAIK everyone is happy with their logitechs.

---

### Post by philipacamaniac on 2006-07-14
Key concept: try to avoid "generic" or very obscure hardware when planning to use Linux. It's quite possible that not even Windows supports that mouse, without that manufacturer-provided drivers.

The Linux kernel team can only go so far as to including driver module after driver module after driver module. There will be times when they miss or deliberately skip an osbcure or generic piece of hardware. Remember that Windows XP doesn't natively support most new hardware. It is up to manufacturers to provide Windows drivers for their hardware. Likewise, it is up to them to provide Linux drivers for their hardware.

When you look at the sheer number of natively supported devices (not manufacturer-provided), Linux wins 10 times over, so the kernel team is actually doing a pretty good job.

So, by using Linux, you are actually helping the effort to get more device manufacturers on board the Linux boat. They need to see high numbers of users using an OS before they deem it financially viable to support with drivers.


I have seen several sub-$5 optical USB mice. A USB mouse is darn near guaranteed to work, because of USB device standards.

---

### Post by Jucato on 2006-07-14
Sorry I was only able to reply today. I had to take care of some stuff.

@Miguel: my Xorg in the currently working kernel is using ExplorerPS/2. Tried your suggestions. Didn't work. :(

So I guess I'm off to buy a new Logitech USB mouse tomorrow. I'll try not to buy those mice with more than 3 buttons, as it seems to be also causing a bit of a problem with some people.

@philipacamaniac: it was Linux's fame for supporting different kinds of hardware that led me to think that my mouse would also be supported. Besides, I already had that mouse before I started Linux. It worked perfectly under Windows. When I decided to try out Linux, I was initially worried that my mouse wouldn't be supported. So I was pleasantly surprised that it worked. That's why I'm also baffled that it doesn't work anymore in future kernel versions. I would probably have understood the situation better if my mouse didn't work from the very beginning.

Anyway, I'll be buying a new mouse. I'm going for a Logitech one, and hope that I'll find something less than US$ 6.

I also decided to just let the bug report at Malone go. Seems like it hasn't attracted any dev's notice, so the issue might be insignificant and moot (since I'm buying a new mouse).

Thanks for the help everyone!! I'll be back on track with my Linux plans/work, and on a new kernel. :D

---

### Post by fuscia on 2006-07-14
ooh! use ratpoison until the problem is resolved.

---

### Post by Jucato on 2006-07-14
I'm not sure that would work. Because my problem is probably more basic than a DE or WM problem. I'm not sure whether the problem lies on the kernel or on Xorg, or on both.

---

### Post by fuscia on 2006-07-14
> **Fenyx said:**
> I'm not sure that would work. Because my problem is probably more basic than a DE or WM problem. I'm not sure whether the problem lies on the kernel or on Xorg, or on both.

if your keyboard shortcuts work, then a keyboard fascist wm might be the thing for you, for now.

---

### Post by Jucato on 2006-07-14
Yes my keyboard works. 
I'm actually using the older 2.6.15-23 kernel, which still has support for my mouse. So I'm still able to work in Linux. Only problem is that I'm running a relatively not-so-secure system, since there have been 2 kernel updates in Ubuntu now.

Btw, there's one thing I've discovered in KDE that I'm not sure GNOME has, by default. It's extremely useful if you have no working mouse, you know how to get around with the keybaord, but you need to use the cursor. In KDE, you can turn your numeric keypad as a mouse! 8 will be up, 2 will be down, 4 will be left, 6 will be right, 7,9,1, and 3 will move the mouse diagonally, 5 is pressing a button, /, *, and - will toggle which action will be produced when you press 5 (left button, middle button, right button respectively). Isn't that convenient? :D

---

### Post by Jucato on 2006-07-16
UPDATE:

Just bought a new Logitech Optical USB Mouse. And it works in all the most recent kernel versions. I'm using the 2.6.15-26-k7 kernel right now, as I'm typing this. So far so good. I have one USB slot left (1 for the mouse, 1 for my smartphone, and 1 for the USB extender, making actually 2 USB slots left :D).

Only 2 disadvantages:
1. It costed almost 5x as much as my previous mouse. The cheapest Logitech optical (wheel) USB mouse I could find cost around US$ 5. There were other mice brands available (A4Tech, Genius, and Creative), but the price differences were just around US$ 1, so I opted to just buy the Logitech mouse, since it was so highly recommended.

2. My computer looks like a Dalmatian. The CPU case and keyboard is black, the monitor and the mouse is white, the USB externder is white, and the USB cable to my smartphone is black. Thank goodness my PC table is brown! :D

Thanks for everybody's input! I'm quite a happy camper now (though, I still can't get the initial frustrations off my mind...).

---

### Post by Fac51 on 2006-07-19
Wow!

---

### Post by Miguel on 2006-07-19
> **Fenyx said:**
> 
though, I still can't get the initial frustrations off my mind...

You can always make a voodoo doll marked with something like "Kernel Developer" or "X.org developer" :mrgreen:

---

### Post by foolsh on 2006-07-21
sounds like a regression to me the problem could be the kernel or it could be Xwindow system maybe both.
you could try somethings before storming off back to windows.
in your /etc/X11/xorg.conf file there is a section for configured mice, in that section it specifies what device to use i.e. "/dev/input/mice" try selecting an old device pointer like "/dev/input/psaux" or "/dev/input/mouse" and saving the file. and restart X.

its maybe worth a shot
best of luck a computer without a mouse is like a playstation without a controller

---

