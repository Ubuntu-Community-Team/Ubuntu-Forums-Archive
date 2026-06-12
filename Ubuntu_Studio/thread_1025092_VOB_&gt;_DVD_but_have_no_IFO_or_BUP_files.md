---
title: "VOB &gt; DVD but have no IFO or BUP files"
date: 2008-12-29
forum: Ubuntu Studio
---

### Post by foxmulder881 on 2008-12-29
I have some VOB files that I want to burn to disc. But the problem is, when I try to burn them in K3b, it complains with some errors telling me the movie disc will not be playable. And I suspect it's due to the selected VOB files don't have any other files with them.

So is there a way to burn simple VOB files to DVD?

---

### Post by 2hot6ft2 on 2008-12-29
Yes the other files would be needed for a dvd. Might try DeVeDe or ManDVD and see if they will create them for you.

Also vob's are basically mpeg4 files. You could change their extensions to mpg and try again with one of the above.

---

### Post by foxmulder881 on 2008-12-29
> **2hot6ft2 said:**
> Yes the other files would be needed for a dvd. Might try DeVeDe or ManDVD and see if they will create them for you.

Also vob's are basically mpeg4 files. You could change their extensions to mpg and try again with one of the above.

I'll try that, thanks.

Just a note too, vobs are actually mpeg2 not mpeg4.

---

### Post by 2hot6ft2 on 2008-12-29
> **foxmulder881 said:**
> I'll try that, thanks.

Just a note too, vobs are actually mpeg2 not mpeg4.
Didn't know that. I just know it works. Good luck

---

### Post by foxmulder881 on 2008-12-29
Actually I have just realized what the problem is.

The vob file I'm working with here is over 2GB. Because it was compiled from 2 different vobs to make one video for PC viewing. For PC viewing vobs greater than 2GBs isn't an issue, but when it comes to burning them to a DVD structure, **** hits the fan.

As far as I'm aware, there's no way to split vobs. Let me know if there is. :)

As a last resort, I'm going to try importing the vob into my DVD Authoring software, Kino, and try to set up a structure to burn that way.

---

### Post by foxmulder881 on 2008-12-30
I ended up finding the original 700MB avi's on my hard drive that I didn't even realize were there. A quick transcode and burn with tovid and I was back in action. Thanks for your help and suggestions 2hot6ft2.

---

### Post by euriconeto on 2009-05-14
Hi,

I have a related question, but not quite the same... Actually two:
1 - How do I edit vob files already in my computer using Kino (or similar app)?;
2 - How do I burn the files I saved in HD (when I was still running windows) back into DVD using linux apps?
I tried with Brasero but it always ends up with error message...
Cheers!

---

