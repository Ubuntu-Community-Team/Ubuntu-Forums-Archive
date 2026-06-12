---
title: "Assisted computer suicide"
date: 2007-08-10
forum: The Cafe
---

### Post by hackle577 on 2007-08-10
[COLOR="Red"]DISCLAIMER: PLEASE DO NOT ACTUALLY TRY RUNNING THE COMMAND, YOU WILL ERASE EVERYTHING ON YOUR HARD DRIVE!!! YOU HAVE BEEN WARNED[/COLOR]

I got a new computer a few days ago from the IT company where I work, so for a few days I've been in the process of transferring all my data over. I just finished last night. My old laptop was, by that time, an empty shell of a computer. It was too crappy to sell and had caused me too much pain over the years for me to let it live now. (OK, so I'm a bit evil too...) 

I decided to run "sudo rm -rf /" in terminal and see what would happen. After triple-checking that I had removed everything I needed, I opened a terminal and typed in the command. Believe it or not, my heart rate was a little higher than normal. Would my laptop explode in my face?

It asked me for my password. I typed it in and hit Enter. "Sorry, incorrect password. Try again." After typing it in correctly, I hit Enter again. Oh boy.

The first thing that happened was my desktop background disappeared. Pretty soon after that, customizations started vanishing (my fonts, theme, etc.) and the screen flashed a few times. Some errors were appearing in th terminal about how some files couldn't be deleted because they were in use. Bah.

I tried clicking on some stuff but nothing happened. I couldn't even get to the terminal again. I did Ctrl-Alt-Backspace and the screen went blank, but the computer was still running. A bunch of garbled text appeared but went away a few seconds later. I held the power button down until it shut off.

Trying to power back up, GRUB halted with Error 15. I don't know what this is, but I'm guessing it's something like "You are totally screwed." I guess to *really* get it to work I should have used a LiveCD, but it was kinda fun to see a computer self-destruct like that.

In other news, I just graduated from Kevorkian University.

---

### Post by original_jamingrit on 2007-08-10
I've done that before, while I was still learning how to use rm.  I call it the super-lightweight version of Ubuntu.

---

### Post by Circus-Killer on 2007-08-10
heh, us geeks have a strange form of cruel amusement. ;)

i rate when i upgrade to gutsy (which i always upgrade with a fresh install), ill give it a bash, sounds fun :popcorn:

---

### Post by Evil Blu Jedi on 2007-08-12
I'm bored and have an old box with Ubuntu Feisty on it.  I think I'll try this command and try another flavor of Ubuntu on the box.

---

### Post by goumples on 2007-08-12
In hardware class when we were in the troubleshooting phase, we partnered up and sabotaged each others machines and then would try to discover what was wrong.  We were using win 2k boxes to do this.  So I opened regedit and started deleting random registry files.. I finally popped the right one and it crashed.. The instructor said that, total destruction of the OS wasnt the point of the exercise but ehhh... it was funny as hell watching this other guy turn on his PC and it crashed immediately during boot.

---

### Post by Dr. C on 2007-08-12
When I see the command "sudo rm -rf /"  my thoughts come to installing Cygwin on Windows Vista and then trying it to see what Vista would do.

---

### Post by Evil Blu Jedi on 2007-08-12
It worked, Error 15 with GRUB.  Now if only I had a free computer with Windows that I could do that too.....

---

### Post by @trophy on 2007-08-12
Yes, but "rm -rf /" is just... so... cliché.  It's been done.  What are some OTHER ways you could assist your computer's suicide?

We'll count anything that prevents you from using your computer at all.  The first thing I could come up with is setting the default run-level to 6 or 0.

What's everyone else got?

---

### Post by heimo on 2007-08-12
> **@trophy said:**
> What's everyone else got?

I think it should somehow involve Doom.
[http://www.cs.unm.edu/~dlchao/flake/doom/](http://www.cs.unm.edu/~dlchao/flake/doom/)

---

### Post by ThinkBuntu on 2007-08-12
# mv -rf /usr /mnt/sda1

Maybe? Assume /mnt/sda1 is an iPod or something. I guess it would crap out when /bin/rm was moved though, although the process may prevent it because it's running.

Then proceed to

# mv -rf /bin /mnt/sda1 && rm -rf /sbin/sda1

---

### Post by celsofaf on 2007-08-12
> **@trophy said:**
> Yes, but "rm -rf /" is just... so... cliché.  It's been 
We'll count anything that prevents you from using your computer at all.  The first thing I could come up with is setting the default run-level to 6 or 0.

What could happen then? :D

---

### Post by jgrabham on 2007-08-12
> **goumples said:**
> In hardware class when we were in the troubleshooting phase, we partnered up and sabotaged each others machines and then would try to discover what was wrong.  We were using win 2k boxes to do this.  So I opened regedit and started deleting random registry files.. I finally popped the right one and it crashed.. The instructor said that, total destruction of the OS wasnt the point of the exercise but ehhh... it was funny as hell watching this other guy turn on his PC and it crashed immediately during boot.

restart in DOS mode and delete config.sys :D

---

### Post by insane_alien on 2007-08-12
you could always write a big string of zeros to the drive. or randomness from /dev/random

---

### Post by Tuna-Fish on 2007-08-12
how about sudo dd </dev/null >/dev/hda?

---

### Post by @trophy on 2007-08-12
> **celsofaf said:**
> What could happen then? :D

Well in the run levels, 0 means off and 6 means reboot, so theoretically the computer would either turn itself off immediately after GRUB loaded the OS, or reboot itself over and over.  I've never tried it though so I don't know if it'd work or not.

---

### Post by init1 on 2007-08-13
> **@trophy said:**
> Yes, but "rm -rf /" is just... so... cliché.  It's been done.  What are some OTHER ways you could assist your computer's suicide?

We'll count anything that prevents you from using your computer at all.  The first thing I could come up with is setting the default run-level to 6 or 0.

What's everyone else got?
Install Windows. 
cat /bin/*>/dev/dsp
It doesn't actually harm anything, but it sounds like something bad is happening :D

---

### Post by init1 on 2007-08-13
> **Tuna-Fish said:**
> how about sudo dd </dev/null >/dev/hda?
Wouldn't you do a
dd if=/dev/null of=/dev/hda 
instead? Or do they do the same thing?

---

### Post by heimo on 2007-08-13
> **init1 said:**
> cat /bin/*>/dev/dsp
It doesn't actually harm anything, but it sounds like something bad is happening :D

Hmm... to modify this to be actually destructive... one could pipe output from microphone to program which would then OR it with contents of hard disk. "Shh! Everybody quiet!"

---

### Post by BOBSONATOR on 2007-08-13
I rember once someone asked for help in the ubuntu irc channel, and someone replied with the command rm -rf /" and im pretty sure he did it..

---

### Post by init1 on 2007-08-13
> **BOBSONATOR said:**
> I rember once someone asked for help in the ubuntu irc channel, and someone replied with the command rm -rf /" and im pretty sure he did it..
Maybe I should put that in my signature: 
WHATEVER YOU DO, DON'T DO THIS! ```
rm -rf /
``` :twisted:

---

### Post by kozy6871 on 2007-08-13
How about taking the magnet from a sub-woofer and sticking it to the HD?

---

### Post by @trophy on 2007-08-13
How about mapping /dev/null to somewhere important like /boot or something?

Once the garbage starts flowing in and the partition filled up, would anything bad happen or not?

---

### Post by Rhubarb on 2007-08-13
You could install linux genuine advantage
[http://www.linuxgenuineadvantage.org/](http://www.linuxgenuineadvantage.org/)

If you don't remove it after 30 days, you won't be able to login to your computer.  (Yes, you can still revive it by going into single user mode - so it's more of a computer suicide attempt).

---

### Post by goumples on 2007-08-13
> You could install linux genuine advantage
[http://www.linuxgenuineadvantage.org/](http://www.linuxgenuineadvantage.org/)

That's some funny mess.

---

