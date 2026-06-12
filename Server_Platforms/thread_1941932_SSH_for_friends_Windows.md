---
title: "SSH for friends? Windows?"
date: 2012-03-16
forum: Server Platforms
---

### Post by Hank_The_Dog on 2012-03-16
Ok,

After some great help from the community, I got my home server (which used to be only a simple samba share) up and going with openSSH.

Now, I have shell access from any remote location! :guitar:

My next goal is to be able to have friends and family access my server. Although, I would like restricted privileges on certain folders. Also It would be great if my samba share directory was the only accessible directory for the client.

I am not even sure if SSH is the right way to go for this?

1. What is the most convenient way of modifying user permissions? [I]
**chmod?**[/I]

Most of the users who will be accessing the server, are windoze users. 
And some of those users are (to say the least) not very competent.

2. What is the most user friendly way for them (windoze users) to access the server? 
***putty?***


Basically my goal is to host a server where my friends and family can store and backup data, in the most convenient way possible, without many (if any) security flaws. *Think drag and drop here. These kids like shiny buttons and mapped network drives. *
 

 Any help or tips would be great. 

Thanks again everyone.

---

### Post by Holdolin on 2012-03-16
Are your frinds at different location (other houses)?  If so you can open port 22 (ssh) on your firewall to let them in, but be warned the script kiddie out there probe the internet for open ports and 22 (ssh) is one of their favorites, so be sure your system is secure.  Also, your frinds will need to know the IP addy yuor ISP has assigned to you, and keep track if they change it (most home ISP's are dynamic.)

The easist way i know for your frinds to ssh in would be using putty.

Yes, chmod would be able to change permissions.

---

### Post by spynappels on 2012-03-16
This may be very difficult to achieve securely, even more so if the other users are not already Linux users.

If you are serious about this, I'd look at a VPN solution so at least the server is not world accessible.

---

### Post by Hank_The_Dog on 2012-03-16
Any tips on a good VPN solution? I have looked into logmein's hamachi. But not in great detail.

---

### Post by spynappels on 2012-03-16
OpenVPN is very good, takes a little setting up but the HowTo on the OpenVPN website is very comprehensive. Search on here for OpenVPN, there are a lot of good threads explaining some of the pitfalls to watch out for.

---

### Post by Vishal Agarwal on 2012-03-16
WINSCP can be the best option if the goal is for file transfer only [Upload/Download, as a web storage server].

---

