---
title: "One of my server's domains are showing the 404 error"
date: 2017-11-15
forum: Server Platforms
---

### Post by ianobe on 2017-11-15
One of my 2 websites I have running on my Ubuntu 17 Apache2 webserver is not appearing while the other is. Both websites ran when I first set up the websites until I was working on one that displays the other for marketing purposes. I looked at everything I know but nothing seems wrong. I've opened both .conf files for the 2 websites and both seem to be configured the same with the required changes made. I've rebooted Apache 2 and the entire server but I'm still having issues. Please help.

```
Not Found: The requested URL / was not found on this server.
Apache/2.4.25 (Ubuntu) Server at skysharksphoto.com Port 80
```

---

### Post by slickymaster on 2017-11-15
Thread moved to **Server Platforms** from the Resolution Center

---

### Post by ianobe on 2017-11-15
Thank you for the transfer slicky

---

### Post by ianobe on 2017-11-16
I found the solution. The .conf redirectory was miswritten. I forgot that when I made the file that holds the website it was missing a keyword and in the conf I included that keyword in the directory.

---

