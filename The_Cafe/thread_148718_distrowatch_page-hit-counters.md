---
title: "distrowatch page-hit-counters"
date: 2006-03-22
forum: The Cafe
---

### Post by lee_connell on 2006-03-22
How do these work?  How does DW detect hits on a completely different site?

---

### Post by s|k on 2006-03-22
What are you talking about?

---

### Post by aysiu on 2006-03-22
From [the DistroWatch FAQ](http://distrowatch.com/dwres.php?resource=faq): > It is a lighthearted way of looking at a popularity of any given distribution. Since each distribution has its own page, I decided to track the number of visitors viewing individual web pages. The HPD figure represents hits per day by unique visitors, the emphasis being on the word unique; the uniqueness is determined by the visitor's IP address. This prevents those visitors, not disciplined enough, from rigging the results by reloading the pages multiple times. The idea is to identify which distributions attract most attention and to rank them accordingly. This also introduces an element of competition and competitions are fun, aren't they? Admittedly, the page clicks by themselves may not always reflect the popularity correctly. They are also "seasonal", meaning that distribution currently in beta testing will often receive much more clicks than the one past the stable release. All in all, these numbers should, over time, provide an indication about the popularity of Linux distributions.

These rules have been implemented to prevent various counter reloading schemes:

    * Repeated page and counter reloads in short or regular intervals are not allowed. If you are inclined to set up cronjobs to repeatedly wget your favourite distro's page counter, then please do yourself a favour and go to see a psychologist. You need help.
    * All suspicious page hit counts will be investigated and any regularly reloaded counts will be deducted from the total count.
    * The repeat offender's IP address will be banned from accessing all areas of DistroWatch, including mirrors, for a period of 30 days.

---

### Post by lee_connell on 2006-03-22
Thanks for the reply.

I still don't understand how DW monitors says fedora.redhat.com, opensuse.org, ubuntulinux.org etc...

Does DW count page hits that originate from DW only?

If that's the case, I understand how it's done, if not then those page hits are most likely very unaccurate and was just curious how it was accomplished.

---

### Post by digby on 2006-03-22
It's counting the number of hits on each distro's page on distrowatch (eg. distrowatch.com/ubutntu, distrowatch.com/suse, etc.).  It's not at all reflective of the number of hits to each distro's official page.

---

### Post by lee_connell on 2006-03-22
thanks!

---

