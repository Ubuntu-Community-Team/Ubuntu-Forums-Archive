---
title: "Perl's parse_dir does not work"
date: 2008-05-22
forum: Server Platforms
---

### Post by Rasvari on 2008-05-22
I have a problem listing directories with Perl in Ubuntu 8.04.

For example this won't read directory. No error messages - anything which may provide clue. 

```

#!/usr/bin/perl -W

use File::Listing;

# Let's read directory list
open(DIR_LISTING, "ls -l /tmp|") or die "buu buu!";
        print ("Parsing dir\n");
        my @dir_contents = parse_dir(\*DIR_LISTING);
close(DIR_LISTING);

foreach (@dir_contents) {
        ($name, $type, $size, $mtime, $mode) = @$_;
        if ($type eq 'd') {
                print("Directory: $name\n");
        }
        else {
                print("File: $name\n");
        }
}

```

Strange enough it worked earlier versions of Ubuntu and works still with CentOS 5.

Am I missing some packets are something?

---

### Post by Rasvari on 2008-05-22
Speaking to my self,

I found a way around it.

```


use File::Find;

find(\&wanted , "/tmp");

sub wanted {
        $time_now = time();
        $f_mtime = stat($File::Find::name)->mtime;
        $f_ctime = stat($File::Find::name)->ctime;
        if ( $time_now - $f_mtime < 900 ) {
                $nice_mtime = time2str("%Y.%m.%d %H:%M:%S", $f_mtime);
                print "New file found: $File::Find::name $nice_mtime\n";
        }

}


```

Perhaps parse_dir is somehow obsolete?

---

### Post by nova1313 on 2008-07-06
Ran into this same problem. Any reason to why parse_dir doesn't work? It doesn't seem obsoleted. It just doesn't return anything...

---

