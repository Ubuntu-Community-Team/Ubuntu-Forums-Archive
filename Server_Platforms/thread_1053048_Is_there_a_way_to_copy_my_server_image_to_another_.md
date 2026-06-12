---
title: "Is there a way to copy my server image to another box?"
date: 2009-01-28
forum: Server Platforms
---

### Post by Maheriano on 2009-01-28
I have Apache2 installed on my desktop with a website all set up with PHP and some MySQL databases. I want this exact same setup on a standalone box I just set up with 8.1 server edition on it. How do I transfer everything over without having to rebuild everything? Is there an import/export option?

---

### Post by fjgaude on 2009-01-28
It's not something I do often but this works, whole disk to whole disk:

```
sudo dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror
```

You might want to read the **dd** **man** pages before you try this. It's best to not have the drives working at the time, but it still works even if the source is running your OS.

---

### Post by HermanAB on 2009-01-28
You can use netcat or ssh and dd:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by volkswagner on 2009-01-28
To do it with out the host OS running you can dd via a live CD.  If you don't mind adding the slave disk to the host machine.

This [how to works]("http://www.justlinux.com/forum/showthread.php?threadid=134457"), I tried it to image a windows box.

---

### Post by Maheriano on 2009-01-28
This looks like just copying the install right from one drive to another, including all files. I got a AMD64 8.1 Desktop Edition installed which is running Apache in the background. I also have a x86 8.1 Server Edition that I just finished setting up and has Apache running. I want to serve the webpages from the new box instead of my desktop for obvious reasons and don't want to recreate all the MySQL tables and users again. Can I just export the tables and users? Then I can just copy the public_html directory for each website.

---

