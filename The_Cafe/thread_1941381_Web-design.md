---
title: "Web-design"
date: 2012-03-15
forum: The Cafe
---

### Post by ric1321 on 2012-03-15
I've been asked by a cousin of mine to help him to develop some websites in HTML 5. Actually he uses Mac and he had suggested me using Rapidweaver. What about linux? Is there some useful platform for my work, considering that I am an absolute beginner?

---

### Post by imachavel on 2012-03-15
create an index.html file in gedit

at the very least it should contain

<body>

<head>

<p>

</p>

</head>

</body>

I know that is a very very basic description that is extremely general, but it will get you started, if you want to see the more complex workings. in your browser(hopefully it's chrome), open a web page that is a favorite of yours, and then go to tools, and view source

---

### Post by ric1321 on 2012-03-15
Compozer seems to be a good platform? What do you think? Can I find some good tutorials?

---

### Post by user1397 on 2012-03-15
You don't need any special programs to do simple web design (or even complex for that matter).  A lot of people just use a basic text editor (like gedit in gnome or kate in kde), save it as .html and go from there.

Some people prefer wysiwyg editors (what you see is what you get) like kompozer or dreamweaver.  Professional grade apps like dreamweaver supposedly give greater productivity boosts but I've never used it and I'm not a professional web developer so I couldn't say.  I will say that I've heard many people complain about wysiwyg editors because it contains less than perfect code, while if you do it by "hand" you have complete control and you can write very clean code.

A good place to start is [here]("http://www.w3schools.com/html5/default.asp").  That is one of the best web developing tutorial and reference websites on the web, given that it is the official w3c website (world wide web consortium, the makers of all the web standards like html, xhtml, svg etc)

---

### Post by ric1321 on 2012-03-18
I've tried Kompozer so far, it seems quite good. How can I make an object (link or pic) that changes when I move the mouse over it?

---

### Post by Lars Noodén on 2012-03-18
> **ric1321 said:**
> I've tried Kompozer so far, it seems quite good. How can I make an object (link or pic) that changes when I move the mouse over it?

That would be a common [CSS](http://www.w3.org/TR/CSS/) trick.  There are dozens of tutorials and howtos available on the net. Whatever one you find, it will be using the :hover pseudo-class.

---

### Post by alphacrucis2 on 2012-03-18
> **ric1321 said:**
> I've tried Kompozer so far, it seems quite good. How can I make an object (link or pic) that changes when I move the mouse over it?


Kompozer isn't too bad but the only dev hasn't worked on it for quite some time. Another one to look at is bluegriffon. That is actively developed but only the base package is free. There are a bunch of plugins with quite good features but I believe most of the plugins you have to buy (although they aren't that bad price wise). Anyway it is quite useable without the plugins. I don't think bluegriffon is in the repos so you would have to download a deb file which I think they provide.  

Bluegriffon is developed by the original Kompozer dev (which was called NVU at that time). NVU development was taken over by "Kaze" who had to create the Kompozer fork due to naming rights of NVU.

---

### Post by Paqman on 2012-03-19
> **ubuntuman001 said:**
> I will say that I've heard many people complain about wysiwyg editors because it contains less than perfect code, while if you do it by "hand" you have complete control and you can write very clean code.


They're not mutually exclusive. WYSIWYG editors still allow you to code by hand, they just bundle a lot of useful workflow tools into the same suite. You can use them to auto-generate bad code, but it's certainly not compulsory. Much of the code they produce automatically is perfectly fine, too.

Much of the anti-WYSIWYG camp is just snobbery. Using Gedit doesn't make you a better coder, it just means that's the tool you prefer. Use what works for you.

---

### Post by ojdon on 2012-03-19
All Hail Sublime Text 2!

---

### Post by chickenPie4breakfast on 2012-03-19
I've heard good things about BlueFish
I've never tried making a website yet on LInux - always used WYSIWYG web builder when I used windows best one I tried - they do a  version for linux and Mac but it's not free

---

### Post by simptechmike on 2012-03-19
I wouldn't be able to give good advice on any of the available web design software as I hand code everything using gEdit. If you wish to go the same route and write the code yourself, you might want to check out w3schools.com. That's a pretty hand source for the basics.

---

### Post by trivialpackets on 2012-03-19
I'll second sublime text 2.  I love that as an editor, however you can do html editing with just about anything.  

As to the WYSIWYG editor snobbery, I guess I look at it a little differently.  If you don't know html already, a WYSIWIG editor is not necessarily the best way to learn.  If you do know html and a WYSIWIG can save you some time, then it can be a good tool.  I do personally feel like you're better off without one, but it's certainly not a crime to use one.

---

### Post by juancarlospaco on 2012-03-19
**[http://maqetta.org](http://maqetta.org)**

---

### Post by SeijiSensei on 2012-03-19
I recommend looking at how the websites you use are coded.  Next time you visit a new site, if you're using Firefox, right-click on the page and choose View Page Source.  A window will open with the HTML code used to generate the page.  You'll be able to see how elements are encoded and can compare them with the rendered version you see in the normal browser window.

---

### Post by Merk42 on 2012-03-20
> **ric1321 said:**
> I've been asked by a cousin of mine to help him to develop some websites **in HTML 5**. Actually he uses Mac and he had suggested me using Rapidweaver. What about linux? Is there some useful platform for my work, considering that I am an absolute beginner?Do either of you know what this means or are you just throwing around buzzwords?

While I agree with everyone else in this thread, with regards to suggestions of WYSIWYG and text editors, I'd hate for you to make something and your cousin go "but is it HTML5?!" and neither of you know the answer.


All "HTML5" is, really, is a doctype difference from HTML4. Granted there are features* in HTML5, but your cousin's site may not even need them.

*[SIZE="2"]not all features available in all browsers[/SIZE]

---

