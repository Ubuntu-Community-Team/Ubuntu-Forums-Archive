---
title: "Good anti-spam solution for mail servers (postfix)"
date: 2009-11-24
forum: Server Platforms
---

### Post by StrangeWill on 2009-11-24
So I'm looking for a decent anti-spam solution, we're getting some issues which what I believe is dictionary attacks (bob@domain, sally@domain, etc.) and was looking for an easy to implement and best at avoiding false positives.

I've been looking at spamassassin, but this seems to be a bit of work to get it to play nice with postfix, and requires every e-mail to be processed twice through postfix, dunno how I feel about that. Also it uses apparently a lot of methods to check for spam, but in the end just marks it with a new subject as spam. So not only worried about false positives, but spam will still show up in boxes.

Any ideas?

---

