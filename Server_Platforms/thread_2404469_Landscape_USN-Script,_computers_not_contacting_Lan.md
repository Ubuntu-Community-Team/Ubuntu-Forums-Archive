---
title: "Landscape USN-Script, computers not contacting Landscape-Server and deleting Users"
date: 2018-10-24
forum: Server Platforms
---

### Post by hofmannj-fisp on 2018-10-24
Hello there,

we recently bought the LandscapeOnPremise Edition and set it up so we can manage all our Ubuntu-Servers with it. Nearly everything works fine, except for the 3 topics mentioned in the Title.

1) We get an Error-Message when clicking the "Packages"-Tab saying that the USN update cron script is not running. (attached usn.png). What exactly is this error? I tried to find out and saw that in /opt/canonical/landscape/scripts/ there is a script called "landscape-env.sh", that is used by most of the other scripts. I also saw, that it excludes Proxy-Servers implemented in /etc/environment. I tried to hardcode the companies proxy-settings into this landscape-env and the scripts are running now, but the error is still there.

2) We currently only have 2 clients connected to the landscape-server for testing-purposes. Both of the servers are listed as "...haven't contacted Landscape within the last 5 minutes". What could that be? I tried to check how this "contact-mechanism" works but i am not quite sure yet. Somehow there is a python-script running, opening a port internally on 8070 and Apache redirecting $server/ping to this script. But how does it work and why do my 2 Test-servers are listed as "havent contacted"?

3) One of the users forgot his password and we deleted him from the Administrators accounts and just invited him again. In the online-documentation it says, that you can just invite people again, but when he tries to register, it just says "E-Mail-Adress already exists". Is there a way?

Thanks in advance for the help, and i you need any more information, please just ask :)

Regards

Jonas

---

### Post by hofmannj-fisp on 2018-10-30
*push*

---

