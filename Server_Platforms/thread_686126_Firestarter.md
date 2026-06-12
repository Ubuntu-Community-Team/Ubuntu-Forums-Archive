---
title: "Firestarter"
date: 2008-02-02
forum: Server Platforms
---

### Post by rockrocket on 2008-02-02
Hi guys,

I recently installed firestarter and notice that every time i turn it on and cuts off all internet connectivity in my mozilla browser.

I wanted to know instead of putting every single site that i want to visit and open the ports. Is there a way i can put my browser serving in front of my firewall or is there another way to have my browser full access without opening too many ports.


Thanks

I do, I learn, and I love it

---

### Post by ssuehr on 2008-02-02
Usually an outbound rule allowing TCP/80 and TCP/443 would cover browsing, as long as established and related connections are allowed back in.  Note that I'm not sure what your security requirements are though, so opening 80 and 443 outbound might not be plausible depending on your requirements.

Steve

---

### Post by rockrocket on 2008-02-02
I appreciate it, but i think maybe i'm better off putting the browser outside the firewall thats what i was really wanting to do, but thank you
ps; they should make the thank you icon bigger lol i was looking for it, but i found it.

---

### Post by Irihapeti on 2008-02-03
I wonder if you have got the outgoing policy set to "blacklist all traffic" which means you then have to set up each exception. Try changing it to "whitelist all traffic" or "allow all" and see if that helps.

The exact wording may be different, but it will be something very similar to that.

---

### Post by rockrocket on 2008-02-03
no it's on white list also when i tried to 

sudo apt-get update 

in the terminal while the firestarter was on it read all packages but didn't download them.

[I]-Usually an outbound rule allowing TCP/80 and TCP/443 would cover browsing, as long as established and related connections are allowed back in. Note that I'm not sure what your security requirements are though, so opening 80 and 443 outbound might not be plausible depending on your requirements.
[/I]


Also i have done this also to see but it still didn't help me browse.

---

### Post by rockrocket on 2008-02-03
I figured it out

Thanks for all the help i appreciate it.

---

