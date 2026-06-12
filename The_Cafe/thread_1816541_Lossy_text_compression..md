---
title: "Lossy text compression."
date: 2011-08-02
forum: The Cafe
---

### Post by firefish5000 on 2011-08-02
Hi, you may laugh if  you wish but do you know any lossy text compression programs?
If your wondering my reason for wanting one it is to show the difference between lossless and lossy in a way in which "normal" people would easily understand. (they do not quite 'get it' with JPEG images as an example) on the other hand, I may very well use it on the daily basis depending on how it works (if its changing it into something unreadable with its high compression ratio, chances are I will only use it for examples, if it makes it into something you would expect to receive in a text message or IM, I will probably use it for such purposes)
I was going to type some more information, but I have drifted off into wonderland again and the thought has reached the point of no return...

---

### Post by ve4cib on 2011-08-02
I don't know of any lossy general data compression algorithms, but you could probably make something that would do the trick.  Throw away all characters that make up less than 1% of the file or something simple like that.

You might also try really cranking up the compression on a JPEG if you haven't already.  A standard .jpg is pretty good for most people.  But if you take a nice-qualith 600x800 png or tiff image, and save a copy as a jpg with all of the compression levels set to maximum there will be a very obvious change to the image.

---

### Post by ve4cib on 2011-08-02
<duplicate post>

---

### Post by MadCow108 on 2011-08-02
probably the most obvious way is to convert text into sms language, which is lossy compression which still remains readable to some extent:
[http://en.wikipedia.org/wiki/SMS_language](http://en.wikipedia.org/wiki/SMS_language)
[http://www.nationaltextingregistry.us/acronym_listing/](http://www.nationaltextingregistry.us/acronym_listing/)

also droping al double leters and punctuation and replacing all words with their shortest synonyms will further reduce the size

---

### Post by jhonan on 2011-08-02
Remove all the vowels - The text is still barely readable.

```
tr -d [aeiouAEIOU] < old.txt > new.txt
```

---

### Post by ssam on 2011-08-02
good lossy compression is based on perception. eg removing detail that will not be noticed.

a lossy text compression would keep the same rough meaning of a sentence, but remove the subtler meaning. so you could make an algorithm that looks up each word in a thesaurus and replaces it with its shortest synonym.

so 'good compression algorithm' would be compressed to 'ace confining way'. this a bit shorter, but still means roughly the same thing. has many properties of a lossy algorithm. you can't get back to the original. you loose detail. and you will sometimes get strange artefacts.

---

### Post by juancarlospaco on 2011-08-02
i spprt ths dea

---

### Post by Npl on 2011-08-02
translate it into chinese, you will end up with 1 letter per word.

---

### Post by forrestcupp on 2011-08-02
> **jhonan said:**
> Remove all the vowels - The text is still barely readable.

```
tr -d [aeiouAEIOU] < old.txt > new.txt
```Y bt m t t. :)

> **Npl said:**
> translate it into chinese, you will end up with 1 letter per word.
Lol. But then you'd have to have a font set with 15 million characters. :)

I wonder what Chinese keyboards are like.

Edit: I know there are only about 6000 characters in everyday use. ;) Still, what is a keyboard like!

---

### Post by Erik1984 on 2011-08-02
> **forrestcupp said:**
> Y bt m t t. :)


Lol. But then you'd have to have a font set with 15 million characters. :)

I wonder what Chinese keyboards are like.

Edit: I know there are only about 6000 characters in everyday use. ;) Still, what is a keyboard like!

You made me curious with that question

[http://www.slate.com/id/2136726/](http://www.slate.com/id/2136726/)

> In the Peoples' Republic of China, most computer users type out their  Chinese in transliteration, using the standard Roman alphabet keys on a  QWERTY keyboard. To generate a character, you type out its sound  according to the same spelling system—called [Pinyin]("http://www.pinyin.info/readings/zyg/rules.html")—that  represents the name of China's capital with the word "Beijing." The  computer automatically converts the Pinyin spelling to the correct  Chinese characters on the screen.

---

### Post by Chronon on 2011-08-02
A Chinese coworker of mine told me that every word can be written with 4 keystrokes, so it's actually more efficient to type than English (though you have to carry around a rather complicated map in your head).

---

### Post by forrestcupp on 2011-08-02
> **Euroman said:**
> You made me curious with that question

[http://www.slate.com/id/2136726/](http://www.slate.com/id/2136726/)

It's kind of disappointing but not surprising that they are like that. I'd rather think of them all as being like this large Chinese keyboard.

[IMG]http://upload.wikimedia.org/wikipedia/commons/4/4f/Large_chinese_keyboard.jpg[/IMG]

---

### Post by AlphaLexman on 2011-08-02
Just have your students watch any episode of 'CSI: New York' or 'CSI: Miami'... [CSI_Lossless.jpg]("http://www.dailyacid.com/2009/10/csi-zoom-fail.html")

---

### Post by cgroza on 2011-08-02
> **AlphaLexman said:**
> Just have your students watch any episode of 'CSI: New York' or 'CSI: Miami'... [CSI_Lossless.jpg]("http://www.dailyacid.com/2009/10/csi-zoom-fail.html")
So they got a reflection on a screw from a camera 50 m away from the car... Does all this add up to anyone?

---

### Post by aaaantoine on 2011-08-02
> **cgroza said:**
> So they got a reflection on a screw from a camera 50 m away from the car... Does all this add up to anyone?

That's the joke, yes.

---

