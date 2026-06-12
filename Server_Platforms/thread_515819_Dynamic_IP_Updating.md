---
title: "Dynamic IP Updating"
date: 2007-08-02
forum: Server Platforms
---

### Post by infinitezero on 2007-08-02
I am planning to go through a service instead of going the Static route. Does anyone have any experience with different Dynamic IP Updating services, any recommendations?

Has anyone dealt with this company?

[http://www.no-ip.com/](http://www.no-ip.com/)

Thanks,
iz

---

### Post by Viruk on 2007-08-02
I use [http://www.dyndns.com/](http://www.dyndns.com/)

See the home users section: [http://www.dyndns.com/about/home_solutions.html](http://www.dyndns.com/about/home_solutions.html)

Specifically [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

They have a huge number of [domains available to choose from]("http://www.dyndns.com/services/dns/dyndns/domains.html")

The service i use is free and I've never had a problem with it, the best part for me is that it works seamlessly with my smoothwall so as soon as the smoothwall detects an IP change it automatically updates the dyndns service for me. 

The only time it needs any attention at all is if my IP address goes for more than a month without changing. The dyndns service detects that it has not had an update and mails you a reminder to manually do this - in smoothwall it is simply a matter of hitting an update button.

---

### Post by Warren Watts on 2007-08-02
I host several small personal pages on apache using No-IP, and I have never had any problems.  I had a few minor kiccups getting the IP update client properly installed so that it executed at boot, but that was mostly due to my newbieness...

Other than that, their services have worked just fine for my relatively simple needs.

---

### Post by infinitezero on 2007-08-02
Thanks for the info, I appreciate it.


iz



side note: Ubuntu has the best community support, you folks ROCK.

---

