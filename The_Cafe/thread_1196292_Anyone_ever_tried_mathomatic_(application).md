---
title: "Anyone ever tried mathomatic (application)?"
date: 2009-06-24
forum: The Cafe
---

### Post by monsterstack on 2009-06-24
It's a terminal app, and ridiculously powerful stuff. If you want to try, run,
```
sudo apt-get install mathomatic
```
or just search for it in Synaptic or Add/Remove. Then just run "mathomatic" in the terminal to start doing cool stuff.

To try it out, I made it do Pythagoras' theorem:

```

1-> a^2=b^2+c^2
#1: a^2 = (b^2) + (c^2)
```

Well, not much there. But what if I wanted to solve that equation to find b? I tried doing that:

```
1-> b
                              1
#1: b = ((-1*((c^2) - (a^2)))^-)*sign1
                              2
```

Yowzer, it actually did all the transposition for me. This is pretty cool stuff. The answer it gives for b is a little unwieldy, so I tried simplifying it:

```
1-> simplify
                         1
#1: b = (((a^2) - (c^2))^-)*sign1
                         2
```

Cool stuff! But maybe I want to use this equation in a C programme, and also a python app, so I tried that:

```
1-> code c
b = (pow(((a*a) - (c*c)), (1.0/2.0))*sign1);
1-> code python
b = ((((a*a) - (c*c))**(1.0/2.0))*sign1)
```

Not bad. Not bad at all. I think this little application is awesome. That is all. Bye!

---

### Post by dragos240 on 2009-06-24
> **monsterstack said:**
> It's a terminal app, and ridiculously powerful stuff. If you want to try, run,
```
sudo apt-get install mathomatic
```or just search for it in Synaptic or Add/Remove. Then just run "mathomatic" in the terminal to start doing cool stuff.

To try it out, I made it do Pythagoras' theorem:

```

1-> a^2=b^2+c^2
#1: a^2 = (b^2) + (c^2)
```Well, not much there. But what if I wanted to solve that equation to find b? I tried doing that:

```
1-> b
                              1
#1: b = ((-1*((c^2) - (a^2)))^-)*sign1
                              2
```Yowzer, it actually did all the transposition for me. This is pretty cool stuff. The answer it gives for b is a little unwieldy, so I tried simplifying it:

```
1-> simplify
                         1
#1: b = (((a^2) - (c^2))^-)*sign1
                         2
```Cool stuff! But maybe I want to use this equation in a C programme, and also a python app, so I tried that:

```
1-> code c
b = (pow(((a*a) - (c*c)), (1.0/2.0))*sign1);
1-> code python
b = ((((a*a) - (c*c))**(1.0/2.0))*sign1)
```Not bad. Not bad at all. I think this little application is awesome. That is all. Bye!


Oh yeah.... now math is easier than ever, even though math to me is easy anyways.

---

### Post by H2SO_four on 2009-06-24
using a TI-83 is still easier...

---

