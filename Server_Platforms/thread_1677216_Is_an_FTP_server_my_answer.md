---
title: "Is an FTP server my answer?"
date: 2011-01-28
forum: Server Platforms
---

### Post by garfonzo on 2011-01-28
Hi Folks:

I need to share files with 3-5 users across the internet who are all part of a small business. We use these files daily, create new files, and generally work with them as any office would (MS Word, Excel, and PDF type documents - nothing fancy). 

I'm wondering if an FTP server would accomplish this as each user could log into the FTP site, navigate the folder hierarchy, and download the file they want to work with. The problem is, the files that are being downloaded would absolutely need to be re-uploaded to be saved on the server. We couldn't have users leaving copies of the files on their workstations. 

Some questions:
[LIST=1]
[*]Is there any way to ensure/force/suggest users re-upload the file that they've downloaded?
[*]Is there a way to lock a file from being downloaded if another user has already downloaded the file for use?
[/LIST]

Basically, I'm looking for a system where users can "check out" a file and then must "check it in" at the end of the day. 

Any ideas?

Thanks!

---

### Post by amish_geek on 2011-01-28
Take a look at a service like [www.dropbox.com](www.dropbox.com)

If you want to "check out" and "check in" files and be able to "roll-back" to a previous version, then a solution like SVN or GIT might suit your needs.  But for 4-5 people, using a solution like dropbox, where every user has a mapped drive/folder that is kept synched across all computers would probably be best.

---

### Post by lukeiamyourfather on 2011-01-28
The "proper" way to do this would be to setup a VPN for the remote users and have them mount a common shared directory (NFS, Samba, whatever). Their computer would see the mount as if it was a local disk and they could save and work without have to worry about uploading changed documents again because it would all happen in real-time.

---

### Post by garfonzo on 2011-01-28
> **lukeiamyourfather said:**
> The "proper" way to do this would be to setup a VPN for the remote users and have them mount a common shared directory (NFS, Samba, whatever). Their computer would see the mount as if it was a local disk and they could save and work without have to worry about uploading changed documents again because it would all happen in real-time.

Indeed that would be the best solution. However, that would require a fairly beefy server and relatively expensive software to handle the virtualization of up to 5 users at once. That might be a bit pricey. I'm hoping I can find an alternative that is a bit more cost effective yet still meets all out needs.

---

### Post by garfonzo on 2011-01-28
> **amish_geek said:**
> Take a look at a service like [www.dropbox.com](www.dropbox.com)

If you want to "check out" and "check in" files and be able to "roll-back" to a previous version, then a solution like SVN or GIT might suit your needs.  But for 4-5 people, using a solution like dropbox, where every user has a mapped drive/folder that is kept synched across all computers would probably be best.

I have actually heard of Dropbox but totally forgot about it. This looks like a possibility. Thanks for the link.

---

### Post by HermanAB on 2011-01-28
Here is a better solution:
[http://www.knowledgetree.com/](http://www.knowledgetree.com/)

---

### Post by garfonzo on 2011-01-28
> **HermanAB said:**
> Here is a better solution:
[http://www.knowledgetree.com/](http://www.knowledgetree.com/)

Thanks for this! While this is precisely what I am looking for, this is a paid for service. I want to host the system and all the files on our company's server.

---

### Post by lukeiamyourfather on 2011-01-28
> **garfonzo said:**
> Indeed that would be the best solution. However, that would require a fairly beefy server and relatively expensive software to handle the virtualization of up to 5 users at once. That might be a bit pricey. I'm hoping I can find an alternative that is a bit more cost effective yet still meets all out needs.

It would not take a beefy server at all, even an Atom based server could handle five users in this scenario. The only thing the server would be doing is forwarding network traffic from point A to point B and handling the authentication/encryption.

There are open source VPN clients and servers available so the software doesn't have to cost anything (as long as you don't need support). 

[http://en.wikipedia.org/wiki/OpenVPN](http://en.wikipedia.org/wiki/OpenVPN)
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

