---
title: "Fun with Google Translate!!!"
date: 2009-06-23
forum: The Cafe
---

### Post by hkbruvold on 2009-06-23
I made a simple python-program to translate text from English to Japanese and back again. When you translate text from a language to Japanese and back you'll get a funny sentence.

Here is an example:

> text: hello, what the hell are you doing today
number: 5
Hi, I was doing

Here it is translating the text to Japanese and back to English 5 times.


Here is the code:
```
#! /usr/bin/python

from urllib2 import urlopen
from urllib import urlencode
import sys

# The google translate API can be found here: 
# http://code.google.com/apis/ajaxlanguage/documentation/#Examples

def translate(source_lang, target_lang, text):
    lang1=source_lang
    lang2=target_lang
    langpair='%s|%s'%(lang1,lang2)
    text=''.join(text)
    base_url='http://ajax.googleapis.com/ajax/services/language/translate?'
    params=urlencode( (('v',1.0),
                       ('q',text),
                       ('langpair',langpair),) )
    url=base_url+params
    content=urlopen(url).read()
    start_idx=content.find('"translatedText":"')+18
    translation=content[start_idx:]
    end_idx=translation.find('"}, "')
    translation=translation[:end_idx]
    return translation

text2 = raw_input("text: ")
try:
    times = raw_input("number: ")
    times = int(times)
except:
    print "you need to give me a number!"

for x in range(times):
    text1 = translate('en', 'ja', text2)
    text2 = translate('ja', 'en', text1)

    print text2
```


This is a modification of a code from the thread:
[http://ubuntuforums.org/showthread.php?t=1087457](http://ubuntuforums.org/showthread.php?t=1087457)

EDIT: Made the code print each translation.

---

### Post by Artisten on 2009-06-23
Haha, good idea!

Here is my test:
> text: chess is a complicated board game
number: 5
This is a complex game of chess board


Finally some fun out of Google's grammar mistakes:D

Anyone else getting funny results?

---

### Post by sisco311 on 2009-06-23
:)

> text: Hey, you've got a banana in your ear! What? I said, YOU'VE GOT A BANANA IN YOUR EAR!What? I can't hear you; I've got a banana in my ear!


**number: 1**
Hey, have you heard of a banana! What? I will have a banana in your ear! What? I can not hear you. In my ear I have a banana!

**number: 2**
Hey, I heard the story of the banana! What? I have a banana in your ear! What? I can not hear you. I hear I have a banana!

**number: 3+**
Hey, I heard the story of the banana! What? I have a banana in your ear! What? I can not hear you. I hear the banana!


---

### Post by Sealbhach on 2009-06-23
text: may I borrow your wife?
number: 1
What may I borrow your wife?

text: may I borrow your wife?
number: 2
Does your wife, I can borrow?

text: may I borrow your wife?
number: 3
Your wife, or can I borrow?

.

---

