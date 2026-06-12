---
title: "Precautions before going online?"
date: 2012-01-30
forum: Security
---

### Post by jpdeaton on 2012-01-30
I'm doing a clean alternate install and don't trust the network I am connecting to. Are there any security measures that can be taken before I connect to the internet?
Would it be better to connect directly to the router with an ethernet while configuring everything?

---

### Post by Dangertux on 2012-01-30
If you don't trust the network you're on there really aren't any security measures you can take. 

That being said , choosing a switched connection to the router does give you a little bit. Though that traffic can still be sniffed by anyone on that router (via arp poisoning)

You need to be using SSL/TLS for all sensitive online dealings. IE: Internet banking , email , social networking etc. You could use a VPN or ssh tunnel to further this if you have or can get access to one. 

Other than that standard rules apply. Noscript on our browser (as well as other similar addons) , decent firewall config, apparmor profiles enforced, well configured file permissions, strong passwords, etc. 

Hope this helps.

---

### Post by uRock on 2012-01-30
Enabling UFW will make you invisible to port scans, but your packets will still be sniffable. As mentioned above, HTTPS and other encrypted connections are the way to go when using an insecure network. If the router is yours, then yes, connect to it with hard wire and lock it down.
```
sudo ufw enable
```

---

### Post by jpdeaton on 2012-01-31
How can I delete the firefox disable file for apparmor? It's not letting me delete it.
Anyone know whats up with the 140TB? lol...

[IMG]http://www5.picturepush.com/photo/a/7456923/1024/Anonymous/Screenshot-at-2012-01-31-05%3A35%3A19.png[/IMG]
[IMG]http://picturepush.com/public/7456923[/IMG]

---

### Post by uRock on 2012-01-31
You have to open Nautilus as the root user. This is not recommended. You can set the profile to complain, if needed. 

To open Nautilus as root, copy and paste the folling in a terminal,```
gksudo nautilus
```then enter your password. Be careful as it is easy to destroy your install by altering the wrong directory.

---

### Post by jpdeaton on 2012-01-31
Is it normal for /usr/share to be a large file? How can I disable any shared files/folders?

thanks again

---

### Post by OpSecShellshock on 2012-01-31
> **jpdeaton said:**
> Is it normal for /usr/share to be a large file? How can I disable any shared files/folders?

thanks again

/usr/share shouldn't be messed with. It's got application libraries in it, so it's not a folder that contains your files shared out over a network, but rather it contains necessary software and libraries that need to be accessed, or shared, by all users of the local computer. If you're the only user then that's just you anyway. Don't remove anything from it as it will break things.

The folder size does not seem to be reporting accurately. I doubt very much that there's that much space on the drive to begin with.

---

### Post by jpdeaton on 2012-02-01
I ended up doing a command line minimal install. While gdm was installing I noticed a line that said "setting up user nopwd"   

Normal or no?

---

