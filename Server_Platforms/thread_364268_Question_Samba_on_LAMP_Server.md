---
title: "Question: Samba on LAMP Server"
date: 2007-02-18
forum: Server Platforms
---

### Post by lenwood on 2007-02-18
Hi All,
   I've spent most of the night setting up an old desktop to put in my closet as a LAMP server for use in web development. I'm through the installation, and am trying to get Samba set up correctly. I'm following [this thread]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html"), and I can't access Samba for the life of me. When I get to step 18, I enter

```
http://hostname:901/shares
```

the new server responds with a login prompt, but nothing I enter will give me access. I've tried my username, root, blank, nothing gets me in. I'm positive that I'm using the correct password.

If it makes a difference, I'm using a static IP, SSH access works great, and I was able to install PHPMyAdmin without a hitch. Everything else is working but hostname:901 access.

Any tips on this? I'm lost.

Thanks,
Len

---

### Post by Mike'sHardLinux on 2007-02-18
Are you sure you didn't skip any steps? Possibly step 13?

---

### Post by lenwood on 2007-02-18
Thanks for a speedy answer, and for reading the link that I provided. I just checked my command history, and I did follow step 13 to create a password. Just be sure, I just did it once more, and again the authorization prompt just keeps appearing.

I don't know if this makes a difference or not, but the authorization prompt says that I'm entering the password for SWAT. I thought this step was for logging into Samba. But, either way, my usernames and passwords for each are the same, so this shouldn't make a difference.

Thanks,
Len

---

### Post by Mike'sHardLinux on 2007-02-18
ahhh. I believe you are right. SWAT password, not Samba.

One other possibility I noticed is in the SWAT configuration has a line:
user = root

According to step 4, you gave a password to root. It looks like you should use the user root and the password you assigned in step 4. I assume you already tried this?

Maybe re-do step 4, just to make sure you typed the root password right.

---

### Post by lenwood on 2007-02-18
Last night I was tired, so I figured that was at least part of the problem. This morning, I woke up, had some coffee, then tried these steps again. Still no go. Here's a list of what I've tried:

username + password
username + blank
root + password
root + blank

I tried resetting each password with passwd and smbpasswd, then repeated the steps. Nothing gets me in.

Does anyone have any suggestions? I'm tempted to wipe the drive and start over.

Thanks,
Len

---

### Post by lenwood on 2007-02-18
Okay, I finally figured it out. After my last post, I wiped the drive and reinstalled from scratch. I was super careful to follow the instructions, the only deviation that I made was that I listed 'username' instead of root in the /etc/xinetd.d/swat file, since the line right above it recommends using a more limited user. When I changed it back to root, it worked properly.

This system is going to be a personal file server in my bedroom closet. It's connected to the web through a D-Link router. I'm not a millionaire so I'm not worried about it getting hacked. That said, am I opening up a security risk by having root here?

Thanks,
Len

---

### Post by polc1410 on 2007-02-18
Not being a millionaire means nothing these days.

Robots like to find holes and then install backdoor software to send spam / host phishing sites etc (been there ;-( )

However IN THEORY if port 901 is blocked on your firewall at the router you should be OK.  Somewhere (not sure where) it would make sense to tell SWAT only to accept connections from local IP addresses too (i.e. hosts allow 192.168.1. type thing), you can possibly also do that on your server firewall too.

---

