---
title: "Error accessing Horizon (OpenStack Folsom)"
date: 2013-03-18
forum: Server Platforms
---

### Post by Tarek Heggi on 2013-03-18
Dear Sir,

We are using Ubuntu 12.10 server 64 bits & OpenStack Folsom.
We have installed OpenStack using "Open Stack-Folsom-Install-Guide", our setup includes 2 machines "controller & compute". we have reached to the dashboard component and we have the the following errors during accessing after authentication:
First
1. Error: Unable to retrieve Usage information
2. Error: Unable to retrieve quotate information
Second 
also when try to access the instance and gives the following error:
Error: Unable to retrieve instance list
Third, when we run any nova commands such as:
nove list
nova image-list

it gives us error http 404

Regards,
Tarek Heggi

---

### Post by kenan2 on 2013-10-02
Hi,

i had the same problem, after good review there was missing line in the nova.conf
if you could submit the nova.conf to get more info.

Regards,

---

