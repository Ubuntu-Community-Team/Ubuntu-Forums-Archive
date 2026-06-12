---
title: "Suspicious Activity on Server"
date: 2011-09-02
forum: Server Platforms
---

### Post by baruch60610 on 2011-09-02
I have a VPS running Ubuntu 10.4.1.  My Apache access log files have been showing some puzzling activity that worries me.  The entries go like this:

```
174.123.174.34 - - [02/Sep/2011:07:04:53 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" **200** 470 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)" 
64.120.232.114 - - [02/Sep/2011:07:07:37 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" **200** 470 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)" 
174.123.174.34 - - [02/Sep/2011:07:07:51 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" **200** 470 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)" 
174.123.174.34 - - [02/Sep/2011:07:10:46 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" **200** 470 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)" 
174.123.174.34 - - [02/Sep/2011:07:13:41 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" **200** 470 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
...

```I don't think this is a good thing.  In particular, I am concerned because Apache is honoring these requests, as shown by the HTTP response code of 200 for the POST requests (in **bold**).  Even if this isn't something terrible, I am sure these folks do not have my best interests at heart.

I would like to make them go away.  I tried blocking the IP numbers through iptables.  This worked for the particular IP numbers, but then new ones kept popping up.  I feel like I'm playing Whac-A-Mole.

I understand that it is possible for me to use Apache rewrite rules to address this issue, but I am almost completely clueless about how to begin.  Also, I am not sure that this would be the most effective way to deal with the problem.  Heck, I'm not even sure it *is* a problem, to tell the truth.

So - I guess my questions are as follows:

[LIST=1]
[*]**Is** this a problem that I need to be concerned about?
[*]If so, what would be the most effective method for dealing with it?
[*]Where can I find more information about that method?
[/LIST]
I've tried the Apache documentation, but it is a bit dense and hard to understand.  Is there some other resource that mere mortals can read and understand?

I would appreciate any assistance anyone could give me.  Thanks...

Note:  To my best understanding, all my software is updated, including Apache and Wordpress.  There also have not been any unexpected file uploads or other evidence of an intrusion.  Of course, since I don't really know what I'm doing, this isn't as comforting as it might otherwise be.

---

### Post by SeijiSensei on 2011-09-02
Your server is probably not providing any real replies to these requests, just giving back the default page.

You can block requests from "any-request-allowed.com" by using the allow/deny features in Apache.  In the <Directory> container for your virtual host add this:

<Directory /path/to/my/website>
Order allow, deny
Allow from all
Deny from .any-request-allow.com
[other stuff]
</Directory>

See the documentation for [mod_authz_host]("http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html") for more details.

---

### Post by baruch60610 on 2011-09-02
SeijiSensei, thank you for this information.  I appreciate it.  I'll try what you suggested, and see how it goes.  I'll report back if I learn anything new.

Update:  OK, finally there was another hit, and it was accepted.  I'm obviously doing something wrong.  I'll review my various config files and such, and see whether I've missed something....

Update:  I *think* I see the problem.  I'm using authz_host to block traffic coming from .any-request-allow.com, but the traffic isn't coming from there - it's being sent there.  The latest hit was:

```
[FONT=monospace]
[/FONT]22.ae.7bae.static.theplanet.com - - [02/Sep/2011:12:06:26 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" 200 470 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"[FONT=monospace]
[/FONT]
```

The from changes, while the POST reference remains the same.  So I've got to figure out some way of rejecting stuff being sent to the offending address, instead of rejecting where it's coming from.  I think...

Suggestions?

---

### Post by SeijiSensei on 2011-09-02
Does the traffic always originate from 22.ae.7bae.static.theplanet.com, or is this coming from multiple hosts? I suspect the latter; otherwise you could firewall off that host in particular using iptables or deny it in Apache.

If your site doesn't require POSTs, you can deny them using something like this:

```

SetEnvIf REQUEST_METHOD ^POST$ post_request
<Directory /path/to/your/website>
[stuff]
Order Allow,Deny
Allow from All
Deny from env=post_request
</Directory>

```

[SetEnvIf]("http://httpd.apache.org/docs/2.2/mod/mod_setenvif.html") sets an environment variable called "post_request" if the REQUEST_METHOD is a POST.  This should categorically deny all post requests of any kind at your site.

If, however, you need to accept POSTs, you'd need a much more complicated regular expression in the SetEnvIf directive to discriminate between legitimate and illegitimate requests.  I'm not really sure how I'd design a test for that.  I think rejecting illegitimate POSTs is better handled in the application for which they are intended.  All my sites run PHP, and early on I test for whether there's a URL in the QUERY_STRING because that's a common exploit.  In reality, my server wouldn't be exploited by these probes, but I prefer to dump them early on in the page-creation task since they're not worth any more attention.

As I said, I don't think the traffic you're seeing is dangerous, either.

---

### Post by lisati on 2011-09-02
You might also want to take a look at [mod_defensible]("http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch") which can help block blog spammers. IP address 174.123.174.34 seems to be listed in [list.blogspambl.com]("http://blogspambl.com/lookup/174.123.174.34")

---

