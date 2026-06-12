---
title: "Custom per-site CSS with Firefox"
date: 2005-03-06
forum: The Cafe
---

### Post by Ironi on 2005-03-06
I just found this Firefox extension called [URIid]("http://extensionroom.mozdev.org/more-info/uriid") that lets you override CSS elements on specific sites with userContent.css. What does this mean? You can change the color scheme of individual sites, among other possibilities. However, there is one caveat: Your CSS changes won't apply until pages are completely loaded.

Demonstration of the possibilities with GMail:
[http://persistent.info/archives/2004/10/05/gmail-skinning]("http://persistent.info/archives/2004/10/05/gmail-skinning")

Example userContent.css for this site (it's not meant to look good; it demonstrates the coloration for different elements):
```

body#www-ubuntuforums-org .alt1 {
	background-color: #D3D3DD /* grey */ !important;
}
body#www-ubuntuforums-org .alt1Active {
 	background-color: #D3D3DD /* grey */ !important;
 }
body#www-ubuntuforums-org .alt2 {
	background-color: #FAFFD2 /* yellow */ !important;
}
body#www-ubuntuforums-org .alt2Active {
 	background-color: #FAFFD2 /* yellow */ !important;
 }
body#www-ubuntuforums-org .tcat {
	background-color: #3FFFE9 /* cyan */ !important;
}
body#www-ubuntuforums-org .thead {
	background-color: #201DEF /* blue */ !important;
}
body#www-ubuntuforums-org .info {
	background-color: #0EEF17 /* green */ !important;
}
body#www-ubuntuforums-org .vbmenu_control {
	background-color: #EF0EEA /* purple */ !important;
}

```

BTW,  the [WebDeveloper]("https://addons.update.mozilla.org/extensions/moreinfo.php?id=60") and [ColorZilla]("https://addons.update.mozilla.org/extensions/moreinfo.php?id=271") extensions are quite useful for live CSS modifications and color matching (or finding hexadecimal values of colors), respectively.

Enjoy.

---

### Post by jensyt on 2005-03-06
[QUOTE=Ironi]BTW,  the [WebDeveloper]("https://addons.update.mozilla.org/extensions/moreinfo.php?id=60") and [ColorZilla]("https://addons.update.mozilla.org/extensions/moreinfo.php?id=271") extensions are quite useful for live CSS modifications and color matching (or finding hexadecimal values of colors), respectively.[/QUOTE]
Might I also suggest [EditCSS]("https://addons.update.mozilla.org/extensions/moreinfo.php?id=179") for live CSS modifications, since it is much more lightweight than WebDeveloper. The reason I know is because I just did this same thing for these forums yesterday. :D

---

### Post by Ironi on 2005-03-06
Whoops, I originally specified userChrome.css instead of userContent.css (it should be the latter). Sorry about that. :-k

---

