---
title: "locale problem with C standard library"
date: 2014-06-11
forum: Ubuntu Application Development
---

### Post by rclocher3 on 2014-06-11
Hi all,

I live in the US but I don't like inches, the mm/dd/yy way of writing dates, 12-hour time with AM/PM, and so on.  So I created my own custom locale.  I had some problems installing my new custom locale, so I wrote a simple program in C to test the installed locale:

```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>

int main(int argc, char *argv[])
{
    char *setlocalestr, timestring[200], datestring[200];
    time_t t;
    struct tm *tmp;

    setlocalestr = setlocale(LC_ALL, NULL);
    printf("Current locale: %s\n", setlocalestr);

    t = time(NULL);
    tmp = localtime(&t);
    if (strftime(datestring, sizeof(datestring), "%x", tmp) == 0) {
        fprintf(stderr, "strftime returned 0");
        exit(EXIT_FAILURE);
    }
    if (strftime(timestring, sizeof(timestring), "%X", tmp) == 0) {
        fprintf(stderr, "strftime returned 0");
        exit(EXIT_FAILURE);
    }
    printf("Date formatted according to current locale: %s\n", datestring);
    printf("Time formatted according to current locale: %s\n", timestring);
    exit(EXIT_SUCCESS);
}

```

I figured out what I was doing wrong with installing my locale, so I no longer get locale warnings when I use the command line.  Now my Lightning calendar uses 24-hour time, but unfortunately my test program says that I'm using the "C" locale, and the date is formatted incorrectly!  Why doesn't the GNU C Library use the installed locale?

Here's the output from my program:
```

$ ./locale-test
Current locale: C
Date formatted according to current locale: 06/11/14
Time formatted according to current locale: 18:09:29
$

```

/etc/environment contains the line ```
LANG="rob_custom.utf8"
``` .  /etc/default/locale has the same line.  If I run "locale -a", "rob_custom.utf8" (without quotation marks) is at the bottom of the list, showing that I managed to install my custom locale.  Here's the output of "locale":

```

$ locale
LANG=rob_custom.utf8
LANGUAGE=en
LC_CTYPE="rob_custom.utf8"
LC_NUMERIC="rob_custom.utf8"
LC_TIME="rob_custom.utf8"
LC_COLLATE="rob_custom.utf8"
LC_MONETARY="rob_custom.utf8"
LC_MESSAGES="rob_custom.utf8"
LC_PAPER="rob_custom.utf8"
LC_NAME="rob_custom.utf8"
LC_ADDRESS="rob_custom.utf8"
LC_TELEPHONE="rob_custom.utf8"
LC_MEASUREMENT="rob_custom.utf8"
LC_IDENTIFICATION="rob_custom.utf8"
LC_ALL=
$ 

```

If anyone can give me any hints why the C standard library does not use the installed locale specified by the LANG environment variable, then I would be very grateful.

- Rob

---

### Post by rclocher3 on 2014-06-11
I read my own post, and I thought I saw the problem: LC_ALL is passed to the setlocale() function, but the LC_ALL environment variable is empty.  So I edited /etc/environment and /etc/default/locale, and added a line to each:
```

LC_ALL="rob_custom.utf8"

```

After a reboot, running "locale" now shows that LC_ALL has been set to the same value as LC_CTYPE, LC_NUMERIC, LC_TIME, etc.  Unfortunately my test program still reports that the GNU C Library is falling back to the default "C" locale.  How confusing!

- Rob

---

### Post by steeldriver on 2014-06-12
Hmm... just had a play with this and I *think* the answer is that the 2nd argument to setlocale should be the empty (not NULL) string if you want the program to inherit the environment's local e.g. for LC_TIME

```

    setlocalestr = setlocale(LC_TIME, [COLOR=#0000ff]**""**[/COLOR]);

```

From the setlocale manpage:

```

       char *setlocale(int category, const char *locale);


       **If locale is not NULL**, the program's current locale is modified accord&#8208;
       ing  to the arguments.  The argument category determines which parts of
       the program's current locale should be modified.
      .
      .
      .
       [B]If locale is "", each part of the locale that should be modified is set
       according to the environment variables.[/B]  The  details  are  implementa&#8208;
       tion-dependent.   For  glibc, first (regardless of category), the envi&#8208;
       ronment variable LC_ALL is inspected,  next  the  environment  variable
       with  the same name as the category (LC_COLLATE, LC_CTYPE, LC_MESSAGES,
       LC_MONETARY, LC_NUMERIC, LC_TIME) and finally the environment  variable
       LANG.   The  first existing environment variable is used.  If its value
       is not a valid locale specification, the locale is unchanged, and  set&#8208;
       locale() returns NULL.

```

Perhaps the way to think about it is like the strtok function - you call it the first time with a non-NULL argument (either a specific locale string, or "" to indicate that the program should inherit the environment's locale), then subsequent calls with a NULL argument will poll the actual value set by the first call. For example, changing your code to
```

.
.
    setlocale(LC_ALL, "");
    setlocalestr = setlocale(LC_TIME, NULL);
    printf("Current locale: %s\n", setlocalestr);
.
.

```

I get
```

$ ./locale-test 
Current locale: en_CA.UTF-8
Date formatted according to current locale: 14-06-12
Time formatted according to current locale: 08:04:29 AM
$ 
$ LC_ALL=en_GB.UTF-8 ./locale-test 
Current locale: en_GB.UTF-8
Date formatted according to current locale: 12/06/14
Time formatted according to current locale: 08:04:47
$ 
$ LC_TIME=en_US.UTF-8 ./locale-test 
Current locale: en_US.UTF-8
Date formatted according to current locale: 06/12/2014
Time formatted according to current locale: 08:05:30 AM

```

---

### Post by rclocher3 on 2014-06-12
Thank you steeldriver, that was it!  That points out a surprising "gotcha": a program that uses the GNU C Library will ignore the user's locale unless the program calls setlocale() first (and does so correctly, haha).

I'm very grateful for your help!

Regards,
- Rob

---

