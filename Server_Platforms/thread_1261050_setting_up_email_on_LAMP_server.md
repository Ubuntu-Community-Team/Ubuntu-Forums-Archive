---
title: "setting up email on LAMP server"
date: 2009-09-08
forum: Server Platforms
---

### Post by mjfroggy on 2009-09-08
Hello,

I setup a Ubuntu Lamp server and also just installed sendmail.

My issue is I still am not able to get the php mail() function to work. Do I need to also install exim as my mta?? Or is Sendmail fine. If I just need sendmail then what might not be allowing the php mail() function to work??

thanks for any help

---

### Post by Bachstelze on 2009-09-08
> **mjfroggy said:**
> If I just need sendmail then what might not be allowing the php mail() function to work??

It could be lots of thing: dynamic IP, ISP or firewall blocking port 25, incorrectly configured host/domain name, etc.

Please tell us more about your environment.

---

### Post by mjfroggy on 2009-09-09
The server has a dedicated IP but it is on a corporate network that functions behind a corporate firewall/router

I am told port 25 is not blocked on the network/corporate router
So I am thinking it might be some sort of misconfigured or missing software on the server itself. I do have apache working fine on the server with database interaction.  I dont think its a domain misconfig issue cause when I putty into the server remotely I do so via the domain not the servers IP  and am able to login to ssh via putty using the servers domain and roots username and password.

Not sure if this helps with understanding how the server is setup and the enviornment it is in.

---

