---
title: "Website: Java text or Flash text?"
date: 2008-08-12
forum: The Cafe
---

### Post by -Outcast- on 2008-08-12
Just wondering what people's general thoughts are here? 

I have a dark styled website. And thought the nav bar could do with some brightening up. A roll over effect. 

With flash text I get a nice effect. As I do with java script roll over. 

On analytics it seems both are split with 3% having neither one nor the other. 

Java roll overs increase page load speeds. But flash is easier to quickly set up. 

Which do you think will have the greatest compatibility on FF3 and IE7?

---

### Post by mc4100 on 2008-08-12
I'd say go with JavaScript, not Flash.
Better yet, go CSS

---

### Post by ghindo on 2008-08-12
I feel that JavaScript is much better supported than Flash.

---

### Post by Thee_Baron_ on 2008-08-12
Why not use CSS for the rollovers?

---

### Post by -Outcast- on 2008-08-12
> Why not use CSS for the rollovers? 

I am afraid I am a bit old school and still use tables. CSS is something I can't get my head around! :confused:

So far Java script is in the lead then!

---

### Post by master5o1 on 2008-08-12
> 
<style type="text/css">
tr.menu,td.menu
{
background-color: #FFFFFF;
color: #000000;
}

tr.menu:hover,td.menu:hover
{
background-color: #000000;
color: #FFFFFF;
}
</style>

<table>
<tr><td class="menu">On the left</td><td class="menu">On the right</td></tr>
<tr class="menu"><td>On the left</td><td>On the right</td></tr>
</table>



TOP LINE OF TABLE: Individual cells `light up`
BOTTOM LINE: Both cells light up.

---

### Post by Tomosaur on 2008-08-12
Don't use either if you can do it in CSS. Flash is way too much overkill - and believe it or not some people don't have any kind of Flash support on their machine. If you absolutely don't want to do it in CSS, use JavaScript, but never use Flash for such a small thing.

---

### Post by Cobol to Java on 2008-08-12
Hmmmm..flash is a bit heavy. CSS would be a great choice. And there are lots of ebooks on coding CSS on bittorrent sites, you might want to download some. Java would be good too.

---

### Post by Tomosaur on 2008-08-12
^^ Please don't use Java for simple elements of style like mouse rollover type stuff. Java should be reserved solely for applications.

**JavaScript** on the other hand, is great for such things because it has great support and is pretty much instantaneously executed by the client.

Java **is not the same thing** as JavaScript - so watch out for any confusion!

---

### Post by -Outcast- on 2008-08-12
Ah java=javascript for my purposes. Many thanks for clearing that up for me. 

Many thanks for the replies, much appreciated. It looks like Javascript is the way to go. I am afraid CSS for the whole site will have to wait as I am still getting my head around html! lol

OK, thanks again for the advice.

---

### Post by lukjad on 2008-08-12
I disable JavaScript and Flash is hard on a lot of browsers. Go with CSS if you can.

---

### Post by Hells_Dark on 2008-08-12
I don't talk to people using table designs >__<

Just joking n__n

..well..maybe not.

---

### Post by hessiess on 2008-08-12
CSS ----> javascript -----------------------------------------------------> flash

remember that flash navigations WILL NOT WORK if the persion viewing the page has eather flashblock or adblock pluss installed, both of which will stop flash content loading.

---

### Post by -Outcast- on 2008-08-12
Ok, so I will change to Javascript and start working on some new navigation jpgs. 

It's very useful information to have. 

I checked on my blog analytics and it conflicted a little. Though I think analytics uses java script to analyze, so if a browser doesn't have it then it will not report back properly? 

I will have to go unspoken to for using tables I guess ;) Sorry!

---

### Post by picpak on 2008-08-12
CSS and div's are way better than tables for design, but there are some things I can do with tables I just can't do with div's. :( It's frustrating.

---

