---
title: "Unexplained Tor speed up"
date: 2010-03-09
forum: Security
---

### Post by Herbivore on 2010-03-09
9.10 Karmic (LinuxMint 8)); FF3.5.8

Did the search first here, and there are a lot of Tor related posts to wade through. The posts concerning speed were dealing with a problem opposite to mine, namely, when using Tor there is sometimes a **sustained jump in download speed** to the maximum possible (~60KB/s). IP check at checkip.dyndns.org, tor status at showmyip.com, and check.torproject.org all indicated secure Tor browsing. 

Was running Noscript, Betterprivacy, and had Java and Javascript turned off. Was, however, using FF addon DownloadHelper. Do you think this is the culprit? Or was Tor just suddenly insanely fast? Or ...

---

### Post by cdenley on 2010-03-09
I believe tor always reconfigures itself to tunnel traffic through different servers. You probably just stopped using the server which was creating a bottleneck. I wouldn't be concerned about it.

---

### Post by rookcifer on 2010-03-09
> **Herbivore said:**
> 
Was running Noscript, Betterprivacy, and had Java and Javascript turned off. Was, however, using FF addon DownloadHelper. Do you think this is the culprit? Or was Tor just suddenly insanely fast? Or ...

The plugin might not be secure -- that is it could be leaking your real IP which is the reason for the speed up.

---

### Post by Herbivore on 2010-03-09
Thanks for the replies. It would seem unusual to get 60 KB/s through the Tor network especially when that is the maximum obtainable without Tor. Is there a way to check if a plugin is insecure?

---

### Post by rookcifer on 2010-03-10
> **Herbivore said:**
> Thanks for the replies. It would seem unusual to get 60 KB/s through the Tor network especially when that is the maximum obtainable without Tor. Is there a way to check if a plugin is insecure?

Well, if you're using Torbutton, you should be OK.  Are you?

---

### Post by Herbivore on 2010-03-10
> **rookcifer said:**
> Well, if you're using Torbutton, you should be OK.  Are you?

Yes, Torbutton 1.2.4

---

### Post by cdenley on 2010-03-10
You can always capture the traffic with wireshark to verify the traffic is going through tor. If you're using a thirdy party add-on for downloading, I can't tell you for sure the add-on uses firefox's proxy configuration. It may have its own.

---

### Post by Agent ME on 2010-03-10
If you use Vidalia with Tor, you can check the network map page to see what connections are being made through Tor.

---

### Post by nmyrick on 2010-03-13
I can't get Tor to work with my Ubuntu Karmic.  Can anyone tell me how to get it to work?  I'm new to using Tor on Ubuntu.  I have Vidalia, but I can't get firefox to work with the Tor button enabled.

---

### Post by Ijan on 2010-03-15
If you can't get Tor to work you have a different problem than the one discussed in this thread.

You will probably get better answers by finding another thread that has more in common with your problem and posting there or if you open a new thread of your own.

Mention which installation guide you were following (Tor-project, Ubuntu-wiki etc.) and at which point you got stuck.

---

