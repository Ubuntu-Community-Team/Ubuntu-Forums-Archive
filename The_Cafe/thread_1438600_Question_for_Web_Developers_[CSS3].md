---
title: "Question for Web Developers [CSS3]"
date: 2010-03-25
forum: The Cafe
---

### Post by LepeKaname on 2010-03-25
Hi all!

Many of you already know that you can express colors in your stylesheets like:

color: #FFF;
color: #FFFFFF;
color: rgb(255,255,255);
color: hsl(100%,100%,100%);

and that you can use rgba() and hsla() to express color transparency.

Do you think it would be a good idea to be able to express color transparency in #RRGGBBAA or #RGBA annotation?

Why YES, and why NOT???

Also if you want, give a little of details of how you perform your development (if you use a web-builder software, a graphic software (for designs), use vim, etc..)

---

### Post by madnessjack on 2010-03-25
I voted no but tbh it might be useful. Would prefer it in a separate attribute- easier to manipulate without affecting colour.

---

### Post by PartisanEntity on 2010-03-25
I would also prefer a seperate attribute.

I use a combination of DreamWeaver, CSSedit and Textedit, as well as Eclipse for all my web work.

---

### Post by LepeKaname on 2010-03-25
By separate attribute you mean something like:

```
color-transparency:
background-color-transparency:
border-color-transparency:
```

and what about gradients? 
until now, this is an example of the proposed format:

```
background: gradient(linear, center, bottom, color-stop(0.1, rgba(51,51,51,0.3)), color-stop(1, rgba(255,255,255,0.8)));
```

How do you think transparency can be replaced here with a separate attribute? maybe:

```
background-gradient-color-transparency-stop: 1 #333; ?
```

Sorry, but I don't think that could work.

In the example above, the alternative annotation could be:

```
background: gradient(linear, center, bottom, color-stop(0.1, #3335), color-stop(1, #FFFC));
```

---

### Post by themarker0 on 2010-03-25
Imho, i don't use it. If i do transparency i use images. Its better imho.

---

