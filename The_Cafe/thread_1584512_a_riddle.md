---
title: "a riddle"
date: 2010-09-29
forum: The Cafe
---

### Post by limestone on 2010-09-29
Ok, I saw a riddle the other day on a milk carton that confuses me. Actually it's the answer that confuses me. Here is the riddle:
> You catch a pike, but the scale is broken.
The pike weighing two kilograms plus half its weight.
How much does the pike weigh?The answer according to the milk carton is 4, with the equation: x=2+0.5x.
I get the answer to 3 not considering the equation. 

Here is the answer:
> **pont.andersson said:**
> 
x = 2 + 0.5x

x = 2

[I]"I've been told that between a number and x/y there is a +.
But here they mean half x."[/I]

So. 
0.5x = 4 because half of x (2)/0.5 = 4 <----------- The pike weight is 4kg

Assuming you don't know the equation you could assume that half of something also is /2, in that case x (2)/2=1 and that would make the pike weight 3kg as I first suggested. 

But, there must be a wormhole in this, because the pike can't obviously not weight both 3 and 4kg. I hate these things :P

---

### Post by RiceMonster on 2010-09-29
Well right away, I can see an issue with you're code. You're adding where you should be multiplying.

Also, you're program wouldn't correctly solve it anyway. Because at the beginning, x has no value, so you're program thinks it's "2 + 0.5 + nothing". You can't just give c straight algebra and expect it to solve it.

---

### Post by limestone on 2010-09-29
> **RiceMonster said:**
> Well right away, I can see an issue with you're code. You're adding where you should be multiplying.

Also, you're program wouldn't correctly solve it anyway. Because at the beginning, x has no value, so you're program thinks it's "2 + 0.5 + nothing". You can't just give c straight algebra and expect it to solve it.

I figured, it has to be x=2+0.5 and then x=x+x but thats 5 :P
multiply? between 0.5 and x?

---

### Post by RiceMonster on 2010-09-29
When I originally posted, you had 

x = 2 + 0.5 + x

whereas the original equation is x = 2 + 0.5x
Also, the answer IS 4. I will demonstrate.

x = 2 + 0.5x
x - 0.5x = 2
0.5x = 2
x = 2/0.5
x = 4

Your solution is incorrect. You had x = 2 + 0.5. No, that's not what x is, because by saying that, you're assuming x is 1.

---

### Post by limestone on 2010-09-29
> **RiceMonster said:**
> When I originally posted, you had 

x = 2 + 0.5 + x

whereas the original equation is x = 2 + 0.5x. 0.5x.

God I hate math :P but the original equation says x=2+0.5x. how is that x = 2 + 0.5x. 0.5x?

---

### Post by RiceMonster on 2010-09-29
Sorry, that was a typo. See my edit above.

---

### Post by limestone on 2010-09-29
> **RiceMonster said:**
> 
x = 2 + 0.5x
x - 0.5x = 2
0.5x = 2
x = 2/0.5
x = 4


Ok, I trust you but I still don't get it.. Seems like I need to go back to school :P damn:P

---

### Post by Bodsda on 2010-09-29
Yeah, I'm having trouble with this one as well. This is the way I interpret it.
 
1) You catch a pike, but the scale is broken.
2) The pike weighing two kilograms plus half its weight.
3) How much does the pike weigh? 
 
Line 1 seems irrelevant
Line 3 asks the sum of the equation in line 2
 
Line 2 doesnt sound right, it doesnt seem complete to me but I interpret it as
 
Pike = 2KG
Pike / 2 = 1KG
Pike + (Pike / 2) = 3KG
I can't understand how RiceMonster gets his answer
 
1) x = 2 + 0.5x
2) x - 0.5x = 2
3) 0.5x = 2
4) x = 2/0.5
5) x = 4
 
where does 0.5 come from?
 
We are told that weight = 2KG, so 0.5x, assuming you mean (x / 2) = 1 not 2
 
-- Bodsda

---

### Post by limestone on 2010-09-29
> **Bodsda said:**
> 
Pike = 2KG
Pike / 2 = 1KG
Pike + (Pike / 2) = 3KG

  
I know, right? :D wtf?

---

### Post by Bachstelze on 2010-09-29
> **Bodsda said:**
> 
Line 2 doesnt sound right, it doesnt seem complete to me but I interpret it as
 
Pike = 2KG
Pike / 2 = 1KG
Pike + (Pike / 2) = 3KG

No. You don't know what pike is (and therefore you don't know what pike/2 is either). What you know is that
pike = 2 + pike/2.

---

### Post by limestone on 2010-09-29
> **Bachstelze said:**
> No. You don't know what pike is (and therefore you don't know what pike/2 is either). What you know is that
pike = 2 + pike/2.
 
Ah! A light went off! So pike (x) already = to something, and then = 2 + .05 pike (x). right?:P

---

### Post by Bachstelze on 2010-09-29
> **pont.andersson said:**
> Ah! A light went off! So pike already = to something, and then = 2 + .05 pike. right?:P

Yes.

---

### Post by nlsthzn on 2010-09-29
Oh wow!  This brings back mega memories... got this riddle about 20 odd years ago, was somewhere between primary and high school and had a few epic fights with my parents and some other grown ups about what the right answer is... can't remember what I though the answer was now so I am not sure who was right :p

---

### Post by limestone on 2010-09-29
Well, I still can't get it. I don't know whats the deal with my head, because now I cant get how 2/0.5=4 ? :-( starting to get worried..  :-(

---

### Post by Bachstelze on 2010-09-29
Why do you insist in making a C program for it? As RiceMonster said, that's not what C is for.

---

### Post by limestone on 2010-09-29
> **Bachstelze said:**
> Why do you insist in making a C program for it? As RiceMonster said, that's not what C is for.

Just began learning C, and programming is solving problems, so I thought this was good mind training.

And RiceMonster said "You can't just give c straight algebra and expect it to solve it."

---

### Post by formaldehyde_spoon on 2010-09-29
The only maths you need for this is to be able to multiply/divide by 2.

Total weight is 2 + (the other) half the weight. 
So 2kg is half the weight, total is 4.

---

### Post by whiskeylover on 2010-09-29
"2 kg + half its weight" means the other half is 2 kg. So, total weight is 4 kgs. Simple.

---

### Post by limestone on 2010-09-29
> **whiskeylover said:**
> "2 kg + half its weight" means the other half is 2 kg. So, total weight is 4 kgs. Simple.

Yeah, That did the last push :)
x = 2 + 0.5x

x = 2

[I]"I've been told that between a number and x/y there is a +.
But here they mean half x."[/I]

So. 
0.5x = 4 because half of x (2)/0.5 = 4 <-------

Assuming you don't know the equation you could assume that half of something also is /2, in that case x (2)/2=1 and that would make the pike weight 3kg as I first suggested. 

But, there must be a wormhole in this, because the pike can't obviously not weight both. I hate these things :P

---

### Post by Dougie187 on 2010-09-29
This is really easy. Basically as everyone else has said.

You are given that the pike weighs 2 kg + half of it's weight. So your equation (as you have written previously) is

Weight = 2 + (Weight/2)

In this case, you are adding two things, 2 and (Weight/2) and you know that (Weight/2) is half of Weight, so that means that 2 is also half of Weight. Since 2*(Weight/2) has to be Weight as well.

So Weight = 4.

Also, as other people have said, it's useless to write this in C, because you are basically doing symbolic algebra. To do this in C you would have to be able to solve it on paper first, and then write the code in C to to the elementary operations.

---

### Post by grahammechanical on 2010-09-30
If the Pike weighs 4Kg as some say it does, then, according to the equation 4Kg = 2kg + 2Kg. 

On the other hand if the Pike weighs 3Kg then, according to the equation 3Kg = 2kg + 1.5kg. 

Which one is right in the real world or when you find a working set of scales?

regards

---

### Post by grahammechanical on 2010-09-30
According to the equation if the Pike weighed 4kg, as some say it does then, 4kg would equal 2kg plus half of 4kg. Which it does.

On the other hand if the Pike weighed 3kg then, 3kg would equal 2kg plus half of 3kg (1.5 kg). Which it does not

Regards

---

### Post by Old_Grey_Wolf on 2010-09-30
x=2+0.5x
x-0.5x=2+0.5x-0.5x (subtract 0.5x from both sides)
x-0.5x=2 (simplify)
(x/x)-(0.5x/x)=2/x (devide both sides by x)
1-0.5=2/x (simplify)
0.5=2/x (simplify)
0.5*x=(2/x)*x (multiply both sides by x)
0.5x=2 (simplify)
0.5x/0.5=2/0.5 (divide both sides by 0.5)
x=2/0.5 (simplify)
[COLOR="Red"]x=4[/COLOR] (simplify)

---

### Post by formaldehyde_spoon on 2010-09-30
> **pont.andersson said:**
> Yeah, That did the last push :)
x = 2 + 0.5x

x = 2

[I]&quot;I've been told that between a number and x/y there is a +.
But here they mean half x.&quot;[/I]

So. 
0.5x = 4 because half of x (2)/0.5 = 4 <-------

Assuming you don't know the equation you could assume that half of something also is /2, in that case x (2)/2=1 and that would make the pike weight 3kg as I first suggested. 

But, there must be a wormhole in this, because the pike can't obviously not weight both. I hate these things :P

!!

There aren't any wormholes, you're confusing yourself.  This isn't really about maths at all, just logic. 

To correct you above: 
x = 2 + 0.5x
x = **4**
(x is the total weight here, not the 'unknown' half) 

Exactly half the weight is unknown, so the unknown part must equal the same as the known half. 

If it instead said ''the fish weighs 3kg plus one quarter of the weight'' the answer would also be 4kg - one quarter is unknown, therefore the known part (3kg) must be the other three quarters. 

''1kg plus three quarters of the weight'' would also be the same, and so on.

---

### Post by standingwave on 2010-10-01
We used to get the coolest puzzles on this forum. Monty Hall, Boy-Girl, etc. How about this one? 

A census-taker knocks on a door, and asks the woman inside how many children she has and how old they are.

*"I have three daughters, their ages are whole numbers, and the product of the ages is 36,"* says the mother.

"That's not enough information," responds the census-taker.

*"I could tell you the  sum of their ages, but you'd still be stumped."*

"I wish you'd tell me something more."

*"Okay, my oldest daughter Annie likes dogs."*

What are the ages of the three children?

---

### Post by frup on 2010-10-01
> **standingwave said:**
> We used to get the coolest puzzles on this forum. Monty Hall, Boy-Girl, etc. How about this one? 

A census-taker knocks on a door, and asks the woman inside how
many children she has and how old they are.

*"I have three daughters, their ages are whole numbers, and the product of the ages is 36,"* says the mother.

"That's not enough information," responds the census-taker.

*"I could tell you the  sum of their ages, but you'd still be stumped."*

"I wish you'd tell me something more."

*"Okay, my oldest daughter Annie likes dogs."*

What are the ages of the three children?


My guess is 1 x 12 x 3

---

### Post by standingwave on 2010-10-01
> **frup said:**
> My guess is 1 x 12 x 3That adresses the first clue but not the second, i.e.  *"I could tell you the  sum of their ages, but you'd still be stumped."*

---

### Post by formaldehyde_spoon on 2010-10-01
2, 2, 9.

---

### Post by standingwave on 2010-10-01
> **formaldehyde_spoon said:**
> 2, 2, 9.Yep.

---

### Post by formaldehyde_spoon on 2010-10-01
> **standingwave said:**
> Yep.

Only 'cause I've seen similar. ;)
I was totally stumped the first time I saw one...

Now that I've answered it (too late!), someone tell me whether it would have been better form to not answer a riddle I already knew how to figure out... Am  I ruining others' enjoyment??

---

### Post by frup on 2010-10-01
> **formaldehyde_spoon said:**
> Only 'cause I've seen similar. ;)
I was totally stumped the first time I saw one...

Now that I've answered it (too late!), someone tell me whether it would have been better form to not answer a riddle I already knew how to figure out... Am  I ruining others' enjoyment??

I accept the answer, but I don't understand the relationship to "being stumped" over the sum or anything to do with dogs.

So while there is one correct answer, I don't see how any other answer is invalid, aside from not being what the question master determines as so.

---

### Post by formaldehyde_spoon on 2010-10-01
> **frup said:**
> I accept the answer, but I don't understand the relationship to &quot;being stumped&quot; over the sum or anything to do with dogs.

So while there is one correct answer, I don't see how any other answer is invalid, aside from not being what the question master determines as so.

Ah, well that's what makes it interesting ;)
There is only one correct answer, and all three clues are vital.

---

### Post by standingwave on 2010-10-01
> **formaldehyde_spoon said:**
> Now that I've answered it (too late!), someone tell me whether it would have been better form to not answer a riddle I already knew how to figure out... Am  I ruining others' enjoyment??I don't think so. At least not in this case as you didn't reveal the reasoning behind the answer.

---

### Post by frup on 2010-10-01
I got it. I just tabled out the various answers and the reason I would be stumped jumped out at me. The first time I just went with the first answer that came to my head.

---

### Post by forrestcupp on 2010-10-01
> **pont.andersson said:**
> 
Assuming you don't know the equation you could assume that half of something also is /2, in that case x (2)/2=1 and that would make the pike weight 3kg as I first suggested. 


Your whole problem is that you think x is 2, and x is not 2.  It never said that the weight of the pike is 2kg and if you add half to it then you get some magical new weight because the pike suddenly grew.  It said that the weight is 2 *plus* half of its weight.  So it's silly to say x (2)/2=1 when x isn't 2 in the first place.

Also, you can't assume that we don't know the equation.  We come up with the equation just by reading the riddle.  You need to brush up on how to translate story problems to equations.

The Pike's weight is 2kg plus half of the Pike's weight.
So we'll let **x** represent the **Pike's weight** and we know that **is** always means "=" in story problems, so if we directly translate the story to an equation:
x=2+(x/2)

The reason Ricemonster got from
x-0.5x=2
  to
0.5x=2
is because 1.0x - 0.5x = 0.5x

To do this in C or C++, you pretty much have to run through the numbers testing each one.  Assuming the weight is an integer:
```
float x = 0;
while (x != 2.0 + x/2.0)
{
   x++;
}

```
This starts at 0 and if that isn't the answer, it increments it by 1 and tests it again.  Whatever x ends up being is the answer.  If the weight isn't an integer, it makes things a lot harder.  Just knowing that everything is divided in half, you could increment by 0.5 instead of 1.

---

### Post by Calash on 2010-10-01
> **Old_Gray_Wolf said:**
> x=2+0.5x
x-0.5x=2+0.5x-0.5x (subtract 0.5x from both sides)
x-0.5x=2 (simplify)
(x/x)-(0.5x/x)=2/x (devide both sides by x)
1-0.5=2/x (simplify)
0.5=2/x (simplify)
0.5*x=(2/x)*x (multiply both sides by x)
0.5x=2 (simplify)
0.5x/0.5=2/0.5 (divide both sides by 0.5)
x=2/0.5 (simplify)
[COLOR="Red"]x=4[/COLOR] (simplify)

My algebra is rusty.  Had to read that 3 times to comprehend all the steps.


Nice job.

---

### Post by skeebo on 2010-10-01
Well lets say hypothetically the pike weighs 14.

That would mean it weighs 2 + (half of 14, which is 7)

so that would mean 14 = 2+7 which IS NOT TRUE.

Take any real number and try that....it won't work. The only number that you can apply to the equation 2+0.5x = x is 4. Remember guys, you have TWO x's in this equation, both x's have to be the SAME number, otherwise it would use another variable in the place of x.

So the only real number that can fit this equation is 4.

---

### Post by nlsthzn on 2010-10-01
On the second riddle about the ages I still don't get why 2,2,9 is correct and what it has to do with the sum getting you stumped and where the dog fits in the picture...?

---

### Post by koenn on 2010-10-01
> **nlsthzn said:**
> On the second riddle about the ages I still don't get why 2,2,9 is correct and what it has to do with the sum getting you stumped and where the dog fits in the picture...?


1- the first clue is simple: a * b * c = 36
where a, b, c are the ages of the respective daughters.

2- second clue tells you even if you'd know the sum of a + b + c, you still wouldn't know the answer, suggesting that this information would still allow for multiple solutions.
So you got to work out for which values/combinations of a,b,c this would be the case

3- third clue then probably contains information that helps to choose between the solutions you get in step 2


I know how to compute it, but does anyone know the math to do this ?

---

