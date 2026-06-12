---
title: "Create new WWW directory apache"
date: 2011-05-13
forum: Server Platforms
---

### Post by euhiemf on 2011-05-13
Hi!, I’m new the Linux and Apache there. I want to make a image directory in the WWW folder. It works fine, but when I link to the images on the page it stands that I don’t have permission to the picture, 403. How do I set the permission?!

Thanks for answers!

---

### Post by Lars Noodén on 2011-05-13
Something like this:

```

sudo chmod o=rx /var/www/images

```

---

### Post by euhiemf on 2011-05-13
Thank you so much!! it worked!!! :popcorn:

---

