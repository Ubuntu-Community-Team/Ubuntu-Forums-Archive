---
title: "Problem sending Apache Headers from PHP"
date: 2009-06-24
forum: Server Platforms
---

### Post by boyracerr on 2009-06-24
Hi, 

I have an Ubuntu VM which I use as a local development server for PHP applications. Currently I have a script which causes a file download by sending HTTP headers using PHP's header() function and then content.

This works fine on the live server (which I believe is a RedHat variant). However, on the Ubuntu server the headers are not sent; rather, normal headers are sent causing the binary file content to be dumped into the browser window.

Would anybody have tips as to where I might look for a solution? I'm assuming its a config thing due to the difference in behaviour of two servers with same codeset.

Thanks,
Ben

---

### Post by masux594 on 2009-06-24
The header must be the **FIRST** thing of the page..No spaces, no character, no lines before the header.. But, if the browser is able to display the file..for example, a *.css file, it will be displayed.. Hmm, if in another server the same page work differently, it's only a different configurations of the servers.. Do you want the configuration of the "real" server for your local server?

Sysc, A

---

