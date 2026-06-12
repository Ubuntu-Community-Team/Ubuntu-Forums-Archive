---
title: "Republican Calendar App?"
date: 2012-03-22
forum: The Cafe
---

### Post by m5K5n on 2012-03-22
I'm not sure if this is the right place for this, but...

Are there any programs for Ubuntu that display the date/time in the French Republican Calendar?

---

### Post by Sector11 on 2012-03-22
> **m5K5n said:**
> I'm not sure if this is the right place for this, but...

Are there any programs for Ubuntu that display the date/time in the French Republican Calendar?

Republican Date Library
[LibRdate]("http://librdate.sourceforge.net/") is a small C library to manage French republican dates and decimal time fully compliant to historical decrees that established the French Republican Calendar in revolutionary France. 

Reference [here]("http://www.w3schools.com/php/php_ref_calendar.asp") as well.

Also gcal
```
sudo apt-get install gcal
```

```
         $ gcal --usage=?
gcal: Use `gcal --usage[=ARG]' with one of these arguments

   adjust-value,
   alternative-format,
   astronomical-holidays,
   atmosphere,
   bahai-holidays,
   bahai-months,
   biorhythm-axis,
   blocks,
   calendar-dates,
   cc-holidays,
   celtic-holidays,
   chinese-flexible-holidays,
   chinese-flexible-months,
   chinese-holidays,
   chinese-months,
   christian-holidays,
   coptic-months,
   copyleft,
   copyright,
   cycle-end,
   cycle-step,
   date-format,
   date-variable,
   debug,
   descending-fixed-dates,
   descending-holiday-list,
   disable-highlighting,
   end-of-month,
   end-of-week,
   end-of-year,
   ethiopic-months,
   exclude-fixed-dates-list-title,
   exclude-holiday-list-title,
   execute-command,
   exit-status-help-non-zero,
   export-date-variables,
   export-text-variables,
   filter-day,
   filter-period,
   filter-text,
   fixed-dates,
   force-highlighting,
   **[COLOR="DarkRed"]french-revolutionary-months,[/COLOR]**
   gregorian-reform,
   grouping-text,
   heading-text,
   hebrew-holidays,
   hebrew-months,
   help,
   here,
   highlighting,
   holiday-dates,
   holiday-list,
   ignore-case,
   include-consecutive-number,
   include-holidays,
   include-resource-file-name,
   include-today,
   include-week-number,
   indian-civil-months,
   islamic-civil-holidays,
   islamic-civil-months,
   iso-week-number,
   japanese-flexible-holidays,
   japanese-flexible-months,
   japanese-holidays,
   japanese-months,
   leap-day,
   license,
   limit,
   list-mode,
   list-of-fixed-dates,
   long-help,
   mail,
   month,
   moonimage-lines,
   multicultural-new-year-holidays,
   old-armenic-months,
   old-egyptic-months,
   omit-multiple-date-part,
   orthodox-calendar,
   orthodox-new-holidays,
   orthodox-old-holidays,
   pager,
   period-of-fixed-dates,
   persian-jalaali-holidays,
   persian-jalaali-months,
   precise,
   resource-file,
   response-file,
   revert-match,
   shell-script,
   start-of-month,
   start-of-week,
   start-of-year,
   starting-day,
   suppress-calendar,
   suppress-date-part,
   suppress-fixed-dates-list-separator,
   suppress-holiday-list-separator,
   suppress-text-part,
   text-variable,
   time-offset,
   today,
   tomorrow,
   transform-year,
   translate-string,
   type,
   usage,
   version,
   week,
   with-week-number,
   year,
   zero-dates-only,
   zodiacal-marker-holidays

  08:07 ~
         $
```

---

### Post by m5K5n on 2012-03-23
Thanks, but for gcal I'm not sure what you type in to get the French Revolutionary Calendar version/use the french-revolutionary-months argument.

---

### Post by Sector11 on 2012-03-25
> **m5K5n said:**
> Thanks, but for gcal I'm not sure what you type in to get the French Revolutionary Calendar version/use the french-revolutionary-months argument.

Sorry for the delay, I'm still playing with gcal myself.  If I figure it out I will post it.

---

### Post by Sector11 on 2012-04-11
```
  23:13:10 ~
         $ gcal --holiday-list=long --french-revolutionary-months

Eternal holiday list:                      The year 2012 is A leap year

Start of common month 05/220 (FRR*)      - Sat, Jan  21st 2012 =  -81 days
Start of common month 06/220 (FRR*)      - Mon, Feb  20th 2012 =  -51 days
Start of common month 07/220 (FRR*)      - Wed, Mar  21st 2012 =  -21 days
Start of common month 08/220 (FRR*)      - Fri, Apr  20th 2012 =   +9 days
Start of common month 09/220 (FRR*)      - Sun, May  20th 2012 =  +39 days
Start of common month 10/220 (FRR*)      - Tue, Jun  19th 2012 =  +69 days
Start of common month 11/220 (FRR*)      - Thu, Jul  19th 2012 =  +99 days
Start of common month 12/220 (FRR*)      - Sat, Aug  18th 2012 = +129 days
Start of leap month 12/220 (FRR*)        - Mon, Sep  17th 2012 = +159 days
Start of common month 01/221 (FRR*)      - Sat, Sep  22nd 2012 = +164 days
Start of common month 02/221 (FRR*)      - Mon, Oct  22nd 2012 = +194 days
Start of common month 03/221 (FRR*)      - Wed, Nov  21st 2012 = +224 days
Start of common month 04/221 (FRR*)      - Fri, Dec  21st 2012 = +254 days

  23:14:06 ~
         $ 
```


Or
```
  23:14:06 ~
         $ gcal --holiday-list=long --french-revolutionary-months 1795


                                  1795


      January                   February                   March
 Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa
              1  2  3       1  2  3  4  5  6  7       1  2  3  4  5  6  7
  4  5  6  7  8  9 10       8  9 10 11 12 13 14       8  9 10 11 12 13 14
 11 12 13 14 15 16 17      15 16 17 18 19 20 21      15 16 17 18 19 20 21
 18 19 20 21 22 23 24      22 23 24 25 26 27 28      22 23 24 25 26 27 28
 25 26 27 28 29 30 31                                29 30 31            
                                                                         


       April                      May                       June
 Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa
           1  2  3  4                      1  2          1  2  3  4  5  6
  5  6  7  8  9 10 11       3  4  5  6  7  8  9       7  8  9 10 11 12 13
 12 13 14 15 16 17 18      10 11 12 13 14 15 16      14 15 16 17 18 19 20
 19 20 21 22 23 24 25      17 18 19 20 21 22 23      21 22 23 24 25 26 27
 26 27 28 29 30            24 25 26 27 28 29 30      28 29 30            
                           31                                            


        July                     August                  September
 Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa
           1  2  3  4                         1             1  2  3  4  5
  5  6  7  8  9 10 11       2  3  4  5  6  7  8       6  7  8  9 10 11 12
 12 13 14 15 16 17 18       9 10 11 12 13 14 15      13 14 15 16 17 18 19
 19 20 21 22 23 24 25      16 17 18 19 20 21 22      20 21 22 23 24 25 26
 26 27 28 29 30 31         23 24 25 26 27 28 29      27 28 29 30         
                           30 31                                         


      October                   November                  December
 Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa      Su Mo Tu We Th Fr Sa
              1  2  3       1  2  3  4  5  6  7             1  2  3  4  5
  4  5  6  7  8  9 10       8  9 10 11 12 13 14       6  7  8  9 10 11 12
 11 12 13 14 15 16 17      15 16 17 18 19 20 21      13 14 15 16 17 18 19
 18 19 20 21 22 23 24      22 23 24 25 26 27 28      20 21 22 23 24 25 26
 25 26 27 28 29 30 31      29 30                     27 28 29 30 31      
                                                                         

Eternal holiday list:                      The year 1795 is NO leap year

Start of common month 05/3 (FRR*)        - Tue, Jan  20th 1795
Start of common month 06/3 (FRR*)        - Thu, Feb  19th 1795
Start of common month 07/3 (FRR*)        - Sat, Mar  21st 1795
Start of common month 08/3 (FRR*)        - Mon, Apr  20th 1795
Start of common month 09/3 (FRR*)        - Wed, May  20th 1795
Start of common month 10/3 (FRR*)        - Fri, Jun  19th 1795
Start of common month 11/3 (FRR*)        - Sun, Jul  19th 1795
Start of common month 12/3 (FRR*)        - Tue, Aug  18th 1795
Start of leap month 12/3 (FRR*)          - Thu, Sep  17th 1795
Start of common month 01/4 (FRR*)        - Wed, Sep  23rd 1795
Start of common month 02/4 (FRR*)        - Fri, Oct  23rd 1795
Start of common month 03/4 (FRR*)        - Sun, Nov  22nd 1795
Start of common month 04/4 (FRR*)        - Tue, Dec  22nd 1795

  23:18:31 ~
         $ 
```

[As seen here]("https://www.gnu.org/software/gcal/manual/gcal.html")  Hope that helps.

Check this out as well: [The French Revolutionary Calendar]("http://www.tondering.dk/claus/cal/french.php")

---

