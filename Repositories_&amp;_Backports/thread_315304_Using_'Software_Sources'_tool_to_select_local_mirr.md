---
title: "Using 'Software Sources' tool to select local mirror"
date: 2006-12-09
forum: Repositories &amp; Backports
---

### Post by jdpipe on 2006-12-09
Hi all

I would like to set Ubuntu to use a local repository for my software updates, rather than the usual one. In particular, I'm in Australia and my ISP will not deduct from my bandwidth allowance if I use their mirror of the Ubuntu repository.

I know that such a thing is possible by editing files (sources.list) directly, however I am also noting the entry in the System->Adminstration menu called 'Software Sources'.

This control panel thing opens up and shows a "Download from" box but this box only contains "Main server" and "Server for United States".

Shouldn't this box show a fuller list of Ubuntu repository mirrors? Is there a reason why it's not?

Cheers
JP

---

### Post by ShadowZ on 2007-03-21
bump...

i had this with "server for Portugal" selected... then i changed it to "main server" because for some reason i couldn't connect to the portuguese one...

Now the portuguese server doesn't appear in the list anymore...

it's probably something simple to solve but atm i have no clue... :S

thanks in advance

---

### Post by nyinge on 2007-03-22
> **ShadowZ said:**
> bump...

i had this with "server for Portugal" selected... then i changed it to "main server" because for some reason i couldn't connect to the Portuguese one...

Now the portuguese server doesn't appear in the list anymore...

it's probably something simple to solve but atm i have no clue... :S

thanks in advance
Isn't there an option called "others"?  If you click on it, you'll be able to choose the closest server by country.  In your case, it will be Portuguese.

---

### Post by Kateikyoushi on 2007-03-22
Isn't that a new feisty only feature ?

---

### Post by nyinge on 2007-03-23
> **Kateikyoushi said:**
> Isn't that a new feisty only feature ?
doh!  I'm sorry then.  I was looking at my Feisty and thought it was there.  My bad.  :D

Ok.  He/she then should simply edit the /etc/apt/sources.list file.  A sample line in the file, sources.list, should look like the following:
```
 deb http://us.archive.ubuntu.com/ubuntu feisty main restricted universe multiverse 
```The two letters "us" in "http://us.archive.ubuntu.com..." is the country code for United States.  You should change that country code to your desired country in all the lines in the file.  That should make the updater grab all the necessary updates from the nearest server.

---

### Post by ShadowZ on 2007-03-25
that did it ;) Thanks

---

### Post by jdpipe on 2007-03-27
So the answer to my original question is that this is not supported in Edgy, but it will be fixed in Feisty, right?

---

### Post by nyinge on 2007-03-27
Well...  yes, AFAIK that feature unfortunately was not implemented for Edgy, but you can follow my [previous post]("http://ubuntuforums.org/showpost.php?p=2340590&postcount=5") about changing the country code in the sources.list file.

---

### Post by jdpipe on 2007-03-29
I tried it and it didn't work. Where can I go to find a list of the supported country codes (ie those with a server)? Or is this done with DNS trickery and all countries supported?

---

### Post by nyinge on 2007-04-01
"[Ubuntu sources.list generator]("http://www.ubuntu-nl.org/source-o-matic/")" page came up as a top result after I googled for "ubuntu country sources.list".  Those weren't the best search keywords, but it did the trick.  :)

---

