---
title: "Apache 2"
date: 2006-08-08
forum: Server Platforms
---

### Post by dareofficer on 2006-08-08
Could someone help me start my Apache2 page please?  I just need a simple [http://local](http://local) page started.  So I can file serve in my home.  I have it all downloaded and installed, I just don't know how to link the files to the *. /var/www/??

Thanks

---

### Post by em3raldxiii on 2006-08-08
Mmm ... going off memory here (I'm at work).  As far as I can remember, all ya gotta do is place an **index.htm** file in your /var/www/ directory.  You have to have sudo access to do that if I remember correctly.  I often just use my terminal command line and do this:
 
```

cd /directory/that/holds/my/file.html
sudo cp myfile.htm /var/www/

```

---

### Post by alamba on 2006-08-08
The default page of apache should already be in your /var/www. Just use a browser to go to [http://localhost](http://localhost)

A

---

### Post by dareofficer on 2006-08-09
Thanks, got it going.

---

