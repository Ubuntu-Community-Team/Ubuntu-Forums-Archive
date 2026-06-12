---
title: "I just finished designing my first website, and wanted some feedback."
date: 2007-07-27
forum: The Cafe
---

### Post by rich.bradshaw on 2007-07-27
Hi,

Just finished designing a website for a wedding photographer, wondered if anyone had any feedback.

The weddings section is the most developed, as that is where the bulk of the business is at the moment.

[http://www.focalpix.co.uk](http://www.focalpix.co.uk)

---

### Post by LaRoza on 2007-07-27
+
0. Good layout and design
1. Works in 800x600 fine
2. Works in Opera, Firefox and IE7
3. Mostly easy navigation
-
0.There is no way to get back to the main page from the Wedding section, "Home" brings you to the Wedding Home, not the site's home.
1. [http://www.focalpix.co.uk/weddings/contactform.php](http://www.focalpix.co.uk/weddings/contactform.php) has no client side validation
2. Your homepage doesn't have enough content, it is mostly images.
3. Navigation is impossible with a text-browser, (and probably a screen reader)

---

### Post by rich.bradshaw on 2007-07-27
You can click on the Focal Pix logo to go all the way back, but I agree with that - considering if the first page is even useful...

Validation is a good point.

Why do you say the navigation is impossible? It's just an ul, no javascript/images etc?

---

### Post by LaRoza on 2007-07-27
> **rich.bradshaw said:**
> 
Why do you say the navigation is impossible? It's just an ul, no javascript/images etc?

In Lynx, navigation doesn't make sense, and I couldn't get to another page easily even though I already saw the layout.

Few people will navigate to your site in Lynx, because it is mostly images, but screen readers will not make sense of the site.


> 
#[1]Weddings Home [2]Sitemap

   Focal Pix Logo

Focal Pix Photography

   Commercial,  Wedding  and  Portrait  Photography  - a professional and
   personal service
   [3]Commercial 

   [4]Commercial
   [5]Weddings 

   [6]Weddings
   [7]Portrait 

   [8]Portrait

   © Focal Pix Photography 2007
   Focal Pix Photography is a division of Focal Strategy Limited
   Directors: Peter S Bradshaw and Sue Bradshaw
   Hampshire,  Dorset,  Wiltshire,  Somerset,  Devon,  Berkshire, Sussex,
   Surrey, Cornwall[

Here is what it looks like, the numbers in brackets are images.

---

### Post by rich.bradshaw on 2007-07-27
Ok, what does the main site look like? i.e. [www.focalpix.co.uk/weddings](www.focalpix.co.uk/weddings) (I'm not at a Linux computer at the mo...)

Do you know what i can do to improve things?

---

### Post by LaRoza on 2007-07-27
The site is pretty good, I would:

0. Make navigation to the main page easier from EVERY page.
1. Make the home page more edifying, i.e. smaller images, more words.
2. Use ECMAScript to do some form of validation on the...form. (I can do that for you, if you want)
3. Just a thought, but the left side is empty, so that would be a good place for text-links.

Overall, the site is good.

---

### Post by cpeckert on 2007-07-27
I liked the site, however I think it might be good to hava a "CONTACT"  button on each page.

---

### Post by rich.bradshaw on 2007-07-27
Thanks for your help!

I'll speak with the client again before changing too much of the actual design.

What validation do I need? I don't mind if people don't fill in all the boxes, I do mind if the script is hacked to send spam!

I already use htmlentities and stripslashes on all input in the php script handling the form, is that enough?

Javascript will just check if the boxes are full won't it?

---

### Post by LaRoza on 2007-07-27
> **rich.bradshaw said:**
> 
What validation do I need? I don't mind if people don't fill in all the boxes, I do mind if the script is hacked to send spam!

I already use htmlentities and stripslashes on all input in the php script handling the form, is that enough?

Javascript will just check if the boxes are full won't it?
You don't mind, but a user might if they accidentally send wrong info.

That is probably enough.

ECMAScript can do many tasks, the easies will be to check if the input is not empty, but you test against regular expression, like looking for '@' in a field supposed to contain an email address. It is best to keep validation simple. I would just verify the info with the user with an alert box, asking if the info is correct, the form submission can be cancelled or sent.

---

### Post by kostkon on 2007-07-27
Nice site!! I, especially, like your if clauses to serve gif images instead of pngs for IE 6 and less, clever!!

---

### Post by rich.bradshaw on 2007-07-27
Thanks koston!

I wouldn't mind something simple to check that it's not all empty, and an dialog to confirm whether to send...

How can I do that?

I appreciate your help!

---

### Post by kostkon on 2007-07-27
Oh, and a couple of recommendations:

Code-wise, for a semantically better HTML, on the front page you could just put the phrase *Commercial, Wedding and Portrait Photography - a professional and personal service* inside a <h2> tag instead of a <div> one.

Also, you can have the services your offer (I mean the *Commercial*,* Weddings*, *Portait*) as list items inside a <ul> list instead of paragraphs. Then, using CSS, you can have the images for every service not as an <img> tagged image but as a background image of the link tag. This way, you will create a more semantic markup, I believe.

That's the things that caught my attention after a short examination of your HTML.

---

### Post by rich.bradshaw on 2007-07-27
I have the Commercial, Wedding etc in a div because I reused the code from the nav bar on other pages - I agree though, I have thought of doing this...

Do you think that the active menu item on the nav bar in the weddings section should be an h2 as well? i.e. if you are on the links page, the links in the navbar would be h2.

I tried doing this using php, but it looked crap in IE, it had too much padding etc and I couldn't get it looking neat - is it worth the effort?

---

### Post by rich.bradshaw on 2007-07-27
Oh, I changed the php so that compleltly blank forms aren't sent, so don't really need any javascript i don't reckon...

---

### Post by Sayers on 2007-07-27
It looks very nice and professional.

---

### Post by rich.bradshaw on 2007-07-27
Thanks Sayers!

---

### Post by kostkon on 2007-07-27
> **rich.bradshaw said:**
> I have the Commercial, Wedding etc in a div because I reused the code from the nav bar on other pages - I agree though, I have thought of doing this...

Do you think that the active menu item on the nav bar in the weddings section should be an h2 as well? i.e. if you are on the links page, the links in the navbar would be h2.

I tried doing this using php, but it looked crap in IE, it had too much padding etc and I couldn't get it looking neat - is it worth the effort?

If I understand well what you want to say, no I don't think this is a good way of showing to a visitor in which page he/she is. It is wrong to transform the list item to a <h2> title.

The right way, if you want to show to the visitor which section of the site looks at, is to put a title in every page. I mean, for every page you will have to put a <h2> title, for example, in the Links page after the *navigation bar* you'll need to  put
```
<h2>Links</h2>
```

and then the rest of the content. Do this for every page. I know this is a big change to make, but I think is the best one.

Thus, even a person who uses a text based browser will easily understand which page of the site is visiting.

---

### Post by rich.bradshaw on 2007-07-27
I did that for this page [http://www.focalpix.co.uk/weddings/terms.php](http://www.focalpix.co.uk/weddings/terms.php) 
but I'm not sure if it breaks up the design too much...

---

### Post by rich.bradshaw on 2007-07-27
Oh, do you like the way it's XHTML 1.1 application/xhtml+xml for browsers that support it, but just XHTML 1.0 text/html for older ones?

---

