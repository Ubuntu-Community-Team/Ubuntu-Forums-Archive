---
title: "Wireshark Shows Odd Connections with Skype....When I Don't Have It Installed"
date: 2020-03-24
forum: Security
---

### Post by KenUBF on 2020-03-24
The Issue and my Concern:

Hi all, I had a question about some Wireshark results I've been getting lately. I have been getting a ton of Skype connections when running Wireshark. This is strange because I've never used Skype and don't have it installed. I've looked up the IP addresses that I'm connected to and couldn't find anything on them. It made me wonder about a possible hacking attempt or some kind of remote connection from malware. I have been downloading from torrents lately and I got lazy and didn't scan them like I usually do so I wondered if perhaps I downloaded some kind of trojan or something along with the files.

What I Did to Try to Figure out What's Going On:

I do have the LBRY app running in the background and I've wondered if that could be what Wireshark is picking up, just misidentifying the traffic. To test this I shutdown LBRY and confirmed that no instances were running with netstat and htop while running Wireshark and there does seem to be a large decrease in Skype packets, but they still come through, just about 80% less when I shut down LBRY. Then I restarted LBRY and the flood of alleged Skype packed spiked again in Wireshark.

This makes me wonder if Wireshark is merely misidentifying the traffic as Skype, but why do those connections persist when the app and the connections are shut down and don't show up in the netstat and htop results? I was wondering if perhaps someone could be hiding their hacking attempts in traffic they saw from my machine. I’m still learning about this kind of stuff and I’m not sure if that’s realistic. 

I also ran rkhunter and chkrootkit and I know these apps are more for servers since files change so often on Desktop Linux but I figured I'd cover my bases. rkhunter said it found 6 rootkits. That number is very high from when I've run it in the past. Usually I'll only get 1 or 2 confirmed false positives, but 6? Again, I was wondering if there may be a few false positives and maybe I had downloaded something bad.

 After writing all this out I am feeling better about my theory that it’s most likely the LBRY app running in the background but I suppose I am just paranoid and want to be sure if my instincts are correct and want to see what others think.

 Anyone else use the LBRY app and get the same results? I attached a screenshot of a small portion of the results for reference.

---

### Post by EuclideanCoffee on 2020-03-24
You already stated the problem. You've been downloading torrents and cannot identify which application may be the trojan.  In security terms, you've been conducting high risk activity, which will make you at higher risk to be compromised. There is no other way for us to troubleshoot. You're likely compromised either way. I'd reformat at this point.

---

### Post by KenUBF on 2020-03-26
Thanks for the reply. I believe I've finally isolated the program sending the traffic. Today I turned off the LBRY app all day and ran Wireshark and saw no Skype packets at all. I think even after the app closes it seems to send some data temporarily, but for how long I'm not sure. It seems to be a good while. After seeing this today I opened the app again and saw the flood of Skype packets again. It looks like Wireshark is just misidentifying the traffic, confirming my original theory. It doesn't look like I downloaded anything bad. I did multiple scans with antivirus and saw nothing odd going on with the network today. I just need to be more careful and scan all files I download. Lesson learned!

---

