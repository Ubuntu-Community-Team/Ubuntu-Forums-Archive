---
title: "Make my LAMP server available for acess outside of my network"
date: 2010-05-24
forum: Server Platforms
---

### Post by Kdar on 2010-05-24
How can I make my LAMP server visible to other people outside of my network?

I am building a site and want to make it possible for another person to view it as well.

What do I need to do to my LAMP server to do this?

---

### Post by lisati on 2010-05-24
You need to make sure that your router forwards port 80 to your server. Details vary from router to router - there might be someone with a similar router to yours (feel free to ask if you get stuck)

Also be aware that some ISPs block port 80.

---

### Post by wojox on 2010-05-24
Yes like lisati indicated some are different. On mine you need to activate port 443 as well as 80.

---

### Post by cph05a on 2010-05-24
If you intend to user your server for a while, you might consider getting a dynamic dns. Unless you're paying for a static ip address from your ISP, there is no guarentee that your ip address will remain the same. I've used no-ip.com and it works great.

---

### Post by Kdar on 2010-05-24
I think I have dynamic ip, I have cable internet provider.

---

