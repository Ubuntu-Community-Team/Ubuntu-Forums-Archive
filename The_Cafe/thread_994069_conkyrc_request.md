---
title: "conkyrc request"
date: 2008-11-26
forum: The Cafe
---

### Post by spyd4r on 2008-11-26
conkyrc request

hey guys;

Does anyone have example of a conky config that would have a countdown timer to a specific date/time.

Thanks in advance.

---

### Post by nhandler on 2008-11-27
Here is a small perl script that should do what you want.

```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler@ubuntu.com>

use strict;
use warnings;
use Date::Manip;

my $target=$ARGV[0] || "April 23, 2009";
my $delta = DateCalc(ParseDate("today"),ParseDate($target),1);

$delta=~s/^[+-]//;
my($y,$m,$w,$d,$h,$min,$s) = split(/:/,$delta,7);

print $y . "y " if($y>0);
print $m . "m " if($m>0);
print $w . "w " if($w>0);
print $d . "d " if($d>0);
print "$h:$min:$s" if($h>0||$min>0||$s>0);

```

Before it will work, you need to install the 'libdate-manip-perl' package from the repositories. You also need to make this script executable.

If you run 'perl ./howLong.pl', it will display how long until Jaunty is released on April 23, 2009. You can also pass a date as a command line argument to the script. For instance, I could run 'perl ./howLong.pl "January 1, 2009"' to see how long until New Years. The date that you pass to the script can be in any format supported by the [Date::Manip]("http://search.cpan.org/~sbeck/Date-Manip-5.54/lib/Date/Manip.pod") perl module.

To make this script work with conky, add something like this to your conkyrc file.

```
${execi 300 /usr/bin/perl /path/to/howLong.pl "January 1, 2009"} until 2009
```

The 300 is how long (in seconds) conky should wait before running the script again.

---

### Post by spyd4r on 2008-12-05
Thanks ;)

---

### Post by Bruce M. on 2008-12-26
Hi Folks,

I'm using Xubuntu 8.04-64bit

I installed: libdate-manip-perl.

I copied:
```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler@ubuntu.com>

use strict;
use warnings;
use Date::Manip;

my $target=$ARGV[0] || "April 23, 2009";
my $delta = DateCalc(ParseDate("today"),ParseDate($target),1);

$delta=~s/^[+-]//;
my($y,$m,$w,$d,$h,$min,$s) = split(/:/,$delta,7);

print $y . "y " if($y>0);
print $m . "m " if($m>0);
print $w . "w " if($w>0);
print $d . "d " if($d>0);
print "$h:$min:$s" if($h>0||$min>0||$s>0);
```
to ~/Conky/scripts/HowLong.pl and made it executable.

Added the following to my conky:
```
${execi 300 /usr/bin/perl ~/Conky/scripts/HowLong.pl "January 1, 2009"} until New Years
${execi 300 /usr/bin/perl /home/bruloo/Conky/scripts/HowLong.pl "January 1, 2009"} until New Years
```
and I see:
```
until New Years
until New Years
```
Opened terminal and did what was suggested:
```
bruloo@bruloo:~$ perl ~/Conky/scripts/HowLong.pl
ERROR: Date::Manip unable to determine Time Zone.
 at /usr/share/perl5/Date/Manip.pm line 3659
	Date::Manip::Date_TimeZone() called at /usr/share/perl5/Date/Manip.pm line 686
	Date::Manip::Date_Init() called at /usr/share/perl5/Date/Manip.pm line 1456
	Date::Manip::ParseDate('today') called at /home/bruloo/Conky/scripts/HowLong.pl line 10
bruloo@bruloo:~$
```

Rebooted and got the same results.
Any help out there?

CHIMO!
Bruce

---

### Post by Sealbhach on 2008-12-26
> **nhandler said:**
> 

If you run 'perl ./howLong.pl', it will display how long until Jaunty is released on April 23, 2009. 


Shakespeare's birthday (also his deathday).

Also St. George's Day.:)


.

---

### Post by ddnev45 on 2008-12-26
> **Bruce M. said:**
> 
Opened terminal and did what was suggested:
```
bruloo@bruloo:~$ perl ~/Conky/scripts/HowLong.pl
ERROR: Date::Manip unable to determine Time Zone.
 at /usr/share/perl5/Date/Manip.pm line 3659
	Date::Manip::Date_TimeZone() called at /usr/share/perl5/Date/Manip.pm line 686
	Date::Manip::Date_Init() called at /usr/share/perl5/Date/Manip.pm line 1456
	Date::Manip::ParseDate('today') called at /home/bruloo/Conky/scripts/HowLong.pl line 10
bruloo@bruloo:~$
```

Rebooted and got the same results.
Any help out there?

CHIMO!
Bruce

What timezone is your computer actually set to (I see that there are four times in your conky ([http://img518.imageshack.us/img518/7924/screenshotzl3.gif]("http://img518.imageshack.us/img518/7924/screenshotzl3.gif"))?

All I can think of for you to try is verify your timezone set up and try the script again.

---

### Post by Bruce M. on 2008-12-28
> **ddnev45 said:**
> What timezone is your computer actually set to (I see that there are four times in your conky ([http://img518.imageshack.us/img518/7924/screenshotzl3.gif]("http://img518.imageshack.us/img518/7924/screenshotzl3.gif"))?

All I can think of for you to try is verify your timezone set up and try the script again.

My timezone is: Buenos Aires.

What you see in conky are simply displays of other timezones.
UTC: obvious
Man: - my sister
Ont: - my boys

---

### Post by ddnev45 on 2008-12-28
> **Bruce M. said:**
> My timezone is: Buenos Aires.

What you see in conky are simply displays of other timezones.
UTC: obvious
Man: - my sister
Ont: - my boys

Instead of using the Orage clock, trying using the "Time and Date" settings that are located in the system sub-menu (see the attached images) to set your time zone. If I set my computer to Buenos Aires with the Orage clock settings, the script doesn't work -- same error you get; if I use the System > Time and Date, the conky works just fine.

If it works, I suggest you use the "clock" not the "orage clock" in your xfce panel (assuming you use a panel).

---

### Post by Bruce M. on 2008-12-29
> **ddnev45 said:**
> Instead of using the Orage clock, trying using the "Time and Date" settings that are located in the system sub-menu (see the attached images) to set your time zone. If I set my computer to Buenos Aires with the Orage clock settings, the script doesn't work -- same error you get; if I use the System > Time and Date, the conky works just fine.

I know where the Time & Date are set. Orage clock was just faster to get to.

> **ddnev45 said:**
> If it works, I suggest you use the "clock" not the "orage clock" in your xfce panel (assuming you use a panel).

I have the "Clock" on my panel and it is telling the correct time for Buenos Aires.

But the script still is not working, and I reinstalled Xubuntu yesterday.

**EDIT:** Don't know what happened, but today it started working.  Colour me -> happy.

**EDIT:** DUH! I saw and applied this from the first post:
> Before it will work, you need to install the 'libdate-manip-perl' package from the repositories. You also need to make this script executable.

CHIMO!
Bruce

---

