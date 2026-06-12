---
title: "Kernel 3.8 to drop I386 support. Is that a problem for you."
date: 2012-12-14
forum: The Cafe
---

### Post by rrnbtter on 2012-12-14
Greetings,
Linux kernel 3.8 will probably drop I386 support. I like where Linux is going and don't have anything that old. Just curious as to your opinion on this matter.
rrnbtter

---

### Post by tgalati4 on 2012-12-14
It depends on what packages get broken because they rely on i386 libraries, regardless of what hardware is installed.  Also, embedded systems use 386 processors, so if you want to develop and compile in a native 386 environment, that will be more difficult if i386 is dropped.

But I don't have any 386 machines so I don't really care, but there are some that do and may want to keep support.  What are the gains to the 3.8 kernel by dropping such support?  Is it just kernel size?  Or are there real performance gains by dropping legacy code?

---

### Post by pqwoerituytrueiwoq on 2012-12-14
if we cant use the 32bit libraries ia32-libs, there goes wine,  google earth, team viewer (custom wine build), and netflix (since it run on a custom wine build)

---

### Post by rrnbtter on 2012-12-14
Greetings,
My understanding of the information is that it is the I386 HW architecture support that is being dropped. I don't think that interpolates to 32 bit libraries. I don't really know what the linux community is running 12.10 on but I doubt that it is a 386. I do know that there is still a lot of 486 hardware still running, especially in the corporate world.  That is to remain. While back I installed a copy of MS-DOS on my 686 but I couldn't do much with it. So it doesn't matter to me that Windows 7 or XP doesn't support 8086. I do know that there tends to be more hanger-on-ers in the Linux crowd that might want continued support.  Also, it seems to me as we move forward the newer Ubuntu Os's run faster on my same equipment, but of course there are limits to that. 
rrnbtter

---

### Post by smellyman on 2012-12-15
i386 is really really old at this point.

if you are still running i386 chances are you are not, nor should you be, running a current kernel.

---

### Post by HibyPrime on 2012-12-15
I think there's some confusion here, they're dropping support for the 386 processor, not the architecture we refer to as i386.

This isn't a dropping of 32-bit (think of what would happen to all the ARM devices out there running on linux), just the old processor.

---

### Post by haqking on 2012-12-15
> **HibyPrime said:**
> I think there's some confusion here, they're dropping support for the 386 processor, not the architecture we refer to as i386.

This isn't a dropping of 32-bit (think of what would happen to all the ARM devices out there running on linux), just the old processor.

nostalgic really, Linux was conceived on a 386 but to quote Linus > [I'm not sentimental. Good riddance]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git&a=commitdiff&h=743aa456c1834f76982af44e8b71d1a0b2a82e21") LOL[]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git&a=commitdiff&h=743aa456c1834f76982af44e8b71d1a0b2a82e21")

---

### Post by mips on 2012-12-15
I doubt much will run on i386. I don't really see a need to support anything below i686.

---

### Post by mastablasta on 2012-12-15
i used to have a 8086 or something like that CPU (i think it was z-80), then 286 12Mhz (turbo). and craved for 386. never got it. but by the time i managed to get some savings and persuade parents it's time to go with the flow i got a 486. which at the time was almost top of the line (p90 was a little bit better). i still lhave the 486 with win95 installed.

so as long as they still suport 486... :-P

---

