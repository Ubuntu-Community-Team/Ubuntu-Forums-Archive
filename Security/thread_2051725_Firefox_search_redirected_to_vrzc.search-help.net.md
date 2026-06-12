---
title: "Firefox search redirected to vrzc.search-help.net"
date: 2012-09-01
forum: Security
---

### Post by plynch on 2012-09-01
I am trying a 12.04 LiveCD.  I configured Firefox to only allow connections to specific sites by setting up a manual proxy (Preferences->Advanced->Network->Settings) with the proxy set to "no access", port 80, and the checkbox "use this proxy server for all protocols" checked.  As a test, I tried a search in the Firefox field that goes to Google-- except that rather than going to Google, the URL in the location bar said "vrzc.search-help.net", and I also saw it trying (and failing) to connect to wwwz.websearch.verizon.net.

The Firefox on this LiveCD is 14.01.  I also have a Ubuntu 10.04 running Firefox 15, with the same settings, and there I do not get redirected; instead I get the expected message "Unable to find the proxy server".  So, I am wondering if there is a problem with the LiveCD, or if Ubuntu's Firefox was modified via one of the plugins to send searches to these sites (perhaps only if it can't reach the selected search provider, as in my case?)

---

### Post by cryptotheslow on 2012-09-01
Is your internet provider Verizon?

I wouldn't be surprised if Google put search cache engines in ISP networks (by commercial agreement not subterfuge!). Win for the ISP as they don't need to transit to Google for all the searches from their subscribers, win for Google as they don't need to reciprocate.

ISP's can be complicit here in subverting the common Google related DNS requests to their own caches and servers to preserve their own bandwidth.

There is a .....  sorry there was....   a reason why some people  shouted about net neutrality and ISPs just being pipes...... too late. It's sad.

---

### Post by plynch on 2012-09-02
Yes, my internet provider is Verizon (DSL).  However, I don't see how Firefox would know about that.  In my test with the Live CD, I actually had all internet access (except to localhost) disabled by the manual proxy settings.  So, in the attempt to connect to [www.google.com](www.google.com), there would have been no response (because the manual proxy was not there to answer.)  Also, if the issue were with Google or my ISP, then I should get the same result with my 10.04 Ubuntu, but I do not.

---

### Post by feydrutha on 2012-09-07
> **plynch said:**
> Yes, my internet provider is Verizon (DSL).  However, I don't see how Firefox would know about that.  In my test with the Live CD, I actually had all internet access (except to localhost) disabled by the manual proxy settings.  So, in the attempt to connect to [www.google.com](www.google.com), there would have been no response (because the manual proxy was not there to answer.)  Also, if the issue were with Google or my ISP, then I should get the same result with my 10.04 Ubuntu, but I do not.

I think Verizon hijacks NX domain replies to redirect you to their own servers. Try this: go to the website [http://dkdasklfjdsalkdfajueailae.com](http://dkdasklfjdsalkdfajueailae.com) in your browser. Yes, this is a random soup of letters, that is not registered (unless i was really lucky!). You will likely see a search page from verizon.

I don't know the reason for the difference between the two firefox versions, but it could be related to what the different versions do when a proxy does something unexpected (such as answer with a HTTP 300 redirect), or how they treat an odd-looking string in the proxy address field... 

If you want to know the details run wireshark to capture the traffic from your host and see what DNS and HTTP requests are going over the wire.

---

