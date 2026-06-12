---
title: "I hear the word hacked too often ;-)"
date: 2011-01-03
forum: Security
---

### Post by xathras1982 on 2011-01-03
Hi,
So I've been going through my logs, my regular audits and some scans and everything looks fine. 
 
I just came online to post some results from a PCI Scan which I think are false positives and see a post that I think needs some guidance. So the work hacked is used, but what does that actually mean and how do we tell?
 
Can anyone put their hat into the ring and lets put together some steps to help those understand and put together some information that will help.
 
So, here goes for me:
 
- Check my firewall logs from UFW / Shorewall to see if anything is showing up
- I run a listing on all active processes and compare to the system I configured fresh out of the can
- I check the var/log files for mail, auth errors etc
- I have sudo locked down and check logs to see what has been done. I look for gaps/missing logs etc
- I run an NMAP Scan
- I run an Nessus Scan
- Compare files against a backup to check for differences
 
Any other suggestions?

---

### Post by cariboo on 2011-01-03
The majority of the people that start a thread here with the word hacked in the title, are mostly inexperiences users that seem to think that anything they don't understand is someone trying to hack/crack their system. It usually ends up that it is something that they have done to the system themselves.

The only cure for this is education, but how do you do that, if they never even notice the stickies at the top of the page. bodhi_zazen has put in a lot of time creating them, but they don't do a lot of good if no one reads them.

---

### Post by xathras1982 on 2011-01-03
> **cariboo907 said:**
> The majority of the people that start a thread here with the word hacked in the title, are mostly inexperiences users that seem to think that anything they don't understand is someone trying to hack/crack their system. It usually ends up that it is something that they have done to the system themselves.
 
The only cure for this is education, but how do you do that, if they never even notice the stickies at the top of the page. bodhi_zazen has put in a lot of time creating them, but they don't do a lot of good if no one reads them.
 
I agree. I've sent two weeks reading through the stickies here and I've got everything up and running as per suggestions :). However, I do have some Linux experience :)

---

### Post by handy on 2011-01-04
> **xathras1982 said:**
> I agree. I've sent two weeks reading through the stickies here and I've got everything up and running as per suggestions :). However, I do have some Linux experience :)

From what I've seen over the last 5 years or so is that in general Linux desktop boxes don't get hacked, cracked, viruses, root-kits, or other mal-ware installed on them. If they did there would be a whole lot of posts in this forum about these problems.

The only posts in these forums about these problems are from people worried about these problems, NOT from people suffering from these problems.

If you don't believe me do some web searches on the topics, all you will get will in the end turn out to be nothing.

Which is nice eh!? :)

---

### Post by msandoy on 2011-01-04
> **cariboo907 said:**
> The majority of the people that start a thread here with the word hacked in the title, are mostly inexperiences users that seem to think that anything they don't understand is someone trying to hack/crack their system. It usually ends up that it is something that they have done to the system themselves.

The only cure for this is education, but how do you do that, if they never even notice the stickies at the top of the page. bodhi_zazen has put in a lot of time creating them, but they don't do a lot of good if no one reads them.

Readers of stickies count = 2

I have spent quite alot of time reading those stickies, may I suggest compiling them into a security manual in the same spirit as manual-ubuntu.org project?

The word Hacking has got a bad reputation from various Hollywood movies and clueless journalists. And I have been following many posts in here regarding "Hacked" systems. There are two common faults in those systems mentioned. 1. Server services with poor/non-existent password open to the internet. 2. Users who have done configurations/installations they do not understand.

I have been messing around with Linux for a few years, and I have to say, I have messed up my systems quite frequently. But I'm still learning. I might be above medium computer interested, since I have 4 stationary computers and 3 laptops running in local network. I'm testing hardware configurations and server services. And when your internet connection starts lagging like a can of glue, and the server logs grow exponentially in a matter of seconds, it's back to reading up on security again.

---

### Post by xathras1982 on 2011-01-04
> **msandoy said:**
> I have been messing around with Linux for a few years, and I have to say, I have messed up my systems quite frequently. But I'm still learning. I might be above medium computer interested, since I have 4 stationary computers and 3 laptops running in local network. I'm testing hardware configurations and server services. And when your internet connection starts lagging like a can of glue, and the server logs grow exponentially in a matter of seconds, it's back to reading up on security again.
 
Lol, me too - hence the reason I try it first out in VirtualBox ;-)

---

