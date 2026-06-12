---
title: "Can computers decipher these type of complex codes?"
date: 2011-06-10
forum: The Cafe
---

### Post by brawnypandora0 on 2011-06-10
Ok, this question might seem strange to you, but it raises an important question about computer science. The Zodiac killer who stalked the Bay Area in the late 60s and early 70s wrote four cryptic letters to newspapers. Here's an example of the only one that has been deciphered manually:

[http://en.wikipedia.org/wiki/Zodiac_killer#The_Zodiac_letters_begin](http://en.wikipedia.org/wiki/Zodiac_killer#The_Zodiac_letters_begin)

Notice how it contains multiple spelling mistakes on purpose, corresponding to continuous symbols with no spacing between any of them:

[http://www.google.ca/imgres?imgurl=http://files.abovetopsecret.com/images/member/f50ef9af4acf.gif&imgrefurl=http://www.abovetopsecret.com/forum/thread476796/pg1&usg=__bpNo1DrinmE4xKHs-BoSiCNY6Hs=&h=895&w=640&sz=24&hl=en&start=0&sig2=A3tCCKp438HYD63FwOEsSw&zoom=1&tbnid=bH0yGYVZn9VF6M:&tbnh=148&tbnw=106&ei=Bu7xTcaCLYPbiALjkbXqBw&prev=/search%3Fq%3Dzodiac%2Bkiller%2Bletter%26um%3D1%26hl%3Den%26safe%3Doff%26sa%3DN%26biw%3D1280%26bih%3D602%26tbm%3Disch&um=1&itbs=1&iact=hc&vpx=842&vpy=56&dur=384&hovh=266&hovw=190&tx=77&ty=133&page=1&ndsp=24&ved=1t:429,r:5,s:0]("http://www.google.ca/imgres?imgurl=http://files.abovetopsecret.com/images/member/f50ef9af4acf.gif&imgrefurl=http://www.abovetopsecret.com/forum/thread476796/pg1&usg=__bpNo1DrinmE4xKHs-BoSiCNY6Hs=&h=895&w=640&sz=24&hl=en&start=0&sig2=A3tCCKp438HYD63FwOEsSw&zoom=1&tbnid=bH0yGYVZn9VF6M:&tbnh=148&tbnw=106&ei=Bu7xTcaCLYPbiALjkbXqBw&prev=/search%3Fq%3Dzodiac%2Bkiller%2Bletter%26um%3D1%26hl%3Den%26safe%3Doff%26sa%3DN%26biw%3D1280%26bih%3D602%26tbm%3Disch&um=1&itbs=1&iact=hc&vpx=842&vpy=56&dur=384&hovh=266&hovw=190&tx=77&ty=133&page=1&ndsp=24&ved=1t:429,r:5,s:0")

Can a computer program someday solve the other three letters? If so, how quickly? What type of algorithm would it use? Of course, he could have just been scribbling nonsense with the other three.

---

### Post by Paqman on 2011-06-10
Another homework question?

---

### Post by brawnypandora0 on 2011-06-10
> **Paqman said:**
> Another homework question?

What do you mean?

---

### Post by ChipOManiac on 2011-06-10
It's a good question actually... If a computer could solve this it'd be pretty bad for a lot of criminals out there who act smart...

Maybe we CAN create a program like that... but it'd take a long time to build that... I.M.O. you'd need an A.I. that can think like a detective and be able to peice evidence from other cases together... It'll call for some serious pattern finding that goes on to a human level... Algorithms would be very complex...

But I.M.O. computers can never match the way a Human brain works (if it did guys like me lose their jobs)... This example itself is an act of sheer creativity: it's designed to be secretive and undechiperable, and we can never really tell what the Zodiac was trying to say.

It's confused the authorities for so long, I don't think a computer would be able to do it at all... even if it did... it'd create a lot of possibilites... even with an A.I. ... Since we're not sure about what even one character means... The possibilites are endless...

So 70% no and the rest yes

---

### Post by Barrucadu on 2011-06-10
The code was cracked by a human, as far as we know humans do not have super-Turing computation abilities, therefore a computer can crack the code.

However, whether the implementation is feasible or not&#8230;

**edit:** To expand further, his code is based on a set of rules (all codes are, if they weren't they'd just be random symbols). Assuming the symbols correspond to letters (the simpler case) symbol frequency can be used to guess which symbols correspond to which letters. From this, some plaintext could be extracted.
However, he was clever - he used many symbols for some letters, and included deliberate misspellings. Thus, the computer would have to be able to recognise misspelt words (more difficult, but entirely possible), and also be able to revise its symbol-frequency calculations to include *sets* of symbols. That is, I think, the most difficult step.

I should add that I don't know anything about cryptography, and what I've proposed is effectively a brute-force solution making use of some heuristics to narrow it down. There are almost certainly better ways.

---

### Post by ihendley on 2011-06-10
> **Barrucadu said:**
> Assuming the symbols correspond to letters (the simpler case) symbol frequency can be used to guess which symbols correspond to which letters.

An even better method is to look at all pairs of consecutive symbols x,y and see how likely y is to follow x for a given mapping to the english alphabet. See the introduction of [this paper [pdf]]("http://www-stat.stanford.edu/~cgates/PERSI/papers/MCMCRev.pdf").

---

### Post by 3Miro on 2011-06-10
Computers don't "solve" anything. Only people do that.

Computers are tools. If you can reduce a problem to a series of addition, subtraction, multiplication and division, then you can use a computer to do it very fast for you. Computers are incapable of doing anything other than the above 4 operations. 

A deciphering algorithm can be made to solve these problems, but it will probably have to make some assumptions.

---

### Post by Barrucadu on 2011-06-10
> **3Miro said:**
> Computers are incapable of doing anything other than the above 4 operations.

Strictly speaking, (normal) computers can only do logical operations, and all computable (in the theoretical sense of the word) problems can be reduced to logic.

---

### Post by earthpigg on 2011-06-10
> **brawnypandora0 said:**
> 
Can a computer program someday solve the other three letters? If so, how quickly? What type of algorithm would it use? Of course, he could have just been scribbling nonsense with the other three.

I don't think it would be especially difficult today to solve such a human-generated code, if anyone had the knowledge and inclination.

Brute force it, and alert the human any time a potential solution yields more than X of the top 1,000 used words in the English dictionary or (to hedge) more than X of the top 100 used words in the top 10 second languages spoken in the US.

---

### Post by KiwiNZ on 2011-06-10
Homework

---

