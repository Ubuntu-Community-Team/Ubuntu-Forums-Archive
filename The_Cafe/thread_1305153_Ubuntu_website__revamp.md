---
title: "Ubuntu website  revamp"
date: 2009-10-29
forum: The Cafe
---

### Post by andymorton on 2009-10-29
I was just wondering what everyone thinks of the new look Ubuntu website. Personally I think it's vast improvement on the previous one and makes the OS look much more attractive. :)

---

### Post by Excedio on 2009-10-29
> **andymorton said:**
> I was just wondering what everyone thinks of the new look Ubuntu website. Personally I think it's vast improvement on the previous one and makes the OS look much more attractive. :)
 
I enjoy it as well. I'm curious what programs they use to create their site. Do they use GIMP to create all the artwork on the site? Anyone know?

---

### Post by The Toxic Mite on 2009-10-29
If they did use GIMP to design all the artwork, then I'm bloody impressed! :D

---

### Post by Excedio on 2009-10-29
Exactly! I wannt know how they did that. I want to do that!

---

### Post by Mr. Picklesworth on 2009-10-29
The eradication of ugly stock photos is quite beautiful :)

(I have to say, though, the icons used on certain pages, such as the [support overview]("http://www.ubuntu.com/support"), are really inconsistent).

---

### Post by Excedio on 2009-10-29
> **Mr. Picklesworth said:**
> (I have to say, though, the icons used on certain pages, such as the [support overview]("http://www.ubuntu.com/support"), are really inconsistent).
 
Agreed...it looks like they did a google search for those.

---

### Post by jrrader on 2009-10-29
I don't see what on their website couldn't be done with either gimp or inkscape :confused:

---

### Post by Dharmachakra on 2009-10-29
I think the 'Feature Tour' looks pretty nice.

---

### Post by Johnsie on 2009-10-29
The tour on the old site was of 8.10 and there was no uniformity between page layouts. Some of the screenshots looked pretty tacky but I think that was just the gui of some of the programs. There was also too much jargon on the download page. "Here are the ISO
's". Does the average joe even know what an ISO is? Do you know what ISO stands for? ;-) Does the average joe know what 32-bit and 64-bit means?

The new design is a vast improvement. Makes things look better and is more user friendly. There is still a long way to go to make Ubuntu installation dummy proof though.

---

### Post by Frak on 2009-10-29
Looks better... I guess...

Nothing to write home about, personally.

---

### Post by wulfgang on 2009-10-29
The ubuntu site looks a million times better than the previous one. It also appears more welcoming to new users or potential new users. :)

---

### Post by The Real Dave on 2009-10-29
Prrrrrrreeeeeeetttyyy :) 



If anyone knows, could you point me a tutorial on making those foreground seperate to the background effect? I would love to know how, but have yet to figure out :(

---

### Post by Frak on 2009-10-29
> **The Real Dave said:**
> Prrrrrrreeeeeeetttyyy :) 



If anyone knows, could you point me a tutorial on making those foreground seperate to the background effect? I would love to know how, but have yet to figure out :(
Could you give an example? I could probably explain everything on the page.

---

### Post by The Real Dave on 2009-10-29
> **Frak said:**
> Could you give an example? I could probably explain everything on the page.

How the white centre of the page, where the content is, seems to be seperate to the brown background :) Web design is a new and exciting thing for me :lolflag:

---

### Post by Occasionally Correct on 2009-10-29
One thing kinda bugs me. Why is Ubuntu "an open-source alternative to Windows *and Office*?" :P I do like the changes otherwise. It looks more approachable.

---

### Post by Excedio on 2009-10-29
> **jrrader said:**
> I don't see what on their website couldn't be done with either gimp or inkscape :confused:
 
I'm sure it can as well. But I currently do not know how. I have yet to scratch the surface of what GIMP can do.

---

### Post by lovinglinux on 2009-10-29
Yep, it's really better now. I like it.

---

### Post by Frak on 2009-10-29
> **The Real Dave said:**
> How the white centre of the page, where the content is, seems to be seperate to the brown background :) Web design is a new and exciting thing for me :lolflag:
The background is an image being repeated on the y-axis.

[IMG]http://www.ubuntu.com/sites/all/themes/ubuntu09/images/bg.png[/IMG]

Within that is a container that holds the content. It can be centered with a simple

```
margin: 0 auto;
```
(Means: Top and bottom should be nudged 0 pixels, and the browser should determine the amount of space on the right and left)

That's really it. The content is just composed of a bunch of images. The body is just one image repeated on the x-axis:

[IMG]http://www.ubuntu.com/sites/all/themes/ubuntu09/images/body-bg.png[/IMG]
(There's an image directly above this sentence)

The top and bottom have their own respective images.

[IMG]http://www.ubuntu.com/sites/all/themes/ubuntu09/images/top.png[/IMG]
[IMG]http://www.ubuntu.com/sites/all/themes/ubuntu09/images/bottom.png[/IMG]

(those are two images)

Hope that helps.

---

### Post by hellmet on 2009-10-29
The new design is lovely.. yet, Canonical needs to wipe out and organize all the clutter of the previous releases and maintain proper design consistency, or our website will turn into another Sun.com or Microsoft.com in a few years.

---

### Post by misfitpierce on 2009-10-29
I was impressed, the tour of 9.10 is even more impressive and looks much better! Very happy with site upgrade as well!

---

### Post by The Real Dave on 2009-10-30
> **Frak said:**
> 
Hope that helps.

I think I understand the concept, but havn't a clue how to but it into practice :) Its CSS ya? 

Thanks anyway, you've satisfied my curiosity at least :) Now just to learn how to do it :lolflagL

---

### Post by forrestcupp on 2009-10-30
> **Excedio said:**
> I enjoy it as well. I'm curious what programs they use to create their site. Do they use GIMP to create all the artwork on the site? Anyone know?

Oh boy.  Here we go again.  It wasn't that long ago that we had a lynch mob because they used a photo that was designed in Photoshop.

---

### Post by Frak on 2009-10-30
> **The Real Dave said:**
> I think I understand the concept, but havn't a clue how to but it into practice :) Its CSS ya? 

Thanks anyway, you've satisfied my curiosity at least :) Now just to learn how to do it :lolflagL
[http://css-tricks.com/](http://css-tricks.com/)

---

### Post by Stan_1936 on 2009-10-30
> **andymorton said:**
> I was just wondering what everyone thinks of the new look Ubuntu website. Personally I think it's vast improvement on the previous one and makes the OS look much more attractive. :)

Dude, you got my hopes up.  FALSELY!!!

It's the same with different colors.

---

### Post by Crunchy the Headcrab on 2009-10-30
> **jrrader said:**
> I don't see what on their website couldn't be done with either gimp or inkscape :confused:
x2

---

