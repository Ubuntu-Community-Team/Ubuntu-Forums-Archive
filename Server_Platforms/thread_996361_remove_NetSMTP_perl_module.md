---
title: "remove Net::SMTP perl module"
date: 2008-11-28
forum: Server Platforms
---

### Post by bluethundr on 2008-11-28
Currently, my Net::SMTP installation is interfering with my twiki setup and I need to remove it. How do you remove a perl module that was installed with perl -MCPAN -e shell ?

---

### Post by hictio on 2008-11-28
For exactly that purpose (not for twiki, but for testing different Perl's Oracle modules) I have used this script:

```

#!/usr/local/bin/perl -w 

use ExtUtils::Packlist; 
use ExtUtils::Installed; 

$ARGV[0] or die "Usage: $0 Module::Name\n"; 

my $mod = $ARGV[0]; 

my $inst = ExtUtils::Installed->new(); 

    foreach my $item (sort($inst->files($mod))) { 
             print "removing $item\n"; 
             unlink $item; 
          } 

     my $packfile = $inst->packlist($mod)->packlist_file(); 
          print "removing $packfile\n"; 
          unlink $packfile; 


# EoF #

```

Found it after Googling a bit, about a year ago, I guess.
Be sure to modify the interpreter's path to suit your needs.

---

