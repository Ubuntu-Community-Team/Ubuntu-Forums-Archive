---
title: "it would be nice to have a feature in firefox ..."
date: 2020-08-15
forum: The Cafe
---

### Post by Skaperen on 2020-08-15
it would be nice to have a feature in firefox that allows a local user script (e.g. an API) to carry out navigation (click on stuff, type in stuff, drag things around, scroll and pan), access and save stuff (HTML, style sheet, javascript, DOM), and view (pixels of entire screen) on the current page.  this would allow the script to work on a logged in page on sites with non-standard logins which can't be delivered with ordinary HTTPS libraries or require manual navigation to reach.

of course such a feature would have to be done with security in mind to prevent bad actors from navigating by bank account or spending my bitcoin.

---

### Post by &amp;KyT$0P# on 2020-08-15
Can't Firefox extensions already do almost all of this?

If you want to write such extension yourself, to use it you'll need either Firefox Developer Edition or [this Firefox build]("https://wiki.mozilla.org/Add-ons/Extension_Signing#Unbranded_Builds").

---

### Post by Skaperen on 2020-08-17
what language are extensions written in?  if Java or C++ or Perl then it won't be happening.  what i think all programs on the scale that users want to "script them", they should accept a secured Unix socket connection at any time and do everything over that.  requiring the script to be inside the process or start with the process is too limited.  it needs to be a well defined inter-process API.  then any language that can do networking can be used.

securing it might include starting it with an environment variable or other configuration telling it which ports to accept or keys to use.

---

### Post by pqwoerituytrueiwoq on 2020-08-17
so basically tampermonkey?
[https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/)

---

### Post by &amp;KyT$0P# on 2020-08-17
> **Skaperen said:**
> what language are extensions written in?

Usually Javascript and JSON for the code, HTML/CSS for the UI.  See [documentation]("https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions").

---

### Post by Skaperen on 2020-08-17
> **pqwoerituytrueiwoq said:**
> so basically tampermonkey?
[https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/)

i went there (and then on to the tampermonkey.net site) to look for API documentation to see how it can be used.  i could not find any.  so i cannot judge this.

---

### Post by Skaperen on 2020-08-17
> **halogen2 said:**
> Usually Javascript and JSON for the code, HTML/CSS for the UI.  See [documentation]("https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions").

it seems that my best choice will be to develop an extension.

my project is to improve the UI of the *ancestry.com* web site for myself and other paying users.  one lacking feature is the ability to copy or compare branches between trees.

---

### Post by math492m on 2020-08-18
yup would have been nice

---

### Post by pqwoerituytrueiwoq on 2020-09-13
> **Skaperen said:**
> i went there (and then on to the tampermonkey.net site) to look for API documentation to see how it can be used.  i could not find any.  so i cannot judge this.
It is just native JavaScript, the script you make will run during page load
TamperMonkey based on GreaseMonkey
[https://wiki.greasespot.net/Greasemonkey_Manual:API](https://wiki.greasespot.net/Greasemonkey_Manual:API)
[https://www.tampermonkey.net/documentation.php](https://www.tampermonkey.net/documentation.php)

in JS you can click a button like this
```
inputElement.click();
```
or if it is not a input/button element you may want to do it like this
```
element.dispatchEvent(new Event('click'));
```
here is a example of something you may want to automate (youtube set to dark mode and stop autoplay; great for private windows)
[https://pastebin.com/EqNAW55j](https://pastebin.com/EqNAW55j)

---

