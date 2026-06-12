---
title: "Smtp relay - outbound email issues"
date: 2010-03-08
forum: Server Platforms
---

### Post by jeffshowalter7 on 2010-03-08
I installed the citadel suite on ubuntu server 9.10 Email obviously works fine internally. I tried to setup a smart host to send my mail through as my isp(Verizon) obviously blocks port 25. I tried to send out the Verizon smtp server on port 587. In the  Administration> Domain names and Internet mail configuration>Smarthosts
My smarthost entry on the citadel configureation page above was username:password@outgoing.verizon.net:587 but after sending an outgoing email, it comes back with a "invalid/host-not-in-DNS return address not allowed"

I have also tried using gmail and a hotmail account with the respective smtp address's in but they come back with "Must issue a STARTTLS command first"
I have researched both messages and come up with squat that has helped me. 

I know that my mail will have to go out through a smarthost of somekind. So is am I on the right track with choosing verizon/gmail/or something else as my smtp relay, or is there a free service out there that I can send email through(haven't found one if there is)

Anyone else ever setup Citadel and got around their isp blocking port 25?
I am also not sold on citadel, it was just the first/ nicest looking one that I found. 

thanks,

Jeff

---

### Post by cdenley on 2010-03-08
When building a mail server, I looked at Citadel briefly since it was highly recommended, but my experience with it was terrible. I would recommend zimbra over it any day. I used the open-source version briefly, and was much more satisfied with it. We ended up purchasing zimbra network edition, though.

---

### Post by jeffshowalter7 on 2010-03-09
I will have to check it out. I guess what I really have a question about, no matter what product I select, is that I should be able to send mail out of my providors smtp server using my credentials? or even through my gmail or hotmail account or something like that?

---

