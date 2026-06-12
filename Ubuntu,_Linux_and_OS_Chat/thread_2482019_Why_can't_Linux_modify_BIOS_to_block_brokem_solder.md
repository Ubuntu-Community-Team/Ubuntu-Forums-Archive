---
title: "Why can't Linux modify BIOS to block brokem soldered RAM on a Thinkpad?"
date: 2022-12-16
forum: Ubuntu, Linux and OS Chat
---

### Post by smith73 on 2022-12-16
I was planning to buy a Lenovo Thinkpad E14 gen2 with amd ryzen 3 and now see that it may have at least 8 GB RAM soldered and 8 GB inserted.
If the soldered RAM is broken than the whole board needs replacement even if the inserted RAM is ok, which is so idiotic.

I heard Linux is best at dealing with hardware, why can't it modify laptop's BIOS to block broken soldered RAM and use the inserted one?
What are fundamental limitations in Linux that it can't modify BIOS in this way?

---

### Post by Tadaen_Sylvermane on 2022-12-16
That's not the bios. All the bios/efi is a very low level operating system that is flashed into the machine. You would need to flash a new one. You can't just change it on the fly. That and the ram amount isn't controlled from the bios / efi most likely. It's hard wired so to speak. You might be able to destroy the traces on the board or something. But that comes with it's own risks obviously.

Blame soldered RAM. Not linux for this problem. In their quest for money / control hardware companies will make you buy a new one instead of being able to fix the old one. And they save money building it in the first place. Win win for them.

---

### Post by smith73 on 2022-12-16
Here [1] someone actually could upgrade the soldered RAM on a Dell XPS13, but seems like lots of hustle.

[[1]("https://hackaday.com/2021/11/24/you-cant-upgrade-soldered-on-laptop-ram-think-again/")["]]]("https://hackaday.com/2021/11/24/you-cant-upgrade-soldered-on-laptop-ram-think-again/)

And on Quora someone also mentioned that:
"Also,  in the case of something like the Apple M1, where it&#8217;s soldered  directly to the chip, it&#8217;s probably easier to make it run fast, since  the impedance and everything is much better with a short solder joint  compared to long copper traces and sockets and what not, all of which  have parasitic effects that degrade the signals."
Though I'd wonder how much noticable performance or anything such soldering actually adds.

I do not think that RAM soldering is an essential big win. It seems the same type of win as with plastic waste.
This is the attitude due to which there aren't any essential breakthroughs in current human civilization.

But someone could start a startup to manufacture more open-source like renewable hardware laptops, by the same token as Arduino or Raspberry Pi.

---

### Post by Tadaen_Sylvermane on 2022-12-16
I'm sorry I didn't mean that in a good way. They win by selling you a new one or fixing the old one when you pay them to. And they save money by not having to install removable ram slots. There is no positive for anyone other than the company. And most of them have no morals so for them they win multiple times.

Actual results from things they cause are left to the taxpayer... who they somehow stiff yet again by avoiding all kinds of taxes in various ways despite making hundreds of millions if not a few billion in profits every year. In the US anyhow.

---

### Post by smith73 on 2022-12-16
I didn't mean that in a "good" way either. Or do they actually perform 100% recycling of system boards with broken soldered RAMs?

I asked an acquaintance of an acquaintance in a local PC repair (a  rather mediocre one) shop regarding how many times they had to deal with  broken soldered RAMs in Thinkpads. He said sort of 0 with thinkpad's,  but 2 with ASUS (during their whole practice).

So now I am unsure whether to buy a new Lenovo Thinkpad E14 with AMD 3 but 8 GB soldered RAM or a used T480 with i5 8350U 4 cores and 16GB replaceable RAM.

---

### Post by #&amp;thj^% on 2022-12-16
> **smith73 said:**
> 
So now I am unsure whether to buy a new Lenovo Thinkpad E14 with AMD 3 but 8 GB soldered RAM or a used T480 with i5 8350U 4 cores and 16GB replaceable RAM.

Mine is a [X1 carbon]("https://www.amazon.ca/TOPSELLER-THINKPAD-X1-C6-I5/dp/B079J3NWYZ?th=1") was 8 gigs soldered RAM now 12 gigs soldered RAM, But if there is any warranty remaining on that system it will now be out of warranty. (something to consider)

---

### Post by smith73 on 2022-12-29
Here (1,2) there seems to be a possibility to make Ubuntu not to use "bad" RAM addresses.
Mine E14 new soldered and slotted RAM seems ok and I will take all possible measures to keep it away from risks of external damage,
so would like to ensure those measures in advance.

But I am curious how disabling "bad" RAM addresses in Ubuntu would work on a Win10/Ubuntu dual boot laptop, to make Windows 10
also ignore the "bad" RAM.

[1] [https://askubuntu.com/questions/1428808/can-i-disable-one-slot-of-ram](https://askubuntu.com/questions/1428808/can-i-disable-one-slot-of-ram)
[2] [https://askubuntu.com/questions/908925/how-do-i-tell-ubuntu-not-to-use-certain-memory-addresses](https://askubuntu.com/questions/908925/how-do-i-tell-ubuntu-not-to-use-certain-memory-addresses)

---

### Post by smith73 on 2023-01-08
In continuation of this [1] thread, I'd like to inquire about your experience with soldered RAM.
There is a new Lenovo ThinkPad E14 Gen2 (AMD) with 8GB soldered RAM.
Is soldered RAM reliable? How often have you encountered issues with soldered RAM, 
in what circumstances and how were they resolved?

[1] [https://ubuntuforums.org/showthread.php?t=2482019](https://ubuntuforums.org/showthread.php?t=2482019)

---

### Post by QIII on 2023-01-08
Threads merged

---

### Post by #&amp;thj^% on 2023-01-08
EDIT:> **smith73 said:**
> 
There is a new Lenovo ThinkPad E14 Gen2 (AMD) with 8GB soldered RAM.

If it's this one you mention there should be no worries (no soldered RAM). [https://www.lenovo.com/us/en/p/laptops/thinkpad/thinkpade/thinkpad-e14-gen2-(amd)/22tpe14e4a2?orgRef=https%253A%252F%252Fduckduckgo.com%252F](https://www.lenovo.com/us/en/p/laptops/thinkpad/thinkpade/thinkpad-e14-gen2-(amd)/22tpe14e4a2?orgRef=https%253A%252F%252Fduckduckgo.com%252F)

Really not sure the question was aimed at anyone, but my experience has been trouble free.
I may need to mention though the x1 carbon 7th gen was a pair, I sold the second one to a friend that I myself modified to the 12 Gigs per order, this was a couple of years back now.
I have not heard a peep from him, bought for his daughter for school. So if anything was a miss, I would of heard by now.
I wouldn't try this yourself though, unless your a confidant builder.

---

### Post by smith73 on 2023-01-08
I am a bit worried whether running some compute intensive machine learning etc tasks wouldn't damage the 8GB soldered RAM.
It has 8 gb slotted though and plenty of SSD for swap paging.

---

### Post by #&amp;thj^% on 2023-01-08
That would be a crap shoot, with out knowing what you would be running on it.
Don't miss-understand me here, I love AMD and own one:
```
Lenovo Legion 5 15ARH05
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1399 min/max: 1400/3000 cores: 1: 1400 2: 1400 3: 1400
    4: 1397 5: 1400 6: 1400 7: 1400 8: 1400 9: 1400 10: 1400 11: 1400 12: 1400

```
But I'm very disappointed on what it runs smoothly.**(freezing where intel just bangs on and on with 8Gigs ram)**
It's geared more to multimedia and gaming, I'm not a gamer.;) 
Moral, I'm happy I have both though, your mileage may vary>>IJDK

---

### Post by lammert-nijhof on 2023-01-08
Linux can block erroneous RAM, I've done it and you don't need the BIOS!!
I once did block say 100MB of erroneous RAM on a 4GB stick. I switched off the erroneous part of the RAM in /etc/default/grub, see the following lines in that file:

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

I used it too block the usage of say 100MB or erroneous RAM on an 4GB stick.  To find the erroneous RAM I did run the memory test from the boot menu first.  I noted the erroneous addresses and added them to the GRUB_BADRAM entry. You might need to combine many small areas into one bigger area. I think I remember, it must be specified as address, length, address, length, address, length etc etc. All hexadecimal of course.
Afterwards the OS will avoid to use those memory locations :)

---

