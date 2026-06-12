---
title: "My intrepid ibex experience"
date: 2009-01-15
forum: Testimonials &amp; Experiences
---

### Post by superoptimo on 2009-01-15
Hi. I finally upgrade to Ubuntu 8.10; great work! this version has many improvements and its performance its great. But it only has a little but significant error: PERL!!

After installing Ubuntu 8.10 I found Perl 5.10 very buggy and unstable. People of Ubuntu have made a big mistake by choosing it for their Intrepid release. They just are damaging the entire project by building the core system on top of this faulty component.

I also tried to install a previous version of perl. But it make things worst, because many of the ubuntu components (Dpkg as an example) are hard linked to the Perl 5.10 modules, and they had stop working then. So finally I have to keep two versions of perl. One is the ActivePerl 5.8 version installed appart on the /opt folder for the scripts that present segfaults with 5.10, and the other is the original shipped with Intrepid (5.10) for the hardlinked Ubuntu components.

Believe me, Perl 5.10 was a failure in general. Just look at this other threads:

[http://ubuntuforums.org/showthread.p...96#post6550296](http://ubuntuforums.org/showthread.p...96#post6550296)

[http://ubuntuforums.org/showthread.p...highlight=perl](http://ubuntuforums.org/showthread.p...highlight=perl)


I hope that Ubuntu people give users an option to downgrade the Perl version to 5.8, that would repair this issue.

---

