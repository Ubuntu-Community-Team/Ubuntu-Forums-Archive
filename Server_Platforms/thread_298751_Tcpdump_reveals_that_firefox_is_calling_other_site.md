---
title: "Tcpdump reveals that firefox is calling other sites."
date: 2006-11-13
forum: Server Platforms
---

### Post by enthusiast on 2006-11-13
Hi,

I have been observing my tcpdump to see how much spyware is going on my machine.
I know that people don't believe that there is spyware in linux/firefox, but when I hit a website I do notice a lot of traffic going elsewhere that I can not account for from my own computer's running services.

What happens is that if I go to a site I  see requests going to other sites other that the one my browser is pointing to. I have set to accept only originating website images, but am still getting other traffic to third party sites.

What I am assuming is that the web page is telling the web browser to pull some of the content from third party sites. How can I turn this cross GETTING/POSTING off in Firefox?

I find that this is a potential invasion of privacy -- i.e. they can track your web browsing session across websites.

Isn't there some Netiquette where sites don't do this? I know the claim is that it enhances the Internet experience, but I think this is bullshit.

Also I had to manually set  to accept cookies from originating websites only. Why don't the browser manufacturers just set this as a default? This would force website designers to only design websites without cross cookiing.

---

### Post by detgar on 2006-11-13
Could you please post some specific sites where this happens? That would make it easier to see what actually happens.

Also, Firefox fetches links from the page you're currently on if idle, turn this off by going to the about:config tab and set **network.prefetch-next** to **false**.

---

### Post by enthusiast on 2006-11-13
Ironically,
Here is one. They want to help you remove spyware, but as you are watching the site it sends information to google.com, cnet.com, buildtraffic.com.

[http://spywarespy.com/](http://spywarespy.com/)


Ubuntu forums sends information to hitbox.com.

---

### Post by _AA_ on 2006-11-13
Did it ever occur to you that the sites you are viewing might have embedded images from other locations?

Just because you visit spyware.com doesn't mean that spyware.com hosts all it's content on the ip that the domain resolves to!

---

### Post by skymt on 2006-11-13
Try turning off third-party cookies.

Also, you may want to look into [Privoxy](http://www.privoxy.org/).

---

