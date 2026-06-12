---
title: "Apache 2 frontpage support"
date: 2011-05-29
forum: Server Platforms
---

### Post by invader7 on 2011-05-29
Hello , it is possible for apache2 (debian) to host a frontpage page ? all links i found from google and microsoft said that frontpage is dead. how can i host the site ?

---

### Post by ruffEdgz on 2011-05-29
I don't know how much you know about apache or frontpage but will need to explain some things:
---
* Frontpage isn't a hosting provider, its editor
* Frontpage has been discontinued as of 2006 so I would advise not using it as an editor ([http://office.microsoft.com/en-us/frontpage-help/the-next-generation-of-microsoft-application-building-and-web-authoring-tools-HA010120522.aspx](http://office.microsoft.com/en-us/frontpage-help/the-next-generation-of-microsoft-application-building-and-web-authoring-tools-HA010120522.aspx))
* Apache is an 'open-source HTTP server' as stated on their website
* Apache is a tool and you will need a server to host this tool and your sites along with it
---
Now that we have some information on this matter, apache should be able to hand a basic website if you need it but depending on your situation, find the provider to host that site is a bit tricky. Is this for personal use or is this for a business? If this is for you, I would look into hosting providers and since I don't want to drop any names, I would suggest looking at a site like this to find one that fits your needs: [http://www.webhostingreviews.com/](http://www.webhostingreviews.com/)

If you are doing this for a company type setting, then I would see if that company has a tech department to ask them this question.

Hope this helps.

---

### Post by Lars Noodén on 2011-05-30
> **invader7 said:**
> Hello , it is possible for apache2 (debian) to host a frontpage page ? all links i found from google and microsoft said that frontpage is dead. how can i host the site ?

Front page creates very poor HTML, but quality is not anything that should help or hinder actual uploading to the server.  It may be included by default.  Have you tried connecting as-is?

Have you considered upgrading website editors to [Bluefish](http://bluefish.openoffice.nl/index.html) or [Kompozer](http://kompozer.net/)?

---

### Post by SeijiSensei on 2011-05-30
FrontPage is not just an HTML editor.  It also relied on server-side cgi-bin executables to handle a variety of tasks. Microsoft released versions of the binaries for Unix platforms, but [prospects look very dim](http://www.rtr.com/fpsupport/) for finding this software any longer.

You'd need to examine the FP code carefully to see whether it has procedures that rely on the server-side binaries.  Most of these handled tasks like like forms processing.  If the site doesn't require these, then you can just host the HTML pages with Apache.  If the site does require the server-side stuff, you may have to rewrite those functions in a server-side language like PHP.

After this experience is over, perhaps your client will see why it's advisable to stick to software that relies on open standards for Internet applications.

---

### Post by invader7 on 2011-06-01
thanks, it's for business , i don't have the site in order to try as it is but the client told me that my apache should support frontpage extensions. probably i will not accept to host their site , discontinued means no support even from google

---

