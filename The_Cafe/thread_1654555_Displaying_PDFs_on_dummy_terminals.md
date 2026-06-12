---
title: "Displaying PDFs on dummy terminals"
date: 2010-12-28
forum: The Cafe
---

### Post by timzak on 2010-12-28
Kind of a weird question, but was wondering if anyone had any ideas for the following:

We would like to send specific work instructions in PDF format to different production departments.  For example, we may have a dept of 10 people, where we'd like to put 5 screens that all display work instructions for the employees.  A supervisor would "push" the PDF files out to these monitors that would be specific to each dept.  We are looking for a simple, inexpensive way to do this.  Thin clients almost seem overkill given that all the client monitors will be doing is displaying a PDF file.

Thanks for any ideas.

---

### Post by sdowney717 on 2010-12-28
can you send them out as jpg pictures or png images?
they can be zoomed and scrolled

---

### Post by timzak on 2010-12-28
Well, I guess the question is, is there a way to do this without having any sort of thin client PC at each monitor?  In other words, have a single computer as the "server" with cabling to multiple monitors and the ability to display different images on each monitor.

My initial thought was to use Kindle devices since they can display PDFs and have wireless capabilities, but if this can be done cheaper or more simply, I'd love to know.

Thanks!

---

### Post by koenn on 2010-12-28
you can have 1 computer drive multiple monitors. Google "multi-head"or "multi-seat"
It typically requires multiple VGA cards.
It also requires tweaking.

Here's a setup with 6 screens (+ keyb and mouse; 6 seperate user sessions) on 1 PC. You can probably use such setup asd a strating point for what you want to do
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

---

### Post by timzak on 2010-12-28
> **koenn said:**
> you can have 1 computer drive multiple monitors. Google "multi-head"or "multi-seat"
It typically requires multiple VGA cards.
It also requires tweaking.

Here's a setup with 6 screens (+ keyb and mouse; 6 seperate user sessions) on 1 PC. You can probably use such setup asd a strating point for what you want to do
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

Very cool concept, thanks.  I don't think it will work for my situation, though.  It doesn't look stable enough for a production environment.  

What about a plain old 8 port video switch?  The terminals require no interaction.  They're just displaying a static PDF image.

---

### Post by HermanAB on 2010-12-29
You cannot send VGA video over long wires.

---

### Post by audiomick on 2010-12-29
> **timzak said:**
> Very cool concept, thanks.  I don't think it will work for my situation, though.  It doesn't look stable enough for a production environment.  
I think it is stable enough once it is up and running. I think the problem is more to get it running the way you want, and, in your case, determining what appears on which screen.
> 
What about a plain old 8 port video switch?  The terminals require no interaction.  They're just displaying a static PDF image.The problem could be that you are doing the reverse of what the switch is primarily intended to do. The switch is intended to choose between multiple sources for one destination. You want to send one source to multiple destinations. That would be a job for a matrix, but you don't need to be able to send any input to any output, I think. You just need to be able to say "this document to that screen", which shouldn't require a matrix, I think.

> **HermanAB said:**
> You cannot send VGA video over long wires.
True. I've seen 50 metres work, but I think that is pushing things a bit. There are, however, fairly affordable VGA to optical fibre converters available.

---

### Post by timzak on 2010-12-29
Here's a VGA splitter that claims to split your video signal to 8 monitors with high resolution and up to 65 meters:

[http://www.kvms.com/Product/VS98A.aspx](http://www.kvms.com/Product/VS98A.aspx)

Found some comparable ones at Newegg and Tigerdirect as well.  It's cheap enough to buy one for testing purposes.  Think it might work?

---

### Post by timzak on 2010-12-29
Now that I'm thinking about this, I'm starting to get a little more ambitious...could you have a supervisor's workstation and a bunch of monitors at various production seats, and from the supervisor's computer be able to see a small representation of each screen (like a multicam security system), with the ability to drag and drop whatever you want to show on each screen?  What would it take to do this?

---

