---
title: "geo tagging photos concerns"
date: 2010-08-19
forum: The Cafe
---

### Post by sdowney717 on 2010-08-19
[http://www.flickr.com/groups/geotagging/](http://www.flickr.com/groups/geotagging/)

lately I have been wondering If I post online photos, can someone somehow trace it back to my physical address?
Say you post a photo and a thief sees it and gets interested.

I read where celebrities homes have been discovered by geotags in photos they posted.
DO the pictures I would post from a cell phone contain geo tags?

---

### Post by ihatetryingtopickaloginna on 2010-08-19
The IPhone does, but it can be turned off. I guess others are the same way. I have it turned off for photos.

---

### Post by stmiller on 2010-08-20
PS: in Ubuntu, you can stip the geo tag and other data with imagemagick.

Install imagemagick:

```
sudo apt-get install imagemagick
```

Then just run this command:

```
mogrify -strip mypicture.jpg
```

Or do a whole directory of pictures:

```
mogrify -strip *.jpg
```

---

### Post by MCVenom on 2010-08-20
On Android you can turn it on or off from the Camera app itself.

---

