---
title: "Help with script to compose and send email"
date: 2008-09-08
forum: Server Platforms
---

### Post by chuck252 on 2008-09-08
Hi, 
 I've been looking for a way to automate sending an email. I am looking to grab some images using wget, then embedding those images in an email.

I already have POSTFIX running and sending mail, as well as the wget command pulling in the images. 

I'm having some trouble with the email however. Can someone point me in the right direction? It isn't too hard to add the images as attachments, but I really need them to be embedded. 

Thanks
Chuck

---

### Post by inphektion on 2008-09-08
best way to send attachment through script is with mutt or nail.  I'd install mutt and do something like this:
mutt -s "Subject" -a /path/to/attachment recipient << EOF

Body of mesg here
more body...
EOF

if you don't need a msg body then just << /dev/null instead of EOF.
for multiple just keep listing them after the -a I think like 
```
mutt -s "Subject" -a /path/to/attachment /path/to/attachment2 recipient << EOF
```

---

### Post by chuck252 on 2008-09-08
Thanks. But that is where I am. I need to embed the image attachment into the body of the email. So the person can view it without opening the document. I've been playing with MUTT and MAILX, and even SENDMAIL. 

I'm doing this:
```
 mutt -e 'set content_type"text/html"' outbount@address.internet -s "Subject" < mailattachment.html 
```

The mail has an attachment but the html doesn't have the image showing. Do I need to include it as another attachment?

---

### Post by inphektion on 2008-09-08
Hmmmm... that seems rather difficult.  At least more difficult than I originally thought till I google searched for the past 15 minutes.  Anyway here are my leads for you.
1.  Maybe try metasend where you do multiple mime-type definition so define text/html for your web page but all image/png or whatever for your image.  

My question with this is how are you referencing the image in your html file?  with <img src> etc?

Then I thought what if the img src isn't grabbing it off the system and that's why the image isn't there.  Well if its possible for what you are trying to do you can actully EMBED the image to the html then use the exact command you are using now and that would work.  Might be difficult to script embedding an image into an html file though.  See this for how to do that:
[http://www.campaignmonitor.com/blog/archives/2008/08/embedding_images_revisited.html](http://www.campaignmonitor.com/blog/archives/2008/08/embedding_images_revisited.html)

---

### Post by chuck252 on 2008-09-09
Thanks. I'll look into this and try to report my results.

---

### Post by schettj on 2008-09-09
Host the image somewhere - email an html body with an <img> tag pointing to the hosted image.

Of course, any email reading program worth its salt will block said images until the receiver "oks" viewing unsafe images.

Why exactly do you want to do this? Most people would think it rude, or spammish, or malwareish these days. Sad, but true - my first thought was (and still is) "he's up to no good"

Just send as attachment and allow the receiver to decide if they want to view the image (after virus checking, verifying they know you, etc, etc...)

---

### Post by chuck252 on 2008-09-09
>  "he's up to no good" 

I can see your point of view on that. I didn't think about it until you said something, but it really isn't anything rude, or malware related. 

I just want to send out some rrd graphs attached to some reports. The catch is that some of these have to go outside the firewall, and hosting those images outside isn't an option. Just that simple. 

And what you are suggesting is exactly what I'm doing on the inside of my firewall. I'm now just stepping it up a level.

---

### Post by schettj on 2008-09-09
> **chuck252 said:**
> I just want to send out some rrd graphs attached to some reports. The catch is that some of these have to go outside the firewall, and hosting those images outside isn't an option. Just that simple. 
Just send them as mime attachments then. Most decent mail readers will give the reader the option to "view inline" - evolution (*nix) and outlook (m$oft) do, for example.

Sorry about waving the red flags. I just spend way too much time fighting the email garbage - last thing I want to do is be an enabler ;)

So, googling (email with embedded graphics) around, this looks like the mojo

[http://code.activestate.com/recipes/473810/](http://code.activestate.com/recipes/473810/)

(it's the cid: protocol in the image URL that pulls it from the attachment)

Best of luck...

---

### Post by chuck252 on 2008-09-09
Thanks, that works with a little bit of tinkering. You really need to add ```
 #! /usr/bin/python 
``` to the beginning to get it to work correctly. 

Otherwise it looks good. You guys have made my life easier, thanks.

---

