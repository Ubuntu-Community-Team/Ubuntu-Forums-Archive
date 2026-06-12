---
title: "Apache on hardy"
date: 2009-07-30
forum: Server Platforms
---

### Post by Xeekder on 2009-07-30
Hello,

recently finished installing apache but i can't see any pictures on my website, first it just tell me (404) forbidden, then i change permission on www/var giving it "r w x "and now i am able to see html and flash but absolute no pictures at all, any idea i'm using no-ip because i have a non fixed ip i have created a rule in router's firewall to allow http traffic coming and everything seems to  work fine also maybe someone know if it necesary or dangerous to give the x "execute" permision to www/var it's sounds dangerous tought, thanks in advance,

---

### Post by hessiess on 2009-07-30
> **Xeekder said:**
> Hello,

recently finished installing apache but i can't see any pictures on my website, first it just tell me (404) forbidden, then i change permission on www/var giving it "r w x "and now i am able to see html and flash but absolute no pictures at all, any idea i'm using no-ip because i have a non fixed ip i have created a rule in router's firewall to allow http traffic coming and everything seems to  work fine also maybe someone know if it necesary or dangerous to give the x "execute" permision to www/var it's sounds dangerous tought, thanks in advance,

Check the paths to your images, and giving execute permissions isnt a problem unless you have a inscure file uploader.

---

### Post by Xeekder on 2009-07-30
Hello thanks for your quick answer, i have been checking but no luck the webpage works when it's uploaded to a free webhosting, i tried to change the subfolder read permission where the pictures lies so i ended up copyn it directly from my usb whit permissions cp -ar but no pictures at all any idea?

---

