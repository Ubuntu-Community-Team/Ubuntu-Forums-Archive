---
title: "Enable UFW via SSH - stupid mistake"
date: 2014-12-06
forum: Security
---

### Post by Penguin360 on 2014-12-06
I made a stupid mistake. I logged in my Ubuntu via SSH, then I realize that I haven't enabled my firewall yet, without much thinking, I enabled UFW...I know you probably already see it is a big mistake. Once the firewall is enabled, it blocks incoming ports by default I guess, so port 22 is blocked now and I can't access my box via SSH.

I was thinking it would be nice that UFW could recognize, when being enabled via SSH, there is a active SSH connection, so it will automatically open port 22. Now I have to go to my box physically to open port 22.

---

### Post by Lars Noodén on 2014-12-06
That would be a useful safeguard.  Have you filed a bug in launchpad for it?  

With UFW you have to enable SSH incoming before activating it.  If you work with straight iptables instead you can also use [iptables-apply](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-apply.8.html).  And of course both iptables and UFW will work with an [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) job set a few minutes in the future to undo any changes so if you are still able to log in after the changes you can cancel the job.

---

### Post by HermanAB on 2014-12-06
Howdy,
When I have to work on a remote firewall, I first set up a cron (at) job for 1 hour into the future, that will flush all iptables rules.  Then, when the inevitable lock out occurs, I wait for the cron job to let me in again.  Otherwise, if all went well, I stop the cron job when things are done and working right.

---

### Post by kevdog on 2014-12-08
Nice trick Herman.  Never thought of doing that.  I guess I know what I can do if I need an hour break -- /jk

Another, although much more complicated solution would be to set up a port knocker -- however I'd assume you should probably own the box and not just work on it.  I do however find it hand to initiate the port knocking sequence from my phone which temporarily opens a port in the firewall so I can then ssh in.  Once in, then its possible to alter iptables directly.

---

### Post by Penguin360 on 2014-12-08
Thank you Lars and Herman for the helpful information. I just went to my box and manually enabled SSH port, so now I can remotely access the computer via SSH again. 

I tried to use AT job to turn on a port, but it didn't work, I am new to this, so can anyone help me?

1. Create a sh command
```
touch ufwtools.sh
echo "sudo ufw allow 80">>ufwtools.sh
```

2. Make it executable
```
chmod +x ufwtools.sh
```

3. Set up the AT job
```
at now + 5 minutes -f ~/tools/ufwtools.sh
```

However, I check UFW status after 5 minutes, nothing has changed. Is it because sudo needs password?

---

### Post by Lars Noodén on 2014-12-08
> **Penguin360 said:**
> 3. Set up the AT job
```
sudo at now + 5 minutes -f ~/tools/ufwtools.sh
```

'at' has to run as root for this task because, as you've noticed, otherwise the script will get stuck asking for a password.  But port 80 is HTTP.  If you want to get in via SSH, then port 22 is what needs to get opened.

---

### Post by Penguin360 on 2014-12-08
> **Lars Noodén said:**
> 'at' has to run as root for this task because, as you've noticed, otherwise the script will get stuck asking for a password.  But port 80 is HTTP.  If you want to get in via SSH, then port 22 is what needs to get opened.

That makes sense to use "sudo at". I have already manually opened port 22, and I am using port 80 for testing purpose. I want to make sure I do everything correctly and don't want to lock myself again. ;)

Even if I run 'at' as root, I still need to have "sudo" in my "ufw" command, right?

Thanks!

---

### Post by Lars Noodén on 2014-12-08
If you run at as root, via sudo, then anything it runs will subsequently run as root.  So sudo is no longer needed inside the script itself.  But the script should open port 22 so you can get in via SSH if that's how you're logged into the machine, just in case you reset the UFW rules or something.

---

