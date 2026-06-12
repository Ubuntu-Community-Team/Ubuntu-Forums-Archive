---
title: "Math Question Help"
date: 2008-04-22
forum: The Cafe
---

### Post by JohnSearle on 2008-04-22
Hello,

Having an issue with a math question that my girlfriend is doing...

The question is as follows:

You have four balls in a box, one of them is red, the others are not. You remove the first ball, it is not red, you discard it. What are the chances that you'll pick the right ball the second time?

The answer is the following:

1/4 * **3/3** + 3/4 * 1/3 = 1/2

I can explain the reasoning behind everything except the 3/3. My intuition is telling me that it's redundant, and just represents the probability of getting a non-red ball after the red ball is excluded. So technically it could be included in the second portion of the formula as well:

1/4 * **3/3** + 3/4 * 1/3 * **2/2** = 1/2

Is my assumption correct, and if not, what is correct?

EDIT: I didn't make this clear. You are tasked with choosing the red ball out of a box, and you cannot see the balls. You choose the first ball, and it is not red, you discard it. Given that there are three balls left, one of them being red, what are the chances that you'll choose the red ball?

Thanks,

- John

---

### Post by acelin on 2008-04-22
Well 3/3 is 1- it tis redundancy.

---

### Post by Sporkman on 2008-04-22
The second time there is one red ball & two non-red balls.

The chance you'll pick the red ball is 1/3.

---

### Post by SomeGuyDude on 2008-04-22
> **Sporkman said:**
> The second time there is one red ball & two non-red balls.

The chance you'll pick the red ball is 1/3.

Yeah, it's kinda simple. Four balls, one is red. Three balls, one is red.

---

### Post by Barrucadu on 2008-04-22
As said, 3/3 = 1 and is so redundant. They could have put sqrt(4)/2 and the answer would be the same.

---

### Post by JohnSearle on 2008-04-22
> **acelin said:**
> Well 3/3 is 1- it tis redundancy.

Well my question really is: why is it there? 

It's filling out some portion of the formula, that's certain. It's not really redundant if it's representing something that needs to be represented, such as a certain algebraic placeholder that a student should know.

So what does the 3/3 represent?

Thanks for the response, BTW.

- John

---

### Post by trowerpower35 on 2008-04-22
The 3/3 doesn't belong.  There are 3 discrete events making up the event space (pull a red, pull not red, pull other not red).  The probability of any one of these happening is even so its 1/3.
So after looking at your equation it occured to me that maybe you were looking for probability of not pulling red first time and pulling red second ?
3/4*1/3=1/4

---

### Post by CouchMaster on 2008-04-22
The math is wrong to start with - it should be
(1/4 * 3/3 + 3/4) * 1/3 = 1/3
and yes it is redundant because you have
.25 * 1 + .75 * .3333 = 1/3 which equals
.25 + .75 * 1/3 = 1/3

---

### Post by JohnSearle on 2008-04-22
> **CouchMaster said:**
> The math is wrong to start with - it should be
(1/4 * 3/3 + 3/4) * 1/3 = 1/3
and yes it is redundant because you have
.25 * 1 + .75 * .3333 = 1/3 which equals
.25 + .75 * 1/3 = 1/3

I don't think the math is incorrect...

Probability of pulling the ball the first time (1/4), plus the probability of pulling the ball the second time (1/3), times the probability of not pulling the ball the first time (3/4).

1/4 + 1/3 * 3/4 = 1/2

That is verified with the answer sheet, and I've found a similar answer on some math forum.

- John

---

### Post by Barrucadu on 2008-04-22
The 3/3 is there to confuse you. It serves no purpose. It is multiplying by 1, which does not change the answer at all.

---

### Post by trowerpower35 on 2008-04-22
Yeah, that would be correct for pulling the red ball by the second round.  The way you worded question made it sound like you knew the ball was not getting pulled in the first round.

---

### Post by CouchMaster on 2008-04-22
You are right - one has a 25% of pulling the red ball the first time - a 50% chance the second - a 75% chance the third and 100% the fourth!

---

### Post by popch on 2008-04-22
> **JohnSearle said:**
> You have four balls in a box, one of them is red, the others are not. You remove the first ball, it is not red, you discard it. What are the chances that you'll pick the right ball the second time?

The answer is the following:

1/4 * **3/3** + 3/4 * 1/3 = 1/2

It pays to read the text very closely. From what's actually written, you can deduct:

- The 'right' ball is not red
- You can see the balls while picking, so you won't pick the red one (unless you are color blind, which your sister presumably won't be)

That's the only way I can see to have the text be consistent with p=.5.

Does this help?

---

### Post by JohnSearle on 2008-04-22
:lolflag:

My question was just **why** is the 3/3 in there? The professor put it in, so it *must* serve some purpose in a demonstrative way. :confused:

- John

---

