---
title: "Apache2 proxy_module proxy_html_module"
date: 2011-03-03
forum: Server Platforms
---

### Post by aSteve on 2011-03-03
By any chance can anyone offer a hint - I'm tearing my hair out... 

I'm successfully hosting an https site on my single available public facing IP address - but I want to expose a couple of internal web sites.  Essentially, I have:

[http://app1.example.com/](http://app1.example.com/)
[http://app2.example.com/](http://app2.example.com/)
[https://public_ssl.example.com/](https://public_ssl.example.com/)

I want to expose the pages from [http://app1.example.com/](http://app1.example.com/) as if they were hosted at [https://public_ssl.example.com/app1](https://public_ssl.example.com/app1) and [http://app2.example.com/](http://app2.example.com/) as if they were hosted at [https://public_ssl.example.com/app2](https://public_ssl.example.com/app2).

I get most of the way there by using mod_proxy and the directive:

  ProxyPass /app1 [http://app1.example.com/](http://app1.example.com/)

Unfortunately, for example, the site [http://app1.example.com/](http://app1.example.com/) references [http://app1.example.com/style.css](http://app1.example.com/style.css) using the relative URI "/style.css".  Sure, if designing these apps from scratch this would not be a choice I'd make - but I need to treat these apps as 'black boxes' - which means I need to do some sort of URL rewriting on the pages I serve as [https://public_ssl.example.com/app1](https://public_ssl.example.com/app1).

From the web I discovered that proxy_html_module is the recommended approach here - and then my problems began.  From the somewhat sparse documentation, I came up with the following configuration fragment:

  ProxyRequests Off
  ProxyPass /app1 [http://app1.example.com/](http://app1.example.com/)
  ProxyHTMLURLMap [http://app1.example.com/](http://app1.example.com/) /app1
  <Location /app1>
    ProxyPassReverse [http://app1.example.com/](http://app1.example.com/)
    SetOutputFilter proxy-html
    ProxyHTMLURLMap / /app1/
  </Location>

When I visit [https://public_ssl.example.com/app1](https://public_ssl.example.com/app1), I now get some errors.  The browser says:

"Content Encoding Error

The page you are trying to view cannot be shown because it uses an invalid or unsupported form of compression."

When I check the apache logs, I find these errors:
[Thu Mar 03 12:31:02 2011] [error] [client 10.10.10.128] Charset "utf-8" not su      pported.  Consider aliasing it or use metafix?
[Thu Mar 03 12:31:02 2011] [warn] [client 10.10.10.128] No usable charset infor      mation; using configuration default

Here, I've come unstuck.  Should I be thinking about aliasing character sets, and if so, how? What is metafix - is it really relevant?  All google suggested was the source code for the module... where I found this comment about the error message:

/* Unsupported charset.  Can we get (iconv) support through apr_xlate? */
/* Aaargh!  libxml2 has undocumented <META-crap> support.  So this fails
 * if metafix is not active.  Have to make it conditional.
 */

Is there a straightforward way to get this working under Ubuntu?  Am I making things difficult for myself trying to use ProxyHTMLURLMap?

---

### Post by aSteve on 2011-03-03
OK... The problem with character set is resolved using the line:

RequestHeader    unset  Accept-Encoding

Unfortunately, still, none of the URIs in the HTML are being translated...

---

