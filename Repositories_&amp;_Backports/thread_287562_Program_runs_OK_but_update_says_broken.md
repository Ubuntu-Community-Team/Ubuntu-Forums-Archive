---
title: "Program runs OK but update says broken"
date: 2006-10-28
forum: Repositories &amp; Backports
---

### Post by jsandys on 2006-10-28
I installed Atlas for FlightGear on Dapper Drake, I got the .deb from the Debian repository.  When "sudo apt-get -i" complained about dependencies I did a no-no "sudo apt-get -i --force-depends".
  
Atlas 0.3.0-4 runs just fine with FlightGear 0.9.9 from the Ubuntu repository, even though some of my "libs*" libraries are not the latest version listed in the depends list.

But now the update complains about broken packages.  Is there any way that I can tell update to not worry about it?  Besides removing Atlas of course.

-- Jeff

---

