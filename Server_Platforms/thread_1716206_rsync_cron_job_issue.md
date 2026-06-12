---
title: "rsync cron job issue"
date: 2011-03-28
forum: Server Platforms
---

### Post by fan0o on 2011-03-28
Hi,

Following command is working fine but it ask for passphare as shown below. it was supposed to work without password and key should be share. as mentioned in this [link]("http://www.howtoforge.com/mirroring_with_rsync_p2")

```
sudo rsync -avz --delete --exclude=**/stats --exclude=**/error --exclude=**/files/pictures -e "ssh -i /root/rsync/mirror-rsync-key" user@server:/var/www/ /var/www/
```


```
Enter passphrase for key '/root/rsync/mirror-rsync-key':
```

i added the cronjob as  following but it is not working........

```
*/5 * * * * /usr/bin/rsync -azq --delete --exclude=**/stats --exclude=**/error --exclude=**/files/pictures -e "ssh -i /root/rsync/mirror-rsync-key" user@server:/var/www/ /var/www/
```

Please advice how could i make this work without any human interaction. i followed the [tutorial]("http://www.howtoforge.com/mirroring_with_rsync_p2") as it is.

Thanks
Regards

---

### Post by galorin on 2011-03-28
Can you ssh in without a password, as this is going over the same transport?  If not, then you've done something wrong with your key pairs, like not specifying a blank passphrase.  

More than once, I've done things the wrong way around, so the remote server can log in to me without a passphrase.

---

### Post by MrEgg on 2011-03-28
You could try and use sshfs to mount your remote drive and then execute your cron job locally (ie from your local drive to your locally mounted ssh drive).

---

### Post by BkkBonanza on 2011-03-28
You're using a keypair created with passphrase. 
Create a new one and give it a blank (enter when prompted) passphrase.

Or alternately use ssh-agent to handle the passphrase during use but it has to be primed once after startup/login.

---

### Post by K_Light2003 on 2011-03-29
I have just sorted this out on my 10.10 server, after a little messing about I got it all working..  I have written it up on my blog, so I don't forget what I have done, in case I have to do it again..

[Here]("http://linuxserver2011.wordpress.com/2011/03/26/ssh-login-without-password-ubuntu-10-10/") is the SSH password post and [this post]("http://linuxserver2011.wordpress.com/2011/03/26/keeping-calibre-library-in-sync-with-rsync-ssh-cron/") is how I got rsync working. 

Please note that it's just my notes on a 10.10 server and not a complete step by step guide, but maybe it might help you.

I'm not convinced the rsync post is the best way, but it's working for me.

---

