---
title: "Firewall Issue"
date: 2009-02-18
forum: Security
---

### Post by Big Luke on 2009-02-18
Hi, I have just switched from windows to Ubuntu about 2 months ago and I really enjoy it however, there seems to be a firewall blocking certain programs that I have used in the past.  I remember on Windows I could disable the firewall and configure it to allow certain programs, I was wondering if there is any way to disable or at the very least configure the firewall.  I have looked and I cannot find a firewall on Ubuntu...could it possibly be my router?  Any light you could shed on the situation would be much appreciated.

---

### Post by whoop on 2009-02-18
This is most likely your router as ubuntu will not keep any ports closed for you. If you want control you computers ports you might want to consider installing gufw

---

### Post by Big Luke on 2009-02-18
Yes, I think you are right, I had just put in a new router recently so I had not configured it yet but I just did a few minutes ago and I found the firewall settings and disabled them and now everything works fine.

---

### Post by bodhi.zazen on 2009-02-18
Bu default the firewall in Ubuntu allows all traffic. This is fine with desktop installations as there are no open ports.

If you wish to learn how to use the firewall, see these links :

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

---

### Post by Big Luke on 2009-02-18
Thank you bodhi.zazen.  I really appreciate the help, I am always willing to learn more about things I know nothing about lol.  I don't know how you found those pages, I had absolutely no luck.  But, I suppose that is why you are the Ubuntu Guru and I am not. :)

---

### Post by bodhi.zazen on 2009-02-18
You are most welcome.

The page on UFW is hard to find on the wiki, I had to book mark it.

The second link I wrote, because I found it hard to find pages on iptables.

Sorry it is so ugly, I am working on adding some style and updating / organizing the content.

---

### Post by hyper_ch on 2009-02-20
if you configure your router properly there's not much reason to change the default firewall behaviour on linux.

---

### Post by Big Luke on 2009-02-20
O yes I forgot to post it on here, I fixed the problem.  I did not have my router properly configured but after about an hour of mindless clicking :P I got it to work.  Thanks for the help everyone.

---

