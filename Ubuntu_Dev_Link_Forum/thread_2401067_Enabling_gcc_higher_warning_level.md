---
title: "Enabling gcc higher warning level"
date: 2018-09-13
forum: Ubuntu Dev Link Forum
---

### Post by nir4 on 2018-09-13
Hi everybody!
I have tried to to make gcc detect every warning in my code but with no avail .
I used -Wall, -Wextra, -Wpedantic but it still seems that gcc does not detect all warnings.
I think there is a solution for this in GitHub but unfortunately I do not understand it,and don't know how to implement it.
If someone could explain to me in plain words how to make higher the warning level of gcc, so that it detects every 
warning or interchangeably direct me to a site that does it I'll be thankful.
thank you very much in advance!
p.s.
I don't know how to use GitHub very good.

---

### Post by spjackson on 2018-09-14
Welcome to the forums.

> **nir4 said:**
> Hi everybody!
I have tried to to make gcc detect every warning in my code but with no avail .
I used -Wall, -Wextra, -Wpedantic but it still seems that gcc does not detect all warnings.

gcc does not have a simple way of enabling "all" warnings. It is not that good an idea to do so anyway since a) some warnings are language specific (so you don't want to enable C++ warnings when compiling Fortran) and b) some warnings are virtually contradictory (see [https://stackoverflow.com/questions/11714827/how-to-turn-on-literally-all-of-gccs-warnings](https://stackoverflow.com/questions/11714827/how-to-turn-on-literally-all-of-gccs-warnings) for some discussion on this point).

The 3 options you mention above cover most of the reasonable warnings.
> 
I think there is a solution for this in GitHub but unfortunately I do not understand it,and don't know how to implement it.
If someone could explain to me in plain words how to make higher the warning level of gcc, so that it detects every 
warning or interchangeably direct me to a site that does it I'll be thankful.
thank you very much in advance!
p.s.
I don't know how to use GitHub very good.
gcc does not have "levels" of warnings. Different combinations of warnings are just different, not higher or lower.

If you provide a link to what you are talking about on GitHub, someone might be able to explain it to you.

---

