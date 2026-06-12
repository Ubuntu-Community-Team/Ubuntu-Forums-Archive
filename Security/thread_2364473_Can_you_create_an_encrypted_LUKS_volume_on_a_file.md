---
title: "Can you create an encrypted LUKS volume on a file?"
date: 2017-06-23
forum: Security
---

### Post by Paddy Landau on 2017-06-23
I know how to create and use an encrypted LUKS partition.

My question is how to create a file as an encrypted virtual partition. I know that I can use [VeraCrypt]("https://www.veracrypt.fr/en/Home.html") for this, but I'd like to migrate away from VeraCrypt in favour of LUKS.

If it's not possible, I'll stick with VeraCrypt, as it is a good product.

---

### Post by &amp;KyT$0P# on 2017-06-23
This worked for me - [https://www.digitalocean.com/community/tutorials/how-to-use-dm-crypt-to-create-an-encrypted-volume-on-an-ubuntu-vps]("https://www.digitalocean.com/community/tutorials/how-to-use-dm-crypt-to-create-an-encrypted-volume-on-an-ubuntu-vps")

* I notice they've deprecated the article.  Not sure why, as those steps seemed to work fine for me in Xubuntu 16.04, but maybe I missed something. :-k

---

### Post by #&amp;thj^% on 2017-06-23
Or even this method: [http://willhaley.com/blog/encrypted-file-container-disk-image-in-linux/](http://willhaley.com/blog/encrypted-file-container-disk-image-in-linux/)

---

### Post by Paddy Landau on 2017-06-24
Much simpler than I imagined! Thank you.

---

