---
title: "Which browsers compress html for faster download?"
date: 2012-04-05
forum: The Cafe
---

### Post by Kdar on 2012-04-05
I know Opera does it with its Turbo mode (not sure which compression it uses):
[http://www.opera.com/browser/turbo/](http://www.opera.com/browser/turbo/)

Does anyone know other browsers that can do this or support this?

---

### Post by lovinglinux on 2012-04-05
I am not sure which compression they use either. Turbo mode doesn't work for me very well. It is slower than regular browsing.

All major browsers can deal with compression, but that depends on the site ability and configuration to use gzip. Additionally, depending on the platform, you can also compress and trim CSS, HTML and Javascript before sending to the client.

Also look at SPDY [http://en.wikipedia.org/wiki/SPDY](http://en.wikipedia.org/wiki/SPDY)

---

### Post by sudodus on 2012-04-05
Opera does this compression via its own servers, that read the original web pages and make a slim version that is sent to you (and probably saved for reuse, if/when others ask for the same page).

I don't know any other browser that works this way. But some web pages have a fancy and a light version, so that you can get the information with or without eye candy depending on your bandwidth.

---

### Post by Kdar on 2012-04-05
Yes, I know with some you can turn off ability to display images and such. But I was more referring to gzip compression.

I saw this post on GoogleDevelopers site, about gzip pre-compression, but I don't know if Google uses it now somewhere. Plus that page is from 2009.
[https://developers.google.com/speed/articles/gzip](https://developers.google.com/speed/articles/gzip)

---

### Post by lovinglinux on 2012-04-05
> **sudodus said:**
> Opera does this compression via its own servers, that read the original web pages and make a slim version that is sent to you (and probably saved for reuse, if/when others ask for the same page).

I don't know any other browser that works this way. But some web pages have a fancy and a light version, so that you can get the information with or without eye candy depending on your bandwidth.

Is not exactly a browser feature, but a service provided by Opera. You could achieve the same result with a third-party proxy with ability to compress and trim the pages, using any other browser. Opera turbo is just more convenient, because you can easily switch it on/off, you don't need to install an extension and the proxy server is offered by Opera.

---

### Post by lovinglinux on 2012-04-05
> **Kdar said:**
> Yes, I know with some you can turn off ability to display images and such. But I was more referring to gzip compression.

I saw this post on GoogleDevelopers site, about gzip pre-compression, but I don't know if Google uses it now somewhere. Plus that page is from 2009.
[https://developers.google.com/speed/articles/gzip](https://developers.google.com/speed/articles/gzip)

If you are browsing a web site that is properly optimized and uses gzip, then Opera Turbo won't help. It probably will make it worse, since they need to process the pages before forwarding to you.

---

### Post by sudodus on 2012-04-05
> **Kdar said:**
> Yes, I know with some you can turn off ability to display images and such. But I was more referring to gzip compression.

I saw this post on GoogleDevelopers site, about gzip pre-compression, but I don't know if Google uses it now somewhere. Plus that page is from 2009.
[https://developers.google.com/speed/articles/gzip](https://developers.google.com/speed/articles/gzip)
I have not heard or read that gzip is used automatically. I think that big files are fairly well compressed anyway (jpeg and pdf files), and the html scripts are rather small, at least for broadband connections.

---

### Post by Kdar on 2012-04-05
Well, gzip compresses and decompresses files pretty fast, compared to others (not best compression ratio, but probably good enough).
HTML files should actually compress very well.

---

### Post by spynappels on 2012-04-05
The gzip encoding is controlled by the content server, not the browser.

As long as the browser sends the ```
Accept-Encoding: gzip, deflate
``` HTTP header, the content server can choose whether it wants to gzip the data it send back, if it is capable of doing so.

This is also one of the techniques often used by mobile data providers to help their infrastructure cope with current data demands.

---

### Post by sudodus on 2012-04-05
> **spynappels said:**
> The gzip encoding is controlled by the content server, not the browser.

As long as the browser sends the ```
Accept-Encoding: gzip, deflate
``` HTTP header, the content server can choose whether it wants to gzip the data it send back, if it is capable of doing so.

This is also one of the techniques often used by mobile data providers to help their infrastructure cope with current data demands.
I'm reading and learning. Do you have any idea of how common it is that the content servers offer gzip encoding (<1%, ~10%, >30%)?

---

### Post by madjr on 2012-04-05
i think fasterfox extension does it for firefox.

---

### Post by Kdar on 2012-04-05
> **sudodus said:**
> I'm reading and learning. Do you have any idea of how common it is that the content servers offer gzip encoding (<1%, ~10%, >30%)?

yes. I would like to know that too.

--
@madjr Thanks

---

### Post by SeijiSensei on 2012-04-05
The version of Apache running on my CentOS servers loads mod_deflate by default.  I thought server support for compression was pretty widespread.

It probably matters hardly a whit on most sites; HTML documents are usually just a few thousand bytes.  Back in the days when we were on 33.6 modems, compression mattered, but today, I doubt you'd notice it at all.

Remember that the large objects like graphics are already highly compressed.  Indeed re-compressing a JPEG would actually slow down the delivery of the object.

---

### Post by spynappels on 2012-04-06
> **sudodus said:**
> I'm reading and learning. Do you have any idea of how common it is that the content servers offer gzip encoding (<1%, ~10%, >30%)?

I should be able to give you a reasonably accurate answer next week, I need to pull some stats, but won't be able to do that until the middle of next week.

---

### Post by lovinglinux on 2012-04-08
I just found that since Opera 11.10, images are converted to WebP by the Turbo proxy server. That can make a lot of difference. However, if the page is not in the server cache, it will probably take longer to load.


> Opera 11.10 gave Speed Dial  a new look, and changed the image format in Opera Turbo to WebP.

> The technology behind Opera Turbo is a proxy server with server-side compression of webpages. A compression rate of up to 80% can be achieved, in part by reducing the quality of images. If you want to view an image uncompressed, right-click on the image, and select "Reload Image in Full Quality".

---

### Post by spynappels on 2012-04-10
I did some number crunching, and for the logs I have been able to check, the results can be summarised as below:

In one 24 hr period proxy server x handled 38914015 individual requests.

Of these, 4753678 requests received gzip encoded responses and none received a deflate encoded response from content servers.

This suggests that approximately 12.2% of traffic routinely gets gzip encoding applied at the content server.

The one caveat is that there were also 10884551 requests where the client indicated that it was unable to accept gzip encoded data. I suspect the iPhone is a culprit in this scenario.

---

### Post by MisterGaribaldi on 2012-04-10
Unless you're running a dial-up connection, it seems to me that compressing basic data would give you additional overhead that would subtract from performance.

---

