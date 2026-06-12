---
title: "SSH Brute-Force"
date: 2009-11-30
forum: Security
---

### Post by Groover20 on 2009-11-30
I just got an email from my ISP saying I had a virus.  I asked for more info, as I found it odd since I only have Linux boxes.  They mentionned that the attacks were SSH Brute-Force, which would make sense.

My questions are:
Can I find out if any files were touched or copied?
What can I do to stop it and prevent it from happening again?

I'm thinking of changing my passwords on my laptop, server and router, but would that be enough?

---

### Post by sobol_rz on 2009-11-30
Check by tcpdump is this true ... :) 
examples: [http://www.ihtb.org/security/tcpdump-explained.txt](http://www.ihtb.org/security/tcpdump-explained.txt)

---

### Post by OpSecShellshock on 2009-11-30
Couple questions regarding the email from the ISP:

Did they ask you to follow any links and log in to anything?

Did the email have an attachment, perhaps a virus scanner, that they suggested that you download?

Did they tell you that it was an SSH brute force attack before or after you told them you were using Linux?

Do you have your computer set up for login/administration from remote, and if so, do you use SSH?

It might be a scam. Copy and paste the subject line into a google search, and then try it with some direct quotes from the text of the email.

---

### Post by Groover20 on 2009-11-30
The email address they use is fairly unknown, so I'm thinking it is fairly genuine.  I did not follow any links or download attachments, I simply replied to them, asking for more info.  I stated in that email I was running Linux.  They did reply stating it was a SSH Brute-Force and that my computer might have been infected with a Rootkit, or someone had guessed my passwords.

---

### Post by Groover20 on 2009-11-30
Sobol_rz, I'm not sure what you mean by that link...Can you explain?  I might be a bit slower tonight, it was the Grey Cup yesterday!!! ;)

---

### Post by HermanAB on 2009-11-30
If your machine has a weak password then it can easily get compromised and once compromised the hackers usually installs a Spambot.  

See this: [http://www.aeronetworks.ca/ssh-kiddies.html](http://www.aeronetworks.ca/ssh-kiddies.html)

---

### Post by hictio on 2009-12-01
Do you have Rootkit Hunter installed on the server that the ISP is claiming to give them trouble?

---

### Post by Groover20 on 2009-12-01
I did not have RkHunter installed.  However, I corrected the situation this morning, and ran it, as well as CHKROOTKIT.

RKHunter says that /usr/sbin/unhide is a warning.  Then at Checking if SSH root access is allowed, it states Warning, and that there might be suspicious files in /Dev.

I've changed the password on the server.  I'm now thinking of installing Fail2Ban, and removing root access through SSH.  My understanding is that I will still be able to SUDO while connected via SSH, right?

Is there anything else I should be doing to prevent it? Maybe using another port?

---

### Post by cdenley on 2009-12-01
If you set a root password (it is disabled for a reason!) and installed an ssh server, then you probably had your root account compromised due to a weak password, and your computer is now being used to launch the same attack on other computers. You can verify this by checking /var/log/auth.log. However, once you suspect your root account has been compromised, there is no definitive way to determine what damage has been done or if your system is safe.

You can use fail2ban or an alternate port to minimize the authentication attempts, but what is most important is to use strong passwords or keys for authentication, and don't allow password authentication for root.
```

sudo usermod -p ! root

```

---

### Post by bodhi.zazen on 2009-12-01
> **Groover20 said:**
> I did not have RkHunter installed.  However, I corrected the situation this morning, and ran it, as well as CHKROOTKIT.

RKHunter says that /usr/sbin/unhide is a warning.  Then at Checking if SSH root access is allowed, it states Warning, and that there might be suspicious files in /Dev.

I've changed the password on the server.  I'm now thinking of installing Fail2Ban, and removing root access through SSH.  My understanding is that I will still be able to SUDO while connected via SSH, right?

Is there anything else I should be doing to prevent it? Maybe using another port?

If your server has been compromised via a root login over ssh I advise you re-install your OS and restore your data from a previous known good backup.

If you are running a ssh server I advise you use ssh keys and disallow logins via passwords.

See :

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

Your other option is to attempt to perform forensices (see if you can determine what and how you were compromised), but you have to ask yourself if you have the expertise to do so.

From what you posted my guess is you were running a ssh server , allowed root logins, and had a weak password.

---

### Post by HermanAB on 2009-12-01
In my experience, SSH hackers usually set up a spambot such as 'redone' on the compromised machines.  So use tcpdump to look at the traffic on port 25/TCP.  If there is nothing there, then you probably got the problem fixed.  

It really is a good idea to re-install the machine eventually and do change the default port that SSH runs on - that simple fix will throw off most/all hack attempts, but remember to change the firewall to allow the non-standard port and test it properly before you disable the default port 22.

---

