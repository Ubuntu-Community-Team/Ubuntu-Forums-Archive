---
title: "Is there a program for Linux to track weight loss and such?"
date: 2010-10-14
forum: The Cafe
---

### Post by gymophett on 2010-10-14
I want a weight loss program or something on Linux. 
I've found a program called "Perfect Diet Tracker". But it costs $50.

Anything else that's free? 
Thanks! :KS

---

### Post by amauk on 2010-10-14
```
#!/bin/bash

echo "What's your weight [kg]"
read WEIGHT
if [ "$WEIGHT" -lt 50 ]; then
    echo "Eat something, for god's sake"
elif [ "$WEIGHT" -ge 50 ] && [ "$WEIGHT" -lt 100 ]; then
    echo "You're doing OK"
elif [ "$WEIGHT" -gt 100 ]; then
    echo "You fat bastard"
fi
```

---

### Post by juancarlospaco on 2010-10-14
Pondus on the repos.
PyTrainer on the repos.

---

### Post by gymophett on 2010-10-14
> **amauk said:**
> ```
#!/bin/bash

echo "What's your weight [kg]"
read WEIGHT
if [ "$WEIGHT" -lt 50 ]; then
    echo "Eat something, for god's sake"
elif [ "$WEIGHT" -ge 50 ] && [ "$WEIGHT" -lt 100 ]; then
    echo "You're doing OK"
elif [ "$WEIGHT" -gt 100 ]; then
    echo "You fat bastard"
fi
```


funniest thing all day. :)

---

### Post by gymophett on 2010-10-14
> **juancarlospaco said:**
> Pondus on the repos.
PyTrainer on the repos.

Thanks! :D

---

### Post by mr.z on 2010-11-23
Been using pondus, which I'd found it last year! (much messing about with spreadsheets)

one problem though, keep getting an error message "another instance running" or "cannot access datafile" when I start it up..
then allot of the latest logs are missing :/

anyone had similar?

---

### Post by madjr on 2010-11-23
you can track all this stuff in special  websites.

They are free and also offer a community to guide you.

---

