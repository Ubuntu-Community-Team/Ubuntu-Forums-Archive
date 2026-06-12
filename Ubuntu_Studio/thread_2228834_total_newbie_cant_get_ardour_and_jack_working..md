---
title: "total newbie cant get ardour and jack working."
date: 2014-06-09
forum: Ubuntu Studio
---

### Post by andrew110 on 2014-06-09
Hi,im new to just about everything,Im new to linux and digital audio.I have been reading some of the tutorial on how to setup ardour and jack.After many attempts to configure evrythin ,i got jack to start but then it quit.I am using ubuntu studio 14.I am using a usb cable to connect my guitar to the computer.I am now getting an error.Everytime i try to open my ardour file.I am starting to lose my patience and my desire to use a daw.And I do realize that it is my ignorance of the software that is the problem.Here is a screenshot of the error i am getting in ardour.I have also tried to run ardour in the command line but I'm new to that also.I knew there would be a learning curve to all this,but not of this magnitude.I was thinking of having my grandson who is 6 help but he said i was too old to figure it out lol.I think he may be right.Please help a total newbie.Thanx

---

### Post by CrocoDuck on 2014-06-15
> **andrew110 said:**
> I am using a usb cable to connect my guitar to the computer.

:confused::confused::confused:

I guess you are using a compact cable-like USB interface like [this one]("http://www.behringer.com/EN/Products/UCG102.aspx"). Could you please repost the output of this commands?

```

cat /proc/asound/cards

```

```

cat /proc/asound/pcm

```

```

aplay -l

```

```

arecord -l

```

```

cat .jackdrc

```

```

lsusb

```

---

