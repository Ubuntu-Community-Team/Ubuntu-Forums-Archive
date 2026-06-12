---
title: "can't reach ISPConfig page"
date: 2009-01-17
forum: Server Platforms
---

### Post by 10sJunkie on 2009-01-17
I am a complete noob to servers and linux and Ubuntu.... but, Following the "Perfect Server 8.04" tutorial, I managed to get all the packages installed and configured with ISPConfig installed on top of the whole pile...

Now the system tells me that I can point a browser to the domain and find the ISPConfig page at :81 but when I did that, I get an error telling me there is a problem loading the page.

Any ideas what I should check first? I'm so tired, I can't think!
Thanks in advance,
Becks

---

### Post by spiderbatdad on 2009-01-17
That error could be caused by a number of factors...do you have a router, and is it forwarding request on port 81 to the local ip of your server?
Are you listening on port 81 in ports.conf?

---

### Post by 10sJunkie on 2009-01-18
I do have a router - not sure how to check if it is forwarding post 81 but I can also just reach across the desk and plug my laptop into the server. Would that work as a test to eliminate the router?

I believe I am listening to port 81 (but I will check that config file). 

One this occured to me last night... I should check and make sure the server knows itself by the name I am calling, right? I should look in the /etc/hostname file?

---

### Post by 10sJunkie on 2009-01-18
update: nmap says the server is listening where it should...

---

### Post by spiderbatdad on 2009-01-18
I just read through the tutorial you followed...[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5) That one?
Personally, I would purge my system and start from scratch using Ubuntu community based documentation as a primary source. I would install one service at a time and try to not only get it working, but understand a bit of how it works and what config files do what.

Two good guides to get you going:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

The reasons for suggesting the above are that guides uses practices not supported by the forum, ie., enabling a root login, and disabling AppArmor, and that guide installs too many services at once. Do you really want a mail server running? It is a lot more involved than the instructions provided there.

---

### Post by 10sJunkie on 2009-01-18
Funny you should say that. Believe it or not, I have started over from scratch 7 times in order to get as far as I have... Not knowing what all I'm doing is both good and bad at different times. But I know so little about what I'm doing that I would not know where to start without a tutorial such as what I used.

To answer about the mail server - yes. I do want one eventually. But the ISPConfig software won't install unless you have postfix ready to go. So I went back and put it in when I realized that.

---

### Post by 10sJunkie on 2009-01-19
Ok. I'll do it your way.

---

