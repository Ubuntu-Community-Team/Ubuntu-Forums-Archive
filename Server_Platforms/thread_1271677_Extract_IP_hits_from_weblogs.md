---
title: "Extract IP hits from weblogs"
date: 2009-09-21
forum: Server Platforms
---

### Post by dragos2 on 2009-09-21
Hi guys,

I need some help parsing some web logs(apache default format).
```

65.55.*.* - - [16/Sep/2009:16:15:52 +0300] "GET /robots.txt HTTP/1.1" 500 7493 "-" "msnbot/2.0b (+http://search.msn.com/msnbot.htm)"

```
 I have splitted them on days, every file with its own day and then sorted
by IP like 
```

sort 16Sep > 16SepSorted

```

Now I want to count how many request
an IP has in one day.

The first column is the ip so an 

```

awk '{print $1}' 

```

will print my file sorted like this(these are IP's)

```

81.12...
81.12..
81.13..
...

```

Now I only want to count how many times an IP occurs.
Any help please?

---

### Post by t3r0 on 2009-09-21
```

$ awk '{print $1}' /var/log/apache2/access.log | sort | uniq -c | sort -rnk1
```

- Tero

---

### Post by openfly on 2009-09-21
```

#!/usr/bin/perl 

# command line argument is path to log.
$logpath = $ARGV[0];
if (!($logpath)) {
    print "\033[31m ERROR\033[36m:\033[0m Use perl $0 /path/to/access.log \n";
    exit;
}

# rename process
$0 = "parser";


# open filehandle for log readonly
open(LOGPATH, "<$logpath") or die("$logpath is not accessible");
 
$skip = $ARGV[1];
$skipcount = 0;
# begin loop through log
while (<LOGPATH>) {
    if ($skipcount > $skip) {   
    # set stdin to var $linein.
    $linein = $_;
    chomp($linein);

    print "processing\033[31m...\033[0m $linein\n";

    # cut out all the apache data from the log line.
    ($ipaddress, $ident_user)                                = $linein=~ /(\S+) (\S+) /; 
    ($date, $time, $gmtoffset)                               = $linein=~ /\[([^:]+):(\d+:\d+:\d+) ([^\]]+)\]/;
    ($request, $file, $proto, $code, $bytes, $refer, $agent) = $linein=~ /"(\S+) (.+?) (\S+)" (\S+) (\S+) "(.+?)" "(.+?)"/;

    # leave only the ldap data remaining
    $linein =~ s/(\S+) (\S+)//;
    $linein =~ s/\[([^:]+):(\d+:\d+:\d+) ([^\]]+)\]//;
    $linein =~ s/"(\S+) (.+?) (\S+)" (\S+) (\S+) "(.+?)" "(.+?)"//;

    $auth_user = $linein;

    # now chop up the ldap data
    ($cn)  =  $linein =~ /(cn=.+?,)/;
    $cn    =~ s/cn=//;
    $cn    =~ s/,//;

    @ou    =  $linein =~ /(ou=.+?,)/g;

    ($O)   =  $linein =~/(o=.+?\S)/;
    $O     =~ s/o=//;

    $totalou = $#ou;
    for ($counta = 0; $counta <= $totalou; $counta++) {
        $ou[$counta] =~ s/ou=//;
    }
  
    @tempou = @ou;
 

print "parse complete! time for a trip to the pub.\n";
# close the log filehandle
close LOGPATH;


```

This is some parser code ( ripped from something larger so may require some work ) I made up a while back to rip apart Apache logs that included Novell I-chains auth information ( basically raw ldap info ).

It's fairly applicable to all types of apache log shredding.

Enjoy.

---

### Post by dragos2 on 2009-09-21
Thanks.

---

