---
title: "How Does One Block Facebook on a System?"
date: 2020-08-18
forum: Security
---

### Post by uRock on 2020-08-18
Hi all,

I thought this was going to be an easy case of adding things to the host file. Apparently, the host file is just there for the giggles or I missed something. I am working to get it out of my life and off of my system. 

What have I done? I added the entries listed below, then powered off the system(it needed a restart anyway), and flushed DNS.

IPv6 is not in use.

Here's the output of **cat /etc/hosts**
```
127.0.0.1	localhost
127.0.1.1	PCname
127.0.0.1	facebook.com login.facebook.com secure.facebook.com latest.facebook.com inyour.facebook.com beta.facebook.com static.facebook.com touch.facebook.com developers.facebook.com newsroom.fb.com pixel.facebook.com apps.facebook.com graph.facebook.com m.facebook.com upload.facebook.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
Things like DNS servers, Proxies, router configs are out of the question.

---

### Post by TheFu on 2020-08-18
Firefox recently started using DoS by default, unless you tell it not to do so.  I don't know if this is the issue, but it could be.

BTW, seems you are missing [www.facebook.com](www.facebook.com).  I don't know what the limit is for 1-line, but I've never seen one that long.  Usually, people use 1-line per entry to make management easier.
[https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279)

Also, there are some characters in your host file above which aren't legal. remove those.

Setting up a pi-hole isn't THAT hard.  I run it in and lxd container.  Took about 20 minutes. I posted instruction links here.

---

### Post by uRock on 2020-08-18
Thanks TheFu. If you're referring to the illegal character, I am guessing it was in the apostrophe in the computer name. That line is fake as I never share the computer name. I just edited the OP.

I've cleaned up the file and added the line you recommended.

It was previously working in all three browsers, but now it is only working in Firefox, which is due to the enabling of their "security feature" that trusts Facebook. I went through most of everything [here]("https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections") and cleaned Firefox with Bleachbit, yet still it sees Facebook. I hardly ever use Firefox. Chromium is now acting the way I want it. 

Here's the working hosts file.

```
127.0.0.1	localhost
127.0.1.1	PcNameGoesHere

# No More Facebook
127.0.0.1       facebook.com
127.0.0.1       login.facebook.com
127.0.0.1       secure.facebook.com
127.0.0.1       latest.facebook.com
127.0.0.1       inyour.facebook.com
127.0.0.1       beta.facebook.com
127.0.0.1       static.facebook.com
127.0.0.1       touch.facebook.com
127.0.0.1       developers.facebook.com
127.0.0.1       newsroom.fb.com
127.0.0.1       pixel.facebook.com
127.0.0.1       apps.facebook.com
127.0.0.1       graph.facebook.com
127.0.0.1       m.facebook.com
127.0.0.1       upload.facebook.com
127.0.0.1       www.facebook.com

#This one listed as possibly hosting malware
127.0.0.1	cnbc7.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by uRock on 2020-08-18
This was the site I copied the single line of text from, [https://linuxconfig.org/how-to-block-facebook-access-on-linux-desktop](https://linuxconfig.org/how-to-block-facebook-access-on-linux-desktop)

---

