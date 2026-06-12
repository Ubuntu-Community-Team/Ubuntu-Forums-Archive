---
title: "feh on ubuntu 8.10"
date: 2009-03-19
forum: The Cafe
---

### Post by Tux.Ice on 2009-03-19
How can I make feh cycle my background through about 5 images?

---

### Post by Eisenwinter on 2009-03-19
Not sure if feh itself has an option for cycling backgrounds, but I know you can set backgrounds with it.

Yeah, the man entry for feh reveals nothing of that sort.

You'll have to use an external script for it.

---

### Post by Eisenwinter on 2009-03-19
Here's a little Perl script I made, which done something similar.

```
#!/usr/bin/perl -w

use strict;
use File::Find;

#feh background cycler.

#First, retrieve files.

my ($dir, $sleeptime) = (shift, shift);

print "Searching $dir for files\n";

find(\&search_, $dir);

my @Files;

sub search_ {
 my $fname = $File::Find::name;
 if ($fname =~ m/\.jpg$/i) { push(@Files, $fname); }
}
print "Found $#Files files in $dir\n";
#Files retrieved, now lets cycle through the array and set a background each time.
my $i = 0;
while (1) {
 my $background = $Files[$i];
 print "Setting background $background - next background in $sleeptime seconds\n";
 my $feh = `feh --bg-scale $background`;
 #We have set the background, now lets sleep for 10 seconds, this is done for testing purposes.
 
 sleep($sleeptime);
 $i++;
 if ($i >= scalar(@Files)) { $i = 0; }
}
```

Use, [b]perl <filename.pl> <directory of images> <time between each image being set>

I saved it as feh.pl, and my background images are located in /usr/share/archlinux/wallpaper.

So, **perl feh.pl /usr/share/archlinux/wallpaper 15** will search that entire directory, and have a timer to set image 15 seconds after the previous one was set.

This doesn't do exactly what you need, but you can modify the code to your exact needs, if you wish.

EDIT: oh, and yeah, it only works with .jpg images.

You can change it to search for png, or whatever image files you're using.

---

