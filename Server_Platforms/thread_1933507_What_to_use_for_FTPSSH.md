---
title: "What to use for FTP/SSH"
date: 2012-02-29
forum: Server Platforms
---

### Post by techblvd on 2012-02-29
I just installed a LAMP server (Ubuntu 11.10).  I installed OpenSSH as part of the install.  I am going to use this server primarily to serve pages for 3 sites.  I have setup Webmin and am considering installing Virtualmin.

Are there any suggestions as to security and ease of use to setup FTP access that I can use to publish updates to my sites from IWeb (or anything else)?

I am a total Ubuntu/Linux newbie.  While I said I installed Open SSH and Webmin, I have not done anything with them.  Though, I can see what Webmin does as far as creating virtualhosts.  I am not sure what functionality Virtualmin will give me.

Thanks

---

### Post by lykwydchykyn on 2012-02-29
OpenSSh enables SFTP and SCP by default, that's really the best thing to use.  I know nothing about IWeb, so I can't say if it's compatible.

If you need a vanilla FTP, it won't be as secure due to using plaintext passwords, but there are several good servers available.  I mostly stick to proftpd myself, but it really only makes a difference when you get into complicated setups (virtual users, complex chroot setups, etc).

---

### Post by techblvd on 2012-02-29
Thank you...I will look at configuring that

---

### Post by bubylou on 2012-03-08
SFTP using openssh would be the best option in my opinion. If your going to use ssh or sftp outside your local network you should definitely secure it. I recommend setting up key based authentiaction and customizing ssh to make it as secure as you want.

---

