---
title: "[SOLVED] Howo make apache return a fake server name and version"
date: 2007-12-02
forum: Server Platforms
---

### Post by quandary on 2007-12-02
Hi

After installing LAMP, how can I make Apache (preferably & Co.) make return a fake server name (eg. IIS) and version for http requests? I don't find anything on google.

---

### Post by MJN on 2007-12-02
If it's for reasons of security I really wouldn't bother. Such obfuscation will only deter the weakest of crackers given the prevalence of service fingerprinting (to determine service versions) or simple brute force scanning (to pinpoint the vulnerable purely by chance).

At the most simple level you can control the level of detail using the ServerSIgnature and ServerTokens directives.

Changing (to a non-standard form) the information defined by SERVER_SIGNATURE may be a little more involved - I'm not sure if you can do this with the setenv directive from mod_env as you would with other environment variables.

Besides which, do you *really *want people thinking you're running IIS? ;)

Mathew

---

### Post by quandary on 2007-12-02
> **MJN said:**
> 
Besides which, do you *really *want people thinking you're running IIS?;;)


Thanks. I know making a fake server name/version doesn't stop nmap and others.
But I heard it is quite efficient in turning down about 90% of script kiddies ;-)

Why not IIS? 
After all, that's not uncommon, so it's not suspicious. 
I of course have to make them think i use another OS as well, which i also intend to do. 

Sure, it doesn't stop 100% of all attackers by far, but after all, those who are not clever enough will have miserable success in trying to attack Linux with Windows/IIS exploits etc... ;-)

---

### Post by MJN on 2007-12-02
The vast majority of 'attacks' are not executed manually by individuals, but rather they are the result of automated bots running on compromised machines.

Hence, your server ID is of little interest to them - if you've got a web server running on port 80 you'll be picked up by one of their sweeping probes and they'll automatically attempt to exploit the known exploits.

They care not whether you're running Apache or IIS as they'll try either way, and just hope you're running the latter. If they don't succeed they'll move on.

Check your logs - you are bound to see numerous IIS exploit attempts recorded and these won't be the result of individuals sitting there specifically targetting you - to do so is not worth their time as they're looking for the one-out-of-many machines that are in a vulnerable position.

Mathew

---

