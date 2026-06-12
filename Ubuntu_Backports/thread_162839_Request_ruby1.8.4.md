---
title: "Request ruby1.8.4"
date: 2006-04-19
forum: Ubuntu Backports
---

### Post by Felipe_U on 2006-04-19
Hello,
        I've been serching in the repositories for ruby1.8.4. All I've found is what it the repos seems to be ruby 1.8.2 but it actually is ruby1.8.3 and rails doesn't work with ruby 1.8.3.
        Maybe I could send an email to the guy who packaged ruby1.8.3 as ruby1.8.2 and let him now that the version is mistaken, how can I know who is in charge of that package?
       So it would be nice to have a .deb of ruby 1.8.4
Regards,
Felipe

---

### Post by presentt on 2006-04-19
Came across this on another [thread...]("http://ubuntuforums.org/showthread.php?t=151927&highlight=rails%20breezy")

Looks like you need to download 1.8.4 from the Dapper repositories:
[quote=beastie] Get the .deb package for Ruby 1.8.4 and Libruby 1.8.4 from Dapper repository

[http://packages.ubuntu.com/dapper/libs/libruby1.8]("http://packages.ubuntu.com/dapper/libs/libruby1.8")
[http://packages.ubuntu.com/dapper/interpreters/ruby1.8]("http://packages.ubuntu.com/dapper/interpreters/ruby1.8")

Unpack 'em:
  dpkg -i packagename.deb[/quote] 
Hope this works, I haven't tried it.

---

### Post by Felipe_U on 2006-04-20
[quote=presentt]Came across this on another [thread...]("http://ubuntuforums.org/showthread.php?t=151927&highlight=rails%20breezy")

Looks like you need to download 1.8.4 from the Dapper repositories:
 
Hope this works, I haven't tried it.[/quote]


This worked all right!

Regards,
Felipe

---

