---
title: "How to change HTTP port to say 8080"
date: 2011-02-08
forum: Server Platforms
---

### Post by jerrywh3 on 2011-02-08
Ok I will be setting up a web server at my house. It will be a simple page for my family to keep in touch and maybe some other stuff. Here is the problem: I believe my ISP blocks port 80. So when setting up the firewall and it list the normal port 80 am I able to edit to say 8080? I have a ddns already setup for my router and I am waiting for an email back from DynDNS.com on setting up a new domain to forward to my already setup hostname. I just need to get everything redirected to another port beside 80. I thank any ones answer ahead of time.

---

### Post by wormyblackburny on 2011-02-08
There are 3 ways to do this, although arguments for the benefits of each can be tricky:

1) (easiest) Have your router forward all incoming requests to port XXXX to port 80 and set up Apache like normal 

2) Set Apache daemon to listen on the alternate port via httpd.conf

3) Use IPtables to forward all requests on port xxxx to port 80

---

### Post by jerrywh3 on 2011-02-08
> **wormyblackburny said:**
> There are 3 ways to do this, although arguments for the benefits of each can be tricky:

1) (easiest) Have your router forward all incoming requests to port XXXX to port 80 and set up Apache like normal 


Ok gottcha. So have the Wan listen to say 8080 and have the Lan redirect 8080 to 80. That is actually really easy do in my router. I will use the Virtual Server option to do that.

---

### Post by wormyblackburny on 2011-02-09
Make sure you mark your thread as resolved if everything works ok ;)

---

### Post by linuxsyst on 2011-02-13
YOU SHOULDN'T ASK HOW TO in a question it looks like a HOWTO

---

