---
title: "help with sorting/joining 2 text files"
date: 2013-10-25
forum: Server Platforms
---

### Post by nerdtron on 2013-10-25
So I have a file "sorted.txt" which contains about 900 lines of ip addresses i sorted using the sort -u (no duplicates) command like:
```

10.101.252.117
10.101.252.119
10.101.252.120
10.101.252.155
.
.
.

```

And I have another file "master.txt" which contains all ip address with the corresponding site name like:

```

10.101.252.115        site remote
10.101.252.117        site a
10.101.252.118        site b
10.101.252.119        site c
10.101.252.120        site d
10.101.252.214        site e 
10.101.252.155        another site
10.101.252.145        site sample
.
.
.

```

Since "master.txt" contains all IP addresses, all entries in "sorted.txt" can be found in there. Now I want to create another file where the "sorted.txt" will have another column that will tell which site name it is. Like this:
```

10.101.252.117     site a
10.101.252.119     site c
10.101.252.120     site d
10.101.252.155     another site
.
.
.
```

I'm ready to do some scripts. Any idea or commands to do this?

---

### Post by drmrgd on 2013-10-25
Here's one way to do it with Perl:

```

#!/usr/bin/perl


use warnings;
use strict;
use Data::Dumper;


my %result;
open( my $master_fh, "<", "master.txt" ) or die "Can't open the master.txt file: $!";
my %lookup = map { /(\d+\.\d+\.\d+\.\d+)\s+(.*)$/ } <$master_fh>;


open( my $sorted_fh, "<", "sorted.txt" )  or die "Can't open the sorted.txt file: $!";
chomp( my @ips = <$sorted_fh> );


print join( "\t", $_, $lookup{$_} ), "\n" for @ips;

```

First I read in the 'master.txt' file and store the data in a hash with the IP address as the key and the site names as the value:

```

$ perl ip_lookup.pl 
$VAR1 = {
          '10.101.252.115' => 'site remote',
          '10.101.252.117' => 'site a',
          '10.101.252.214' => 'site e ',
          '10.101.252.119' => 'site c',
          '10.101.252.155' => 'another site',
          '10.101.252.120' => 'site d',
          '10.101.252.145' => 'site sample',
          '10.101.252.118' => 'site b'
        };

```

Then I read in the 'sorted.txt' file and store all of those IP addresses in an array.  Finally, I iterate through the array, looking for each one of the IP addresses in hash that I generated above, and printing out the matches.  Since you've already sorted the IP addresses in sorted.txt (which can also be done on the fly in Perl if you want to save one more step), I don't need to sort the output.

If you want to save this to a new file, you can just redirect the output to a new file:

```

perl ip_lookup.pl > new_textfile.txt

```

or we can create a filehandle to directly write the results to.  

Of course, if you don't want a script option (not sure if you just wanted a quickie solution or something that you can play with and modify later), you can always just use the '-f' option of grep:

```

$ grep -f sorted.txt master.txt 
10.101.252.117        site a
10.101.252.119        site c
10.101.252.120        site d
10.101.252.155        another site

```

:)

---

### Post by nerdtron on 2013-10-25
Alright, let me see if that script can do the job. Thanks a lot for that! :)

```
$ grep -f sorted.txt master.txt 
10.101.252.117        site a
10.101.252.119        site c
10.101.252.120        site d
10.101.252.155        another site
```
:shock:
YOU CAN GREP A FILE AGAINST ANOTHER FILE?? I think this if this works, this one is better.

---

