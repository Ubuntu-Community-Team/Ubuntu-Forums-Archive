---
title: "postfix/esmtp/bleeding ulcer"
date: 2007-06-07
forum: Server Platforms
---

### Post by poli on 2007-06-07
I'm setting up some blog software with PHP and would like to have some email support. From what I've dug up so far, all my options basically entail setting up mountains of cryptic files for postfix etc. Are there any options at all that are actually simple for setting up a basic relay? All I need is a simple send capability using one external account.

---

### Post by CaptainMorgan on 2007-06-08
It could depend on the blog software you are using. I too had issues with setting up a mail server, that's when I found my software could utilize a Perl module to relay to a known good smtp like smtp.google.com, pop.gmail.com, etc. It was a piece of cake to install and easy to maintain.

-Capt

---

