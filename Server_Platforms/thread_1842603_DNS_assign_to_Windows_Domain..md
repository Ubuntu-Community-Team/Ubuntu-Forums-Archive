---
title: "DNS assign to Windows Domain."
date: 2011-09-11
forum: Server Platforms
---

### Post by louis vitton on 2011-09-11
Hey guys,

I am a student studying IT networking and for an assignment i have to get a linux based apache web server with mysql up and running which i have done. This server has to join a windows domain.

Lets call the domain "example.edu.au"

[LIST]
[*] I am using ubuntu 11.04 server
[/LIST]
I am having issues with assigning the DNS server as the windows domain i am unsure how to do this?????

once i have worked out the dns issues i wish to join the domain controller which happens to be on the same server as the DNS.

Ubuntu and the dns server can ping but i cant not resolve names.

here is how i intend to join ubuntu to the windows domain also.
1. sudo apt-get install likewise-open
2. sudo domainjoin-cli join yourdomain.com yourADusername
3. sudo update-rc.d likewise-open defaults
4. sudo /etc/init.d/likewise-open start

Step one will prompt your for some info about your AD environment. After executing number two above, you’ll be prompted for your AD password for the user provided. Once this is done, you login by entering YOURDOMAIN\youruser at the login prompt.

Cheers Louis

---

### Post by SeijiSensei on 2011-09-12
We generally don't help with homework here, but I'll give you a hint.  Read the [man page for resolv.conf]("http://linux.die.net/man/5/resolv.conf").

---

### Post by louis vitton on 2011-09-12
> **SeijiSensei said:**
> We generally don't help with homework here, but I'll give you a hint.  Read the [man page for resolv.conf]("http://linux.die.net/man/5/resolv.conf").

No problem i can understand that completely. I normally use Open Suse's linux so this is all new to me as the Open Suse GUI lets me do it all so thanks for the pointer.

---

