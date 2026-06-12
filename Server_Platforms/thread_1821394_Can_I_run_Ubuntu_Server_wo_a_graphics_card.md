---
title: "Can I run Ubuntu Server w/o a graphics card?"
date: 2011-08-09
forum: Server Platforms
---

### Post by shaggy999 on 2011-08-09
Hello,

I am looking to upgrade away from my desktop computer and I was considering re-using the system I have as the base for a home server using Ubuntu Server. The only problem is my motherboard does not have onboard video and I am currently using an 8800GTX installed in there. I really don't want to use the 8800GTX in the server because I'm going to leave this server on all the time and that would be a big waste of electricity for a major graphics card that won't even be used.

So what I was wondering is if I could just have the graphics card plugged in while installing the OS and then take it out afterwards? If not, it seems my only options are to re-use this board, but get a cheap graphics card to install into it or buy a brand new motherboard w/ onboard graphics.

For reference, the motherboard I'm using is the Gigabyte EP45-UD3R w/ an Intel Q6600.

---

### Post by sikander3786 on 2011-08-09
Not really!

The real question is can you run your 'computer' without a graphics card regardless of the OS? It might not POST, it might stop even before loading the Bios thus the OS can't be loaded regardless if it is Ubuntu Server or something else.

I haven't seen anything like this but you might want to refer to your PC's documentation. As soon as you take out the graphics card, you might not be able to power it on. Just test yourself, are there any beeps?

---

### Post by shaggy999 on 2011-08-09
Yeah, I was wondering about that. In my manual it says this:

> Halt On
Allows you to determine whether the system will stop for an error during the POST.
[B]No Errors
The system boot will not stop for any error.[/B]
All Errors
Whenever the BIOS detects a non-fatal error the system boot will stop.
All, But Keyboard The system boot will not stop for a keyboard error but stop for all other
errors. (Default)
All, But Diskette
The system boot will not stop for a floppy disk drive error but stop for all
other errors.
All, But Disk/Key The system boot will not stop for a keyboard or a floppy disk drive error but
it will stop for all other errors.


I assume that means it will continue on, but that's just an assumption.

---

### Post by sikander3786 on 2011-08-09
Hmmm. Still not sure if the same applies to Graphics Card as well. The only method of testing it would be to install Ubuntu Server, take out the graphics card and try finding your Server over the network.

We are making too many assumptions I believe. Might be there is someone who has already tried to achieve this?

---

### Post by Grenage on 2011-08-09
> **shaggy999 said:**
> Hello,

I am looking to upgrade away from my desktop computer and I was considering re-using the system I have as the base for a home server using Ubuntu Server. The only problem is my motherboard does not have onboard video and I am currently using an 8800GTX installed in there. I really don't want to use the 8800GTX in the server because I'm going to leave this server on all the time and that would be a big waste of electricity for a major graphics card that won't even be used.

So what I was wondering is if I could just have the graphics card plugged in while installing the OS and then take it out afterwards? If not, it seems my only options are to re-use this board, but get a cheap graphics card to install into it or buy a brand new motherboard w/ onboard graphics.

For reference, the motherboard I'm using is the Gigabyte EP45-UD3R w/ an Intel Q6600.

I don't see why not; try it to make sure, but I can't see why it shouldn't work.

---

### Post by Wim Sturkenboom on 2011-08-09
See [http://ubuntuforums.org/showthread.php?t=1815352](http://ubuntuforums.org/showthread.php?t=1815352) from about a week ago. That OP never reported back.

I agree that you should simply try it ;)

---

### Post by ingeva on 2011-08-09
> **shaggy999 said:**
> Yeah, I was wondering about that. In my manual it says this:...
I assume that means it will continue on, but that's just an assumption.As said before, you should try.
However, it shouldn't be too hard to find an old VGA card that you can put in there. That would also allow you to connect a screen (character mode is all that's needed) in case you want to log in and do something.

I just threw away several old cheap graphic cards some time ago .... some of them even with ISA plug .... :)  (Computers don't have ISA plugs any more).

---

### Post by tekknoir on 2011-08-09
You can get nvidia GT 210 for like $20 and it has around 30 TDW.  see comparaative specs for 200 and 400 series on wiki pedia.

---

### Post by garfonzo on 2011-08-09
Go to a local computer shop and pick up an old VGA card. You can probably "rescue" one from their scrap heap. I did this the other day and was given 3 crads -- all of which worked and all for free.

---

### Post by arrrghhh on 2011-08-09
> **ingeva said:**
> As said before, you should try.
However, it shouldn't be too hard to find an old VGA card that you can put in there. That would also allow you to connect a screen (character mode is all that's needed) in case you want to log in and do something.

I just threw away several old cheap graphic cards some time ago .... some of them even with ISA plug .... :)  (Computers don't have ISA plugs any more).

Here, here OP, try it!

You'd need the video card for the initial setup, but perhaps once you get past that you wouldn't need it.  If the machine will get past POST and boot, you don't really need a video card per se... But if for any reason you have to troubleshoot the machine you'll have to put that vid card back in it...

Assuming you can accept that risk, I say go for it.  If it doesn't POST/finish booting without a vid card, like others said above - one can be had for very little money.

---

### Post by stefangr1 on 2011-08-09
Also, you may want to add nomodeset to the grub options, and for obvious reasons you should remove splash from there as well :).

I think there is no inherent reason why it should not work withou video, but at the same time it may fail for many different reasons.

---

### Post by shaggy999 on 2011-08-09
I will try this this weekend and report back. I'll have to find a spare hard drive to install to, as I'm not ready to wipe my system yet (I need to build my new computer first! :D)

---

