---
title: "squid and URL blacklist"
date: 2010-04-26
forum: Server Platforms
---

### Post by X1R1 on 2010-04-26
hi all,

I have squid installed and downloaded a sites blacklists to load into squid, thing is, I want to block domains not single URLs so every address is in format "sex.com" but squid needs it to be ".sex.com" (notice the dot at the beggining).

I would be able to input the dot manually if the website list was short, but, there are more than 3 million sites of porn according to URL blacklist (lol they are a lot), so I cant just go an add a dot to every line.

If I dont add the dot at the beggining the acl file is to easy to bypass, you will just need to type [www.sex.com](www.sex.com) instead of sex.com and thats it.

How can I add the dot at the beggining of every line?

cheers

---

