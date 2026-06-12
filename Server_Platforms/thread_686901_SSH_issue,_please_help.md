---
title: "SSH issue, please help"
date: 2008-02-03
forum: Server Platforms
---

### Post by shankscomp on 2008-02-03
OK, I have looked through most of the threads regarding SSH and remote connections, but don't seem to find the answer I'm looking for...  Maybe I've just been sitting here in front of the PC too long on Super Bowl Sunday!!!

Anyhow, I have a Ubuntu 7.10 Server.  OpenSSH is installed.  I can connect from my Win-XP Pro laptop using PUTTY just fine.  On my desktop computer, I have Win-XP Pro also. I am currently NOT able to connect via Putty, or even going through the web shell through webmin.  When I went to connect using Putty, I some how screwed up the fingerprint key.  Is there a way I can reset things on the server so I can connect from my desktop machine???

Please help.  I'm trying to get this webserver up and going soon.

Thanks
Tim

---

### Post by dougfractal on 2008-02-03
can you get to the ~/.ssh/known-hosts
and if you are using ssh-keygen ~/.ssh/authorized_keys 

if you can either delete these and start again (ssh login in as if never done before)  or edit them removing the offending line)   

This happens when using a dhcpd router that give diffent machine the same ip at different times. Static your IP.

---

