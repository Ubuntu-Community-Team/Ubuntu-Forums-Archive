---
title: "Apache2 using too much ram"
date: 2012-04-30
forum: Server Platforms
---

### Post by darknoobie on 2012-04-30
I just installed a webserver that is hosting ajaxplorer. No one is connected to the server and its already consuming 1.9GB of ram. I attached the screenshot of the memory usage. What could it be?
Thank you

---

### Post by d4m1r on 2012-04-30
1) Look like apache is only using 174MB of RAM.

2) Please take a screenshot of what you get running the top command instead.

3) Optimize your apache anyway to use less than 174MB of RAM by editing apache2.conf inside /etc/apache2. Try these settings:


StartServers       1
MinSpareServers    1
MaxSpareServers    5
MaxClients        50
    MaxRequestsPerChild   100

---

