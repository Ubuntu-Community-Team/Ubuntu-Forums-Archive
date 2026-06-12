---
title: "Browsers anomaly - can anyone explain this?"
date: 2010-08-28
forum: The Cafe
---

### Post by bluelamp999 on 2010-08-28
Hi,

Point Firefox, Chrome and Midori at this link - [http://www.e-bug.de/shop/shop_content.php?coID=90&item=8](http://www.e-bug.de/shop/shop_content.php?coID=90&item=8) - and compare the results.

It appears (on my system at least) that Midori is the only browser to correctly render the page.

Any idea what's going on here?

---

### Post by MasterNetra on 2010-08-28
> **bluelamp999 said:**
> Hi,

Point Firefox, Chrome and Midori at this link - [http://www.e-bug.de/shop/shop_content.php?coID=90&item=8](http://www.e-bug.de/shop/shop_content.php?coID=90&item=8) - and compare the results.

It appears (on my system at least) that Midori is the only browser to correctly render the page.

Any idea what's going on here?

Nvm, I see what your talking about after viewing through midori. The issue though is clearly on the site in, suppose to design with the other browsers in mind.

Though viewing the source from firefox, I get this for the center column.

```

		<!-- Center Column Start -->
		<div id="center">
		
			<div class="maincontent">
					<h1 class="h1topic"></h1>
	<br />
	
	<br />
<div class="right" id="add"><a href="javascript:history.back(1)"><img src="templates/ebug/buttons/english/button_back.gif" alt="Back" title=" Back " width="77" height="24" /></a></div>

        
			</div>
			
		</div>
		<!-- Center Column End -->


```

Yet its filled in Midori, so my guess the site is filtering/writing it based upon the browser

---

### Post by Frogs Hair on 2010-08-28
When I allow script and select the home tab on the page with Namoroka , content is loaded in the center of the page.

---

### Post by bluelamp999 on 2010-08-28
Here it is in Midori...




Here it is in Firefox...

---

### Post by MasterNetra on 2010-08-28
Tested Chrome & Chromium, Firefox, and Opera on linux and nothing in that column. Same for IE8 and firefox in windows. Its like they developed and tested it in Midori and assumed it would work right elsewhere.

---

### Post by bluelamp999 on 2010-08-28
It's bizarre isn't it?

It's not like Midori is a super-popular browser or anything...

---

### Post by hhh on 2010-08-28
It ain't no anomaly, it's bad markup. Invalid xhtml...
[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&charset=%28detect+automatically%29&doctype=Inline&group=0)
Invalid css...
[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&profile=css21&usermedium=all&warning=1&lang=en](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&profile=css21&usermedium=all&warning=1&lang=en)

---

### Post by MasterNetra on 2010-08-28
> **hhh said:**
> it ain't no anomaly, it's bad markup. Invalid xhtml...
[http://validator.w3.org/check?uri=http%3a%2f%2fwww.e-bug.de%2fshop%2fshop_content.php%3fcoid%3d90%26item%3d8&charset=%28detect+automatically%29&doctype=inline&group=0](http://validator.w3.org/check?uri=http%3a%2f%2fwww.e-bug.de%2fshop%2fshop_content.php%3fcoid%3d90%26item%3d8&charset=%28detect+automatically%29&doctype=inline&group=0)
invalid css...
[http://jigsaw.w3.org/css-validator/validator?uri=http%3a%2f%2fwww.e-bug.de%2fshop%2fshop_content.php%3fcoid%3d90%26item%3d8&profile=css21&usermedium=all&warning=1&lang=en](http://jigsaw.w3.org/css-validator/validator?uri=http%3a%2f%2fwww.e-bug.de%2fshop%2fshop_content.php%3fcoid%3d90%26item%3d8&profile=css21&usermedium=all&warning=1&lang=en)

+1

---

### Post by lovinglinux on 2010-08-28
> **MasterNetra said:**
> Tested Chrome & Chromium, Firefox, and Opera on linux and nothing in that column. Same for IE8 and firefox in windows. Its like they developed and tested it in Midori and assumed it would work right elsewhere.

Tested on Firefox 3.0.19, Firefox 3.5.9, Firefox 3.6.8, Firefox 4.0b4, Firefox 4.0b5pre, Chrome 6.0.490.1, Konqueror 4.4.2, Opera 10.61. Only Midori works.

---

### Post by mendhak on 2010-08-28
> **hhh said:**
> It ain't no anomaly, it's bad markup. Invalid xhtml...
[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&charset=%28detect+automatically%29&doctype=Inline&group=0)
Invalid css...
[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&profile=css21&usermedium=all&warning=1&lang=en](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fwww.e-bug.de%2Fshop%2Fshop_content.php%3FcoID%3D90%26item%3D8&profile=css21&usermedium=all&warning=1&lang=en)
Nothing to do with standards, though - browsers will still display it.  The problem with this page is that the content itself isn't being served in the markup; indicates something server-side. 

I was able to trace it to the presence of this the gzip/deflate header.  Chrome/FF/IE are sending this header to the page:

> Accept-Encoding: gzip,deflate

But I'm guessing that Midori is not sending that header or it's sending an additional header value - you would need to run Wireshark to find out.  I did a test in Fiddler and removing that header makes the page come back with the mainContent div filled in.

The content comes back as gzip/chunked in the main browsers but this is still a server side problem rather than a browser problem: somehow the rendering of the mainContent div is affected by the presence of encoding header, maybe the developers were trying to do something special there?

---

### Post by hhh on 2010-08-29
> **mendhak said:**
> Nothing to do with standards, though - browsers will still display it.  The problem with this page is that the content itself isn't being served in the markup; indicates something server-side.
You're right, I just never try and troubleshoot a webpage if the designer hasn't even run it through the W3 validators.

---

### Post by handy on 2010-08-29
Try changing the user.agent string in Firefox to say that it is Midori?

It may work.

---

### Post by mendhak on 2010-08-29
Oh forgot to mention that, changing User Agent doesn't help.  I'm pretty sure it has to do with that header.  I think the only way left is to send an email to the developers and ask :D

---

### Post by msch00 on 2010-08-29
Hi,
 
I'm a developer at e-bug.de. Thank you for your efforts on finding the error. 
But the problem you see isn't a &quot;browser anomaly&quot; - it's simply language-related. As you may see in the provided screenshots from bluelamp999, Firefox uses the not-so-well-maintained english-language shop-version, while Midori uses the german-language version. (compare button descriptions, etc.) I think this is related to the user agents language-setting. 
The FAQ-content isn't yet available for english-language shop-version. To view the content with a browser with UA-language set to english, you can use the text-links on the upper right of the page to switch to the german version.
 
Bye.

---

### Post by MasterNetra on 2010-08-29
> **msch00 said:**
> Hi,
 
I'm a developer at e-bug.de. Thank you for your efforts on finding the error. 
But the problem you see isn't a "browser anomaly" - it's simply language-related. As you may see in the provided screenshots from bluelamp999, Firefox uses the not-so-well-maintained english-language shop-version, while Midori uses the german-language version. (compare button descriptions, etc.) I think this is related to the user agents language-setting. 
The FAQ-content isn't yet available for english-language shop-version. To view the content with a browser with UA-language set to english, you can use the text-links on the upper right of the page to switch to the german version.
 
Bye.

So it is. I clicked on german while in firefox and loads. Thats something that needs to be fixed obviously.

---

### Post by msch00 on 2010-08-29
> **MasterNetra said:**
> So it is. I clicked on german while in firefox and loads. Thats something that needs to be fixed obviously.
 
Fixed now. Unfortunately, I wasn't able to translate all the content this fast, ;-) but at least I've configured the german-content to be visible in the english-language shop-version.

---

