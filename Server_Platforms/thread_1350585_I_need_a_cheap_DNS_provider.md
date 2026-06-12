---
title: "I need a cheap DNS provider"
date: 2009-12-09
forum: Server Platforms
---

### Post by Joakim Stokland on 2009-12-09
Hi!
I am setting up a server, and need a DNS provider. I was hoping you can help me find one. I already have a private domain (.net) I want to use, and I was planning on using ZoneEdit, but I found out now that they don't support the letter "ø", and my domain contains it. I have dynamic IP. Got any suggestions? I don't want to pay too much...
Thanks!

---

### Post by slakkie on 2009-12-09
I use xname.org, dunno if they support dynamic IP's in zonefiles. Registration and service are free, so have a look.

---

### Post by argosreality on 2009-12-09
> **Joakim Stokland said:**
> Hi!
I am setting up a server, and need a DNS provider. I was hoping you can help me find one. I already have a private domain (.net) I want to use, and I was planning on using ZoneEdit, but I found out now that they don't support the letter "ø", and my domain contains it. I have dynamic IP. Got any suggestions? I don't want to pay too much...
Thanks!

You might have a problem with ANY dns provider. According to netregister.biz> What are the valid characters for a domain name and how long can it be ?
When choosing the name for your domain, always remember that: - **you *can't* use stressed vowels (such as à, é, ò, etc.);** - you *can't* use symbols (such as ' + . , | ! " £ $ % & / ( ) = ? ^ * ç ° § ; : _ > ] [ @ ); - the name's length must range between 3 and 63 characters (excluding the extension); - the name can neither start nor end with the character "-", although the character "-" is allowed inside the name. So, to name your domain you can use any letter, numbers between 0 and 9, and the symbol "-". .

Length may vary, from 3 to 63 types.So you might just be sunk

---

### Post by Joakim Stokland on 2009-12-09
Xname doesn't accept my domain because of the "ø"-letter. Neither do everydns.net and editdns.net.
Any more suggestions, please? It doesn't have to be a free service, as long as it isn't too expensive.

I guess there HAS to be a DNS provider that allows that letter. For instance, a norwegian electronics dealer, Elkjøp, uses the web address [www.elkjøp.no](www.elkjøp.no). Is there any way to find out wich DNS provider Elkjøp uses at least?

---

### Post by i.r.id10t on 2009-12-09
> **Joakim Stokland said:**
> Xname doesn't accept my domain because of the "ø"-letter. Neither do everydns.net and editdns.net.
Any more suggestions, please? It doesn't have to be a free service, as long as it isn't too expensive.

I guess there HAS to be a DNS provider that allows that letter. For instance, a norwegian electronics dealer, Elkjøp, uses the web address [www.elkjøp.no](www.elkjøp.no). Is there any way to find out wich DNS provider Elkjøp uses at least?

Do a whois on their domain - it will tell you the primary and secondary name servers for them.

Of course, if you have 2 ips you can do your own primary and secondary DNS.

---

### Post by ian dobson on 2009-12-09
Hi,

Have a look at zoneedit, I've been using them for years and have never had a problem.

Regards
Ian Dobson

---

### Post by holastickboy on 2009-12-09
I currently use dyndns.com  It cost me about $30 for a years worth (dns hosting, and .com name)

---

### Post by cdenley on 2009-12-09
The DNS standards don't allow it, so good luck finding someone to host it. Even if you do, some users might have problems.

Maybe in the near future:
[http://news.bbc.co.uk/2/hi/8326241.stm](http://news.bbc.co.uk/2/hi/8326241.stm)

---

### Post by Joakim Stokland on 2009-12-09
My registrar just replied on my question.
There a technique called IDN that allows national characters in domains. Older browsers don't allow this technique, but newer do.
When using IDN, the server is dealing with two domains - there's one technical domain in addition to the standard with international characters. So the domain I have to use with DNS providers is a modified version of the domain, containing a few extra characters, and of course without the international character. My registrar gave me the technical domain, so now I should hopefully get everything up and running :-) Thanks for the help!

---

### Post by joes7 on 2009-12-09
There is a completely free one. It is called freedns.afraid.org . You can get hundreds of subdomains such as .info.tm. 

Good luck, by the way

---

### Post by HighCommander540 on 2009-12-10
Why has no one mentioned no-ip.org yet? It is the leader of free DNS. I use it for all of my domains. And oyu can also get paid support and more domains. Although< i didn't know there were so many free DNS providers.

---

### Post by gabo.cr on 2009-12-10
I use OpenDNS, I have no complaints at all.
It is used by schools and business.
It also gives you a great filter that you can set up.
:wink:

---

