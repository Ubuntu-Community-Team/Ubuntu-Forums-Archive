---
title: "Opera Widget: Please Test"
date: 2007-09-27
forum: The Cafe
---

### Post by LaRoza on 2007-09-27
Like most people with sophistication, I use Opera :D

I wrote a widget inspired by these forums, to convert between Temperature Units (F,C) and distance (Km,Mi).

When posting on these forums, it is useful to put both units in your post, and this widget makes that easy (I hope).

[http://widgets.opera.com/author/LaRoza](http://widgets.opera.com/author/LaRoza)

---

### Post by LaRoza on 2007-09-27
I just uploaded another one. This one converts text to ascii codes.

---

### Post by Erik Trybom on 2007-09-27
I'm not happy with it. First, it doesn't calculate correctly. -40 F should equal -40 C, right? The widget says -4. 

Second, the graphics don't seem to render correctly. The white field floats out to the right (see screenshot.) 

It's a good idea though.

---

### Post by LaRoza on 2007-09-27
> **Erik Trybom said:**
> I'm not happy with it. First, it doesn't calculate correctly. -40 F should equal -40 C, right? The widget says -4. 

Second, the graphics don't seem to render correctly. The white field floats out to the right (see screenshot.) 

It's a good idea though.

It does calculate correctly, 40 F = 4.44 C over here.

-EDIT I see what you mean now, it has to do with how I round the numbers, which I am not happy with. Do you think it would be better if it rounded to integers?

What version of Opera are you using? It looks fine on 9.10 and 9.22, at least for me. I may need to change it if Opera has inconsistant rendering.

What OS are you using, maybe thats it.

On my website, there is an online version of the calculator, it uses the same algorithm, try that and let me know.

Thanks for trying it, although I am puzzled by your experience. It looks like the screenshots on the Opera site to me, I took them today.

Try the Ascii converter, if you have the same problem with the text field, I will have to alter the CSS.

---

### Post by olejorgen on 2007-09-27
I get the same as Erik Trybom on Opera 9.23, Feisty

---

### Post by Iceni on 2007-09-27
It won't install for me, gives me "error occured when applying this file".

Opera 9.51 daily build
Ubuntu Feisty

Probably to do with me using beta software.

---

### Post by RAV TUX on 2007-09-27
> **LaRoza said:**
> Like most people with sophistication, I use Opera :D

I wrote a widget inspired by these forums, to convert between Temperature Units (F,C) and distance (Km,Mi).

When posting on these forums, it is useful to put both units in your post, and this widget makes that easy (I hope).

[http://widgets.opera.com/widget/7570](http://widgets.opera.com/widget/7570)

I tried your new widget in:


> 
Opera
Version: 9.50 Alpha
Build: 1589
Platform: Linux
System: i686, 2.6.18-elive
Qt library: 3.3.7
Java: Java Runtime Environment installed

unfortunately it would not load, see the attached screenshot:

---

### Post by RAV TUX on 2007-09-27
> **Iceni said:**
> It won't install for me, gives me "error occured when applying this file".

Opera 9.51 daily build
Ubuntu Feisty

Probably to do with me using beta software.

do you have a link for the Opera 9.51 download?

---

### Post by LaRoza on 2007-09-28
Ok, I fixed the algorithm.

It was how I was "rounding" before, now it just rounds to an integer.

I don't know why it won't work in the other browsers, maybe it is because it is beta. The people on the Opera site test them before making them available.

---

### Post by Erik Trybom on 2007-09-28
OK, it works better now. Minus forty equals minus forty, and graphics looks good. I'm using Gnome by the way, on Debian stable. Opera version is 9.23.

Using integers only seems like a hack though. It does make a difference if it's four miles or four and a half.

I also have a feature request: kilograms to pounds conversion.

---

