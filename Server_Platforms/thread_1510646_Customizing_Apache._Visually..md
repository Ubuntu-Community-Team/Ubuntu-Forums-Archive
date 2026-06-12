---
title: "Customizing Apache. Visually."
date: 2010-06-15
forum: Server Platforms
---

### Post by Roasted on 2010-06-15
I have Apache set up on a spare Ubuntu box here. I'd like to customize the layout a bit instead of having the bland white background and such with the directory listing. I'm not necessarily looking to CHANGE anything major, I just want to change the background color, perhaps add a picture on the right side, change the text color, etc.

I'm told the best way to do this is to set up a HEADER.html file. I've went through a dozen guides, but I'm still a bit confused, so if anybody can relay to me in basic English terms what I'm supposed to do, it'd be a big help.

Here's what I'm gathering so far as to what I'm supposed to do, so critique it any way you can and tell me what I'm doing wrong:

Create a HEADER.html document with a basic HTML layout, inside with it linking to a separate cascading style sheet. Within the CSS I'd add the coding to a free CSS I found on a free web site, just to tinker and see if I can get somebody else's pre-defined layout to work since my coding skills are very rusty. Then I'm supposed to edit the apache.conf file and at the end add HeaderName HEADER.html in there. Ultimately, this is what I've gathered. But I have no idea what I'm doing wrong. How can I do this?

---

### Post by stmiller on 2010-06-15
If you are referring to the 

Index of /

sort of pages, they by nature of what they are just a directory listing and no css or html is being or can be applied. :/

Unless you do some sort of php wizardry to achieve this.

Example: This sort of thing? [http://www.agency26.com/custom.logo/](http://www.agency26.com/custom.logo/)

Or is is something else you are referring to?

---

### Post by Roasted on 2010-06-16
My buddy was talking to me tonight and was like, why don't you run Wordpress? So I thought about it and figured I'd try it. I installed mysql, phpmyadmin, apache2, and downloaded wordpress. After some quick how-to instructions by him, I had wordpress running. I haven't uploaded any content yet, but I got the gizmo running, and the hundreds of free themes available means I'll have quite a lot of customizing to do.

Do you guys think this is a viable solution to what I want to do? Visually it's MUCH more than I wanted to do, but it doesn't seem to be that difficult to make it happen, so perhaps this is something I should continue following through with.

Thoughts?

---

### Post by Bachstelze on 2010-06-16
> **Roasted said:**
> 
Do you guys think this is a viable solution to what I want to do?

Well, what is it that you want to do? If you only want to display a bunch of mostly static pages, then Wordpress might be a bit overkill, but if it works for you, that's perfectly fine.

---

