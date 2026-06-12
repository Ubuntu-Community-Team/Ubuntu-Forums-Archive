---
title: "Help with setting up webdav on Ubuntu"
date: 2011-03-11
forum: Server Platforms
---

### Post by harisund on 2011-03-11
Hello ! 

I basically want to setup webdav on my Ubuntu machine. I googled for it, and the HowtoForge tutorial link is helpful, but not entirely. I would appreciate if someone could guide me towards customizing that tutorial to fit my needs. 

First and foremost, I don't have a qualified host name. My ISP gives me a public IP that my dd-wrt router takes, and my machines are all behind the wireless LAN. If anything, the IP of my "server" is 192.168.1.23 and the IP of my "client" is 192.168.1.14. What should I be entering in my apache configuration file? Do I still use "example.com" ? 

Next, I don't want to create a folder called "example.com" . I either want my home directory shared out through WebDAV, or one directory within my home directory (I am looking at Dropbox, typically). Do I still need to change permissions ? (chown www-data?) Can I create a symlink to dropbox elsewhere perhaps and give permissions to www-data for that symlink? 

Please help!

---

### Post by volkswagner on 2011-03-11
You had me until you mentioned dropbox.  Are you wanting your dropbox folder to be inside your webdav folder or vise versa?  

You can get a free domain name from places like noip.com or dyndns.com.

---

### Post by harisund on 2011-03-11
> **volkswagner said:**
> You had me until you mentioned dropbox.  Are you wanting your dropbox folder to be inside your webdav folder or vise versa?  

You can get a free domain name from places like noip.com or dyndns.com.

Here's the thing - I have a Nokia smart phone, and Nokia smartphones have the capability to "mount" a Webdav directory, which can then be accessed using the file explorer interface etc. I would like to have my Dropbox available on Webdav yes, so I can edit my Dropbox text files directly on my phone if required 


I do have a free domain name, harisund.homelinux.com . I have setup my dd-wrt router to automatically update it if the DHCP address from my ISP changes. But there's NAT in the background. Technically all of the machines on my LAN have that as a hostname. Is that ok? Wont that cause problems?

---

### Post by volkswagner on 2011-03-11
> **harisund said:**
> Here's the thing - I have a Nokia smart phone, and Nokia smartphones have the capability to "mount" a Webdav directory, which can then be accessed using the file explorer interface etc. I would like to have my Dropbox available on Webdav yes, so I can edit my Dropbox text files directly on my phone if required 

Nice... My N95-4 has older OS, so no native WebDAV :(  it is disappointing that Nokia does not integrate with backports!  Does your device also support SAMBA natively?  Not to make this a Nokia thread, but other apps I like are, Putty, microWOW, JoikuSpot, jmIRC,...

> **harisund said:**
> 
I do have a free domain name, harisund.homelinux.com . I have setup my dd-wrt router to automatically update it if the DHCP address from my ISP changes. But there's NAT in the background. Technically all of the machines on my LAN have that as a hostname. Is that ok? Wont that cause problems?

When you say hostname I hope you mean domain name, since all your machines should not have the same hostname.

When you run 
```
hostname
```
and 
```
hostname -f
```
on your server what do you get.

Perhaps you can have your domain name entry server1.harisund.homelinux.com, or what ever you get from the hostname command in replacement for "server1".

---

