---
title: "bumblebee forked"
date: 2011-09-05
forum: The Cafe
---

### Post by realzippy on 2011-09-05
[ironhide]("https://launchpad.net/~mj-casalogic/+archive/ironhide/")
[bumblebee project]("https://launchpad.net/~bumblebee/+archive/stable")

---

### Post by Thewhistlingwind on 2011-09-05
Why'd they fork it?

---

### Post by Bachstelze on 2011-09-05
What is it?

---

### Post by 3602 on 2011-09-05
Bunblebee is an effort to make nVIDIA Optimus (graphics card switching) work on Linux.

---

### Post by madjr on 2011-09-05
too bad ironhide is dead..... (in the movie :()

and yes, why did they fork it ???

---

### Post by LowSky on 2011-09-05
Why don't they ever spoon a program.

---

### Post by 3rdalbum on 2011-09-05
> **LowSky said:**
> Why don't they ever spoon a program.

That would be too weird and complicated.

---

### Post by DangerOnTheRanger on 2011-09-05
> **3rdalbum said:**
> That would be too weird and complicated.

Sporking would be much better.

---

### Post by realzippy on 2011-09-06
> **Thewhistlingwind said:**
> Why'd they fork it?

Guess it is about the use of acpi_call/test_off to turn off the nvidia card for power saving.They got totally rid of those scripts...:
[I]@LLStarks::
1) There are ACPI vars (in ASL, everything has the same name structure, var, buffers, funcs)
2) The scripts may contain more than one for a same model (in fact, that should be normal, but here it isn't)
3) The script breaks as soon as it found one working
4) A line could be working (understand: acpi_call accept it) without being related to something relevant on an other hardware than the one it cames from
5) No any of those calls should be used because they are all wrong (for those that are not var)
6) You need one for enable, and a priori two to disable, this script isn't handling that
7) Correct enable/disable functions are using args, that are not really easy to guess
8) acpi_call is not testing if it works, it is only answering : yes this object (whatever it is, a func (even without its args), a var, a buffer, ..) exist in this model table.

So, I think that now you should have understand, this script is the worse thing ever...[/I]

...means,in the moment bumblebee_stable can't turn the nvidia card off.
But it switches flawlessly to the nvidia-card,running 2 Xservers,switching via Virtual_GL.They work on switching off nvidia and also on running whole session on nvidia.

This may only affect my machine,but I upgraded from old bumblebee to ironhide,which messed up my system and didn't work.Anything serious,but too much for a normal user....fortunately bumlebee_stable ppa contains a
script cleaning up that ironhide mess.

---

### Post by madjr on 2011-09-06
i dont get it, in the description it says: *Ironhide is the continuation of bumblebee*

if its such a mess, how can it be the *continuation*?

---

### Post by realzippy on 2011-09-06
> **madjr said:**
> i dont get it, in the description it says: *Ironhide is the continuation of bumblebee*
if its such a mess, how can it be the *continuation*?

...yes,Martin Juhl (former bumblebee,now ironhide) doesn't
tell about bumblebee stable.I don't know why.Maybe they did not divorce
in friendship...

Never said that ironhide is a mess generally;on my machine it is.

---

### Post by madjr on 2011-09-06
> **realzippy said:**
> ...yes,Martin Juhl (former bumblebee,now ironhide) doesn't
tell about bumblebee stable.I don't know why.Maybe they did not divorce
in friendship...

Never said that ironhide is a mess generally;on my machine it is.

well you should let em know the mess it is ! :)

---

### Post by foutes on 2011-09-06
Installation notes:  I have given up on supporting the nvidia packages myself.. The version in Natty works just fine, and if you want newer versions, I can confirm that the X-org edgers repository works great with Ironhide.

bumblebee became very buggy right before the fork because of the nvidia packages.

bumblebee stable left the nvidia card always on last time I tried it.

Iron hide turns the nvidia card on and off.

---

### Post by realzippy on 2011-09-06
Yes,bumblebee_stable can't stop the nvidiacard in the moment.
The acpi_call script story...

---

