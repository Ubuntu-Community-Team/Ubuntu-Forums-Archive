---
title: "Problems logging in, ssh, console, sudo"
date: 2012-05-02
forum: Server Platforms
---

### Post by rradam on 2012-05-02
Hello, I have been having some problems logging in via ssh, the console, using sudo when I do manage to login. Logins (if successful) take about 10 minutes at the least, sudo always hangs ( i even let it sit for a couple days). This all seems to have started happening right around the time i installed squid. The only unfortunate part is I can't even get in to do anything about it. anyone have any experience like this or any solutions?
 
TIA

---

### Post by rradam on 2012-05-02
Also this is running on a dl380 vmware cluster running vsphere

---

### Post by CharlesA on 2012-05-02
Are you blocking any outbound connections?

That shouldn't affect sudo at all. Console and SSH connections might take a little longer to login, but not 10 minutes.

---

### Post by hawkmage on 2012-05-02
Make sure that your DNS has the correct forward and reverse look-up entries for the system you are using to ssh into the server from.  

sshd will by default try to validate that you IP and host name are valid bu doing DNS queries.  This can cause longing in via SSH to "hang" for a while as all of the defines DNS servers are tried.  If you can not fix the DNS you can add "UseDNS no" to your /etc/ssh/sshd_config and restart sshd.

As for sudo this also can be related to DNS is you have a the fqdn option in your sudoers file or if you are using any of the host name based rules and there is a DNS issue.

---

### Post by rradam on 2012-05-02
Darn, I would love to try these but I can even get logged into the box right now as it is.  
 
forgot to mention Im running hardy.

---

### Post by rradam on 2012-05-02
It even hangs on reboot normally or vsphere client, there is a squid error, apache error about FQDN using 127.0.0.1, then hangs.

---

### Post by CharlesA on 2012-05-02
What happens when you try to login to the box from the console?

---

### Post by rradam on 2012-05-02
username goes fine, put in password, then just hangs at the login screen waiting.  Every once in a while i get to login, but I can sudo anything to edit anything.

---

### Post by rradam on 2012-05-02
Ok, so quickly logging in at boot, I was able to login, and sudo pkill -9 -u avahi (I read this on another forum).  I am now able to sudo commands and ssh pretty quickly to the host.  I was also able to add my FQDN into the hosts file.  I am also going to remove squid now that I no longer use it just to be safe.

---

### Post by CharlesA on 2012-05-02
avahi is used for APIPA. If this is a server install, that shouldn't be running.

If that box isn't running any mission critical, you might be better off just doing a clean install of Lucid or Hardy and setting stuff back up.

---

### Post by rradam on 2012-05-02
Well its somewhat mission critical, and right now I have it seemingly stable so I think I'm going to leave it alone for now, and make sure all the cron jobs fire off as expected tomorrow and just not touch it. Thanks for the assistaince everyone.

---

