---
title: "Question about Gufw"
date: 2012-11-02
forum: Security
---

### Post by jsvidyad on 2012-11-02
Hello,

 This post is related to some other posts I made regarding ufw at these two links:
[http://ubuntuforums.org/showthread.php?t=1822813&highlight=ufw](http://ubuntuforums.org/showthread.php?t=1822813&highlight=ufw)
[http://ubuntuforums.org/showthread.php?t=1854616&highlight=ufw](http://ubuntuforums.org/showthread.php?t=1854616&highlight=ufw)

 The question I have is that the first time once I enable(activate) Gufw and use it to set up the firewall rules, will the firewall be active and those settings be in place every time I start up and boot into ubuntu in the future? Or every time I boot into ubuntu, will I have to check to see if the firewall(Gufw) is inactive or the settings need to be set again? I am asking this because I used firestarter till a couple of years earlier and once on randomly checking the iptales rules using 'sudo /sbin/iptables -L' I found that that all the chains were set to ACCEPT,i.e. the firewall was not active even though firestarter was supposed to load the firewall settings(incoming-deny,outgoing-allow) at each boot up. Since then, at each boot up, I would log onto the administrative account first, open firestarter and make sure that firestarter was active. Even after switching to ufw and then Gufw, I have been doing the same. Every time at boot up, I log into the administrative account first, open the Gufw window and make sure that Gufw is active(enabled) and that the settings are the same ones I initially set(incoming-deny,outgoing-allow). Is this necessary? Has someone ever reported a bug in Gufw or ufw of this nature where the firewall(Gufw/ufw) is somehow inactive at boot up even though it had been activated and the settings made at an earlier bootup? Or is there no reason for me to worry? Is Gufw a set and forget firewall of the kind we see on default installations of windows 7 where once the firewall is activated and set, it will be active with the correct settings at all future boot ups? 

   The second question is that while using laptops and you switch between wired and wireless connections with the computer on, will it affect firewall(Gufw) security or its settings in any way? 

   The third question is that for a laptop, once you log into an user account and connect to a wireless network, will the Gufw/ufw firewall immediately get activated and set the requisite rules?

---

### Post by thnewguy on 2012-11-02
1. When you enable your firewall using ufw or gufw, then the firewall rules are saved and will be there upon your next boot.

2. Usually when you set up rules they are device intependent, which means it won't matter if you are on a wired or wireless connection. The exception to this rule is if you specify a special device in your firewall rule.

3. The firewall remains active whether any users are logged in or not.

---

### Post by jsvidyad on 2012-11-02
Hello, can you please give answers to all the points I raised in my post?

---

### Post by Ms. Daisy on 2012-11-02
> **jsvidyad said:**
> The question I have is that the first time once I enable(activate) Gufw and use it to set up the firewall rules, will the firewall be active and those settings be in place every time I start up and boot into ubuntu in the future?  yes  > **jsvidyad said:**
> Or every time I boot into ubuntu, will I have to check to see if the firewall(Gufw) is inactive or the settings need to be set again?  you can, but you don't need to. > **jsvidyad said:**
>  I am asking this because I used firestarter till a couple of years earlier and once on randomly checking the iptales rules using 'sudo /sbin/iptables -L' I found that that all the chains were set to ACCEPT,i.e. the firewall was not active even though firestarter was supposed to load the firewall settings(incoming-deny,outgoing-allow) at each boot up. Since then, at each boot up, I would log onto the administrative account first, open firestarter and make sure that firestarter was active.  Yup, firestarter hasn't been maintained for years. I imagine there are some bugs in it, if that wasn't a purposeful feature to begin with. Plus firestarter, ufw, and gufw are all front-ends for iptables. Don't mess with iptables and gufw at the same time, pick one or the other for best results. > **jsvidyad said:**
> Even after switching to ufw and then Gufw, I have been doing the same. Every time at boot up, I log into the administrative account first, open the Gufw window and make sure that Gufw is active(enabled) and that the settings are the same ones I initially set(incoming-deny,outgoing-allow). Is this necessary?Nope. > **jsvidyad said:**
> Has someone ever reported a bug in Gufw or ufw of this nature where the firewall(Gufw/ufw) is somehow inactive at boot up even though it had been activated and the settings made at an earlier bootup? Or is there no reason for me to worry? Are you saying it's not active at boot-up? That's not typical behaviour if it's happening. I wouldn't report a bug yet. Post more details about this: give us the output of ```
sudo ufw status
``` > **jsvidyad said:**
>  Is Gufw a set and forget firewall of the kind we see on default installations of windows 7 where once the firewall is activated and set, it will be active with the correct settings at all future boot ups?  Yup. > **jsvidyad said:**
> The second question is that while using laptops and you switch between wired and wireless connections with the computer on, will it affect firewall(Gufw) security or its settings in any way?   Nope. Gufw is independent from your wireless/ethernet connection.  That's not to say you might want to consider different settings for home vs. wireless at Starbucks. > **jsvidyad said:**
> The third question is that for a laptop, once you log into an user account and connect to a wireless network, will the Gufw/ufw firewall immediately get activated and set the requisite rules? Yes.

[SIZE=3]**I encourage you to read th[SIZE=3]ese:[/SIZE]**[/SIZE]
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by jsvidyad on 2012-11-03
> Quote:
Originally Posted by jsvidyad  
Has someone ever reported a bug in Gufw or ufw of this nature where the firewall(Gufw/ufw) is somehow inactive at boot up even though it had been activated and the settings made at an earlier bootup? Or is there no reason for me to worry?
Are you saying it's not active at boot-up? That's not typical behaviour if it's happening. I wouldn't report a bug yet. Post more details about this: give us the output of
Code:
sudo ufw status

Hello, I have never seen that kind of behavior happening. The firewall(Gufw/ufw) has always been active with the correct settings whenever I checked it on boot up provided it had been activated and configured before that boot up. I was just asking if someone had ever reported seeing it inactive at boot up or with wrong settings even though it had been set and activated at an earlier boot up. That's what I once saw for firestarter

> Quote:
Originally Posted by jsvidyad  
The second question is that while using laptops and you switch between wired and wireless connections with the computer on, will it affect firewall(Gufw) security or its settings in any way?
Nope. Gufw is independent from your wireless/ethernet connection. That's not to say you might want to consider different settings for home vs. wireless at Starbucks.

Is it secure enough if I set Gufw/ufw firewall to deny all incoming connections and allow all outgoing connections. Is this setting good enough for both the home network and public networks?

---

### Post by OpSecShellshock on 2012-11-03
That depends on what you mean by good enough. Deny incoming and allow out is how it's set up to work by default, and for the way most people use computers it's fine. It will prevent a connection from being initiated by an external device no matter what kind of network you're on. Just understand that's the only thing it prevents.

---

### Post by cariboo on 2012-11-03
@jsvidyad, [https://bugs.launchpad.net](https://bugs.launchpad.net) is a good place to check if a bug has been reported, but be aware that anyone with a Launchpad account can report bugs, so there are many incomplete, or invalid bugs in the database as well.

---

