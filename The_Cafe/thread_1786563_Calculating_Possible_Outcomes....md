---
title: "Calculating Possible Outcomes..."
date: 2011-06-19
forum: The Cafe
---

### Post by kevin11951 on 2011-06-19
My math is a little crappy today:

If I create a 16 character phrase made up of the numbers 1 - 9 randomly selected, how many possible outcomes are there?

(BTW, I graduated HS 2 years ago, this is not homework ;))

---

### Post by JustinR on 2011-06-19
I believe it's 144.

123456789 = 9 possible combinations for each character.
9 * 16 characters total = 144.

I feel like I'm wrong for some reason, I learned this in HS too - but it doesn't really seem right.

Edit:
The posts below re correct.

---

### Post by Tibuda on 2011-06-19
9^16=1853020188851840

---

### Post by beew on 2011-06-19
9^16 (9 to the power 16). 

Imagine 16 slots, there are 9 choices for each slot so together there are 9x9x9...x9 (16 times) that many choices.

---

### Post by undecim on 2011-06-20
9^16=1,853,020,188,851,841, or about 1.8 quadrillion (1.8 million billion)

---

### Post by jerenept on 2011-06-20
> **kevin11951 said:**
> My math is a little crappy today:

If I create a 16 character phrase made up of the numbers 1 - 9 randomly selected, how many possible outcomes are there?

(BTW, I graduated HS 2 years ago, this is not homework ;))

16C9 or 11440
(Combinations)

---

### Post by beew on 2011-06-20
> **jerenept said:**
> 16C9 or 11440
(Combinations)

Wrong answer. This answers a different question instead of the OPs:

Imagine you have 9 boxes and 16 characters to choose from, how many ways can you fill up the boxes in such a way that 
1) no two boxes should have the same character.

2) order doesn't matter, so it doesn't matter which character goes to which box, if the same 9 characters are picked from the 16 you have made the same choice

---

### Post by jerenept on 2011-06-20
> **beew said:**
> Wrong answer. This answers a different question instead of the OPs:

Imagine you have 9 boxes and 16 characters to choose from, how many ways can you fill up the boxes in such a way that 
1) no two boxes should have the same character.

2) order doesn't matter, so it doesn't matter which character goes to which box, if the same 9 characters are picked from the 16 you have made the same choice

No, he has 16 boxes, and 9 characters to choose from.

---

### Post by beew on 2011-06-20
> **jerenept said:**
> No, he has 16 boxes, and 9 characters to choose from.

I know, that's why your answer is wrong. What I wrote in post 7 was the question for which your answer would have been correct and as you said, it is not the OP's question.

The correct solution to OP's question with explanation is in my post #4.

---

### Post by Legendary_Bibo on 2011-06-20
16!/9!

---

### Post by beew on 2011-06-20
> **Legendary_Bibo said:**
> 16!/9!

Also wrong. 

16!/9! is the number of 9-charcter words where there are 16 choices for each character and 1) no same character appears twice  2) order matters.

---

### Post by jerenept on 2011-06-20
> **beew said:**
> I know, that's why your answer is wrong. What I wrote in post 7 was the question for which your answer would have been correct and as you said, it is not the OP's question.

The correct solution to OP's question with explanation is in my post #4.

Ahh, I see... I mis-interpreted your post.

how do you explain the fact that 16^9 (according to your logic in post 4) is 68719476736, and not 11440 as I stated?

Also:[Combinations]("https://secure.wikimedia.org/wikipedia/en/wiki/Combination#Example_of_counting_combinations")

---

### Post by Grifulkin on 2011-06-20
> **beew said:**
> Also wrong. 

16!/9! is the number of 9-charcter words where there are 16 choices for each character and 1) no same character appears twice  2) order matters.
 
  9^16 , nothing saying they can't appear twice, that would be impossible, but yes order does matter.

EDIT: Jumped to the last post, you were correct way back when.  My apologies.

---

### Post by Legendary_Bibo on 2011-06-20
Well the only other solution I can think of is 9^16 = 1853020188851841

Repeating can't be an issue because you have more spaces than numbers, and in that case order doesn't either.

---

### Post by beew on 2011-06-20
> **jerenept said:**
> Ahh, I see... I mis-interpreted your post.

how do you explain the fact that 16^9 (according to your logic in post 4) is 68719476736, and not 11440 as I stated?

Also:[Combinations]("https://secure.wikimedia.org/wikipedia/en/wiki/Combination#Example_of_counting_combinations")

You said 16C9 which is 16!/(7!9!) and mine is 9^16, not 16^9.

Combination counts the number of subsets, order doesn't matter and no repeat allowed.

so 4C2is the number of subsets from a pool of 4 objects which has 2 items. Say how many 2 element subset can you get from {a, b, c, d}. It would be 4C2 =6. The subsets are {a, b}, {a, c}, {a, d}, (b, c}, {b, d}, {c, d}. Note that {a, b} and {b, a} are considered the same since order doesn't matter and things like {a, a} don't appear because no repetition allowed.

---

### Post by Grifulkin on 2011-06-20
> **beew said:**
> You said 16C9 which is 16!/(7!9!) and mine is 9^16, not 16^9.

Combination counts the number of subsets, order doesn't matter and no repeat allowed.

so 4C2is the number of subsets from a pool of 4 objects which has 2 items. Say how many 2 element subset can you get from {a, b, c, d}. It would be 4C2 =6. The subsets are {a, b}, {a, c}, {a, d}, (b, c}, {b, d}, {c, d}. Note that {a, b} and {b, a} are considered the same since order doesn't matter and things like {a, a} don't appear because no repetition allowed.
 
In other words pCq = p!/[(p-q)!(q!)] Order doesn't matter.

and pPq = p!/q!.  Order matters.

---

### Post by Legendary_Bibo on 2011-06-20
> **Grifulkin said:**
> In other words pCq = p!/[(p-q)!(q!)] Order doesn't matter.

and pPq = p!/q!.  Order matters.

Yep. Exactly.

---

### Post by beew on 2011-06-20
> **Legendary_Bibo said:**
> Yep. Exactly.

But OP's question obviously allows repetitions,--it would be impossible not to repeat,--so permutation is the wrong answer as well. 

Grifulkin tries to explain the concept, not saying 16P9 is the solution.

---

### Post by jerenept on 2011-06-20
> **beew said:**
> You said 16C9 which is 16!/(7!9!) and mine is 9^16, not 16^9.

Combination counts the number of subsets, order doesn't matter and no repeat allowed.

so 4C2is the number of subsets from a pool of 4 objects which has 2 items. Say how many 2 element subset can you get from {a, b, c, d}. It would be 4C2 =6. The subsets are {a, b}, {a, c}, {a, d}, (b, c}, {b, d}, {c, d}. Note that {a, b} and {b, a} are considered the same since order doesn't matter and things like {a, a} don't appear because no repetition allowed.

oic.... now I understand..

---

### Post by mmsmc on 2011-06-20
the only forums i know of where people argue about math, i think im in heaven

---

### Post by lisati on 2011-06-20
A big "thank you" for helping me exercise my grey matter. The only use I've had for figuring out permutations and combinations that I can remember in the last 30 years or so is trying to figure out the odds of winning Lotto when it was introduced in New Zealand back in the 1980s.

I'm putting in a "+1" for the answers based around 9^16, but, as you can probably guess, I'm a little bit rusty in that area.

---

### Post by 3Miro on 2011-06-20
As per the original post, the answer is 9^16. There are 9 possibilities for each of the 16 slots and the numbers are chosen independently.

If you disallow repeated numbers, then you have to use factorials in the formula, however, with only 9 characters and 16 slots, you must use some numbers two or more times.

---

### Post by Nyromith on 2011-06-20
If you use hex, you can fill each of the 16 slots with a unique number.

---

### Post by earthpigg on 2011-06-20
[Psychohistory]("http://en.wikipedia.org/wiki/Psychohistory_%28fictional%29")?!

Heathens!

---

### Post by jerenept on 2011-06-20
> **mmsmc said:**
> the only forums i know of where people argue about math, i think im in heaven

[http://forums.xkcd.com/]("http://forums.xkcd.com/")

---

### Post by fatality_uk on 2011-06-20
It's 9^16.

[http://www.google.co.uk/#hl=en&sugexp=gsqvh&xhr=t&q=9%5E16&cp=4&pf=p&sclient=psy&source=hp&aq=0&aqi=&aql=f&oq=9%5E16&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=2318d3a2eff346d5&biw=1366&bih=667](http://www.google.co.uk/#hl=en&sugexp=gsqvh&xhr=t&q=9%5E16&cp=4&pf=p&sclient=psy&source=hp&aq=0&aqi=&aql=f&oq=9%5E16&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=2318d3a2eff346d5&biw=1366&bih=667)

See, Google says so.

---

### Post by Bandit on 2011-06-20
Well I am going crazy just trying to get through Intermediate Algebra since I havent been in Highschool since 1996.

So you will understand if I say.. " Hell if I know.. "  :)

Hope everyone else helped.. :-)

---

