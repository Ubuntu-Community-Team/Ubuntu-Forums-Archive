---
title: "free service to point MX at?"
date: 2013-06-20
forum: Server Platforms
---

### Post by SlugSlug on 2013-06-20
Not really a ubuntu question, but a year or so after setting up a mail server I'd like to shut down my PC :)

anyone know a free service I can point MX record to an download via IMAP / POP ?

---

### Post by darkod on 2013-06-20
Hmmm, that would be a free email server. I haven't seen that yet. However, there are providers offering only email hosting for as low as 2&#8364; per month: [http://www.netim.com/hosting/e-mail/spamora.php](http://www.netim.com/hosting/e-mail/spamora.php)

---

### Post by SlugSlug on 2013-06-20
Thats not bad, surely it would cost me more than that to run my PC 24/7 ? Am also looking in to WOL over tinternet so if needed I can just wake it up to ftp etc if you have any advise on that (I don't mean google for me I've done that just after experience)

---

### Post by SeijiSensei on 2013-06-20
If you have a registered domain, your registrar might offer email hosting as a free or inexpensive add-on service.  My registrar, DirectNIC, has such an [option]("https://directnic.com/features/email.php").

---

### Post by SlugSlug on 2013-06-20
Thanks, am with 123-reg.co.uk I've set MX to their defaults but the control panel wont update (~24hrs). Its unclear if it's free or charged atm. I respect both of your comments throughout the forum and would like to take the opontunity to ask if either of you host your own services or use 3rd party?

I've just flattened 24/7 server thinking running costs might be to high to out way the usefulness. Am running about 9 SATA's + a SSD, it was used for a game server / forum but that died off. I like the handiness of being able to ssh in to check stuff out / help with work diagnostics (I don't have much luck with exchange (or windows for that matter) logging).

---

### Post by sandyd on 2013-06-20
If you want, Windows Live supports mx hosting for custom domains. See here -> [http://domains.live.com/](http://domains.live.com/)

---

### Post by SeijiSensei on 2013-06-20
> **SlugSlug said:**
> Thanks, am with 123-reg.co.uk I've set MX to their defaults but the control panel wont update (~24hrs). Its unclear if it's free or charged atm. I respect both of your comments throughout the forum and would like to take the opontunity to ask if either of you host your own services or use 3rd party?

I maintain two virtual servers at [Linode](http://www.linode.com/), one in New Jersey and one in California.  The CA server is my DNS primary; the one in NJ is my secondary.  This conforms to the requirement of having two servers and follows [best practices]("http://www.zoneedit.com/doc/rfc/rfc1912.txt") that suggest the servers be both topologically and geographically separate to ensure redundancy.

I run CentOS on both machines and use bind9 to host my domains.

---

### Post by SlugSlug on 2013-06-21
Turns out I can use a free mail service with 123-reg, thanks!!

SeijiSensei ~ so where am paying 123 to manage my DNS you do yours yourself? I was under the impression it would have to be some form of trusted source like root servers or ISP's etc

---

### Post by SeijiSensei on 2013-06-21
Anyone can manage the DNS for a domain they own if they register the two required nameserver addresses with their registrar.  I generally encourage people to use their registrar's servers since it is easier to manage, but that is not required.  That's especially true if you only have one or two domains.  I manage about a dozen domains myself and am a secondary to a friend's primary with another few dozen domains.  Being a secondary is particularly simple since you don't need to maintain the domain's zone files.  You just create entries in named.conf for each domain telling the server what the primary's IP address is like this:

```

zone "example.com" {
     type slave; 
     file "example.com";
     masters { 10.10.10.10; };
};

```

That tells the server that the master records are at 10.10.10.10 and that a copy of them should be stored in the default directory under the filename "example.com".

---

### Post by SlugSlug on 2013-06-21
Ahh ok dunno why but it never crossed my mind to point nameservers at your own box. Not needed for me but good to know - thanks

---

