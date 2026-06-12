---
title: "Math Question."
date: 2007-07-08
forum: The Cafe
---

### Post by phizikal on 2007-07-08
If a bunch of positive integers add up to 20, what is the greatest possible product of these numbers?


Yeah, for somereason I still can't get it. :)

If you want more let me kow, I know loads.

---

### Post by bread eyes on 2007-07-08
That's so easy.

---

### Post by euler_fan on 2007-07-08
I conjecture that the solution is 3,3,3,3,3,3,2.

I just don't care to try to prove it rigorously :) Ergo I leave it as a conjecture.

I'm curious to know if the problem can be solved efficiently and analytically or if it is an NP or harder problem.

---

### Post by init1 on 2007-07-08
> **phizikal said:**
> If a bunch of positive integers add up to 20, what is the greatest possible product of these numbers?


Yeah, for somereason I still can't get it. :)

If you want more let me kow, I know loads.
Wow. That's hard. :confused:

---

### Post by lisati on 2007-07-08
A quick solution doesn't leap out at me, I'd probably write some code to try to figure it out procedurally, which would probably take some time.

---

### Post by lisati on 2007-07-08
Is there a limit on the number of integers?

---

### Post by Kevin on 2007-07-09
Euler_fan..... great name.... I must say

maybe I'll change my name to eigen_fan

---

### Post by init1 on 2007-07-09
> **euler_fan said:**
> I conjecture that the solution is 3,3,3,3,3,3,2.

I just don't care to try to prove it rigorously :) Ergo I leave it as a conjecture.

I'm curious to know if the problem can be solved efficiently and analytically or if it is an NP or harder problem.
You're right. I came to that conclusion. 
If you do 2's, then it would be 2^10
2^10=4^5
4^5>5^4
4*4*4*3*5<4^5
That's what I have figured. 
3^6*2

---

### Post by init1 on 2007-07-09
> **lisati said:**
> Is there a limit on the number of integers?
Yes, logically, you can only have up to 20.

---

### Post by lisati on 2007-07-09
> **init1 said:**
> Yes, logically, you can only have up to 20.
Good answer - I hadn't thought of that!

---

### Post by euler_fan on 2007-07-09
> **init1 said:**
> You're right. I came to that conclusion. 
If you do 2's, then it would be 2^10
2^10=4^5
4^5>5^4
4*4*4*3*5<4^5
That's what I have figured. 
3^6*2

Have you seen a rigorous proof of this anywhere? I'm convinced but I still want to see how it is done.

---

### Post by phizikal on 2007-07-10
Haha, for someone I still can't get that one.

Here are a few more that I have solved, just wanna see if you guys have fun with it.

#1_____________________ 
A projectile is fired at an angle of 25° to the horizontal with an initial speed of 500 ft/sec. Find the range of the projectile to the nearest meter.


#2_____________________
The year 1978 has an unusual property: When you add the 19 to the 78, you get 97 - the middle two digits of the year! What will be the next year to have this same property?

---

### Post by euler_fan on 2007-07-10
> **phizikal said:**
> Haha, for someone I still can't get that one.

Here are a few more that I have solved, just wanna see if you guys have fun with it.

#1_____________________ 
A projectile is fired at an angle of 25° to the horizontal with an initial speed of 500 ft/sec. Find the range of the projectile to the nearest meter.


#2_____________________
The year 1978 has an unusual property: When you add the 19 to the 78, you get 97 - the middle two digits of the year! What will be the next year to have this same property?

I think I might work on the second problem . . . the first is already well solved and has formulas published on the web thanks to the physicists of the world.

The derivations are in most good college level differential equations books.

---

### Post by stepan2 on 2007-07-10
I feel like giving out a hard equation to all of you guys. I am only 13 so don't make fun9I am from georgia and thats basically more tehn  2 grades ahead of canada and US , so it willl be more then grade 8 level) .

There are four brothers and together , they have 45 dollars.  If you add two dollars to the ammount that first has , subtract two dollars to the ammount that the second has , if you multiply the ammount that the third has by 2 , and divide the ammount that the foruth has by two , all of them will have the same ammount of money. How much money does each brother have?

---

### Post by samjh on 2007-07-10
> **euler_fan said:**
> I think I might work on the second problem . . . the first is already well solved and has formulas published on the web thanks to the physicists of the world.

The derivations are in most good college level differential equations books.

I don't think the first one needs physicists or derivations.

The value of gravity is not specified, and neither is the value of any negative acceleration on the projectile (eg. drag).  Therefore, maximum range is infinity. ;)

---

### Post by jyba on 2007-07-10
> **stepan2 said:**
> There are four brothers and together , they have 45 dollars.  If you add two dollars to the ammount that first has , subtract two dollars to the ammount that the second has , if you multiply the ammount that the third has by 2 , and divide the ammount that the foruth has by two , all of them will have the same ammount of money. How much money does each brother have?

```
for w in $(seq 1 45); do
    for x in $(seq 1 45); do
	[[ $(( $w+2 )) -eq $(( $x-2 )) ]] || continue
        for y in $(seq 1 45); do
            [[ $(( $w+2 )) -eq $(( $y*2 )) ]] || continue
            for z in $(seq 1 45); do
                [[ $(( $w+2 )) -eq $(( $z/2 )) ]] || continue
                if [ $(( $w + $x + $y + $z )) -eq 45 ]; then                  
                    echo "Brother 1 has \$$w"
                    echo "Brother 2 has \$$x"
                    echo "Brother 3 has \$$y"
                    echo "Brother 4 has \$$z"
                fi
            done
        done
    done
done
```:):-D

---

### Post by Atomic Dog on 2007-07-10
Damn I'm glad I don't have to take any more math classes.

---

### Post by euler_fan on 2007-07-10
> **samjh said:**
> I don't think the first one needs physicists or derivations.

The value of gravity is not specified, and neither is the value of any negative acceleration on the projectile (eg. drag).  Therefore, maximum range is infinity. ;)

Very true . . . I suppose you could call it my ingrained desire to do everything in the mode general case and provide rigorous derivation/proof. I am a math major after all :)

---

### Post by sisco311 on 2007-07-10
> #2_____________________
The year 1978 has an unusual property: When you add the 19 to the 78, you get 97 - the middle two digits of the year! What will be the next year to have this same property?

2307

---

### Post by v8YKxgHe on 2007-07-10
Is the answer 250?

10+5+5 = 20
10*5*5 = 250

That's the highest number I could get.

---

### Post by euler_fan on 2007-07-10
For that problem I said I would work on . . .

2307.

Represent a year as an ordered quadruplet *(a,b,c,d)*

Then by the conditions given in the problem, *10a+b+10c+d=10b+c*.

This simplifies to *10a-9b+9c+d=0*

Assume it takes place in this millennium *(a=2)*, the the above reduces further to

*20-9b+9c+d=0*

Since c,d must be strictly non-negative integers, this implies the inequality

*9b+d>=0*.

Thus, *20-9b=-(9c+d) => 20-9b<=0*.

I now find the smallest b such that this last inequality holds (3)

implying *20-27+9c+d=-7+9c+d=0*

At this point, it is obvious that the answer is *d=7, c=0*.

Combining this information with the assumptions and earlier conclusions, this implies *(a,b,c,d)=(2,3,0,7)*, or 2307 as desired.

I think that will do for rigor. :) Another approach might have been the Diophantine equations, but I'm really not familiar with them enough to apply them (not my specialty).

---

### Post by lode on 2007-07-10
> **phizikal said:**
> Haha, for someone I still can't get that one.

Here are a few more that I have solved, just wanna see if you guys have fun with it.

#1_____________________ 
A projectile is fired at an angle of 25° to the horizontal with an initial speed of 500 ft/sec. Find the range of the projectile to the nearest meter.


#2_____________________
The year 1978 has an unusual property: When you add the 19 to the 78, you get 97 - the middle two digits of the year! What will be the next year to have this same property?

I learned the needed formula for the first one last year in my physics class... Unfortunately, I forgot ;)

I'd guess it would be something like:

s = v0 . sin(alpha) . sin(beta) / g ,

where s is the distance or draft, v0 the initial 'launch speed', alpha the corner between the horizontal plane and the launch direction, beta the corner between the launch direction and a vertical plane (90 - alpha) and g the acceleration due to gravity, around 9.8 m.s^&#8722;2.

Therefore:

s = v0.sin 25 sin (90-25)/9.8 .

(Conversion to SI units via [Google]("http://www.google.com/search?client=opera&rls=en&q=500+ft/sec+in+meter/sec&sourceid=opera&ie=utf-8&oe=utf-8").)

s = 152.4 x 0.422618262 x 0.906307787/9.8 .

This would give

5.95638639 meter.

Doesn't sound very credible to me, though :KS

Can someone come up with a correct sollution?

Edit:

I found the needed equation in an old .tex document ;)

d=\frac{2v_0^2\sin\alpha\sin\beta}{g}

(I applaud myself for remembering it almost correctly :P)

(d = s, the rest stays the same.)

Hence:

s = 2x152.4^2 x 0.422618262 x 0.906307787/9.8

<=> s = 1 815.50657 meter
<=> 1 815.50657 meters = 5 956.38638 feet

This one should be correct :)

---

### Post by stepan2 on 2007-07-10
wow u are good. Try solving my question :P

---

### Post by neoflight on 2007-07-10
> **phizikal said:**
> Haha, for someone I still can't get that one.

Here are a few more that I have solved, just wanna see if you guys have fun with it.

#1_____________________ 
A projectile is fired at an angle of 25° to the horizontal with an initial speed of 500 ft/sec. Find the range of the projectile to the nearest meter.


wiil that be more than the escape velocity???? if on earth? if its in Jupiter then is different...

its different if its done underwater....what about drag???

---

### Post by stepan2 on 2007-07-10
man you guys are ignoring my question. it is the one with 4 brothers

---

### Post by euler_fan on 2007-07-10
> **stepan2 said:**
> I feel like giving out a hard equation to all of you guys. I am only 13 so don't make fun9I am from georgia and thats basically more tehn  2 grades ahead of canada and US , so it willl be more then grade 8 level) .

There are four brothers and together , they have 45 dollars.  If you add two dollars to the ammount that first has , subtract two dollars to the ammount that the second has , if you multiply the ammount that the third has by 2 , and divide the ammount that the foruth has by two , all of them will have the same ammount of money. How much money does each brother have?

If it was I you insisted solve your problem, here it is.

Let the brothers be *a,b,c,d* and use the same letters to represent how much each has.

Then the initial condition gives *a+b+c+d=45*

Your further conditions imply the following four equations:
*a+2=e*
*b-2=e*
*2c=e*
*0.5d=e*

Solving for the variables *a,b,c,d* in terms of *e* and substituting these into the first equation yields (after simplification) *e=10*

so *(a,b,c,d)=(8,12,5,20)* as desired.

Or, thinking back on it, it could also have been done easily with linear algebra. But that might be overkill. :)

---

### Post by lode on 2007-07-10
> **neoflight said:**
> wiil that be more than the escape velocity???? if on earth? if its in Jupiter then is different...

its different if its done underwater....what about drag???

In my equation, I used the [standard gravity]("http://en.wikipedia.org/wiki/Standard_gravity"), g. This 'constant' will differ on other planets, but also on earth itself (where I live it's around 9.8, on the equator it's closer to 9,7). In my equation no air resistance was taken into account.

[quote=stepan2]wow u are good. Try solving my question :P[/quote]

I figured that the first brother should have 12, the second 8, the third 5 and the fourth 20 dollar.

I scribled down that

x+2+y-2+2z+w/2=4u

For 9 (just some number I tried), this gave 40.5 for 4u, so one u would be 10.125.

Using 10.125 (minus 2, plus 2, times 2 and divided by 2) this gave 45.5625, leading me to try 10, which gave the numbers 12, 8, 5 and 20.

There probably is a better (mathematically nicer) method, but mine seems to give the right answer, so that's good enough for me :)

Edit:

Hehe, as expected, euler_fan easily came up with an easier solution already :)

---

### Post by stepan2 on 2007-07-10
actually the first brother has 8 and the second has 12. That is some creative solving! The way i solved it is the following :
w=1 brother
x=2nd brother
y=3d brother
z=4th brother

w+2=x-2
w+4=x
-
w+2=2y
w+2/2=y
-
w+2=z/2
2w+4=z
--
w+w+4+w+2/2+2w+4=45
4w+w+2/2+*=45
now multiply the equation by 2=
9w+18=90
9w=72
w=8



Here is another question! So there are two guys , jack and jason . Jack tell jason that if jason gave jack 25 dollars , he would have 3 times the ammount that jack did. jason told jack that if jack gave him 25 dollars , he would have twice as much as jack. How much does jack and jason have?

---

