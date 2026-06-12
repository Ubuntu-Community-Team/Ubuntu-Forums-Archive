---
title: "Security Compromise"
date: 2011-05-13
forum: Security
---

### Post by DeathByLinux on 2011-05-13
Hey guys, 
              I recently figured out how to install a game that I loved as a child and came upon on the internet. It's called Command and Conquer: Red Alert. 
Anyway, it's hard enough running this game in XP, let alone Ubuntu, but I found a set of instructions on how to do this, thanks to this article:
[http://spod.cx/blog/red_alert_wine_ubuntu_hardy_heron.shtml](http://spod.cx/blog/red_alert_wine_ubuntu_hardy_heron.shtml)
I managed to install the game, but running the thing is kind of a tricky maneuver. 
You don't have to read the installing instructions, just the ones under the **RUN** section. He states that there are some security compromises involved in trying to run this thing. I decided to consult someone before proceeding. 
Can someone give me an opinion on this? Here are some things that come to my mind:
Should I do this in order to run the game? Is the compromise as minor as he says it is? Is there another way?
Thanks for reading.
-DeathbyLinux

---

### Post by DeathByLinux on 2011-05-13
No ideas? :(

---

### Post by yetiman64 on 2011-05-14
> ```
sudo sysctl -w vm.mmap_min_addr=0
``` To reset it once you've finished playing:
  ```
sudo sysctl -w vm.mmap_min_addr=65536
```Please note I have added the code boxes above to clarify what are the commands from the website you linked to.

If you follow the instructions from the site you link to and run the *_first command before playing_* and the _*second command after playing*_ in a terminal you should be alright.

On recent versions of Ubuntu the lower address block used by the game is no longer available (to block ***_possible_*** security compromises to the system).

*_Just do not forget to run the second command_* when you have finished playing or you can leave your system open to compromise.

I had to use these commands a while back while using the dosemu program. Had the same issue as you are seeing with this game, Ubuntus tight security vs the memory needs of older game code.

Edit: just spotted the guide is for Hardy Heron, lol, not sure if the instructions there will work on later systems, please let us know what you are release you are trying this on and how it works out, thanks. Though being on wine it may not matter.

---

### Post by DeathByLinux on 2011-05-14
I am using Maverick Meerkat 10.10. (I don't really like the feel of 11.04.)
The instructions have worked beautifully, so far. I just decided to stop when I read "doesn't have too much of an impact on the security of your computer." 

**Yetiman64**, I had a question. I am pretty ignorant as to what is being done, here. Can you try and explain what is being changed and how it affects the security of my computer?

-DeathbyLinux

---

### Post by yetiman64 on 2011-05-14
Old security bulletin [[COLOR=Blue]--Ubuntu Security Notice USN-819-1--[/COLOR]]("http://www.ubuntu.com/usn/usn-819-1/") 

> Tavis Ormandy and Julien Tinnes discovered that Linux did not correctly
initialize certain socket operation function pointers.  A local attacker
could exploit this to gain root privileges.  By default, Ubuntu 8.04
and later with a **non-zero** /proc/sys/vm/**mmap_min_addr** setting were **not**
vulnerable.However the fixing of the vulnerability affects some games/programs that use addresses below that of what was fixed by setting mmap_min_addr to 65536 (64K).

A temporary solution is to set the value to 0, then after completing using the game/program reset the variable to its standard value of 65536.

If at any time you want to check the value to ensure you have set it correctly use,

```
sysctl -a | grep vm.mmap_min_addr
``` You will get a few errors on other keys but the value you need to see will be visible.

I don't fully understand the use of "socket operation function pointers", just that the problem was fixed years ago but still causes problems with the functioning of some wine games and in my case dosemu. 

Beyond that for a fuller description then maybe this should be in security discussions (I'll ask a moderator to consider a move). yetiman64

---

### Post by howefield on 2011-05-14
Thread moved to "*Security Discussions*".

You might get better help in here.

---

### Post by DeathByLinux on 2011-05-14
Thanks Yetiman64. I don't really need any more discussion on this beyond the help I have already received. I just wanted to make sure that I wasn't doing something really dumb and just wanted the communal opinion. 
Seems safe enough to do, as long as I reset the thing everytime.
Thanks guys!
-DeathbyLinux

---

### Post by JKyleOKC on 2011-05-15
Here's a bit of an overview on the whole area: From the very earliest days of personal computers, the "low memory" region (with addresses nearest to zero) has contained critical system data that, if modified, can give an intruder essentially unlimited power. The "socket pointers" referenced in earlier replies are just part of that data.

To prevent problems, some three years ago the kernel got code to prevent any process except the kernel itself from modifying that low memory area. However, to permit troubleshooting, that code included ways to remove the block when necessary.

The commands offered to make running the game possible use those ways to remove the block, and to replace it.

For maximum security you might want to shut down your internet connection and physically unplug its cable while playing the game, but this is probably overkill.

Hope this helps!

---

