---
title: "Lost networking in Ubuntu 11.10 server"
date: 2011-10-14
forum: Server Platforms
---

### Post by rv65 on 2011-10-14
I have a Linode and I have seemed to have lost networking. 

```
/etc/network/if-up.d/upstart: 38: cannot create /run/network/ifup.eth0: Directory nonexistent       
run-parts: /etc/network/if-up.d/upstart exited with return code 2                                   
   ...done. 
```

This is the error I get when I restart the networking command.

---

### Post by matt_symes on 2011-10-14
Hi

> **rv65 said:**
> I have a Linode and I have seemed to have lost networking. 

```
/etc/network/if-up.d/upstart: 38: cannot create /run/network/ifup.eth0: Directory nonexistent       
run-parts: /etc/network/if-up.d/upstart exited with return code 2                                   
   ...done. 
```This is the error I get when I restart the networking command.

Do you have a /run directory at all ?

Kind regards

---

### Post by rv65 on 2011-10-14
I do get the error, but I now have static networking, so it works. I used the static networking article on Linode, and that fixed it. Linode hasn't offered 11.10 yet, but they probably will test it, and they used my support ticket as feedback.

---

### Post by lurker_mike on 2011-10-14
I have experienced this problem, but eth0 did come up, however my eth0:0 alias did not.

Manually creating /run/network and re-running */etc/init.d/networking restart* did not bring up eth0:0.

---

### Post by TheBleak on 2011-10-14
I currently had an issue close to this one
I run VMware 8 and currently 11.04 with a static IP.
 
At the last 4 min of the install time left... the install box starts flashing and I noticed some other white box was behind it asking me something about a passphase. since both these boxes were flashing at a rapid rate I was unable to even look at what it said... 
 
I have tried this upgrade 4 times last night and each time I have to force shut down after the install screen goes all white and freezes.
 
when I restart it says it can't boot with networking and will boot in without networking mode.. .but never does... it just freezes.
 
I can't even copy text of the error or screen shot it =(

---

### Post by MarcusPereira on 2011-10-14
The network fail issue happened to me after the reboot on a Natty to Oneiric upgrade today.

It seems the move from /var/run to /run did not work during the upgrade process.

I fixed with this:

cd /var
mv run _run
ln -s /run .

Then reboot.

---

### Post by Vegan on 2011-10-14
My VM seems to be working OK, wonder if some patch affected your particular HAL

---

### Post by iosox on 2011-10-15
@MarcusPereira Thx.

---

### Post by mmas on 2011-11-15
> **MarcusPereira said:**
> The network fail issue happened to me after the reboot on a Natty to Oneiric upgrade today.

It seems the move from /var/run to /run did not work during the upgrade process.

I fixed with this:

cd /var
mv run _run
ln -s /run .

Then reboot.

Thanks MarcusPereira, that helped me.

---

### Post by LukeQuake on 2011-11-17
> **lurker_mike said:**
> I have experienced this problem, but eth0 did come up, however my eth0:0 alias did not.

Manually creating /run/network and re-running */etc/init.d/networking restart* did not bring up eth0:0.

Hi Lurker - did you manage to solve this? It appears to be a bug with alias in Ubuntu 11.10 (see here: [http://ubuntuforums.org/showthread.php?p=11466145#post11466145](http://ubuntuforums.org/showthread.php?p=11466145#post11466145)). I'm also trying to fix the exact same issue.

---

### Post by me.bionic on 2011-11-21
> **MarcusPereira said:**
> The network fail issue happened to me after the reboot on a Natty to Oneiric upgrade today.

It seems the move from /var/run to /run did not work during the upgrade process.

I fixed with this:

cd /var
mv run _run
ln -s /run .

Then reboot.

Thanks. Worked for me, too.

---

### Post by dukeplc on 2011-11-27
> **me.bionic said:**
> Thanks. Worked for me, too.
 
 
+1
 
Thanks!

---

### Post by TheFuzz4 on 2012-01-13
> **me.bionic said:**
> thanks. Worked for me, too.

+1

---

### Post by Revo- on 2012-01-24
Thanks, this worked :)

---

### Post by progone on 2012-04-17
> **MarcusPereira said:**
> The network fail issue happened to me after the reboot on a Natty to Oneiric upgrade today.

It seems the move from /var/run to /run did not work during the upgrade process.

I fixed with this:

cd /var
mv run _run
ln -s /run .

Then reboot.

:mad: no fix for me :sad:

---

