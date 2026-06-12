---
title: "Simple web design problem"
date: 2009-08-29
forum: The Cafe
---

### Post by huggies15 on 2009-08-29
Hi all,
I'm just learning to build website and have run into a little problem. I have my page as i want it, but i want to have a section that changes when certain links are clicked on. I have the main 'links' section, but these are links within a section. How do i code it so when the link is pressed the data comes into that section only. ive added a screen shot of what i want to do below (done in gimp).
If anyone has any adivce, it will be greatful recieved.
Cheers,
Steve

[IMG]http://img377.imageshack.us/img377/5879/cardiffchemistshowtoresq.jpg[/IMG]

---

### Post by hessiess on 2009-08-29
Simplest way, use PHP to break the page into logical chunks with include statements, more maintainable way, find/write a CMS. Whatever you do, DO NOT use frames.

---

### Post by huggies15 on 2009-08-29
OK, well i only know how to write in html at the moment with <div> etc... i learnt frames dont look good on my previous attempt. CMS scares me as i dont really understand what it is that i does or how it works.
Can you do it with <div> so the data changes, or would it be easier to make a new page for each table i want to show and just link them the 'old skool' way?
Cheers

---

### Post by hessiess on 2009-08-29
> **huggies15 said:**
> Can you do it with <div> so the data changes, or would it be easier to make a new page for each table i want to show and just link them the 'old school' way? Cheers

The only way to do this is to create separate pages, includes are just a way of removing the duplication of `common' content.

i.e. you would create separate pages for the changing elements, and include the common elements of the page.

```

<html>
    <head></head>

    <body>
        <?php include("common.php"); ?>
        <!-- changing element goes here -->
        <?php include("footer.php"); ?>
    </body>
</html>

```

Common.php could look something like this:

```

    <div id="nav">
        <!-- nav goes here -->
    </div>

    <div id="table" >
        <!-- periodic table goes here -->
    </div>

```

Footer.php would also be simmaler, just containing footer stuff.

---

### Post by huggies15 on 2009-08-29
OK, cheers.
Ill have a look at this php stuff soon. in the mean time ill just keep it with seperate pages.
Do u recommend any site other than w3schools for learing php?
Steve

---

### Post by hessiess on 2009-08-29
[http://devzone.zend.com/article/627-PHP-101-PHP-For-the-Absolute-Beginner](http://devzone.zend.com/article/627-PHP-101-PHP-For-the-Absolute-Beginner)

---

