---
title: "CSS help?"
date: 2006-09-06
forum: The Cafe
---

### Post by hizaguchi on 2006-09-06
I'm working on a simple little website to host information for my senior design project, and I know nothing at all about modern webpageification.  I took a class back in high school where we learned some basic html and frames (I hate frames), and that's about it.  So anyhow, since this site is going to be hosted under a university address I thought I'd try to mimic the style of the rest of their pages somewhat.  Problem is that their pages all use tables for the layout and so a simple page requires a TON of code.  Tables look very complicated and confusing, and I don't want to deal with a ton of code when I'm adding content later, so I started reading up on CSS.  With a little tinkering, I've been able to approximate their table layout with way less code, but there's still one hangup.  They have this huge and complicated header at the top of each page that they want to appear of all university sites.  So I'm wondering if anybody who knows more about this than me (which is pretty much everybody) could look at this site: [http://www.engr.utk.edu/]("http://www.engr.utk.edu/") and tell me if there's a better way to pull off the header than what I'm doing here: [http://web.utk.edu/~bshatley]("http://web.utk.edu/~bshatley").

Ideally, is there a way to put that header table in my stylesheet somehow, so it'll show up on every page without me having to copy it over?  Also open to criticism and especially links to good page building resources. :)

---

### Post by Paul41 on 2006-09-06
Can you use php (or something like it)?  I can't think of a good way to do it with css off the top of my head, but you could use php to make it a little easier.  Just put the table in a file and name it something like header.inc.  Then were ever you want it to show up on your page put <?php include 'header.inc'; ?>

You would still have to put it on evey page, but then it would only be one line, and if you need to make a change to the header you would only have to change it in one place.

If that won't work for you let me know and I will give the css idea some more thought.

---

### Post by Eproxus on 2006-09-06
Are you using any scripting language? Is your university using any scripting language? Do they have their header in a separate file? In that case you could just include it. 

It is possible to include content in CSS too, I don't know if it works with HTML though.

Try something like this:
```
#header {
   content: url('/path/to/header.html');
}
```

Sorry if it doesn't work! ^_^

---

### Post by Paul41 on 2006-09-06
> Do they have their header in a separate file? In that case you could just include it.

This is a good point from Eproxus.  If the they do have their header in a separate file and you could get the url you would not have to worry about them making changes and needing to keep up with them on your pages.  That is, of course, assuming either of these options will work for you.

---

### Post by hizaguchi on 2006-09-06
That CSS method sounded really good, but didn't work. :(  Thanks though!

Their header is a gigantic table that's been pasted at the top of every page.  It's got some references to images and stuff that they change occasionally, but the layout of the images is done on each page with a table.

Anything that works better than that would be great with me.  I'll read up on PHP, because putting one line at the top of the file is way better than all the stuff theirs has.  Really though, I don't know why it matters to me.  It's a mechanical engineering class, and the webpage is just a side requirement and very little of the grade, so I should probably leave it alone.  I just obsess about picky things like this. :)

Thanks for the ideas.  Keep em comming.  I've got some stuff to read now at least. :)

---

### Post by xhaan on 2006-09-06
I used to use server side includes for stuff like that, its similar to the PHP thing, PHP might be better, when I used SSI I was pretty much restricted to using the .shtml extension...

---

### Post by kostkon on 2006-09-06
Hi,

I understand what you want to do. You want a CSS version of this header. I think it can be done with a little work, you can even make it structurally good by using h1 header tag for saying "The University of Tennessee", make this header the size of the logo image you have and putting the image as a background for the header, and etc. etc. I could even do it for you if I had some time.

It is one main div. And then maybe, it is one div with the ruled background and inside another div that will have as a bakcground the right image. In that div also you put the h1 header with the university logo image as background.

Lastly another div inside the main for the search and links. Something like that. The only problem is to make it to resize gracefully.

I hope you got my idea. Maybe you or someone else will be able to do it.

---

### Post by hizaguchi on 2006-09-06
I think I see what you're saying.  I'll have to look into that too.  The thought had crossed my mind before, but then when I started looking at all that table stuff I just decided that cut and paste would be easier.  Now that I've got things at least acceptable though, I could sit and try to make sense of the tables (the search bar is the one that scares me).  I know next to nothing about what I'm doing here though, so it'll be an interesting challenge. :)

---

### Post by kostkon on 2006-09-06
I forgot to say to you that would be good to use an image replacement technique.

You will have the header
```
<h1>The University of Tennessee</h1>
```

but you will cover this with the image of the university logo. You can search the net for CSS image replacement techniques.

---

### Post by kostkon on 2006-09-06
Something more.

You can take the images directly from the uni server in the CSS. Anyway, if you make the header CSS based and also included automatically with PHP in every file, this would be the perfect solution ;)

---

