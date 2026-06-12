---
title: "making repository clone for offline updates"
date: 2006-10-20
forum: Repositories &amp; Backports
---

### Post by shlomi on 2006-10-20
Hello,

I am building a network for a company, and I would like to use  Ubuntu/Kubuntu as their operation systems. Our users will only be connected to our LAN and will not have an Internet connection on their desktops. For internet access they will have designated computers with internet connection. 

My question is if there is a way to make a clone of the repositories we need to our specific update server, so all clients will be able the be updated from that server (put our server in the sources.list)?

If there is another way to keep our offline users up to date with the repositories, please let me know.

Best Regards,
Shlomi

---

### Post by UbuWu on 2006-10-20
That can easily be done with apt-mirror or apt-proxy. With apt-mirror you can make a complete copy of the repositories. Apt-proxy only downloads packages when they are needed and then keeps them available.

---

### Post by shlomi on 2006-10-20
Thank you very much UbuWu!

---

