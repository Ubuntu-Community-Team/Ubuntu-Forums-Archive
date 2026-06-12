---
title: "Amavis hyphen bug"
date: 2009-01-26
forum: Server Platforms
---

### Post by NaOH on 2009-01-26
Greetings Everyone,

Perhaps some of you have come into this issue, or even better have worked around it.  It began with setting up my first mailserver on my 8.04 server.  Postfix install/configuration went well as did Postgrey, however I came to grinding halt on the amavisd-new configuration.  While it installs fine, its initial launch fails every time with this:

"The value of variable $myhostname is "y-server", but should have been a fully qualified domain name; perhaps uname(3) did not provide such. You must explicitly assign a FQDN of this host to variable $myhostname in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's network name!"

Having followed those short instructions with no success I have identified the problem over the past two weeks of scouring the web as:

[https://answers.launchpad.net/ubuntu/+source/amavisd-new/+question/28169](https://answers.launchpad.net/ubuntu/+source/amavisd-new/+question/28169)

Amavis does not like hyphenation! My samba server is currently resolving to 127.0.1.1 where users are connecting at smb://y-server...  If at all possible I would like to leave this alone.  Also, the hostname -f inquiry pulls "y-server.local" (as opposed to "y-server" reported by amavis) if that helps, and I'll gladly confess my understanding of the finer points of the ubuntu hosts file is scant at best.

So now I am left wondering if there is a viable workaround out there for my situation.  I would really like to leave my initial hostname alone as other services are riding on it.  Any thoughts?

Thanks!

---

### Post by spiderbatdad on 2009-01-26
It appears in this situation you would edit /etc/host so that:
127.0.0.1 localhost y-server
This aliases y-server to localhost. Will that meet your needs?
Or perhaps you want to alias y-server to the local ip of that machine.
You dont appear to be accessing the network externally.  Otherwise the TLD should
be named to the local ip
like: 192.xxx.xx.xxx example.y-server.com

---

### Post by NaOH on 2009-01-27
Thanks for the reply.  When I put my hosts in the first configuration you mentioned I do get what I think is a desirable result from reading the fqdn, hostname -f; however, amavis reports the same message, and as you have mentioned it is the alias we are probably wanting to come back simply as localhost.  As far as having y-server alias to the machine IP, that would also work for my situation as everything is kept local, except my scant knowledge is now standing in the way.  When you say

192.xxx.xxx.xxx     example.y-server.com

Would such an entry be achieving y-server ---> local IP?
When I do add this with the appropriate info I still report back the same thing hostname -a (and -f).

I'll keep at this, but if I'm missing something let me know

Thanks again.

---

### Post by NaOH on 2009-03-15
Well not much of a solution to the proposition of a workaround, but if anyone else encounters this use logic:

Get the latest amavisd-new from source, follow the INSTALL, and designate your fqdn in the .conf.  No hang-ups, just worked.  Thanks again to those of you who assisted!

---

