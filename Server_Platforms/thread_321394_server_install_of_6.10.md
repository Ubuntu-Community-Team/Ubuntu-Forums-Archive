---
title: "server install of 6.10 ?"
date: 2006-12-18
forum: Server Platforms
---

### Post by bsmith1051 on 2006-12-18
I can see the server CD images for 6.06 but is there anything comparable for 6.10 ?  

I originally tried 6.06 Desktop to test a phpBB setup but the repositories were totally out-of-date, and for security updates, too!  Apache was only 2.0.55 (current is 2.0.55 circa 7/06), phpBB was 2.0.18 (current is 2.0.21 circa 6/06), pHp is 4.4.2 (current is 4.4.4 circa 8/06), and I don't know what it did for MySQL.

I reinstalled with 6.10 Desktop and phpBB, at least, is now current.

---

### Post by PilotJLR on 2006-12-18
Yes. The server iso's are listed under "Other installation options"
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)


> **bsmith1051 said:**
> I can see the server CD images for 6.06 but is there anything comparable for 6.10 ?  

I originally tried 6.06 Desktop to test a phpBB setup but the repositories were totally out-of-date, and for security updates, too!  Apache was only 2.0.55 (current is 2.0.55 circa 7/06), phpBB was 2.0.18 (current is 2.0.21 circa 6/06), pHp is 4.4.2 (current is 4.4.4 circa 8/06), and I don't know what it did for MySQL.

I reinstalled with 6.10 Desktop and phpBB, at least, is now current.

---

### Post by chrisfay on 2006-12-18
> I originally tried 6.06 Desktop to test a phpBB setup but the repositories were totally out-of-date, and for security updates, too!

That is absolutely false.....

> Apache was only 2.0.55 (current is 2.0.55 circa 7/06)

uhhhh.....

---

### Post by PilotJLR on 2006-12-19
Yeah, I think so of the confusion (despite the typo) is over the fact that some packages in the Dapper repo's will not be equal to the Stable release version from the package authors.

This is mainly due to testing and integration with the OS. Being their "enterprise" class release, Ubuntu wants to do at least some testing, to ensure items placed in the repos are kosher with everything else. Hence the small delay. This is not necessarily a bad thing, unless newer versions fix a known bug that you are concerned about.

---

### Post by bsmith1051 on 2006-12-19
> **PilotJLR said:**
> Yes. The server iso's are listed under "Other installation options"
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Oh, wow, that's weird -- When I originally downloaded 6.10 I just clicked the link for "North America" and it immediately prompted me to save the file, i.e., it had automatically picked a download site (and download version!) for me.  Now when I click on it, it expands a list of sites and also shows the "other options link"?!

> **chrisfay said:**
> uhhhh.....
Obviously, I meant to type 2.0.59 for the current Apache version.

> **PilotJLR said:**
> some packages in the Dapper repo's will not be equal to the Stable release version from the package authors. This is mainly due to testing and integration with the OS.
Thanks, and I certainly understand that.  But these aren't the current major-number versions, they're just maintenance releases of the previous stable version.  So the missing updates are almost all security related and I don't understand why there's a 4-6 month delay in implementing them.

---

### Post by chrisfay on 2006-12-19
> pHp is 4.4.2 (current is 4.4.4 circa 8/06)

Did you also mean that?

---

### Post by bsmith1051 on 2006-12-20
> **chrisfay said:**
> Did you also mean that?
Yes.  Do I have the wrong versions listed?  I saw the 4.4.2 listed when I loaded an invalid web-page (the error message had several apps' version numbers).  The PHP homepage, [http://www.php.net/downloads.php](http://www.php.net/downloads.php) shows the most recent update for PHP 4 as 4.4.4.  As I said before, I'm not referring to the most recent 'major' version update (e.g. PHP5 vs PHP4), just the 'minor' updates (4.4.4 vs 4.4.2).

---

