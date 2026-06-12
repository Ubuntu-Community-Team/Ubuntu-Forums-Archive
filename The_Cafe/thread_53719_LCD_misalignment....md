---
title: "LCD misalignment...?"
date: 2005-08-01
forum: The Cafe
---

### Post by macgyver2 on 2005-08-01
My notebook's LCD screen is acting a little funny. It's not a major issue...doesn't prevent me from using it...it's just a bit strange and I have no idea what's going on. I noticed it awhile ago but I can't pinpoint when. It's not Ubuntu specific since it was happening while I was still running Gentoo. And it doesn't have anything to do with Gnome because I used to run XFCE4. I can't, however, definitely rule out Xorg because I can't tell if it happens when I'm in a console. Like I said, I can't pinpoint exactly when it started, but I am 99.99% certain it hasn't always been this way...

What's happening is that 1) the LCD seems to be shifted one column to the left, and 2) the column all the way at the right side repeats a column, but the repeated column is one from a few over from the right. I know that was hard to understand...it's hard to word an explanation! So here's a cheap ascii graphic...

Say the LCD has columns numbered from 0-9.  The LCD *should* look as follows:
```
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
0 1 2 3 4 5 6 7 8 9
```
However, my LCD looks like this (except think 0 through 1279 with it repeating...1276):
```
1 2 3 4 5 6 7 8 9 7
1 2 3 4 5 6 7 8 9 7
1 2 3 4 5 6 7 8 9 7
```

:-k Hmm...:)

Like I said...it's been like this for at least a few months and it doesn't hinder any usage. I guess the only possibility that I'd be concerned about would be if it eventually shifted another column...then another...

Anyway I finally got around to looking into it. I spent about an hour googling around and couldn't find anything, so I'm wondering if anyone on here has any idea what's going on. Could it be software (Xorg)? Or is it hardware? Is it part of the natural aging process of LCDs?

---

### Post by umberleigh on 2006-02-17
Hey, did you find a solution to this?

I'm having the same problem, only my situation is a little different. I'm running 2 CRT monitors and it happens on the primary screen after it goes into standby mode.

---

