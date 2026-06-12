---
title: "Static vs dynamic header/footer on websites"
date: 2012-01-19
forum: The Cafe
---

### Post by CharlesA on 2012-01-19
Hello,

I am trying to decide if I want to include a dynamic footer on my website. It currently uses a static one, but I was thinking that I could cut some of the info out from the main pages and only display it in specific areas of the site.

Are there any pros/cons to this approach?

Thanks,
Charles

---

### Post by Xihuitl on 2012-01-19
IMO

Pros: Dynamic content is great, and really makes each page seem as though you personally worked on each and every page. Depending on what you are planning on putting in the footer, it can be a nice touch. If you are already using some dynamic language in your site, it would be very simple to incorporate.

Cons: Bugs can always happen. If there is something amiss with your coding, your users may or may not see what you intend for them to. If not thought out and planned, it can cause some upkeep issues for you or the webmin.

With the sites I have worked on, I have always used PHP, but have found that the footers are rarely read. I do include standard footers in my sites, but just include it in the script that generates the pages. That way, I only have one file to edit if I choose to update or change the footer. Most of the dynamic content is in the navigation and main areas.

Perhaps if I saw the site you are working on, I could provide more information on how I, personally, would approach it.

---

### Post by CharlesA on 2012-01-19
It's my personal site: [http://charlesa.net](http://charlesa.net)

I'm using PHP for most of it, the snippet that I am thinking of using is this:

[php]<div class="footermodified"><?php print "Last modified: " . date("F jS, Y, g:i a", $last_modified); ?><br /></div>
<div>Content written by Charles Auer, unless noted otherwise.<br /><?php if ($bodyid=="tutorials") print "Feel free to print out and share my tutorials, but please reference where you got them."?><?php if ($bodyid=="scripts") print "You may modify my scripts as you see fit, but please credit the original script to me."?></div>[/php]

---

### Post by undecim on 2012-01-19
> **CharlesA said:**
> I'm using PHP for most of it

If you're already using PHP, then adding more won't slow your site down much, and that's really the only concern I would have. I would definitely go with a dynamic header/footer.

---

### Post by CharlesA on 2012-01-19
> **undecim said:**
> If you're already using PHP, then adding more won't slow your site down much. I would definitely go with a dynamic header/footer.
Ok, Thanks!

---

