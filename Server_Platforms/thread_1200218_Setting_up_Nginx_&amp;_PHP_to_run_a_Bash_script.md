---
title: "Setting up Nginx &amp; PHP to run a Bash script"
date: 2009-06-29
forum: Server Platforms
---

### Post by rmflagg on 2009-06-29
Hey everyone,
   I have had zero experience setting up a web server, so please bear with me if my questions seem a little simple.

   My Goal: To have a Nginx web server with PHP that can execute a Bash script.  That's all that I need to be able to do.  I am running Ubuntu 8.04.
   I have read about 15 different tutorials about how to set up Nginx with PHP and it seems that every one of them is different.  I haven't been able to get any of them to work.  I am not kidding.
   Seeing as this is all that I need to do, it should be fairly simple, right? ;)

   Now another question in case my goal is going about things the wrong way:  Do I need PHP in order to get Nginx to run a Bash script?

Thanks,
RMFlagg

---

### Post by jhannah on 2009-06-30
It sounds like you want to setup Apache with PHP and make use of exec() (see [http://us3.php.net/manual/en/function.exec.php](http://us3.php.net/manual/en/function.exec.php) for the full details on that function). What are you looking to get from using nginx? nginx is a proxy server and used to pass HTTP requests to a HTTP server which will actually run PHP but perhaps I am missing something here?

---

### Post by rmflagg on 2009-07-01
> **jhannah said:**
> It sounds like you want to setup Apache with PHP and make use of exec() (see [http://us3.php.net/manual/en/function.exec.php](http://us3.php.net/manual/en/function.exec.php) for the full details on that function). What are you looking to get from using nginx? nginx is a proxy server and used to pass HTTP requests to a HTTP server which will actually run PHP but perhaps I am missing something here?


Ok, let's suppose that I should not use Nginx(although as far as I can tell is is a HTTP server) and I should use Apache.

Here is what I need to do, and this is *ALL* that I need it to do:  I need the HTTP server(either Apache or Nginx) to serve *one* page.  That page will run a Bash script and then display a single JPG image that the script creates.  I don't need it to do ANYTHING else.  Period.

Now I must admit that when I start reading about setting up an Apache server, my eyes glaze over with a LOT of stuff that I don't understand and what I do understand, is unnecessary to my goal.

I don't know if "simple Apache configuration" is an oxymoron, or I am just the moron, but I really need this to be as simple as possible.

Sincerely,
RMFlagg

---

