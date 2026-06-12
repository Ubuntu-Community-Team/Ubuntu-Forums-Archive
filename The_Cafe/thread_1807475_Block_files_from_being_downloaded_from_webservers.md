---
title: "Block files from being downloaded from webservers"
date: 2011-07-19
forum: The Cafe
---

### Post by vehemoth on 2011-07-19
I found this interesting article written by Richard Stallman, [http://www.gnu.org/philosophy/javascript-trap.html](http://www.gnu.org/philosophy/javascript-trap.html)
So has anything changed from then, is there now an extension to block files from downloading.
If not how could it be done?
and please no arguing about you know what, just nice friendly discussions

---

### Post by jhonan on 2011-07-19
It's easy enough to block Javascript. What he seems to be talking about in that article is getting selective about running browser-based programs (Java, JavaScript, Flash, Silverlight) based on how free they are.

My interpretation is that he wants some way of identifying if the code is 'free' before running it in the browser. And by free he also means non-obfuscated sourcecode, with proper comments and whitespace.

---

### Post by vehemoth on 2011-07-19
I was seeing the problem as how do you replace the javascript etc with your own version whilst blocking the one that the page came with.
If you can do that, then I think you can be on your way to solving the problem.

---

### Post by juancarlospaco on 2011-07-19
Thats not true..., compacted code still being source code, 
with enought skills you can give back its Whitespaces, comments, and blank lines,
im just learning JS and im able to compact and reverse the JS code.

You replace the javascript with your own version, its not hard.
Random example: drop a new line into your /etc/hosts file,
pointing [www.anywebsite.com/script.js](www.anywebsite.com/script.js) to localhost/MyOwnCustom.js

also ECMAScript != JavaScript != JavaApplets
:D

---

### Post by alphacrucis2 on 2011-07-19
Seems to be overzealous to me. A solution looking for a problem.

---

### Post by juancarlospaco on 2011-07-19
> **alphacrucis2 said:**
> a solution looking for a problem.

**+1**   &#664;&#9184;&#664;

---

### Post by jerenept on 2011-07-19
> **vehemoth said:**
> I was seeing the problem as how do you replace the javascript etc with your own version whilst blocking the one that the page came with.
If you can do that, then I think you can be on your way to solving the problem.

[This?]("https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/")

---

### Post by vehemoth on 2011-07-20
> **juancarlospaco said:**
> Thats not true..., compacted code still being source code, 
with enought skills you can give back its Whitespaces, comments, and blank lines,
im just learning JS and im able to compact and reverse the JS code.
:D
With enough skill you can decompile a program into assembly and then into a higher level language.

> **jerenept said:**
> [This?]("https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/")
The author of the article was worried that the script might start running before replaced by greasemonkey.

Yeah sorry for not being clear to start off with and maybe not right through.

---

### Post by jerenept on 2011-07-20
> **vehemoth said:**
> With enough skill you can decompile a program into assembly and then into a higher level language.


The author of the article was worried that the script might start running before replaced by greasemonkey.

Yeah sorry for not being clear to start off with and maybe not right through.

Decompile into assembly? You seem to misunderstand what assembly language is.

---

### Post by vehemoth on 2011-07-20
It's pretty much more easily read binary is it not.

---

### Post by unknownPoster on 2011-07-20
> **vehemoth said:**
> It's pretty much more easily read binary is it not.

Not even close.

Read this: [http://en.wikipedia.org/wiki/Assembly_language](http://en.wikipedia.org/wiki/Assembly_language)

---

### Post by vehemoth on 2011-07-20
> **unknownPoster said:**
> Not even close.

Read this: [http://en.wikipedia.org/wiki/Assembly_language](http://en.wikipedia.org/wiki/Assembly_language)
Thank you for clarifying that :)

---

### Post by BeRoot ReBoot on 2011-07-20
Fun fact: Non-obfuscated GPL code is, on average 15 Stallmans more free than obfuscated GPL code.

---

### Post by juancarlospaco on 2011-07-20
obfuscated != compacted

---

