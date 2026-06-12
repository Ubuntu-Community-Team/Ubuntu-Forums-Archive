---
title: "Calc III help"
date: 2007-12-13
forum: The Cafe
---

### Post by bigee1212 on 2007-12-13
Hey, need some help with problem 3. 

i know how to take the gradient if its the form of grad-f(x, y), but this is just saying that u and v are functions... 

any help would be appreciated. thanks


[http://img122.imageshack.us/img122/5400/nyitie1.jpg](http://img122.imageshack.us/img122/5400/nyitie1.jpg)

---

### Post by bruce89 on 2007-12-13
Helping on someone's homework sounds dodgy.

---

### Post by lswest on 2007-12-13
lol you could just point him in the right direction, or give him an example of a similar question.  I can't help though:P only 16, haven't learned that yet lol.

---

### Post by bruce89 on 2007-12-13
I haven't a bloody clue either.

---

### Post by Kingsley on 2007-12-13
Karl's Math Help may be able to steer you in the right direction. It's what I did for a couple of my Calculus 1 quizzes. Here's his email address: [email]helpwmath@karlscalculus.org[/email]

---

### Post by jasay on 2007-12-13
It says that u and v are functions of x and y so if it helps then you can write it out u(x,y) and v(x,y).  They just wrote u and v to save space.

For a)
(Pretend what follows has partial derivatives since i'm too lazy to look for the right symbol)
grad(u(x,y)) = du/dx*i + du/dy*j
grad(v(x,y)) = dv/dx*i + dv/dy*j

So what is grad(u+v)?  Calculate as above, then rearrange some terms (group the u and v seperately) and go back from i+j terminology to grad terminology.  You should end up with what is on the right of the property.  

Do the same for the b)-d).

---

### Post by Erdaron on 2007-12-13
First, I think there is a typo in 3b, I think. It really should read:
```
grad(uv) = u*grad(v) + v*grad(u)
```

You should have learned that differentiation is [linear]("http://en.wikipedia.org/wiki/Linear_transformation"), meaning it is distributive. That should solve 3a.

Once you have that, you can solve 3b. First hold u constant, then v. Or look up a proof for a one-dimensional case, it should be identical.

3c is the same as 3b: grad (u/v) = grad (u * 1/v). Apply 3b, then simplify.

For 3d, start with expressing u^n = u*u^(n-1) and then apply 3b again. You'll probably end up with some recursive expression.

Dealing with n-dimensional derivatives as if it were normal just takes some getting used to. In the end, you'll realize they all behave the same, whether f() is a function of one x or infinitely many.

It gets extra fun when each variable can be an n-dimensional vector by itself.

---

### Post by jasay on 2007-12-13
> **Erdaron said:**
> First, I think there is a typo in 3b, I think. It really should read:
```
grad(uv) = u*grad(v) + v*grad(u)
```

You should have learned that differentiation is [linear]("http://en.wikipedia.org/wiki/Linear_transformation"), meaning it is distributive. That should solve 3a.

Once you have that, you can solve 3b. First hold u constant, then v. Or look up a proof for a one-dimensional case, it should be identical.

3c is the same as 3b: grad (u/v) = grad (u * 1/v). Apply 3b, then simplify.

For 3d, start with expressing u^n = u*u^(n-1) and then apply 3b again. You'll probably end up with some recursive expression.

Dealing with n-dimensional derivatives as if it were normal just takes some getting used to. In the end, you'll realize they all behave the same, whether f() is a function of one x or infinitely many.

It gets extra fun when each variable can be an n-dimensional vector by itself.I have to agree about the typo.  Now I feel silly for not seeing it.

---

