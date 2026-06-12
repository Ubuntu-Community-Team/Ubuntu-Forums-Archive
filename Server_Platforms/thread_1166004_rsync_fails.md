---
title: "rsync fails"
date: 2009-05-21
forum: Server Platforms
---

### Post by b-boy on 2009-05-21
Hi Guys

I have a regional server where we store Linux images and when an image is changed we rsync the image to our Branch servers. The Problem I am having is some Branch server dont get the new image for various reasons (power, network ...etc) and the only way I can see this is if I log on the each server and do a MD5 on the image. This would have been easy if I had less Branch servers but I have 700. 

My question:
Is there a way I can see if the rsync failed from the regional server?

I have checked the rsync.log and it does indicate some errors but I found that the errors does not necessary mean the Branch server did not get the image

---

### Post by albinootje on 2009-05-21
> **b-boy said:**
>  This would have been easy if I had less Branch servers but I have 700. 


You could make a script on those machines, and let it only email you when the md5sum is incorrect.

Let me give you an example what I'm thinking of. 
At work I have a cronjob running which informs me about new empty (zero bytes) files.
It's simply a diff between a known listing (ls -laR) vs. a new listing.

You could rsync the new md5sum in a text file first, and then compare that (diff) with a cron scheduled automated md5sum written to another new file.
If the diff does find a difference you will be emailed. If there's no difference, no email is received.

This assumes that if you have a power-failure the machine will be
brought up again, and then the comparison will be made.

---

### Post by HermanAB on 2009-05-21
Send the MD5 Sum as well as the image by rsync.  Then when done - at the bottom of the rsync script, test each transfer with for example: 
ssh user@regionalserver "md5sum -c sumfile" 

and note the failures.

---

### Post by Alekz_ on 2009-05-21
If you want to know if the command run successfuly, just take the exit code:

```
rsync SRC DST; echo $?
```

If the exit code is equal to 0, then the command runs ok, else, there was an error!

You can also run rsync with "-v" option, which shows verbosily what's going on!

The `md5sum` idea is pretty nice, but I don't know if it'll work for you!

[]'s

Alekz_

---

### Post by b-boy on 2009-05-22
Thanks guys I will try all your options :D

---

### Post by b-boy on 2009-05-22
> **albinootje said:**
> You could make a script on those machines, and let it only email you when the md5sum is incorrect.

Let me give you an example what I'm thinking of. 
At work I have a cronjob running which informs me about new empty (zero bytes) files.
It's simply a diff between a known listing (ls -laR) vs. a new listing.

You could rsync the new md5sum in a text file first, and then compare that (diff) with a cron scheduled automated md5sum written to another new file.
If the diff does find a difference you will be emailed. If there's no difference, no email is received.

This assumes that if you have a power-failure the machine will be
brought up again, and then the comparison will be made.


How can i send a mail from the server?

---

