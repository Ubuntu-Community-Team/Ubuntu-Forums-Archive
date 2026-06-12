---
title: "Trying to optimize this code... help!"
date: 2009-03-11
forum: The Cafe
---

### Post by kpatz on 2009-03-11
I've been able to consolidate the MyLife() function down to 6 lines of code:
```

void MyLife()
{
  while (!dead())
    {
      go(work);
      work();
      go(home);
      sleep();
    }
}

```
The biggest problem I'm having is the work() function is taking too long to execute.  Any suggestions?

---

### Post by Eisenwinter on 2009-03-11
```
work(quit);
fun(have);
```

---

### Post by Keyper7 on 2009-03-11
The first thing I'd recommend is to run a profiler to check if work() is really the bottleneck. A function might just *seem* it's taking too long. You should run a debugger and check the value of the satisfaction variable during the execution of work(). Excessively low values can lead to a patience overflow error. If that's the case, the solution might be allocating a new instance of Job before calling work() again.

---

### Post by kpatz on 2009-03-11
> **Eisenwinter said:**
> ```
work(quit);
fun(have);
```The problem is, MyLife has a money leak and the code that prevents money exhaustion is inside work().

If the money runs out, it can lead to resource starvation, and possibly dead() returning true...

Another issue is the fact that MyLife is returning void, but I need to get past the performance issue in work() first.

---

### Post by Keyper7 on 2009-03-11
> **Eisenwinter said:**
> ```
work(quit);
fun(have);
```

Both lines have a noun as the function and a verb as the parameter.

Programming with closures much? :)

---

### Post by kpatz on 2009-03-11
> **Keyper7 said:**
> Both lines have a noun as the function and a verb as the parameter.

Programming with closures much? :)Well, that would be valid in an object-oriented language:
```

  work.quit();
  fun.have();

```

---

### Post by Keyper7 on 2009-03-11
An addendum to my previous post:

Don't forget that instantiating a new Job does not require interrupting the execution of work(). It can be done in a separate thread while work() is still running to prevent starvation.

---

### Post by JohnFH on 2009-03-11
I'm afraid the answers aren't quite so simple.  What you'll need to do is step into the code at a lower level to investigate why work != fun.  

For example, assuming Linux = fun, which is generally perceived as true around here, then ...

work.insert(Linux);

or 

work = new Work(Linux);

then work = fun, and you're almost there.  I say almost because you still have to consider the go statements and we all know that goto statements are bad, so see if you can reorganise your code to delete the go statements entirely.  You can do this by:

work = new Work(Linux@Home);

then, since placeOf(work) == placeOf(home), then you life becomes:

while (!dead())
{
    havefun(work);
    havefun(home);
    sleep();
}

You can improve this even further if sleep contains fun and this can be done by using the dreamlinux distro!

---

### Post by kpatz on 2009-03-11
Except for the fact that Job instantiation takes a LOT of resources, and many attempts to instantiate this object will fail, requiring many Try/Catch blocks and retry loops, which further eat into resources.  The end result is even less time for maintenance tasks that run within the sleep() function.

The authentication process for instantiating new Job objects is pretty daunting too.  Creation of Resume keys, submitting the challenge, awaiting the response (and these often timeout with no response), updating the Resume key and submitting to another socket.  And when a Resume key is accepted, the next level of Interview handshaking occurs, which is even more complex and resource intensive than the Resume authentication.  Overall, it's an overly complicated process not unlike hacking into Fort Knox, or installing Vista on an Amiga.  In the end, it's far more efficient to maintain a connection with an existing Job, if available.

JohnFH, the problem with the Linux@Home interface is that it doesn't have sufficient money-leak handlers.  I've tried running that interface during downtime maintenance, and though it runs well, it doesn't help with resource availability in the money heap.  I've also inspected my current Job connection to see if it supports the @Home interface, but unfortunately it doesn't, as they are a bit behind the times.

---

### Post by Keyper7 on 2009-03-11
kpatz, you are forgetting that Job instantiation is debugging code. Sure, it requires extra resources, but after you use it to improve the main function you can disable it.

It's up to you: conform with the current suboptimal code or do some extra effort to debug it. There's no free lunch.

---

### Post by gnomeuser on 2009-03-11
while(ssdd){
 if(pain || boredom > treshold)
 exit 0;
}

---

### Post by kpatz on 2009-03-11
My load averages are already in the high 9s while work() is running.

free -m is showing a lot of swap usage.

The hardware is proprietary with no upgrade path.  Standard DIMMs won't fit.  Nor can I drop in a multi-core CPU.  There isn't even a USB port.

If I kill() the threads that work() spawns, I run into the money leak issue.

If work() segfaults and dies on its own (hopefully doing proper severance cleanup), then I'll have resources to attempt and instantiate a new Job object.  But until then, I'm stuck in this CPU-bound loop.  And the CPU fan is clogged with dirt.

Also, getenv("ECONOMY") is returning low values, which correspond closely with job-instantiation issues.

---

