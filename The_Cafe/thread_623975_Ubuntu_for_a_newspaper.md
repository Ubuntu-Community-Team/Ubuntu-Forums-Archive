---
title: "Ubuntu for a newspaper"
date: 2007-11-26
forum: The Cafe
---

### Post by arigram on 2007-11-26
I work in a small daily newspaper in Greece and we are expecting a dramatic makeover pretty soon which among others, will mean a full replacement for our aging computer systems.
At the moment, about fifteen computers, including the server work with very old hardware and software including MS Windows 2000 and even 98.
I have been running Ubuntu on my personal laptop at work with no problems since 6.06 and recently converted my home desktop to 7.10.
Considering our options and the fact I have a direct say for what systems will be installed in the future, I am seriously considering Linux, especially Ubuntu that I have experience with.
The primary choice of Apple Macs is a poor one because of the very bad support of the local representative that all Greek Mac users dislike. Windows XP will be a backwards step and there is no way I will be letting Vista in the newspaper. That leaves Ubuntu.
My main concern is the availability of Desktop Publishing software at least equal to the capabilities of Quark Express 6 we work with. Other software, just leaves Open Office and Firefox that wouldn't be hard to switch to.

So, what are your thoughts on the matter?

---

### Post by bruce89 on 2007-11-26
Personally, I'd use LaTeX for proper typesetting, not OO.o.

---

### Post by maruchan on 2007-11-26
Take a look at Scribus, [especially this page]("http://wiki.scribus.net/index.php/Success_stories"). Check out [Le Tigre's]("http://www.le-tigre.net/IMG/pdf/lt003.pdf") amazing work they do in Scribus. :shock: (Circular layout starts on page 12)

I can't say it's a 100% pleasurable experience, working in Scribus. It's more like 85% for me. But it's software freedom, you can use experimental over stable very easily (install scribus-ng), and there is good documentation on the wiki.

---

### Post by arigram on 2007-11-27
Bruce, your are not serious about making journalists use LaTeX are you?
Its way too programmer-y for one used to MS Word not to scared by.
OO.org is a good idea because apart from using it for a while now in the newspaper, it practically works and looks like Word so the transition should be smooth.

Scribus looks like a good replacement for Quark, thank you Maruchan. Ofcourse I will need to learn both application so I can promote and finally train the others in using them which is not a small thing. 
At the worst of circuimstances we'll just get a couple of Macs for the typesetting.

The only other problem I see is what to do with the present archive which is all in the propriety formats of Quark and Word. Plus, the other difficulty would be to force people to use ODF instead of Word Doc when all the other media uses the MS format (which would be a problem when communication with the outside world)

It won't be 100% smooth and easy that's for sure.

Thank you for your answers.

---

### Post by HermanAB on 2007-11-27
Use PDF for communicating with the outside world.

---

### Post by arigram on 2007-11-27
> **HermanAB said:**
> Use PDF for communicating with the outside world.

There lies the problem: other media will be sending doc and Quark formated documents to us and probably will be expecting the same.
PDF needs extra software to be edited and possibly to be display if the recipients haven't installed a viewer in their machines.
Apart from our own newspaper no other will be accepting ODF or even PDF as formats open for sharing and editing, although regarding PDF that is something I will need to research further.
The difficulty will be to convincing people to use ODF when all external documents will be in doc and to share our own will need to be converted first to doc, which unfortunately is not very intuitive and raises the question of using ODF in the first place. Philosophy takes second place to practicality in a business.

If the whole newspaper is set up with Linux, we are talking about power, flexibility, security, stability, maintenance and of course ethics, but compatibility would be a problem.

One idea will be to have an ftp or http place in the server to place documents to be available to the outside world with some automation or interface to be converted to the required format. That ofcourse means that someone has to build it and of course the formats will be restricted to ODF, doc and PDF.

---

### Post by p_quarles on 2007-11-27
In my experience, OpenOffice.org Writer is very competent at reading and creating MS Word .doc files. I don't believe it works with the newest specification (.docx), and it won't format everything exactly right, but for reading the kinds of documents that would normally be submitted to a newspaper it should be more than enough.

In any case, every word processor in existence supports .rtf, so that's a good fallback in case you ever run into a difficulty. 

And, of course, there's MS Office running in Wine.

---

### Post by popch on 2007-11-27
What I find a bit unexpected that you want to be able to ***receive*** documents in Word format.

Rather, it is ok to receive them. What I do not really understand is: why do you want to keep the formatting?

The newspaper people I hear of receive their texts in 'any' format. They then remove all formatting as a first thing and apply their own formatting.

Those who do not do that find themselves with texts which will not re-flow or will contain hyphens in the middles of the lines and newlines in the middles of sentences and all that which comes from ineptly formatted documents.

---

