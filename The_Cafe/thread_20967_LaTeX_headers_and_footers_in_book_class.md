---
title: "LaTeX headers and footers in book class"
date: 2005-03-19
forum: The Cafe
---

### Post by karih on 2005-03-19
Hello

First I would like to say that a forum section for "general problems" not related to Ubuntu would be nice :).  If I am posting in a wrong place however, I am sorry.

I am writing a small book in latex and have set up headers and footers to display page numbers and chapter titles in the header.
My problem is that when I start a new chapter it starts on an odd numbered page which sometimes makes a whole white page on the even numbered page and that page has headers/footers which IMO shouldn't be there and look very badly.  There must be a way to get rid of it but I don't see how.  Any ideas?

Thanks in advance!

---

### Post by karih on 2005-03-20
Nevermind, found the fix.
For those with the same problem:
```

\renewcommand{\cleardoublepage}
    {\clearpage\if@twoside \ifodd\c@page\else
    \hbox{}\thispagestyle{empty}\newpage\if@twocolumn\hbox{}\newpage\fi\fi\fi}

```

---

