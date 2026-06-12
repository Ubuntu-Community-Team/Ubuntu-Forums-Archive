---
title: "How do you code binary from ascii?"
date: 2006-08-11
forum: The Cafe
---

### Post by Roasted on 2006-08-11
I'm a little unsure of something. I thought I was doing this right, but after looking for a binary chart online and comparing what I got, I'm a little confused.

For example, the answer I get is 11 digits long. But binary is only supposed to be 8 digits long. My results seem to match up, except for the 3 extra 0's at the front. What am I doing wrong? Can anybody just give me a brief explanation of how to code binary? I'm well aware of the chart you're supposed to use, 1024 512 256 128 64 32 16 8 4 2 1, so if you could just briefly explain it that'd be great. Thanks!

---

### Post by VirtuAlex on 2006-08-11
What are you talking about? Can you give an example of what are you doing and then maybe we could see what are you doing wrong?

---

### Post by MrHorus on 2006-08-11
> **Roasted said:**
> For example, the answer I get is 11 digits long. But binary is only supposed to be 8 digits long. 

Not *quite* true...

A Bit (or Binary Digit) is a 1 or a 0.

A Byte is comprised of 8 bits.

Remember that not everything in the world will fit neatly into little 8bit packages and without knowing what language you are programming and what you are trying to do, it's hard to explain where the leading 0's are coming from.

---

### Post by slimdog360 on 2006-08-11
> **Roasted said:**
> Can anybody just give me a brief explanation of how to code binary?

wow, I think your asking a bit much there. Youd have to pick up a text book on the subject. I couldnt see any reason in the world why you would have to code something in binary. Try learning assembly code or c programming.
maybe someone can come up with a good answer for you but it aint coming from me, hehe.

---

### Post by Roasted on 2006-08-11
It's for a class. We're supposed to code a few words into binary and turn it in, then we'll be tested on it, etc.

I was just told to find the ASCII number in this handout we got. So for example, capital J's ASCII is 74. So then I'd use that umber 74 to figure out the binary for capital J. Does this make sense? Can anyone make sense of ASCII number 74 and make it into binary?

---

### Post by VirtuAlex on 2006-08-11
It's 1001010

---

### Post by VirtuAlex on 2006-08-11
If it is still unclear you can do it by hands. Divide your number successively by 2 and collect reminders:
```
number - reminder
    74 - 0
    37 - 1
    18 - 0
     9 - 1
     4 - 0
     2 - 0
     1 - 1
     0 - 0
```
Now read it from bottom to top

---

### Post by VirtuAlex on 2006-08-11
And in case you need to check, open calculator in scientific mode, enter your number and click bin radio button...

---

### Post by Lord Illidan on 2006-08-11
There are also software calculators available for this task.

---

### Post by VirtuAlex on 2006-08-11
> **Lord Illidan said:**
> There are also software calculators available for this task.
I was talking about software calculator. It is free and available on any platform. The only thing that the default mode is not scientific, so you have to switch.

---

