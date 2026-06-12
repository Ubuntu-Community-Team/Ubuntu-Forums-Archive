---
title: "where do i insert &lt;img&gt; into this footer file using grid system?"
date: 2012-05-10
forum: The Cafe
---

### Post by hanzj on 2012-05-10
Hi.
The footer file looks like [http://pastebin.com/1cGzySvS](http://pastebin.com/1cGzySvS)

I would like to insert two images into this file. Where do I insert the <img> code? 

Thank you.

---

### Post by Bandit on 2012-05-10
> **hanzj said:**
> Hi.
The footer file looks like [http://pastebin.com/1cGzySvS](http://pastebin.com/1cGzySvS)

I would like to insert two images into this file. Where do I insert the <img> code? 

Thank you.

Where ever you need it as long as its inside your html tags, which btw I dont see the opening <html> tag, but I see the closing </html>one.

---

### Post by hanzj on 2012-05-10
Thanks, Bandit.
Should I add the opening <html> tag? If so, where?

---

### Post by CharlesA on 2012-05-10
> **hanzj said:**
> Thanks, Bandit.
Should I add the opening <html> tag? If so, where?
You shouldn't need to add the <html> tag if it's just the php file for the footer.

---

### Post by Bandit on 2012-05-10
> **CharlesA said:**
> You shouldn't need to add the <html> tag if it's just the php file for the footer.

Yea your right if its just the footer file, the main file should need it. So hard to know where someone needs/wants something when your not the one building the sight.

---

### Post by hanzj on 2012-05-10
bandit,
i see the opening <html> code in the header.php. Line 17 in [http://pastebin.com/wfCwpT7G](http://pastebin.com/wfCwpT7G).

---

### Post by wojox on 2012-05-10
Could you show us the page? Making the images show up is easy, aligning them is tricky. ;)

---

### Post by wojox on 2012-05-10
> **hanzj said:**
> bandit,
i see the opening <html> code in the header.php. Line 17 in [http://pastebin.com/wfCwpT7G](http://pastebin.com/wfCwpT7G).

Line 17 is a decleration.
Line 21 is the openening HTML

---

### Post by hanzj on 2012-05-10
I've been able to insert the two images. And they're side by side, just like we want. But we still would like 2 changes:

1. We would like the images to share the  same "bottom level" as the copyright text and the facebook icon. How can we do that.
2. We'd like the images to be centered on the horizontal axis.

Current screenshot:
[http://i.imgur.com/kkm7Y.png?1](http://i.imgur.com/kkm7Y.png?1)

Current footer.php:
[http://pastebin.com/yp5s2HXz](http://pastebin.com/yp5s2HXz)

Current CSS, both the child theme's CSS and the parent's CSS:
[http://pastebin.com/Nvn4q8g2](http://pastebin.com/Nvn4q8g2)

---

### Post by CharlesA on 2012-05-10
If it helps, take a look at my homepage:
[http://charlesa.net/](http://charlesa.net/)

---

### Post by wojox on 2012-05-10
Did you add this part:
```
<div class="special-class"><img src="http://ourwebsite.com/wp-content/uploads/2012/05/member-of-ayt.png" width="223.5" height="60.5" alt="Member of AYT" /><img src="http://ourwebsite.com/wp-content/uploads/2012/05/member_of_WEM.png" width="253.5" height="66.5" alt="Member of WEM Group" />
```

---

### Post by hanzj on 2012-05-10
hi, wojox. where should i insert that code?

---

### Post by wojox on 2012-05-11
> **hanzj said:**
> hi, wojox. where should i insert that code?

Hey hanzj, that block of code above is the right banner in the footer.

---

### Post by hanzj on 2012-05-11
hi, wojox. I don't get it. I'm already seeing the two banners in the footer. So what should I do with the line of code you posted here?

---

