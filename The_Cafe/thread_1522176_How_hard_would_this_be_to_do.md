---
title: "How hard would this be to do?"
date: 2010-07-01
forum: The Cafe
---

### Post by dragos240 on 2010-07-01
I just thought of something this morning. Have a website that allows users to (not permenently) gain more RAM and CPU. We can do this with distcc and cluster computing. But I'm thinking of the idea of a website that gives out a client and server for a user, they will download a server, and thus contribute more CPU/RAM to the site, while downloading the client allows users to access all of that extra CPU and RAM. I don't know how feasible this is, but is it possible?

---

### Post by undecim on 2010-07-01
This would only be useful for solving NP complete problems, like cracking passwords or protein folding (like F@H does)

In other words, this would be abused beyond reason by password crackers, wouldn't make your desktop any faster (because of network latency), and is better done by the institutions that actually need it with their own centralized servers and volunteer or paid computing.

---

### Post by dragos240 on 2010-07-01
> **undecim said:**
> This would only be useful for solving NP complete problems, like cracking passwords or protein folding (like F@H does)

In other words, this would be abused beyond reason by password crackers, wouldn't make your desktop any faster (because of network latency), and is better done by the institutions that actually need it with their own centralized servers and volunteer or paid computing.

Actually I was thinking it could be used for major compile jobs.

---

### Post by Simian Man on 2010-07-01
It's impossible to "give a computer more RAM" using some kind of network storage.  Hard drives are way faster than network access, so it would be slower than swapping and thus defeat the purpose.

As for giving CPU cycles, what undecim said.

---

### Post by Sporkman on 2010-07-01
Computers are so cheap & powerful these days, no one has to settle for less computing power than they need on site.

---

### Post by schauerlich on 2010-07-01
> **dragos240 said:**
> Actually I was thinking it could be used for major compile jobs.

Gentoo@home?

---

### Post by NightwishFan on 2010-07-01
I have heard of games that will run on old machines because all the processing is done on a server, but that may just be a rumor.

---

### Post by schauerlich on 2010-07-01
> **NightwishFan said:**
> I have heard of games that will run on old machines because all the processing is done on a server, but that may just be a rumor.

That's different. A lot of MMO games have the actual game world being managed on a central server, with clients only sending and receiving information about where things are and what's going on. The client then renders the scene based on this information.

---

### Post by chessnerd on 2010-07-01
With SSH it might not be too difficult, but there would be some limitations. I know that it is possible to run programs on another computer through SSH...

```
ssh jsmith@comp program
```
You can even do X forwarding with -

```
ssh -X jsmith@comp gui-program
```
You could set up a system whereby you grant use of another computer through SSH and that person could run a program on there. However, they would not have direct access to their own local files on that computer. For compiling code, however, it wouldn't be too bad.

To compile something, the user would need to do is upload whatever files they are working on to that server, and then compile them on the server, and then download the results when it was done.

If you wanted to set this set up as a peer-to-peer system, then users would need to grant temporary use of their computer's hard drive, RAM, and CPU. You should be able to set up an encryption system to keep it private while the files are being used, set it so that only a certain amount of RAM may be used by the remote users, and throttle the remote programs so that they don't eat all the CPU.

It would be a complicated project. I'm not sure how many people would agree to let their computer be used like this. But I think it would be possible.

---

### Post by Sporkman on 2010-07-01
You could also use RPC calls (for example using [http://en.wikipedia.org/wiki/Open_Network_Computing_Remote_Procedure_Call](http://en.wikipedia.org/wiki/Open_Network_Computing_Remote_Procedure_Call)) to expose function calls to remote clients.

---

### Post by NightwishFan on 2010-07-01
Yeah its different because thats not what I am talking about. It may have been some kind of html5 speculation though who knows.

---

### Post by 98cwitr on 2010-07-01
> **Simian Man said:**
> It's impossible to "give a computer more RAM" using some kind of network storage.  Hard drives are way faster than network access 

Have you seen the bandwidth on SoNET lately? 

SONET/SDH Designations and bandwidths
SONET Optical Carrier Level	SONET Frame Format	SDH level and Frame Format	Payload bandwidth (kbps)	Line Rate (kbps)
OC-1	STS-1	STM-0	50,112	51,840
OC-3	STS-3	STM-1	150,336	155,520
OC-12	STS-12	STM-4	601,344	622,080
OC-24	STS-24	–	1,202,688	1,244,160
OC-48	STS-48	STM-16	2,405,376	2,488,320
OC-192	STS-192	STM-64	9,621,504	9,953,280
OC-768	STS-768	STM-256	38,486,016	39,813,120
OC-3072	STS-3072	STM-1024	153,944,064	159,252,480

---

