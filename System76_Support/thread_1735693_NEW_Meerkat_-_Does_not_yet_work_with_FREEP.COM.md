---
title: "NEW Meerkat - Does not yet work with FREEP.COM"
date: 2011-04-21
forum: System76 Support
---

### Post by paddydd on 2011-04-21
Hi,
  I am setting up a Meerkat for my father-in-law and I am trying to get Firefox to work with FREEP.COM. This is the Detroit Free press Digital Media edition.

  When I start the web site, the screen never fully loads the content and it does not display the content correctly.

  I do not know where to start. This is a brand new install of UBUNTU 10.10 with all of the latest updates.

  Can anyone give me any guidance here.

Thanks
Paddy

---

### Post by Ranko Kohime on 2011-04-21
> **paddydd said:**
> Hi,
  I am setting up a Meerkat for my father-in-law and I am trying to get Firefox to work with FREEP.COM. This is the Detroit Free press Digital Media edition.

  When I start the web site, the screen never fully loads the content and it does not display the content correctly.

  I do not know where to start. This is a brand new install of UBUNTU 10.10 with all of the latest updates.

  Can anyone give me any guidance here.

Thanks
Paddy
I can't tell if I'm loading all the content here, so I'll post an image.

I'm running FFox 4 on 10.10.  The main Ubuntu repositories don't have 4 yet, the latest update it has is 3.6.2, I believe, so you have to add the FFox repository manually:

[http://techie-buzz.com/ubuntu/install-firefox-4-in-ubuntu.html](http://techie-buzz.com/ubuntu/install-firefox-4-in-ubuntu.html)

---

### Post by paddydd on 2011-04-21
HI,
  I downloaded 4.0 - thanks for the info.

  I can see text information but I cannot see any graphics. So I can click on the tab that says contents and then see the contents of the article in a pure text layout but I cannot see the nice graphical picture of the paper.

Is this a flash issue?

Paddy

---

### Post by Ranko Kohime on 2011-04-22
> **paddydd said:**
> HI,
  I downloaded 4.0 - thanks for the info.

  I can see text information but I cannot see any graphics. So I can click on the tab that says contents and then see the contents of the article in a pure text layout but I cannot see the nice graphical picture of the paper.

Is this a flash issue?

Paddy
Turning Flash off (which in 4.0 can be done without a browser restart :) ), results in the same page, so I don't think the images are Flash-based.

Check the error console: Tools -> Error Console.  Clear it, then reload freep.com.  I'm dropping a bunch of styles-related errors, but nothing image related.

Also, I'm assuming the browser loads images from other sites, but not freep.com?  freep.com may have gotten added as an exception to loaded images, check the prefs: Edit -> Preferences -> Content -> Load Images -> Exceptions

---

### Post by paddydd on 2011-04-23
Hi,
  Thanks for the information... I did check the error log and I see errors
from css for filters, fonts, something called GEL, font-size, and moz-opacity. I don't think they relate to my latest issue.

  I can see the freep but it behaves different from the windows version. In particular, when I click on an object, some of it's controls are not active -- in particular the printing. Do you have any idea why this would be different on UBUNTU vs windows?

thanks


Paddy

---

### Post by Ranko Kohime on 2011-04-26
> **paddydd said:**
> In particular, when I click on an object, some of it's controls are not active -- in particular the printing. Do you have any idea why this would be different on UBUNTU vs windows?
Assuming a printer is setup in Ubuntu?  (I'm not sure if Ubuntu or FFox would grey out printing options in the absence of a printer)

I'm getting a little baffled here, actually.  What other controls (if any) are greyed?

---

