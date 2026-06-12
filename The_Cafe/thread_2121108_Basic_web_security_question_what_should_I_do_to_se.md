---
title: "Basic web security question: what should I do to secure personal web server?"
date: 2013-02-28
forum: The Cafe
---

### Post by quickk on 2013-02-28
Hi everyone, 

    I just installed owncloud (an open-source cloud solution that you can host on your own desktop).   Now, when I browse to myservername.com/owncloud I can access the web interface from anywhere in the world.   Cool!   

I am a bit worried though of having my personal desktop computer so exposed though.   It seems that if I place any file in /var/www I can access this file through my browser.   Is this ok?   Is there anything I should know, or do to make sure that my personal web server is secure?

Thank you for any advice!

---

### Post by oldos2er on 2013-03-01
Not an Ubuntu support question, moved to Cafe.

---

### Post by ubudog on 2013-03-01
Hi quickk, 

If there are any applications or services running that can be accessed from the internet I'd recommend locking them down.

You can see which ports are listening by running the following command:
```
sudo netstat -anltp | grep "LISTEN"
```

> It seems that if I place any file in /var/www I can access this file through my browser.
This is normal.

Regards,
ubudog

---

### Post by darkcrimson on 2013-03-02
What about an [.htaccess]("http://en.wikipedia.org/wiki/Htaccess") file, perhaps?

---

### Post by Paqman on 2013-03-03
First things first, make sure you know what services you've got running (eg: SSH, FTP). Cut off access to everything else. Make sure you know how to secure what you do have running. Make sure you've got strong passwords and use something like Fail2ban or Denyhosts, if only to stop the script kiddies from filling your logs up with nonsense.

---

### Post by itrogers on 2013-03-03
Why not just sign up for a free tier of of Amazon EC2?

[http://aws.amazon.com/ec2/](http://aws.amazon.com/ec2/)

If you can install it on your local machine you can run it here. Sign up for the micro instance (its free for 1 year running constantly) and choose ubuntu server 12.04. You can assign an IP to it and everything. Would definitely recommend as you won't be putting all of your data and personal stuff at risk.

---

### Post by ugm6hr on 2013-03-03
> **itrogers said:**
> Why not just sign up for a free tier of of Amazon EC2?

[http://aws.amazon.com/ec2/](http://aws.amazon.com/ec2/)

If you can install it on your local machine you can run it here. Sign up for the micro instance (its free for 1 year running constantly) and choose ubuntu server 12.04. You can assign an IP to it and everything. Would definitely recommend as you won't be putting all of your data and personal stuff at risk.

This is a bit misleading... There is no genuine "free" tier - only a 12-month free period. And credit card details are still required (therefore, only available to over 18s).
So this is only really an option if you are prepared to pay for (or abandon) the service after 12 months.

---

### Post by itrogers on 2013-03-03
> **ugm6hr said:**
> This is a bit misleading... There is no genuine "free" tier - only a 12-month free period. And credit card details are still required (therefore, only available to over 18s).
So this is only really an option if you are prepared to pay for (or abandon) the service after 12 months.

It is what it is. I'm sure one can make the case that after the year the 2 cents per hour is worth the added security. Just offering a solution.

---

### Post by darkcrimson on 2013-03-03
He just wants to know how to make his home cloud server more secure. -Not the caveats to Amazon Cloud services. Honestly, why send someone to Amazon when they're interested in learning more about home server security. That's a bit counter-intuitive don't you think? Especially since the solution he's using is already set up and configured.

---

### Post by quickk on 2013-03-03
Thank you everyone for your replies.   I believe that I have a strong password, and the only services that I have running are ssh at http access.   I've had ssh running for years without any problems, but I don't really know anything about adding http access.   So far so good, and I'll read up on .htaccess.   I had encountered some suggestions about .htaccess during some google searches but the information was conflicting.   As far as I could figure out, it seems that using .htaccess files was deprecated, and that you had to configure apache2 instead (warning: I don't really know what I'm talking about here!).    The Fail2ban or Denyhost options look interesting... thanks!

Apart from the future cost, the Amazon services are not what I am looking for because I want to have full control/ownership of my data.   Also, I'm pretty sure that I can't get hundreds of gigabyted served on Amazon for free.

---

### Post by cariboo on 2013-03-03
You may find the links [here]("http://ubuntuforums.org/showthread.php?t=1046738"), useful, even though they mostly are for the Ubuntu server.

---

