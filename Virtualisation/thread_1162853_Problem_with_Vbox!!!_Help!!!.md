---
title: "Problem with Vbox!!! Help!!!"
date: 2009-05-18
forum: Virtualisation
---

### Post by swrx on 2009-05-18
I installed Vbox. It worked fine. But few days ago it's background became transparent. it can see on screenshot. how can i fix it? 

Edit bodhi.zazen: screen shot deleted. Please do not post such large screen shots, use thumb nails "hot linked" to a larger image.

---

### Post by miwaypet on 2009-05-18
Has there been a recent kernel update. That will cause it to stop working. Try running this command in terminal:

```
sudo /etc/init.d/vboxdrv setup
```

Hope that helps.

---

