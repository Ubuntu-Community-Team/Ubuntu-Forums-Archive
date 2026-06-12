---
title: "How to see list of blacklisted IPs in Apache?"
date: 2010-08-19
forum: Server Platforms
---

### Post by ray otti on 2010-08-19
Hi all,

I'm using Apache server's dos_evasive module to block DoS attacks. How do I see the list of blacklisted IPs? because I want to delete from time to time to monitor the IPs that are blacklisted, but do not know how to. Does anyone have an idea?

Thanks,
Ray

---

### Post by LightningCrash on 2010-08-19
The list is held in memory, you would have to grep for Blacklist in /var/log/messages (or wherever you set mod_evasive to log to)

---

### Post by ray otti on 2010-08-20
thanks for your response, my logs are in ; /var/log/apache2/mod_evasive but when i check they are empty, what is the command line for the grep pls? i used grep 'blacklist' in the log directory, didn't work...

---

### Post by LightningCrash on 2010-08-20
> **ray otti said:**
> thanks for your response, my logs are in ; /var/log/apache2/mod_evasive but when i check they are empty, what is the command line for the grep pls? i used grep 'blacklist' in the log directory, didn't work...

try grep -i 'blacklist' /var/log/apache2/mod_evasive

IIRC you can also configure mod_evasive to email you when it blacklists someone.

---

### Post by ray otti on 2010-08-20
tried grep -i 'blacklist' /var/log/apache2/mod_evasive but it just returned the prompt like it was just a save or create directory command. I entered the /var/log/apache2/mod_evasive directory and typred in grep -i 'blacklist just behaves as before; goes on like it's opening a gedit but never opens anything......

---

### Post by LightningCrash on 2010-08-20
that is a directory?

what's in the directory?

---

### Post by ray otti on 2010-08-20
u know when I do cd /var; 
cd log and so on.... then I get into the var/log/apache2/mod_evasive but normally like I said I use grep -i 'blacklist' it just behaves like it's a mkdir command.
I'm running bonesi on one client and attacking the server just to test the resilience of mod_evasive but I can't see the list of blacklisted IPs. I wanna know if mod_evasive is actually sending 403s and eventually blocking these IPs but I dnt know how to find out. I looked into the /var/log/messages and I found out it says; possible SYN flooding on port 80. Sending cookies.... I dnt understand why is it sending cookies if there's a possible SYN flooding? but my main interest is the blacklisting. Really wanna find where the list is.

---

