---
title: "LAMPP - Configuration Issues"
date: 2016-03-02
forum: Server Platforms
---

### Post by Daniel_Clarke on 2016-03-02
Hey,

So I have installed Ubuntu 14.04 LTS server, I have installed LAMPP and configured Apache for named based virtual hosts. Everything seems to work fine in my local environment when I edit my hosts file, however if I try setting up my DNS file on Godaddy to make the site live it doesn't work. I have created a NAT entry in our company firewall, what else could it be? 

Thanks in advance for any and all help provided.

-daniel

---

### Post by howefield on 2016-03-02
Thread moved to the "*Server Platforms*" forum for better support.

---

### Post by Daniel_Clarke on 2016-03-03
Bump...

Anyone?

---

### Post by Daniel_Clarke on 2016-03-03
Does 14.04 LTS come with an active FIREWALL? I did check the status of Uncomplicated Firewall using this:

sudo ufw status

It displayed the results:

inactive

However I still feel something is blocking this website from properly displaying outside of our local environment? Any help would be greatly appreciated.

Thanks

-Daniel

---

### Post by SeijiSensei on 2016-03-03
> **Daniel_Clarke said:**
> I have created a NAT entry in our company firewall, what else could it be?

This isn't a NAT situation.  You want to forward port 80 on the router back to port 80 on the server.

---

