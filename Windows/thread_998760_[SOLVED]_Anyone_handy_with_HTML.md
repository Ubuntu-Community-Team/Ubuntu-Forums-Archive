---
title: "[SOLVED] Anyone handy with HTML?"
date: 2008-12-01
forum: Windows
---

### Post by poebae on 2008-12-01
I apologise in advance if this doesn't belong on the Ubuntu forums, but I figured that this would be the right crowd to ask since there are so many savvy people around.

My page loads correctly, but when I open a new tab while testing my website in IE7, my page shifts to the left, and the menu overlaps/
obscures parts of the images.

I can't find a reason why this happens, can anyone help?

A screenshot of the error can be found below:

[http://www.onetopsoccer.com/error.jpg](http://www.onetopsoccer.com/error.jpg)

The page itself is at [http://www.onetopsoccer.com](http://www.onetopsoccer.com)

---

### Post by hrod beraht on 2008-12-01
Check out this [[COLOR="Blue"]online HTML validator[/COLOR]]("http://www.htmlvalidator.com/lite/onlineval.php"). It shows 21 specific errors.

Bob

---

### Post by Izek on 2008-12-01
> **hrod beraht said:**
> Check out this [[COLOR="Blue"]online HTML validator[/COLOR]]("http://www.htmlvalidator.com/lite/onlineval.php"). It shows 21 specific errors.

Bob

Though with the w3c validator, it shows you everything: [Click Here](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.onetopsoccer.com&charset=(detect+automatically)&doctype=Inline&group=0) (66 errors mostly type issues, 1 warning)

But when I use the validator you provided Bob, it only shows 2 errors and 0 warnings.

---

### Post by Joeb454 on 2008-12-01
I just had a flick through the W3C validator. Quite a few of those errors are the fact your <script> tags are missing the "type" attribute, i.e. it should be something like [html]<script type="text/javascript">
    /* some JS code */
</script>[/html]

---

### Post by poebae on 2008-12-02
Thanks for the quick responses, guys =)

I've fixed up a lot of the HTML errors, but none of them seem related to my problem.

I received this response elsewhere:

> 
<table width="963"

This is the problem. You have made you page so it precisely fits the particular pixel diimensions of the browser window you started in. Of course it doesn't precisely, or even roughly, fit other people's windows... But when you open a second tab, thanks to the miracle of Microsoft "Innovation", there is a bar across the top. 

So the available _height_ is less, and your page now needs a vertical scrollbar, which causes it to jump left or right or something. This also means it now needs a horizontal scrollbar too, and so it goes on. 


That seems to make sense, but I'm not sure how to go about fixing it, since I'm very new to HTML.

Any ideas?

---

### Post by poebae on 2008-12-02
Actually, I think I've fixed it :D

I changed the width of my left menu area to 16% instead of 152. That way it doesn't insist on staying the same width even when other elements are resized.

Hurrah!!

---

### Post by cardinals_fan on 2008-12-03
> **poebae said:**
> Actually, I think I've fixed it :D

I changed the width of my left menu area to 16% instead of 152. That way it doesn't insist on staying the same width even when other elements are resized.

Hurrah!!
You're down to 11 errors... [http://validator.w3.org/check?uri=http%3A%2F%2Fwww.onetopsoccer.com%2F&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.onetopsoccer.com%2F&charset=%28detect+automatically%29&doctype=Inline&group=0) :)

---

