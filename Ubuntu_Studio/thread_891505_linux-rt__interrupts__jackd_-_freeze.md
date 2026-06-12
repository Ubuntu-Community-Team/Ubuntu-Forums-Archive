---
title: "linux-rt / interrupts / jackd - freeze"
date: 2008-08-16
forum: Ubuntu Studio
---

### Post by bbkz on 2008-08-16
Hello i assembled a new pc with:

[INDENT]- intel core 2 quad 2,5
- 4gb ram
- evga nforce 780i (mainboard)
- m-audio delta 44[/INDENT]

i have a problem, the mouse and keyboard freezes after a while i let jackd running. on qjackctl i see it still runs and changes the value of the cpu % . i dont' know if other parts of the system are unavailable as well, maybe the harddrives, from which i have 2 sata.

first i have tried with ubuntu hardy 32bit with linux-rt where i had similar problems. i have tried to install the 64bit versions of ubuntu and ubuntu studio as well but i have there also the misteryous "black screen" problem, this i did only to check out if it solves my problem ;)

now i have ubuntu studio 32bit installed.

[INDENT]/etc/security/limits.conf:

```
@audio - rtprio 99
@audio - memlock 2000000
@audio - nice -10
```[/INDENT]

i also tried with rtprio 95 and 98, memlock 250000 and 512000 and nice -19. but this didn't help any.

in qjackd i have activated:
[INDENT]
- rt priority = 70
- force 16bit (also tried whitout)
- monitor (also tried without)
- hw-monitor (also tried without)
- realtime (also tried without)[/INDENT]


the error occurs after a while running jackd and there is no application running using jackd (as far as there is no backgroud task, doing so; it's a fresh installation).

it seems that the keyboard and mouse interrupts are not accepted anymore.

the problem is i will have to finish this pc till end of the weekend, so i'll try till tomorrow and after this i will install windows as i did before. (helpless me i tried since 5 years to use linux, but i never really achieved it.)

i hope someone can help me sort out this problem, other wise i'll keep you informed what i did after this weekend.

ps.: sorry for my bad english it's not my mainlanguage. And i forgot to say i have done the following related to the post [http://ubuntuforums.org/showthread.php?p=5600059](http://ubuntuforums.org/showthread.php?p=5600059) :
[INDENT]
- "sudo swapon -s" if there is something more or less then one swap partition, then fix it, as it gives freezing issues.

- edit /etc/gamin/gaminrc and put there "fsset nfs poll 10" "fsset ext3 poll 10" "fsset vfat poll 10". Gamin server is a program that reads frequently hard drive for new changes and in some situations it may cause freezes.[/INDENT]

---

### Post by thorgal on 2008-08-17
first thing to check from a terminal :

cat /proc/interrupts

see if your soundcard shares its IRQ with something else (video card, network chip, USB controller, whatever).

Your soundcard should have its own IRQ. 

second thing : IRQ thread priority. Get hold of a script called rtirq and make sure the audio IRQ thread has a priority over less important stuff. Google rtirq to know more about it.

---

