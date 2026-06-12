---
title: "Cleaning code and getting rid of &quot;daemons&quot;"
date: 2011-12-14
forum: Ubuntu Christian Edition
---

### Post by hoodie-ok on 2011-12-14
The following is a Private Message, sent to the moderator who locked down the "daemon" issue forum thread, after all the posts, and after he locked it down. The link to the forum is:
[http://forums.debian.net/viewtopic.php?f=3&t=73552](http://forums.debian.net/viewtopic.php?f=3&t=73552)
The following message is *not *on the forum.
--------------------------------------------

This is a genuine issue with software. The term "daemon" is a controversial term that is prevalent in the Unix world. Here is an excerpt of source code from [ftp://ftp.gnu.org/gnu/grub/](ftp://ftp.gnu.org/gnu/grub/) GRUB 1.99, in the texinfo.tex file:

\def\finishentry#1{%
    % #1 is the page number.
    %
    % The following is kludged to not output a line of dots in the index if
    % there are no page numbers.  The next person who breaks this will be
    % cursed by a Unix daemon.
    \setbox\boxA = \hbox{#1}%
    \ifdim\wd\boxA = 0pt
      \ %

I understand the puns, but for a lot of people the above code is beyond controversial - it's unacceptable. In addition, there is also a foul language problem in the Linux kernel (see [http://www.vidarholen.net/contents/wordcount/](http://www.vidarholen.net/contents/wordcount/)). So if there is an effort to clean things up, then all the inappropriate words might as well be addressed. Software, after all, is usually developed in such a way that the user often has no idea what is in the code - but there is an expectation that it's just code. It's meeting this expectation that's important.

I'm not sure what I could have done to keep my thread on-topic. It seems that the same reason this is an issue is also the same reason that people didn't respond appropriately.

Since it's unrealistic for me to go through everyone else's code and clean it up, it seems like the best way to solve this issue is with a new standard for clean code. I think I might continue my efforts by seeing if clean code can be a part of the next POSIX standard, or, if it applies, the Linux Standard Base standard - both of which Debian strives to comply with.

Any ideas or support for this initiative from the Debian community are welcome.
--------------------------------------------


So, maybe I'm weird, but I'd rather have a different name for those processes. Perhaps "recess", perhaps something else. But after a trip to the real life library today, and reading - in print - the term "daemon" in a Linux guide, in several places, it became apparent to me that this is a big complicated issue. Any help appreicated!

In my opinion, this is a legitimate reason for a "Christian" Edition. But I really think the Unix community at large shouldn't have to suffer. I think POSIX would appreciate a clean code standard, but if all else fails, a cleaned out Christian Edition would be better than nothing.

Also, the Christian Edition could serve as a pioneer in this area. And if it goes well, the Unix community might find it to be perferable to have clean code and adapt the idea.

---

### Post by Elfy on 2011-12-14
Closed.

---

