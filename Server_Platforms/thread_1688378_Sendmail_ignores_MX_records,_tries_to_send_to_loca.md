---
title: "Sendmail ignores MX records, tries to send to local user, refuses to send to g-apps"
date: 2011-02-15
forum: Server Platforms
---

### Post by skelooth on 2011-02-15
I've been banging my head against my desk for a week trying to figure this out. I'm not even sure where to begin. This seems to be a moderately common problem as posted on message boards, but there are no solutions ever given in any of my searches.

The gist goes like this

sendmail -t
to:anyaddress@underthe.sun
.
.

works fine.

But if I try to send it to my own domain/google apps account, it gets chucked into /var/mail/root with a message that the user is unknown. 

There have been people posting with this problem since 2008, surely there must be a simple fix? 

I've tried masquerading as a different domain name, removing my domain name from my hosts file, and trying the 'don't probe local interfaces' directive. Nothing so far works. 

Any help would be so appreciated. My server administration 'powers' revolve around LAMP, and this sendmail issue is out of my normal territory.

edit: How does sendmail even know that patrickavella.com is a local domain if I removed it from /etc/hosts? I don't see my domain listed anywhere in the sendmail .cf files? I assume when I figure that out the problem will be solved. Thanks again for ANY help at ALL. It is very much appreciated!

---

### Post by skelooth on 2011-02-15
After a lot of searching I finally figured it out. I had to change my hostname to something else, if your hostname and your google apps domain are the same, sendmail tries to send locally.

---

