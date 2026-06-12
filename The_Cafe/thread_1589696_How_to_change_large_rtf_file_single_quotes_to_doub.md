---
title: "How to change large rtf file single quotes to double quotes"
date: 2010-10-06
forum: The Cafe
---

### Post by josephellengar on 2010-10-06
Hello.  I have a strange question that I couldn't really figure out where else I should put it.  Anyway, does anybody know of a way that I can take a large rtf file and convert all of the single quotes: ' to double quotes: " without messing up apostrophes and whatnot?  It's a project Gutenberg ebook and, as a Yankee, I really like my quotes double.  So, does anybody know how?  Thanks!

---

### Post by mkendall on 2010-10-06
Find [space]' and replace with [space]"

Repeat with '[space] and "[space]

On the latter you only have to watch out for possessives that end with an 's' like "Charles'"

---

### Post by josephellengar on 2010-10-06
> **mkendall said:**
> Find [space]' and replace with [space]"

Repeat with '[space] and "[space]

On the latter you only have to watch out for possessives that end with an 's' like "Charles'"

Wow.  I was thinking about regular expressions and whatnot.  :oops:  How simple.  Okay, what do I do when the quote is at the beginning of a paragraph?  I can't replace [whitespace]' with [whitespace]" because that gets rid of the paragraph break.  And I tried replace manual newline and paragraph marker, but Word found none.  So the situation is
This is a sentence with a break.
'This is a new sentence.'

Doesn't have a space at the beginning.  Any idea?  Thanks so much for your help!

---

### Post by josephellengar on 2010-10-06
> **rossholley said:**
> Wow.  I was thinking about regular expressions and whatnot.  :oops:  How simple.  Okay, what do I do when the quote is at the beginning of a paragraph?  I can't replace [whitespace]' with [whitespace]" because that gets rid of the paragraph break.  And I tried replace manual newline and paragraph marker, but Word found none.  So the situation is
This is a sentence with a break.
'This is a new sentence.'

Doesn't have a space at the beginning.  Any idea?  Thanks so much for your help!

Got it.  I just had to use the special character "paragraph mark."  Thank you so much for your help!

---

