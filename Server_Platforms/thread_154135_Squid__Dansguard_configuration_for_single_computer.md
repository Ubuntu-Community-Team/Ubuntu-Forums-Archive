---
title: "Squid / Dansguard configuration for single computer"
date: 2006-04-02
forum: Server Platforms
---

### Post by Cyclops_ on 2006-04-02
Hi All,

I just installed Squid and Dansguard on my home laptop.
I am trying to get them set up so that the proxy server (Squid) cannot be bypassed simply by removing the proxy setting in Firefox or Opera or users' browser of choice...  Basically I want to restrict access to the internet so that the only way to the internet is through the proxy.  That way I can have Dansguard work to protect the users of the laptop.

________________________________________________________________

Edited:  OK, I just found out that I can do this by turning Squid into a
transparent proxy... I guess they have some good FAQs out there for this...
So, no worries with that...

Now I just need to figure out this next part:
________________________________________________________________

Additionally... Is there a way to set it up so that certain files / folders / programs can only be accessed with a special password?  I have a user on the laptop who requires sudo and admin rights, etc, and he might use that power to bypass the proxy or turn off Dansguard, which is something I don't want.  I want to grant someone else permissions to set and maintain a password to the config files for Both applications and to restrict access to programs such as the Boot Up Manager, so that someone with Super User rights can do anything on the laptop except bypass the proxy / web filter.

Does anyone have any suggestions?

---

### Post by Abhi Kalyan on 2007-01-28
Hi,  
just finished config of the above. Could you please point me to the Howto's whihc make squid transparent?
thank you

---

