---
title: "rsync excluding folder and it children"
date: 2007-11-08
forum: Server Platforms
---

### Post by twistedtwig on 2007-11-08
Hi all,

I am trying to set up some backup scrpts to save my self from stupidity... but seem to be having some issues with getting the exclude to work with folders.  In my test env I have

/home/jonh/test/sub1/text1.txt
/home/jonh/tes/sub2/text2.txt
/home/jonh/tes/sub2/sub3/text3.txt

```
rsync -ur --exclude=test1.txt --exclude=sub2/ /home/jonh/test/ /media/Elements/test/
```

The above command will exclude text1.txt and sub2 and all its children.. perfect I say.. then I think.. well with my actual situation there might be some other folder somewhere called sub2 that I want to keep.

So I try and fully path sub2 and this is where I run into problems.

```
rsync -ur --exclude=test1.txt --exclude=jonh/test/sub2 /home/jonh/test/ /media/Elements/test/
```

I have tried a number of variations on this including --exclude=/home/jonh/test/sub2 (with and without the end slash).

But I am not getting anywhere fast.

Does anyone have a nugget or two of wisdom for me please?

Thank you

---

### Post by MJN on 2007-11-08
To anchor the exclusion (i.e. not allow it to match anywhere it likes in the path) you need to state it relative to the source origin (/home/john/test/ in your case). Hence, your exclusion should be --exclude=/sub2

A leading slash anchors the pattern to the root of the source, the lack of a leading slash allows a match anywhere.

Make sense?

Mathew

P.S. At the risk of confusing the issue you might wish to use --exclude=/sub2/* as this will create the sub2 folder in the backup but nothing inside it (I use this method when backing up a full system but not wishing to backup mounted CDs etc yet still wishing to backup the mount point itself).

---

### Post by twistedtwig on 2007-11-09
Hi Mathew,

I just figured that bit out this morning.. had a thought last night and tried it out and was right... was just coming back to post my findings.

Thank you for your help (as always ;) )

Cheers

---

