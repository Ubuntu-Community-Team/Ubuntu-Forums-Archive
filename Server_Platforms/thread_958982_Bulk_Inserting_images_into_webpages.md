---
title: "Bulk Inserting images into webpages"
date: 2008-10-26
forum: Server Platforms
---

### Post by link2008 on 2008-10-26
Is there any program that will automatically insert images into html? I have around 20 albums, each with 100 or so pictures in them. I do not relish the idea of manually adding 2,000 images. I am hosting my website with apache.

PS I am sorry if this is the wrong place to post this.

---

### Post by link2008 on 2008-10-27
No one knows? Could someone at least point me in the right direction?

---

### Post by cariboo on 2008-10-27
Have you had a look at Gallery2, it is available in the repositories, you run it from the server and can do batch uploading.

Jim

---

### Post by Robstarusa on 2008-10-27
What you want to do would be better served by a dynamic page that pulles the image names/paths from the database.

---

### Post by KeyserSoze93 on 2008-10-27
In the top level of the album dirs:

```
for i in $(find -name *.jpg); do
echo "<img src=\"$i\">" >> gallery.html
done
```

Of course, you can tweak the html for the image, which is $i for all jpgs found, as long as you use \" for internal quotes.

---

### Post by link2008 on 2008-10-27
I don't mean to sound stupid, but is this a terminal command? If so, could you explain a little more thoroughy how I use it?

---

