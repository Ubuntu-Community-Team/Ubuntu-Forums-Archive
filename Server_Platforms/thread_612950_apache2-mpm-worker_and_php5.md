---
title: "apache2-mpm-worker and php5"
date: 2007-11-14
forum: Server Platforms
---

### Post by mneisen on 2007-11-14
Hi,

I would like to run apache2 with mpm-worker and php5, but as it seems, apt wouldn't let me do it ... :(

Is there any particular reason that this is not possible? Is there a work-around?

Thanks for you help!

Regards
mneisen

---

### Post by conjur3r on 2007-11-16
[http://au.php.net/manual/en/faq.installation.php#faq.installation.apache2](http://au.php.net/manual/en/faq.installation.php#faq.installation.apache2)

> 
62.1. 	 Why shouldn't I use Apache2 with a threaded MPM in a production environment?

PHP is glue. It is the glue used to build cool web applications by sticking dozens of 3rd-party libraries together and making it all appear as one coherent entity through an intuitive and easy to learn language interface. The flexibility and power of PHP relies on the stability and robustness of the underlying platform. It needs a working OS, a working web server and working 3rd-party libraries to glue together. When any of these stop working PHP needs ways to identify the problems and fix them quickly. When you make the underlying framework more complex by not having completely separate execution threads, completely separate memory segments and a strong sandbox for each request to play in, feet of clay are introduced into PHP's system.

If you feel you have to use a threaded MPM, look at a FastCGI configuration where PHP is running in its own memory space.

And finally, this warning against using a threaded MPM is not as strong for Windows systems because most libraries on that platform tend to be threadsafe. 


---

