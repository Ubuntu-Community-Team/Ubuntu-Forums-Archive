---
title: "PPTP + FreeRadius + LDAP on UBUNTU 12.04 LTS"
date: 2013-04-12
forum: Server Platforms
---

### Post by konelh on 2013-04-12
Hello everyone, I'm a newbie, can anyone help me about pptp + freeRadius + LDAP on Ubuntu 12.04 LTS
I'm working on my VPN server which is connected by pptp authentication.
However, I want to configure my server to use LDAP accounts when it asks for VPN connection
I researched on the internet they did mention pptp, LDAP and FreeRadius
If anyone helps me with the idea, it would be awesome ;)

---

### Post by konelh on 2013-04-17
Can anyone help me with this, please :(

---

### Post by konelh on 2013-04-17
Hello everyone, I'm a newbie, can anyone help me about pptp + freeRadius + LDAP on Ubuntu 12.04 LTS
I'm working on my VPN server which is connected by pptp authentication.
However, I want to configure my server to use LDAP accounts when it asks for VPN connection
I researched on the internet they did mention pptp, LDAP and FreeRadius
If anyone helps me with the idea, it would be awesome :wink:

---

### Post by coffeecat on 2013-04-17
@konelh, I've merged the two posts you made to an old thread into your new thread. It's better to start your own threads, but please do not post the same question in different parts of the forum. This dilutes community effort.

---

### Post by konelh on 2013-04-18
thank you :)

---

### Post by konelh on 2013-04-19
can anyone help me with this :(? Many thanks in advance!!!!

---

### Post by konelh on 2013-05-06
Please someone help me with this bunch of thing :(

---

### Post by MAFoElffen on 2013-05-06
I'll give this a try... (Seeing you orphaned.)

Let me get this straight in my head. 
-You have something running some version of 12.04LTS. Is that a Server or Desktop Edition? 
-You want to install some form of VPN Server on it. For instance OpenVPN Server or ?
-- You want to install Active Directory services via LDAP on your network, possibly on this server... possibly using FreeRadius or OpenLDAP Server.

PTPP is old technology. I was using that 25 years ago. You sure that is what you want?  OpenVPN is a lot newer tech. FreeRadius Is a kind of LDAP Server...

So, this will effect the server install:
- What kinds of clients are you going to have connecting to it for what kind of purpose? (What is your requirements and goal?)
- Do you have a test client and what is it?

Do you have packages installed already and need help configuring them to work together? Configured and need help debugging to work out the problems? Or do you need help picking out packages that will work together? I see a few different posts, that say a few different things... but there is no clear picture of what "kind" of help you are asking for.

EDITED-- I should probably ask about your skill level, so I know what the level of the target audience is...

---

### Post by konelh on 2013-05-07
> **MAFoElffen said:**
> I'll give this a try... (Seeing you orphaned.)

Let me get this straight in my head. 
-You have something running some version of 12.04LTS. Is that a Server or Desktop Edition? 
-You want to install some form of VPN Server on it. For instance OpenVPN Server or ?
-- You want to install Active Directory services via LDAP on your network, possibly on this server... possibly using FreeRadius or OpenLDAP Server.

PTPP is old technology. I was using that 25 years ago. You sure that is what you want?  OpenVPN is a lot newer tech. FreeRadius Is a kind of LDAP Server...

So, this will effect the server install:
- What kinds of clients are you going to have connecting to it for what kind of purpose? (What is your requirements and goal?)
- Do you have a test client and what is it?

Do you have packages installed already and need help configuring them to work together? Configured and need help debugging to work out the problems? Or do you need help picking out packages that will work together? I see a few different posts, that say a few different things... but there is no clear picture of what "kind" of help you are asking for.

EDITED-- I should probably ask about your skill level, so I know what the level of the target audience is...

Thank you MAFoElffen
-I'm watching over my remote servers which are located in Singapore, it's running on Linux all, and the method of connecting to VPN is PPTP from Windows desktop
[IMG]http://s11.postimg.org/3zydmoabn/VPN_connection.jpg[/IMG]
-Once VPN is connected, I can manage to control the servers through ssh connection by Cygwin, with[COLOR=#b22222]** LDAP accounts**[/COLOR], and password from a token.
[IMG]http://s23.postimg.org/gish5lemj/SSH_with_token.jpg[/IMG]
- Account from VPN connection and account for ssh connection are different, so I want to configure my servers to ask **[COLOR=#b22222]LDAP account for VPN connection[/COLOR]**
- I know PPTP is old, but our group has found out that [COLOR=#b22222]**OpenVPN and LDAP**[/COLOR] have conflicts somehow so we decided to work with PPTP and LDAP
- And I've been searching for this combination online because we have no experience about these stuff. I found many websites did mention PPTP and FreeRadius.
- I'm an Administrator and I'm supporting my clients (as my R&D Project said so), my servers are well configured before, but it needs upgrading for sure.
- I'm expected to integrate LDAP with PPTP (first it was OpenVPN) for more secure, and also with token password requirement, sounds tricky for me...
- If you don't mind showing me the ideas, it would be great, or you can integrate LDAP with OpenVPN on Linux, that will be better!!!
Anyway, you replied me and gave me some hopes, I've been waiting for so long...
If you want to know something more, If I could tell, I will, please reply and ask more to help me, you're the man!

---

### Post by MAFoElffen on 2013-05-07
Just a note- I suggested that this be Moved to Server Platforms, so it could get some proper exposure in the right place.

---

### Post by CharlesA on 2013-05-07
[Just an FYI about PPTP]("http://www.computerworld.com/s/article/9229757/Tools_released_at_Defcon_can_crack_widely_used_PPTP_encryption_in_under_a_day").

I haven't really heard much about issues with OpenVPN and LDAP and found this page on their site:
[http://openvpn.net/index.php/access-server/docs/admin-guides/190-how-to-authenticate-users-with-active-directory.html](http://openvpn.net/index.php/access-server/docs/admin-guides/190-how-to-authenticate-users-with-active-directory.html)

---

### Post by konelh on 2013-05-07
> **CharlesA said:**
> [Just an FYI about PPTP]("http://www.computerworld.com/s/article/9229757/Tools_released_at_Defcon_can_crack_widely_used_PPTP_encryption_in_under_a_day").

I haven't really heard much about issues with OpenVPN and LDAP and found this page on their site:
[http://openvpn.net/index.php/access-server/docs/admin-guides/190-how-to-authenticate-users-with-active-directory.html](http://openvpn.net/index.php/access-server/docs/admin-guides/190-how-to-authenticate-users-with-active-directory.html)

but this is not what I really want...

---

### Post by MAFoElffen on 2013-05-08
Let me get back to you tonight. I had to move my sister-in-law yesterday. Today I have to make some signs for a bar, then have to make get something done on one of my programming projects... before I can clear my head enough to think on  something like this.

---

### Post by konelh on 2013-05-08
> **MAFoElffen said:**
> Let me get back to you tonight. I had to move my sister-in-law yesterday. Today I have to make some signs for a bar, then have to make get something done on one of my programming projects... before I can clear my head enough to think on  something like this.

Thank you!!! really appreciate your working attitude!!!

---

### Post by konelh on 2013-05-14
Hello everyone, I found this link and I decided to quit pptp, maybe this will help me configure OpenVPN authentication against LDAP
[http://www.howtoforge.com/setting-up-an-openvpn-server-with-authentication-against-openldap-on-ubuntu-10.04-lts](http://www.howtoforge.com/setting-up-an-openvpn-server-with-authentication-against-openldap-on-ubuntu-10.04-lts)
Anyone has experience about this, please tell me :D

---

