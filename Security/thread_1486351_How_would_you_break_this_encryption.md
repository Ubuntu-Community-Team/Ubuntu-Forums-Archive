---
title: "How would you break this encryption?"
date: 2010-05-17
forum: Security
---

### Post by Ulysses_ on 2010-05-17
Say we scan a physical English dictionary and use OCR to convert it all to text, except some pages picked at random. We isolate the first word of each entry and add it to a list. Now we have a list of words from English that is very rich, except some words are missing. We make a duplicate of the list and shuffle it using a true random number generator.  Messages can be encrypted by simply replacing each word in the plaintext with the word in the shuffled list that is at the same position as the word in the original list.  The statistics of English words are known, so I guess with plenty of encrypted text one can establish the two lists and break the encryption.  But how is this done? Doesn't the fact that the list is incomplete make it harder to break?

---

### Post by Agent ME on 2010-05-17
Most sentences start with "The". "A" is also used a lot. If some words were repeated a lot, and especially if the attacker had some clue on what the message was about already, some words could be discovered. Also, that doesn't seem to give any method to encrypting numbers or non-dictionary words.

And that's a lot of work to do when there are already many better and proven methods available. Using a symmetric cipher with a long passphrase or even a one-time-pad seems feasible if you were already planning on carrying around a shuffled dictionary of words. Public key cryptography could work even better depending on how exactly the people were communicating with each other.

---

### Post by anomie on 2010-05-18
I'm going to have to agree with the last guy. There are well-established symmetric encryption ciphers (e.g. AES!) that have been run through the full range of analyses/attacks and thoroughly vetted. 

What you are proposing would definitely be a fun experiment, but I wouldn't use it for anything that your finances or your safety depend on.

---

### Post by Ulysses_ on 2010-05-18
Thanks, I am fully aware this is breakable, that's what the title implies.  But I have forgotten how this is done, and looking for a reminder, don't want to actually use this scheme.    It seems that text encrypted this way is unlikely to be fully broken by word frequency analysis alone, there must be better tricks.  Cause how on earth can the frequencies of words in two long texts (the message and the sample of the subject matter) be identical? Surely there would be plenty of differences.

---

### Post by Peter09 on 2010-05-18
Not an expert here --
 
This is similar to the 'one time pad' that I believe was used during the war (1940s). The agent was given a note book. On each page was a list of numbers which he used to translate from plain text to code. (not sure of the exact mechanism). After each message he destroyed the current page and moved on to the next which had a different set of numbers.
 
The weakness was
 
Both transmitter and reciever needed to have identical pads and be on identical pages.
It took some time to encrypt and decrypt the message (most probably not relavent today)
If the pad fell into enemy hands then they would also be able to encrypt/ decrypt messages.

---

### Post by VeeDubb on 2010-05-18
I really can't see any way to break that other than intercepting the key or word analysis.

If you did this as literally as you laid it out, and we're talking about paper here, I can't imagine any other options.

Analyze the words, sentence structure, repeated patterns.  Sort of reminds me of sudoku.  Every time you figure out a position, you reduce the possible values of the other positions. You figure out "a" and "the" (as pointed out) and you know that the words following them will be nouns.  Figure out a few of the conjunctions, and pretty soon all you're left with is the nouns and verbs.

Of course, even at that, unless you have some clue as to the overall topic being discussed, you'll get to a point where there is an infinite variety of possible outcomes, (okay, not infinite, but uncountably large) sort of like a deranged mad-libs.  With no known nouns and verbs, you could be reading a pornographic novel just as easily as you could be reading a battle plan.

---

### Post by Ulysses_ on 2010-05-18
What if you shift each word in the alphabetical list by N places where N = 1 for the first word in the plaintext, N = 2 for the second word in the plaintext, etc and then move to the shuffled list.  Then any patterns repeated in the plaintext are not repeated in the encrypted text, there's no pattern repetition or sentence structure.  What do you do then.

---

### Post by Peter09 on 2010-05-18
Looking at how the enigma code was broken was dependent of knowing things like
 
- The transmission always started with an identification string which was the same for each station.
- Looking at things that were likely to crop up such as names, incidents, weather conditions etc
 
In the end just mass substitution, looking for sentences which came out and made sense.
 
I guess, in the end, your code would fall to mass substitution. Put it into a computer and churn it around with potential lists of words, perhaps saving configurations that produced a valid sentence etc.

---

### Post by teh_drizzle on 2010-05-18
This sounds like a homework problem, hehe. 

I think the most suitable solution is indeed frequency analysis. As posted above, the frequency chart for a natural language can be established exactly as you've described (using the correct OCR). The bit about missing pages is semi-trivial, it does not effect the frequency distribution. If you are still selecting from the entire English language when constructing plain-text it does create a wrap-around possibility. Since your selection is not one-to-one you'll have to do minor natural language processing where multiple mappings exist occur.

---

### Post by Ulysses_ on 2010-05-18
> **teh_drizzle said:**
> If you are still selecting from the entire English language when constructing plain-text it does create a wrap-around possibility. 

I do not understand, could you rephrase this? 

> **teh_drizzle said:**
> The bit about missing pages is semi-trivial, it does not effect the frequency distribution.  Missing columns of the frequency distribution do not make a difference?  Here's why I think missing pages make a non-trivial difference: a few missing words can spoil the entire mapping the adversary sees. Explaining: Say the full dictionary has these 7 words: alpha, beta, gamma, delta, epsilon, zeta, eta, with these frequencies in the subject matter:  

1. 14313 epsilon 
2. 13328 beta 
3. 11211 theta 
4. 9872  alpha 
5. 8211  eta 
6. 6543  zeta 
7. 3211  gamma  

If the frequencies of a long ciphertext using 4 words (for the sake of argument) are like this:  

1. 123 eta 
2. 111 gamma 
3. 96  epsilon 
4. 12  zeta  

Then the adversary derives this mapping:  

1. epsilon -> eta 
2. beta -> gamma 
3. theta -> epsilon 
4. alpha -> zeta  

Which may well be the correct mapping. But if the dictionary is missing 2 words, say:

2. beta 
7. gamma  

and these words are simply deleted from the plaintext (to be guessed by a legitimate reader or even converted to individual letters or something), then the adversary sees these frequencies:

1. 123 eta 
2. 96  epsilon 
3. 12  zeta  

and the adversary thinks the mapping is  

1. epsilon -> eta          (correct)
2. beta -> epsilon  **(incorrect)** 
3. theta -> zeta     **(incorrect)**  

In other words, **a few missing words can spoil the entire mapping starting from the first missing word**.

---

### Post by rookcifer on 2010-05-19
> **Peter09 said:**
> Not an expert here --
 
This is similar to the 'one time pad' that I believe was used during the war (1940s). The agent was given a note book. On each page was a list of numbers which he used to translate from plain text to code. (not sure of the exact mechanism). After each message he destroyed the current page and moved on to the next which had a different set of numbers.
 
The weakness was
 
Both transmitter and reciever needed to have identical pads and be on identical pages.
It took some time to encrypt and decrypt the message (most probably not relavent today)
If the pad fell into enemy hands then they would also be able to encrypt/ decrypt messages.

A one-time pad is the only 100% provably unbreakable encryption scheme.  The problem with it is the key has to be as long as the plaintext, thus making it impractical to use in most scenarios.  But it is provably unbreakable (if implemented properly).

---

### Post by teh_drizzle on 2010-05-19
> **Ulysses_ said:**
> 
[QUOTE=teh_drizzle;9321122]If you are still selecting from the entire English language when constructing plain-text it does create a wrap-around possibility.
I do not understand, could you rephrase this? [/QUOTE]

Sure no problem. :) 

The original problem stated:

"Say we scan a physical English dictionary and use OCR to convert it all to text, except some pages picked at random. We isolate the first word of each entry and add it to a list. Now we have a list of words from English that is very rich, except some words are missing."

There are two possibilities here,
A) The plain-text is selected entirely from the "very rich", albeit missing pages worth of entries, constructed list.
B) The plain-text can be constructed from any English word, including those missing from the OCR'ed list.

When considering B, a one-to-one mapping does not exist. This leaves some possibilities without corresponding frequencies. If considering A, then there is a one-to-one mapping and no extra work is required. 

I made a mistake here and figured natural language processing could consult the mapped frequency choice appended with the dropped entries as possible plain-text candidates.

> **Ulysses_ said:**
> In other words, **a few missing words can spoil the entire mapping starting from the first missing word**.

Right :)

---

### Post by Ulysses_ on 2010-05-19
Option B. seemed a second problem with trivial solutions like 
"delete unknown words and let the recipient guess them" or 
"let the recipient ask the sender to rephrase sentence 6 because a critical word is missing" or 
"replace unknown word by letters separated by spaces and include letters a-z in the dictionary".

I propose that this method does not suffer from the one-time constraint of the one-time pad because unlike the one-time pad, given two messages encoded with the same key it is not trivial to derive the key with this method. Word frequencies would only derive part of the mapping, just from the start to the first missing word, the rest of the mapping would still be unknown.

Also that you need a supercomputer to fully break this and derive the full mapping, because you'd need to try an astronomical number of mappings in search of common phrases or grammatical patterns until you find a mapping that has optimal results (eg maximum number of common phrases and grammar) and call it the optimal mapping.

---

### Post by Peter09 on 2010-05-19
There are many other solutions to this which are equally as good. For instance selecting a book (say war and peace) and encoding your message by giving the page number and line number and position in the line of the word that you want. This is unbreakable as long as the 'enemy' does not know which book you are using.

The power of modern encryption mechanisms is that the 'encryptor' cannot decode the encrypted message - even the one that he just encrypted. 

This means that even if the 'enemy' discovers the encryption codes he cannot decrypt any message. So you can give the same encryption codes to all your agents knowing that, even if one is captured and gives away the codes, other agents messages are still a mystery to the enemy.

---

### Post by faargenwelsh on 2010-05-20
if you use a word-based method of encryption instead of a letter-based  method of encryption, the frequency distribution will be much less an  issue. 

i mean, the frequency of an "e" or a "t" is more or less comparable from one text to another (be it poetry, bible, university textbook or a dictionary), while the frequency of any particular word depends very heavily on the nature of text encrypted. therefore, there's no really such thing as a "word's frequency distribution index", at least until the nature of the encrypted text is not reasonably assessed. 

also, while the alphabet counts only 26 letters, the oxford dictionary of english language has about 128.000 different words... 

thus, provided that 1/ the message is short, 2/ its intrinsic entropy is high and 3/ the encryption scheme is used only once, i see no single chance for an interceptor to decipher it.

UPD : just to illustrate - take a sentence such as "fsck the fscking fsckers" ; this is theoretically breakable with most of the letter-substitution cryptographic systems, for obvious reasons ; but if the substitution scheme is word-based and the words fsck, fscking and fsckers constitute different dictionary entries - well... it's unbreakable

---

