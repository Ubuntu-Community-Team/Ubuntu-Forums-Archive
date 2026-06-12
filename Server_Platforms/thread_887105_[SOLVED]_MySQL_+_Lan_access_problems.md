---
title: "[SOLVED] MySQL + Lan access problems"
date: 2008-08-11
forum: Server Platforms
---

### Post by dave.mack on 2008-08-11
Problem Solved with some google fu.

Hi Guys, 

I am a Ubuntu wait linux 'newbie'... I have had some problems configuring mysql so that our LAN clients can connect to it. So I was getting a 10061 error I think that was it. I then commented out bind-address line in my.cnf, still now luck I though the firewall might be blocking it be I can connect via telnet, when I do I get the following response: "Host '****.*******.com' is not allowed to connect to this MySQL server" at which point the connection is terminated. I also did a netstat -tap which returned this: tcp 0 0 *:mysql *:* LISTEN.. 

Any help would be great I am TD in an animation studio who really needs a sys admin...

Cheers, 
Dave

---

