---
title: "Ubuntu iso images download directed to cloudfront.net: What is cloudfront.net?"
date: 2015-10-30
forum: Security
---

### Post by tiredman2 on 2015-10-30
Hi, I have a bit weird question, that I really hope that somebody can clarify.

I downloaded Lubuntu from "**cdimage.ubuntu.com/lubuntu/releases/15.10/release/lubuntu-15.10-desktop-amd64.iso**" and was a bit suprised when the download redirected to "**d33vwem6kwnf57.cloudfront.net/lubuntu-15.10-desktop-amd64.iso**". Well no big deal, I thought it's just some mirror, but I wondered about the strange "d33vwem6kwnf57" so decided to ask Google what is this "cloudfront.net". I was extremely shocked about the search results, as many of them were "How to remove cloudfront.net Virus" and "Cloudfront popup virus" and so on. So this got me a bit scared I must say. I also searched Ubuntu forums and found this thread [http://ubuntuforums.org/showthread.php?t=2190408](http://ubuntuforums.org/showthread.php?t=2190408) from what I understand that somebody using Linux was also affected by this virus.

I did a bit more digging around and found out that Cloudfront actually is some Amazon service of some kind, and there should be nothing dangerous using it?

But as the Google search results were so shocking, I am very confused: If Cloudfront.net is safe, then what is cloudfront.net virus? How can there be a virus with the same name as some Amazon service? Is it not "bad PR" to use the service for ubuntu downloads, if the address ends up being random (the "d33vwem6kwnf57"-part) and if it is known that if somebody search the site address (the "cloudfront.net"-part) he will get such "shocking" search results?

And also if there is a virus called "cloudfront.net" that has nothing to do with "Amazon Cloudfront" can it affect Linux also, as the ubuntuforum post would suggest? Or did I understand it wrong? The response was rather relaxed, considering that this would indicate that there is a nasty virus in the wild that can affect Linux machines?

---

### Post by Habitual on 2015-10-30
Amazon CloudFront is a content delivery web service. and is completely safe to use content  delivered from there.
"How to remove cloudfront.net Virus" google results. well it's google. Relax, it's Linux.

---

### Post by SeijiSensei on 2015-10-30
I was curious so I did a search for "cloudfront.net virus".  There are dozens of pages about this though few from major antivirus companies like Kaspersky.  It appears that the messenger is being blamed for the message.  Apparently there is a JavaScript or similar exploit that redirects web requests that happens to have been distributed from servers in cloudfront.  That's not too surprising given how easy it is to spin up an AWS instance.  Neither cloudfront nor Amazon are behind this exploit, but they are getting the blame.

---

### Post by kostkon on 2015-10-30
Most of the files on the internet are served by [CDN]("https://en.wikipedia.org/wiki/Content_delivery_network")s nowadays. Nothing strange about Ubuntu isos being on cloudfront.net

---

### Post by tiredman2 on 2015-11-14
Thank you for your answers. I tried downloading the same iso again, and now it is back to cdimage.ubuntu.com. From ubuntu podcast I found out that there was some error or something and that's why the iso images went thru cloudfront for awhile. So everything is back to normal, although the virus thing (if you don't believe me, just google it to see yourself) is still confusing me, but I guess it's more of a Amazon PR problem, and is off topic here. I still do not understand the forum post that I linked where somebody using ubuntu said they were affected by the cloudfront virus. But the whole thread is a bit vague, so maybe I am seeing something in there that is not in there in reality.

---

