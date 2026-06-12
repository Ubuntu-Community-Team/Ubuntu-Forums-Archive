---
title: "Using Kindle on Ubuntu"
date: 2010-08-19
forum: The Cafe
---

### Post by motorcity909 on 2010-08-19
Hi all

I'm thinking about getting a Kindle and wondered about people's experience using them on Ubuntu.

I know that books can bought direct from Amazon on the Kindle itself, no PC needed, but what about transferring my own files (pdf, pictures) to the Kindle?  Does it simply show as a removable hard-drive on Ubuntu and files can be drag & dropped onto it?

Also, the [app]("http://www.amazon.com/gp/feature.html/ref=kcp_pc_mkt_lnd?docId=1000426311") for synching books from PC to Kindle is only for Windows at the moment but I believe [Calibre]("http://calibre-ebook.com/") does the job just as well?  And it can convert ebook files that the Kindle wouldn't normally work with?

Cheers as always
Dave

---

### Post by Henry Flower on 2010-08-19
As you say, drag and drop works fine, or Calibre can transfer to the Kindle as well as doing conversions.  No problems at all.

---

### Post by NCLI on 2010-08-19
I second Henry. Install Calibre, it's an awesome little application. You won't have any problems with Kindle compatibility.

---

### Post by melle0616 on 2010-08-19
Installation 
Installation is simple as you will find Clibre in the standard repositories. So you will only need to issue a command like sudo apt-get install calibre. Or you can do the usual: 
Open up your Add/Remove Software application. 
Search for “calibre” (no quotes). 
Mark Calibre for installation. 
Click Apply to install. 
You can fire up Calibre either from the command line (enter calibre) or from the Applications > Office menu. As you will know (from previous Ghacks Calibre articles), the interface is simple. I won’t go over that. But I will walk you through the new first run wizard for setting up Calibre to be used with a Kinde. 
When you first fire up Calibre you will be asked to set up the application for your eReader. The first step you will see this in is shown in Figure 1. Make sure you select the correct version of the Kindle you own. 
In the next step you will set up how Calibre can send books to your Kindle without the device having to be plugged in. You will need to know your Kindle email address in order to set this up. Figure 2 shows the information you will need in order to get this working. You can use Gmail mail servers if you do not have access to an smtp server. I highly recommend you test the email settings before you move on. Upon a successful email test, you can then click the Next button to complete the setup. 
Sending books to your Kindle 
Let’s say you have already added a bunch of books to your Kindle. You don’t have your Kindle attached to your computer but you want to send a few books anyway. If you open up your library and right click a book you want to send you can select the book to be sent to your Kindle email address (see Figure 3). 
Yes, there are books on my Kindle written by me ;-).  As usual, the emailed book will only arrive to your Kindle if you have the Whispernet turned on. 
Final thoughts 
Managing your Kindle books is getting easier and easier. And thanks to applications like Calibre, the task only gets more seamless
via [www.gHacks.net](www.gHacks.net)

---

### Post by melle0616 on 2010-08-19
OR:
 
You would first need a Kindle "app" for your think pad.  If you have the app, then you can download the book.  
 
They currently have aps for PC, Mac, iPhone, iPad, or BlackBerry--no mention of ubuntu; but perhaps one of the apps is compatible with your system? They promise "more reading apps coming soon", but there is no indication what systems they will provide for. 
 
 
Go to this page to check out the downloads:
[http://www.amazon.com/gp/feature.html/ref=amb_link_352814002_3?ie=UTF8&docId=1000493771&pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-6&amp;pf_rd_r=0YVPHF169R5TX15EKQF0&pf_rd_t=1401&pf_rd_p=1261756042&pf_rd_i](http://www.amazon.com/gp/feature.html/ref=amb_link_352814002_3?ie=UTF8&docId=1000493771&pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-6&amp;pf_rd_r=0YVPHF169R5TX15EKQF0&pf_rd_t=1401&pf_rd_p=1261756042&pf_rd_i)
 
 
[FONT=Tahoma][crete]("http://**************.info/greece/") [/FONT]
[FONT=Tahoma][meatball sauce ]("http://www.dsmfoodlimited.com/recipes/meat/easymeatballrecipe.html")[/FONT]
[FONT=Tahoma][affiliate marketing ]("http://www.dsm-publishing.co.uk/affiliates")[/FONT]
[FONT=Tahoma][seo services ]("http://www.dsm-publishing.co.uk/services/seocampaigns.html")[/FONT]
[FONT=Tahoma][internet marketing services]("http://www.dsm-publishing.co.uk") 

[/FONT]

---

### Post by Docaltmed on 2010-08-19
Instead of buying a Kindle, I bought a Nook. It is far more friendly to open systems solutions, and handles a much wider variety of file types. I can upload epub, pdf, etc. without having to worry about (or pay for) conversions.

Nook uses the Android OS; Kindle is proprietary. Price is comparable.

The other nice thing about Nook is that I get a free book every Friday. Sometimes they aren't so great, but I've been turned on to a couple of good authors that way.

---

### Post by motorcity909 on 2010-08-19
Thanks everyone for your replies.  Knowing I can drag & drop files and that Calibre can do the job too convinces me to get a Kindle!!

I won't be able to use any of the existing Kindle apps as I'm running a desktop PC with Ubuntu (no Thinkpad ;)).

Cheers all
Dave

---

### Post by everytimeref on 2010-08-19
> **Docaltmed said:**
> Instead of buying a Kindle, I bought a Nook. It is far more friendly to open systems solutions, and handles a much wider variety of file types. I can upload epub, pdf, etc. without having to worry about (or pay for) conversions.

Nook uses the Android OS; Kindle is proprietary. Price is comparable.

The other nice thing about Nook is that I get a free book every Friday. Sometimes they aren't so great, but I've been turned on to a couple of good authors that way.

unfortunately we do not all live in North America...

---

### Post by markMDW on 2010-08-19
Great advice on this tread! One extra: As already mentioned you can easily set Calibri to email your Kindle translated books and documents etc. Be aware that the Kindle, by default, only accepts documents and emailed books from your default email address that was used to setup your Kindle account. That's so-as to defend against spammers sending you ebook junk. Can you imagine, if your Kindle accepted just anyone's email address you'd eventually be getting tons of advertisements for who knows what, and you'd hardly be able to find the books you actually wanted to read.
 
Now if you have a secondary and other additional email addresses that you want to accept ebooks from, then be sure to go to Kindle's "Manage My Kindle", on Amazon's site, and allow all the other email addresses that you may want to receive books from, for example from Calibri if setup to send from a different email address.

---

### Post by Calash on 2010-08-19
> **everytimeref said:**
> unfortunately we do not all live in North America...

You will have to educate me on this one.  I was under the impression that because of it's WiFi capability the Nook would be the better device to use outside of the US.

---

### Post by markMDW on 2010-08-19
The new Kindle will have wi-fi on all models.  I believe the chief advantage of the Nook will be the dual screen, one with color and touch menus.  Kindle would be better for those who like buttons and a compact size

---

### Post by NCLI on 2010-08-19
> **markMDW said:**
> The new Kindle will have wi-fi on all models.  I believe the chief advantage of the Nook will be the dual screen, one with color and touch menus.  Kindle would be better for those who like buttons and a compact size

And free worldwide 3G coverage.

---

### Post by motorcity909 on 2010-08-20
Regarding Calibre, will using that mean I can use .epub files on the Kindle?  

I believe Kindle doesn't support .epub files but Calibre converts them?

---

### Post by samalex on 2010-08-20
> **motorcity909 said:**
> Regarding Calibre, will using that mean I can use .epub files on the Kindle?  

I believe Kindle doesn't support .epub files but Calibre converts them?

Calibre can convert ePub files to Mobi, PDF, etc which the Kindle can use.  I'm planning on ordering a Kindle 3 next month (hopefully), so I'm already getting my media ready for importing through Calibre.  I have lots of books in PDF format, and with the new Kindle 3 supposedly having awesome PDF support I'm looking forward to that.

As for folks pointing to the Nook, I've done TONS of research on this, and though I like the lending aspects of the Nook, for me the biggest selling points for a Kindle are Text to Speech, better PDF support, TXT/DOC support, viewing docs in landscape or portrait, plus the browser works via 3G (Nook is only via Wifi).  ePub is a huge hit as I also have lots of ePub documents, but most were downloaded from Project Gutenberg so MOBI, Txt, or PDF versions are readily available.  Also Kindle is compatible with Audible, which is a nice perk.

Lots of folks mention Nook being more open since it's on Android, but honestly I'm not planning on hacking my Nook or Kindle so I'm looking at features outta the box.  If Nook were truly open and allowed Android apps to be installed to add the functionality it lacked (to complete more with Kindle), I would probably go with Nook.  But comparing Nook to Kindle 3, for me anyway Kindle 3 has more bells and whistles.  

Sam

---

### Post by drawkcab on 2010-08-20
This is interesting:

[http://www.bestebookreaders.com/hacking-kindle-running-ubuntu-on-kindle/](http://www.bestebookreaders.com/hacking-kindle-running-ubuntu-on-kindle/)

---

### Post by bookcrazy on 2011-06-25
I'm sorry I'm coming to this late but I absolutely LOVE my kindle, I sync it with Calibre, and it works like a charm.

---

### Post by Perfect Storm on 2011-06-25
[[img]http://s4.postimage.org/jbyj0j85e/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)

---

