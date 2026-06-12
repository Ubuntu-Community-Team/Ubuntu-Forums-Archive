---
title: "Postfix - I want people to able to send email to me."
date: 2008-03-24
forum: Server Platforms
---

### Post by haryoh on 2008-03-24
I'm kinda newbie, but I love what I've done so far. I just configured my postfix so I can emails out from my home network server. However, I can't send anything into my server from an outside email. I have the feelings I will have to let my server become browse-able by the public before this can be done which is my outer most goal using Bind9 that come with my ubuntu distribution that I use.

Is there any advise? Thanks

---

### Post by Metro_Dan on 2008-03-24
> **haryoh said:**
> I'm kinda newbie, but I love what I've done so far. I just configured my postfix so I can emails out from my home network server. However, I can't send anything into my server from an outside email. I have the feelings I will have to let my server become browse-able by the public before this can be done which is my outer most goal using Bind9 that come with my ubuntu distribution that I use.

Is there any advise? Thanks I am a newbie myself, but I followed [this]("http://howtoforge.com/perfect_server_ubuntu7.10_p5") tutorial for Postfix and I have it running perfectly now. You will need to have a FQDN with the proper MX settings.

---

### Post by kool_kat_os on 2008-03-24
this is the perfect tutorial: [http://help.ubuntu.com/community/MailServer]("http://help.ubuntu.com/community/MailServer")

---

### Post by haryoh on 2008-03-25
> **Metro_Dan said:**
> I am a newbie myself, but I followed [this]("http://howtoforge.com/perfect_server_ubuntu7.10_p5") tutorial for Postfix and I have it running perfectly now. You will need to have a FQDN with the proper MX settings.
the tutorial in howtoforge.com was the one I followed but i think I screwed up where it say 
> mynetworks = 127.0.0.0/8

I left mine like that, what do you think i should put there? I'm 192.168.1.1 for gateway...

Windows will still be alive but won't used by us.

---

### Post by Metro_Dan on 2008-03-25
> **haryoh said:**
> the tutorial in howtoforge.com was the one I followed but i think I screwed up where it say 


I left mine like that, what do you think i should put there? I'm 192.168.1.1 for gateway...

Windows will still be alive but won't used by us.
Yea I added my local networks, 192.168.10.0/24  and 127.0.0.1

---

