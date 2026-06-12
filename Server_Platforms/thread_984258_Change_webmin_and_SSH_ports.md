---
title: "Change webmin and SSH ports"
date: 2008-11-16
forum: Server Platforms
---

### Post by wattaman on 2008-11-16
First, I'm a noob, so please, if you can help, do it in a way I can understand what you're saying.
The problem I have is that I want to change the webmin's port (from 10000 to whatever else) and the SSH port (from 22...).
I've tried a couple of times and almost locked myself outside of the server.
Now, corect me (or complete this) if I'm wrong:
- I change the port in the firewall (for webmin) from 10000 to, let's say, 12345;
- Then I change the port the webmin's settings from 10000 to, again, 12345;
- Same with SSH; 

Is there something I'm missing?
Everytime I do this I can't connect after that. Luckly I've tried them one by one, so when the webmin didn't load I could fix the original ports from within SSH and the other way.
Please tell me how to change those settings. I'm kin of worried since more and more alerts is sending me the denyhosts script lately - I'd like to change those ports as a security improvement.
Thank you!

---

### Post by Philio on 2008-11-16
Have you changed the ports in the relavent config files as well as just changing the firewalls (and restarted the services afterwards)?

I don't use webmin so don't know what you have to do to change it's default port, however for SSH you can do the following:

1. Edit /etc/ssh/ssh_config and uncomment and change the port line
2. Restart ssh with /etc/init.d/ssh restart

I would open both ports on the firewall to make sure you don't get locked out of the server, once you can login ok on the new port you can remove port 22 from the firewall rules.

---

### Post by wattaman on 2008-11-16
Philio, thx for the reply. Didn't worked though.
So, step-by-step: created a similar rule for the new port in the firewall settings, applied the new settings, changed the port for SSH, again applied the new settings (after restarted the server, just in case) .. and when I conected (using putty) I got only the 'Connection reset by peer' error message.

---

### Post by Thirtysixway on 2008-11-16
Under webmin, go to Webmin > Webmin Configuration > Ports and Addresses

There you'll see where you can change the port that webmin listens on.

It's wise to change the port that ssh runs on, it will cut back on 90% of brute-forcers who do nothing but scan default ports.

---

### Post by Philio on 2008-11-16
> **wattaman said:**
> Philio, thx for the reply. Didn't worked though.
So, step-by-step: created a similar rule for the new port in the firewall settings, applied the new settings, changed the port for SSH, again applied the new settings (after restarted the server, just in case) .. and when I conected (using putty) I got only the 'Connection reset by peer' error message.

You were able to connect via port 22 still after the changes?

---

### Post by Philio on 2008-11-16
Sorry I gave you the wrong config file to change!

You need to modify /etc/ssh/sshd_config in exactly the same way as above, changing the Port line.

The file I mentioned before is the client configuration file!! Ooops :) (You might want to revert that back to port 22, although it probably doesn't matter unless you SSH from your server to other machines.)

---

### Post by Thirtysixway on 2008-11-16
Remember to reload ssh after you change the config.

---

### Post by hictio on 2008-11-16
If you haven't already, the Webmin port can be changed editing the configuration text file located in '/etc/webmin/miniserv.conf', you have to do that as root, using sudo.
The directive is the oen called 'port', the original is like this:
```

port=10000

```

Remember to restart the Webmin service after you do the changes.

---

