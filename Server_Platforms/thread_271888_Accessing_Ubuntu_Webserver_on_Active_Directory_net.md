---
title: "Accessing Ubuntu Webserver on Active Directory network"
date: 2006-10-05
forum: Server Platforms
---

### Post by OneSeventeen on 2006-10-05
I would like to set up my Ubuntu box so I can access the website hosted on it using the server name (or any name I choose).

We are on an Active Directory, so if my desktop is named "oneseventeen" then I can go to any computer on the network and type in: [http://oneseventeen/](http://oneseventeen/)
and it goes to the website hosted on my computer.  (currently running XP Pro)

I would like to do the same thing, but with an Ubuntu box.

So I need to install samba and connect it to the network somehow?

---

### Post by inthewayboy on 2006-10-05
Actually if that's all you want you just need to create a DNS record for the ubuntu server on your Active Directory DNS server. You'll want to give the ubuntu server a static IP, and once that record is in the system all of your clients should be able to hit it by the hostname.

Now if you want it to join the domain so you can share user/pass and security and such then that's a different story.

---

### Post by OneSeventeen on 2006-10-06
Awesome!

I just had to go to the domain controller, launch the DNS control pannel, go to the reverse lookup foder, then my local intranet, then right-click, New Host(A), then filled in my desired name "linuxtest" and the IP "10.0.0.66" and clicked OK!

And yes, having it share folders is another bear altogether, and hopefully I'll get that figured out soon too.  (but that is [another post](http://ubuntuforums.org/showthread.php?t=255996), as is the topic of having [transparent active directory logons](http://ubuntuforums.org/showthread.php?t=255432) using Ubuntu.)

Thanks for the tip!

---

