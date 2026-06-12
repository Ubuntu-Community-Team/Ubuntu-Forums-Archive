---
title: "To all calcurse/google calendar users."
date: 2010-03-21
forum: The Cafe
---

### Post by PurposeOfReason on 2010-03-21
Wrote a perl script to convert ics files (what google calendar exports as) to UTC time. Still has absolute paths and I mean to write a cron job to download and import it every <time here> but I have to get to work.

UPDATED

```

#!/usr/bin/perl -w
#################################
### A Simple regex program to ###
### change from one timezone  ###
### to another with ics files ###
###                           ###
###         Shawn Dyjak       ###
###     dyjaks@gmail.com      ###
#################################

use Time::Local;
$infile = $ARGV[0];
$outfile = $ARGV[1];
if (!$infile || !$outfile) {
    print "Welcome to tz_convert. You must specify files to use!\n";
    print "Usage : perl tz_convert <read file> <output file>\n";
    exit;
}
open(INFILE, "+<$infile") or die $!;
my @lines = <INFILE>;
$count = 0;
foreach (@lines) {
    if ($_ =~ /DTSTART:(\d{4})(\d{2})(\d{2})T(\d{2})(\d{2})/) {
        my ($year, $mon, $day, $hour, $min) =
            $_ =~ /(\d{4})(\d{2})(\d{2})T(\d{2})(\d{2})/;
        my $time = timegm(0, $min, $hour, $day, $mon- 1, $year - 1900);
        (undef, $min, $hour, $day, $mon, $year) = localtime($time);
        my $local_date = sprintf "%d%02d%02dT%02d%02d00Z\n", $year + 1900, $mon + 1, $day, $hour, $min;
        $lines[$count] = "DTSTART:$local_date";
    } elsif ($_ =~ /DTEND:(\d{4})(\d{2})(\d{2})T(\d{2})(\d{2})/) {
        my ($year, $mon, $day, $hour, $min) =
            $_ =~ /(\d{4})(\d{2})(\d{2})T(\d{2})(\d{2})/;
        my $time = timegm(0, $min, $hour, $day, $mon- 1, $year - 1900);
        (undef, $min, $hour, $day, $mon, $year) = localtime($time);
        my $local_date = sprintf "%d%02d%02dT%02d%02d00Z\n", $year + 1900, $mon + 1, $day, $hour, $min;
        $lines[$count] = "DTEND:$local_date";
    }
    $count++;
}
close(INFILE);
open(INFILE, ">$outfile") or die $!;
$count = 0;
    foreach (@lines) {
        print INFILE "$lines[$count]";
        $count++;
    }
close(INFILE);

```

---

### Post by juancarlospaco on 2010-03-21
You say Calcurse the NCurses program?
i dont understand, maybe a Pic *(?)*

---

### Post by PurposeOfReason on 2010-03-21
when you export a calendar from google, or any program that supports timezones in the .ics file, the format is such that it calculates what time to show on the fly. Calcurse doesn't understand timezones so the imported times are wrong. Running this on the .ics before importation fixes this.

---

### Post by PurposeOfReason on 2010-03-22
Went ahead and made a github account; been meaning to for a while. If some people could test it out it would be great. Just added full date support but even if the file reads:
```

BEGIN:VEVENT
DTSTART:20090401
DTSTAMP:20100322T193608Z
UID:h@043c1b6e2868da630e9ae15ffdabfb3ab28c5e7c@google.com
ATTENDEE;CUTYPE=INDIVIDUAL;ROLE=REQ-PARTICIPANT;PARTSTAT=ACCEPTED;CN=US Hol
 idays;X-NUM-GUESTS=0:mailto:en.usa#holiday@group.v.calendar.google.com
CLASS:PUBLIC
CREATED:20100322T173400Z
LAST-MODIFIED:20100322T173400Z
SEQUENCE:1
STATUS:CONFIRMED
SUMMARY:April Fool's Day
TRANSP:OPAQUE
END:VEVENT
END:VCALENDAR

```

it still shows up on the 31st of March, a day early. That is true for all full day events. Even when calcurse exports it looks proper but is read wrong.

[http://github.com/dyjaks/TZ_Convert](http://github.com/dyjaks/TZ_Convert)

---

