---
title: "Remote file access questions- currently  using openssh- what about vpn, samba?"
date: 2008-11-18
forum: Server Platforms
---

### Post by bcn17 on 2008-11-18
Right now I have a 8.04 ubuntu server running openssh. I use it to store media mostly. I access it with sshfs and it is basically seamless except for instance when I used the ubuntu usb application to make a install disk I had to copy the image from the server to my laptop. Anyways, I am wondering why people choose to go with samba, or a vpn over openssh. It seams openssh is very secure and with sshfs integrates very nicely. What do you recommend I do and why?

Security is very important to me, seeing as I access my files from multiple locations, sometimes untrusted connections. So I like openssh's ability for keys. (What I'm using)

I expect it to be seamlessly integrated. (openssh is)

In the future I play on possibly putting certain things like my mozilla thunderbird profile and firefox bookmarks and other /home folders/files on the server so that I can have seamless usage between my laptop and desktop. I would like basically ANY data I need to be stored on the server. I suppose the entire home directory could be on the server but this might degrade performance? I don't know. 

Recommendations, ideas, wise thoughts please!

---

### Post by bcn17 on 2008-11-18
bump :)

---

### Post by kevdog on 2008-11-19
a vpn over ssh?

That statement doesn't make much sense.

Both vpn and ssh offer end-to-end encryption.  Depending on how your vpn is configured, you can make a computer accessing your local LAN over the VPN, appear as if it were one of the local LAN computers.  All applications are automatically tunneled over the VPN -- with SSH you need to set up port forwarding for this.

SSH is much easier to set, maintain and run unless I guess you are a sysadmin and do VPN things for a living.

In my experience samba is buggy, but does interface with windows quite well.

---

### Post by bcn17 on 2008-11-19
> **kevdog said:**
> a vpn over ssh?

That statement doesn't make much sense.



I meant vpn over ssh as in use a vpn rather than openssh. Like using item x over item y. But thanks for your input!

---

