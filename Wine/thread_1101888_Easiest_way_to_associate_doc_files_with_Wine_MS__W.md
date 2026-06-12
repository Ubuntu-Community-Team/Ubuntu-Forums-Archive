---
title: "Easiest way to associate doc files with Wine MS  Word?"
date: 2009-03-20
forum: Wine
---

### Post by O-pos on 2009-03-20
Hi,

What would be the easiest way to associate .doc files with wine MS Word? - so that when double-clicking on .doc file to have it open in MS Word? (and not to have just blank page open in MS Word)?

Thanks! :)

---

### Post by Akvel on 2011-04-02
my way 

1. create script msword.pl with follow code
> 
#!/usr/bin/perl
my $path = `winepath -w \"@ARGV\"`;
$path =~ s%\\%/%g;
`wine "/home/USER/.wine/drive_c/Program Files/Microsoft Office/OFFICE11/winword.exe" \""$path"\"`;


2. chmod a+x msword.pl 
3. Now open .doc ->open with ->msword.pl 

:popcorn:

---

