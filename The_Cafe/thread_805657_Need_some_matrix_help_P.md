---
title: "Need some matrix help :P"
date: 2008-05-24
forum: The Cafe
---

### Post by aimran on 2008-05-24
Hi guys. I need some help with solving a set of simultaneous equations. I have three matrices, f, h and V. F and V are known. h is the unknown.

f[SIZE="1"]i[/SIZE] = f[SIZE="1"]1[/SIZE],f[SIZE="1"]2[/SIZE],...,f[SIZE="1"]n[/SIZE]


h[SIZE="1"][/SIZE] = h[SIZE="1"]1[/SIZE],h[SIZE="1"]2[/SIZE],...,h[SIZE="1"]j[/SIZE]

and V[SIZE="1"]m,n [/SIZE]is an m x n matrix.

An example of the simultaneous equation looks like this:

f[SIZE="1"]1[/SIZE] = h[SIZE="1"]j[/SIZE] * V[SIZE="1"]1,j[/SIZE]             ..................j = 1,2,...,r

f[SIZE="1"]2[/SIZE] = h[SIZE="1"]j[/SIZE] * V[SIZE="1"]2,j[/SIZE]        ..................j = 1,2,...,r

My assumptions are that since f is a scalar, h must be a row matrix and V is a column matrix since that will give a sum equal to f. IE: V must be transposed from a m x n matrix to a n x m matrix.

I've now transposed V, giving v. What I tried to do to find f so far:

f*v'*inv(v*v') = h*v*v'*inv(v*v')

But of course, the inverse of a matrix times by its transpose is going to give a singular matrix.

So does anyone have an alternative solution?

---

### Post by red_Marvin on 2008-05-24
I have some difficulties getting what you mean due to the lack of proper math scripting methods available in the forum but I think this is what you mean/want, or maybe at least is to some use? I wrote it in the equation editor of open office (oomath), so to view it just paste the code there. It is possible that I've swapped rows with columns or somesuch but I did a little test run in octave and it seems to have worked...

```
"If you have an equation system of the type" newline
y_1 ~=~ a_11 x_1 ~+~ a_12 x_2 ~+~ dotsaxis ~+~ a_1n x_n newline
y_2 ~=~ a_21 x_1 ~+~ a_22 x_2 ~+~ dotsaxis ~+~ a_2n x_n newline
dotsvert newline
y_m ~=~ a_m1 x_1 ~+~ a_m2 x_2 ~+~ dotsaxis ~+~ a_mn x_n newline newline
"where y and a is known, it can be represented and solved on matrix form like this" newline
Y ~=~ left( matrix{ y_1 ## y_2 ## dotsvert ## y_m} right) ~~~~~~ 
X ~=~ left( matrix {x_1 ## x_2 ## dotsvert ## x_n } right) ~~~~~~ 
A ~=~ left( matrix {a_11 # dotsaxis # a_1n ##
dotsvert # dotsdown  # dotsvert ##
a_m1 # dotsaxis  # a_mn} right) newline newline
Y~=~AX newline newline
drarrow ~ A^{-1}Y ~=~ A^{-1}AX ~~=~~ A^{-1}Y ~=~ IX ~=~ X newline newline
drarrow ~ X ~=~ A^{-1}Y
```

---

### Post by Mazza558 on 2008-05-24
> Need some matrix help :P

Take either the Red Pill or Blue Pill. The choice is yours.

---

### Post by urgnom on 2008-05-24
Latex notation usually works among nerds....

---

### Post by aimran on 2008-05-24
Thanks Marvin, I seem to have missed to mention that my matrices aren't square. Which is why i forced a square matrix by multiplying it with its transpose, then finding an inverse.

---

### Post by aimran on 2008-05-24
> **urgnom said:**
> Latex notation usually works among nerds....

Whats that suppose to mean lol

---

### Post by Barrucadu on 2008-05-24
> **aimran said:**
> Whats that suppose to mean lol

LaTeX: A language for typesetting things, particularly good for maths. For example, the quadratic formula would be:
```
$${-b \pm \sqrt{b^2 - 4ac}} \over 2a$$
\end
```

LaTeX source code is passed through an interpreter to generate a DVI, PDF, or PS file.

---

### Post by aimran on 2008-05-24
Yes I know what Latex is :/ Just wondering what his reference to it meant. Marvin was using OOo Writer formula not latex.

---

### Post by perce on 2008-05-24
> **aimran said:**
>  Just wondering what his reference to it meant. Marvin was using OOo Writer formula not latex.

It means that fewer people will be able to understand his message if he uses an obscure notation.

---

### Post by original_jamingrit on 2008-05-24
> **perce said:**
> It means that fewer people will be able to understand his message if he uses an obscure notation.

Which is unfortunate, LaTeX is pretty cool and should be more widely used.  But it's not WYSIWYG, so it is obscure.

---

### Post by perce on 2008-05-24
> **original_jamingrit said:**
> Which is unfortunate, LaTeX is pretty cool and should be more widely used.  But it's not WYSIWYG, so it is obscure.

I was actually referring to ooffice equations writer, LaTeX is the standard in Mathematics.

---

### Post by perce on 2008-05-24
> **aimran said:**
> Hi guys. I need some help with solving a set of simultaneous equations. I have three matrices, f, h and V. F and V are known. h is the unknown.

f[SIZE="1"]i[/SIZE] = f[SIZE="1"]1[/SIZE],f[SIZE="1"]2[/SIZE],...,f[SIZE="1"]n[/SIZE]


h[SIZE="1"][/SIZE] = h[SIZE="1"]1[/SIZE],h[SIZE="1"]2[/SIZE],...,h[SIZE="1"]j[/SIZE]

and V[SIZE="1"]m,n [/SIZE]is an m x n matrix.

An example of the simultaneous equation looks like this:

f[SIZE="1"]1[/SIZE] = h[SIZE="1"]j[/SIZE] * V[SIZE="1"]1,j[/SIZE]             ..................j = 1,2,...,r

f[SIZE="1"]2[/SIZE] = h[SIZE="1"]j[/SIZE] * V[SIZE="1"]2,j[/SIZE]        ..................j = 1,2,...,r

My assumptions are that since f is a scalar, h must be a row matrix and V is a column matrix since that will give a sum equal to f. IE: V must be transposed from a m x n matrix to a n x m matrix.

I've now transposed V, giving v. What I tried to do to find f so far:

f*v'*inv(v*v') = h*v*v'*inv(v*v')

But of course, the inverse of a matrix times by its transpose is going to give a singular matrix.

So does anyone have an alternative solution?

Gauss elimination:

[http://en.wikipedia.org/wiki/Gauss_elimination]("http://en.wikipedia.org/wiki/Gauss_elimination")

it's the only viable method for solving linear system of a certain complexity.

---

### Post by Glucklich on 2008-05-24
> **Mazza558 said:**
> Take either the Red Pill or Blue Pill. The choice is yours.

"You take the blue pill, the story ends. You wake in your bed and believe whatever you want to believe. You take the red pill, you stay in Wonderland and I show you how deep the rabbit-hole goes." 
Classic. LOL

Edit: For me it wouldn't be a tough choice. Knowing the truth, have a lot of trouble but score Trinity or wake up, go to the disco and score a random drunken chick? Besides the fact that I'm a lazy ***, I didn't found Trinity that hot (at least for the stuff I had to do). So, the blue pill would be definitely my choice.

---

### Post by Tundro Walker on 2008-05-24
What class are you taking in college that gives you homework like this?

I want to know, so I can be sure to avoid it.

---

### Post by aimran on 2008-05-24
Lol it's just simple matrix operations, shouldn't be hard. I'm trying to follow the inverse matrix method which doesn't seem to be working.

However, as perce suggested, Gaussian might work. I've been avoiding that :P. I have a reasonably large matrix and implementing Gauss code in Matlab is :mad:

---

### Post by urgnom on 2009-05-25
> **perce said:**
> Gauss elimination:

[http://en.wikipedia.org/wiki/Gauss_elimination]("http://en.wikipedia.org/wiki/Gauss_elimination")

it's the only viable method for solving linear system of a certain complexity.

I know this is pretty old... but, Gaussian elimination is one of many methods - there are lots of numerical methods for linear algebra!

---

