---
title: "2 internet exit : configurate the routes"
date: 2009-02-17
forum: Server Platforms
---

### Post by k_gillot on 2009-02-17
Hi everybody,

I have a Ubuntu Server 6.04 with 3 interfaces : normal exit to Internet thought broadband (**net**) which is the default exit, a second exit on a satellite connexion (**sat**) and a local network (**loc**).
The **net **has a dynamic IP, while the **sat **has a static IP.

I am facing the following problem:
when I send a https request (with specified port) to the **sat**, the server sends the response on the **net** interface; so from the outside, I can never get the answer.

Do you know how I can configure my server saying that 'the response must be sent on the same interface the request was made'

I guess that would be a Shorewall issue, but dont know what direction to go...

Thank you for the help!

---

