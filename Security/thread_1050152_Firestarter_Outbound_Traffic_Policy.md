---
title: "Firestarter Outbound Traffic Policy"
date: 2009-01-25
forum: Security
---

### Post by Bigmo1942 on 2009-01-25
What services do I really need on my desk top computer. My outbound policy includes BitTorrent, HTTP, HTTPS, POP3 and SMTP. Do I need to allow anything else outbound? I was not sure other services.

---

### Post by Dr Small on 2009-01-25
Why are you specifing an OUTBOUND policy? If you are behind a router, you don't need to configure your firewall anyhow, but INBOUND is generally the policy you'd be wanting to modify.

---

### Post by Bigmo1942 on 2009-01-25
I do not have a router as I'm on dial up. I have inbound policy set so that my computer is in stealth mode. I am concerned about limiting outbound in case I pick up some form of malware that could make outbound communications.

Most firewalls are two way and have Inbound and Outbound rules.

---

### Post by Dr Small on 2009-01-25
> **Bigmo1942 said:**
> I do not have a router as I'm on dial up. I have inbound policy set so that my computer is in stealth mode. I am concerned about limiting outbound in case I pick up some form of malware that could make outbound communications.

Most firewalls are two way and have Inbound and Outbound rules.
Ok, well setting INBOUND policies is fine, since you're not behind a router or firewall. But setting OUTBOUND policies isn't necessary since you fairly well immune to viruses, trojans and malware. I wouldn't worry about it.

---

### Post by The Cog on 2009-01-26
You definitely need DNS outgoing so you can do name lookups. DNS uses both UDP and TCP port 53. You might also want to allow ICMP ping requests outgoing.

I gather that BitTorrent works much better if you also allow incoming connections to it.

---

