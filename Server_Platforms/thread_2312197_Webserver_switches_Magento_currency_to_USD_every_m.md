---
title: "Webserver switches Magento currency to USD every month"
date: 2016-02-02
forum: Server Platforms
---

### Post by joss2 on 2016-02-02
Hi everyone

I'm having a strange issue on my dedicated ubuntu server 12.04. 
It has a Magento webshop on it.
Every first of second day of the month, the currency suddenly changes from EUR to USD. In my Magento controlpanel everything is normal. 
When cleaning the cache of my Magento directory, the problem isn't solved. Only after rebooting the server, The issue is resolved and all prices are back to normal again. 

Do any of you have an idea why this acts so strange? Why do I have to reboot the server for it to resolve? 

I'm using virtualhosts. 


Sinerely

Joss

---

### Post by albertgroply on 2016-02-05
I've had some issues similar to this on my online retail store which is based on the Existore theme from [http://www.templatemonster.com/magento-themes.php](http://www.templatemonster.com/magento-themes.php). I wanted to change the currency from USD to Euro, but when I tried to appliy the changes from the admin panel, some error was displayed. If I am not mistaken, you can use CTRL key to select multiple values. I am using the Auto Currency Switcher extension since then, it automatically changes the default currency to match the visitor's location.

---

