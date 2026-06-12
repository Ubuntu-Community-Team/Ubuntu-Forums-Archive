---
title: "svg and mozilla 2.0.0.10"
date: 2007-12-01
forum: The Cafe
---

### Post by engine on 2007-12-01
According to [http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html), "SVG support is built in to Mozilla Firefox 1.5.x/2.0 and SeaMonkey 1.0.x."

This assertion does not appear to be entirely true <g>  and after a lot of clicking I found [http://developer.mozilla.org/en/docs/SVG_in_Firefox](http://developer.mozilla.org/en/docs/SVG_in_Firefox)

This page explains a) that two modules (animation and font) are not implemented at all, and b) that quite a lot of others are only implemented in Firefox 3

Anyone have any idea whether we might get Firefox 3 for Ubuntu? or do I just need to upgrade from 7.04?

---

### Post by Colonel Kilkenny on 2007-12-01
> **engine said:**
> According to [http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html), "SVG support is built in to Mozilla Firefox 1.5.x/2.0 and SeaMonkey 1.0.x."

This assertion does not appear to be entirely true <g>  and after a lot of clicking I found [http://developer.mozilla.org/en/docs/SVG_in_Firefox](http://developer.mozilla.org/en/docs/SVG_in_Firefox)

This page explains a) that two modules (animation and font) are not implemented at all, and b) that quite a lot of others are only implemented in Firefox 3

Anyone have any idea whether we might get Firefox 3 for Ubuntu? or do I just need to upgrade from 7.04?

I don't think they're updating to Firefox 3 in 7.04. In 7.10 there's Firefox 2 as a default but you can install Firefox 3 as well (firefox-granparadiso is package name). Maybe that package is available in 7.04 repos?

And yeah, Firefox lags behind with svg-support if we're comparing it to Opera (not quite sure what the situation in Webkit is atm). I'm currently developing my own webpage as a some sort playground for new stuff and I can assure you that SVG as a div background totally rocks when you need to have scalable background image with rounded corners...
I'm pretty much loving all the new stuff Opera 9.50 is offering (CSS3 selectors, SVG stuff, etc.)

edit. Here are the charts: [http://www.codedread.com/svg-support.php](http://www.codedread.com/svg-support.php)

---

