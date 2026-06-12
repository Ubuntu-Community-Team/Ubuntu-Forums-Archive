---
title: "Multiple servers, hosting users files from the webserver"
date: 2009-08-14
forum: Server Platforms
---

### Post by seaders on 2009-08-14
So, we've 2+ servers, but our main two are our webserver and our users server. Webserver is a powerful little rig, but without masses of space. Users server is the opposite, masses of space, but not too powerful (it's grand, but nothing crazy).

Now, we're in charge of our own domain, so we can write our own domain rules and all that jazz and we're hosting with Apache. What our ultimate goal would be to have is all our users to have their own subdomain, ie username.domain.com, but there's a few irritations to do that.

We don't really want anyone logging into the webserver, bar admins, who have to login through the users server, so we want to keep the amount of registered users on the webserver down to the bare minimum. Because of that, we've a different pool of users between the servers and solutions like mounting users homes wouldn't, I don't think, be the best solution.

But, I don't know. I'm not an Apache, nor server expert and would love some advise on the manner. All help and suggestions are greatly appreciated, thanks.

---

