---
title: "How would I detect if my website is a victim of domain shadowing?"
date: 2022-09-23
forum: The Cafe
---

### Post by Paddy Landau on 2022-09-23
Today, I discovered a black hacking technique called [domain shadowing]("https://www.bleepingcomputer.com/news/security/domain-shadowing-becoming-more-popular-among-cybercriminals/"). I'm sure that this is old hat for many people, but it's new for me!

I don't understand exactly how it works, but I think that it works like this:

[LIST=1]
[*]The black hacker hacks into the account that holds your domain's DNS records.
[*]The hacker adds subdomains. E.g., if your domain is [example.com]("https://example.com"), the hacker adds the subdomain [evil.example.com]("https://evil.example.com").
[*]The hacker amends the DNS records just for the subdomain [evil.example.com]("https://evil.example.com") to point to the hacker's own server.
[/LIST]
Have I understood this correctly?

If so, the only way for me to proactively detect if my website has been hacked with domain shadowing would be to check for subdomains that I didn't create, and to check that the main domain and all subdomains point to my host, not a nefarious one.

Please correct me if I've gone wrong.

(I realise that to reduce the chance of hacking in the first place, I need a strong password, 2FA, and good digital hygiene.)

---

### Post by SeijiSensei on 2022-09-23
All my DNS records are on servers I control. Where are yours?

---

### Post by Paddy Landau on 2022-09-24
> **SeijiSensei said:**
> All my DNS records are on servers I control. Where are yours?
My domain names are registered with GoDaddy, and my hosting is with SiteGround.

---

