---
title: "BASH - service --status-all"
date: 2013-03-08
forum: Ubuntu Application Development
---

### Post by RaHorakhty on 2013-03-08
the following cmd generates a .txt with a partial listing of running services on my system:

service --status-all > services.txt | gedit& services.txt

I cannot remember exactly how load the text file with the complete listing.  any suggestions?  I'm looking for a one linerer....

---

### Post by steeldriver on 2013-03-08
I'm not sure I understand what you're asking, but iirc the services whose status can't be determined (the ones shown with [ ? ] alongside) go to stderr instead of stdout - so if you want to capture those to the file as well you would need something like

```
service --status-all > services.txt **2>&1**
```

or (in newer versions of bash only)

```
service --status-all **&**> services.txt
```

---

### Post by RaHorakhty on 2013-03-09
perfect! the 2>@1 is the (passing cmdline params to apps) is the part I didn't quite get.  I'm going to experiment...stay tuned...

---

### Post by RaHorakhty on 2013-03-14
now all the services appear but its not opening the services.txt.  can you explain why > service --status-all &> services.txt  requires the &?  whats the difference btw 2>&1 and &>?  It craps out when I try piping it directly to gedit using the following cmd: service --status-all &> services.txt | gedit "services.txt"

---

### Post by sudodus on 2013-03-14
This would be a one-liner
```
 service --status-all &>services.txt; less services.txt
```

edit: or even better if you need not save a file
```
service --status-all &> /dev/stdout|less
```

---

### Post by schragge on 2013-03-14
> **RaHorakhty said:**
> can you explain why  requires the &?  whats the difference btw 2>&1 and &>?[COLOR=blue]&>file[/COLOR] is a bash-specific shortcut for [COLOR=blue]>file 2>&1[/COLOR]. As to what all this means, please have a look at [Illustrated Redirection Tutorial]("http://wiki.bash-hackers.org/howto/redirection_tutorial").

---

