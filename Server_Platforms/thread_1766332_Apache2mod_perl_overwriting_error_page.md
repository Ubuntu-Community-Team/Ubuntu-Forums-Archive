---
title: "Apache2/mod_perl overwriting error page"
date: 2011-05-24
forum: Server Platforms
---

### Post by Frusty on 2011-05-24
Hi all,

I have a small problem with my mod_perl implementation.

I recently switched from CentOS to Ubuntu.

Within my mod_perl script, I do custom error handling and print() my own error messages. This worked perfectly on CentOS. I am setting a HTTP error code and return out of my code. Apache was always appending it's standard Error page to my output.

Now switching to Ubuntu and using the same code, Apache overwrites my output with the error page.

I have not found the correct method to get my custom (and dynamic) error pages back.

Anyone knows how I can turn of apache overwriting my mod_perl output, even though I generate an error response?

---

