---
title: "ruby gems problem"
date: 2009-07-20
forum: Ubuntu Studio
---

### Post by wonderingwout on 2009-07-20
Hi,

I'm having trouble on my ubuntu server.
In Rails I can load all the necessary gems.

But when I start irb from the command line, i can not load any gems.
require 'rubygems' works fine, but than I am not able to load any other gem installed on the system.

I'm running Ubuntu 8.04 with ruby 1.8.6 enterprise edition.
I already tried to play with the PATH configuration, but I no improvement there...

---

### Post by wonderingwout on 2009-07-20
Great, found the solution myself.
I noticed there was another version of ruby installed on the system.

It also was a version 1.8.6 so I overlooked that the first times.
Now he's using the right verion.

---

