---
title: "Any skilled programmers here?"
date: 2009-09-09
forum: The Cafe
---

### Post by praveesh on 2009-09-09
Are you a skilled programmer? If yes, create a small program to print either 1 or 0 randomly(that is , we should not be able to predict what it will print. Just like tossing a coin.) in c++/c (preferably in c++). I have just thought of a problem like this while walking ,but couldn't find a solution. Even if you don't know , c++/c , write the algorithm/logic. Let's see who will win.

---

### Post by Siph0n on 2009-09-09
Why not use python?


print random.randint(0, 1)

Done....

---

### Post by Bachstelze on 2009-09-09
> **praveesh said:**
> I have just thought of a problem like this while walking ,but couldn't find a solution.

If you were looking for a solution to obtain perfectly random numbers, it's no wonder you couldn't find one, because it's impossible to do on a computer, which is a deterministic machine. However, any decent programming language will provide one or more fucnctions to generate numbers that are random enough for all practical purposes.

---

### Post by nobodysbusiness on 2009-09-09
Are you willing to accept pseudo-random numbers? If not, this might be a bit more of a challenge than you realize...

:)

---

### Post by praveesh on 2009-09-09
> **Siph0n said:**
> Why not use python?


print random.randint(0, 1)

Done....

because it's the Python who handles the logic. There is no use of human brain. It's the person(s) who created the python interpreter who did the job (and I know only c and c++.)

---

### Post by Bachstelze on 2009-09-09
> **praveesh said:**
> because it's the Python who handles the logic. There is no use of human brain. It's the person(s) who created the python interpreter who did the job (and I know only c and c++.)

It all depends on how "random" you want to go...

[img]http://imgs.xkcd.com/comics/random_number.png[/img]

This is no less of a random number than any other.

---

### Post by praveesh on 2009-09-09
> **nobodysbusiness said:**
> Are you willing to accept pseudo-random numbers? If not, this might be a bit more of a challenge than you realize...

:)

pseudo-random numbers?.

---

### Post by Ozor Mox on 2009-09-09
> **praveesh said:**
> because it's the Python who handles the logic. There is no use of human brain. It's the person(s) who created the python interpreter who did the job (and I know only c and c++.)

I think [this](http://www.random.org) is the closest you will get to finding a true random number generator.

---

### Post by Bodsda on 2009-09-09
> **praveesh said:**
> Are you a skilled programmer? If yes, create a small program to print either 1 or 0 randomly(that is , we should not be able to predict what it will print. Just like tossing a coin.) in c++/c (preferably in c++). I have just thought of a problem like this while walking ,but couldn't find a solution. Even if you don't know , c++/c , write the algorithm/logic. Let's see who will win.

```

include <headers>
set random seed
int get_random_number()
{
    <some code to get random number>
    return random_num
}
for(int num = get_random_number();;)
{
     cout << num 
}

```

This does not care for psuedo-random/real random -- its just how you get a pretty damn random number.

Been a while since I did  C++ so forgive the psuedo code, but there is the logic

---

### Post by Simian Man on 2009-09-09
> **praveesh said:**
> because it's the Python who handles the logic. There is no use of human brain. It's the person(s) who created the python interpreter who did the job (and I know only c and c++.)

That is retarded.  In C++, you can just as well say it's the compiler who does all the work.

Here ya go:
```

#include <cstdlib>
#include <iostream>

int main( ) {
  srand(time(0));
  std::cout << (rand( ) % 2) << std::endl;
  return 0;
}

```

But rand( ) is not very good when used like that.

---

### Post by praveesh on 2009-09-09
> **HymnToLife said:**
> It all depends on how "random" you want to go...

[img]http://imgs.xkcd.com/comics/random_number.png[/img]

This is no less of a random number than any other.

please explain what this function do. What all values will it return.

---

### Post by aaaantoine on 2009-09-09
> **praveesh said:**
> please explain what this function do. What all values will it return.

It will return 4.  The number 4 was chosen by rolling a die.  It is completely random (the joke being that the number chosen for the function was chosen randomly, but that the function does not return any number other than 4).

You know, even a dice roll is not random.  There's physics involved, after all.  If you know the starting point and all the forces applied to the die, you can predict the outcome.

---

### Post by chessnerd on 2009-09-09
> **Ozor Mox said:**
> I think [this](http://www.random.org) is the closest you will get to finding a true random number generator.

Yeah, random.org is about as random of a number generation as you can get. Anything "random" done in any language is always determined by something that can be found out and then used to predict the outcome.

That said, I don't know C or C++, but here's a Java program:

import java.util.Random;

public class RandomNumber0or1{

public static void main(String [] args) {
Random rand = new Random();
System.out.println(rand.nextInt(1));
}
}

---

### Post by praveesh on 2009-09-09
Initially ,I Was thinking of creating a small program to print a random mathematical expression with two random numbers(it's because Iam too weak in computation speed. Just for training). From there , I arrived to the given problem.  Then I have thought of artificial intelligence . If generating perfect random numbers is possible, artificial intelligence will be possible. For the former problem, perfect random number is not required. Anyhow, thanks for everyone who helped.

---

### Post by praveesh on 2009-09-09
> **aaaantoine said:**
> It will return 4.  The number 4 was chosen by rolling a die.  It is completely random (the joke being that the number chosen for the function was chosen randomly, but that the function does not return any number other than 4).

You know, even a dice roll is not random.  There's physics involved, after all.  If you know the starting point and all the forces applied to the die, you can predict the outcome.

won't it always return 4? Where's the randomness. What about two numbers ? Returning 1 out of two by random.

---

### Post by Eisenwinter on 2009-09-09
What is random anyway? Can "random" be influenced in any way?

---

