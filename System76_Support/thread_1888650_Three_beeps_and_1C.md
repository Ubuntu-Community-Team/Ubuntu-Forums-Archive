---
title: "Three beeps and 1C"
date: 2011-11-29
forum: System76 Support
---

### Post by lordbah on 2011-11-29
Leopard Extreme desktop, on poweron it emits 3 beeps and the LCD shows 1C. I can't get past this. I have sent mail to support but if someone here can get me back up and running quicker, great! Do we know the meaning of the beep codes or the LCD codes?

I don't see any dust in there at all. The memory cards seem to be properly seated. It was running, but with "flaky" errors like Chrome bombing on a page and then a reload drawing it okay, Banshee and Miro bombing on startup, so I decided to reboot to see if that would make the problems go away. Instead I got a message about an unsuccessful POST attempt. No entries in the BIOS Event Log though. Disabled boot from everything but hard disk, told it to Exit Saving Changes, and since then it doesn't get past the 3 beeps - not even a prompt about going to the BIOS.

---

### Post by bluexrider on 2011-11-29
sounds like a 64K RAM failure. Just my guess.

Try to re-seat the processor

-----------------------------------------

edit post info
[http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

---

### Post by lordbah on 2011-11-29
Presumably the processor is inside that huge metal case which says "Intel". Hey, I haven't gone near one since the 68000. There's a switch on that which says "Q" and "P", any idea what that's for? Anyway I see 4 Philips on the "feet" of this beast and one in the center, but I can't really see the underside of it - is there some kind of socket it plugs into? Do I just unscrew the screws and pull?

PS: One new result to report. One time it did not beep, but the screen remained black, and the LCD said "bF".

---

### Post by bluexrider on 2011-11-29
First thing!!! if your machine has any warranty left then let them take care of it otherwise you might VOID it.

Second. I am NOT an expert. Just experienced because of similar issues.

If its not getting past POST its usually a hardware issue, again refer to First thing. 
 

Have you re-seated the memory sticks, unplugged and reconnected the electrical connections? This would probably be the thing I would do.  

If you don't have it here is the number for support:

Our representatives are available to take questions and comments by  phone between 8:00 a.m. and 5:00 p.m. Mountain Time, Mon-Fri. You can  reach us at 888-468-6482.

---

### Post by lordbah on 2011-11-30
I did reseat all of the memory sticks, no change. Haven't unplugged anything else yet.

I found out the "Q" and "P" have to do with the speed of the fan on the processor. "Q" for quieter but not as cool, "P" for ... well I don't know, but the opposite, cool but not quiet. Also it's not just a toggle switch, it's variable. Anyway it seems irrelevant here.

---

### Post by bluexrider on 2011-11-30
I think I would then be on the phone.

---

### Post by lordbah on 2011-11-30
Finally got a reply to my email. Suspects memory issue, says to run memtest when I see the grub menu. He loses points for reading comprehension there, as I said in the email the system is beeping within 3 seconds of poweron and I never see anything at all on the screen, so I can't run memtest. He also suggested removing pairs of memory cards to see if the problem can be narrowed down that way, and I will try that when I get home. He ignored my inquiry about the 1C - don't we have any reference for those LCD codes?

---

### Post by bluexrider on 2011-11-30
Not sure of any LCD codes. I would expect that because the monitor is not receiving burst signals that it displays a code. If you have another computer to hook the monitor to it would confirm it to be good or bad.

I think its a memory stick issue or the socket. Follow the instruction given in the e-mail for testing.

---

### Post by lordbah on 2011-11-30
Looks like one bad memory card. There are 6 cards and any combination of 4 boots, unless this one card is in the mix. Never had one go bad in the first 5 weeks before.

---

### Post by bluexrider on 2011-12-01
> **lordbah said:**
> Looks like one bad memory card. There are 6 cards and any combination of 4 boots, unless this one card is in the mix. Never had one go bad in the first 5 weeks before.

So are we talking about your machine being able to boot again? Are you getting some new memory?

---

### Post by lordbah on 2011-12-01
Yes the machine boots (with 4 cards instead of 6, i.e. 2/3 the usual memory). Yes I will be getting a replacement card, just received the email to begin the advanced replacement a little while ago.

---

### Post by isantop on 2011-12-01
Three beeps indicates a memory failure. If you've narrowed down a particular card as being bad.

I do apologize for him having ignored the bit about 1C. That diagnostic code indicates some sort of processor failure, but that could be the memory. Since we've confirmed that that is bad, we'll replace that and then see about the processor.

---

### Post by bluexrider on 2011-12-01
I think we had reasoned it was a memory issue. i am sure that the OP thanks you for the follow up.

happy *buntu 

please mark this (Solved)

---

### Post by lordbah on 2011-12-11
I sent in the form for the replacement and haven't heard a thing since. After a few days I emailed (I don't do telephone) asking him to verify he received the forms - no reply. After a couple of days I pinged again. And again each day for the rest of the week. I don't see anything in my mail server logs to indicate that I'm discarding mail from system76 or marking it as spam. Is this a one-man operation and he went on vacation or something?

---

### Post by lordbah on 2011-12-26
I got a reply on the 15th saying "I'll look into it in the morning", and nothing more since then. Am I the only one to have a poor experience with this company?

---

### Post by bk7777` on 2012-01-01
All I will say is no you are not the only one having poor customer service / issues with Leopard..

I just submitted a long 18 month review on the thread named "[Please share your experiences with System76]("http://ubuntuforums.org/showthread.php?t=343798&highlight=Leopard+Extreme")" if you are interested.

Brian

---

### Post by lordbah on 2012-01-04
Finally received the replacement memory and it appears to be working. They didn't provide any information or materials on returning the defective memory, and haven't promptly answered my question about it, so I'll just forget about it and consider the case, at long last, closed.

---

### Post by mcpetersen.dsm on 2012-02-05
I have the same problem that occurred with a 6-week-olld Leopard. My email to System76 produced a turnaround in less than a day. The advice was the same as above: pull the memory and check it to find which stick was responsible. That worked, and I've requested info on replacing the bad RAM. Will post again with the outcome.

22 Feb 2012: A response of System76 requested information about my machine (order #, serial #, etc). The replacement memory stick arrived a few days later, and all has been well since.

---

