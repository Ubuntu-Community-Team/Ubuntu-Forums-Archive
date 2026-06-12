---
title: "test this little site please (converts temperature units)"
date: 2007-09-21
forum: The Cafe
---

### Post by LaRoza on 2007-09-21
[http://laroza.freehostia.com/home/calculator/](http://laroza.freehostia.com/home/calculator/)

It is written in client side ECMAScript, and I tried to make it useable, let me know what you think.

IE6 handle it weird, visually, but otherwise works. FF, Opera, Safari, and IE7 handle it fine.

Feedback appreciated.

Thanks.

---

### Post by aaaantoine on 2007-09-21
I can type 123-45 in there, and it will accept (and convert) the first part of the number.

Maybe you want to evaluate the input box with a regex that goes something like this:

/$[0-9](.[0-9])?^/

Or however it goes.  I'm not exactly sharp with Regular Expressions.

Though if you go down this path, maybe you also want to ignore whitespace:

/$[ ]*[0-9](.[0-9])?[ ]*^/

...And trim it out when you run the conversion.

---

### Post by LaRoza on 2007-09-21
> **aaaantoine said:**
> I can type 123-45 in there, and it will accept (and convert) the first part of the number.


I didn't want to make it too restrictive, validation can be a difficult thing to do right, but the general rule is to not be too restrictive.

Right now, it looks for numbers at the beginning of the input, and uses those (parseFloat). It also round answers to the nearist integer, which I might change to increase precision.

Thanks, I will look into re for validation, and trimming whitespace is a good idea.

(I wrote this last night, out of boredom and because I often wish to put temps on this forum, but don't want to alienate anyone, so use C and F.)

---

### Post by slimdog360 on 2007-09-21
try putting in > 8 )and converting to and from centigrade. You should make it check each character.

---

### Post by LaRoza on 2007-09-21
> **slimdog360 said:**
> try putting in and converting to and from centigrade. You should make it check each character.

Overvalidation is not a good thing.

Putting in non-numerical characters will not give warnings or errors if there are leading numbers.

The main thing for me was not to have "NaN" show up in the conversion field. I can make it throw errors if any character is invalid, but what if someone copies a temp from a website, like 20 ° C, and puts it in? It will convert it because of the leading 20

---

### Post by Sporkman on 2007-09-21
It worked once for me, then stopped working (just toggles between F & C).

Also, when I hit refresh, a bright red message about JavaScript not working flashes momentarily then disappears (though my javascript is on & is fine)...

---

### Post by Biochem on 2007-09-22
I can only do one conversion. After, the bouton are sheded and become useless. The need to refresh would probably be considered an annoyance.

Negative number and 0 don't work. If you don't know what -20 °C feels like I really envy you.

---

