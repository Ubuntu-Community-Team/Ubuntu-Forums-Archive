---
title: "750+ MAC address registration"
date: 2006-11-16
forum: The Cafe
---

### Post by jd65pl on 2006-11-16
Hello,

I am on a university network and currently had my connectivity blocked by the administrators for registering 750+ mac addresses in a week! I have no idea how this could of happened, does any one have any idea how it could occur?

Thanks

---

### Post by dataw0lf on 2006-11-16
Is this a joke?

I'm really chuckling at this one, that's why I ask.

They obviously do mac address filtering and you're swamping their database.  How many boxes and how often do you authenticate with them at a time?  I can just see some junior sys admin having to enter mac addys by hand getting fed up with you and complaining.   
They might've cited performance reasons, but I doubt that's the real reason.

---

### Post by KoRnholio on 2006-11-16
I think his question was 'How did it appear to them that I registered 750 MAC addresses?'.

If he actually registered 750+ MAC addresses, I don't think he'd be confused.

Work of a hacker, or a mixup.  I don't know, because I don't know what a MAC address is.

---

### Post by ciscosurfer on 2006-11-16
And do you have 750 machines/nics that you are running from your dorm room?

Totally confused.  But amusing nonetheless.

Something fishy is definitely going on there...Maybe someone is using your box as a zombie and registering whole blocks of machines through you.

---

### Post by red_Marvin on 2006-11-16
Wouldn't 750 amc adresses require 750 NIC's?

---

### Post by dataw0lf on 2006-11-16
No, you can change your MAC address quite easily (that's how ARP poisoning works:  you sniff an authenticated MAC address and hijack it).

---

### Post by ciscosurfer on 2006-11-16
> **dataw0lf said:**
> No, you can change your MAC address quite easily.We call this MAC address spoofing :-D

---

### Post by dataw0lf on 2006-11-16
It's also called ARP poisoning/spoofing, due to the fact that ARP is the protocol that resolves MAC addresses to IP addresses.

---

### Post by jd65pl on 2006-11-16
Hi guys thanks for the replys.

No I dont have 750 nics! I am aware of ARP poisoning and have run a POC of the method on one of my machines. Is anyone aware of a game or other reason for this?

---

### Post by dataw0lf on 2006-11-16
Well, there's your problem.  I assume the proof of concept wasn't written by you, so here's my theory: the POC is grabbing ARP packets and replicating the MAC addresses contained therein, and then attempting to auth with said MAC addresses, on the external network.  You're going to be hard pressed to explain why exactly you ran a POC ARP poisoning attack on their live network. 

Moral of the story?  Run the POC, especially if you don't understand exactly what's going on, in a closed network.

What box and in what sort of network did you run the POC?

---

### Post by ciscosurfer on 2006-11-16
> **dataw0lf said:**
> It's also called ARP poisoning/spoofing, due to the fact that ARP is the protocol that resolves MAC addresses to IP addresses.You are quite correct, sir!

---

### Post by dataw0lf on 2006-11-16
> **ciscosurfer said:**
> You are quite correct, sir!


Well, thank god.  My company will be happy to know that the money they dropped on my CCIEs in R&S and Sec haven't been wasted.  On an online forum for a distro they refuse to use, no less!

:)

---

### Post by ciscosurfer on 2006-11-16
> **dataw0lf said:**
> Well, thank god.  My company will be happy to know that the money they dropped on my CCIEs in R&S and Sec haven't been wasted.  On an online forum for a distro they refuse to use, no less!

:)Too bad they refuse the 'buntu.  As a side question, how long did it take you pass your CCIE?  Did you pass on your first shot?  Pretty demanding test, that CCIE is. (and yes, Yoda I am). ;)

---

### Post by dataw0lf on 2006-11-16
> **ciscosurfer said:**
> Too bad they refuse the 'buntu.  As a side question, how long did it take you pass your CCIE?  Did you pass on your first shot?  Pretty demanding test, that CCIE is. (and yes, Yoda I am). ;)

Just passed my Sec lab a couple weeks ago.  R&S I passed the written and lab on both first tries.  Took a second attempt to get the Sec written, lab in one shot.

---

### Post by jd65pl on 2006-11-16
> **dataw0lf said:**
> Well, there's your problem.  I assume the proof of concept wasn't written by you, so here's my theory: the POC is grabbing ARP packets and replicating the MAC addresses contained therein, and then attempting to auth with said MAC addresses, on the external network.  You're going to be hard pressed to explain why exactly you ran a POC ARP poisoning attack on their live network. 

Moral of the story?  Run the POC, especially if you don't understand exactly what's going on, in a closed network.

What box and in what sort of network did you run the POC?

The POC was NOT run on someone else's live network. It was  run on a private network with only 3 machines and a router. Which was not open to any outside connection. It was run between an ubuntu a windows and a mac osx. AND was only run after the connection was blocked on the university network.

---

### Post by ciscosurfer on 2006-11-16
> **dataw0lf said:**
> Just passed my Sec lab a couple weeks ago.  R&S I passed the written and lab on both first tries.  Took a second attempt to get the Sec written, lab in one shot.Well done!

---

### Post by dataw0lf on 2006-11-16
> **jd65pl said:**
> The POC was NOT run on someone else's live network. It was  run on a private network with only 3 machines and a router. Which was not open to any outside connection. It was run between an ubuntu a windows and a mac osx. AND was only run after the connection was blocked on the university network.

Well something got out, I'm telling you that.  Don't you think it's hugely coincidental that you run a POC for ARP poisoning and then all of a sudden you're hit by your WAN's administrators for 750+ MAC address registrations?  The POC may have been viral.  Wanna send me the code?

---

### Post by dataw0lf on 2006-11-16
> **ciscosurfer said:**
> Well done!

Thanks! It was a huge relief to pass that Sec lab, I tell you what.  R&S I wasn't so worried about.

---

### Post by jd65pl on 2006-11-16
> **dataw0lf said:**
> Well something got out, I'm telling you that.  Don't you think it's hugely coincidental that you run a POC for ARP poisoning and then all of a sudden you're hit by your WAN's administrators for 750+ MAC address registrations?  The POC may have been viral.  Wanna send me the code?

NOTE I did not run it before to the connection blocking, the 750+ addresses were registered before! As this happened prior to me running the POC I fail to see why it would have any influence?!?!?!??!

Order of events
[LIST=1]
[*]Connection gets block - you have registered 750+ mac addresses
[*]I look in to the reasons why
[*]I run POC ARP poisoning on an isolated network
[*]I post my question on reasons for 750+ MAC addresses[/LIST]

---

### Post by dataw0lf on 2006-11-16
> **jd65pl said:**
> NOTE I did not run it before to the connection blocking, the 750+ addresses were registered before! As this happened prior to me running the POC I fail to see why it would have any influence?!?!?!??!


Whoa, sorry buddy.  No need to get agitated, I merely misunderstood your messages.  

I'd isolate the machines, tcpdump on all of them, and connect to a fake 'external' network, possibly by NATing between your router, the existing network when it happened, and another machine that was uninvolved.  I can help you do this if you have the hardware required.  Basically, we're looking for suspicious traffic so we can determine if there's some viral form of program on your existing network that created this problem.  Call your administrators and tell them what you're doing, too.  They might be interested enough to lend a hand (especially if it's replicated and they're seeing similar problems on other machines).

---

### Post by jd65pl on 2006-11-16
> **dataw0lf said:**
> Whoa, sorry buddy.  No need to get agitated, I merely misunderstood your messages.  

I'd isolate the machines, tcpdump on all of them, and connect to a fake 'external' network, possibly by NATing between your router, the existing network when it happened, and another machine that was uninvolved.  I can help you do this if you have the hardware required.  Basically, we're looking for suspicious traffic so we can determine if there's some viral form of program on your existing network that created this problem.  Call your administrators and tell them what you're doing, too.  They might be interested enough to lend a hand (especially if it's replicated and they're seeing similar problems on other machines).

Theres alot of incomming requests to ubuntu via ports 138 + 137, windows filesharing ports. Could a program such as skype which uses computers as nodes be giving this effect?

Sorry I wasn't getting agitated just trying to explain my situation more clearly.

---

### Post by dataw0lf on 2006-11-16
That's NetBIOS, got Samba on your Linux system?

---

### Post by jd65pl on 2006-11-16
> **dataw0lf said:**
> That's NetBIOS, got Samba on your Linux system?
Nope but it is a huge network (10000+ computers) with alot of people running itunes which may be scanning filestores for stuff

---

### Post by ciscosurfer on 2006-11-16
> **dataw0lf said:**
> Thanks! It was a huge relief to pass that Sec lab, I tell you what.  R&S I wasn't so worried about.The CCIE Security lab is quite a doozy--lot's of info that sometimes seems very contradictory.  I would agree that the Routing and Switching was a bit easier--of course, this all depends on how much R&S experience you have prior to taking the CCIE R&S exams.

---

