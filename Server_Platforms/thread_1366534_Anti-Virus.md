---
title: "Anti-Virus??"
date: 2009-12-28
forum: Server Platforms
---

### Post by StrangeWill on 2009-12-28
Well we were hit by a pretty nasty virus lately, infected a bunch of files on our server, having to use a windows machine to clean it up was quite a bummer.
(Win32/Gaelicum.A, what a yummy virus)

I've wanted to go with ClamAV, but apparently it's kind of garbage. (It's nice for detecting, but I'd rather be able to clean files, not delete only)

Any recommendations for server quality command line AV software? I can get lists but I don't want to be installing and uninstalling AV software willy nilly. We run our own mail server and I'd like to scan that too, so something that plugs in with postfix easily would be great.

---

### Post by noway2 on 2009-12-28
Avast is pretty highly regarded and has a Linux version too.  If I recall correctly, though it has been a while since I looked, it will plug into Postfix.  What you will probably want to do is use the program called Amavis, or rather Amavis-new.  It makes insertion of an anti-virus into postfix very easy.

---

### Post by StrangeWill on 2009-12-29
> **noway2 said:**
> Avast is pretty highly regarded and has a Linux version too.  If I recall correctly, though it has been a while since I looked, it will plug into Postfix.  What you will probably want to do is use the program called Amavis, or rather Amavis-new.  It makes insertion of an anti-virus into postfix very easy.

I think I remember hearing about Avast on Windows, though I don't remember seeing it's detection rates... it's pretty robust I'm guessing, yes?

$15/year is a steal, makes me buy it in 10 year chunks (err... I think... or 10 licenses :confused: ) For the most part I guess you only really need this on your file and mail server (or a server that is setup to scan other servers).

---

### Post by doas777 on 2009-12-29
there is also bitdefender (free with registration). 

many viruses cannot be "cleaned/disinfected". depends on the strain and what file got infected. more tools may not be the answer in this case.

---

### Post by StrangeWill on 2009-12-29
> **doas777 said:**
> there is also bitdefender (free with registration). 

many viruses cannot be "cleaned/disinfected". depends on the strain and what file got infected. more tools may not be the answer in this case.

That is fine, I just knew there were tools that were cleaning the virus we had, and that ClamAV can't clean anything period. I don't mind if the files are uncleanable and therefore must be deleted/quarantined. 

Thanks I'll go research both of these and see which will be my best bet. :)

---

### Post by Vegan on 2009-12-29
AVG has a version for Linux but I have not been successful to get it working.

---

