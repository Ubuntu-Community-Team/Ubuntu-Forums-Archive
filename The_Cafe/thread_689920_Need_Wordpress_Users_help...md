---
title: "Need Wordpress Users help.."
date: 2008-02-06
forum: The Cafe
---

### Post by Dark Star on 2008-02-06
Hi all
I have a WP blog but as I am new to this blogging stuff I don't know much codes :( So I was wating this page .. and want to know how this guy has done following this ? [http://www.taimila.com/?q=node/3](http://www.taimila.com/?q=node/3)

[LIST=1]
[*]How he has give heading for every topic with underline ?  I mean he has give under line in such a way that it separates the topic with other ? while the underline that I do just underline the text ?
[*]How to wrap the codes in those black boxes ?
[*][OT]Also how to make a image border curved using **Gimp ?**[/LIST]That's all for know ..

 Adios :D

---

### Post by K.Mandla on 2008-02-06
He's just adding a horizontal rule after each title.
[HTML]<h1>Firefox &amp; Opera - Web browser</h1>
<p><hr /><br />[/HTML]
The reverse black console text is just a custom CSS style, probably.
[HTML]<div class="console">
sudo cp gaim.png /usr/share/pixmaps/
</div>[/HTML]

---

### Post by natedawg on 2008-02-06
It appears that site is running drupal not wordpress.

---

### Post by Dark Star on 2008-02-08
> **K.Mandla said:**
> He's just adding a horizontal rule after each title.
[HTML]<h1>Firefox &amp; Opera - Web browser</h1>
<p><hr /><br />[/HTML]
The reverse black console text is just a custom CSS style, probably.
[HTML]<div class="console">
sudo cp gaim.png /usr/share/pixmaps/
</div>[/HTML]

Hey thanks.. That Horizontal rule working but that console 1 is not working ... :( You got a gr8 blog.. Mine is [http://tuxenclave.wordpress.com/](http://tuxenclave.wordpress.com/) I am fed up pf Wordpress.com is there a way so that I can shift my whole blog to Wordpress.org ? on a free Blog Hosting ? I don't want to loose my stats comments and posts :(

---

### Post by MetalPrincess on 2008-02-09
> **Dark Star said:**
> 

How he has give heading for every topic with underline ?  I mean he has give under line in such a way that it separates the topic with other ? while the underline that I do just underline the text ?

As said above looking at the page source he is using the <hr> (horizontal rule) code. 

> **Dark Star said:**
> How to wrap the codes in those black boxes ?

This is done with CSS. You need to add to your CSS a div tag either ID or class (most likely class) and then put the code for the box in the CSS style code markup. Here's just a brief example something very easy and off the top of my head...

```

.box {
      width: 500px;
      height: 50px;
      background-color: #000000;
      color: #FFFFFF;
}
```

That is of course just something as a hint. But you get the idea on it. 

As for moving your wordpress blog there are a few questions you need to answer before its clear how it can or cannot be moved. Sometimes with free sites its not as easy as when you have paid for hosting. 

1. Do you use FTP to upload any files to the site or better yet do you have FTP access to the wordpress install you have?
2. Are you able to download all the files off your free wordpress pages via FTP?
3. Does the free server you want to go to support you uploading & configuring your current wordpress files?
4. Do you have access to the MySQL database so you can back it up & download it?

In order to move a wordpress site including the database you need to pretty much have access to everything on the site including backend functions. If not then there is little to no way to move the site. Unless you can get the site owners to move it for you or back it up for you and send it to you via e-mail or something. Its always best to purchase your own hosting, its so much easier to have your site and have full access to these things. There are many hosting companies that are quite affordable these days.

---

