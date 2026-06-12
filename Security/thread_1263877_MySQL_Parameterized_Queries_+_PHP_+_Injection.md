---
title: "MySQL Parameterized Queries + PHP + Injection"
date: 2009-09-11
forum: Security
---

### Post by Lucky. on 2009-09-11
The following link made me think of this:

[http://ubuntuforums.org/showthread.php?t=1258982](http://ubuntuforums.org/showthread.php?t=1258982)

In the past year, I dropped my attempts at sanitizing input, and moved 100% to parameterized input.  Now I only have to sanitize my output to avoid somebody from inserting html code/javascript.

I've been plenty happy.

However every once in a while I catch somebody saying something like "YOU MUST DO EVERYTHING YOU CAN!!!!  Sanitize + Parameterized input + Escape characters + kitchen sink etc."  It makes me feel a little uneasy, but nobody can ever provide a proof of concept as to why parameterized input isn't sufficient.

Is it still possible to inject SQL if the server is using parameters?  If yes, examples speak louder than "Yep" or "It's always good practice."  I'm not trying to hack anyone...I'm just trying to save myself from writing useless code and wasting processor cycles.

---

### Post by phillw on 2009-09-11
Everytime I *think* I understand, s.o. comes on and adds something else :)

I was told to read up and learn about different peoples approaches - As I find them, I drop them on there for them to be discussed. It's a bit of brain-ache at times, but as I am learning how to keep it safe - I figure I may as well learn how to do it & more importantly, WHY to do it a particular way - For me, the slight overhead in code that may add the odd milli-second here and there is nowhere in the same league as the headache that will be caused if I 'goof' up.

Thanks for your interest in the thread. I will, as I mentioned, nail all the contributors down to a module that can be considered as safe as can be made and write a tutorial detailing what & why things have been done that way.

As for your question ... it is certainly on-topic for the thread, please feel more than welcome to ask, as these questions are asked people can discuss the various options with a view to reaching a consensus of 'best practice'.

Regards,

Phill.

---

### Post by __p1n__ on 2009-09-11
Cross-site scripting (in all it's forms) although independent of sql injection can be frequently be addressed through a common solution.  Parameterized input *plus* output sanitation is pretty nearly the equivalent of input sanitation IMHO for both vulnerabilities.

---

### Post by bobince on 2009-09-12
> **Lucky. said:**
> Is it still possible to inject SQL if the server is using parameters?

No. That is the whole point of parameters.

> However every once in a while I catch somebody saying something like "YOU MUST DO EVERYTHING YOU CAN!!!!  Sanitize + Parameterized input + Escape characters + kitchen sink etc."Yeah, they don't really know what they're talking about. They don't understand the difference between HTML-escaping, SQL-escaping and any other ways of putting out-of-bounds characters in a string, so being scared of &#8220;special&#8221; characters in general they try to filter everything they can think of out. It doesn't generally work reliably, and it messes up legitimate input that happen to contain &#8216;difficult&#8217; characters. Many's the web site that has mangled or rejected people with names like &#8220;O'Reilly&#8221;.

OK: there are reasons to &#8216;sanitise&#8217; incoming input, but they are nothing to do with SQL injection, they're usually not security problems, and they're niche issues that most other websites get wrong.

In particular, if you are using UTF-8 pages (and you should be), it can be worth it to filter away input sequences that are not valid UTF-8, to avoid a potential HTML-injection security hole in older broken browsers that allow bogus [overlong sequences]("http://www.w3.org/International/questions/qa-forms-utf-8"). But the issue only affects IE6 pre-Service Pack 1 and Opera pre-7, so it's not a huge deal.

Also most string inputs are better off without control characters (U+0000 to U+001F, other than U+00A0 in multi-line textboxes, plus U+007F to U+00BF). Naturally other specific controls may have their own validation rules. You can remove control characters from submitted values at the start of the script, whist doing the UTF-8 checking. It' can also be a good idea to get rid of the following Unicode characters which are [discouraged for use in markup]("http://unicode.org/reports/tr20/") by Unicode:

    U+0340-U+0341
    U+17A3-U+17D3
    U+2028-U+202E
    U+206A-U+206F
    U+FFF9-U+FFFC

otherwise people can do silly visual tricks like making part of the remaining page render right-to-left instead of left-to-right&#8201;&#8212;&#8201;not a security issue, just annoying. And annoying for scripts to block in traditional PHP with its lack of support for Unicode strings.

---

### Post by Lucky. on 2009-09-14
Thanks a bunch guys.  I feel reassured.  And the UTF-8 suggestion is indeed valuable.  I've read about it a little before, and will investigate it more fully.

---

