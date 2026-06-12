---
title: "About the BSOD screen saver"
date: 2006-04-19
forum: The Cafe
---

### Post by halfvolle melk on 2006-04-19
This great screen saver is the only one used here and I am amused each and every time it springs into action. (But) there's one SOD, I think it's a linux one, that prints an ASCI dog saying something like "Your system ate a SPARC. Gah!". Could someone explain what that's about so I can laugh at that as wel? ;)

---

### Post by Nequeo on 2006-04-19
[QUOTE=halfvolle melk]This great screen saver is the only one used here and I am amused each and every time it springs into action. (But) there's one SOD, I think it's a linux one, that prints an ASCI dog saying something like "Your system ate a SPARC. Gah!". Could someone explain what that's about so I can laugh at that as wel? ;)[/QUOTE]

Dunno the History - but it seems to be a Kernel error message:

[http://lists.parisc-linux.org/pipermail/parisc-linux/2002-November/018252.html](http://lists.parisc-linux.org/pipermail/parisc-linux/2002-November/018252.html)

---

### Post by halfvolle melk on 2006-04-19
Hehe, nice. Thanks.

---

### Post by Nequeo on 2006-04-19
[QUOTE=halfvolle melk]Hehe, nice. Thanks.[/QUOTE]

Np. Was intrigured enough to look into it a little more. Can only find mentions of that error message in relation to PA-RISC linux ([http://www.parisc-linux.org/)](http://www.parisc-linux.org/)). Btw, pretty sure it's a cow, not a dog :)

Looks very much like the 'cowsay' program to me. Which is in Ubuntu, too! Just 'apt-get install cowsay'. It's in the Universe repo. I use it for displaying fortunes in Bash.

---

### Post by halfvolle melk on 2006-04-19
[QUOTE=Nequeo]Can only find mentions of that error message in relation to PA-RISC linux ([http://www.parisc-linux.org/)](http://www.parisc-linux.org/)).
Btw, pretty sure it's a cow, not a dog :)[/QUOTE]
I'm no ASCI artist but that's a louwsy cow :)
> Looks very much like the 'cowsay' program to me. Which is in Ubuntu, too! Just 'apt-get install cowsay'. It's in the Universe repo. I use it for displaying fortunes in Bash.
Erm ... I'll look into that. I'm quite 'new'. Thanks for the suggestion though!

---

### Post by Wallakoala on 2006-04-19
wow this screensaver is awesome

---

### Post by endersshadow on 2006-04-19
FYI-SPARC is Sun's version of the RISC instruction set.  It's on UltraSPARC right now.  You can find them [here](http://www.sun.com/processors/UltraSPARC-IVplus/index.xml)...but I don't know what the cow means...

---

### Post by halfvolle melk on 2006-04-19
Hmm, ok. I thought SPARC was an architecture, a chip. Or is it?

edit: sorry, silly question.

---

### Post by nighttime on 2006-04-19
Haha, I love the BSOD screensaver! I even got a little panic adrenaline rush from seeing it once when I was getting back from the restroom lol.

---

### Post by richardward101 on 2006-04-20
Loving cowsay!

---

### Post by gxam on 2008-09-24
I think I can shine some light in there.

The error message originated from me (Markus "Max" Grabert) back in 2003.
I tried to get a standard IDE PCI controller working in my HP C3000 workstation. It worked with a 2.4 kernel (somewhat), but not with newer 2.6 kernels.

Here is the full kernel log: [http://www.cs.ucc.ie/~xam/siimage/bootlog-2.6.0-test11-pa2.txt](http://www.cs.ucc.ie/~xam/siimage/bootlog-2.6.0-test11-pa2.txt)

And here are the relevant postings in the parisc-linux kernel list:
[http://osdir.com/ml/linux.ide/2003-12/msg00038.html](http://osdir.com/ml/linux.ide/2003-12/msg00038.html)
[http://ut.ag/urlweb.aspx?email=steve@fooworks.com&url=http%3A//lists.parisc-linux.org/pipermail/parisc-linux/2003-December/021839.html](http://ut.ag/urlweb.aspx?email=steve@fooworks.com&url=http%3A//lists.parisc-linux.org/pipermail/parisc-linux/2003-December/021839.html)

A couple of months later I was contacted off-list by someone who asked if he could use my kernel panic log for the BSOD screen saver. Of course I agreed :-)

---

### Post by 1oooop on 2010-03-10
wow, seems someone's famous... (I'm jealous) =D>=D>=D>=D>

---

### Post by sulfo on 2010-10-01
thanks for explaining, gxam :) now i feel there's one more question only you are qualified enough to answer: is it a dog or a cow? :wink:

---

### Post by cascade9 on 2010-10-01
> **sulfo said:**
> thanks for explaining, gxam :) now i feel there's one more question only you are qualified enough to answer: is it a dog or a cow? :wink:

I might not be qualified, but I'll answer anyway- 

\   ^__^
 \  (xx)\_______
    (__)\       )\/\
     U  ||----w |
        ||     || Cow. You can see her udder ;) Hey, maybe I should censor the udder, save a mod/admin the job.......breast for all concerned, otherwise there could be udder chaos. :lolflag: \   ^__^
\   ^__^
 \  (xx)\_______
    (__)\       )\/\
     U  ||----x |
        ||     ||[FONT=Verdana]

[/FONT] Fixed!

---

### Post by Elfy on 2010-10-01
closed - necro threaad

---

