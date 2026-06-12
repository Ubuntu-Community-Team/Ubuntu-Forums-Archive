---
title: "besides LTS, why choose 6.06 over 7.04?"
date: 2007-07-08
forum: Server Platforms
---

### Post by g[r]eek on 2007-07-08
hi guys

busy downloading 7.04 server iso purely because 6.06 didn't support some software we needed. 

now besides the long term service (up untill 2011), is there any other reason why we should stick to using 6.06?

if not, then i guess there's no risk in our company upgrading to 7.04 since we don't really use support anyway.

please advise. thanks.

---

### Post by madmetal on 2007-07-09
> **'g[r]eek said:**
> hi guys

busy downloading 7.04 server iso purely because 6.06 didn't support some software we needed. 

now besides the long term service (up untill 2011), is there any other reason why we should stick to using 6.06?

if not, then i guess there's no risk in our company upgrading to 7.04 since we don't really use support anyway.

please advise. thanks.

since you want to use latest version of programs i suggest you installing 7.04 server..
although its better to make a clean install of 7.04 rather than upgrading from 6.06.1
feisty is pretty stable....
look for tutorials about how to create a good ubuntu server..

ps. happy to see greek(?) companies using ubuntu at their servers ;)

---

### Post by g[r]eek on 2007-07-09
(please see next post)

---

### Post by g[r]eek on 2007-07-09
thanks for reply

regarding feisty server - the install phase stalls. first it stalls for about 5 minutes or so when the install is started ("creating temporary buffer" on black screen with blinking cursor), and then later it stalls permanently when scanning ide - something about a trm290 driver. so we basically just put feisty on hold for now, and decided to stick to dapper (which installs and works perfectly) - albeit we still have to figure out a way to get postgresql-8.2 to work (dapper only supports up to 8.1 via backports, and we need 8.2).

regarding greeks using ubuntu servers - hehe it's a greek company in so far as the owner (myself) is 100% greek and our company colours are blue and white ;-)

but we are based in cape town, south africa, where i should add, the founder of ubuntu comes from.

ego eime kalamatianos. milas ellinika? pou menis stin ellada?

cheers

---

### Post by Wim Sturkenboom on 2007-07-10
> **'g[r]eek said:**
> hi guys
busy downloading 7.04 server iso purely because 6.06 didn't support some software we needed. 
....
if not, then i guess there's no risk in our company upgrading to 7.04 since we don't really use support anyway.
I think your reasons (as posted above) are valid enough to use the newer version.

LTS implies updates including bug fixes and vulnerabilities. If you don't encounter problems, you don't need bugfixes. If you're not connected to the internet and you can trust your employees, there is no need for fixing of vulnerabilities.

We're still running RH6.2 boxes in our environment as we don't have the time to check if the dedicated software will work on newer versioons.

---

