---
title: "CSS content area/sidebar height question"
date: 2007-10-01
forum: The Cafe
---

### Post by bmeyer on 2007-10-01
I have a div containing my main content area with a footer at the bottom.  In this div is another div block, floating right (sidebar).  What's the easiest way to force the main content area to be at least as long as the sidebar (the sidebar is longer than the content in some pages, causing an overlap)?

Here's the problematic page:
[http://wynn.pescott.nl/2007/09/26/wynn-8-weken/](http://wynn.pescott.nl/2007/09/26/wynn-8-weken/)

Thanks in advance for any ideas.  I'd like to stick to CSS-only development (no tables).

---

### Post by proalan on 2007-10-01
The footer problem is more of a challenge than it should be. I had the same problem a few weeks ago. I applied the method from...

[http://ryanfait.com/sticky-footer/](http://ryanfait.com/sticky-footer/)

which only uses div to manage the containers. I think the solution in your case would be to have a container that contains your content area and sidebar, then a further div containing the footer.

---

### Post by bmeyer on 2007-10-01
Thanks.  That's definitely an option.

But is there a way to do it without using a completely separate div for the footer?  I'd like to keep the footer in the main content container (styling reasons)...

---

### Post by igknighted on 2007-10-01
> **bmeyer said:**
> Thanks.  That's definitely an option.

But is there a way to do it without using a completely separate div for the footer?  I'd like to keep the footer in the main content container (styling reasons)...

The clear isn't the issue, the float is too big to fit into the <div> it is in.  Either add an overflow:hidden or manually set the size of the box that has #subcontent floating in it.

EDIT: I would either change the height of the sidebar to 100% or set it manually, or else set the height of the #main div manually in order to make sure enough space is there.  Make sure you comment that somewhere so when you make changes you can very quickly make sure that the sizes are still correct.

---

### Post by bmeyer on 2007-10-02
> **igknighted said:**
> The clear isn't the issue, the float is too big to fit into the <div> it is in.  Either add an overflow:hidden or manually set the size of the box that has #subcontent floating in it.

EDIT: I would either change the height of the sidebar to 100% or set it manually, or else set the height of the #main div manually in order to make sure enough space is there.  Make sure you comment that somewhere so when you make changes you can very quickly make sure that the sizes are still correct.

Makes sense.  Thanks!

---

