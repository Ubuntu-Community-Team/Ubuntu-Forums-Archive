---
title: "Sniffing Out Illicit BitTorrent Files"
date: 2009-02-14
forum: The Cafe
---

### Post by Sporkman on 2009-02-14
[http://www.technologyreview.com/computing/22107/?a=f](http://www.technologyreview.com/computing/22107/?a=f)

> **Sniffing Out Illicit BitTorrent Files**

A new tool promises to detect illegal files without slowing network traffic.

By Duncan Graham-Rowe

A new technique has been developed for detecting and tracking illegal content transferred using the BitTorrent file-trading protocol. According to its creators, the approach can monitor networks without interrupting the flow of data and provides investigators with hard evidence of illicit file transfers.

Contraband files might include pirated movies, music, or software, and even child pornography. When the tool detects such a file, it keeps a record of the network addresses involved for later analysis, says Major Karl Schrader, who led the work at the Air Force Institute of Technology, in Kettering, OH.

The use of peer-to-peer (P2P) software and of the BitTorrent protocol in particular have increased steadily over recent years. In fact, for many Internet service providers (ISPs), the vast majority of Internet traffic now consists of P2P transfers.

ISPs are generally only interested in detecting this type of traffic in order to control, or "throttle," it and free up bandwidth for other uses. However, this approach reveals nothing about the contents of each transfer, says Schrader. A handful of network-monitoring tools can identify specific BitTorrent files, but the process is generally slow, since the contents of each file have to be examined. The time that this takes also increases exponentially as the number of files that need to be scanned grows.

"Our system differs in that it is completely passive, meaning that it does not change any information entering or leaving a network," says Schrader. It works, he says, by first spotting files that bare the hallmark of the BitTorrent protocol by examining the first 32 bits of the files' header data. Then the system looks at the files' hash, a unique identifying code used to coordinate the simultaneous download of hundreds of file fragments by different users. If a hash matches any stored in a database of prohibited hashes, then the system will make a record of the transfer and store the network addresses involved.

"I'm convinced that the solution works and that it will be quite cheap, as it is very specialized," says Hendrik Schulze, chief technology officer of Ipoque, a network analysis company based in Leipzig, Germany. More generalized solutions that try to monitor for a wide range of file types may be more flexible, he says, but they will also be more expensive.

One reason why the new technique is so fast is that the apparatus required consists of a specially configured field programmable gate array (FPGA) chip and a flash-memory card that stores a log of the illicit activity.

This setup means that the contents of files can be scanned directly by tapping into an Ethernet controller buffer, thereby leaving the network's traffic undisturbed. It also means that it's impossible for users to tell if a network is being monitored, Schrader says. "Our system does not modify traffic in any way, nor does it interfere in the delivery of traffic either in or out of a network," he says.

Ross Anderson, a computer-security expert at the University of Cambridge, U.K., says that the idea is nothing new. "Cisco has for years been selling kits to the Chinese government for the 'Great Firewall of China' that does just what these guys propose," he says. Similarly, an Australian firm called Brilliant Digital Entertainment sells a tool called CopyRouter that analyzes hashes to identify illegal files on other kinds of P2P networks.

Schulze adds that the approach relies on having an up-to-date list of illegal files. "The system has to update a huge list of file hashes frequently," he says. "Somebody has to qualify the hashes as copyright infringements or other criminal content."

From a legal standpoint, Schulze says that privacy may be a more significant problem. "Neither the U.S. nor any European country would allow [anyone] to install a device that inspects the traffic of every user just to stop Internet piracy," he says. "In this approach, every user is considered to be suspicious."

Even if the legal framework were to allow the technology, it is not quite ready to go. Tests of the system, details of which will be published later this year in a book called Advances in Digital Forensics V, showed that it was effective at detecting 99 percent of illicit files, but only at speeds of 100 megabits per second.

That's too slow for commercial or law-enforcement purposes, according to Anderson. Schulze agrees: "One gigabit per second or ten gigabits per second are required today to monitor a network." He also says that it is unclear whether the system might produce false positives, incorrectly labeling legitimate files as illegal.

Another drawback is that the system cannot cope with encrypted files. "Today, about 25 percent of BitTorrent traffic is encrypted," says Schulze. If such a tool became widely used, then anyone with something to hide would almost certainly switch to using encryption, he says.

---

### Post by Kingsley on 2009-02-14
I'll just continue to stick with encrypted BitTorrent traffic. :)

---

### Post by wolfen69 on 2009-02-14
> **kingsley said:**
> i'll just continue to stick with encrypted bittorrent traffic. :)

+1

---

### Post by solitaire on 2009-02-14
+1 for encryption!
Not got anything to hide! I just like my privacy..

---

### Post by MikeTheC on 2009-02-14
This article makes me happy that I don't own any Cisco or Cisco-owned equipment.

---

### Post by blueshiftoverwatch on 2009-02-15
How would one go about encrypting their bittorrent downloads?

---

### Post by Polygon on 2009-02-15
its usually a setting. just set it to encrypt entire stream and your good.

bur seriously, why waste your time with developing something like this? the article even says:

> 
Another drawback is that the system cannot cope with encrypted files. "Today, about 25 percent of BitTorrent traffic is encrypted," says Schulze. If such a tool became widely used, then anyone with something to hide would almost certainly switch to using encryption, he says.


---

### Post by solitaire on 2009-02-15
> **Polygon said:**
> its usually a setting. just set it to encrypt entire stream and your good.

bur seriously, why waste your time with developing something like this? the article even says:


Think it's called the "Darwin" effect.
It will get those too stupid or careless out of the general population and subsequently off of the Internet, thereby letting the more intelligent surfers thrive on the increased bandwidth, low congestion broadband and having less dumb questions to answer in blogs and forums :D:lolflag::lolflag:

---

### Post by handy on 2009-02-15
Interesting, I hadn't looked at Darwin as being an egotistical, self centred, elitist before...

---

### Post by Barrucadu on 2009-02-15
Well, as the article says, this is what encryption is for. Slower downloads are worth it.

---

### Post by Paqman on 2009-02-15
> **solitaire said:**
> +1 for encryption!
Not got anything to hide! I just like my privacy..

+1
It's not even a privacy issue for me, i'd just rather not be throttled down.

---

### Post by DMcA on 2009-02-15
> **handy said:**
> Interesting, I hadn't looked at Darwin as being an egotistical, self centred, elitist before...

Darwin, no. Darwinism, natrually

---

### Post by handy on 2009-02-15
> **DMcA said:**
> Darwin, no. Darwinism, natrually

Due to the CoC, I will tread no further down this path. :P

---

### Post by 3rdalbum on 2009-02-15
Hahaha, that's hilarious. They are merely intercepting .torrent files and comparing the hashes against known illegal files? That's not newsworthy! I could implement that in Python in about 5 minutes.

It's not necessary to encrypt the files in order to defeat this system, although encrypting them is a good secure step. All you'd need to do would be to open your child porn picture in The Gimp, add a single red pixel to the bottom right corner, save it and then torrent it. For music files you could alter the ID3 tags, and for video files you could simply "cat" some random data to the end.

If Australian ISPs have to have a Bittorrent filtering system, I sure hope it's this one. Because it's a complete joke. I mean, come on, the RIAA and MPAA have a more sophisticated system than this!

---

