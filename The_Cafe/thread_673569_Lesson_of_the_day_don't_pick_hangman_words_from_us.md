---
title: "Lesson of the day: don't pick hangman words from /usr/share/dict"
date: 2008-01-20
forum: The Cafe
---

### Post by jdong on 2008-01-20
So, I was writing a hangman game in Python for fun, and needed a wordlist. So I decided to use /usr/share/dict/words, which is the first thing that came to my mind when I needed a wordlist.

Well so let's write a word picking function. I thought the one I wrote was very efficient, scalable and beautiful:

```

def pick_word():
  def wc_l(file):
    count=0
    for line in file.xreadlines(): count +=1
    return count
  import random
  num_words=wc_l(open('/usr/share/dict/words'))
  import linecache
  word=linecache.getline('/usr/share/dict/words',
      random.randint(0,num_words-1)).strip()
  if len(word) > 1:
    return word
  else:
    return pick_word()

```

Ok, let's run it!

__r__rl_ss

Hmm, what is it, you ask? **vergerless**.  What does it mean? *shrug*

So I started looking through the list just to see what was in it, and a snippet from the first few lines:
> 
abacate
abacay
abacinate
abacination
abaciscus
abacist
aback
abactinal
abactinally


Ok, so I guess I should try to find a list of **common** words rather than using /usr/share/dict/words. 90% of the words in there I don't even recognize :D

---

### Post by dgray_from_dc on 2008-01-23
:lolflag:

---

### Post by tgalati4 on 2008-01-23
Makes for killer game of hangman.  The computer always wins!

---

### Post by fatality_uk on 2008-01-23
Class. :lolflag:

---

### Post by Namtabmai on 2008-01-23
Err you may want to check your dict word files.
Mine doesn't have that word in it, in fact more of the words look pretty sensible.

---

### Post by jdong on 2008-01-23
I wrote the code on my macbook (OS X 10.4.11) so we might have different dict/words :)

---

