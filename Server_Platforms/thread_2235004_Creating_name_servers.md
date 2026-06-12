---
title: "Creating name servers"
date: 2014-07-18
forum: Server Platforms
---

### Post by mhm5000 on 2014-07-18
Hi
I'm a web developer and I want to host DNSes of sites that I develop.
Let's assume that I have 3 servers in 3 locations.
after deciding which one I want to be **ns1**, what should I do?
I couldn't find a simple solution on the web.
Let's assume my portfolio is on X.com
[LIST=1]
[*]I want to point X.com to ns1.X.com [IP1] and ns2.Xcom [IP2] (I believe it's called glue record),
[*]I want a simple gui for dns.X.com, where I could simply enter information of each domain name and the backend, sync the information with IP1 and IP2,
[*]And that's It
[/LIST]
Is there any ready to use package or a well written article on creating this kind of thing?

Is Ubuntu the best choice for this matter?

P.S:
If I have 100 sites and each of them 1000 requests per day, How many BandWidth are we talking about?

;)

---

### Post by TheFu on 2014-07-18
Below are my opinions. Others will have different opinions and claim that I'm paranoid and that they've never been hacked. Great. Until you get hacked, it is hard to understand ...

Running a DNS on the internet is fraught with security risks.  DNS is hacked all the time and professionals have problems doing it well.  They are still failing from time to time.  12 yrs ago, my DNS server was hacked.  I've learned to pay a professional to manage DNS servers while I retain management of the records. Look at the security history for DNS to gain a better understanding of why.

Do NOT run DNS and a website on the same machine. That is asking for trouble.

If you insist on running your own, be certain you setup 2 or 3 redundant DNS servers.  Also, it would be smart to run these servers internally for 6+ months first, before putting them on the internet, so you get familiar with the day-to-day aspects. There are many best practices for running DNS that I've never seen written in a book. Perhaps I'm just not reading the correct books?

DNS servers don't need much CPU or bandwidth ... if they do, then that server is under attack.  100 sites with 1,000 requests is NOTHING, assuming an average size DNS request. A rasberry Pi could serve that traffic.  DNS queries are cached, so a proper client will only request updated information 1-2 times a week (or after a reboot), unless you set the refresh time too small.  YOU have control over how long the DNS data is cached by clients (other DNS server and real client devices).

A hacked DNS can completely break everything else related to a domain - EVERYTHING. To the point that nothing from that domain can be trusted. Not certs, not emails, not websites.

---

### Post by mhm5000 on 2014-07-18
Thanks @TheFu ...
I'm going to spend more time on learning more about DNSes.

But I still need that Web Application that said in my first post.

Although if I know the full concept, I may create it myself.

---

### Post by TheFu on 2014-07-18
DNS is managed by text files of a specific format.  There are probably more user-friendly methods, I just don't know them, since the text files are known, understood, and work.  Be careful running anything except BIND with DNSSEC - just sayin'.  For internal DNS, there are lots of options, since security isn't that big of a concern.

Start here: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
I should point out that we've all written scripts to create the initial files for DNS. That part is relatively easy. The hard part is handling odd requirements. The subtle complexity of BIND configuration ... well, I suppose you've seen that already.  Don't forget to run BIND inside a chroot.  I wasn't when my server was hacked.

Oh - and do not place your master DNS server on the internet - just put slaves there and ensure the master cannot be reached from the internet directly - ever. Review this short paper [http://www.sans.org/reading-room/whitepapers/dns/security-issues-dns-1069](http://www.sans.org/reading-room/whitepapers/dns/security-issues-dns-1069) to understand the concerns more.

---

### Post by mhm5000 on 2014-07-19
Thanks for the links... They were great, but I still need a good enough application, article for starting...

Anybody to rescue???

---

### Post by SeijiSensei on 2014-07-21
Why do you need to maintain a DNS server at all?  I would start by checking whether your domain name registrar offers DNS hosting on its servers.  Many registrars will host your DNS records for free as part of their service package.

Remember that you have to maintain *two* DNS servers, a primary and a secondary, in order to conform to Internet standards. Do you want to devote the resources to doing so?

---

### Post by mhm5000 on 2014-07-23
Thanks for the advice...
But I need to do this

---

