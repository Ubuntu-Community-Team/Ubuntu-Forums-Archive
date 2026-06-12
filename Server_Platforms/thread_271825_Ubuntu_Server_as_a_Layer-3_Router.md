---
title: "Ubuntu Server as a Layer-3 Router"
date: 2006-10-05
forum: Server Platforms
---

### Post by TheKyle on 2006-10-05
I have what I believe to be a unique routing configuration requirement and after doing some research on my own I thought I would pose this question to the more knowledgeable people of the Ubuntu Forums.

How can I use Ubuntu Server to act as a Layer-3 router?  I want to segment computers from a corporate network by having the Ubuntu Server computer act as a router.  Within my segmented network, I would like to have my own network services running, such as Active Directory or LDAP and DHCP.  To complicate things, I would also like these network services to communicate with the corporate network services, as well as having Windows file sharing be accessible both ways through the router.  I think I'm correct in saying that I would need something capable of layer 3 routing, so that the DHCP BOOTP packets (I think that's correct) requests would be blocked while normal IP traffic would be allowed.

I do have some background with networking protocol concepts and client networking, but I lack the Linux utility know-how to pull this off without further help.  So, although I don't need someone to hold my hand and instruct me, I would like to know what the best approach would be regarding what Linux utilities to use and what to avoid.  Right now I'm thinking that IP and DNS forwarding/masquerading with port forwarding might be my best bet.

I am a noob to these forums, but my initial impressions are that the community is very active and helpful.  Hopefully that will be the case here.  :D

---

