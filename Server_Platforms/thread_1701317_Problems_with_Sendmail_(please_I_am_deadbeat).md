---
title: "Problems with Sendmail (please I am deadbeat)"
date: 2011-03-06
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-06
Hi everyone, 

I have an 10.10 ubuntu server, where I am running some CMS wrote on PHP. 
I need the php mail function so I installed the sendmail.

It works but the main problem was a painfull slow when try to send a mail (it did, but needs a minute or so).

Pray Google and finally discovered this: [http://www.flogiston.net/blog/2009/05/11/sendmail-painfully-slow-on-ubuntu/comment-page-1/#comment-14423](http://www.flogiston.net/blog/2009/05/11/sendmail-painfully-slow-on-ubuntu/comment-page-1/#comment-14423)

So, have to modify the /etc/hosts file. - I have done it, like this:

127.0.0.1    localhost localhost.localdomain example

And more examples.
But mails doesnt appear.

Now when I try to write as it was i cant send anything.

Please, what to do to make sendmail works and fix the /etc/host file. :confused:

Thanks in advance!!

---

### Post by Demented ZA on 2011-03-06
I posted about your /etc/hosts problem in the other thread you made. 
As for your mail problem, I'll need a little more insight into how things are set up, and how they should be set up.

First off, does your server have a static IP given by your isp? Is this IP set up as an MX record on your domain? That would be the yourdomain.com part in your e-mail address in the format of [email]you@yourdomain.com[/email].

If you don't know what the above is, or havn't set it up, this could be the reason for your mail problems.

You could set up your mail server to use a relay host, meaning your server forwards mails to another mailserver such as your isp's mailserver. You can also set your CMS to use your isp's server directly, and not even pass mails to the localhost.

using your isp's mail server directly from the cms is easier to set up, but the other option is more scalable.

---

### Post by acastrolorenzo on 2011-03-06
Thanks Demented ZA.

When first install sendmail it works but very slow and always sent to spam folder. I read something about MX but I am newbie and I am not sure what to do. And now, after edit /etc/hosts doesnt send anything.

I have static IP but well connected with NO-ip service, and from that static name to an usual domain.

Thanks again :)

---

