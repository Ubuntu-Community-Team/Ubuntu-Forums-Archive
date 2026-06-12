---
title: "File server vs remote desktop security questions for archiving pictures"
date: 2008-09-27
forum: Security
---

### Post by flatland2d on 2008-09-27
Since I got my first digital camera a couple years ago, the "My Pictures" folder in my Windows partition has exceeded 100GB.  This was before I got into Linux, else my pictures would have been stored under Ubuntu.:)

Anyway, I've been wanting to move my pictures folder to its own network storage drive to get them off the OS drive and be able to access them from anywhere on the network without my desktop having to be on.  Then I got into the idea of building a barebones computer that would act as my network storage drive (set up with redundant raid array), plus add some addition features like being able to run Ubuntu and having a remote desktop connection to my house network.  The computer would sit in a closet with the remote desktop being the only interface to it.

So my question is, with enough security, such as a VPN to my server computer, would my pictures be protected from being accessed or destroyed by a hacker?  What exactly would be required to secure this as much as practical?

What about security from the OS?  Would I be better off running a dumbed down file server instead of the full blown OS?  I just don't want the OS to accidentally corrupt or otherwise destroy my pictures.  Are there any options I could set up in Ubuntu to safeguard these pictures from becoming corrupt or deleted?

Anything else I should consider?  My goal is to find the safest and most practical way to store my pictures.  If there is a better way, please let me know.  Thanks!

---

### Post by cariboo on 2008-09-28
If your server isn't accessible from the internet and you are behind a good hardware firewall you have nothing to worry about from that end. If someone has access to your network internally, that is more worrisome. I would also suggest not relying on a raid array to store your valuable data. Hard drives fail, it is just a matter of when. I hope you have a good backup plan, and have at least two complete sets of backups, with one set preferable off site.

Jim

---

### Post by flatland2d on 2008-09-28
So would setting up a remote desktop on the server make it vulnerable even with a VPN?  It doesn't have to be 100% locked down, but a reasonable amount of security for personal stuff.  Part of the reason for building a server is to be able to use a remote desktop on my home network from the outside internet, and if that is just too insecure, I might reconsider just getting a file server.

What else do you suggest I look into instead of a raid array for backup?

My hardware firewall is a Linksys router running DD-WRT.  Do you consider that good enough?

I don't think it's too likely of a possibility that someone gains access to my home network.  I know it's not totally secure, but I do use WPA-PSK on the wireless side.  I live in a rural area and not many people are even close enough to get a signal on my router.

Thanks for helping me out!

---

### Post by cariboo on 2008-09-28
Your linlksys is more than enough to protect your network. Using VPN will make it harder for anyone else to access your network. As extra protection use either Denyhosts or Fail2ban to deny anybody from accessing your network after the default is 5 failed tries. Also use a strong password, the stronger the password the harder it is for someone to crack it.

Jim

---

### Post by flatland2d on 2008-09-28
Cool.  Thanks again for the help.

---

### Post by Biochem on 2008-09-29
> **flatland2d said:**
> 
What else do you suggest I look into instead of a raid array for backup?



A raid array IS NOT A BACKUP SOLUTION. If your array gets corrupted, you loose your data. If your server get's stolen you loose your data. If your house get burned you loose your data (by the fire or the water used to extinguish it). If you delete or reformat your array by accident you loose your data. Etc.

A raid array is more a way to either get a bigger harddrive (Raid0) or increase your your availability. Like if you are using your file server as a backup server you might want to make sure it continues to work even if one or more HD are broken.

---

