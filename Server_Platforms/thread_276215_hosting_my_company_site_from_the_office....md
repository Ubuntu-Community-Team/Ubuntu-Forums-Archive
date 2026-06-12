---
title: "hosting my company site from the office..."
date: 2006-10-12
forum: Server Platforms
---

### Post by huggy77 on 2006-10-12
i have been running UBUNTU for months without a problem... i have a local server - only visible within the office...  I only run coldfusion, apache and mysql...

I can get a highspeed line with a dedicated ip...
I have a very robust machine (hp proliant), battery backup and a tape drive...  


If i connect this server to a firewalled static IP - what would be different from an admin standpoint?

i know this is a broad question but it has to be harder to host a box connected to the outside, correct?

---

### Post by Endwin on 2006-10-12
If I understand you correctly it shouldn't. Assuming you have a registered domain name and point the public DNS servers to your static IP, and finally poke port 80 (default for web) through the firewall to the internal web server it should work.

Or do you mean security or something diffrent?

---

### Post by huggy77 on 2006-10-12
no that was it... My ubuntu experience bas been so positive that it is making me nervous...

---

### Post by huggy77 on 2006-10-15
can you recommend a good server brand - i am not married to hp. i dont want to purchase the wrong server.

---

### Post by Endwin on 2006-10-16
Depends on the load of your server. I run a personal web server on a 300 MGHTZ AMD K6 with 192 MB RAM and a 20 Gig HD. My load is less then a percent most of the time. If you expect a lot of work to be done by your machine (Database, PHP, etc) and a lot of people accessing you may want to spend money on a real server. 

I know system76 has some nice servers with ubuntu preinstalled. It may be worth checking out.

[http://system76.com/index.php/cPath/43]("http://system76.com/index.php/cPath/43")

---

### Post by huggy77 on 2006-10-23
what about a firewall - i have a cisco soho 91 now... Is that serviceable for a non ecommerce site?  What else should i be looking for?

-thanks

---

