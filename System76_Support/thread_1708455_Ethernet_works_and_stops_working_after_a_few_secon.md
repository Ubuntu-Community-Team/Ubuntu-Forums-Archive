---
title: "Ethernet works and stops working after a few seconds"
date: 2011-03-16
forum: System76 Support
---

### Post by PDXJon on 2011-03-16
I just got a brand new gazelle:

[http://www.system76.com/product_info.php?cPath=28&products_id=113](http://www.system76.com/product_info.php?cPath=28&products_id=113)

I turned it on and plugged in an ethernet cable.  All worked fine for about 10 seconds when browsing a website.  Then the internet no longer works.  I restart the computer and it freezes and never shuts down, it just shows the desktop background.

Upon restart I can use the internet for a few seconds and then it stops working. 

I tried using a different computer on the same port (works). 
I tried restarting the router, same issues.
I tried a different port, same issues.

Any ideas?

---

### Post by PDXJon on 2011-03-16
Ok narrowed it down.

When the computer goes into hibernate / suspend and is woken up again, the ethernet no longer works.

Any ideas?

---

### Post by isantop on 2011-03-17
I think you contacted us via email. We can continue here or there, it's your choice.

---

### Post by thomasaaron on 2011-04-15
Please try this fix...

Turn you computer off. Hook up Ethernet and AC power. Boot Up. You should have Ethernet now.

1. Click the link below and save. The package should go to your Downloads folder...

[http://mirror.pnl.gov/ubuntu//pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb)

2. Now open a terminal and run these commands, pressing Enter after each one...

cd Downloads

sudo dpkg -i pm-utils_1.3.0-1ubuntu1_all.deb 
# NOTE: after typing the "pm" you can just hit tab and auto-complete the rest of the filename

You'll be prompted for your password. You won't see it typing, but the terminal is accepting it. Hit enter after typing it.

Once the terminal returns you to a command prompt, you're finished. Reboot your computer.

At this point, the Ethernet should be working fine, and the freezing should be solved.

---

### Post by jij on 2012-12-17
not working..TT
 
> **thomasaaron said:**
> Please try this fix...
 
Turn you computer off. Hook up Ethernet and AC power. Boot Up. You should have Ethernet now.
 
1. Click the link below and save. The package should go to your Downloads folder...
 
[http://mirror.pnl.gov/ubuntu//pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb)
 
2. Now open a terminal and run these commands, pressing Enter after each one...
 
cd Downloads
 
sudo dpkg -i pm-utils_1.3.0-1ubuntu1_all.deb 
# NOTE: after typing the "pm" you can just hit tab and auto-complete the rest of the filename
 
You'll be prompted for your password. You won't see it typing, but the terminal is accepting it. Hit enter after typing it.
 
Once the terminal returns you to a command prompt, you're finished. Reboot your computer.
 
At this point, the Ethernet should be working fine, and the freezing should be solved.

---

### Post by overdrank on 2012-12-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

