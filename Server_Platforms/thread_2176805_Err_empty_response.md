---
title: "Err_empty_response"
date: 2013-09-26
forum: Server Platforms
---

### Post by sonic2 on 2013-09-26
Hello.

I am running Ubuntu server on VPS with Apache v2.2.17, PHP v5.3.5 and MySQL v5.1.63 and i can not trace the source of the ERR_EMPTY_RESPONSE when view some sites running on it.
This error appears only from some IP, for example, if i browse from my work, home computer or on my smartphone all works great, no errors, but at one of my friends home and thru my neighbors Wi-Fi on my work i get that error when i try to enter administration panel on some of my sites on that VPS. I figured, that this is not device dependent (i try from many computer, notebooks, smartphones, tablets), the problem obviously on server side.
In the apache or mysql logs i found no errors then i get ERR_EMPTY_RESPONSE in browser. In access logs there is record with HTTP 200 code when i login to administrator panel and catch error, at the same time on other computer i see that user (that catch that error) as logged in.
When i see apache server-status page at the moment of catching error in column "Request" is "..reading..", in "VHost" is "?" and in "Client" is "?".
I have no restriction by IP or something else neither on site nor server.

How can i trace the source of that problem? Please, help.

---

