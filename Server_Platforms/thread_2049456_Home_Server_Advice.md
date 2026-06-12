---
title: "Home Server Advice"
date: 2012-08-28
forum: Server Platforms
---

### Post by PriestyUK on 2012-08-28
Hi guys could you please share some of your great wisdom.

This is what I want to do, I have brought a Dell Powergate 1850 server and my plans for it is to create a home server.

Ive seen a bit of software called owncloud.org which I want to use to create my own cloud where I can back up to onw multiply platforms.  I want to also share this with my brothers where we can all have one music folder and movie folder which we share to and update to.

My problem is I feel to go to ubuntu desktop version rather than run a server version as I like the idea of being able to vpn into it etc what can you recommend and advice me on.

Thanks guys

PriestyUk

---

### Post by thnewguy on 2012-08-28
Rather than try setting up ownCloud you might want to consider a slightly different approach. What you seem to want with shared folders and backups is fairly straight forward to do on either Ubuntu Desktop or Ubuntu Server.

Try creating an account for userself and one for each of your family members. Install and neable Secure Shell (openssh) logins. In the /home folder create a new sub-folder called "shared" and make sure your family can read and write in that folder. Maybe make more folders under /home/shared called "video" and "music".

When you make backups, just make sure everything under /home is backed up. This will probably be easier than setting up and adminning cloud software, especially considering the small number of people involved.

---

### Post by bootedguy on 2012-08-28
Another approach is to buy a Pogoplug or Tonidoplug and setup a "private" cloud.

---

### Post by PriestyUK on 2012-08-29
I see what you are saying, but I like the thiught of owncloud as it supports mobile devices to :( Im new to this and felt like a new project so will take all advice greatfully :)

I have a imac running mountain lion and my brothers run windows 7, ubuntu will be able to talk to both right? (By using sumba yeah?)  

Me and my brothers dont all live together so was thinking of setting it all up at mine then taking it round my mums and plugging it in there as she has a 100mb fibre connection this wont be a issue will it?

So do I go with Ubuntu desktop?  And what features will I have to enable or install to get the desktop version to act like a server so to speak?

Thanks for the advice so far guys

---

### Post by HugoSerrano on 2012-08-29
Don't really know if i get it, but check XBMC.
Also, P.M. with the server link when it's done ;-P (kidding)

---

### Post by thnewguy on 2012-09-08
You can use Ubuntu Server for this or Ubuntu Desktop, whichever you feel more comfortable with. I believe ownCloud is in the Ubuntu repositories so installing it is a simple matter of running

sudo apt-get install owncloud

Once it is installed you can login to the web interface, probably at [http://localhost/owncloud](http://localhost/owncloud)
If you family has a static IP address, then you're good and you can just give people the IP address. If not, then you might want to get a name to dynamic address service like dyndns.org

---

