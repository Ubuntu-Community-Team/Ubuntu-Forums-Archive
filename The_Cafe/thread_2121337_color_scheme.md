---
title: "color scheme"
date: 2013-03-01
forum: The Cafe
---

### Post by stalkingwolf on 2013-03-01
Why do those that choose always choose such hideous colour combinations?
Im color blind and it is still hideous.

---

### Post by GreatDanton on 2013-03-01
Same here. Color of the titles is just horrible.

---

### Post by pqwoerituytrueiwoq on 2013-03-01
What color would you suggest?

---

### Post by GreatDanton on 2013-03-01
Black would be great =)

---

### Post by Paqman on 2013-03-01
> **GreatDanton said:**
> Black would be great =)

+1

Links don't *have *to be a special colour, people understand about clicking on thread titles on a forum. This is not 1993.

---

### Post by pqwoerituytrueiwoq on 2013-03-01
Here, enjoy your black links in your firefox (If [FONT=courier new]cat[/FONT][FONT=courier new] ~/.mozilla/firefox/*.default/chrome/userContent.css 2> /dev/null[/FONT] has output I don't suggest running this)
```
cd ~/.mozilla/firefox/*.default/;mkdir chrome;echo -e '@namespace url(http://www.w3.org/1999/xhtml);\n@-moz-document url-prefix("http://ubuntuforums.org/") {\n\tbody a {\n\t\tcolor:black!important;\n\t}\n}' > chrome/userContent.css;cd;echo "Now restart firefox and enjoy your black links"
```
to change the color:
```
sed 's/**old_color**/**new_color**/' -i ~/.mozilla/firefox/*.default/chrome/userContent.css
```
in this case old_color would be black
to go back to default
```
rm ~/.mozilla/firefox/*.default/chrome/userContent.css
```

---

### Post by GreatDanton on 2013-03-01
> **pqwoerituytrueiwoq said:**
> Here, enjoy your black links in your firefox
```
cd ~/.mozilla/firefox/*.default/;mkdir chrome;echo -e '@namespace url(http://www.w3.org/1999/xhtml);\n@-moz-document url-prefix("http://ubuntuforums.org/") {\n\tbody a {\n\t\tcolor:black!important;\n\t}\n}' > chrome/userContent.css;cd;echo "Now restart firefox and enjoy your black links"
```



Thank you. It's perfect now.

---

### Post by pqwoerituytrueiwoq on 2013-03-01
i doubt you can see the links in my signature without putting you mouse over the text, probably affected the header as well

---

### Post by GreatDanton on 2013-03-01
You are right. Links looks the same as text.

---

### Post by pqwoerituytrueiwoq on 2013-03-01
you are welcome to lean a [little CSS]("http://www.w3schools.com/css/") <- that is a link BTW
```
gedit ~/.mozilla/firefox/*.default/chrome/userContent.css
```
replace gedit with your preferred editor, i like [geany]("apt:geany") <- that is a link BTW
The element targeting in css works like this (just the basics)
```
body a {
```
the A element (a tags are links) must be contained in the body element (the body element contains all visible parts of a web page)
```
body a#someID {
```
this modification requires the link to have a id attribute with the value "someID"
```
.someClass {
```
this requires the target element to have the class attribute with a value of "someClass"
```
p > a {
```
this will affect all links (A tag) that are directly inside of a paragraph element (P tag)
```
p > a, div span {
```
commas can be used specify multiple targets

---

### Post by SantaFe on 2013-03-02
If you have Firefox & the NoSquint extension, you can play around with changing a few color options.

Only problem is, if you have code blocks in the post, it can tend to make them hard to see as NoSquint can't change the background color of the code /code box, but will change the text, so if you have white text, it's white on light gray.  Durn it. ;)

---

### Post by MadmanRB on 2013-03-02
Meh black is overdone, I kind of like the orange.

---

### Post by stalkingwolf on 2013-03-02
Asking me to suggest a color scheme is dangerous.  I work with 5-6 bright colors that i can see well.  Mine would im sure be worse.

---

### Post by Linuxratty on 2013-03-02
> **GreatDanton said:**
> Black would be great =)

NnnNoooooO! I hate black themes..So depressing!
 I like the orange and gray,but the yellow clashes with it really bad.

Perhaps a light gray behind our letters and a slightly darker gray for the user's info and boarders?? And changeling the yellow do a darker shade of gray or orange would be my suggestion.

---

### Post by Morbius1 on 2013-03-02
I installed the ColorThatSite firefox addon in response to these changes to the forum. Your post looks like the Before attachment when it's not invoked and the After attachment when it is. The addon is here if interested: [https://addons.mozilla.org/en-us/firefox/addon/color-that-site/](https://addons.mozilla.org/en-us/firefox/addon/color-that-site/) You might be able to do more with it than I have. I just wanted to cut down on the intense titanium white / orange , Orange Julius thing going on here. When composing this reply it looks to me like the Reply attachment

---

