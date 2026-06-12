---
title: "[SOLVED] Setting up a website on Ubuntu VPS"
date: 2015-06-27
forum: Server Platforms
---

### Post by adam153 on 2015-06-27
Hello everyone.  New to the forum! I've had a class with Red Hat Academy a year or so ago and that's gotten me started on Ubuntu besides a lot of tutorials :D.

Anyway, let's cut to the chase.  I was able to get apache2 to work (set up for ip connect to visit the website) however I am stranded when it comes to setting up the domain for it.  I tried some tutorials online but there's no way to tell if I was using the right ones.  I essentially have a Ubuntu VPS and I have a domain on GoDaddy.com and I can't seem to figure out how to set up the domain properly.  P.S.  I don't want to just mask the website.  I.E.  I want extensions:  [www.example.com/index]("http://www.example.com/index"), [www.example.com/forum]("http://www.example.com/forum"), [www.example.com/about]("http://www.example.com/about")  etc.

I'm not asking for a step by step (Unless you're willing :D)  but I would like to be pointed in the right direction.  I tried to use bind9 and didn't have much success.  Sorry; just another noob swinging by.  And thanks, I hope I can get the help I need.

---

### Post by darkod on 2015-06-27
From what you said I assume you can reach the apache default page by IP, right?

For a simple setup of couple of domains, don't bother with your own bind (dns) server. Unless it's really necessary for your setup, and it doesn't sound like that.

Open your GoDaddy panel, go into the DNS options, and in the A records section set the main @ record to point to your public IP assigned to the VPS. Also in the dns options look if there is already an A record or CNAME record for www, and make it point to the same IP (or to @ if it's CNAME). If it doesn't exist you can create new CNAME record called www that points to @.

That covers the domain dns setup. The GoDaddy dns servers will do the dns resolving.

From there on, it depends only on apache and how you configure it. If it's already running, upload your files in the correct folder and you should see your domain open when you type [www.domain.com](www.domain.com) in a browser.

---

### Post by adam153 on 2015-06-27
Edit2:  So, something along these lines?  [[]("http://i.imgur.com/rqJLjar.jpg")img removed]

P.S.  arkgaming.net forwards to the direct http:// ip, (it said it may take 1-48 hours to apply changes from that panel), but [url removed] redirects to a type of apache default site it seems.  Just want to know if after the domain updates, if it would all work?  I'm not too sure as what to set the apache settings at, either.  I.E.  I would like a www. in front of the url but in apache settings that's done through the alias, which in this case would be [www.i]("http://www.ip")p

Edit3:  I've just uninstalled bind9 from my VPS and now [url removed] and [url removed] redirect to the same page, but if you were to enter the IP addr it would work just fine: [url removed] should I just wait it out until GoDaddy does its magic?  Currently through apaches .conf files I have it pointing to /var/www/[name removed]/public_html  which will work with the direct ip (the .conf is [name removed].conf)

---

### Post by cariboo on 2015-06-27
Why do you think you need /var/www/158.69.1.146/public_html, the default apache2 configuration points to /var/www/html, I'd suggest using the default configuration, until you've learned to use apache2. If you don't want others altering files in the /var/www/htrml directory, just use the default permissions. You are making things more complicated than they need to be.

---

### Post by darkod on 2015-06-27
The DNS is already working. That is a standard warning that any changes might take up to 48hrs to propagate to nameservers worldwide, but usually it works much faster than that. Your domain is already resolving to that IP.

Now, the apache part, I agree with cariboo. As I mentioned, for a start, simply upload your files to the default apache folder (/var/www/html) and check if that opens the website you expect. Keep it like that until you get more familiar with apache. In fact, you never need to change it, not really a need for that.

---

### Post by adam153 on 2015-06-27
Fantastic!  Thank you both very much.  That's what I get for following some tutorials I guess...  It works perfectly when I transferred the data into the /var/www/html folder.  I guess I wasn't so trusting of this since I didn't realize the time it took to load the website properly via GoDaddy and that our previous website ~ 1-2 years ago wasn't hosted via a VPS but some stupid CMS website that I advised my friends against.  Thanks, again (P.S. editing prior posts to remove some information)  Will change title to [SOLVED]

---

