---
title: "Password padding"
date: 2012-04-10
forum: The Cafe
---

### Post by bedpotato on 2012-04-10
Recently I stumbled across the concept of password "padding." I had never heard of it before and I found it very interesting.

[https://www.grc.com/haystack.htm](https://www.grc.com/haystack.htm)

(scroll down link for comparison between two examples)

Does that really mean that if I picked the word "red" for example, and turned it into this:

R3d&&&&&&&&&&&&&&&&&&&&&&&&

it would be just as secure as a more complex passphrase? 

This padding technique only seems to take into account *how many* characters the password consists of. 

Shouldn't we be worried about also using as many *different characters* as possible? Or is it enough to cover all four kinds (upper case, lower case, symbol, and number)?

The author of that article seems to think so, but I don't know how password cracking software works, so I don't know.

Please can someone enlighten me?

Edit: the article calls it "entropy." That's a new concept to me as well! Can any clever people explain which is best: high entropy or long length? :)

---

### Post by Grenage on 2012-04-10
Effectively, length makes it secure, and you still have to try the same number of permutations when you don't know the characters in the password.

I would, however, never recommend grc.com for information; that fellow is a joke.

---

### Post by bedpotato on 2012-04-10
> **Grenage said:**
> Effectively, length makes it secure, and you still have to try the same number of permutations when you don't know the characters in the password.

I would, however, never recommend grc.com for information; that fellow is a joke.

Oh, thank you. I haven't read the rest of the page, so I don't know who wrote it; I just stumbled across that one article in a Google search and found it interesting.

So what you're saying is that it doesn't matter if you repeat one character lots of times. Is that correct?

Edit: here's another question. Can machines detect dictionary words if you substitute the vowels for symbols? (As in "r3d" and "d0g" in the example on that webpage). 

Would "g3tl0sth$ck3rs" actually be any more secure than "getlosthackers?"

---

### Post by Megaptera on 2012-04-10
A slight detour, but I find this site useful for selecting p/w:
(and there aren't just 10 p/w per line)

"A PasswordCard is a credit card-sized card you keep in your wallet, which lets you pick very secure passwords for all your websites, without having to remember them! You just keep them with you, and even if your wallet does get stolen, the thief will still not know your actual passwords." [http://www.passwordcard.org/en](http://www.passwordcard.org/en)

---

### Post by bedpotato on 2012-04-10
> **Megaptera said:**
> A slight detour, but I find this site useful for selecting p/w:
(and there aren't just 10 p/w per line)

"A PasswordCard is a credit card-sized card you keep in your wallet, which lets you pick very secure passwords for all your websites, without having to remember them! You just keep them with you, and even if your wallet does get stolen, the thief will still not know your actual passwords." [http://www.passwordcard.org/en](http://www.passwordcard.org/en)

That's all very well but what if you lose the card? I'm sure that's a great idea for many people though. Everyone has their own ways of doing things. Personally I would rather keep my passwords safely inside my head (or in my safe). :) 

Also that card system seems to require you to invent lots of brand new, random passwords. I can't remember multiple, genuinely random passwords. I'd rather invent one algorithm and remember it to create multiple, *apparently* random passwords. :)

---

### Post by Grenage on 2012-04-10
> **bedpotato said:**
> Would "g3tl0sth$ck3rs" actually be any more secure than "getlosthackers?"

Yes and no; someone cracking the password would need to know that you'd included (or omitted) characters in order to use/skip them in any brute force attempt.  If they were to assume that no special characters were used, then they would discover your password more quickly.  When I say quickly, we are talking relatively.

---

### Post by bedpotato on 2012-04-10
> **Grenage said:**
> Yes and no; someone cracking the password would need to know that you'd included (or omitted) characters in order to use/skip them in any brute force attempt.  If they were to assume that no special characters were used, then they would discover your password more quickly.  **When I say quickly, we are talking relatively**.

As in, 3 million years as opposed to 25 billion?

(Those are the kind of weird results it always comes up with on those strength checker websites).

---

### Post by Grenage on 2012-04-10
Well computers can be rather fast at thrashing passwords, but you'll generally have a limiting factor.  I'd be lying if I said that my passwords were not intricate - it really can't hurt to increase their complexity.

---

### Post by haqking on 2012-04-10
You may enjoy reading some posts i made a few weeks back in a thread about whether a PC had been hacked or not

this is the thread [http://ubuntuforums.org/showthread.php?t=1943036](http://ubuntuforums.org/showthread.php?t=1943036)

This is my post #16

[http://ubuntuforums.org/showpost.php?p=11791296&postcount=16](http://ubuntuforums.org/showpost.php?p=11791296&postcount=16)

and onwards between me and Dangertux explains entropy

A topic came up in the thread about security of passwords and in comparison length vs complexity.

length overall is more secure than complexity due to information entropy, but both would be better of course from a brute force point of view.

Peace

---

### Post by bedpotato on 2012-04-10
Thank you Haqking. I remember reading that thread, but not really understanding it. :redface:

---

### Post by Megaptera on 2012-04-10
Yes, I agree it's not a system for everyone but it's just worth mentioning to stop peoplefrom  picking "password" etc.  :p

> **bedpotato said:**
> That's all very well but what if you lose the card? 
Quote from site "This is the number of your card. Store it somewhere safe! If you want to regenerate a card you lost, type the number here and press Enter:"  So it can be rescued :p

---

### Post by bedpotato on 2012-04-10
That's good, megaptera! :) It's certainly an ingenious idea! 

Just to clarify my original post: I wasn't really thinking of using "padding" for online account passwords, which normally have a relatively short maximum length anyway, so I just use an algorithm. Rather, I was thinking about using padding for encryption passwords, which have to be very long (say 50 characters). 

I like using Truecrypt, and I made very long passwords using song lyrics and taking the first letter of every word. I think padding would be a much easier way and save me typing it in wrongly all the time, but I don't think you can change a Truecrypt password once you've created the volume, can you? :( I think decrypting and recrypting (sp?) 1 terabyte just to change the password to something else is not worth the hassle!

---

