---
title: "determining a date."
date: 2010-09-22
forum: The Cafe
---

### Post by chips24 on 2010-09-22
ok, how would i be able to find a weekday by a date in any random year, so lets say, February 26, ...1456
how would i find the week day?

i looked it up on line and its a 
Thursday, February 26, 1456.

how would i calculate that by myself?

---

### Post by Bachstelze on 2010-09-22
```
cal feb 1456
```

Why would you want to calculate that by yourself? It's really not interesting. You know how many days there are in a week, how many days there are in a year, you can do the math. Only need to be careful about leap years.

---

### Post by chips24 on 2010-09-22
sorry, but how would i calculate the weekday with that information?
thanks for the code btw.

---

### Post by Bachstelze on 2010-09-22
You know that there are 365 days in a normal year. That's 52 weeks plus one day. 26 Feb 2010 was a Friday, so 26 Feb 2009 was a Thursday (one day before in the week). 2008 was a leap year, so 26 Feb 2008 was a Tuesday (two days before), not a Wednesday. 26 Feb 2007 was a Monday, etc.

You can make a quick Python script to repeat the process until you reach 1456, or you can look at what happens if you go backwards 10 or 100 years instead of one.

---

### Post by SeijiSensei on 2010-09-22
For years since the beginning of the "Unix epoch" which began on January 1st, 1970, you can use the "date" command like this:

date +%w --date='20-sep-2010'

which returns a value of 1 corresponding to Monday.  (Sunday = zero.)

Of course, that won't help much for a date in 1456!

Type "man date" at the command prompt for a full list of available date formats like %w.

---

### Post by saulgoode on 2010-09-22
You could examine [the source code for 'cal']("linux-ng.git;a=blob;f=misc-utils/cal.c;h=65d517a8c204276b1e15328512a468101bdb0e58;hb=HEAD"), however, the basic theory is to count the number of days since a certain date. Knowing what day that original date falls upon, you can then figure out what day your date falls upon by taking the modulus of the number of days and 7 (the modulus is the remainder left after division).

It is common to use March 1st, 0001 as the original "Day 1", and for your current date counting the days since its previous March 1st (and adding this to the days that elapsed in all preceding years). This makes it easier to account for the days added to February in leap years (since such days are added at the end of the "Martian" year). You will also have to account for September 1752 when 11 days were removed when switching to the Gregorian calendar (run 'cal 9 1752' in the terminal for more info).

---

### Post by whiskeylover on 2010-09-22
Also, keep in mind that every year divisible by 4 is a leap year. 
BUT, every year divisible by 100 is NOT.
BUT, every year divisible by 400 IS a leap year.

Eg. 2004 and 2008 are leap years
But 2100 will not be a leap year
But 2400 will be a leap year.

Now start writing the script. : )

---

### Post by t0p on 2010-09-22
There's also the wonderfully useful **ddate**, which tells you today's date according to the Discordian calendar.  For example:

```

t0p@deimos:~$ ddate
Today is Setting Orange, the 46th day of Bureaucracy in the YOLD 3176

```There are also various options that can tell you the Discordian date for any conventional date you may need or want to know.  For more info, cast this spell:

```

man ddate
```Hail Eris!

---

### Post by chips24 on 2010-09-22
> **Bachstelze said:**
> You know that there are 365 days in a normal year. That's 52 weeks plus one day. 26 Feb 2010 was a Friday, so 26 Feb 2009 was a Thursday (one day before in the week). 2008 was a leap year, so 26 Feb 2008 was a Tuesday (two days before), not a Wednesday. 26 Feb 2007 was a Monday, etc.

You can make a quick Python script to repeat the process until you reach 1456, or you can look at what happens if you go backwards 10 or 100 years instead of one.

so there is no way to figure it out except to work backwards?
ok, ive gotten some really good information here. this is awesome.

interesting calendar here...

September 1752
Su Mo Tu We Th Fr Sa
           1  2 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30

---

### Post by ratcheer on 2010-09-22
> **chips24 said:**
> so there is no way to figure it out except to work backwards?
ok, ive gotten some really good information here. this is awesome.

interesting calendar here...

September 1752
Su Mo Tu We Th Fr Sa
           1  2 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30

I know there was a month with some dates skipped, but I didn't think it was as late as 1752. I will do some research and report back.

Tim

---

### Post by Bachstelze on 2010-09-22
> **chips24 said:**
> so there is no way to figure it out except to work backwards?


YOu can also use saulgoode's method, it's basically the same thing done in a different way. More straightforward, but requires a bit more math.

---

### Post by ratcheer on 2010-09-22
> **ratcheer said:**
> I know there was a month with some dates skipped, but I didn't think it was as late as 1752. I will do some research and report back.

Tim

I was mistaken, it was, indeed September, 1752 with the missing dates:

> The Gregorian calendar was soon adopted by most Catholic countries (e.g.  Spain, Portugal, Poland, most of Italy). Protestant countries followed  later, and the countries of Eastern Europe adopted the "new calendar"  even later. In the [British Empire]("http://en.wikipedia.org/wiki/British_Empire") (including the [American colonies]("http://en.wikipedia.org/wiki/United_States")), Wednesday 2 September 1752 was followed by Thursday 14 September 1752. For 12 years from 1700 [Sweden]("http://en.wikipedia.org/wiki/Sweden") used a [modified Julian calendar]("http://en.wikipedia.org/wiki/Swedish_calendar"), and adopted the Gregorian calendar in 1753, but [Russia]("http://en.wikipedia.org/wiki/Russia") remained on the Julian calendar until 1918 (1 February became 14 February), after the [Russian Revolution]("http://en.wikipedia.org/wiki/Russian_Revolution_of_1917") (which is thus called the "[October Revolution]("http://en.wikipedia.org/wiki/October_Revolution")" though it occurred in Gregorian November), while [Greece]("http://en.wikipedia.org/wiki/Greece") continued to use it until 1924. [http://en.wikipedia.org/wiki/Julian_calendar](http://en.wikipedia.org/wiki/Julian_calendar)

Also, here is an article on calculation of day of the week: [http://en.wikipedia.org/wiki/Calculating_the_day_of_the_week](http://en.wikipedia.org/wiki/Calculating_the_day_of_the_week)

Tim

---

### Post by saulgoode on 2010-09-22
Here is some Scheme code that determines the day of the week. I wrote it as part of [a GIMP script]("http://gimp-registry.fargonauten.de/node/20193") and I completely ignored the 1752 problem (by limiting the script to handling only later dates).

```
;; Given a Gregorian date, the following computes the number 
;; of days that have elapsed since March 1st, 0000. This date
;; is chosen as an absolute reference so that leap days occur
;; at the "end of the year" (simplifying calculations). For
;; lack of a better name, I shall call this a "martius date" 
;; after the Roman word for the month of March.
;
(define (gregorian->martius yy mm dd)
  (set! mm (modulo (+ mm 9) 12))
  (set! yy (- yy (truncate (/ mm 10))))
  (inexact->exact (+ (* 365 yy)
                     (truncate (/ yy 4)) 
                     (- (truncate (/ yy 100))) 
                     (truncate (/ yy 400)) 
                     (round (* mm 30.6)) 
                     dd 
                     -1))
  )
;; Given a Gregorian date, return the day of the week 
;; (0=Sunday, 1=Monday,...)
;
(define (day-of-week yy mm dd)
  (modulo (+ (gregorian->martius yy mm dd) 3) 7)
  )

```

---

### Post by t0p on 2010-09-22
So if some guy was born on 13 September, 1734, he never had an 18th birthday?  Bummer!  If that was me, the Gregorian calendar would never have happened!  No way would I have missed that party!

---

