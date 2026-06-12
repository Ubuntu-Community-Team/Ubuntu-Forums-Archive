---
title: "Forward domain to mail server"
date: 2012-11-01
forum: Server Platforms
---

### Post by yc2 on 2012-11-01
Hi,

I need help understanding how to forward my domain to the mail server.

I enclose a screen shot from my account at my domain registrar. I have no current use of the domain and I wish to forward the IP to the web-server, which I think I have already done (A-record).

But I also want to make forwarding for mail. (The name of my registrar is loopia, they seem to have some forwarding already.)
(the forwarding to xxxx.tw I do not understand. I do not recognize the domain xxxx.tw, it must be something old that I entered by mistake long time ago?)

As I understand, I should just simply enter forwarding like
mail.mydomain.com type:MX
is this correct?

There are also entries for TTL and "Data" i do not know what to write there.

Thanks for guidance.

---

### Post by darkod on 2012-11-01
For mail you also need a host (A record) pointing to the correct public IP. Lets say you mail server is at 123.123.123.123.

In that case, you need to configure:
A record, called for example 'mail', pointing to 123.123.123.123
the MX record pointing to mail.yourdomain.com

This is because the MX record can't use IPs directly, it has to use a host name. And for that host you need to configure to which IP it points.

That's it. You should probably delete the mailforward records that seem to exist by default, or simly use one of them in the A record definition.

---

### Post by yc2 on 2012-11-01
Thank you, I appreciate.
After editing my account at the registrar it now looks as in the attachment.
I entered
mail.mydomain.com
as "data" but only "mail" shows up in the overview.

The servers can not be installed today, but as I understand this is the correct DNS data?

Thanks

---

### Post by darkod on 2012-11-01
And where is the mail record?

You need something similar to the www. You see how it says:
www   A   123.123.123.123

Create it like that:
mail   A   x.x.x.x

And then adjust the MX into:
MX   10   mail.domain.com (it needs the full FQDN name, not just mail)

PS. You can safely enlarge the TTL, that is Time To Live in seconds. 600 is only 10mins and since you don't plan to make many frequent changes I guess, you can have a much larger TTL. The Prio is priority but it's usually only used for mail servers, like 10 for the first, 20 for the second (if more than one), etc.

---

### Post by yc2 on 2012-11-01
Thank you for guiding me, I appreciate.

I can not follow the instructions because:

1. The registrars page will not allow higher TTL than 600. ("illegal value")

2. I can not change the MX record, when I edit it in the registrar's "DNS-editor" I enter it as "mail.domain.com" but when it lists in the overview (the attachment to the post) it will only come out as "mail". I think it is correct, just the listing incomplete?

3. It is not possible to enter an A record with the sub-domain "mail.domain.com". The "mail.domain.com" will not be accepted by the "DNS editor". Is it possible that the A-record I have entered under the heading "@" will fill that function?

Sorry for asking a mixed up question also depending on the registrar's way of listing things.

Thanks for your assistance.

---

### Post by yc2 on 2012-11-01
I have one computer physically, it has one IP. This IP is already pointed to by an A record. (For usage by the web server.)

Now I am adding a subdomain for the mail server. (mail.domain.com). But the mailserver is also located on the same computer as the webserver.

Now I am requested to add an A record for the mailserver. That A record will have to have the same IP as the A record for the web server

maybe this is the problem I have. I can not have the same IP for two A records (both for the domain and the the subdomain?)

If I only have one physical computer on one IP. It is then not possible to put the mail server on a subdomain (mail.domain.com)?

Maybe I must have both web-server and mail-server on the same domain (domain.com) if I only have one computer on one IP???

Sorry for messy question.

---

### Post by yc2 on 2012-11-02
Due to your help I think I finally understood the "DNS editor" of my registrar. I think this is what it should be, isn't it?
[http://img9.imageshack.us/img9/3213/subco.jpg](http://img9.imageshack.us/img9/3213/subco.jpg)

---

### Post by darkod on 2012-11-02
Hmm, I am not sure, it looks good but I am confused is mail.domain.com a subdomain, or a host. Maybe they just call it subdomain.

If I understand it correctly, mail.domain.com is only a host with A record pointing to the IP. And yes, you can have more than one A record pointing to the same IP, you can have many of them.

It looks OK to me like it is now, only I don't know whether your registrar makes a difference between a host and a subdomain.

---

### Post by yc2 on 2012-11-02
Thanks for your time.
I just know that I had to create a "subdomain" in the registrar's "DNS-editor".
It still doesn't work, though. Incoming and outgoing mail just "disappears" without any trace (like delivery error reports by mail etc, I haven't checked log file yet though). I think I must give it 24 hrs before it is sure to have effect over the entire Internet.
I'll report the result.
Thanks again, very useful to me. I grasped the basics now, A and MX record is what the mailserver needs.

---

