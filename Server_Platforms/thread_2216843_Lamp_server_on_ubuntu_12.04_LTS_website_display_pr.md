---
title: "Lamp server on ubuntu 12.04 LTS website display problem"
date: 2014-04-14
forum: Server Platforms
---

### Post by razvan2 on 2014-04-14
Hi guys, couple days ago I decided to host my wordpress website on my ubuntu machine.I installed everything by the book.Now I have a small problem ,after I have forwarded my ports and configure my ports.conf file , when I open my website in my intranet everything is ok but when I open it in internet my pictures are not displayed and my website looks like one of those old  html websites. the other disturbing thing is that is verry slow also ( now I don't know if it is because of my upload bandwith or something else).I have atached some errors from my error.log file. Any help will be very much apeciated. Thank you

---

### Post by SeijiSensei on 2014-04-14
None of those errors are relevant.  The ones referring to "favicon.ico" means you haven't created a little .ico file that appears in the tabs like the Ubuntu icon in the tab for this site.

The entry with all the gibberish is the result of someone trying to break into your server by sending it a particular string.

In the future, it would be more helpful if you copied those log entries into your post inside [noparse]```

```[/noparse] tags.  That would be a lot easier to read.

I don't know why you cannot see the images.  Can you open an image by navigating directly to its URL?  It could be a permissions problem.  Does the pseudo-user "www-data" that owns the Apache server process have permissions to read all the directories in the WordPress tree?

And, yes, your upload bandwidth could be a problem.  Test your connection by visiting [http://speedtest.net/](http://speedtest.net/).

---

### Post by razvan2 on 2014-04-14
What I have tried now is to access some of the links that my website displays....the thing is that when I access them somehow it directs me to the intranet...and my upload bandwith is 3 Mpbs

---

### Post by SeijiSensei on 2014-04-14
Take a look at /etc/fstab.  Is there an entry there that points your server's name to its local IP?  If so, remove it and force the server to rely on DNS to resolve your server's name.

---

### Post by razvan2 on 2014-04-14
I cannot see any entry or any IP at all in there...:(

---

### Post by Habitual on 2014-04-14
> **razvan2 said:**
> I cannot see any entry or any IP at all in there...:(

check /etc/hosts
That's what I believe he meant. :)

---

### Post by SeijiSensei on 2014-04-14
Whoops.   Shouldn't comment before coffee!

Yes I meant /etc/hosts.

---

### Post by koenn on 2014-04-14
> **razvan2 said:**
>  when I open my website in my intranet everything is ok but when I open it in internet my pictures are not displayed and my website looks like one of those old  html websites. the other disturbing thing is that is verry slow also ( now I don't know if it is because of my upload bandwith or something else

I've seen the same symptons during network trouble, so its not unlikely you simply have a bandwith problem. 
What appears to be happening is that the CSS and the image files don't make it through  (or your browser gives up waiting for them because it takes too long) so all you get is the plain html - that 80s-90s look.

---

### Post by razvan2 on 2014-04-15
Thank you for your answers, I believe this is the problem or at least the most probable one.I have though 3Mbps upload bandwith which you would think is enough but then again...

---

